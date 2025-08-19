# What-is-Event--

### ইভেন্ট কী?
ইভেন্ট হলো ওয়েব পেজে ব্যবহারকারী বা সিস্টেমের কোনো ক্রিয়া বা ঘটনা, যা DOM (Document Object Model) এর মাধ্যমে ধরা এবং হ্যান্ডল করা যায়। সহজ কথায়, যখন কোনো ইউজার ওয়েব পেজে কিছু করে (যেমন বাটন ক্লিক, মাউস মুভ, কীবোর্ডে টাইপ), তখন একটি ইভেন্ট তৈরি হয়। জাভাস্ক্রিপ্ট ব্যবহার করে এই ইভেন্টগুলো শনাক্ত করে নির্দিষ্ট কাজ (যেমন টেক্সট পরিবর্তন, স্টাইল চেঞ্জ) করা যায়। ইভেন্ট হলো ডাইনামিক ওয়েবসাইট তৈরির একটি মূল অংশ, কারণ এটি ইউজার ইন্টারঅ্যাকশনের ভিত্তিতে পেজ আপডেট করে।

### ওয়েবে ইভেন্টের বিভিন্ন প্রকার
ওয়েবে ইভেন্ট বিভিন্ন ধরনের হতে পারে, যেগুলো ইউজারের ক্রিয়া বা সিস্টেমের অবস্থার উপর নির্ভর করে। নিচে প্রধান প্রকারগুলো বাংলায় ব্যাখ্যা করছি, সাথে উদাহরণ হিসেবে ইংরেজি কোড দেবো। এই তথ্যগুলো MDN Web Docs এবং অন্যান্য ওয়েব ডেভেলপমেন্ট সোর্স থেকে নেয়া।

#### ১. মাউস ইভেন্ট (Mouse Events)
এগুলো ইউজারের মাউস-সম্পর্কিত ক্রিয়ার সাথে যুক্ত, যেমন ক্লিক, হোভার, ড্রাগ ইত্যাদি।  
- **click**: ইউজার কোনো এলিমেন্টে ক্লিক করলে ঘটে।  
- **dblclick**: ডাবল ক্লিক করলে।  
- **mouseover**: মাউস পয়েন্টার এলিমেন্টের উপরে যায়।  
- **mouseout**: মাউস এলিমেন্টের বাইরে চলে যায়।  
- **mousedown**: মাউস বাটন প্রেস করা হয়।  
- **mouseup**: মাউস বাটন ছাড়া হয়।  
- **mousemove**: মাউস মুভ করলে।  

**উদাহরণ (ইংরেজিতে)**:
```html
<!DOCTYPE html>
<html>
  <body>
    <button id="myButton">Click Me</button>
    <p id="output">Waiting...</p>
    <script>
      let button = document.getElementById("myButton");
      button.addEventListener("click", () => {
        document.getElementById("output").innerText = "Button Clicked!";
      });
      button.addEventListener("mouseover", () => {
        button.style.backgroundColor = "yellow";
      });
      button.addEventListener("mouseout", () => {
        button.style.backgroundColor = "";
      });
    </script>
  </body>
</html>
```
**ব্যাখ্যা**: বাটনে ক্লিক করলে টেক্সট পরিবর্তন হয়, মাউস হোভার করলে ব্যাকগ্রাউন্ড হলুদ হয়, এবং মাউস সরালে ব্যাকগ্রাউন্ড ফিরে আসে।

#### ২. কীবোর্ড ইভেন্ট (Keyboard Events)
ইউজার কীবোর্ডে কিছু টাইপ বা প্রেস করলে এই ইভ

েন্টগুলো ঘটে।  
- **keydown**: কোনো কী প্রেস করা হলে।  
- **keyup**: কী ছাড়া হলে।  
- **keypress**: কী প্রেস করা হলে (শুধু ক্যারেক্টার কী-এর জন্য, এখন ডিপ্রিকেটেড)।  

**উদাহরণ (ইংরেজিতে)**:
```html
<!DOCTYPE html>
<html>
  <body>
    <input type="text" id="myInput" placeholder="Type here">
    <p id="output">Key pressed: None</p>
    <script>
      document.getElementById("myInput").addEventListener("keydown", (event) => {
        document.getElementById("output").innerText = `Key pressed: ${event.key}`;
      });
    </script>
  </body>
</html>
```
**ব্যাখ্যা**: ইনপুট ফিল্ডে কী প্রেস করলে সেই কী-এর নাম প্যারাগ্রাফে দেখানো হয়।

