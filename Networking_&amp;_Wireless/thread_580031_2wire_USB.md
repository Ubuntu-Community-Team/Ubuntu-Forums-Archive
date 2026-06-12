---
title: "2wire USB?"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by rohizzle121 on 2007-10-18
i have searched throught your forums and some people somehow got the 2wire isb dongle to work!


how is this possible?
please help this is the only thing holding me back from dedicating my pc to ubuntu

---

### Post by zeusdo on 2007-10-18
I'm having the same problem. Under network connections there is no icon for wireless, I guess because it doesn't recognize the 2wire USB wireless adapter.

---

### Post by rohizzle121 on 2007-10-18
its seems as tho some people got it to work.
i just dont know how.

---

### Post by pinkmonkey on 2007-10-24
I just finished solving this problem on my sisters computer and after only three hours the wireless network is up and running.
Follow the instructions@ [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless)
for windows wireless cards. I tried using the GUI but I found that terminal worked better. The two files needed were WlanUIG.inf and WlanUIG.sys. If found them on the Quest quick network cd. (The wireless card came with her router and so did the cd). 
The only problems Is that it has to be re initialized every  time I log in. The directions say that sudo ndiswrapper -m is supposed to load the module when the computer boots but it doesn't seem to be the case. If anyone knows what to do about it some help would be appreciated

---

### Post by defconoii on 2008-02-25
This should help you setup the 2WIRE USB Dongle:
[http://www.ubuntu-unleashed.com/2008/02/howto-setup-2wire-80211g-wireless-usb.html](http://www.ubuntu-unleashed.com/2008/02/howto-setup-2wire-80211g-wireless-usb.html)

---

