---
title: "How to install .linux file??"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by gaillour13 on 2010-09-18
Total n00b with ubuntu, please help me out. I'm trying to install a program called cacaoweb.linux I've downloaded it but I'm not sure how to actually install it now. Thanks for any help.

---

### Post by davidmohammed on 2010-09-18
this [step by step]("http://www.cacaoweb.org/downloads.html") guide should get you going.

---

### Post by gaillour13 on 2010-09-18
When I paste that into the terminal it says no such file or directory. And when I try it in the directory that I downloaded the file to and I press enter it doesn't do anything, it just goes to the next line?

---

### Post by gaillour13 on 2010-09-26
Could somebody help me out?

---

### Post by halitech on 2010-09-26
> **gaillour13 said:**
> Could somebody help me out?

so when you ran the second step it just dropped a line?

> How to use on Linux

1. Download the latest executable
2. Make it executable with

chmod +x cacaoweb.linux

3. Launch it with

./cacaoweb.linux

or

./cacaoweb.linux &

4. Navigate to [http://127.0.0.1:4001/index.html](http://127.0.0.1:4001/index.html) in your favorite browser

---

### Post by Spidertech500 on 2010-09-29
I've got you on this:
1.download cacaoweb.linux
2. right click and select "open with other application"
3.hit the arrow next to "use a custom command"
4.UNCHECK "REMEMBER THIS APPLICATION FOR EXECUTABLE FILES" VERY IMPORTANT!!!!!
5.type in box:chmod +x cacaoweb.linux
click open and your browser should redirect to this: [http://127.0.0.1:4001/index.html](http://127.0.0.1:4001/index.html)

 Give that a whirl!

---

### Post by Spidertech500 on 2010-09-29
One last thing, once you execute the file, you need to keep the program/plugin whereyou originally executed it;
ex, i did steps on desktop, file must stay on desktop or else location is lost,
solution: i created a folder called Applications in my home folder and ran it there, i sugest you do the same
Enjoy!

---

### Post by gaillour13 on 2010-10-08
Awesome, worked perfectly, thanks so much.

---

