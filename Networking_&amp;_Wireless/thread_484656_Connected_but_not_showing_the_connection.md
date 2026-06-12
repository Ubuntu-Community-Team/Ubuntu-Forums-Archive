---
title: "Connected but not showing the connection"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by fuzzled on 2007-06-26
Well, I got my wireless card working, but something odd is occurring.  I am connected to my home network, the "iwlist scanning" command works and shows the network and all the information.  However, under the network manager in the system tray, it is not showing I am connected like it did when I was wired.  Is there anything to remedy this?  I've tried searching and have not come up with anything.  Any help would be greatly appreciated.


Additionally, is there some sort of graphical utility that shows all the local networks in the area with the ability to click a connection and connect, akin to XP?  The reason I ask is, this laptop is for my parents and I'd prefer some familiarity for them in the case that I am not around to help. Thanks again.

---

### Post by fuzzled on 2007-06-26
If it helps the laptop is a Dell Inspiron 1300


From the ndiswrapper site

Dell Wireless 1470 (802.11a/b/g) Dual-Band WLAN miniPCI Card

    *
      Chipset: Broadcom BCM4319 (rev 02)
    *
      pciid: 14e4:4319

---

### Post by Ayuthia on 2007-06-26
If you see an icon by the clock that looks like two computers, that is network manager.  If you left click on the icon, it will show you the possible connections (wired and wireless).

---

### Post by fuzzled on 2007-06-26
> **Ayuthia said:**
> If you see an icon by the clock that looks like two computers, that is network manager.  If you left click on the icon, it will show you the possible connections (wired and wireless).


That's the issue, the only thing showing up is manual configuration.  I am able to connect to the network but for some reason it's not being recognzed.  The network is also broadcasting the SSID as well, so that rules that out...

---

### Post by Ayuthia on 2007-06-26
I have not seen that option before.  I am curious if that is the same application that I am running.  Can you see if nm-applet is running?  Two ways to check:
1) System->Adminstration->System Monitor (Click on the Processes tab)
2) At the terminal, type 'ps -ef|grep nm-applet'

The | is pipe.  It usually lives above the \ on US keyboards..

---

### Post by fuzzled on 2007-06-26
> **Ayuthia said:**
> I have not seen that option before.  I am curious if that is the same application that I am running.  Can you see if nm-applet is running?  Two ways to check:
1) System->Adminstration->System Monitor (Click on the Processes tab)
2) At the terminal, type 'ps -ef|grep nm-applet'

The | is pipe.  It usually lives above the \ on US keyboards..
Yes, nm-applet is running, I made a mistake in referring to the option that was available, the edit reflects that.

---

### Post by fuzzled on 2007-06-26
bump for help..

---

### Post by Ylang on 2007-06-26
I have been experiencing the same problem, my wireless as been very sketchy lately. It will work for a time period, and then the wireless networks will dissapear from the options on the network settings. I have ndiswrapper installed and the only difference is that I cannot connect to my network when the option is not available.

---

### Post by fuzzled on 2007-06-28
bump

---

