---
title: "PXE Netboot Ubuntu"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by WitchCraft on 2010-03-30
Question: 
I want to install Ubuntu over a network.
I already did that once, but I have a few questions:

The last time I did it like described here:
[http://www.lockstockmods.net/2008/04/07/pxe-install-ubuntu-via-windows/](http://www.lockstockmods.net/2008/04/07/pxe-install-ubuntu-via-windows/)

I enabled PXE netboot in the target-computer BIOS, then I used tftp server on Windows XP (didn't work on Vista), to load Ubuntu on the other computer. Then it installed over the network (I had to attach monitor and keyboard)

Now I want to install again, but from Ubuntu.
I found this guide here:
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
and this one, which I personally find better:
[https://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](https://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)

I'm now a bit confused/annoyed, as they both make entries in the DHCP configuration and use a DHCP server on the server computer. 
My problem with this is I have my netgear router as DHCP server, and neither do I need nor want another DHCP server in my network.
And there certainly was no DHCP server installed on windows, so I think that is utterly unnecessary.

My question now: is it really necessary to install the DHCP server?
Or can I just skip this, and install the TFTP server?

And another thing that annoyed me:
Is there no way to do the install process without attaching a monitor/keyboard to the target computer ? IMHO, it should be possible to do this via SSH, shouldn't it ?

I really don't want to attach a monitor and a keyboard, just to remove them again later...


**Edit/PS:** BTW, is it possible to change the BIOS PXE settings over the network, so I don't need to attach a monitor to do that...

Additional Links:
[http://syslinux.zytor.com/wiki/index.php/PXELINUX](http://syslinux.zytor.com/wiki/index.php/PXELINUX)
[http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/](http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/)

---

### Post by WitchCraft on 2010-04-01
bump.

---

### Post by WitchCraft on 2010-05-15
bump. That's not an april fool.

---