#### ৩. ফর্ম ইভেন্ট (Form Events)
ফর্ম-সম্পর্কিত ক্রিয়া, যেমন সাবমিট, ইনপুট পরিবর্তন ইত্যাদি।  
- **submit**: ফর্ম সাবমিট করলে।  
- **change**: ইনপুট ফিল্ডের ভ্যালু পরিবর্তন হয়ে ফোকাস হারালে।  
- **input**: ইনপুট ফিল্ডে কিছু টাইপ বা পরিবর্তন হলে (রিয়েল-টাইম)।  
- **focus**: এলিমেন্ট ফোকাস পেলে।  
- **blur**: ফোকাস হারালে।  

**উদাহরণ (ইংরেজিতে)**:
```html
<!DOCTYPE html>
<html>
  <body>
    <form id="myForm">
      <input type="text" id="myInput" placeholder="Enter text">
      <button type="submit">Submit</button>
    </form>
    <p id="output">No submission yet</p>
    <script>
      document.getElementById("myForm").addEventListener("submit", (event) => {
        event.preventDefault(); // Prevents page reload
        let input = document.getElementById("myInput").value;
        document.getElementById("output").innerText = `Submitted: ${input}`;
      });
    </script>
  </body>
</html>
```
**ব্যাখ্যা**: ফর্ম সাবমিট করলে ইনপুটের ভ্যালু প্যারাগ্রাফে দেখানো হয়। `preventDefault()` পেজ রিলোড আটকায়।

#### ৪. উইন্ডো ইভেন্ট (Window Events)
এগুলো ব্রাউজার উইন্ডো বা পেজের সাথে সম্পর্কিত।  
- **load**: পেজ বা রিসোর্স সম্পূর্ণ লোড হলে।  
- **resize**: উইন্ডোর সাইজ পরিবর্তন হলে।  
- **scroll**: পেজ স্ক্রল করলে।  
- **unload**: পেজ বন্ধ বা রিলোড হলে।  

**উদাহরণ (ইংরেজিতে)**:
```html
<!DOCTYPE html>
<html>
  <body style="height: 2000px;">
    <p id="output">Scroll position: 0</p>
    <script>
      window.addEventListener("scroll", () => {
        document.getElementById("output").innerText = `Scroll position: ${window.scrollY}`;
      });
    </script>
  </body>
</html>
```
**ব্যাখ্যা**: পেজ স্ক্রল করলে স্ক্রল পজিশন রিয়েল-টাইমে দেখানো হয়।

#### ৫. ড্রাগ অ্যান্ড ড্রপ ইভেন্ট (Drag and Drop Events)
এলিমেন্ট ড্রাগ এবং ড্রপ করার সময় ঘটে।  
- **dragstart**: ড্রাগ শুরু হলে।  
- **dragover**: ড্রাগ করা এলিমেন্ট কোনো ড্রপ জোনে থাকলে।  
- **drop**: এলিমেন্ট ড্রপ করা হলে।  

**উদাহরণ (ইংরেজিতে)**:
```html
<!DOCTYPE html>
<html>
  <body>
    <div id="dragItem" draggable="true" style="width: 100px; height: 100px; background: blue;">Drag Me</div>
    <div id="dropZone" style="width: 200px; height: 200px; border: 2px solid black;"></div>
    <script>
      let dragItem = document.getElementById("dragItem");
      let dropZone = document.getElementById("dropZone");
      dragItem.addEventListener("dragstart", (e) => e.dataTransfer.setData("text", e.target.id));
      dropZone.addEventListener("dragover", (e) => e.preventDefault());
      dropZone.addEventListener("drop", (e) => {
        e.preventDefault();
        let id = e.dataTransfer.getData("text");
        dropZone.appendChild(document.getElementById(id));
      });
    </script>
  </body>
</html>
```
**ব্যাখ্যা**: নীল বক্সটি ড্রাগ করে ড্রপ জোনে নিয়ে গেলে তা সেখানে যোগ হয়।

#### ৬. টাচ ইভেন্ট (Touch Events)
মোবাইল ডিভাইসে টাচ-সম্পর্কিত ইভেন্ট।  
- **touchstart**: স্ক্রিনে টাচ শুরু হলে।  
- **touchmove**: টাচ মুভ করলে।  
- **touchend**: টাচ ছাড়া হলে।  

**উদাহরণ (ইংরেজিতে)**:
```html
<!DOCTYPE html>
<html>
  <body>
    <div id="touchArea" style="width: 200px; height: 200px; background: lightblue;">Touch Me</div>
    <p id="output">No touch</p>
    <script>
      document.getElementById("touchArea").addEventListener("touchstart", () => {
        document.getElementById("output").innerText = "Touch Started!";
      });
    </script>
  </body>
</html>
```
**ব্যাখ্যা**: মোবাইল ডিভাইসে ডিভ টাচ করলে টেক্সট পরিবর্তন হয়।

