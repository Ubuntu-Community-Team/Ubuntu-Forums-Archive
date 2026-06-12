---
title: "wireless lan question"
date: 2005-08-28
forum: Networking &amp; Wireless
---

### Post by linuxgrrl on 2005-08-28
hello, 
I am trying to get a microsoft mn-520 USB wireless lan adapter working.

My system seems to recognize it: lsusb gives "Bus 001 Device 004 ID 045E:006e" and the name of the adapter; doing "lsmod" causes my machine to mention a prism2 module which I gather has something to do with a wlan.

from reading other posts I guess the next step is "DHCP wlan0", however, this command returns "sit0: unknown hardware address type 776" and more errors after that.

despite  reading other posts/howtos, I just can't tell what to do next.  Do I need to install some "drivers" for this device [even tho' the kernel seems to see it just fine?]   I assume the answer is NOT ndiswrappers, since that software seems to support microsoft "cards" but I can find no mention of the USB device.

thanks,
Mary

---

### Post by blu.gecko on 2005-08-28
On the note of the HOWTO'S, have you installed ndiswrapper?
thats the 1st step. :???:

---

### Post by Kloaf222 on 2005-08-28
Well I have it installed, but I didnt think that it was needed with madwifi files...

---

### Post by linuxgrrl on 2005-08-29
It is indeed true that ndiswrapper is not needed for the USB device.  (some guides even recommend removing it if it's there, which I did).

I got the device working by a combination of the following:
1. install linux-wlan-ng packages from a cdrom (since I have no internet)
2. shut down any other network interfaces with "ifdown eth0" and "ifdown lo"
3. obtain the source tar.gz file for the linux-wlan-ng package, then unzip it to view the README file.
4. load the wlan-ng drivers following the USB-specific instructions in the README (scroll to the bottom of the README file, skipping all instructions except the USB-specific ones)
4.5  I might have done an "ifup wlan0" at some point along the line, though I'm not sure if that was necessary.
5.  type "sudo dhclient wlan0" from a command prompt.

That's what worked for me ... there's probably a more elegant way, but hopefully this will help someone else spend less time than I did.

---

