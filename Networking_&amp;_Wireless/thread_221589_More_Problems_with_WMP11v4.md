---
title: "More Problems with WMP11v4"
date: 2006-07-23
forum: Networking &amp; Wireless
---

### Post by SargentFuzz on 2006-07-23
I've just begun my excursion into Linux, and so far have been amazed by the power and usability of the OS, with few exceptions, the main one being Wireless Internet. I have read many a thread about people's problems with the WMP11v4 Linksys card, and have yet to get mine to work in Dapper (it works fine in XP). I have used ndiswrapper to attach the Windows driver to it, lsipnds.inf, and ndiswrapper -l states that driver and hardware are both present. modprobe ndiswrapper and then ndiswrapper -n  gives me the following: "modprobe config already contains alias directive," but then iwconfig gives me no wireless extensions on any of the options, lo eth0 and sit0. The WMP11v4 card is also not recognized under System->Administration->Networking, though does appear in the device manager. I have searched all over the internet for several hours, and am wondering if anyone could give me a hand.

---

### Post by SargentFuzz on 2006-07-23
If it helps, here is what I get in lspci:

0000:00:09.0 Ethernet controller: Linksys, A Division of Cisco Systems WMP11v4 802.11b PCI card

---

### Post by SargentFuzz on 2006-07-23
I think the problem may be with the 32-bit drivers on my 64-bit processor, but I'd appreciate some reassurance, and possibly a link to any 64-bit drivers...

---

### Post by SargentFuzz on 2006-07-24
I have found several places that say Linksys' drivers work fine on 64-bit systems, and I found one tutorial that looked promising, only it used the command "make" which is not recognized as a command in my terminal. I think I may have a bigger problem than just my wireless card... I'd appreciate any advice...

---

