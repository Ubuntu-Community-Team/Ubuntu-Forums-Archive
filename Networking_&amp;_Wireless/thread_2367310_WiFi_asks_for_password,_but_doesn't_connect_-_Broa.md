---
title: "WiFi asks for password, but doesn't connect - Broadcomm B43"
date: 2017-07-28
forum: Networking &amp; Wireless
---

### Post by conantroutman2 on 2017-07-28
Hi, 

I've just installed the newest Lubuntu on an old Laptop and at first I couldn't activate Wifi. I've followed the steps on the sticky guide and it appears the drivers are installed correctly and the Wifi card is active now - but when I try to connect to my network, it asks for the password repeatedly, yet it doesn't connect successfully. 

I'v attached the wireless info script results.

Edit:
I can't see the attachment. 
Anyway, here's the link to the pastebin:
[http://paste.ubuntu.com/25191367/](http://paste.ubuntu.com/25191367/)

---

### Post by oldos2er on 2017-07-28
No attachment? Please use the paper clip icon in the advanced editor to attach the file, thanks.

---

### Post by conantroutman2 on 2017-07-28
I've tried that, but it says: 

"The following errors occurred:

wireless-info.txt: Your file of 34.1 KB bytes exceeds the forum's limit of 19.5 KB for this filetype."

---

### Post by oldos2er on 2017-07-28
Ok. Pastebin is fine, which I see you've posted.

---

### Post by praseodym on 2017-07-28
Does the router use a MAC address filter? If yes, deactivate it (check the manual)

---

### Post by QIII on 2017-07-28
Let me tag something on to praseodym's post:

If you are worried about turning off MAC filtering, don't be.  MAC filtering is a tool to manage your network, but it is NOT a good security feature.  MAC addresses are sent in the clear to your router.  They can be sniffed and then spoofed.  They are completely ineffective in and of themselves in protecting you from intrusion.  All it takes to defeat MAC address filters is Kali Linux, Wireshark and a few seconds.  Once an intruder has that, the current device can be deassociated, the MAC spoofed and their device connected.  Some crackers find MAC filtering to be an irresistable plaything and will hack just for the fun of it when they find a router using MAC filtering.  Your neighbor may be doing it to you on a regular basis with a simple script and a list of sniffed MACs.

Using WPA-PSK2 with a strong passphrase is the best first line of defense for wireless security.  That is a process that does not occur in the clear, so it is not so easy to hack.

---

### Post by conantroutman2 on 2017-07-28
First, thank you all for helping! 
While checking the router for the MAC filter, I found the issue - the wireless settings for the 2.4 ghz channel were set to n only, I changed them to g/n and now it works fine.

---

