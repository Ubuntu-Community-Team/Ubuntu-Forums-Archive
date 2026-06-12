---
title: "Vanishing WiFi"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by WileyHunter on 2008-03-08
Ok, so I got the Linksys WMP300N PCI adapter the other day...  Got it installed and recognized via ndiswrapper.

Now, the problem is that when I shutdown/reset computer into Linux mode (I'm dual boot Vista), the Network manager doesn't bring up the WiFi...  I have to go to System/Administration/Windows Wireless Drivers and remove driver/re-install for it to work.  Then it immediately pulls it up and connects to WiFi net.

This is more of an frustration at this point than a true problem, but I figure that someone here probably has knowledge of this.

Running Ubuntu 7.10 on a Compaq SR5250NX.

Thanks
WH

---

### Post by alphacrux on 2008-03-26
Hey Wiley! Let me see if I can help

So is your wireless device even being loaded on startup or is it just that Network Manger isn't finding any networks. You can use "iwconfig" to find out whether or not the device is being loaded. If it is try "lshw -C network" right after you boot up let me know what driver is being loaded with your card. It may be a competing driver problem, if so thats pretty easy to fix.

---

### Post by trigsenior on 2008-03-26
I can't  help unforunately ,
I am having the same problem as you , i have to reboot to get my wifi back .

Ubuntu 7.10 gutsy
hp pavilion slimline ... (not sure)

---

### Post by WileyHunter on 2008-03-29
I will have to get back to you later on this...  I'm currently on shift and won't have a chance to get into the system till I get off later next week.  I appreciate your assistance in this though.

WH

---

### Post by vlaar on 2008-03-29
hey,
i had the same problem at first.
but have you tried to restart ndiswrapper (don´t know if restart is the right word for this)
try this:
_modprobe ndiswrapper_ (get root first!!)

---

### Post by WileyHunter on 2008-04-13
This problem is on hold for me for a while...  My second desktop (DVR?) is now dead, primary desktop has wifi module on the DSL modem as an add-on and it works fine.  So until I re-build/replace the DVR unit I won't be facing this.

WH

---

