---
title: "(K)ubuntu in flight-- how to turn off wireless transmitter"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by esekyavuz on 2007-07-23
Hi all

I would like to turn wifi (and bluetooth) off for continued GNU/Linux joy on airplanes. Can someone please tell me how to do this?

Running Kubuntu Fiesty on Dell Latitude D620.

TIA

---

### Post by fredj on 2007-07-24
Most notebooks have a Fn key combination that allows you to do that from the keyboard. If not look in the
bios and see if you can disable them there.

---

### Post by esekyavuz on 2007-07-28
Yes! Thank you! It turns out ot be a slide switch on the left side of the computer.

---

### Post by noob12 on 2007-07-28
And for those who don't, the following should do it in software.  This assumes you have wlan0 as your wireless interface logical name.  Replace as appropriate

```
sudo iwconfig wlan0 txpower off
```

---

