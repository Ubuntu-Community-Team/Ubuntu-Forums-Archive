---
title: "modprobe ndiswrapper makes system freeze"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by grossespinne on 2007-06-24
Hi! I have installed Ubuntu 7.04 (kernel version: 2.6.20-15 generic) and ndiswrapper 1.47 in order to use my usb wlan adapter (SMC SMCWUSB-G EU EZ, its identifier is 083A:4505). I am using the driver that came on its CD (which is the same suggested by the list on the ndiswrapper site). 
I think ndiswrapper manages to see the card:
```

# ndiswrapper -l 
smcwgu: driver installed 
device (083A:4505) present

```

But when I type the command 
```

modprobe ndiswrapper

```

the whole system feezes and only hardware reset helps.
Do you have any idea what the problem can be?

TIA

---

### Post by spd106 on 2007-07-05
Perhaps try downloading the newer 2.6.20-16 kernel and have a go with that one instead. If you can get a wired connection temporarily or maybe download the linux-image-2.6.20-16-generic and corresponding kernel headers deb files through another PC.

---

### Post by dinub1 on 2007-11-26
> **spd106 said:**
> Perhaps try downloading the newer 2.6.20-16 kernel and have a go with that one instead. If you can get a wired connection temporarily or maybe download the linux-image-2.6.20-16-generic and corresponding kernel headers deb files through another PC.

That is not it. I have the newest 2.6.22.14 kernel and I have the same freezing problem with the Dlink DWA-642 PCMCIA card. Any other ideas :) ?

---

### Post by zeesson on 2008-03-22
I had the exact same problem and then  I installed Linux Mint 4.0 which is another distro that has ndiswrapper preinstalled and I still couldnt get it to work so i ended up using madwifi.  I wrote a HOW TO: you can check it out [here]("http://ubuntuforums.org/showthread.php?t=718244")

---

### Post by anonymousphrase on 2008-07-03
```

# ndiswrapper -l 
smcwgu: driver installed 
device (083A:4505) present

```

But when I type the command 
```

modprobe ndiswrapper

```

the whole system feezes and only hardware reset helps.
Do you have any idea what the problem can be?

TIA[/QUOTE]

Had the same problem (using kernel version 2.6.24-19)

Solved by removing installed drivers (in this case "ndiswrapper -r smcwgu").
Then added module ("modprobe ndiswrapper").
Finally installed the drivers in ndiswrapper ("ndiswrapper -i smcwgu").

---

### Post by anonymousphrase on 2008-07-03
> 
```

# ndiswrapper -l 
smcwgu: driver installed 
device (083A:4505) present

```

But when I type the command 
```

modprobe ndiswrapper

```

the whole system feezes and only hardware reset helps.
Do you have any idea what the problem can be?

TIA

Had the same problem (using kernel version 2.6.24-19)

Solved by removing installed drivers (in this case "ndiswrapper -r smcwgu").
Then added module ("modprobe ndiswrapper").
Finally installed the drivers in ndiswrapper ("ndiswrapper -i smcwgu").

Why this works I have no idea.

---

