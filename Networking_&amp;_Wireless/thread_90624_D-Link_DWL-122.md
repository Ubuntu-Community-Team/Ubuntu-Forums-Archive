---
title: "D-Link DWL-122"
date: 2005-11-15
forum: Networking &amp; Wireless
---

### Post by wlankatt on 2005-11-15
I'm trying to make my D-Link DWL-122 Wireless USP Adapter to work with Ubuntu, but I can't figure out how. Can anyone help me? :confused:

---

### Post by pholi90 on 2005-11-15
I'v get the exact same problem;) ! Have tyed out Ndiswrapper program but it dosent work at all... And the guide I found hare at this forum  did'nt help me too much... (I'm cind of a noob...) Good luck!

---

### Post by az on 2005-11-15
[http://bugzilla.ubuntu.com/show_bug.cgi?id=15346](http://bugzilla.ubuntu.com/show_bug.cgi?id=15346)

It is supposed to work out of the box once you install linux-wlan-ng but does not for me.  I have to use a script detailed in that bug report.  Using that script, the device is more reliable in linux than in windows.

Please add to the bug report as well as you can.

---

### Post by ali780 on 2007-10-25
I have the same problem!

---

### Post by markschu on 2007-10-25
me too

---

### Post by isparkes on 2007-11-01
It worked right out of the box for me - I should note that I use an Open WiLAN (no encryption). I am writing this using the live CD, with nothing special installed and no manual setup performed.

---

### Post by markschu on 2007-11-02
The problem for me disappeared after removing a "Blacklist rt2500" line. And using the "RUtilT WLAn manager"

---

### Post by anunn2001 on 2007-11-02
To get it to work for me I had to install linux-wlan-ng and then add the following lines to the /etc/network/interfaces file:

iface wlan0 inet dhcp
wireless_essid MYESSID             (the essid of my router)
wireless_key MyWirelessKey     (MyWirelessKey is my router WEP key)

I can only get WEP encryption to work

---

