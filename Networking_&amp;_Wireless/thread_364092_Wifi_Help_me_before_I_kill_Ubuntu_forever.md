---
title: "Wifi: Help me before I kill Ubuntu forever"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by axxiom on 2007-02-17
I cannot get Ubuntu 6.10 to connect to my wifi network.  I've scanned these forums.  I've tried the "simple guide".  I've tried everything except asking for help.

Help me before I kill Ubuntu forever.

Here's what I got.

Computer
Dell 700m Notebook
Intel 2200bg wifi card

My Wifi
ESSID: killmenow
Mode: AP
Channel: 3
Encryption: WPA pre-shared key
pre-shared key format: passphrase
pre-shared key:: okifyouinsist

There's a bazillion threads in this forum so I will not link to them all.  Instead, I will link you to the "simple guide" that doesn't work for me.
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

This is what happens when I try to execute step 3.  This is the code.
```
sudo apt-get install network-manager-gnome network-manager
```
This is the result.
```
E: Couldn't find package network-manager-gnome
```
I have an active internet connection.  I'm using the LAN cabled connection until I can figure out this goshforsaken wifi jungle.

I've walked through this guide at least a dozen times.  It doesn't work for me.  This error is the only error I receive so I figure it must be what is stopping it from working.

This is where you come in.  You can save Ubuntu so I don't have to kill it.  Believe me, I'm ready to kill it.  I'll do it.

If I've overlooked some magical help guide feel free to hit me, then kick me, then link me to this magical help guide.  If I haven't missed anything and it just doesn't work and Ubuntu makes you have to jump through hoops, walk on broken glass, and swallow burning coals then Ubuntu is an terrible product.  Absolutely awful.  I've got a lot more to say, but it's useless ranting that won't fix my problem.  However, it will KILL UBUNTU.

---

### Post by gradedcheese on 2007-02-17
Hi.  Please relax.  Pour yourself some nice tea.

Alright.  

```

sudo apt-get update
sudo apt-get install network-manager-gnome network-manager

```

Does that work?  network-manager-gnome should be in the default repositories.

---

### Post by axxiom on 2007-02-17
You saved Ubuntu.  I will not have to kill Ubuntu after all.

I figured it was going to be something simple.  Well, the "simple guide" could really use this tip.  Thanks gradedcheese.

---

### Post by gradedcheese on 2007-02-17
please don't resort to killing stuff over so simple a thing...

---

### Post by IamAcoconut on 2007-02-18
Just a question!
Did your card detect nearby networks? Was that the connection itself that was a problem?
That's my problem - I detect the networks but can connection always fails. Oh, those were unencrypted networks, so linked guide doesn't address issue. Or does it?
Will you save one more Ubuntu? ;)

---

### Post by gradedcheese on 2007-02-18
IamAcoconut -- which card do you have?  Are you using NetworkManager or the standard utilities that ship in Ubuntu?  If you want, we can go through some troubleshooting steps.

---

### Post by IamAcoconut on 2007-02-18
> **gradedcheese said:**
> IamAcoconut -- which card do you have?  Are you using NetworkManager or the standard utilities that ship in Ubuntu?  If you want, we can go through some troubleshooting steps.Well I'd be glad, as I am stuck and out of ideas.
As to tools I'm using, I tried Wifi-radar and Wireless Assistant, as well as NetworkManager. I've recently installed XP drivers for the card via ndiswrapper yet nothing changes: I can see all the networks but every time I try to connect I get "connection failed".
My card (just temporarlily disabled) 
```
  *-network:0 DISABLED    
       description: Ethernet interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 7
       bus info: pci@01:07.0
       logical name: wlan0
       version: 00
       serial: 00:12:0e:1d:14:91
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=acx_pci multicast=yes
       resources: iomemory:e00fc000-e00fdfff iomemory:e00c0000-e00dffff irq:193
```
What else information should I provide you with?
It would be better to analyse the problem first instead of rushing for trial & error as I have no AP at home right now. Will try to set up an ad-hoc network from another laptop though.

Thanks in advance!

---

### Post by gradedcheese on 2007-02-18
Alright.  Network Manager can only use interfaces that you've disabled in the normal utilities (that is, wlan0 needs to be disabled in /etc/network/interfaces).  According to what you posted, the card is supported by the acx_pci driver and not ndiswrapper.  If you want to use ndiswrapper instead, you need to tell the Kernel not to use acx_pci (this can be done via /etc/modprobe.d/blacklist) and then you can "sudo modprobe ndiswrapper".  Otherwise, the Kernel picks acx_pci even though you installed this other driver.

If you do have ndiswrapper correctly installed, you can tell the Kernel to switch drivers like this:

(if you're not using Network Manager, do this first, otherwise uncheck 'enable wireless' in network manager)

```

sudo ifdown wlan0

```

now switch drivers:

```

sudo rmmod acx_pci
sudo modprobe ndiswrapper

```

now bring up the interface (Network Manager: 'enable wireless', otherwise "sudo ifup wlan0")

---

### Post by IamAcoconut on 2007-02-19
```
$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
$ sudo rmmod acx_pci
ERROR: Module acx_pci does not exist in /proc/modules
```
lsmod just gave me 'acx' so...
```
$ sudo rmmod acx
$ sudo modprobe ndiswrapper
$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

```

---

### Post by gradedcheese on 2007-02-19
hmm... can you, after the driver reload (rmmod/modprobe)

```

sudo ifconfig wlan0 up
sudo iwlist wlan0 scan

```

---

### Post by yankeebisbis on 2007-02-19
"sodo" "apt" blah blah..that is why linux is still and will aways lag behind windows...to do simple things look how many commands you have been told  to type and they are thinking that one day this operating system will become popular? well now bill gate is planning to retire in near future and I am sure he will be laughing at all the vain affords made by linux advocates and developers. CLICK  CLICK AND DONE is what linux need. SUDO APT codes should all be transparent  to the average users. Good luck

---

### Post by gradedcheese on 2007-02-19
huh?  they are.  it's just that, **in a web-based forum where we type stuff, it's easier for me to tell you commands to type** than it is to tell you which icon to click on, how that icon looks, where it is relative to some other icon, etc.  All of this can be done from a  GUI (which, in my opinion is better than anything Windows ships with) but it's easier to talk shell commands.  Sorry if that somehow bothers you.

---

### Post by IamAcoconut on 2007-02-20
```
sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 7
       bus info: pci@01:07.0
       logical name: wlan0
       version: 00
       serial: 00:12:0e:1d:14:91
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=**ndiswrapper** driverversion=1.22 firmware=Texas Instruments,12/01/2004,7. link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:e00fc000-e00fdfff iomemory:e00c0000-e00dffff irq:193
```
Now it should work, I guess. Thanks :)
And it does indeed! I could kiss you if I weren't at a public hotspot ;)

---

