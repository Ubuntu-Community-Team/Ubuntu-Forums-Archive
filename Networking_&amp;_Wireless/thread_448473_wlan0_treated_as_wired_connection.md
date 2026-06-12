---
title: "wlan0 treated as wired connection?"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by Ryutatsu on 2007-05-19
I recently upgraded to Feisty and when I did all of a sudden my wireless card at wlan0 was recognised as a wired connection. The card is a Netgear MA311 and I also have a wired NIC at eth1 that's working fine.

---

### Post by PhatBoy on 2007-06-17
I have the same issue. Worked perfectly under Edgy.

---

### Post by NilsE on 2007-06-17
I am not sure how to explain this but I think ethernet adapters are recognized and managed as eth which is correct.  Since 7.04 arrived it is recognizing internal wireless cards as eth also but managing them correctly as wireless. External cards are sometimes designated as wlan and managed as wireless.

The bottom line is that it may label a wireless as eth but it manages it as wireless. So the question is does the label (eth vs. wlan) really matter since is is more aesthetic than functional. 

Personally if it is wireless I would prefer it be labeled as such but using network manager roaming you never have to see that anyway.

---

### Post by kevdog on 2007-06-17
You can change the interface name back to wlan0 if you want (this is important if using ndiswrapper).  Edit with root permission the /etc/iftab file.  Find the interface name you want to change for example eth0 and change it to wlan0.  Reboot and you should be good to go.

---

### Post by PhatBoy on 2007-06-23
Got it working by blacklisting a few things:

Created file in /etc/modprobe.d

```
blacklist prism2_pci
blacklist hostap_pci
blacklist hostap
```

after seeing comments about the MA311 in  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

Now on to persuading WPA to work properly... for some reason I only have WEP as an option and only 1 network out of the 6 I can normally detect is showing (and its not my one).

---

### Post by plainstarchedtom on 2007-07-28
After having the same problem when upgrading from 6.06 Dapper to 6.10 Edgy, adding those three blacklist items worked for me also.  As a note, I added them to /etc/modprobe.d/blacklist (after first trying to edit /etc/modprobe.d and getting a directory listing, oops).  

Thanks for help!

---

