---
title: "AC600 usb wifi adapter 17.10 need help -wireless script pastebin inc..."
date: 2018-03-01
forum: Networking &amp; Wireless
---

### Post by jason coale on 2018-03-01
After many months of reading and following thru the many threads both on and off Ubuntuforums, I submit! 

Here's my wireless script

[http://paste.ubuntu.com/p/MrcNc2KYVG/]("http://paste.ubuntu.com/p/MrcNc2KYVG/")

kernel is 4.13.0-32-generic (#35-Ubuntu SMP Thu Jan 25 09:13:46 UTC 2018)

Thank you in advance for helping..

---

### Post by chili555 on 2018-03-01
With a temporary working internet connection by ethernet, tethering or whatever means possible, open a terminal and do:

```
sudo apt update
sudo apt install git
git clone https://github.com/gnab/rtl8812au.git
sudo dkms add ./rtl8812au
sudo dkms build rtl8812au/4.2.2
sudo dkms install rtl8812au/4.2.2
```
Reboot and tell us if the wireless is working.

---

### Post by jason coale on 2018-03-01
Hello, and thank you for your reply... 

prior to completing without error, this was generated.  In case it helps, as I've certainly ran much code over the time I've spent trying to fix this issue.

 8812au:
Running module version sanity check.
Error! Module version v4.2.2_7502.20130517 for 8812au.ko
is not newer than what is already found in kernel 4.13.0-32-generic (v5.1.5_19247.20160830).
You may override by specifying --force.

depmod........

DKMS: install complete

rebooting now....

EDIT:  NO LOVE  :-(

jason@budgie:~$ sudo dkms status
[sudo] password for jason: 
8812au, 4.2.2: added
bbswitch, 0.8, 4.13.0-32-generic, x86_64: installed
bbswitch, 0.8, 4.13.0-36-generic, x86_64: installed
kpatch, 0.3.2: added
ndiswrapper, 1.60, 4.13.0-32-generic, x86_64: installed
ndiswrapper, 1.60, 4.13.0-36-generic, x86_64: installed
nvidia-340, 340.104, 4.13.0-32-generic, x86_64: installed
nvidia-340, 340.104, 4.13.0-36-generic, x86_64: installed
rtl8812au, 4.2.2, 4.13.0-25-generic, x86_64: built
rtl8812au, 4.2.2, 4.13.0-32-generic, x86_64: installed (WARNING! Diff between built and installed module!)
rtl8812au, 4.3.8.12175.20140902+dfsg, 4.13.0-32-generic, x86_64: built
rtl8812au, 4.3.8.12175.20140902+dfsg-0ubuntu7, 4.13.0-25-generic, x86_64: built
rtl8812au, 4.3.8.12175.20140902+dfsg-0ubuntu7, 4.13.0-32-generic, x86_64: built
rtl8812au, 5.2.9, 4.13.0-25-lowlatency, x86_64: installed
rtl8812au, 5.2.9, 4.13.0-31-generic, x86_64: built
rtl8812au, 5.2.9, 4.13.0-31-lowlatency, x86_64: installed
rtl8812au, 5.2.9, 4.13.0-32-generic, x86_64: built
rtl8812au, 5.2.9, 4.13.0-36-generic, x86_64: installed

---

### Post by chili555 on 2018-03-01
Jason, Jason, Jason! You have been a busy Ubuntuan, haven't you?

Let's clean out the basement:

```
sudo dkms remove rtl8812au/4.3.8.12175.20140902+dfsg --all
sudo dkms remove 8812au/4.2.2 --all
sudo dkms remove rtl8812au/5.2.9 --all
```

You probably don't need ndiswrapper, either; nobody does:

```
sudo apt purge ndiswrapper*
```

Now check:

```
sudo dkms status
```

If there are any remaining 8812au instances sudo dkms remove -all them as well until status is cleaned.

Then we'll try again.

---

### Post by jason coale on 2018-03-01
jason@budgie:~$ sudo dkms status
bbswitch, 0.8, 4.13.0-32-generic, x86_64: installed
bbswitch, 0.8, 4.13.0-36-generic, x86_64: installed
kpatch, 0.3.2: added
nvidia-340, 340.104, 4.13.0-32-generic, x86_64: installed
nvidia-340, 340.104, 4.13.0-36-generic, x86_64: installed

I'll ran the first codes you suggested again and rebooted, with fingers X'd, but no love

---

### Post by chili555 on 2018-03-01
May we see:```
sudo dkms status
modinfo 8812au | grep 9052
```Hint:> 0846:[COLOR="#FF0000"]9052 [/COLOR]NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]

---

### Post by jason coale on 2018-03-01
8812au, 4.2.2: added
bbswitch, 0.8, 4.13.0-32-generic, x86_64: installed
bbswitch, 0.8, 4.13.0-36-generic, x86_64: installed
kpatch, 0.3.2: added
nvidia-340, 340.104, 4.13.0-32-generic, x86_64: installed
nvidia-340, 340.104, 4.13.0-36-generic, x86_64: installed
rtl8812au, 4.2.2, 4.13.0-32-generic, x86_64: installed (WARNING! Diff between built and installed module!)

modinfo 8812au | grep 9052

I know my device id is 0846:9052 but not getting any output with the code..  Is the Diff referring to 8812au and 8811au, perhaps?

---

### Post by holiday on 2018-03-02
To clear things up for me, could you run 

$ sudo lshw -class network

and post the output. 

I'm interested in two fields: 1) serial; 2) logical name.

I've looked through your pastebin and the association of these is not clear to me. Depending on the output, I'd like to try working with wpa_supplicant and its generic wireless driver. If you've already looked down that hole then never mind. Let me know though.

---

### Post by chili555 on 2018-03-02
> [COLOR="#FF0000"]8812au, 4.2.2: added[/COLOR]
bbswitch, 0.8, 4.13.0-32-generic, x86_64: installed
bbswitch, 0.8, 4.13.0-36-generic, x86_64: installed
kpatch, 0.3.2: added
nvidia-340, 340.104, 4.13.0-32-generic, x86_64: installed
nvidia-340, 340.104, 4.13.0-36-generic, x86_64: installed
[COLOR="#FF0000"]rtl8812au, 4.2.2, 4.13.0-32-generic, x86_64: installed (WARNING! Diff between built and installed module!)[/COLOR]
Let's try harder.```
sudo dkms remove 8812au/4.2.2 --all
sudo dkms remove rtl8812au/4.2.2 --all
```Next, we try to build and install again:```
cd ~
sudo dkms add ./rtl8812au
sudo dkms build rtl8812au/4.2.2
sudo dkms install[COLOR="#FF0000"] --force[/COLOR] rtl8812au/4.2.2
```Next, try:```
sudo modprobe 8812au
modinfo 8812au | grep 9052
```

---

### Post by chili555 on 2018-03-02
> **holiday said:**
> To clear things up for me, could you run 

$ sudo lshw -class network

and post the output. 

I'm interested in two fields: 1) serial; 2) logical name.

I've looked through your pastebin and the association of these is not clear to me. Depending on the output, I'd like to try working with wpa_supplicant and its generic wireless driver. If you've already looked down that hole then never mind. Let me know though.Do USB wireless devices show up in lshw if there is no associated driver that informs the system that this is, indeed a network device?

Until a driver associates with the hardware, wpa_supplicant will be useless.

---

### Post by holiday on 2018-03-02
Chili I don't know!

Is it a rhetorical question? I can see you might need software that can understand the hardware but then wpa_supplicant can work with a generic wireless adapter driver so there must be some common API. We often see 'good enough' drivers that 'work' but don't work well. 

It's possible that all devices comply with a basic hardware API for identification. The MAC address for example is an attribute of the hardware device so there may be other information passed through that interface. 

But I don't know. I'm just guessing. Do you know?

---

### Post by chili555 on 2018-03-02
> But I don't know. I'm just guessing. Do you know?I do know the answer to the question above. > Do USB wireless devices show up in lshw if there is no associated driver that informs the system that this is, indeed a network device?
No.

It is not useful, in my view, to ask the OP for data points that clearly hold no probable clues as to a workable solution.

---

### Post by Penguin360 on 2018-03-02
> **chili555 said:**
> Let's try harder.```
sudo dkms remove 8812au/4.2.2 --all
sudo dkms remove rtl8812au/4.2.2 --all
```Next, we try to build and install again:```
cd ~
sudo dkms add ./rtl8812au
sudo dkms build rtl8812au/4.2.2
sudo dkms install[COLOR=#FF0000] --force[/COLOR] rtl8812au/4.2.2
```Next, try:```
sudo modprobe 8812au
modinfo 8812au | grep 9052
```

This worked for me like a charm. The only thing I had to change is to the the folder name to 8812au, instead of rtl8812au, because apparently it created /usr/src/8812au folder on my computer, instead of /usr/src/rtl8812au.

```
sudo dkms build [COLOR=#ff0000]8812au[/COLOR]/4.2.2
sudo dkms install[COLOR=#FF0000] [/COLOR]--force[COLOR=#FF0000][/COLOR] [COLOR=#ff0000]8812au[/COLOR]/4.2.2
```

Now my adapter is working. Thank you so much.

---

### Post by jason coale on 2018-03-03
> **holiday said:**
> To clear things up for me, could you run 

$ sudo lshw -class network

and post the output. 

I'm interested in two fields: 1) serial; 2) logical name.

I've looked through your pastebin and the association of these is not clear to me. Depending on the output, I'd like to try working with wpa_supplicant and its generic wireless driver. If you've already looked down that hole then never mind. Let me know though.

Hello, so heres the output without the AC600 adapter, using an old adapter...
jason@budgie:~$ sudo lshw -class network
[sudo] password for jason: 
  *-network                 
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 16
       serial: 00:1c:25:e5:57:6a
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:24 memory:feafc000-feafffff ioport:e800(size=256) memory:feac0000-feadffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlxe0469a16e52c
       serial: e0:46:9a:16:e5:2c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=4.13.0-32-generic firmware=1.4 ip=10.0.0.36 link=yes multicast=yes wireless=IEEE 802.11

And heres after swapping in the AC600 w/ a shutdown and reboot, but using usb tether from my cellphone....

jason@budgie:~$ sudo lshw -class network
[sudo] password for jason: 
  *-network                 
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 16
       serial: 00:1c:25:e5:57:6a
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:24 memory:feafc000-feafffff ioport:e800(size=256) memory:feac0000-feadffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: enp0s19f2u6
       serial: aa:ee:c6:65:dd:aa
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.108 link=yes multicast=yes
jason@budgie:~$

---

### Post by jason coale on 2018-03-03
> **chili555 said:**
> Let's try harder.```
sudo dkms remove 8812au/4.2.2 --all
sudo dkms remove rtl8812au/4.2.2 --all
```Next, we try to build and install again:```
cd ~
sudo dkms add ./rtl8812au
sudo dkms build rtl8812au/4.2.2
sudo dkms install[COLOR="#FF0000"] --force[/COLOR] rtl8812au/4.2.2
```Next, try:```
sudo modprobe 8812au
modinfo 8812au | grep 9052
```

Hey Chilli!!  Here's all of your cmds ran...

jason@budgie:~$ sudo dkms remove 8812au/4.2.2 --all

------------------------------
Deleting module version: 4.2.2
completely from the DKMS tree.
------------------------------
Done.
jason@budgie:~$ sudo dkms remove rtl8812au/4.2.2 --all

-------- Uninstall Beginning --------
Module:  rtl8812au
Version: 4.2.2
Kernel:  4.13.0-32-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod........

DKMS: uninstall completed.

------------------------------
Deleting module version: 4.2.2
completely from the DKMS tree.
------------------------------
Done.
jason@budgie:~$ cd ~
jason@budgie:~$ sudo dkms add ./rtl8812au

Creating symlink /var/lib/dkms/8812au/4.2.2/source ->
                 /usr/src/8812au-4.2.2

DKMS: add completed.
jason@budgie:~$ sudo dkms build rtl8812au/4.2.2

Creating symlink /var/lib/dkms/rtl8812au/4.2.2/source ->
                 /usr/src/rtl8812au-4.2.2

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' all KVER=4.13.0-32-generic.......................................
cleaning build area...

DKMS: build completed.
jason@budgie:~$ sudo dkms install --force rtl8812au/4.2.2

8812au:
Running module version sanity check.
 - Original module
   - This kernel never originally had a module by this name
 - Multiple same named modules!
   - 2 named 8812au.ko in /lib/modules/4.13.0-32-generic/
 - Installation
   - Installing to /lib/modules/4.13.0-32-generic/updates/dkms/

depmod...

DKMS: install completed.
jason@budgie:~$ sudo modprobe 8812au
jason@budgie:~$ modinfo 8812au | grep 9052
alias:          usb:v0846p9052d*dc*dsc*dp*ic*isc*ip*in*

SUCCESS!!  

jason@budgie:~$ sudo dkms status
8812au, 4.2.2: added
bbswitch, 0.8, 4.13.0-32-generic, x86_64: installed
bbswitch, 0.8, 4.13.0-36-generic, x86_64: installed
kpatch, 0.3.2: added
nvidia-340, 340.104, 4.13.0-32-generic, x86_64: installed
nvidia-340, 340.104, 4.13.0-36-generic, x86_64: installed
rtl8812au, 4.2.2, 4.13.0-32-generic, x86_64: installed
rtl8812au, 4.3.8.12175.20140902+dfsg, 4.13.0-32-generic, x86_64: built

I didn't have to edit the folder name to omit the RTL in /usr/src/rtl8812au  But I'll look at that if something fails..

THANK YOU GUYS SO MUCH. I'm embarrassed to say just how long have been working on this following threads...
 
Is there anything else I need to do to prevent this from happening again when I update my kernel to avoid the recent cpu exploits?

---

### Post by chili555 on 2018-03-03
Awesome! Glad it's working! Have fun.

---

### Post by jeremy31 on 2018-03-03
I would want to remove rtl8812au-dkms as it might cause issues with the next kernel install and it doesn't support your chipset yet

---

### Post by holiday on 2018-03-03
> **jason coale said:**
> Hello, so heres the output without the AC600 adapter, using an old adapter...
jason@budgie:~$ sudo lshw -class network
[sudo] password for jason: 
  *-network                 
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 16
       serial: 00:1c:25:e5:57:6a
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:24 memory:feafc000-feafffff ioport:e800(size=256) memory:feac0000-feadffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlxe0469a16e52c
       serial: e0:46:9a:16:e5:2c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=4.13.0-32-generic firmware=1.4 ip=10.0.0.36 link=yes multicast=yes wireless=IEEE 802.11

And heres after swapping in the AC600 w/ a shutdown and reboot, but using usb tether from my cellphone....

jason@budgie:~$ sudo lshw -class network
[sudo] password for jason: 
  *-network                 
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 16
       serial: 00:1c:25:e5:57:6a
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:24 memory:feafc000-feafffff ioport:e800(size=256) memory:feac0000-feadffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: enp0s19f2u6
       serial: aa:ee:c6:65:dd:aa
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.108 link=yes multicast=yes
jason@budgie:~$

Thanks Jason

Would you do this again now that you have it working. This week I've installed three USB wireless dongles without Network Manager and have become interested. 
 
EEH

---

### Post by jason coale on 2018-03-04
Alright so, after rebooting Kpatch crashed but I'm still on the same boot. Wifi is working but its not real stable, having dropped a few times needing to reload chrome web pages a few times within an hr. also can see the wifi signal icon flicker like a candle at times.  I'll reboot as well as take Jeremys advice to keep things clean, with some guidance.

Holiday,  *-network                 
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 16
       serial: 00:1c:25:e5:57:6a
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:24 memory:feafc000-feafffff ioport:e800(size=256) memory:feac0000-feadffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:6
       logical name: enxa0046026d11b
       serial: a0:04:60:26:d1:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8812au ip=10.241.44.189 multicast=yes ***[I]wireless=IEEE 802.11bgn*[/I]**  <--No AC here. Is that due to the driver? Link speed is 72Mb on two wifi different networks..

---

### Post by chili555 on 2018-03-04
> wireless=IEEE 802.11bgn <--No AC here. Is that due to the driver?Probably, although I'm not at all certain that the notation here is significant. Here is the same from my machine; mine easily does AC:```
*-network
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 83
       serial: 5c:c5:d4:0e:64:a6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.13.0-36-generic firmware=17.608620.0 ip=192.168.0.120 latency=0 link=yes multicast=yes **wireless=IEEE 802.11**
       resources: irq:32 memory:e0400000-e0401fff

```> Wifi is working but its not real stable, having dropped a few times needing to reload chrome web pages a few timesMay we see:```
sudo iwlist scan
```We suspect WPA/WPA2 mixed mode and TKIP which your driver and old Chili both hate hate hate.

---

### Post by jason coale on 2018-03-04
> **chili555 said:**
> Probably, although I'm not at all certain that the notation here is significant. Here is the same from my machine; mine easily does AC:```
*-network
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 83
       serial: 5c:c5:d4:0e:64:a6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.13.0-36-generic firmware=17.608620.0 ip=192.168.0.120 latency=0 link=yes multicast=yes **wireless=IEEE 802.11**
       resources: irq:32 memory:e0400000-e0401fff

```May we see:```
sudo iwlist scan
```We suspect WPA/WPA2 mixed mode and TKIP which your driver and old Chili both hate hate hate.

Okay, had to go this route due to size...  

[https://paste.ubuntu.com/p/4vVfvBfGVc/](https://paste.ubuntu.com/p/4vVfvBfGVc/)

jason@budgie:~$ iwconfig
enxa0046026d11b  IEEE 802.11bgn  ESSID:"xfinitywifi"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 8A:F7:C7:CB:86:C5   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=79/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jason@budgie:~$ sudo lshw -class network
  *-network                 
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 16
       serial: 00:1c:25:e5:57:6a
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:24 memory:feafc000-feafffff ioport:e800(size=256) memory:feac0000-feadffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1
       logical name: enxa0046026d11b
       serial: a0:04:60:26:d1:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8812au ip=10.241.44.189 multicast=yes wireless=IEEE 802.11bgn

jason@budgie:~$ sudo dkms status
[sudo] password for jason: 
8812au, 4.2.2: added
bbswitch, 0.8, 4.13.0-32-generic, x86_64: installed
bbswitch, 0.8, 4.13.0-36-generic, x86_64: installed
kpatch, 0.3.2: added
nvidia-340, 340.104, 4.13.0-32-generic, x86_64: installed
nvidia-340, 340.104, 4.13.0-36-generic, x86_64: installed
rtl8812au, 4.2.2, 4.13.0-32-generic, x86_64: installed

---

### Post by chili555 on 2018-03-04
```
Cell 01 - Address: 8A:F7:C7:CB:86:C5
                    ESSID:"xfinitywifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                   [COLOR="#FF0000"] Encryption key:off[/COLOR]
                    Bit Rates:144 Mb/s
                    Quality=87/100  Signal level=66/100  
```Why not just leave your credit cards and cash in a shoebox on the front steps?

Please log on to the administration pages of the router and change the encryption to WPA2-AES, sometimes known as CCMP, and please do it immediately. This is a huge security risk on many levels.

---

### Post by jason coale on 2018-03-04
Sharshar is my home network, but lacks 5Ghz,, I connect to the xfinitywifi network sometimes when home is slow and if in Windows I can use the AC band of the adapter that we've been working on. In windows, xfinity provides a secure profile to connect thru as well as android and ios. I've tried to emulate android here in ubuntu in order to create a secure connection in a few ways such as the defunct RemixOS and some phone emulators but have pretty much failed for different reasons. Any advice on how to protect my computer if I want to connect to the open xfinitywifi hotspots,?  VPN perhaps but what ab from within Ubu? Where I just moved from had ssid:XFINITY in the city that were fast, secure and free which fits nicely with my disability income. 
Good looking out though, it's appreciated.

Cell 01 - Address: C4:27:95:4F:6C:86
                    ESSID:"sharshar"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8C0050F204104A0001101044000102103B00010310470010B8C56708C83B6FF23D0258EF405D8FD91021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
                    Quality=100/100  Signal level=83/100

---

### Post by chili555 on 2018-03-05
> IE: WPA Version 1
Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Extra:rsn_ie=30180100000fac020200000fac04000fac020 100000fac020c00
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSKExactly as I expected; WPA and WPA2 mixed mode and TKIP.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router.

---

### Post by jason coale on 2018-03-07
Thank you. Speeds are better after applying much of what I've learned from the help I've gotten here.. I've applied the driver from Artful and Here's where I'm at.. 

jason@budgie:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]

jason@budgie:~$ sudo dkms status

bbswitch, 0.8, 4.13.0-32-generic, x86_64: installed
bbswitch, 0.8, 4.13.0-36-generic, x86_64: installed
kpatch, 0.3.2: added
nvidia-340, 340.104, 4.13.0-32-generic, x86_64: installed
nvidia-340, 340.104, 4.13.0-36-generic, x86_64: installed
 
jason@budgie:~$ sudo lshw -class network
    *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1
       logical name: wlxa0046026d11b
       serial: a0:04:60:26:d1:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=8812au ip=10.0.0.28 multicast=yes wireless=IEEE 802.11

jason@budgie:~$ modinfo 8812au
filename:       /lib/modules/4.13.0-32-generic/kernel/drivers/net/wireless/8812au.ko
version:        v5.1.5_19247.20160830
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     C9C61FB257AD148370C9130

alias:          usb:v0846p9052d*dc*dsc*dp*ic*isc*ip*in*

depends:        cfg80211
name:           8812au
vermagic:       4.13.0-32-generic SMP mod_unload 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_drv_log_level:set log level when insert driver module, default log level is _DRV_INFO_ = 4 (uint)
parm:           rtw_tx_bw_mode:The max tx bw for 2.4G and 5G. format is the same as rtw_bw_mode (uint)
parm:           rtw_country_code:The default country code (in alpha2) (charp)
parm:           rtw_channel_plan:The default chplan ID when rtw_alpha2 is not specified or valid (int)
parm:           rtw_excl_chs:exclusive channel array (array of uint)
parm:           rtw_force_igi_lb:force IGI low-bound, 0:no specified (int)
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_pwrtrim_enable:int
parm:           rtw_initmac:charp
parm:           rtw_special_rf_path:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_bw_mode:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_vht_enable:int
parm:           rtw_beamform_cap:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_full_ch_in_p2p_handshake:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_drv_ant_band_switch:int
parm:           rtw_switch_usb_mode:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_check_hw_status:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           rtw_led_enable:Enable status LED (int)
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_adaptivity_dml:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_dc_backoff:DC backoff for Adaptivity (uint)
parm:           rtw_adaptivity_th_l2h_ini:TH_L2H_ini for Adaptivity (int)
parm:           rtw_adaptivity_th_edcca_hl_diff:TH_EDCCA_HL_diff for Adaptivity (int)
parm:           rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
parm:           rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
parm:           rtw_RFE_type:default init value:64 (uint)
parm:           rtw_powertracking_type:default init value:64 (uint)
parm:           rtw_GLNA_type:default init value:0 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_OffEfuseMask:default open Efuse Mask value:0 (uint)
parm:           rtw_FileMaskEfuse:default drv Mask Efuse value:0 (uint)
parm:           rtw_rxgain_offset_2g:default RF Gain 2G Offset value:0 (uint)
parm:           rtw_rxgain_offset_5gl:default RF Gain 5GL Offset value:0 (uint)
parm:           rtw_rxgain_offset_5gh:uint
parm:           rtw_rxgain_offset_5gm:default RF Gain 5GM Offset value:0 (uint)
parm:           rtw_pll_ref_clk_sel:force pll_ref_clk_sel, 0xF:use autoload value (uint)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_target_tx_pwr_2g_a:2.4G target tx power (unit:dBm) of RF path A for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_b:2.4G target tx power (unit:dBm) of RF path B for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_c:2.4G target tx power (unit:dBm) of RF path C for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_d:2.4G target tx power (unit:dBm) of RF path D for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_a:5G target tx power (unit:dBm) of RF path A for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_b:5G target tx power (unit:dBm) of RF path B for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_c:5G target tx power (unit:dBm) of RF path C for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_d:5G target tx power (unit:dBm) of RF path D for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)
jason@budgie:~$ 

The adapter still only connects only at 72Mb.. Even from my Cell set to 5ghz band.. 
How do things look now?  And thanks again, I'm learning a lot

---

### Post by chili555 on 2018-03-07
> The adapter still only connects only at 72Mb.. Even from my Cell set to 5ghz band.. 
How do things look now? And thanks again, I'm learning a lotThe connection speed is limited partially by the driver and partially by the physical device itself and, especially the size and number of antennae.

Your readings look very fine to me. Post back if we can help you further.

---

