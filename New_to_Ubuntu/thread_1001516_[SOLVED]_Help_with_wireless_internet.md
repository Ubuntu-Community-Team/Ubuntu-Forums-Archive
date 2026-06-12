---
title: "[SOLVED] Help with wireless internet"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by James Matthew Tuten on 2008-12-04
In my enthusiasm upon recieving ubuntu in the mail , I did a full install (no partion). The problem is that I can connect to the internet via ethernet cable, but not wireless. The help tutorial describes using the terminal(uhoh) I followed the instructions and this is what it produced

matthew@C-3PO:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:72:89:9b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full ip=192.168.0.2 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 62:31:5d:41:be:0b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
matthew@C-3PO:~$ 

I have used the synaptic package to download drivers, I have searched for .inf files , I have downloaded a madwifi(can't build it). Even hardware driver shows there being two drivers activated but not in use and there are no other options available. I would appreciate any help , and please if you tell be to build something or use terminal be simple (I am simple)

Sincerely James T

---

### Post by manilaph on 2008-12-04
What version of Ubuntu did you receive in the mail?

Did you try the LiveCd or Live version first before installing it?

In my experience as a newbie, the 2 best distros that provide "out-of-the-box" wireless connection is Ubuntu (xubuntu & kubuntu) and Mandriva 2009.

I tried Fedora 10 and I would not recommend it. So many things do not work... including "no sound" and updating was a pain... and so I switched my other laptop back to Ubuntu 8.10.

When you try to connect via wireless... do you see that "green colored" swirling thing on the network manager icon? Does it detect any network at all?

---

### Post by ja660k on 2008-12-04
Post result of iwconfig...

if there is no wlan0
then go to system-> administration->hardware drivers.

and it SHOULD have your atheros hardware access layer
and the support for the wireless divice... 

make sure those are unchecked (disabled)...
because we will manage them using ndiswrapper

you dont need madwifi; Just be sure you have your windows driver specifically the .inf

---

### Post by Peter09 on 2008-12-04
I know its basic - but check any hardware on/off switch for your wireless device is in the 'on' position.

---

### Post by porchrat on 2008-12-04
> **James Matthew Tuten said:**
> I have used the synaptic package to download drivers, I have searched for .inf files , I have downloaded a madwifi(can't build it). Even hardware driver shows there being two drivers activated but not in use and there are no other options available. I would appreciate any help , and please if you tell be to build something or use terminal be simple (I am simple)

Sincerely James T

When you say you can't build madwifi you'll need to be a little more specific...do you have the relevant packages for building installed?

I have had good experiences with madwifi.  I have used it on 2 machines with both 8.04 and 8.10 and it works wonderfully.

Have you tried compat-wireless directly from their site?  Works wonderfully for me on 8.10

EDIT:  [here]("http://ubuntuforums.org/showthread.php?t=964836") is a thread from ubuntuforums that deals with how to install the compat-wireless manually...this one is relatively simple as far as linux driver installations go.

---

### Post by Michael.Godawski on 2008-12-04
If you are on 8.10 try this:

> The module is on **[linux-backports-modules-intrepid]("https://help.ubuntu.com/community/UbuntuBackports")** and it's called **ath5k**. You just need to install the package, either using Synaptic or apt-get, and make sure that is activated on System/Administration/Hardware Drivers.

---

### Post by porchrat on 2008-12-04
The ath5k is definitely the easiest solution.  For some reason (I can't recall) it never worked for me though, had to go for the compat-wireless install.  Wish I could've used the ath5k though.

---

### Post by fedja.hvastija on 2008-12-04
Had the same issue last night, this is how I solved it:

in /etc/NetworkManager/nm-system-settings.conf
set managed=false

The network manager was blocking my wifi for some reason, seems pretty common.

---

### Post by nothingspecial on 2008-12-04
I use madwifi because I always have can do so without thinking.

I find after that installing wicd provides a faster more stable connection. Have a look.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by nothingspecial on 2008-12-04
Sorry, not as helpful as I could have been, if you want to use madwifi just copy and paste these into your terminal.


Download the latest madwifi snapshot.

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz	

```
Unzip it

```
tar -xvf madwifi-hal-0.10.5.6-r3875-20081105.tar.gz 	
```


navigate to the extracted file


```
cd madwifi-hal-0.10.5.6-r3875-20081105
```

If you`ve not got the tools necessary for compiling get them
```

sudo apt-get install build-essential linux-headers-$(uname -r)
```

Then compile it

```
sudo make
```
```

sudo make install
```

load the module (driver)
```

sudo modprobe ath_pci
```

make it load every time you boot
```

gksudo gedit /etc/modules
```

then copy and paste this to the bottom of that file
```

ath_pci
```

save
exit 
reboot

That`s it.

---

### Post by porchrat on 2008-12-04
He said he couldn't build madwifi...perhaps he hasn't installed build-essential yet

---

### Post by James Matthew Tuten on 2008-12-04
I received Ubuntu 8.10 , I did try the live version before I installed it, but I thought because it was a demo and not fully installed that my wireless would not be recognized. How do I see if the device is on, device manager shows it being there. I already downloaded ath5k from synaptic and I activated it , but Device Driver says that it is active , but not in use. I did download madwifi , and when I say build it I mean that I don't know how to compile it in the terminal . I will try everything that ya'll have posted and keep trying . Thanks

---

