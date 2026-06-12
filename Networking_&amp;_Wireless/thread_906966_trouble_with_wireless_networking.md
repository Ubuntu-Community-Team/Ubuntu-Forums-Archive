---
title: "trouble with wireless networking"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by ajaxmehta on 2008-09-01
Here's my current state on the hardware front:
Generic network card (wired)
Netgear WG311 PCI Wireless Card

Internet and networking is working fine via the LAN cable; despite the fact that the network status icon on the panel says: "No network connection"

I am trying to get the wireless card going. Installed ndisgtk but am unable to install the windows drivers for the card. Nothing happens when I try to do this install.

Here's what I get on the terminal on  "sudo lshw -C network"

[COLOR="Red"] *-network:0             
       description: Ethernet interface
       product: Hangzhou Silan Microelectronics Co., Ltd.
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: eth0
       version: 01
       serial: 00:e0:20:ac:ae:5a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sc92031 driverversion=2.0c duplex=full ip=192.168.1.5 latency=32 link=yes maxlatency=40 mingnt=20 module=sc92031 multicast=yes port=MII speed=100MB/s
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32[/COLOR]


[COLOR="Black"][/COLOR]Am grateful for all help from the community. Pardon me if this is the wrong place for this query or if this has been dealt with earlier.

---

### Post by prshah on 2008-09-01
> **ajaxmehta said:**
> 
Netgear WG311 PCI Wireless Card

See [[SOLVED] How to activate WG311v3 (or any ndiswrapper or native) wireless ]("http://ubuntuforums.org/showthread.php?t=756260") for a command-line based howto with expected outputs for this card. Post back here if you have any difficulties.

---

### Post by ajaxmehta on 2008-09-01
On trying ndiswrapper from the terminal, here's what I get:

juhi@juhi-desktop:~/Desktop/Windows 2000$ ndiswrapper -i WG311v3.inf
[COLOR="Red"]couldn't create /etc/ndiswrapper/wg311v3: Permission denied at /usr/sbin/ndiswrapper-1.9 line 152.
[/COLOR]

---

### Post by ajaxmehta on 2008-09-01
Thanks prshah
Finally had the driver installed, and is showing in the ndisgtk as well
Following your instructions to the T, BUT.... this is where things get stuck:

[COLOR="Red"]juhi@juhi-desktop:~/Desktop/Windows 2000$  sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.[/COLOR]
[COLOR="Black"][/COLOR]
Rather amazing, considering I just installed the driver with ndiswrapper

Now what !!

And Thanks again for your help

---

### Post by prshah on 2008-09-01
> **ajaxmehta said:**
> 
juhi@juhi-desktop:~/Desktop/Windows 2000$ ndiswrapper -i WG311v3.inf
[COLOR="Red"]couldn't create /etc/ndiswrapper/wg311v3: Permission denied at /usr/sbin/ndiswrapper-1.9 line 152.
[/COLOR]

> **ajaxmehta said:**
> 
[COLOR="Red"]juhi@juhi-desktop:~/Desktop/Windows 2000$  sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.[/COLOR]
[COLOR="Black"][/COLOR]


The first "-i" command has to be run with sudo.

For the second, after the driver is installed successfully, you should "modularize" it with the command ```

sudo ndiswrapper -m
```, then repeat the modprobe command.

btw, can you post the outputs of this command```
history | tail
```

---

### Post by ajaxmehta on 2008-09-01
Sorry! Should have posted the entire output
[COLOR="Red"]
juhi@juhi-desktop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

[COLOR="Red"]juhi@juhi-desktop:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.[/COLOR]


juhi@juhi-desktop:~$ history | tail
  122  sudo modprobe
  123  sudo modprobe ndiswrapper
  124  sudo ndiswrapper
  125  sudo ndiswrapper -l
  126  sudo ndiswrapper -m
  127  juhi@juhi-desktop:~/Desktop/Windows 2000$  sudo modprobe ndiswrapper
  128  FATAL: Module ndiswrapper not found.
  129  sudo modprobe ndiswrapper
  130  sudo ndiswrapper -m
  131  history | tail[/COLOR]

---

### Post by prshah on 2008-09-01
> **ajaxmehta said:**
> 
juhi@juhi-desktop:~$ sudo ndiswrapper -m
module configuration already contains alias directive


OK, can you post the following outputs as well:```
ndiswrapper -l
cat /etc/network/interfaces
```

---

### Post by ajaxmehta on 2008-09-01
Here;s the output of:
ndiswrapper -l
cat /etc/network/interfaces

[COLOR="Red"]juhi@juhi-desktop:~$ ndiswrapper -l
wg311v3 : driver installed
        device (11AB:1FAA) present
juhi@juhi-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback




iface eth0 inet dhcp

auto eth0
juhi@juhi-desktop:~$ [/COLOR]

---

### Post by prshah on 2008-09-01
> **ajaxmehta said:**
> juhi@juhi-desktop:~$ ndiswrapper -l
wg311v3 : driver installed
        device (11AB:1FAA) present


This means that driver is installed correctly. However, you probably have a duplicate alias definition somewhere. I think it will be in /etc/modprobe.d/ndiswrapper, but I'm not sure; can you check if you have that file?

If you do have that file, (temporarily) move it to your home directory,```
sudo mv /etc/modprobe.d/ndiswrapper ~
``` and then restart your system and try the "ndiswrapper -m" step again.

If you don't have the file, then give the command ```
sudo modprobe -r ndiswrapper
``` (you may get an error message which you can ignore) and then try the "ndiswrapper -m" command again. 

If you still get an error, please post the output to the following command (immediately after the "ndiswrapper -m" command)```
dmesg | tail
```

I suspect that using both ndis-gtk and ndiswrapper directly have created this situation; it should be easy to resolve, but I can't recall where the alias directive for ndiswrapper is to be placed... I can check that tomorrow, though.

One last thing: I hope you're not using ubuntu 64-bit; the Windows 2000 driver is 32 bit. to confirm, post output of ```
uname -a
```

---

### Post by ajaxmehta on 2008-09-01
Yes the alais definition was there. I moved it with the command, restarted and .....

juhi@juhi-desktop:~$ sudo ndiswrapper -m
[sudo] password for juhi:
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
juhi@juhi-desktop:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
juhi@juhi-desktop:~$ dmesg | tail
[   55.830440] Bluetooth: Core ver 2.11
[   55.830706] NET: Registered protocol family 31
[   55.830711] Bluetooth: HCI device and connection manager initialized
[   55.830719] Bluetooth: HCI socket layer initialized
[   55.857244] Bluetooth: L2CAP ver 2.8
[   55.857262] Bluetooth: L2CAP socket layer initialized
[   55.912312] Bluetooth: RFCOMM socket layer initialized
[   55.912502] Bluetooth: RFCOMM TTY layer initialized
[   55.912508] Bluetooth: RFCOMM ver 1.8
[   61.386993] eth0: no IPv6 routers present
juhi@juhi-desktop:~$ uname -a
Linux juhi-desktop 2.6.22-14-386 #1 Sun Oct 14 22:36:54 GMT 2007 i686 GNU/Linux
juhi@juhi-desktop:~$

---

### Post by prshah on 2008-09-01
> **ajaxmehta said:**
> 
juhi@juhi-desktop:~$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
juhi@juhi-desktop:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.


And here we are back to the same status as Post #4 of this thread. :)

Well; try this;```
sudo depmod -a
sudo modprobe ndiswrapper
```

---

