---
title: "access routers firmware page using ssh?"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by josh on 2007-04-26
hello!

how can i access my router's firmware page from my office using ssh? 
do i need to port forward/tunnel? i have connected to my home pc using ssh but its only the command prompt. i would like to use my "work" browser (while being connected to my home pc using ssh) to access my routers firmware page maybe through port forwarding or tunneling? i sure don't know how to. any suggestions?

cheers!
josh

---

### Post by chili555 on 2007-04-26
Once you have reached your home pc through ssh and have a command prompt, have you tried```
lynx 192.168.1.1
```If you do not have lynx, you can, through the same command prompt:```
sudo apt-get install lynx
```Lynx is an ncurses-based web browser. It takes some fiddling to learn how to navigate without a mouse, but it works well enough in situations where you do not have X and a GUI.

---

### Post by josh on 2007-04-26
hey chilli555!

thanks for your reply. but what i had in mind is using firefox from my work browser. i know with email you can tunnel incoming traffic and outgoing traffic and just change the port numbers in the mailclient. is that also possible in a web browser?

---

### Post by chili555 on 2007-04-26
If your work machine is running X, then simply do:```
ssh -X user@host
firefox http://192.168.1.1
```If your work machine is a typical Windows installation, it probably doesn't run X and unless you run the company, you probably can't get permission to install it.

---

### Post by josh on 2007-04-26
unfortunately my workpc is a window box :( sux!

well i guess its not possible. thanks for your help chilli555!

---

### Post by chili555 on 2007-04-26
It IS possible, with lynx. Please try it before you dismiss it.

---

