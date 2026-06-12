---
title: "Chicken or egg?"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by Ray G on 2009-03-27
I have been trying to install Ubuntu Studio for two days on my pc at home.
I posted earlier as I initially had problems booting from the DVD I downloaded, but was kindly told that the features that make up Studio are already bundled with Ubuntu.  One quick test on my work machine (where I am dummy-running everything) proved this to be the case and I raced home to reproduce the experiment on my pc at home.
However it did not work (same install CD so same version, 8.10).  I have tried everything I can think of in the past few hours.  As well as trawling this forum for help, I have tried networking the pc to my lappy, which connects directly to the internet (I am assuming the terminal command sudo apt-get install...ubununtustudio-audio etc... tells ubuntu to connect to the internet am I correct?) but cannot get it to share the internet connection or file-share either (although I think the Ubuntu machine recognises the IP of the lappy in tracing, but will not ping it).
Finally I thought I would try to install my broadband on the Ubuntu machine and connect directly to the internet from there, this is the chicken and egg bit; I am with Pipex, but cannot install the software as it is an exe. file, and cannot download Wine because I can't get on the internet with Ubuntu.  

Am I missing something?

---

### Post by tom56 on 2009-03-27
You shouldn't need to install any software to access the internet, just plug in and away you go. Even if you do need to fiddle around a bit the Windows software shouldn't be necessary - those discs are usually just an excuse for the ISP to rebrand Internet Explorer with their own logos.

You might find this page helpful - [https://help.ubuntu.com/8.10/internet/C/connect.html](https://help.ubuntu.com/8.10/internet/C/connect.html)

Depending on what kind of connection you are setting up, you might want to look around the settings in System->Preferences->Network Connections. If you want to add a conection that requires a username and password, then look at "Add" under the DSL tab.

---

### Post by Ray G on 2009-03-27
Thanks for the tip.

---

