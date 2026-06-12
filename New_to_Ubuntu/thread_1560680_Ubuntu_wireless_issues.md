---
title: "Ubuntu wireless issues"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by Smooth357 on 2010-08-25
[FONT=Comic Sans MS]Ok this going to be stupid , but here is my problem.
I have a dual boot of ubuntu 10.04 64 bit and my wireless card is not working it worked when I first installed  then quit. re installed 3 times worked until I shut the machine down. then it worked for 4 or 5 days with shutdowns. Then I installed a theme program epidermis I think and my buttons disappeared on the windows my compiz can't do the wobbly thing and I cant move the windows and have to minimize by hitting the taskbar. I am so freaking frustrated ](*,) I like ubuntu and would consider moving full time, but I need to get to know the system much better than I do. Any suggestions on the wireless card and the disappearing buttons would be helpful.[/FONT]

---

### Post by Peter09 on 2010-08-25
Looks like you screwed Compiz. Change the theme back to a standard one and check in System->preferences->appearance that you have 'normal' effects (or greater) selected. Then logout (or reboot) and log in again. See if that resolves your problems.

---

### Post by Peter09 on 2010-08-25
just a thought - if you mean emerald - rather than epidermis, then try in a terminal
 
> emerald
 
if everything recovers OK you need to run emerald at start up.
 
System->preferences->startup

---

### Post by Smooth357 on 2010-08-26
[FONT=Comic Sans MS]Frustration took the better of me and I just reinstalled the whole shebang I tried kubuntu first and I was so lost. LOL anyway I have reinstalled and I am try to learn. :popcorn:
BTW still having trouble with the wireless going out after shutdown and I reinstalled 3 times then to get it to work please help with that if possible u can hit me in email or PM doesn't matter I need help though.
[/FONT]

---

### Post by Peter09 on 2010-08-27
Can you post the output of
```
ifconfig
```
and
```
lshw -C network
```
 
when your wireless is working

---

