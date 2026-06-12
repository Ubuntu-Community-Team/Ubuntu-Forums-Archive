---
title: "Ethernet working but wireless doesn't Ubuntu 14.04.5"
date: 2017-09-13
forum: Networking &amp; Wireless
---

### Post by qwertyforever on 2017-09-13
Hi,

I'm currently running Ubuntu 14.04.5 and am trying to get a wireless connection. I'm stuck on 14.04 because my project requires it. My wireless card is an Intel AC 3165 + bluetooth. I did try getting the firmware, but it seems to already have been installed to /lib/firmware/. I have tried a lot of other things like pulling the HWE stack (whatever that means), upgrading my kernel to 4.8 (not sure if I'm required to remove my 4.4 kernel for that) ,downloading the Intel connection manager and finally screwing over my whole internet connection and having to restore Ubuntu. I'm not sure what to try anymore.

I have attached my wireless-info.txt file at [http://paste.ubuntu.com/25527090/](http://paste.ubuntu.com/25527090/)
Please help.
Thank you very much.

EDIT:
My wifi card is an Intel AC 3168. Apologies on the matter.

---

### Post by chili555 on 2017-09-13
Please see: [https://askubuntu.com/questions/868075/how-to-get-intel-dual-band-wireless-ac-3168-work-on-ubuntu-16-04](https://askubuntu.com/questions/868075/how-to-get-intel-dual-band-wireless-ac-3168-work-on-ubuntu-16-04)

Please note that you have the same 8086:24fb device.> Network controller [0280]: Intel Corporation Device [8086:24fb] (rev 10)
	Subsystem: Intel Corporation Device [8086:2110]

---

### Post by qwertyforever on 2017-09-13
Hi, Thanks a lot for pointing that out.
I have revised my post. However after more searching, I found that 14.04 might no longer be feasible for running the firmware for this card. I shall pursue a different course of action for my project.
Thank you all very much.

---

