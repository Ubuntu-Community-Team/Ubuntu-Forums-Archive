---
title: "Lenovo P1 total wireless failure in 20.04"
date: 2020-12-08
forum: Networking &amp; Wireless
---

### Post by perlyking on 2020-12-08
Hi,

I have a first generation Lenovo P1 which has been running Kubuntu 20.04 since July. On Friday WiFi and Bluetooth were both working, but having not used the laptop over the weekend, when I opened it on Monday morning neither WiFi nor Bluetooth was working. The controls to turn them on have also vanished.

I can boot into Windows 10 and the problem is the same there. Both OSes are fully up to date.

The last entry in [FONT=courier new]/var/log/apt/history.log[/FONT] is:


```

Start-Date: 2020-12-03  17:03:22
Commandline: packagekit role='update-packages'
Requested-By: jim (1000)
Upgrade: libefivar1:amd64 (37-2ubuntu2.1, 37-2ubuntu2.2), xserver-common:amd64 (2:1.20.8-2ubuntu2.4, 2:1.20.8-2ubuntu2.6), xserver-xorg-core:amd64 (2:1.20.8-2ubuntu2.4, 2:1.20.8-2ubuntu2.6), libefiboot1:amd64 (37-2ubuntu2.1, 37-2ubuntu2.2), xserver-xorg-legacy:amd64 (2:1.20.8-2ubuntu2.4, 2:1.20.8-2ubuntu2.6)
End-Date: 2020-12-03  17:03:25

```

Could this be related? I think wireless was still working after that time on Friday and I didn't reboot between then and Monday.

The output of the wireless-info script is at [https://paste.ubuntu.com/p/RYwyjJkqpb/](https://paste.ubuntu.com/p/RYwyjJkqpb/).

Thanks very much for any help!

Jim

---

### Post by CelticWarrior on 2020-12-08
> [COLOR=#000000]I can boot into Windows 10 and the problem is the same there. [/COLOR]
The above always means hardware problem. It's either disabled in the firmware (BIOS or UEFI) or it's now defective.

---

### Post by Autodave on 2020-12-08
One easy thing to try: does this laptop have an easily removable battery?  If so, disconnect EVERY cable from machine and remove battery.  Wait 10 minutes and reinstall battery.  Hookup power cable and power up and see if it is now working.

---

### Post by perlyking on 2020-12-09
I was afraid of that :-( I can't find anything that looks likely in the BIOS settings, so I guess it's screwdriver time!

Thanks.

Jim

PS: This was a reply to CelticWarrior.

---

### Post by perlyking on 2020-12-09
> **Autodave said:**
> One easy thing to try: does this laptop have an easily removable battery?  If so, disconnect EVERY cable from machine and remove battery.  Wait 10 minutes and reinstall battery.  Hookup power cable and power up and see if it is now working.
No, the battery is internal only. As I said in my reply to CelticWarrior, it looks like it's screwdriver time; I'll see if anything looks loose, and try disconnecting the battery as you suggest.

Thanks!

Jim

---

### Post by perlyking on 2020-12-09
> **perlyking said:**
> No, the battery is internal only. As I said in my reply to CelticWarrior, it looks like it's screwdriver time; I'll see if anything looks loose, and try disconnecting the battery as you suggest.

Thanks!

Jim
Disconnecting and reconnecting the battery seems to have done the trick.

Thank you Autodave!

Jim
(posting via WiFi)

---

### Post by perlyking on 2020-12-10
UPDATE

Last night's fix worked for about 10 minutes :-(

I spent all day today working with a wired network connection, and that disconnected for a few seconds every few minutes (fortunately not long enough to kill a Citrix connection, which would have been even more annoying!)

This evening I booted into Windows for one last go, and found a Lenovo firmware update waiting. Since installing that... well, so far so good! :-\"

---

