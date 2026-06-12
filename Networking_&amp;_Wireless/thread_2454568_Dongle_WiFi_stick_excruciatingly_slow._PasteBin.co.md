---
title: "Dongle WiFi stick excruciatingly slow. PasteBin.com diagnose"
date: 2020-12-02
forum: Networking &amp; Wireless
---

### Post by ggrillea on 2020-12-02
Hi I have D-Link wifi stick.
I was following [https://ubuntuforums.org/showthread.php?t=2404659](https://ubuntuforums.org/showthread.php?t=2404659)
 Diagnose result posted here 
[https://pastebin.com/NBzg9Kzr](https://pastebin.com/NBzg9Kzr)

Can anybody suggest a way to please speed things up a bit?


Thank You

---

### Post by wildmanne39 on 2020-12-02
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by CelticWarrior on 2020-12-02
The WiFi dongle is old but its age shouldn't be a problem.

There are two issues with the router it is connecting to: Mixed mode and TKIP.
Please change the settings to WPA2-AES.

---

### Post by ggrillea on 2020-12-02
@CelticWarrior. thanks for the reply. I'm a beginner/learner. Do I have to change the router settings? Or is this something I can change from the terminal?
Could you please give me more details on how to do this?

---

### Post by CelticWarrior on 2020-12-02
Yes, you need to change the router settings and perhaps upgrade to a proper one. TKIP has been deemed unsafe and deprecated many years ago.

---

### Post by ggrillea on 2020-12-02
thanks for the advice on the router. I will have to look into it. I did manage to go in the router settings. But when I changed to WPA2 I lost the internet connection.

So I spent one hour with the CenturyLink provider here in the US... guess what their solution was: "Sir please hit the reset button at the bottom of your router".

So I am back to square one.

Anything else I can try while I wait on upgrading the router?

Thanks again

---

### Post by CelticWarrior on 2020-12-02
Yes, when you change any router settings you should 1) reboot the router (unplug and reconnect the power supply) and 2) at the client devices delete the previous connection profile and add it again (same name but different). That's all.

If you can enable WPA2 and AES (AKA CCMP) as the encryption type you can comfortably and rationally, rather than impulsively, study your options for a new router including the option to keep that one if it proves to be stable and reliable with the recommended WiFi settings.

---

### Post by ggrillea on 2020-12-02
I tried again to enable WPA2 and AES without crashing. I followed your protocol. It is working great and the connection is also faster now. 
Thanks for the guidance. :KS

---

### Post by chili555 on 2020-12-02
Awesome! Please use Thread Tools at the top to mark Solved. The searchers will appreciate it.

---

