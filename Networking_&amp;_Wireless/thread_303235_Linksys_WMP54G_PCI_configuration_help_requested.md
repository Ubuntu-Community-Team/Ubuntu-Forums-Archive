---
title: "Linksys WMP54G PCI configuration help requested"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2006-11-19
Here's my terminal result for "lspci -n...Linksys WMP54G...Kubuntu Edgy LiveCD

00:00.0 0600: 1106:0691 (rev 42)
00:01.0 0604: 1106:8598
00:07.0 0601: 1106:0596 (rev 11)
00:07.1 0101: 1106:0571 (rev 06)
00:07.2 0c03: 1106:3038 (rev 05)
00:07.3 0600: 1106:3051 (rev 20)
00:0a.0 0200: 1113:1211 (rev 10)
00:0b.0 0401: 127a:4310
00:0b.1 0780: 127a:4311
00:0b.2 0980: 127a:4312
01:00.0 0300: 10de:002c (rev 15)


Running "lshw" from the terminal doesn't show the wireless card as a hardware device.

Does this help ID the pci card?

Thanks

---

### Post by DapperMe17 on 2006-11-20
Just an update...

I have switched the PCI card to another PCI slot, thinking that it was a bad slot. Unfortunately, the device not listed in the PCI device manager in the new slot(which has a working sound card).

I've come to the conclusion that the Linksys WMP54G is defective.

Although I am an enthusiastic newbie, I "really can" put two and two together:) If all the other PCI devices are listed in the Kubuntu device manager, it's obvious that the Linksys is the only card not listed, and thus, must be kapeeeeesh.

It's a Version 4 WMP54G.


Looks like I'll look into a replacement. If anyone can recommend one that will seem nicely with Xubuntu/Kubuntu(I have referenced the wireless Wiki), feel free to let me know.

Thanks mucho!

---

### Post by neveceral on 2006-11-20
wmp54g is not working from live cd, so install what you want (Kubuntu, Ubuntu or Xubuntu) and follow this HOWTO [http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)

---

### Post by DapperMe17 on 2006-11-20
Even if not even appearing as a PCI device in the Info Manager?

No disrespect to your fine tutorial, but are you certain this will work? That's alot to ask of a "lowly" newbie:o 

Because I have no internet on that machine, could I download the drivers to a USB drive on a Windows machine, then copy to Xubuntu machine, etc? 

Would it be any easier a task by using Dapper?

Thanks

---

