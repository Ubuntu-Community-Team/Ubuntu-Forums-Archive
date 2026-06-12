---
title: "dell wireless WLAN 1350 WLAN Mini-PCI card supported?"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by grandpa2390 on 2007-07-07
is this card supported for wireless

---

### Post by grandpa2390 on 2007-07-07
can somebody walk me through the set up of a wireless ntwork on this card

---

### Post by Swab on 2007-07-07
I think [this]("http://ubuntuforums.org/showthread.php?t=297092") might work for you.  Should work for your 1350.

---

### Post by grandpa2390 on 2007-07-07
i don't know how to code

---

### Post by DFLiddle on 2007-07-27
Take courage, grandpa2390 — I just opened a terminal today on my Dell Latitude D600, followed the instructions, and now I'm in business with wireless. I don't understand everything that each command did, but I know that it worked.

---

### Post by kevdog on 2007-07-27
I think  off the top of my head the 1350 is a Broadcom chipset.  To confirm this, please at the command prompt type the following commands and cut and paste output:

lspci -nn
lshw -C network

Thanks.

---

### Post by nookatee on 2008-03-22
I tried running the howto, but I was unsuccessful.

everything seemed to work ok - no unexpected messages - but still no wireless.

I'm running Ubuntu 7.10 on a D600.
I used the R140745.EXE driver instead of the one outlined in the how-to (that's the driver i used when i was running windows).

I wanted to ask for some help under the how-tow thread, but I wasn't too sure which the "relevant rows" of the log files indicated would be. for dmesg, I ran: dmesg | grep eth0, but I don't know if that's too limitiing.

Also, when i run 'iwconfig eth0' this is the output I get (both before and after I ran the how-to):
"no wireless extensions."

any help would be greatly appreciated. I'm so close to being Windows free!!

---

