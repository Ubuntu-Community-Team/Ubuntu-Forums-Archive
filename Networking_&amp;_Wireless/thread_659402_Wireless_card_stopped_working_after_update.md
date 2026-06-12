---
title: "Wireless card stopped working after update"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by dodgingspam on 2008-01-05
Hi,

My wireless card (Netgear WG511 v2) was working fine, but a week or so ago I saw that Ubuntu had some updates ready for install. I went ahead and installed them and logged out. After that my card stopped responding. I checked in hardware profile and I see it when I plug or unplug the card. Just now I am back home and am able to look into this issue. I checked to see if I needed to re-install the drivers with ndiswrapper but got a message that it is already installed. 

What do I do next? How do I bring my laptop back online?

Thanks.

---

### Post by carrett on 2008-01-05
Can you figure out which packages were updated?

---

### Post by dodgingspam on 2008-01-05
Unfortunately I can't remember what was updated. I assume it has something to do with the interface change for wireless networks. I got it to work by going through the following steps:
[PHP]
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
[/PHP]

On line 2 the first light comes on and on the last line the second one starts blinking. However, after I shut-down my laptop and restarted it later, I had to go through these steps again...

:confused:

---

### Post by dodgingspam on 2008-01-06
Now, every time when I need to connect to Internet I have to first enter the following:[PHP]
sudo modprobe ndiswrapper
sudo ndiswrapper -m 
[/PHP] 
for my wireless card to kick in. Is there a way I can add these commands somewhere in order for it to connect automatically?

---

### Post by dodgingspam on 2008-01-12
Any ideas on how can I avoid typing this in every time in order to connect to Internet?

[PHP]sudo modprobe ndiswrapper
sudo ndiswrapper -m  [/PHP]

---

