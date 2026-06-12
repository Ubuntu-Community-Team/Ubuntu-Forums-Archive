---
title: "Problems with broadcom wireless adapter..."
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by dramaticexit on 2007-02-28
Hi,

So I'm completely new to linux.  I've installed ubuntu edgy on a Dell Latitude D620 with the broadcom wireless card.  I followed the instructions here:

[http://www.ubuntuforums.org/showthread.php?t=190177](http://www.ubuntuforums.org/showthread.php?t=190177)

but I'm still having problems.  When I type 

lshw -C network

I get

*-network UNCLAIMED
     description: Network controller
     product: Broadcom Corporation
     vendor: Broadcom Corporation
     physical id: 0
     bus info: pci@0c:00.0
     version: 01
     width: 32 bits
     clock: 33MHz
     capabilities: bus_master cap_list
     resources: iomemory:dcffc000-dcffffff irq:3

I think I might be getting somewhere, because initially the message started "*-network DISABLED" but I'm really at a loss as to where to go from here.

The wireless card is also not showing up in the GUI network settings tool.

Any help would be greatly appreciated.

---

### Post by tgalati4 on 2007-03-01
I was under the impression that the 43xx driver is broken under Edgy.  Did you search the forums to verify this?

I think folks have had luck using 43xx under Dapper Drake 6.06 or using ndiswrapper under Edgy.

You have some work to do.

Good luck and welcome to the community.

---

### Post by dramaticexit on 2007-03-02
Yeah, I replaced the 43xx with ndiswrapper.  It seemed to me like it installed correctly, but the wireless card isn't showing up in the network tool.  I didn't notice how many people seem te be having similar problems in the forums, though...I'll look around.

Thanks.

---

### Post by DarkN00b on 2007-03-02
I got my Broadcom 4318 based card working here: [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

It worked perfectly and I am posting with it now. Use the driver named [COLOR="Red"]wl_apsta.o[/COLOR] in the second step and follow the rest of the HOWTO.

**It is important to read all the instructions!** You shouldn't have to install network-manager though. just stop after step 4 like the article cays and it should work just fine. You may have to eject the card and then plug it in again for it to work. I have found that I have to insert my card after I boot into Ubuntu for it to work.

Hope this helps...

---

### Post by tgalati4 on 2007-03-03
Did you properly blacklist the existing 43xx driver?  Failure to do so will leave the original (nonworking) driver in place and ndiswrapper will not complain about it.  (But it won't work either with the 43xx already installed.)

Good luck!

---

