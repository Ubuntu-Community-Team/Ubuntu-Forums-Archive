---
title: "Linksys wusb11v4 working but"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by tech.roberts on 2007-03-02
OS Ubuntu 6.10 Edgy Eft - Linksys USB adapter WUSB11 v4

I have the hardware setup and working well using ndiswrapper.  However, there is a bit of a quirk when I first start the system.  The wireless interface does not associate with the access point and become usable until I enter a terminal and issue the command “sudo iwconfig wlan0 key open s:xxxxxx”  where xxxxxx is my key.   I have entered this command in my interfaces file as “wireless-key open s:xxxxxx” but the wireless network still does not associate on startup.    I have also noticed that I must wait at least 2 minutes after I arrive at the desktop before the command will cause the access point to show up as associated and become usable.  If I wait and do not issue the command the access point never associates and my patience times out.  This behavior has been consistent since I installed the USB adapter.  More of an annoyance than a show stopper as I could script it away I suppose.  Has anyone experienced this?

---

### Post by tech.roberts on 2007-03-05
I followed the suggestion in the thread  "[COLOR="DarkRed"]Linksys WUSB11v4 ndiswrapper[/COLOR]" and used wireless-key1 ...... and wireless-key ...... in my interfaces file.  The interface comes up fine now.  I did have to use both commands instead of just substituting  wireless-key1 for wireless-key.

---