#### ৭. অন্যান্য ইভেন্ট
- **copy**, **cut**, **paste**: ক্লিপবোর্ড অপারেশন।  
- **error**: ইমেজ বা স্ক্রিপ্ট লোডে ত্রুটি হলে।  
- **animationend**: CSS অ্যানিমেশন শেষ হলে।  

### ইভেন্ট হ্যান্ডলিং এর গুরুত্বপূর্ণ বিষয়
- **Event Object**: প্রতিটি ইভেন্টে একটি অবজেক্ট পাস হয় যাতে ইভেন্টের বিস্তারিত থাকে (যেমন event.target, event.key)।
- **Event Bubbling**: ইভেন্ট চাইল্ড থেকে প্যারেন্টে প্রোপাগেট করে। `event.stopPropagation()` দিয়ে আটকানো যায়।
- **Event Delegation**: প্যারেন্টে লিসেনার সেট করে চাইল্ড এলিমেন্ট হ্যান্ডল করা, পারফরম্যান্স বাড়ায়।
- **preventDefault()**: ডিফল্ট আচরণ (যেমন ফর্ম সাবমিটে পেজ রিলোড) আটকায়।

**উদাহরণ – Event Delegation**:
```html
<!DOCTYPE html>
<html>
  <body>
    <ul id="myList">
      <li>Item 1</li>
      <li>Item 2</li>
    </ul>
    <script>
      document.getElementById("myList").addEventListener("click", (event) => {
        if (event.target.tagName === "LI") {
          event.target.style.color = "red";
        }
      });
    </script>
  </body>
</html>
```
**ব্যাখ্যা**: লিস্ট আইটেমে ক্লিক করলে শুধু সেই আইটেমের রং লাল হয়, প্যারেন্টে লিসেনার ব্যবহার করে।

### কেন ইভেন্ট জানা জরুরি?
- **ইন্টারঅ্যাকটিভিটি**: ইউজারের অ্যাকশনের উপর ভিত্তি করে পেজ আপডেট করা।
- **ডাইনামিক ওয়েব**: ফর্ম ভ্যালিডেশন, রিয়েল-টাইম আপডেট, ড্রাগ-ড্রপ ফিচার।
- **ইউজার এক্সপেরিয়েন্স**: মসৃণ এবং ইন্টারঅ্যাকটিভ UI তৈরি।

--


---

### কোড এবং লাইন বাই লাইন ব্যাখ্যা

```html
<!DOCTYPE html>
```
- **ব্যাখ্যা**: এটি HTML ডকুমেন্টের প্রথম লাইন, যা ব্রাউজারকে জানায় এটি একটি HTML5 ডকুমেন্ট। `<!DOCTYPE html>` ডকুমেন্টের টাইপ ডিক্লেয়ার করে এবং নিশ্চিত করে যে ব্রাউজার HTML5 স্ট্যান্ডার্ড অনুযায়ী পেজটি রেন্ডার করবে। এটি DOM তৈরির প্রথম ধাপ, কারণ ব্রাউজার এই ডকুমেন্ট থেকে DOM ট্রি তৈরি শুরু করে।

```html
<html>
```
- **ব্যাখ্যা**: এটি HTML ডকুমেন্টের রুট এলিমেন্ট। DOM ট্রির রুট নোড হিসেবে `<html>` কাজ করে। এর ভেতরে সব এলিমেন্ট (যেমন `<head>`, `<body>`) চাইল্ড নোড হিসেবে থাকে। এখানে `<html>` ট্যাগে কোনো অ্যাট্রিবিউট (যেমন `lang="en"`) দেয়া হয়নি, তবে সাধারণত ভাষা নির্দিষ্ট করা ভালো প্র্যাকটিস।

```html
  <body>
```
- **ব্যাখ্যা**: `<body>` ট্যাগ হলো HTML ডকুমেন্টের প্রধান কনটেন্ট এরিয়া, যেখানে ব্রাউজারে দৃশ্যমান এলিমেন্টগুলো থাকে। DOM ট্রিতে এটি `<html>` এর একটি চাইল্ড নোড। এর ভেতরের সব এলিমেন্ট (যেমন বাটন, প্যারাগ্রাফ) `<body>` এর চাইল্ড হিসেবে DOM এ যোগ হয়।

