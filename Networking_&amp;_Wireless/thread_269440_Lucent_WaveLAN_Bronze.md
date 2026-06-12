---
title: "Lucent WaveLAN Bronze"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by mckemie on 2006-10-01
I was thrilled to find that the kernel in Dapper supports my Compaq Armada 7400/7800 USB controller.  Older 2.6 kernels have not, though the Compaq USB works well with all the 2.4 kernels.

However...... Dapper does not handle my Lucent WaveLAN Bronze wireless PCMCIA card.  The Bronze has worked well in numberous other laptops running 2.4 kernels.  Other Orinico type cards work fine with Dapper, just not the Bronze.  The Bronze is rather old and does not do 11mbps, only 2mbps I believe.  But, that's fast enough for me.

Does anyone know of this situation?  Or have suggestions on how to fix it?

I have a number of the 7400/7800 laptops and a number of the Bronze cards; I am running mostly Sarge, which handles both the USB and a wide variety of wireless cards.  But, I would really like to start upgrading to Dapper.

---

### Post by fistfullofroses on 2006-10-03
I am also using a Lucent WaveLAN Bronze card on PCMCIA. I run Xubuntu 6.06 on a Winbook SI. When I use the command lsmod it displays a list of running modules. The Hermes module which consists of orinoco and orinoco_cs is running, but for some reason the card is not listed as a network interface device. I have no clue what the problem is, but my card worked just fine in Slackware, and in Damn Small. It didn't work in Debian, or Xubuntu.

---

### Post by tturrisi on 2006-10-03
You may want to try an older version of the drivers, say orinoco_cs 13 or earlier.

---

### Post by mckemie on 2006-10-05
> **tturrisi said:**
> You may want to try an older version of the drivers, say orinoco_cs 13 or earlier.

Can you be specific as to how to install an earlier orinoco_cs?

---

### Post by tturrisi on 2006-10-05
It's been a while since I did that, what I did was this:
1. download the version I wanted.
2. as root make & build the drivers in some dir.
(below can be done via a root nautilus window)
3. as root backup the existing drivers.
4. as root replace the existing ones w/ the fresh built ones.
5. reboot.
6. view /var/dmesg to verify what driver version is loaded.

---

### Post by mckemie on 2008-01-29
I would still like to find a viable solution to this problem.  I don't really consider trying to run older versions "viable".  To reinterate: Somewhere along the way, support for the Wavelan Bronze card was dropped; back in maybe a few Ubuntu versions ago, they "just worked".  The Bronze version looks just like the Silver and Gold, but does only 2mbps.  I have a supply of these cards and they could be used in many situations.

---

