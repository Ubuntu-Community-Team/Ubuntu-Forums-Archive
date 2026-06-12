---
title: "screen not working"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by alexvision on 2009-01-28
i just installed ubuntu on a friends laptop, but when it boots into ubuntu up it splits up into three vertical screens each showing different parts of the screen, it there any way to fix this??

---

### Post by halovivek on 2009-01-28
Hi could you please post more details about your friends computer?
what is the graphics card, RAM, Hard disk?

---

### Post by Omegaxis on 2009-01-28
I'm having a similar problem. [here]("http://ubuntuforums.org/showthread.php?t=1036357")

---

### Post by affl1cted on 2009-01-28
Thats a graphics problem. You should use Envy to install apropriate Drivers (assuming you have infact ATi or NVidia) that should detect your proper screen size & hopefuly fix the problem. Also, if the GUI is causing too much hassle to navigate properly, I believe if you go to console, and type:

sudo -s [return]
<your password> [return]
init 1 [return]

wait about 5 seconds and choose the option to drop into shell, you can do everything you need from there, just be prepared to use apt-get, wget & aptitude a bit XD

---

