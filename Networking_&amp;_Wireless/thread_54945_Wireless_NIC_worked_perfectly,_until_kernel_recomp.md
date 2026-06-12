---
title: "Wireless NIC worked perfectly, until kernel recompilation"
date: 2005-08-06
forum: Networking &amp; Wireless
---

### Post by eepiccolo on 2005-08-06
OK, I'm hoping this won't be a difficult problem.

When I installed Kubuntu, the installer detected my wireless network PCI card flawlessly as wlan0, and the network work perfectly after entering the ESSID of my network.

However, because I am a curious fellow and am trying to learn all about Linux, I recompiled the kernel, selecting the P4 architecture to better optimize the kernel for my machine.  

As you may have guessed from the subject, the network connection does not work with the recompiled kernel.  However, if I boot into the original kernel, the connection works.

So, does anybody know what might be happening, and how I can get the connection working in the new kernel?  

Or did I miss a setting for the kernel, and I need to recompile the kernel with different settings?  And any suggestion to what those settings might be?

Thanks very much for any help

EDIT: and in case it's useful information, the NIC is a Netgear 54Mbps card, model number WG311.  However, I remember the installer saying the card was Texas Instruments.  I suppose TI is the chipset.

---

### Post by az on 2005-08-06
You need the acx_pci module.  Where did you get your source, and did you use the configuration of the stock kernel?

---

### Post by eepiccolo on 2005-08-06
I used the ubuntu kernel, obtained by using apt-get linux-tree.  I followed the HOWTO compile kernel instructions found here: [http://www.ubuntuforums.org/showthread.php?t=43065&page=1&pp=10&highlight=linux-tree](http://www.ubuntuforums.org/showthread.php?t=43065&page=1&pp=10&highlight=linux-tree)
Using xconfig, I guess it started with the default options, but I changed the CPU architecture and removed some things I knew I wouldn't need, like ISA support.  I'm fairly sure I didn't touch the network compile settings, unless I touched something by accident.

And now for my noobness to really show, how do I check to see if I have the acx_pci module, and can I add it without recompiling the kernel in case I don't have it?

---

### Post by eepiccolo on 2005-08-09
*bump*

Any suggestion to fix my problem?

---

### Post by tymek666 on 2005-08-12
I have similar problem, but i've compiled kernel from downloaded from kernel.org, 2.6.12.4 i think. I need new kernel cause 2.6.10 doesn't fully support my ati-based motheboard.
BTW did you try to use yours oldconfig? Maybe it helps, i'm going to try this tommorow.

---

### Post by tymek666 on 2005-08-13
I don't know why new kernel doesn't load acx_pci module. I'm sure I picked this module during kernel configuration. However lspci find and recognize my card propertly, but of course there's no acx_pci module in lsmod listing :(

---

### Post by tymek666 on 2005-08-13
After compiling 2.6.11 kernel from ubuntu reps i have module loaded, but wfif card is stiil not working :( Any ideas?

---

