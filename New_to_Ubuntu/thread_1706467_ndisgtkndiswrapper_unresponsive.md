---
title: "ndisgtk/ndiswrapper unresponsive"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by Carter12s on 2011-03-13
Hello, I am brand new to Ubuntu and have just completed my first installation. Now, I am trying to configure my belkin play wireless USB adapter to work with Ubuntu 10.10. I found this guide:
[http://www.linuxforums.org/forum/ubuntu-linux/168175-belkin-f7d4101.html](http://www.linuxforums.org/forum/ubuntu-linux/168175-belkin-f7d4101.html)

I downloaded the file indicated there and tried to add it through Windows Wireless Drivers. When I did I received an error, and now every time I start Windows Wireless Drivers it immediately freezes. I have tried completely uninstalling and re-installing ndisgtk, but that produced no change.

I am sure that there are some terminal commands that could allow me to access ndisgtk in a way that won't freeze it, but I don't know them. I want to get ndisgtk working, because I have now found the correct .inf driver by using wine on USB setup executable. Can anyone help me?

---

### Post by wep940 on 2011-03-14
Please post back the following information to give us more to go on towards helping you:
 
[LIST=1]
[*]lsusb   -> with the device plugged in
[*]Are you running 32-bit or 64-bit Ubuntu?
[*]The drivers you use for ndiswrapper/ndisgtk must be Windows XP drivers, and they must match your architecture - 32-bit for 32-bit Ubuntu, 64-bit for 64-bit Ubuntu.  What drivers are you using?
[*]Do you have a way to temporarily hard-wire a connection between your PC and your router?  If so, the much preferred way is to do that connection, run sudo apt-get update in a terminal window, then check in system/administration/additional drivers and see if a driver shows there - if so, be sure it is enabled.  Also be sure you have reversed ANYTHING you did with ndiswrapper/ndisgtk prior to doing anything.
[/LIST]

---

