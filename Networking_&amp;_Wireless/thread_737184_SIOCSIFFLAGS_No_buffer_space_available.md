---
title: "SIOCSIFFLAGS: No buffer space available"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by tompickles on 2008-03-27
Fresh 7.10 install. Well, nearly. Updated all fine and dandy. Have a RT2500usb device, which connected fine. Until now :( Using the native driver - not ndiswrapper

Tired iwconfig which shows that the device is there and is named wlan0

sudo ifconfig wlan0 up - just produced ```
SIOCSIFFLAGS: No buffer space available
```

Help please! Don't know how to fix this issue,

---

### Post by tompickles on 2008-03-27
Just an update - erm, well booted into windows to post that post - which took flipping ages to get my wireless to work in windows - no surprise with windows and belkin. but anyway - back to ubuntu and it worked fine again. so, i guess this is solved?! ill wait until i reboot just to make sure before marking solved.

---

### Post by tompickles on 2008-03-28
rebooted this morning and the initial problem still applies. any hints?

---

### Post by tompickles on 2008-03-30
my "work-around" so to speak. Boot into Ubuntu - does wireless work ----- no :(. Rebot into XP. Wireless works. Reboot into Ubuntu - wireless works, as long as I select which network to use - despite it trying to connect to that one alrady (it will fail unless I click) :( any help? this iisnt an ideal solution.

---

### Post by tompickles on 2008-03-31
Does anybody have any idea? I would like to see ifI am the only one experianceing this with my hardware - Belkin USB wirless dongle F5D7050?

---

### Post by jaymac407 on 2008-04-01
I can confirm this bug is **still** an issue in Ubuntu 8.04.

I'm using a zd1211 wireless chipset, but.

This is unreliable and is causing really bad problems, this did not exist <Ubuntu 7.10.

---

### Post by tompickles on 2008-04-01
ok, thanks for the heads up - going to upgrade to 8.04 now - but downloading wireless cd as internet is still unreliable. really annoying!

---

