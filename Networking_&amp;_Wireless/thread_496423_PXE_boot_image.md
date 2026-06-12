---
title: "PXE boot image"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by szquirrel on 2007-07-09
I manage a small computer lab made up almost entirely of old, donated PCs. About six months ago I turned it into a thin-client network using Ubuntu and the results have been nothing less than spectacular.

Fortunately I was lucky, as it turned out most of the workstations supported PXE boot. But with recent donations I haven't been as lucky. I've got several old PCs that I would love to deploy as thin clients but they don't have built-in PXE.

I'm thinking I can't be the first person to have this problem. Does anyone know of a boot image that can autodetect the network card and act as a PXE bootloader? Yes, I know about Rom-o-Matic, but it requires me to know the NIC hardware (not always easy) and make a different boot image for each client.

Or, alternately, is there an easy way to find out what NIC I've got? All of these machines have 128 MB of RAM or less, so booting from the Ubuntu Live CD is not an option.

Sorry, I know this is not strictly an Ubuntu support question, though it does impact the quality of my Ubuntu experience. Thanks for your help.

---

### Post by szquirrel on 2007-07-09
Right, [I'm an idiot]("http://thinstation.sourceforge.net/wiki/index.php/ThIndex").

After spending I don't want to say how long searching for the answer, of course I find it just minutes after calling for help. I'll let y'all know how it goes. Thanks!

---

### Post by szquirrel on 2007-07-10
I ended up using the [All-drivers Etherboot floppy]("http://etherboot.anadex.de/") which does exactly what I wanted. To make the floppy I used DskImage which I got from [this page]("http://www.fdos.org/ripcord/rawrite/") (DskImage worked great under WinXP).

---

