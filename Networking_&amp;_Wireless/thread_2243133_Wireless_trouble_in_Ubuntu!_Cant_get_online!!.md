---
title: "Wireless trouble in Ubuntu! Cant get online!!"
date: 2014-09-06
forum: Networking &amp; Wireless
---

### Post by Zhitzu on 2014-09-06
Ok, im trying to get online on wifi in my newly installed ubuntu.

There is no wireless network card in my computer, so I'm using a netgear wnda3100 n600 wireless dual band usb adaptor!

This has caused me alot of trouble, that i couldt find any linux based driver for this adaptor!!!

So i found some articles on the internet on how to get this working, and I found some drivers that apparently should be to windows! These was some INF files..

[FONT=arial]I then installed ndiswrapper with [/FONT][FONT=arial]"sudo apt-get install ndiswrapper-common ndiswrapper-dkms;" command, to get these INF files installed..

Then I installed the drivers I've downloaded by using "[/FONT][FONT=arial]sudo ndiswrapper -i bcmn43xx64.inf".[/FONT]

[FONT=arial]Everything installed properly, but still, when i use[/FONT] "iwconfig", i get this:

```
eth0      no wireless extensions.

lo        no wireless extensions.
```

I really dont know what to do now, please help!!

---

### Post by Zhitzu on 2014-09-06
...Ok just found out that this simply cant be done..... the smartest thing for me to do ist just to get another wifi adaptor supported by linux..

just close the thread... sigh....

---

### Post by cariboo on 2014-09-06
closed thread by request.

---

