---
title: "SAMBA printing not working :("
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by neptune on 2006-12-08
Hi,

I'm trying to share my printer through Ubuntu so the Windows computers can print to it.

I've followed the HowTo here: [http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10) and have file sharing working perfectly fine.

The Windows computers are not on the same domain or workgroup as configured in smb.conf, but thats not a problem for connecting to shared folders.

Now the printing issue:
First, there isn't a Linux driver for it (Dell 1100 Laser). I tried using the RAW mode in CUPS but when I type in *cupsaddsmb -a*, it says something to the effect of *no ppd file present*. 
Fine, so I'm now using the Samsung ML-1610 driver (some folks have said it works), and indeed it works fine printing from Linux.

On Windows computers, I can browse to the Ubuntu server and see the printer as a shared device. I can add it as well without any problems. Windows has drivers for Dell 1100 so I'm using them.
However, once its added, the status shows ***Access denied, unable to connect*** under Windows.

I'm pretty sure I've done things as outlined in the HowTo document but this doesn't seem to be working.

I'd appreciate any help on this issue. Its one of the last things I need to do to complete my SAMBA setup (final step is AV server).

Thanks!

---

### Post by mitch.c on 2006-12-08
Samba is a great thing once you get it configured properly. If you need file sharing that's great, but in my experience it's easier to print from Windows to Ubuntu over IPP. It's native to cups and Windows supports it.

If you want to give it a try, follow this:
[http://www.ubuntuforums.org/showpost.php?p=1561331&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1561331&postcount=2)

Use Samba for file sharing; Cups IPP for printing.

---

### Post by neptune on 2006-12-08
Wow what a simple fix.

Thanks bud! :)

---

