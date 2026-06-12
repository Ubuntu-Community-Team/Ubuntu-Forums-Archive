---
title: "[SOLVED] Can't Connect to  Wireless Network"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by puckrat3 on 2008-09-28
I am not able to connect to my wireless network on my notebook.  I have it dualbooted with windows xp and the wireless works in there so, i don't think it is my network card.  any tips would be very helpfull. thank you.

---

### Post by Ayuthia on 2008-09-29
> **puckrat3 said:**
> I am not able to connect to my wireless network on my notebook.  I have it dualbooted with windows xp and the wireless works in there so, i don't think it is my network card.  any tips would be very helpfull. thank you.

Can you help provide some more information about your wireless card?  Can you post the results of the following from the Konsole:
```
lspci -nn
```This will give some information about your pci cards.  One of them should be your wireless card.

---

### Post by shanix on 2008-09-29
```
lspci -vvnn | grep Wireless
```

Might provide more info on the issue.

---

### Post by puckrat3 on 2008-09-29
Ok, i typed in both and here are the results,

lspci -nn:  03:00:0 Network controller [0280]: broadcom corporation bcm4311 802.11b/g wlan[14e4:411] (rev 02)

lspci -vvnn | grep wireless:  subsystem: hewlett packard company bcm4311 802.11b/g wireless lan controller [103c:1374]

Hope this helps!

---

### Post by puckrat3 on 2008-10-01
bump

---

### Post by ittiam on 2008-10-01
Have you got the driver installed using ndiswrapper? 

If not download it from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/) or you can add the repo.

THen you can follow this,

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by puckrat3 on 2008-10-01
I downloaded it from the kubuntu restricted drivers manager.

---

### Post by Ayuthia on 2008-10-02
Ok.  I am going to assume that you have a wired connection in Ubuntu.  Can you post the following information:
```
uname -a
lshw -C network
ndiswrapper -v
ndiswrapper -l
```
The commands will help us see what kernel you are using, if you are using 32 or 64-bit, what driver your wireless is using, what version of ndiswrapper is installed along with what driver is being used in ndiswrapper.  It is possible that you will get error messages for the ndiswrapper command if it is not installed.

---

### Post by shanix on 2008-10-02
try this:
[http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)

---

### Post by puckrat3 on 2008-10-02
For, lshw -C network

```

WARNING: you should run this program as super-user.
SCSI
  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:c9:c2:76
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.4 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:00:00:1a:73:c3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```
For, ndiswrapper -v
```

The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found

```
And for, ndiswrapper -l
```

The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found

```

---

### Post by Ayuthia on 2008-10-02
You might want to try the ndiswrapper route first because the 4311 rev 02 card did not work so well in 8.04, but I think it is better now in 8.04.1.

Here is a link to a good guide for ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by puckrat3 on 2008-10-02
No, sorry, this didn't work. Do you have any other ideas?

---

### Post by puckrat3 on 2008-10-02
I tried to disable the current wireless driver and then enable it.  When i try to enable it, it tells me this,

**Broadcom B43 wireless driver**
While this driver itself is free software, it relies on proprietary firmware which cannot be legally shipped with the operating system. Your hardware will not work without the firmware.

---

### Post by Ayuthia on 2008-10-02
> **puckrat3 said:**
> No, sorry, this didn't work. Do you have any other ideas?

What part did not work?

What version of Ubuntu are you using?  If you don't know, please post the results of:
```
cat /etc/issue
```
8.04 does not really work with your card, but it might work with 8.04.1 so if you have 8.04.1, we can try to manually install the firmware.

Do you have a working internet connection in Ubuntu?

---

### Post by puckrat3 on 2008-10-02
cat /ect/issue
```

Ubuntu 8.04.1 \n \l

```
 
Yes, i have a wired connection that works in kubuntu

---

### Post by Ayuthia on 2008-10-02
Let's try the following:
```
sudo apt-get install b43-fwcutter
```
It should ask you if you would like it to install the firmware for you.  Select yes.  Once that is done, please do the following:
```
sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```

---

### Post by puckrat3 on 2008-10-02
Allright, i'm not sure this worked because it didn't ask me to install the firmware, only for my password, and there were some deceving responds from the computer, here is what it responded.

sudo apt-get install b43-fwcutter

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx

reply: nothing

sudo modprobe b43

reply:nothing

sudo ifconfig wlan0 up

reply:nothing

sudo iwlist scan

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```

---

### Post by Bucky Ball on 2008-10-02
Seems to be happening:

wlan0     No scan results

Just not finding your network.

Open System->Admin->Network and fill in the appropriate details (ESSID and security details) to connect to your router. Make sure you have "Automatic DHCP" setting for now and disable roaming. You can tweak these things later but for now you just want to connect. :)

---

### Post by puckrat3 on 2008-10-02
awesome, it was DHCP, it wasn't set to automatic. Thanks so much Bucky Ball. You too, Ayuthia, thanks so much for giving up your time to help me with my computer.

---

### Post by puckrat3 on 2008-10-03
ok, never mind, it connected to the wireless and it worked. then i shut it down, went upstairs and now it will connect,(sometimes) but the internet won't connect... any help with this?

---

### Post by Bucky Ball on 2008-10-03
Does this mean you have changed your location in regards to where you have your router (downstairs)? This can effect the signal which is why it is dropping out. Possibly. Even when windoze does connect fine from a certain position, Ubuntu doesn't sometimes. 

Does it still work consistently downstairs?

---

### Post by puckrat3 on 2008-10-03
> **Bucky Ball said:**
> Does this mean you have changed your location in regards to where you have your router (downstairs)? This can effect the signal which is why it is dropping out. Possibly. Even when windoze does connect fine from a certain position, Ubuntu doesn't sometimes. 

Does it still work consistently downstairs?
No, I went next to the router and it does the same thing, gets to 28% or even 57% through connecting to the router then it says unable to connect to the wireless internet.  i think it is just something with the settings of the network card, but i'm not sure exactly what it is.

---

### Post by puckrat3 on 2008-10-03
Ok, as it turns out it will slowly connect when directly next to the router. but, even next to the router, it only gets 90% signal.  i isn't the router, it's brand new and it's a Netgear Rangemax Wireless-N Gigabit Router.  when in windows, the wireless will work fine and have a great signal, but in Kubuntu, it is awful. any tips on being able to connect with a better signal in Kubuntu, like windows does?

---

### Post by Bucky Ball on 2008-10-04
Unless Ayuthia wants to chime in, not much coming from here. :(

---

### Post by Ayuthia on 2008-10-04
The only other thing that I can think to try is going with another driver.  The wl driver has produced fairly good signal strength.  There has been some mixed reviews with connecting with encrypted networks and using ssh.

If you want to try the hardy-proposed version (it is using a kernel that is still in test), you can try this link:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)
The advantage to this one is that the Ubuntu developers have made some fixes to the driver.

If you want to go with installing the driver on your own, you will need to install build-essential from Synaptic or go to the Terminal and type:
```
sudo apt-get install build-essential
```
Then you can follow the steps in this link:
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

If you don't want to try those steps, you might try using a different channel on the router, maybe set it to only work with the g instead of mixed/a/b/n.  I am not for sure it that will help or not though.

---

