---
title: "ESSID in iwconfig won't stay set"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by Silox on 2006-09-04
When I try setting the essid on my wireless card using:
iwconfig wlan0 essid whatever
The essid won't stay set.  Whenever I try looking at it after configuring the essid it shows any/off.  
I am using ndiswrapper if that makes any type of difference.  
The drivers for ndiswrapper do seem to work because iwlist wlan0 scan works and shows broadcasting AP's in the area.

---

### Post by x64Jimbo on 2006-09-04
Try using NetworkManager to take care of your wifi connections. I haven't typed a wifi command in weeks.

---

### Post by Silox on 2006-09-04
It just keeps searching when its trying to aquire using network manager.

---

### Post by Thund3rstruck on 2006-10-29
Did you ever resolve this? I have the same issue in kubuntu 6.10, I must reset the ESSID every time the system boots. None of the network manager packages have worked in remembering the ESSID

---

### Post by x64Jimbo on 2006-10-30
As a silly hack to get around this, you could put a shell script in your Autostart directory that sets the essid each time your system starts up.

---

### Post by Thund3rstruck on 2006-10-30
Yea.. thats so weak, but I guess thats the only resolution to this issue

---

