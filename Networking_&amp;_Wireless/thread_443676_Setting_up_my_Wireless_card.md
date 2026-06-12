---
title: "Setting up my Wireless card"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by RedSamurai on 2007-05-14
I have 2 questions. One how would I set my wireless card up. I have the Dell Insprion E1505 My wired eth0 works but i want to set up wireless. (I am new to linux :( ) 

Question 2:
How would i install Kismet. i try Sudo apt-get install kismet but nothing can someone help me thank you very much.

---

### Post by kilroy423 on 2007-05-14
If your wifi card is'nt recognized you can try and load the driver via ndiswrapper which is availible through the package manager

read the man pages to walk you through:

```
man ndiswrapper
```

but in a nutshell...get the windows .inf file and then install it using:

```
sudo ndiswrapper -i
```

lists current drivers installed

```
sudo ndiswrapper -l
```

removes driver

```
sudo ndiswrapper -e Driver
```

GL,
dan

***EDIT

Kismet only uses certain chipsets so make sure yours is compatible...IDK if it is in the default repositories so that is why apt-get can't find i, but you can get a repository that has it...STW for Kismets site and RTFM...since I am not compatible with Kismet I use aircrack-ng(which rocks BTW)

---

### Post by agurk on 2007-05-14
If you have the (optional) Intel 3945ABG wireless card (to find out, type *lspci* in a terminal window), you need to install the linux-restricted-modules for your kernel, from the "restricted" repository.

---

### Post by RedSamurai on 2007-05-14
> **agurk said:**
> If you have the (optional) Intel 3945ABG wireless card (to find out, type *lspci* in a terminal window), you need to install the linux-restricted-modules for your kernel, from the "restricted" repository.

How would i do this Ndiswrapper didnt work for me on Gentoo ether i get invaled driver.
and it did see my wireless on install it asked which one i wanted to use i choose wired but i want my wireless to work

---

### Post by agurk on 2007-05-15
What is the output of the *lspci* command?

---

### Post by RedSamurai on 2007-05-15
<code>
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7149
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
</code>

---

### Post by RedSamurai on 2007-05-16
Thats what i ended up getting ^

---

### Post by RedSamurai on 2007-05-17
Hello :P Anyone?

---

### Post by agurk on 2007-05-17
Well, unfortunately you seem to have the Broadcom-based wireless adapter, which basically leaves you with two options:

* Start looking for guides on how to install Broadcom drivers.
* Cough up €40 and a screwdriver and get some Intel 3945abg sweetness instead.

---

### Post by RedSamurai on 2007-05-18
i got the driver installed useing ndiswrapper but how do i get my wlan0 to show up

---

### Post by RedSamurai on 2007-05-23
anyone :'(

---

### Post by RedSamurai on 2007-05-23
I have tryed useing Ndiswrapper but i think i am doing it wrong is there anyway someone can help me i really need my wireless up. Thank you all very much

---

### Post by whitetrash on 2007-05-23
I also have a broadcom card. This guide worked for me (its really simple, it's a how-to on installing the firmware - seems to be working for quite a few people) - [http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom).

as for Kesmit - your command seems right, but you had sudo with a capital 'S' - should be a small one.

Hope that's somewhat helpful.

---

### Post by stchman on 2007-05-23
> **RedSamurai said:**
> I have 2 questions. One how would I set my wireless card up. I have the Dell Insprion E1505 My wired eth0 works but i want to set up wireless. (I am new to linux :( ) 

Question 2:
How would i install Kismet. i try Sudo apt-get install kismet but nothing can someone help me thank you very much.

What kind of wireless card do you have.  You can get the info via lspci.

---

### Post by freak101 on 2007-05-23
Don't forget to check if your wlan card is activated (wlan led). Otherwise turn it on in your bios settings or via software.

---

