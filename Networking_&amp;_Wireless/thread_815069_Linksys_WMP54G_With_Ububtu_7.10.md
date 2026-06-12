---
title: "Linksys WMP54G With Ububtu 7.10"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by Muchohombre57 on 2008-06-01
I am trying to get my Linksys WMP54G wireless card to work with Ubuntu 7.10. I have found a guide online, but have a question.

The guide asks me to open up the terminal and navigate to the folder where I have the "ndiswrapper." I have the folder on my desktop, but do not know how to get there through the terminal.

When I open up the terminal it has "my log on name@my log on name-Desktop:~$."

I also have the "Windows" driver which I need. It is on my desktop.

My thanks to all for your help!

---

### Post by chili555 on 2008-06-01
```
cd Desktop
```Then your prompt should change to ```
my log on name@my log on name-Desktop:~/Desktop$
```Then you can do:```
ls -l
```and see the contents of *Desktop.*Your inf file may be in a folder, Drivers for example. Then you can:```
cd Drivers
```and drill down to the inf file. Then run your *ndiswrapper -i whatever.inf* command.

---

### Post by Muchohombre57 on 2008-06-01
Chili:

I thank you for you help! When I entered "1s-1" I get "bash: command not found."

---

### Post by chili555 on 2008-06-01
It's the lower case letter L, not the number 1. It means, roughly, 'list the directory contents, in the long format, please.' Directories show up in purty colors.

---

### Post by Muchohombre57 on 2008-06-01
Chili555:
Thank you for correcting my mistake. However I am now getting "bash: ls-l command not found."

Being new to Linux I believe my best course of action is to try and find a wireless card which will work with Ubuntu out of the box.

If you know of any please direct me to where I can purchase one.

Thank you again!

---

### Post by chili555 on 2008-06-01
ls -l

With a space.

Please do not give up on yourself. We are close. We can master this stuff with a bit of practice.

---