```html
    <button id="myButton">Click Me</button>
```
- **ব্যাখ্যা**: এটি একটি `<button>` এলিমেন্ট যার `id` অ্যাট্রিবিউট হলো `"myButton"`। বাটনের ভেতরের টেক্সট হলো "Click Me", যা ব্রাউজারে বাটনের লেবেল হিসেবে দেখায়। DOM এ এটি একটি এলিমেন্ট নোড, এবং `id` ব্যবহার করে এটি জাভাস্ক্রিপ্টে অ্যাক্সেস করা যায়। এই বাটনের সাথে ইভেন্ট লিসেনার যুক্ত করা হবে।

```html
    <p id="output">Waiting...</p>
```
- **ব্যাখ্যা**: এটি একটি `<p>` (প্যারাগ্রাফ) এলিমেন্ট যার `id` হলো `"output"`। এর ভেতরের টেক্সট হলো "Waiting..."। DOM এ এটি একটি এলিমেন্ট নোড, এবং এর টেক্সট পরিবর্তন করা যায় জাভাস্ক্রিপ্ট দিয়ে। এই প্যারাগ্রাফটি বাটনের ইভেন্টের ফলাফল দেখানোর জন্য ব্যবহৃত হবে।

```html
    <script>
```
- **ব্যাখ্যা**: `<script>` ট্যাগ জাভাস্ক্রিপ্ট কোড ধারণ করে। এটি DOM এর সাথে ইন্টারঅ্যাক্ট করার জন্য ব্যবহৃত হয়। এর ভেতরের কোড ব্রাউজারে এক্সিকিউট হয় এবং DOM ম্যানিপুলেট করে। এখানে আমরা বাটনের ইভেন্ট হ্যান্ডল করার কোড লিখবো।

```javascript
      let button = document.getElementById("myButton");
```
- **ব্যাখ্যা**: এই লাইনে `document.getElementById("myButton")` মেথড ব্যবহার করে `id="myButton"` সহ বাটন এলিমেন্টটি খুঁজে বের করা হয়। `document` হলো DOM এর রুট অবজেক্ট, যা পুরো HTML ডকুমেন্টকে রিপ্রেজেন্ট করে। এই এলিমেন্টটি `button` নামে একটি ভেরিয়েবলে স্টোর করা হয়, যাতে পরে এটি ব্যবহার করা যায়। এটি একটি DOM নোড রিটার্ন করে।

```javascript
      button.addEventListener("click", () => {
```
- **ব্যাখ্যা**: এখানে `addEventListener` মেথড ব্যবহার করে বাটনে একটি ক্লিক ইভেন্ট লিসেনার যুক্ত করা হয়েছে। `"click"` হলো ইভেন্টের নাম, এবং তারপরে একটি অ্যারো ফাংশন (`() => {}`) দেয়া হয়েছে, যা ক্লিক ইভেন্ট ঘটলে এক্সিকিউট হবে। এটি বলে যে বাটনে ক্লিক করলে নির্দিষ্ট কাজ হবে।

```javascript
        document.getElementById("output").innerText = "Button Clicked!";
```
- **ব্যাখ্যা**: এই লাইনটি ক্লিক ইভেন্টের ফাংশনের ভেতরে আছে। এটি `id="output"` সহ `<p>` এলিমেন্টটি খুঁজে বের করে এবং তার `innerText` প্রোপার্টি ব্যবহার করে টেক্সট পরিবর্তন করে "Button Clicked!" করে। `innerText` শুধু টেক্সট কনটেন্ট পরিবর্তন করে, HTML ট্যাগ নয়। এটি DOM ম্যানিপুলেশনের একটি উদাহরণ।

```javascript
      });
```
- **ব্যাখ্যা**: এটি ক্লিক ইভেন্ট লিসেনারের ফাংশনের শেষ, যা `addEventListener` এর দ্বিতীয় আর্গুমেন্ট বন্ধ করে। এটি কেবল সিনট্যাক্সের অংশ।

```javascript
      button.addEventListener("mouseover", () => {
```
- **ব্যাখ্যা**: এখানে আরেকটি ইভেন্ট লিসেনার যুক্ত করা হয়েছে, এবার `"mouseover"` ইভেন্টের জন্য। এটি ঘটে যখন মাউস পয়েন্টার বাটনের উপরে আসে। আবার একটি অ্যারো ফাংশন দেয়া হয়েছে, যা মাউস হোভার করলে এক্সিকিউট হবে।

