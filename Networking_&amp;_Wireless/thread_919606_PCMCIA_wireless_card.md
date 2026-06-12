---
title: "PCMCIA wireless card"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by speculatius on 2008-09-14
Hi,

I need to install PCMCIA wireless card on xubuntu 8.04. This card is not supported by ndiswrapper. I tried some tutorials, but it is still not working. Now, when I plug card to pc, lshw shows me:

...
          *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:02:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
              *-network
                   description: FLASH OFDM PC CARD DEVICE
                   product: FT2000
                   vendor: FLARION
                   physical id: 0
                   version: V1
                   slot: Socket 0
...

How can I connect to this device? Can you pls help me?

Link to tutorial I used /SVK/:

[http://www.aelias.eu/index.php?option=com_content&task=view&id=61&Itemid=37](http://www.aelias.eu/index.php?option=com_content&task=view&id=61&Itemid=37)

Thanks...

---

### Post by pytheas22 on 2008-09-14
This [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/135760") says that adding the pci=assign-busses option to your grub boot menu solves the problem.  To do that, first boot open up your grub menu by typing:
```

sudo gedit /boot/grub/menu.lst
```

Scroll down through the file until you find a section that looks similar to this:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

(There may be several sections, depending on how many kernels you have installed on your system. Each entry corresponds to a different line in the grub boot menu that you see when you first start your computer.)

Add the "pci=assign-busses" option to the end of the "kernel" line as below:
```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro quiet splash **pci=assign-busses**
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

Now reboot.  Does the device work?  If not, what is the output of:
```

lshw -C Network
dmesg | grep -e yenta -e wlan -e eth1
```

---

### Post by speculatius on 2008-09-15
I changed the grubmenu-configuration, but it didnt solve my prolem.

Output for "lshw -C Network":

```

  *-network               
       description: FLASH OFDM PC CARD DEVICE
       product: FT2000
       vendor: FLARION
       physical id: 0
       version: V1
       slot: Socket 0

```

Output for "dmesg | grep -e yenta -e wlan -e eth1" is empty, but last lines of dmesg after inserting device are:

```

[   62.049739] pccard: PCMCIA card inserted into slot 0
[   62.050068] pcmcia: registering new device pcmcia0.0

```

Output for "lspci -v | grep subordinate"

```

	Bus: primary=00, secondary=01, subordinate=05, sec-latency=32
	Bus: primary=01, secondary=02, subordinate=05, sec-latency=176

```

Thank you very much for your time...

---

### Post by pytheas22 on 2008-09-15
What is the output of:
```

iwlist scan
iwconfig
```

It looks like the interface should work--it's not listed as 'unclaimed'--so I'm still not sure what's going on.  But we'll figure it out.

---

### Post by speculatius on 2008-09-15
Output for "iwlist scan":

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

"iwconfig":

```

lo        no wireless extensions.

eth0      no wireless extensions.

```

eth0 is wired ethernet /I didnt mention it in "lshw -C Network" output in previous post/

The led diode on device is not shining. It looks like there should be switch for turning on wireless, but there is not.

I googled around and I found stuff called pcmciautils [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html]("http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html") . Do you think, that it can help me?

Thank you...

---

### Post by cteneyck on 2008-09-15
what is the output of

dmesg

lspci

also what kind of pcmcie card is it. ie make and model #


thx

---

### Post by speculatius on 2008-09-16
Thank you for all your effort, but there was no more time to solve it. So I gave it up :(

---

