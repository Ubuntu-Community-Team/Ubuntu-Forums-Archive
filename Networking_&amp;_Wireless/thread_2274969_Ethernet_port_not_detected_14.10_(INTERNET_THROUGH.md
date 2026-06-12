---
title: "Ethernet port not detected 14.10 (INTERNET THROUGH TETHERING)"
date: 2015-04-23
forum: Networking &amp; Wireless
---

### Post by manny9 on 2015-04-23
Ok so i am using tethering from my phone to get on the internet as the port wont work,it shows activity on bootup(the orange blinking light) then as soon as ubuntu boots, -disconnected, you are offline, i have looked at other forumns nm-tools alot of stuff nothing has worked so far,maybe someone can help me troubleshoot the port as i know nothing about troubleshooting,on ubuntu, please help me out it was working yesterday..maybe it got disabled or something?

---

### Post by manny9 on 2015-04-23
can anyone help me out please , Bump!

whats happend is that my ethernet wire is in the computer but the computer is not detecting it,no activity lights,when ubuntu boots,it blinks orange when the computer button is turned on as soon as i sign in says disconnected, your are offline

---

### Post by michi1983 on 2015-04-24
In the forum overview there are 2 sticky posts on top. One says: **[Before posting in Networking & Wireless]("http://ubuntuforums.org/showthread.php?t=370108")**
Please provide that information and it will be easier to help you.

---

### Post by manny9 on 2015-04-24
I don't have a wireless problem i have a wired port problem,that did not help.. on past post about the same thing people are asked to post nm-tool results here are mine

NetworkManager Tool

State: connected (global)

- Device: usb0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        4E:96:E6:6B:D8:57

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.154
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        BC:5F:F4:F1:0F:B7

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

These results are while tethering from my phone because i cannot connect to internet by other means

---

