---
title: "problems on PRO/Wireless 3945ABG Network Connection"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by Pekkaniska on 2007-09-21
Hi, i'm running feisty, and PRO/Wireless 3945ABG Network Connection does not show up on network manager. it is in Device manager and  "iwconfig" prints this:
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

and  "lspci -v|grep 3945" this:
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by theox26 on 2007-09-21
Have you enabled the drivers in the non-free driver menu, I think it's called restricted drivers. (sorry I forget what it's called and i'm not in ubuntu right now.

---

### Post by NilsE on 2007-09-21
This worked for my in Feisty with the same card:

```
In Synaptic package manager:

1) Make sure network-manager-gnome  is installed
2) Make sure wpasupplicant is installed
3) Install libpam-keyring


``````
In System Administration:

Make sure the restricted driver for the chip is there, enabled and in use.
```
```
In terminal:

sudo echo "@include common-pamkeyring" | sudo tee -a /etc/pam.d/gdm

NOTE: This will allow you to remember connection passwords/keys in the keyring
and not get prompted by the keyring manager every time. This is not mandatory.
```
```
In System/Preferences/Session:

Add gksudo nm-applet (if the network manager is not there) as the command
line to a new start programs. You can name it whatever you want. It may
work without the gksudo.
```
```
You may also have to clean out the /etc/network/interfaces file if you have
configured any devices manually. Just leave these 2 lines. (back it up first)

auto lo
iface lo inet loopback
```
SHUTDOWN AND RESTART

NOTE: The applet may not show up in the upper panel so you can right click
on the top panel, select add to panel then add the notification applet.

NOTE: After the first time you try to connect to a new available network in the pulldown it will ask for the SSID and key etc. but should remember it after that.

NOTE: Make sure that in the manual settings for the configuration that all devices are set to roaming.

---

### Post by Pekkaniska on 2007-09-22
> **NilsE said:**
> This worked for my in Feisty with the same card:

```
In Synaptic package manager:

1) Make sure network-manager-gnome  is installed
2) Make sure wpasupplicant is installed
3) Install libpam-keyring


``````
In System Administration:

Make sure the restricted driver for the chip is there, enabled and in use.
```
```
In terminal:

sudo echo "@include common-pamkeyring" | sudo tee -a /etc/pam.d/gdm

NOTE: This will allow you to remember connection passwords/keys in the keyring
and not get prompted by the keyring manager every time. This is not mandatory.
```
```
In System/Preferences/Session:

Add gksudo nm-applet (if the network manager is not there) as the command
line to a new start programs. You can name it whatever you want. It may
work without the gksudo.
```
```
You may also have to clean out the /etc/network/interfaces file if you have
configured any devices manually. Just leave these 2 lines. (back it up first)

auto lo
iface lo inet loopback
```
SHUTDOWN AND RESTART

NOTE: The applet may not show up in the upper panel so you can right click
on the top panel, select add to panel then add the notification applet.

NOTE: After the first time you try to connect to a new available network in the pulldown it will ask for the SSID and key etc. but should remember it after that.

NOTE: Make sure that in the manual settings for the configuration that all devices are set to roaming.

did everything. And nothin changed. I have also tried to use WICD instead of network manager and that didn't help either. /etc/network/interfaces is still only the two lines :

auto lo
iface lo inet loopback

So i'm guessing network manager did nothin on startup?

edit: Currently on Gutsy

---

### Post by imdano on 2007-09-22
What's the output of ```
lshw -C network
```

---

### Post by Pekkaniska on 2007-09-22
```
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:41:e2:dd:4a
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.1.43 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945

```

So there's no logical name etc for the wireless? possible to give these manually or some other way?

---

### Post by Pekkaniska on 2007-09-23
bumb.. any ideas? anyone?

---

### Post by Zorael on 2007-09-23
Is the interface listed in /etc/iftab? I can't imagine why it shouldn't be, though - I think it gets automatically assigned there if missing.

---

### Post by Pekkaniska on 2007-09-23
/etc/iftab
```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

```

and nothing else

---

### Post by Zorael on 2007-09-23
Most interesting. It doesn't seem to be able to extract the card's mac address. I have no idea what could cause this.

If you dualboot, does it work in Windows? Have you tried loading a Gutsy development Live CD? Does it work there?

---

### Post by xc3RnbFO8P on 2007-09-23
I got similar problem, it is a hotkey problem.

In hardware information I can see "Acer hotkey".

I have to run this in terminal: 

sudo depmod -a

sudo modprobe -r acerhk

sudo modprobe acerhk poll=1 autowlan=1

---

### Post by Pekkaniska on 2007-09-23
> **Zorael said:**
> Most interesting. It doesn't seem to be able to extract the card's mac address. I have no idea what could cause this.

If you dualboot, does it work in Windows? Have you tried loading a Gutsy development Live CD? Does it work there?


Havent tried.. Ill maybe have to. Yeah i have dualboot on my t60 but vista doesn't boot... It only boots to that lenovo problem solver thingie and want's to repair my hard drive (propably format linux off the system) :)

I will perhaps try to remove linux completely and regain my vista to try if it works there. then install gutsy, fresh.

---

### Post by Pekkaniska on 2007-09-23
> **Ringi said:**
> I got similar problem, it is a hotkey problem.

In hardware information I can see "Acer hotkey".

I have to run this in terminal: 

sudo depmod -a

sudo modprobe -r acerhk

sudo modprobe acerhk poll=1 autowlan=1


what could that be on a t60? the acerhk i mean

---

### Post by Zorael on 2007-09-23
You could always try to reload the ipw3945 module - if I unload it, I see its mac adress disappearing from the lshw -C network output, however it also ends up in an UNCLAIMED state, which yours does not.

```
$ sudo modprobe -r ipw3945 && sudo modprobe ipw3945
```

---

### Post by Pekkaniska on 2007-09-24
I just might be a fuckin' idiot but at least I let you all know about it. This is what you get when you never read any of the manuals that they ship with new electronics.I'm sorry for taking your time with my problem and it is clearly only a problem in my head.

There is a brightly colored (black on black as usual on a thinkpad) switch on the side of the thinkpad. There is a dim shade of gray image of a computer emitting radiowaves. Switch it and it will enable the wireless device. So no more problems for me. And i will propably keep reading the manuals when i buy something new, or just bang my head against the wall for a week. This took me 4 friking days to find this switch. So thank you everyone and sorry again. ](*,)](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by xc3RnbFO8P on 2007-09-24
You shouldn't take it so hard, I don't :) 
We can only learn from it.

---

