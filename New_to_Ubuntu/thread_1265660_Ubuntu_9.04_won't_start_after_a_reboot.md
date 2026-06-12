---
title: "Ubuntu 9.04 won't start after a reboot"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by Toivoja on 2009-09-13
Hi. I'm new in Linux-world and decided to Replace Vista with Ubuntu 9.04. Problems came when I started my computer after a normal shutdown. It seems to load Ubuntu normally but when it's supposed to ask username and password it just gives me a screen where there is some fuzzy colors that do not make any sense.
 
I have already installed it three times over and everytime I need to reboot the computer after intallation, it works but after that booting doesn't work.
 
Tried to use Ubuntus recovery system but it doesn't help. Also Tried to repair the system with CD's repair tool but in no vain.
 
As I'm new I'm pretty helpless with this Ubuntu problem. Does anyone have any Ideas?

---

### Post by stderr on 2009-09-13
Hi Toivoja. Good decision to move to Ubuntu, I took a solemn oath never to install the retail version of Vista after trying an early version! 

When you boot to the useless fuzzy screen, can you get a textual login screen by using Ctrl+Alt+F2 ?

Also, do you happen to know what graphics card you have? If not, no matter, we can find out later.

---

### Post by kansasnoob on 2009-09-13
Please boot the Ubuntu Live CD in that machine and go to Terminal. Then post the output of this command:

```
lspci | grep VGA
```

That should provide some needed info.

---

### Post by Toivoja on 2009-09-13
It seems that I have more Problems but this time not with Ubuntu. I installed Ubuntu to a Computer that I used to use and It's Battery ain't in a good shape. Furthermore this time Ubuntu has started perfectly.
 
If the trouble comes again, I'll try your suggestions. Thanks for your help.

---

