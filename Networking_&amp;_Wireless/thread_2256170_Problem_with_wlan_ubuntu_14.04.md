---
title: "Problem with wlan ubuntu 14.04"
date: 2014-12-10
forum: Networking &amp; Wireless
---

### Post by lukas-buehrer on 2014-12-10
Hello,

im using for my internet connection the huawei e3531 umts stick and it works perfectly fine. Because i use more than one device i bought the [COLOR=#000000][FONT=sans-serif]TP-Link Wireless Router TL-MR3020. i put my umts stick in there and it lets me connect thorugh wlan to the internet and that also works great, but:

my destop pc uses the [/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]Edimax EW-7811Un for wlan and there is the problem. the  wifi connection is extremely slow. when i connect the router with my desktop via lan, it works just fine. on the same pc is also windows and there everything works fine, wlan and lan. On my Laptop i also have Ubuntu 14.04 and there also everything works great. 
it seems that something is just not right with the edimax and ubuntu.

Hope you can help me :)[/FONT][/COLOR]

---

### Post by lah7 on 2014-12-11
Hello. Welcome to the forums!

I found these links that allow you to compile a different driver that might prevent the wireless from dropping:
[http://ubuntuforums.org/showthread.php?t=1744371&p=10743921#post10743921]("http://ubuntuforums.org/showthread.php?t=1744371")
[http://askubuntu.com/questions/246236/compile-and-install-rtl8192cu-driver](http://askubuntu.com/questions/246236/compile-and-install-rtl8192cu-driver)

Be careful, since this could *potentially *break networking functionality altogether.


I can share your frustrations with slow wireless connectivity since I had a similar problem 2 years ago with a USB Netgear Wireless Adapter.
Ubuntu 11.04 was all great, 11.10 had a new driver with no easy way to revert, it wasn't until 12.10 when it was fixed.

---

