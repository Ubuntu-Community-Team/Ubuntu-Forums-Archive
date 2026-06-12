---
title: "Linksys WPC54G ver.2 &amp; Live CD"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by mjblane on 2006-11-23
Hi,
I'm testing an old Dell Latitude with a DDrake live CD.

Everything seems to work, it even finds my Linksys PCMCIA WPC54G ver.2 card.
It shows that there is signal strength but does not allow me to connect to my home AP (non encrypted). Usually the SSID is turned off but is on for testing/configuring.

Is this just a problem with running from live cd?

If I go ahead and install and it doesn't connect, I'll have no way of getting other drivers into the machine. (and I really don't want to reinstall xp)

Any thoughts on where to look?

I have DDrake on my desktop machine and all's well; if I can get it to be happy on that old laptop that would be one less XP machine in the home.

Thanks for reading and any help,
Michael

---

### Post by x64Jimbo on 2006-11-23
Can you connect the machine with ethernet? You can install the system and then get new drivers if you can connect with LAN.

---

### Post by mjblane on 2006-11-23
No, no built in modem, no built in ethernet.
If it's just a hic-up from the live CD, I can install and configure. If it's more than that I'll be in trouble.
Maybe d/l needed drivers, burn to CD then copy to Laptop. Long way around.

mjb

---

### Post by x64Jimbo on 2006-11-24
Most things are not a hiccup on the liveCD. Download the drivers to your windows partition first, then use them from the liveCD, and if they work, give Ubuntu a shot.

---

### Post by mjblane on 2006-11-24
I'm gaining on it.
Wiped xp, installed DDrake.
Got wireless card to run . . . then rebooted.
I think I missed something about ndiswapper running on boot.

I'll look some more.

mjb

---

### Post by NetworkGuy on 2006-11-24
Don't worry about NDiswrapper.

I have the same card and what I do is to add a line to the /etc/modprobe.d/options file.

options acx firmware_ver=1.2.1.34

The latest version of firmware for the acx chipset doesn't work correctly.  Making the change above tells the kernel to boot the correct version every time.

I don't think you can do this using the LiveCD however.

---

### Post by x64Jimbo on 2006-11-25
Any particular reason you went with Dapper rather than Edgy (the current version)?

---

### Post by mjblane on 2006-11-25
I had a Dapper CD that I had burnt a month or so ago for some other testing.

If I re-install using Edgy will it recognize my WPC54G ver.2 card without my intervention or will I need to do this installing/configuring manually anyway?

I'll d/l Edgy and keep it on hand, just in case.

mjb

---

### Post by mjblane on 2006-11-25
OK, I've now installed Edgy and will try this first.
Thanks,
mjb


> **NetworkGuy said:**
> Don't worry about NDiswrapper.

I have the same card and what I do is to add a line to the /etc/modprobe.d/options file.

options acx firmware_ver=1.2.1.34

The latest version of firmware for the acx chipset doesn't work correctly.  Making the change above tells the kernel to boot the correct version every time.

I don't think you can do this using the LiveCD however.

---

### Post by mjblane on 2006-11-25
Hi and thanks to all.

Edgy is installed on my 5 y/o Dell Latitude.
I used the options acx firmware_ver=1.2.1.34 addition to /etc/modprobe.d/options and all seems to be working OK.

Now I just need it to see the USB drive on my Dapper desktop machine that contains all the FLAC files.

Thanks again,
Michael

---

### Post by dmizer on 2006-11-25
> **mjblane said:**
> Now I just need it to see the USB drive on my Dapper desktop machine that contains all the FLAC files.

Thanks again,
Michael

share the drive using nfs (fourth link in my sig).  much easier than trying to tackle samba.

---

### Post by mjblane on 2006-11-28
Thanks,
I just got home from work and gave it a quick look, doesn't look too difficult. I'll try it soon.

The drive that I need to share is an external USB, /media/usbdisk by default; should I make a regular type of mount point and go from there?

Later,
mjb

---

