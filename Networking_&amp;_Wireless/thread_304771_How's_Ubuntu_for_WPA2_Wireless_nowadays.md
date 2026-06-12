---
title: "How's Ubuntu for WPA2 Wireless nowadays?"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by sulu on 2006-11-22
Hey there,


It was about 7 months ago when i first heard about Ubunt and tried it out, back in the day I was stunned how well it was working and how easy however despite huge efforts I never managed to get Ubuntu to support WPA2 on my Computers. Wpa1 no problem. WPA2 AES only no chance. Since im quite keen on my WPA2 connection tho, I sadly had to switch back to Windoze.

How's  it looking for that nowadays? I've got a Notebook here with a Intel 2200BG Wlan Adapter and a PC with a RalinkRT2500. 
What are the chances you presume, to get that running with WPA2 AES ONLY on the newest stable Ubuntu?

Thanks for your replies.

---

### Post by wieman01 on 2006-11-23
As for IPW2200, no problem. RT2500 only if you install your wireless card using "ndiswrapper" and the latest(!) Windows driver. The native RTxxxx drivers are in a very early stage & fairly unreliable as far as encryption is concerned. 

I have got WPA2 working (AES, PSK) with my IPW2200 & Linksys WUSB54G (Ralink chipset with "ndiswrapper") & have created a howto a while ago. Check it out:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

Post there if you need help.

---

