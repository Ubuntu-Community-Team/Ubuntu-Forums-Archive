---
title: "logs?"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by a cup of tea on 2009-03-24
A few hours ago, my computer froze up. I know there's a way to get to the terminal with the keyboard, but I couldn't remember what, ended up shutting off the computer by killing the power. Ugh.

Yeah, ok, I'm a noob. Now...I think I know why this happened. Pretty sure it had to do with a device I had attached to my computer at the time malfunctioning. I want to know if there's some sort of log kept by my computer of stuff like this. How would I access this log, what would I be looking for?

---

### Post by sazan on 2009-03-24
> **a cup of tea said:**
> A few hours ago, my computer froze up. I know there's a way to get to the terminal with the keyboard, but I couldn't remember what, ended up shutting off the computer by killing the power. Ugh.

Yeah, ok, I'm a noob. Now...I think I know why this happened. Pretty sure it had to do with a device I had attached to my computer at the time malfunctioning. I want to know if there's some sort of log kept by my computer of stuff like this. How would I access this log, what would I be looking for?

u can check 
/var/log/messages 

or run the command ->
dmesg|tail

---

### Post by a cup of tea on 2009-03-24
> **sazan said:**
> u can check 
/var/log/messages 

Thank you. I found the logs and am looking through them. There's a lot that I don't understand there, but I found what I was looking for in them, so I'm rather happy about that.

---

### Post by a cup of tea on 2009-03-24
Wow, I am an idiot. 

I plugged the (known to be totally messed up) device back into the computer. I just wanted to try to find out more about it. I was looking for information.

Computer froze. Again. I would like to know how to get to the terminal if the screen is frozen and I can't move the mouse. I know I read about there being a way to do it with the keyboard, and I tried it when I read it. And then I forgot it. :roll:

---

### Post by VCoolio on 2009-03-24
<ctrl><alt>F1-F6 gives commandline (depending on your getty settings; 6 is default). 
<ctrl><alt>F7 gets you back, although that may not work if everything was frozen.

---

### Post by a cup of tea on 2009-03-24
thanks. :D

---

