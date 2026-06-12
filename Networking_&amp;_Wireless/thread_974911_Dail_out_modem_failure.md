---
title: "Dail out modem failure"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by garydem on 2008-11-07
I am having a problem dialing out on an analog modem.  My system is a dual boot computer with Vista and Ubuntu 8.10.  The analog modem is a US Robotics Sportster, and the ISP is ISP.com.

I can dial out fine using Vista but when I try with Ubuntu loaded it fails.  I am using Gnome PPP and KPPP as the dialer and both programs fail.  The system dials out and carrier is detected, however the calls immediately drop.  I would appreciate any help on fixing this issue.


Gary

---

### Post by GuyK on 2008-12-31
I'm having the same problem and I have just seen a later posting with the same problem. Seems as though some answers should be forthcoming. Keep me in mind if help comes your way.

Guy K

---

### Post by sonu 1807 on 2008-12-31
I am able to connect to internet with an analog modem using sudo wvdial command but i have not got Gnome-PPP to work. The log says " check your permission" in Gnome-PPP. It is clear that your modem is being identified. May be you should try sudo wvdial. In terminal, you will be able to see what's wrong if the connection fails

---

### Post by cebobbitt on 2009-01-02
Have you tried pppconfig? Its a cli program, but very good and powerful. You must be root to use it, I hope this helps...hee hee Yepper!!

---

### Post by ieee488 on 2009-01-02
[https://wiki.ubuntu.com/SettingUpModems](https://wiki.ubuntu.com/SettingUpModems)

---