```javascript
        button.style.backgroundColor = "yellow";
```
- **ব্যাখ্যা**: এই লাইনটি মাউসওভার ইভেন্টের ফাংশনের ভেতরে। এটি বাটনের `style` অবজেক্টের `backgroundColor` প্রোপার্টি পরিবর্তন করে "yellow" সেট করে। এর ফলে বাটনের ব্যাকগ্রাউন্ড হলুদ হয়ে যায় যখন মাউস এর উপরে থাকে। এটি DOM এর স্টাইল ম্যানিপুলেশনের উদাহরণ।

```javascript
      });
```
- **ব্যাখ্যা**: এটি মাউসওভার ইভেন্ট লিসেনারের ফাংশন বন্ধ করে।

```javascript
      button.addEventListener("mouseout", () => {
```
- **ব্যাখ্যা**: এখানে তৃতীয় ইভেন্ট লিসেনার যুক্ত করা হয়েছে, `"mouseout"` ইভেন্টের জন্য। এটি ঘটে যখন মাউস পয়েন্টার বাটনের উপর থেকে সরে যায়। আবার একটি অ্যারো ফাংশন দেয়া হয়েছে, যা মাউস সরে গেলে এক্সিকিউট হবে।

```javascript
        button.style.backgroundColor = "";
```
- **ব্যাখ্যা**: এই লাইনটি মাউসআউট ইভেন্টের ফাংশনের ভেতরে। এটি বাটনের `backgroundColor` খালি করে দেয় (ডিফল্টে ফিরিয়ে দেয়)। এর ফলে মাউস সরে গেলে বাটনের ব্যাকগ্রাউন্ড হলুদ থেকে আগের অবস্থায় ফিরে যায়।

```javascript
      });
```
- **ব্যাখ্যা**: এটি মাউসআউট ইভেন্ট লিসেনারের ফাংশন বন্ধ করে।

```html
    </script>
```
- **ব্যাখ্যা**: এটি `<script>` ট্যাগ বন্ধ করে। এর ভেতরের জাভাস্ক্রিপ্ট কোড এক্সিকিউট হয়ে DOM এর সাথে ইন্টারঅ্যাক্ট করে।

```html
  </body>
```
- **ব্যাখ্যা**: এটি `<body>` ট্যাগ বন্ধ করে। এর ভেতরের সব এলিমেন্ট DOM ট্রিতে `<body>` নোডের চাইল্ড হিসেবে থাকে।

```html
</html>
```
- **ব্যাখ্যা**: এটি `<html>` ট্যাগ বন্ধ করে। এটি পুরো HTML ডকুমেন্টের শেষ। DOM ট্রির রুট নোডও এখানে শেষ হয়।

---

### কোডের কার্যকারিতা (সংক্ষেপে)
- পেজে একটি বাটন আছে ("Click Me") এবং একটি প্যারাগ্রাফ ("Waiting...")।
- বাটনে তিনটি ইভেন্ট লিসেনার যুক্ত করা হয়েছে:
  1. **click**: ক্লিক করলে প্যারাগ্রাফের টেক্সট "Button Clicked!" হয়।
  2. **mouseover**: মাউস বাটনের উপরে গেলে বাটনের ব্যাকগ্রাউন্ড হলুদ হয়।
  3. **mouseout**: মাউস সরে গেলে ব্যাকগ্রাউন্ড ডিফল্টে ফিরে যায়।

### DOM এর সাথে সম্পর্ক
- **এলিমেন্ট অ্যাক্সেস**: `getElementById` ব্যবহার করে DOM থেকে বাটন এবং প্যারাগ্রাফ অ্যাক্সেস করা হয়েছে।
- **ইভেন্ট হ্যান্ডলিং**: `addEventListener` দিয়ে ইউজার ইন্টারঅ্যাকশন (ক্লিক, হোভার) হ্যান্ডল করা হয়েছে।
- **DOM ম্যানিপুলেশন**: `innerText` এবং `style.backgroundColor` দিয়ে DOM এলিমেন্টের কনটেন্ট এবং স্টাইল পরিবর্তন করা হয়েছে।

### কেন এটি গুরুত্বপূর্ণ?
এই কোডটি DOM এর তিনটি মূল দিক দেখায়:
1. **এলিমেন্ট সিলেকশন**: `getElementById` দিয়ে নির্দিষ্ট এলিমেন্ট খুঁজে বের করা।
2. **ইভেন্ট হ্যান্ডলিং**: `addEventListener` দিয়ে ইউজারের অ্যাকশন ধরা।
3. **ডাইনামিক আপডেট**: `innerText` এবং `style` দিয়ে পেজ রিয়েল-টাইমে পরিবর্তন।
