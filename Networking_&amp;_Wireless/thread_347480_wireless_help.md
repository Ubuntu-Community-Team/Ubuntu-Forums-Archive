---
title: "wireless help"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by Eggsaregood on 2007-01-27
So I just installed Ubuntu 6.10 and its my first time using Ubuntu and Linux so it is complete noob talk here. I have a wireless card Linksys WMP11 Wireless-B card on my computer. It does not have a native linux driver, when i go to System>Administration>Network (or something like that) I only get an option for modem, but no wireless. (yes, i am using another computer right now with windows) I do not have acess to my computer now since someone is working on my windows OS...

---

### Post by hggdh on 2007-01-27
The WMP11 is indeed not natively supported under Linux (seems to come with a Broadcom BCM43xx chipset). You will have to use ndiswrapper ([http://ndiswrapper.sf.net](http://ndiswrapper.sf.net)) or, at Edgy, the ndiswrapper packages (sudo apt-get install ndiswrapper).

You will also need the Windows drivers for the WMP11. See the web site above for installation & configuration options.

Now... there is a new kernel module -- bcm43xx -- that *might* do the trick. You may also try it, if your distro has it supported.

---

