---
title: "Help! Broadband Issues"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by jgpb1986 on 2009-03-01
I find Ubuntu really quick on firefox but everytime I sign in it wont automatically find the connection. I have to play around for ages trying passphrase key etc 

When it does work it disconnects as soon as I start to try and download extra programs

Any ideas?

Thinking maybe I need to use a certain security type passcode or something that is more acceptable with ubuntu, i am using WEP at the min

thanks

---

### Post by Doug11 on 2009-03-01
> **jgpb1986 said:**
> I find Ubuntu really quick on firefox but everytime I sign in it wont automatically find the connection. I have to play around for ages trying passphrase key etc 

When it does work it disconnects as soon as I start to try and download extra programs

Any ideas?

Thinking maybe I need to use a certain security type passcode or something that is more acceptable with ubuntu, i am using WEP at the min

thanks
Are you using any kind of Network Manager?

---

### Post by jgpb1986 on 2009-03-01
thanks for your reply

Sorry, how do you mean a network manager? All I am doing is using the ubuntu os, i am not using any extra programs

---

### Post by Kevbert on 2009-03-01
Welcome to Ubuntu.
Please go to Applications-Accessories_Terminal and enter the following command
```
lspci
```to list all PCI devices including your wireless card or
```
lsusb 
```if your wireless adapter is USB.
If you can connect to broadband please enter the following command
```
iwconfig
```to list your wireless configuration. In each case select the text displayed by highlighting it with the mouse and pressing Ctrl-Shift-C (to copy), open a new post and press Ctrl-V to paste the text into the post.
Have you installed any wireless drivers ?

---

