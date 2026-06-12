---
title: "Screen Resolution Problem U8.10"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by milkolate on 2008-12-04
Hello everyone!

I just installed U8.10 in my organization's computer. But the maximum resolution is only up to 800x600. We don't have internet access in that area so I need to fix it offline. There is a pop-up window that showed proprietary drivers (nvidia). But since I don't have internet connection there, I can't download them.

2 Questions:
1. Does that mean that my video card is nvidia?
2. How do I get a driver without having to connect the PC directly to the internet? Can I download it in a separate computer then just transfer the file to the one with Ubuntu installed?

Thanks for the help

---

### Post by DieB on 2008-12-04
to 1: si - yes - da - your feelings were right

to 2: yes there is that ability - even in synaptic.

simply marke the packeges to be installedand then go to "file"-create a skript for download ( not using english version of ubuntu). after that use the skript to donload fil (it should have a *.deb - ending). this file u then transfer to your machine, double-click it and   it would prompt u for installation.

hope i had been a help

---

### Post by eternalnewbee on 2008-12-04
> to 2: yes there is that ability - even in synaptic.
I don't think Synaptic is useful without internet connection, in this case.

---

### Post by eternalnewbee on 2008-12-04
> to 2: yes there is that ability - even in synaptic.
Sorry for the double post.

---

### Post by karuptdata on 2008-12-04
First we need to identify what type of video card that you do have. From your terminal issue the following command:

```
lspci | grep -i pci || lspci
```

Once you run that command post back the results and we will be able to work with you further from there.

---

### Post by DieB on 2008-12-04
hallo,

so please go to your "hardware and drivers" and check out which one is recommended. 

After that - start a live cd on your home computer (we use the live-cd so we get all dependencies) start synaptic and mark the needed nvidia driver for installation (it should mark the dependencies too). After that go to file and choose the make a script option, it will ask u to save it somewhere (best might be a usb stick) - lets call the script nvidia . After this is done close synaptics (don't worry about the marked changes).

now start a terminal (it is in applications-accesoirs) and type the following commands:

> cd /media/disk

probably u might have to change this - the proper addres of the stick can be found in the filemanager

> chmod +x nvidia
> ./nivida
> chmod +x nvidia*

now it should download the packages to the stick and with that stick u go to work put it in and simply double-click and it should install, if u get a failure it might be due to dependencies (but u will be noticed which package is missing)

hope that is a help

p.s:
@eternalnewbee: and how do u think milkolate posted this without internet?

---

### Post by milkolate on 2008-12-09
> **karuptdata said:**
> First we need to identify what type of video card that you do have. From your terminal issue the following command:

```
lspci | grep -i pci || lspci
```

Once you run that command post back the results and we will be able to work with you further from there.

sanggunian@sanggunian-desktop:~$ lspci | grep -i pci || lspci
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge

---

