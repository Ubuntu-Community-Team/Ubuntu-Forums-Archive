---
title: "My ethernet port is not working anymore..."
date: 2008-12-19
forum: New to Ubuntu
---

### Post by SwooshOU on 2008-12-19
I have an hp mini 1000 and installed Ubuntu 8.10.  It's been running fine.  I've been able to access the internet via wifi just fine.  Yesterday at work, I was able to access the internet via ethernet.  After some automatic updates this morning, my ethernet port is not even being recognized.

I think it used to say eth0 in the wired tab of network connections, now it doesn't say anything.  There used to be a mac id there, but now there's nothing.

Any clue on how to revive my ethernet port?

Thanks

---

### Post by Michael.Godawski on 2008-12-19
> **SwooshOU said:**
> I have an hp mini 1000 and installed Ubuntu 8.10.  It's been running fine.  I've been able to access the internet via wifi just fine.  Yesterday at work, I was able to access the internet via ethernet.  After some automatic updates this morning, my ethernet port is not even being recognized.

I think it used to say eth0 in the wired tab of network connections, now it doesn't say anything.  There used to be a mac id there, but now there's nothing.

Any clue on how to revive my ethernet port?

Thanks

Indeed that is not normal.

Can you please post the outputs from these terminal commands - might be hard without a working Internet connection, I know...:

```
sudo lshw -C network
iwconfig
ifconfig
cat /etc/network/interfaces
```

---

### Post by SwooshOU on 2008-12-19
I will post the results of those commands a little later.  I have actual work to do right now. :)

---

### Post by Michael.Godawski on 2008-12-19
no problem, but I cannot promise you that I can answer because tomorrow I am on ski-vacation in Austria and I do not take my laptop with me... :p

PS. Merry Christmas to every reader

---

### Post by SwooshOU on 2008-12-19
So, when I type the commands above, I get this:

```
remix@mini:~$ sudo lshw -C network
[sudo] password for remix: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
lshw -C network
[sudo] password for remix: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:23:4e:1c:b3:fe
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:be:06:38:e0:2c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
remix@mini:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.

remix@mini:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:23:4e:1c:b3:fe  
          inet6 addr: fe80::223:4eff:fe1c:b3fe/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:744
          TX packets:16 errors:20 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1808 (1.8 KB)  TX bytes:2288 (2.2 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:944 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47732 (47.7 KB)  TX bytes:47732 (47.7 KB)

remix@mini:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:23:4e:1c:b3:fe
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:be:06:38:e0:2c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
remix@mini:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.

remix@mini:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:23:4e:1c:b3:fe  
          inet6 addr: fe80::223:4eff:fe1c:b3fe/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:744
          TX packets:16 errors:20 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1808 (1.8 KB)  TX bytes:2288 (2.2 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:944 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47732 (47.7 KB)  TX bytes:47732 (47.7 KB)

remix@mini:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

---

### Post by Tech Wrangler on 2008-12-19
I'm having the same problem, so maybe the outputs from my computer will help:

sudo lshw -C network ->
> 
*-network DISABLED      
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair

iwconfig ->
> 
lo        no wireless extensions.

eth0      no wireless extensions.

ifconfig ->
> 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:186190 (181.8 KB)  TX bytes:186190 (181.8 KB)

cat /etc/network/interfaces ->

> auto lo
iface lo inet loopback


Other possibly helpful info:  Processor is an Athlon 64 X2, version is 8.04, computer booted to 'busybox' mode before being rebooted.  Nothing wrong with the hardware because it's a dual-boot machine and Vista had no trouble with the ethernet port.

Any help is extremely appreciated; I'm going off to do more research on this problem...

---

### Post by baAng on 2008-12-19
hello..i've tried this solution that i got from Ubuntu Documentation. I managed to enable *the wired connection and can surf the net*, but it seems like in the Network Manager the Wired Connection status don't pop up and also in the panel tray there is still X sign at the Network Manager icon.

This are the steps.

1) Open the terminal.

2) Type **sudo ifdown eth1** in the terminal and press **Enter**. 
*Replace eth1 with the name of your network interface if it is different. *

3) Enter the password if prompted.

4) Type **sudo ifup eth1** in the terminal and press **Enter**, again replacing _eth1_ with the name of your network interface.

5) If you have connected successfully, you should see a message similar to the following:

```
DHCPACK from 192.168.2.1
bound to 192.168.2.4 -- renewal in 536349522 seconds.
```

Now, you should be able to surf the net. I hope it helps.:p

---

### Post by Tech Wrangler on 2008-12-20
Thanks for the try, but that doesn't help. For the first command I get

```
ifdown: interface eth0 not configured
```

and the second

```
Ignoring unknown interface eth0=eth0.
```

Curiously, sudo is complaining 

```
sudo: unable to resolve host Vigilante
```

when processing those commands.  

The Network Tools GUI shows I have only one network device: lo.  I guess I have to reconfigure the ethernet port but I have no idea how to do that.  I also have no idea of why it just disappeared.  And as I mentioned before, it still works fine in Vista, so it's not hardware related.

I'm hoping this is a simple problem, but so far I'm mystified.

---

### Post by albinootje on 2008-12-20
> **Tech Wrangler said:**
> 
product: 88E8055 PCI-E Gigabit Ethernet Controller

Check this, at the end, about 8.10 in 2008 :
[https://bugs.staging.launchpad.net/linux/+bug/138611](https://bugs.staging.launchpad.net/linux/+bug/138611)

---

### Post by albinootje on 2008-12-20
> **SwooshOU said:**
> 
       product: 88E8040 PCI-E Fast Ethernet Controller

[https://bugs.launchpad.net/ubuntu/+bug/297263](https://bugs.launchpad.net/ubuntu/+bug/297263)
[https://bugs.launchpad.net/ubuntu/+bug/293590](https://bugs.launchpad.net/ubuntu/+bug/293590)

---

### Post by Tech Wrangler on 2008-12-20
Again, thanks, but this doesn't help.  The bug report seems to be about the ethernet port 'locking', which can be overcome by a reboot or the commands given by the other poster.  When I reboot, the ethernet is *still* down.  I'm guessing there is some file claiming ownership of the device that has to be deleted.  Or something.  Really, I have no clue.  Here's some other info that may be of interest:

I have had no problems with networking of this computer (vigilante).  It was operating in Vista when I added another Ubuntu machine (momentum) to the network (connected through a DSL router).  When I switched vigilante to Ubuntu, it started booting fine, but then stalled and went to the 'busybox' prompt.  After trying every command I could think of to resume the boot, I did a hard reset.  It took a long time to boot, but eventually made it.  But the networked was down and seems unable to get up again.

I haven't actually looked at momentum as I planned to vnc to it from vigilante.  I thought that perhaps momentum had stolen vigilante's IP, but that wouldn't take the ethernet down.  

Any help is appreciated.  I'm watching this thread pretty closely and will try to answer any questions promptly.

---

### Post by albinootje on 2008-12-20
> **Tech Wrangler said:**
> 
 When I switched vigilante to Ubuntu, it started booting fine, but then stalled and went to the 'busybox' prompt.  After trying every command I could think of to resume the boot, I did a hard reset.  It took a long time to boot, but eventually made it.

Can you check whether you have any files in /lost+found/ ?
And post the output of : 
```
lsmod|grep sky 
```

And it could be useful to file a bug-report at [http://launchpad.net](http://launchpad.net) because there are much more Ubuntu-developers reading/writing there.

---

### Post by SwooshOU on 2008-12-21
My wifi network has worked all along, so this ethernet issue wasn't a real pressing issue.  I just needed it to be working at my work where we don't have wifi, only wired networks.  Today, when I am planning to go into work, I was going to run some of the commands listed in this thread.  Strangely, I haven't done anything but use my computer normally on my wifi network at home.  I'd shut it down, suspend it and wake it up just normally.  Well, now (for whatever reason) the eth0 port is back with the settings and everything...

I'm assuming it will work fine when I go in to work, but I will report back.

Could simply restarting it have reset something?  Because I was actually able to use the ethernet a few days ago with no hitches.

Really weird.

---

### Post by albinootje on 2008-12-21
> **SwooshOU said:**
> My wifi network has worked all along, so this ethernet issue wasn't a real pressing issue.  I just needed it to be working at my work where we don't have wifi, only wired networks.  Today, when I am planning to go into work, I was going to run some of the commands listed in this thread.  Strangely, I haven't done anything but use my computer normally on my wifi network at home.  I'd shut it down, suspend it and wake it up just normally.  Well, now (for whatever reason) the eth0 port is back with the settings and everything...

I think i've seen problems like this with suspend.
You could search [http://launchpad.net](http://launchpad.net) for your NIC's chipset and similar problems.

---

### Post by SwooshOU on 2008-12-21
OK, so I'm at work and go to test out the ethernet.

Of course the eth0 setting is gone again.

How frustrating...

---

### Post by SwooshOU on 2008-12-21
I did the sudo ifdown eth0 and then sudo ifup eth0 and it tells me that that is an unknown interface.

I've looked at those launchpad bugs and as much as I can decipher it appears that there is a bug with my ethernet drivers.

I'm trying to figure out how I brought it back accidentally...  Any recommendations?

---

### Post by albinootje on 2008-12-21
> **SwooshOU said:**
> I did the sudo ifdown eth0 and then sudo ifup eth0 and it tells me that that is an unknown interface.

I've looked at those launchpad bugs and as much as I can decipher it appears that there is a bug with my ethernet drivers.

I'm trying to figure out how I brought it back accidentally...  Any recommendations?

Friend of mine had a problem with a brand new laptop:
See here : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749)
Can you try his work-around to see whether that could help ?
> 
doing a warm reboot, hit the bios, disable LAN, continue boot, surely eth0 is not there
but
do a warm reboot again, hit bios, enable LAN, continue reboot and ta-ta eth0 is working again.


---

### Post by SwooshOU on 2008-12-21
I got to the bios screen I think.  But I don't know how to enable or disable LAN.

---

### Post by albinootje on 2008-12-21
> **SwooshOU said:**
> I got to the bios screen I think.  But I don't know how to enable or disable LAN.

The line you need to look for in the BIOS is probably about "onboard LAN" or "onboard NIC".

---

### Post by SwooshOU on 2008-12-21
This is where I hit f10 on startup right?

---

### Post by albinootje on 2008-12-21
> **SwooshOU said:**
> This is where I hit f10 on startup right?

Getting into the BIOS depends per machine.
On a lot of machines it's the "DEL" key. For some others it's F2
Some older compaq machines needed F10 afair.

Usually it's shown which key you need for getting into the BIOS,
and pretty often it's called "setup" instead BIOS.

---

### Post by SwooshOU on 2008-12-21
I think I got to the Bios thing I needed to get to...

Here are my options:

Main:  Time, Date, Diagnostic Log

Security:  Set administrator password, Set power on password

System Configuration:  Language, Processor C4 State, Boot Options (Internal Network adapter boot, Boot device priority)

Diagnostic:  Memory Test

Exit

I didn't see anything related to networking or LAN or NIC or something like that except for the network boot.  But that didn't seem like the right thing.

---

### Post by albinootje on 2008-12-21
> **SwooshOU said:**
> I think I got to the Bios thing I needed to get to...

Here are my options:

Main:  Time, Date, Diagnostic Log

Security:  Set administrator password, Set power on password

System Configuration:  Language, Processor C4 State, Boot Options (Internal Network adapter boot, Boot device priority)

Diagnostic:  Memory Test

Exit

I didn't see anything related to networking or LAN or NIC or something like that except for the network boot.  But that didn't seem like the right thing.
Indeed, network boot is not what you were looking for.

Can you go in a sub-section of System Configuration ?
If so, it might be there somewhere.

By the way. Are you using a dual boot system, Linux/Windows ?
Some time ago i think i read something about certain settings for the network-card in Windows, which could cause a problem after a reboot in Linux.
Hopefully some time later i can find back that link about it.

---

### Post by albinootje on 2008-12-21
Can you try the following.
First unplug the ethernet-cable, then :
```

sudo modprobe -r sky2
sudo modprobe sky2

```
Plug the cable back in.

---

### Post by SwooshOU on 2008-12-21
> **albinootje said:**
> Can you try the following.
First unplug the ethernet-cable, then :
```

sudo modprobe -r sky2
sudo modprobe sky2

```
Plug the cable back in.

I did this.  Nothing happened.  After the first line, it asked for a password.  Then it was ready for more input.  I typed in the second line.  Again, it just went back to the regular prompt.

Someone had asked if my system was a dual boot... nope.

---

### Post by albinootje on 2008-12-21
> **SwooshOU said:**
> I did this.  Nothing happened.  After the first line, it asked for a password.  Then it was ready for more input.  I typed in the second line.  Again, it just went back to the regular prompt.

Someone had asked if my system was a dual boot... nope.

After doing this, can you please post this again :
```

lshw -c Network
route -n
ifconfig -a
cat /etc/resolv.conf
cat /etc/network/interfaces

```
Thanks in advance.

---

### Post by SwooshOU on 2008-12-21
> **albinootje said:**
> After doing this, can you please post this again :
```

lshw -c Network
route -n
ifconfig -a
cat /etc/resolv.conf
cat /etc/network/interfaces

```
Thanks in advance.

Does the network cable need to be plugged in?  And is "resolv" supposed to be spelled that way?

---

### Post by unutbu on 2008-12-21
SwooshOU, how about post ```

tail -n100 /var/log/dpkg.log | grep installed
```

This will show what packages have been installed recently. 
My quite pedestrian idea is to find the recent linux kernel update and to remove it.

---

### Post by albinootje on 2008-12-21
> **SwooshOU said:**
> Does the network cable need to be plugged in? 
 
Yes.
> And is "resolv" supposed to be spelled that way?
Yes, it is.

---

### Post by SwooshOU on 2008-12-21
```
remix@mini:~$ lshw -c Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:23:4e:1c:b3:fe
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.64 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: be:32:6b:89:a5:59
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

```
remix@mini:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth1
remix@mini:~$ 
```

```
remix@mini:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:23:4e:1c:b3:fe  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4eff:fe1c:b3fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1667 errors:0 dropped:0 overruns:0 frame:19360
          TX packets:1134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1140905 (1.1 MB)  TX bytes:265186 (265.1 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

pan0      Link encap:Ethernet  HWaddr be:32:6b:89:a5:59  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
remix@mini:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain gateway.2wire.net
search gateway.2wire.net
nameserver 192.168.1.254
```

```
remix@mini:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

There ya have it!

:)

---

### Post by albinootje on 2008-12-21
> **SwooshOU said:**
> 
There ya have it!

:)

Thanks!
So.. you have a wifi-connection but the network-interface is not really doing anything :(

Can you also post the output of 
```

tail -n100 /var/log/dpkg.log | grep installed

```
if you haven't done that in the meantime ?

And can you boot with an older kernel version in the grub menu at boot time ?
You might have to press <escape> before you see the full grub menu,
and then choose one of the other options (other than the default), but not the recovery mode ones.

---

### Post by SwooshOU on 2008-12-21
```
remix@mini:~$ tail -n100 /var/log/dpkg.log | grep installed
2008-12-19 13:47:27 status installed libopenspc0 0.3.99a-2
2008-12-19 13:47:27 status installed libsoundtouch1c2 1.3.1-2
2008-12-19 13:47:27 status installed libwildmidi0 0.2.2-2
2008-12-19 13:47:27 status installed gstreamer0.10-plugins-bad 0.10.8-1
2008-12-19 13:47:27 status installed libc6 2.8~20080505-0ubuntu7
2008-12-19 16:55:14 status half-installed gstreamer0.10-ffmpeg 0.10.5-1
2008-12-19 16:55:14 status half-installed libsidplay1 1.36.59-5
2008-12-19 16:55:15 status half-installed gstreamer0.10-plugins-ugly 0.10.9-1ubuntu0.1
2008-12-19 16:55:19 status installed gstreamer0.10-ffmpeg 0.10.5-1
2008-12-19 16:55:19 status installed libsidplay1 1.36.59-5
2008-12-19 16:55:19 status installed gstreamer0.10-plugins-ugly 0.10.9-1ubuntu0.1
2008-12-19 16:55:19 status installed libc6 2.8~20080505-0ubuntu7
2008-12-19 21:23:39 status half-installed libglib2.0-dev 2.18.2-0ubuntu2
2008-12-19 21:23:41 status half-installed libglib2.0-dev 2.18.2-0ubuntu2
2008-12-19 21:23:41 status half-installed libmono-dev 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:43 status half-installed libmono-peapi2.0-cil 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:43 status half-installed mono-2.0-devel 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:43 status half-installed mono-2.0-devel 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:44 status half-installed mono-gmcs 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:44 status half-installed mono-gmcs 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:50 status installed man-db 2.5.2-2
2008-12-19 21:23:55 status installed libglib2.0-dev 2.18.2-0ubuntu2
2008-12-19 21:23:55 status installed libmono-dev 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:55 status installed libmono-peapi2.0-cil 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:55 status installed mono-2.0-devel 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:55 status installed mono-gmcs 1.9.1+dfsg-4ubuntu2

```

---

### Post by unutbu on 2008-12-21
I misjudged how many packages you installed on 2008-12-19. How about posting:
```
grep installed /var/log/dpkg.log 
```

---

### Post by SwooshOU on 2008-12-21
```
2008-12-16 00:05:50 status installed libgnome-window-settings1 1:2.24.0.1-0ubuntu7.1
2008-12-16 00:05:50 status installed gnome-control-center 1:2.24.0.1-0ubuntu7.1
2008-12-16 00:05:50 status installed libx11-xcb1 2:1.1.5-2ubuntu1.1
2008-12-16 00:05:50 status installed compiz-wrapper 1:0.7.8-0ubuntu4.1
2008-12-16 00:05:50 status installed compiz-core 1:0.7.8-0ubuntu4.1
2008-12-16 00:05:50 status installed compiz-plugins 1:0.7.8-0ubuntu4.1
2008-12-16 00:05:55 status installed compiz-gnome 1:0.7.8-0ubuntu4.1
2008-12-16 00:06:01 status installed compiz-fusion-plugins-main 0.7.8-0ubuntu2.2
2008-12-16 00:06:03 status installed compiz 1:0.7.8-0ubuntu4.1
2008-12-16 00:06:03 status installed libcups2 1.3.9-2ubuntu3
2008-12-16 00:06:03 status installed libcupsimage2 1.3.9-2ubuntu3
2008-12-16 00:06:03 status installed cups-common 1.3.9-2ubuntu3
2008-12-16 00:06:10 status installed cups 1.3.9-2ubuntu3
2008-12-16 00:06:11 status installed cups-client 1.3.9-2ubuntu3
2008-12-16 00:06:13 status installed cups-bsd 1.3.9-2ubuntu3
2008-12-16 00:06:13 status installed libgtkhtml-editor-common 1:3.24.1.1-0ubuntu1
2008-12-16 00:06:13 status installed libebackend1.2-0 2.24.2-0ubuntu1
2008-12-16 00:06:13 status installed libecal1.2-7 2.24.2-0ubuntu1
2008-12-16 00:06:13 status installed libedata-book1.2-2 2.24.2-0ubuntu1
2008-12-16 00:06:13 status installed libedata-cal1.2-6 2.24.2-0ubuntu1
2008-12-16 00:06:13 status installed libegroupwise1.2-13 2.24.2-0ubuntu1
2008-12-16 00:06:13 status installed libgdata1.2-1 2.24.2-0ubuntu1
2008-12-16 00:06:14 status installed libgdata-google1.2-1 2.24.2-0ubuntu1
2008-12-16 00:06:14 status installed evolution-data-server-common 2.24.2-0ubuntu1
2008-12-16 00:06:14 status installed evolution-data-server 2.24.2-0ubuntu1
2008-12-16 00:06:14 status installed libedataserverui1.2-8 2.24.2-0ubuntu1
2008-12-16 00:06:14 status installed libexchange-storage1.2-3 2.24.2-0ubuntu1
2008-12-16 00:06:14 status installed libgnome-pilot2 2.0.15-2ubuntu4
2008-12-16 00:06:15 status installed libgtkhtml3.14-19 1:3.24.1.1-0ubuntu1
2008-12-16 00:06:15 status installed libgtkhtml-editor0 1:3.24.1.1-0ubuntu1
2008-12-16 00:06:15 status installed evolution-common 2.24.2-0ubuntu1
2008-12-16 00:06:30 status installed evolution 2.24.2-0ubuntu1
2008-12-16 00:06:44 status installed evolution-exchange 2.24.2-0ubuntu1
2008-12-16 00:06:48 status installed evolution-plugins 2.24.2-0ubuntu1
2008-12-16 00:06:48 status installed libgphoto2-port0 2.4.2-0ubuntu3
2008-12-16 00:06:48 status installed libgphoto2-2 2.4.2-0ubuntu3
2008-12-16 00:06:48 status installed f-spot 0.5.0.3-0ubuntu4
2008-12-16 00:06:49 status installed xulrunner-1.9 1.9.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-16 00:06:50 status installed xulrunner-1.9-gnome-support 1.9.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-16 00:06:50 status installed gdm-guest-session 0.6.1
2008-12-16 00:06:50 status installed libgtksourceview2.0-common 2.4.1-0ubuntu1
2008-12-16 00:06:50 status installed libgtksourceview2.0-0 2.4.1-0ubuntu1
2008-12-16 00:06:50 status installed gedit-common 2.24.2-0ubuntu1
2008-12-16 00:07:07 status installed gedit 2.24.2-0ubuntu1
2008-12-16 00:07:10 status installed gnome-cards-data 1:2.24.1.1-0ubuntu1
2008-12-16 00:07:23 status installed gnome-games-data 1:2.24.1.1-0ubuntu1
2008-12-16 00:07:28 status installed gnome-games 1:2.24.1.1-0ubuntu1
2008-12-16 00:07:42 status installed gnome-panel-data 1:2.24.1-0ubuntu2.1
2008-12-16 00:07:48 status installed gnome-panel 1:2.24.1-0ubuntu2.1
2008-12-16 00:08:00 status installed gnome-power-manager 2.24.0-0ubuntu8.1
2008-12-16 00:08:23 status installed gnome-terminal-data 2.24.1.1-0ubuntu1
2008-12-16 00:08:30 status installed gnome-terminal 2.24.1.1-0ubuntu1
2008-12-16 00:08:35 status installed hal-info 20081124-0ubuntu1~intrepid
2008-12-16 00:08:35 status installed human-theme 0.28.6
2008-12-16 00:08:36 status installed jockey-common 0.5~beta3-0ubuntu6.1
2008-12-16 00:08:36 status installed jockey-gtk 0.5~beta3-0ubuntu6.1
2008-12-16 00:08:36 status installed libpulse0 0.9.10-2ubuntu9.1
2008-12-16 00:08:36 status installed libasound2-plugins 1.0.17-0ubuntu5
2008-12-16 00:08:36 status installed libtrackerclient0 0.6.6-1ubuntu5.1
2008-12-16 00:08:37 status installed tracker 0.6.6-1ubuntu5.1
2008-12-16 00:08:37 status installed tracker-utils 0.6.6-1ubuntu5.1
2008-12-16 00:08:37 status installed libtracker-gtk0 0.6.6-1ubuntu5.1
2008-12-16 00:08:37 status installed tracker-search-tool 0.6.6-1ubuntu5.1
2008-12-16 00:08:37 status installed libdeskbar-tracker 0.6.6-1ubuntu5.1
2008-12-16 00:08:38 status installed libglib2.0-data 2.18.2-0ubuntu2
2008-12-16 00:08:38 status installed libnm-util0 0.7~~svn20081018t105859-0ubuntu1.8.10.1
2008-12-16 00:08:38 status installed libnm-glib0 0.7~~svn20081018t105859-0ubuntu1.8.10.1
2008-12-16 00:08:38 status installed libpulse-browse0 0.9.10-2ubuntu9.1
2008-12-16 00:08:38 status installed libpulsecore5 0.9.10-2ubuntu9.1
2008-12-16 00:08:38 status installed libshout3 2.2.2-4ubuntu1
2008-12-16 00:08:38 status installed libwbclient0 2:3.2.3-1ubuntu3.3
2008-12-16 00:08:39 status installed libsmbclient 2:3.2.3-1ubuntu3.3
2008-12-16 00:08:39 status installed libsnmp-base 5.4.1~dfsg-7.1ubuntu6.1
2008-12-16 00:08:39 status installed libsnmp15 5.4.1~dfsg-7.1ubuntu6.1
2008-12-16 00:08:39 status installed libtotem-plparser12 2.24.2-0ubuntu1
2008-12-16 00:08:39 status installed libv4l-0 0.5.6-1~intrepid1
2008-12-16 00:08:39 status installed libxml2-utils 2.6.32.dfsg-4ubuntu1.1
2008-12-16 00:08:39 status installed linux-headers-2.6.27-7 2.6.27-7.16
2008-12-16 00:08:42 status installed linux-headers-2.6.27-7-generic 2.6.27-7.16
2008-12-16 00:08:42 status installed linux-headers-2.6.27-9 2.6.27-9.19
2008-12-16 00:08:44 status installed linux-headers-2.6.27-9-generic 2.6.27-9.19
2008-12-16 00:08:44 status installed linux-headers-generic 2.6.27.9.13
2008-12-16 00:08:44 status installed linux-libc-dev 2.6.27-9.19
2008-12-16 00:08:46 status installed network-manager 0.7~~svn20081018t105859-0ubuntu1.8.10.1
2008-12-16 00:08:46 status installed network-manager-gnome 0.7~~svn20081020t000444-0ubuntu1.8.10.1
2008-12-16 00:08:46 status installed nvidia-96-modaliases 96.43.09-0ubuntu1
2008-12-16 00:08:46 status installed pm-utils 1.1.2.4-1ubuntu8
2008-12-16 00:08:46 status installed pulseaudio 0.9.10-2ubuntu9.1
2008-12-16 00:08:46 status installed pulseaudio-esound-compat 0.9.10-2ubuntu9.1
2008-12-16 00:08:46 status installed pulseaudio-module-gconf 0.9.10-2ubuntu9.1
2008-12-16 00:08:46 status installed pulseaudio-module-hal 0.9.10-2ubuntu9.1
2008-12-16 00:08:46 status installed pulseaudio-utils 0.9.10-2ubuntu9.1
2008-12-16 00:08:47 status installed pulseaudio-module-x11 0.9.10-2ubuntu9.1
2008-12-16 00:08:47 status installed python-libxml2 2.6.32.dfsg-4ubuntu1.1
2008-12-16 00:08:47 status installed python-software-properties 0.68.1
2008-12-16 00:08:49 status installed rhythmbox 0.11.6svn20081008-0ubuntu4.2
2008-12-16 00:08:55 status installed samba-common 2:3.2.3-1ubuntu3.3
2008-12-16 00:08:55 status installed smbclient 2:3.2.3-1ubuntu3.3
2008-12-16 00:08:57 status installed software-properties-gtk 0.68.1
2008-12-16 00:08:58 status installed splix 2.0.0~rc2-0ubuntu2.3
2008-12-16 00:08:58 status installed system-tools-backends 2.6.0-1ubuntu1.1
2008-12-16 00:09:11 status installed totem-common 2.24.3-0ubuntu1
2008-12-16 00:09:23 status installed totem-gstreamer 2.24.3-0ubuntu1
2008-12-16 00:09:23 status installed totem-plugins 2.24.3-0ubuntu1
2008-12-16 00:09:23 status installed totem 2.24.3-0ubuntu1
2008-12-16 00:09:23 status installed totem-mozilla 2.24.3-0ubuntu1
2008-12-16 00:09:24 status installed transmission-common 1.34-0ubuntu2.1
2008-12-16 00:09:24 status installed transmission-gtk 1.34-0ubuntu2.1
2008-12-16 00:09:34 status installed vinagre 2.24.1-0ubuntu1.1
2008-12-16 00:09:40 status installed xserver-xorg-input-evdev 1:2.0.99+git20080912-0ubuntu6
2008-12-16 00:09:40 status installed xserver-xorg-input-vmmouse 1:12.5.1-1ubuntu5.1
2008-12-16 00:09:46 status installed gnome-pilot 2.0.15-2ubuntu4
2008-12-16 00:09:49 status installed openoffice.org-core 1:2.4.1-11ubuntu2.1
2008-12-16 00:09:49 status installed openoffice.org-calc 1:2.4.1-11ubuntu2.1
2008-12-16 00:09:49 status installed openoffice.org-draw 1:2.4.1-11ubuntu2.1
2008-12-16 00:09:50 status installed openoffice.org-impress 1:2.4.1-11ubuntu2.1
2008-12-16 00:09:51 status installed python-uno 1:2.4.1-11ubuntu2.1
2008-12-16 00:09:52 status installed openoffice.org-math 1:2.4.1-11ubuntu2.1
2008-12-16 00:09:52 status installed openoffice.org-writer 1:2.4.1-11ubuntu2.1
2008-12-16 00:09:57 status installed openoffice.org-emailmerge 1:2.4.1-11ubuntu2.1
2008-12-16 00:09:58 status installed firefox-3.0-branding 3.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-16 00:09:58 status installed firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-16 00:09:58 status installed firefox-3.0-gnome-support 3.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-16 00:09:58 status installed firefox 3.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-16 00:09:58 status installed firefox-gnome-support 3.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-16 00:09:58 status installed ubufox 0.6-0ubuntu1.8.10.1
2008-12-16 00:09:58 status installed language-pack-en 1:8.10+20081107
2008-12-16 00:09:58 status installed language-pack-gnome-en 1:8.10+20081107
2008-12-16 00:09:58 status installed initramfs-tools 0.92bubuntu16
2008-12-16 00:09:59 status installed udev 124-9
2008-12-16 00:10:53 status installed linux-image-2.6.27-7-generic 2.6.27-7.16
2008-12-16 00:11:40 status installed linux-image-2.6.27-9-generic 2.6.27-9.19
2008-12-16 00:12:16 status installed linux-restricted-modules-2.6.27-9-generic 2.6.27-9.13
2008-12-16 00:12:17 status installed openoffice.org-style-human 1:2.4.1-11ubuntu2.1
2008-12-16 00:12:18 status installed openoffice.org-common 1:2.4.1-11ubuntu2.1
2008-12-16 00:12:19 status installed openoffice.org-gtk 1:2.4.1-11ubuntu2.1
2008-12-16 00:12:19 status installed openoffice.org-gnome 1:2.4.1-11ubuntu2.1
2008-12-16 00:12:25 status installed console-setup 1.25ubuntu4
2008-12-16 00:12:25 status installed linux-image-generic 2.6.27.9.13
2008-12-16 00:12:25 status installed linux-restricted-modules-generic 2.6.27.9.13
2008-12-16 00:12:25 status installed linux-generic 2.6.27.9.13
2008-12-16 00:13:13 status installed language-pack-en-base 1:8.10+20081107
2008-12-16 00:13:13 status installed language-pack-gnome-en-base 1:8.10+20081107
2008-12-16 00:13:14 status installed libc6 2.8~20080505-0ubuntu7
2008-12-16 00:13:14 status installed python-support 0.8.4
2008-12-16 00:13:45 status installed initramfs-tools 0.92bubuntu16
2008-12-16 07:40:42 status half-installed adobe-flashplugin 10.0.12.36-1hardy1
2008-12-16 07:40:45 status installed adobe-flashplugin 10.0.12.36-1hardy1
2008-12-16 08:01:29 status half-installed libaudio2 1.9.1-4
2008-12-16 08:01:30 status half-installed libqt3-mt 3:3.3.8-b-5ubuntu1
2008-12-16 08:01:35 status installed libaudio2 1.9.1-4
2008-12-16 08:01:35 status installed libqt3-mt 3:3.3.8-b-5ubuntu1
2008-12-16 08:01:36 status installed libc6 2.8~20080505-0ubuntu7
2008-12-16 08:01:37 status half-installed opera 9.63.2474.gcc4.qt3
2008-12-16 08:01:40 status half-installed opera 9.63.2474.gcc4.qt3
2008-12-16 08:01:44 status installed opera 9.63.2474.gcc4.qt3
2008-12-16 08:01:44 status installed man-db 2.5.2-2
2008-12-16 17:03:59 status half-installed go-home-applet 0.2-0ubuntu1
2008-12-16 17:04:01 status half-installed human-netbook-theme 0.7~ppa1
2008-12-16 17:04:02 status half-installed libclutter-0.8-0 0.8.2-0ubuntu1
2008-12-16 17:04:02 status half-installed libclutter-gtk-0.8-0 0.8.2-0ubuntu1
2008-12-16 17:04:03 status half-installed libfakekey0 0.1-1
2008-12-16 17:04:03 status half-installed maximus 0.4.2~ppa1
2008-12-16 17:04:03 status half-installed maximus 0.4.2~ppa1
2008-12-16 17:04:03 status half-installed netbook-launcher 1.5.1~ppa1
2008-12-16 17:04:03 status half-installed netbook-launcher 1.5.1~ppa1
2008-12-16 17:04:05 status half-installed window-picker-applet 0.4.5~ppa1
2008-12-16 17:04:15 status installed man-db 2.5.2-2
2008-12-16 17:04:18 status installed go-home-applet 0.2-0ubuntu1
2008-12-16 17:04:19 status installed human-netbook-theme 0.7~ppa1
2008-12-16 17:04:19 status installed libclutter-0.8-0 0.8.2-0ubuntu1
2008-12-16 17:04:19 status installed libclutter-gtk-0.8-0 0.8.2-0ubuntu1
2008-12-16 17:04:20 status installed libfakekey0 0.1-1
2008-12-16 17:04:21 status installed maximus 0.4.2~ppa1
2008-12-16 17:04:22 status installed netbook-launcher 1.5.1~ppa1
2008-12-16 17:04:23 status installed window-picker-applet 0.4.5~ppa1
2008-12-16 17:04:24 status installed libc6 2.8~20080505-0ubuntu7
2008-12-16 17:22:01 status half-installed metacity-common 1:2.24.0-0ubuntu1
2008-12-16 17:22:03 status half-installed metacity-common 1:2.24.0-0ubuntu1
2008-12-16 17:22:03 status half-installed metacity-common 1:2.24.0-0ubuntu1
2008-12-16 17:22:05 status half-installed libmetacity0 1:2.24.0-0ubuntu1
2008-12-16 17:22:05 status half-installed libmetacity0 1:2.24.0-0ubuntu1
2008-12-16 17:22:05 status half-installed metacity 1:2.24.0-0ubuntu1
2008-12-16 17:22:05 status half-installed metacity 1:2.24.0-0ubuntu1
2008-12-16 17:22:06 status installed man-db 2.5.2-2
2008-12-16 17:22:25 status installed metacity-common 1:2.24.0-0ubuntu1netbook1
2008-12-16 17:22:28 status installed libmetacity0 1:2.24.0-0ubuntu1netbook1
2008-12-16 17:22:29 status installed metacity 1:2.24.0-0ubuntu1netbook1
2008-12-16 17:22:29 status installed libc6 2.8~20080505-0ubuntu7
2008-12-16 21:06:54 status half-installed mysql-common 5.0.67-0ubuntu6
2008-12-16 21:06:54 status half-installed libmysqlclient15off 5.0.67-0ubuntu6
2008-12-16 21:06:56 status half-installed libqtcore4 4.4.3-0ubuntu1.1
2008-12-16 21:06:59 status half-installed libqt4-network 4.4.3-0ubuntu1.1
2008-12-16 21:07:00 status half-installed libqt4-assistant 4.4.3-0ubuntu1.1
2008-12-16 21:07:00 status half-installed libqt4-xml 4.4.3-0ubuntu1.1
2008-12-16 21:07:00 status half-installed libqt4-dbus 4.4.3-0ubuntu1.1
2008-12-16 21:07:01 status half-installed libqt4-script 4.4.3-0ubuntu1.1
2008-12-16 21:07:01 status half-installed libqt4-test 4.4.3-0ubuntu1.1
2008-12-16 21:07:02 status half-installed libqt4-core 4.4.3-0ubuntu1.1
2008-12-16 21:07:02 status half-installed libqtgui4 4.4.3-0ubuntu1.1
2008-12-16 21:07:04 status half-installed libqt4-designer 4.4.3-0ubuntu1.1
2008-12-16 21:07:06 status half-installed libqt4-svg 4.4.3-0ubuntu1.1
2008-12-16 21:07:06 status half-installed libqt4-opengl 4.4.3-0ubuntu1.1
2008-12-16 21:07:07 status half-installed libqt4-gui 4.4.3-0ubuntu1.1
2008-12-16 21:07:07 status half-installed libqt4-sql 4.4.3-0ubuntu1.1
2008-12-16 21:07:07 status half-installed libqt4-qt3support 4.4.3-0ubuntu1.1
2008-12-16 21:07:08 status half-installed libqt4-sql-mysql 4.4.3-0ubuntu1.1
2008-12-16 21:07:08 status half-installed qt4-qtconfig 4.4.3-0ubuntu1.1
2008-12-16 21:07:09 status half-installed qt4-qtconfig 4.4.3-0ubuntu1.1
2008-12-16 21:07:10 status installed man-db 2.5.2-2
2008-12-16 21:07:13 status installed mysql-common 5.0.67-0ubuntu6
2008-12-16 21:07:13 status installed libmysqlclient15off 5.0.67-0ubuntu6
2008-12-16 21:07:14 status installed libqtcore4 4.4.3-0ubuntu1.1
2008-12-16 21:07:14 status installed libqt4-network 4.4.3-0ubuntu1.1
2008-12-16 21:07:14 status installed libqt4-assistant 4.4.3-0ubuntu1.1
2008-12-16 21:07:14 status installed libqt4-xml 4.4.3-0ubuntu1.1
2008-12-16 21:07:14 status installed libqt4-dbus 4.4.3-0ubuntu1.1
2008-12-16 21:07:14 status installed libqt4-script 4.4.3-0ubuntu1.1
2008-12-16 21:07:15 status installed libqt4-test 4.4.3-0ubuntu1.1
2008-12-16 21:07:15 status installed libqt4-core 4.4.3-0ubuntu1.1
2008-12-16 21:07:15 status installed libqtgui4 4.4.3-0ubuntu1.1
2008-12-16 21:07:15 status installed libqt4-designer 4.4.3-0ubuntu1.1
2008-12-16 21:07:15 status installed libqt4-svg 4.4.3-0ubuntu1.1
2008-12-16 21:07:15 status installed libqt4-opengl 4.4.3-0ubuntu1.1
2008-12-16 21:07:15 status installed libqt4-gui 4.4.3-0ubuntu1.1
2008-12-16 21:07:15 status installed libqt4-sql 4.4.3-0ubuntu1.1
2008-12-16 21:07:15 status installed libqt4-qt3support 4.4.3-0ubuntu1.1
2008-12-16 21:07:15 status installed libqt4-sql-mysql 4.4.3-0ubuntu1.1
2008-12-16 21:07:16 status installed qt4-qtconfig 4.4.3-0ubuntu1.1
2008-12-16 21:07:16 status installed libc6 2.8~20080505-0ubuntu7
2008-12-16 21:07:18 status half-installed skype 2.0.0.72-1
2008-12-16 21:07:32 status installed skype 2.0.0.72-1
2008-12-17 16:51:57 status half-installed liba52-0.7.4 0.7.4-11ubuntu1
2008-12-17 16:51:58 status half-installed libavutil49 3:0.svn20080206-12ubuntu3
2008-12-17 16:51:58 status half-installed libgsm1 1.0.12-1
2008-12-17 16:51:59 status half-installed libavcodec51 3:0.svn20080206-12ubuntu3
2008-12-17 16:52:00 status half-installed libavformat52 3:0.svn20080206-12ubuntu3
2008-12-17 16:52:01 status half-installed libdvbpsi4 0.1.5-3.1
2008-12-17 16:52:01 status half-installed libdvdread3 0.9.7-11ubuntu2
2008-12-17 16:52:02 status half-installed libdvdnav4 4.1.2-3
2008-12-17 16:52:02 status half-installed libebml0 0.7.7-3.1
2008-12-17 16:52:02 status half-installed libenca0 1.9-6
2008-12-17 16:52:03 status half-installed libfaad0 2.6.1-3.1
2008-12-17 16:52:03 status half-installed libid3tag0 0.15.1b-10
2008-12-17 16:52:03 status half-installed libiso9660-5 0.78.2+dfsg1-3
2008-12-17 16:52:04 status half-installed liblua5.1-0 5.1.3-1
2008-12-17 16:52:04 status half-installed libmad0 0.15.1b-3
2008-12-17 16:52:04 status half-installed libmatroska0 0.8.1-1.1
2008-12-17 16:52:04 status half-installed libmodplug0c2 1:0.7-7
2008-12-17 16:52:05 status half-installed libmpcdec3 1.2.2-1build1
2008-12-17 16:52:05 status half-installed libmpeg2-4 0.4.1-3
2008-12-17 16:52:05 status half-installed libpostproc51 3:0.svn20080206-12ubuntu3
2008-12-17 16:52:06 status half-installed libsdl-image1.2 1.2.6-3
2008-12-17 16:52:06 status half-installed libswscale0 3:0.svn20080206-12ubuntu3
2008-12-17 16:52:06 status half-installed libtar 1.2.11-5
2008-12-17 16:52:07 status half-installed libtwolame0 0.3.12-1
2008-12-17 16:52:07 status half-installed libvcdinfo0 0.7.23-4ubuntu1
2008-12-17 16:52:07 status half-installed vlc-data 0.9.4-1ubuntu3
2008-12-17 16:52:22 status half-installed libvlccore0 0.9.4-1ubuntu3
2008-12-17 16:52:23 status half-installed libvlc2 0.9.4-1ubuntu3
2008-12-17 16:52:24 status half-installed libx264-59 1:0.svn20080408-0.0ubuntu1
2008-12-17 16:52:24 status half-installed libdca0 0.0.5-0.1
2008-12-17 16:52:25 status half-installed libdca0 0.0.5-0.1
2008-12-17 16:52:25 status half-installed vlc-nox 0.9.4-1ubuntu3
2008-12-17 16:52:25 status half-installed vlc-nox 0.9.4-1ubuntu3
2008-12-17 16:52:27 status half-installed libass1 0.9.5-0ubuntu2
2008-12-17 16:52:27 status half-installed vlc 0.9.4-1ubuntu3
2008-12-17 16:52:27 status half-installed vlc 0.9.4-1ubuntu3
2008-12-17 16:52:29 status half-installed mozilla-plugin-vlc 0.9.4-1ubuntu3
2008-12-17 16:52:29 status half-installed vlc-plugin-esd 0.9.4-1ubuntu3
2008-12-17 16:52:31 status installed man-db 2.5.2-2
2008-12-17 16:52:33 status installed liba52-0.7.4 0.7.4-11ubuntu1
2008-12-17 16:52:33 status installed libavutil49 3:0.svn20080206-12ubuntu3
2008-12-17 16:52:33 status installed libgsm1 1.0.12-1
2008-12-17 16:52:33 status installed libavcodec51 3:0.svn20080206-12ubuntu3
2008-12-17 16:52:33 status installed libavformat52 3:0.svn20080206-12ubuntu3
2008-12-17 16:52:33 status installed libdvbpsi4 0.1.5-3.1
2008-12-17 16:52:33 status installed libdvdread3 0.9.7-11ubuntu2
2008-12-17 16:52:34 status installed libdvdnav4 4.1.2-3
2008-12-17 16:52:34 status installed libebml0 0.7.7-3.1
2008-12-17 16:52:34 status installed libenca0 1.9-6
2008-12-17 16:52:34 status installed libfaad0 2.6.1-3.1
2008-12-17 16:52:34 status installed libid3tag0 0.15.1b-10
2008-12-17 16:52:34 status installed libiso9660-5 0.78.2+dfsg1-3
2008-12-17 16:52:35 status installed liblua5.1-0 5.1.3-1
2008-12-17 16:52:35 status installed libmad0 0.15.1b-3
2008-12-17 16:52:35 status installed libmatroska0 0.8.1-1.1
2008-12-17 16:52:35 status installed libmodplug0c2 1:0.7-7
2008-12-17 16:52:35 status installed libmpcdec3 1.2.2-1build1
2008-12-17 16:52:35 status installed libmpeg2-4 0.4.1-3
2008-12-17 16:52:35 status installed libpostproc51 3:0.svn20080206-12ubuntu3
2008-12-17 16:52:36 status installed libsdl-image1.2 1.2.6-3
2008-12-17 16:52:36 status installed libswscale0 3:0.svn20080206-12ubuntu3
2008-12-17 16:52:36 status installed libtar 1.2.11-5
2008-12-17 16:52:36 status installed libtwolame0 0.3.12-1
2008-12-17 16:52:36 status installed libvcdinfo0 0.7.23-4ubuntu1
2008-12-17 16:52:36 status installed vlc-data 0.9.4-1ubuntu3
2008-12-17 16:52:37 status installed libvlccore0 0.9.4-1ubuntu3
2008-12-17 16:52:37 status installed libvlc2 0.9.4-1ubuntu3
2008-12-17 16:52:37 status installed libx264-59 1:0.svn20080408-0.0ubuntu1
2008-12-17 16:52:37 status installed libdca0 0.0.5-0.1
2008-12-17 16:52:37 status installed vlc-nox 0.9.4-1ubuntu3
2008-12-17 16:52:37 status installed libass1 0.9.5-0ubuntu2
2008-12-17 16:52:38 status installed vlc 0.9.4-1ubuntu3
2008-12-17 16:52:38 status installed mozilla-plugin-vlc 0.9.4-1ubuntu3
2008-12-17 16:52:38 status installed vlc-plugin-esd 0.9.4-1ubuntu3
2008-12-17 16:52:38 status installed libc6 2.8~20080505-0ubuntu7
2008-12-17 16:58:49 status half-installed adobe-flashplugin 10.0.12.36-1hardy1
2008-12-17 16:58:50 status half-installed adobe-flashplugin 10.0.12.36-1hardy1
2008-12-17 16:58:51 status half-installed libcups2 1.3.9-2ubuntu3
2008-12-17 16:58:51 status half-installed libcups2 1.3.9-2ubuntu3
2008-12-17 16:58:52 status half-installed libcupsimage2 1.3.9-2ubuntu3
2008-12-17 16:58:52 status half-installed libcupsimage2 1.3.9-2ubuntu3
2008-12-17 16:58:52 status half-installed cups-common 1.3.9-2ubuntu3
2008-12-17 16:58:53 status half-installed cups-common 1.3.9-2ubuntu3
2008-12-17 16:58:54 status half-installed cups 1.3.9-2ubuntu3
2008-12-17 16:58:57 status half-installed cups 1.3.9-2ubuntu3
2008-12-17 16:58:57 status half-installed cups 1.3.9-2ubuntu3
2008-12-17 16:58:58 status half-installed cups 1.3.9-2ubuntu3
2008-12-17 16:58:58 status half-installed cups 1.3.9-2ubuntu3
2008-12-17 16:59:01 status half-installed cups-bsd 1.3.9-2ubuntu3
2008-12-17 16:59:01 status half-installed cups-bsd 1.3.9-2ubuntu3
2008-12-17 16:59:01 status half-installed cups-bsd 1.3.9-2ubuntu3
2008-12-17 16:59:01 status half-installed cups-client 1.3.9-2ubuntu3
2008-12-17 16:59:01 status half-installed cups-client 1.3.9-2ubuntu3
2008-12-17 16:59:01 status half-installed cups-client 1.3.9-2ubuntu3
2008-12-17 16:59:02 status installed doc-base 0.8.16
2008-12-17 16:59:05 status installed man-db 2.5.2-2
2008-12-17 16:59:07 status installed ufw 0.23.2
2008-12-17 16:59:10 status installed adobe-flashplugin 10.0.12.36-1intrepid2
2008-12-17 16:59:10 status installed libcups2 1.3.9-2ubuntu4
2008-12-17 16:59:11 status installed libcupsimage2 1.3.9-2ubuntu4
2008-12-17 16:59:11 status installed cups-common 1.3.9-2ubuntu4
2008-12-17 16:59:17 status installed cups 1.3.9-2ubuntu4
2008-12-17 16:59:18 status installed cups-client 1.3.9-2ubuntu4
2008-12-17 16:59:19 status installed cups-bsd 1.3.9-2ubuntu4
2008-12-17 16:59:20 status installed libc6 2.8~20080505-0ubuntu7
2008-12-18 07:45:35 status half-installed login 1:4.1.1-1ubuntu1.1
2008-12-18 07:45:35 status half-installed login 1:4.1.1-1ubuntu1.1
2008-12-18 07:45:35 status half-installed login 1:4.1.1-1ubuntu1.1
2008-12-18 07:45:39 status installed man-db 2.5.2-2
2008-12-18 07:45:41 status installed login 1:4.1.1-1ubuntu1.2
2008-12-18 07:45:43 status half-installed passwd 1:4.1.1-1ubuntu1.1
2008-12-18 07:45:44 status half-installed passwd 1:4.1.1-1ubuntu1.1
2008-12-18 07:45:44 status half-installed passwd 1:4.1.1-1ubuntu1.1
2008-12-18 07:46:04 status installed man-db 2.5.2-2
2008-12-18 07:46:06 status installed passwd 1:4.1.1-1ubuntu1.2
2008-12-18 07:46:11 status half-installed adobe-flashplugin 10.0.12.36-1intrepid2
2008-12-18 07:46:12 status half-installed adobe-flashplugin 10.0.12.36-1intrepid2
2008-12-18 07:46:13 status half-installed firefox-3.0-branding 3.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:13 status half-installed firefox-3.0-branding 3.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:14 status half-installed xulrunner-1.9-gnome-support 1.9.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:14 status half-installed xulrunner-1.9-gnome-support 1.9.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:16 status half-installed xulrunner-1.9 1.9.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:20 status half-installed xulrunner-1.9 1.9.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:24 status half-installed firefox-3.0-gnome-support 3.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:24 status half-installed firefox-3.0-gnome-support 3.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:25 status half-installed firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:25 status half-installed firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:27 status half-installed firefox 3.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:27 status half-installed firefox 3.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:28 status half-installed firefox-gnome-support 3.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:28 status half-installed firefox-gnome-support 3.0.4+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:28 status half-installed libgadu3 1:1.8.0+r592-1
2008-12-18 07:46:28 status half-installed libgadu3 1:1.8.0+r592-1
2008-12-18 07:46:29 status half-installed liblcms1 1.16-10
2008-12-18 07:46:29 status half-installed liblcms1 1.16-10
2008-12-18 07:46:32 status installed adobe-flashplugin 10.0.15.3-1intrepid2
2008-12-18 07:46:48 status installed xulrunner-1.9 1.9.0.5+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:48 status installed xulrunner-1.9-gnome-support 1.9.0.5+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:48 status installed libgadu3 1:1.8.0+r592-1ubuntu0.1
2008-12-18 07:46:48 status installed liblcms1 1.16-10ubuntu0.1
2008-12-18 07:46:48 status installed firefox-3.0-branding 3.0.5+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:49 status installed firefox-3.0 3.0.5+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:49 status installed firefox-3.0-gnome-support 3.0.5+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:49 status installed firefox 3.0.5+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:49 status installed firefox-gnome-support 3.0.5+nobinonly-0ubuntu0.8.10.1
2008-12-18 07:46:50 status installed libc6 2.8~20080505-0ubuntu7
2008-12-19 07:43:16 status half-installed avahi-autoipd 0.6.23-2ubuntu2
2008-12-19 07:43:16 status half-installed avahi-autoipd 0.6.23-2ubuntu2
2008-12-19 07:43:16 status half-installed avahi-autoipd 0.6.23-2ubuntu2
2008-12-19 07:43:16 status half-installed libavahi-common-data 0.6.23-2ubuntu2
2008-12-19 07:43:17 status half-installed libavahi-common-data 0.6.23-2ubuntu2
2008-12-19 07:43:17 status half-installed libavahi-common3 0.6.23-2ubuntu2
2008-12-19 07:43:17 status half-installed libavahi-common3 0.6.23-2ubuntu2
2008-12-19 07:43:17 status half-installed libavahi-core5 0.6.23-2ubuntu2
2008-12-19 07:43:18 status half-installed libavahi-core5 0.6.23-2ubuntu2
2008-12-19 07:43:18 status half-installed avahi-daemon 0.6.23-2ubuntu2
2008-12-19 07:43:18 status half-installed avahi-daemon 0.6.23-2ubuntu2
2008-12-19 07:43:19 status half-installed avahi-daemon 0.6.23-2ubuntu2
2008-12-19 07:43:20 status half-installed libavahi-client3 0.6.23-2ubuntu2
2008-12-19 07:43:20 status half-installed libavahi-client3 0.6.23-2ubuntu2
2008-12-19 07:43:20 status half-installed avahi-utils 0.6.23-2ubuntu2
2008-12-19 07:43:20 status half-installed avahi-utils 0.6.23-2ubuntu2
2008-12-19 07:43:20 status half-installed avahi-utils 0.6.23-2ubuntu2
2008-12-19 07:43:21 status half-installed libavahi-compat-libdnssd1 0.6.23-2ubuntu2
2008-12-19 07:43:21 status half-installed libavahi-compat-libdnssd1 0.6.23-2ubuntu2
2008-12-19 07:43:21 status half-installed libavahi-glib1 0.6.23-2ubuntu2
2008-12-19 07:43:21 status half-installed libavahi-glib1 0.6.23-2ubuntu2
2008-12-19 07:43:21 status half-installed libavahi-gobject0 0.6.23-2ubuntu2
2008-12-19 07:43:21 status half-installed libavahi-gobject0 0.6.23-2ubuntu2
2008-12-19 07:43:22 status half-installed libavahi-ui0 0.6.23-2ubuntu2
2008-12-19 07:43:22 status half-installed libavahi-ui0 0.6.23-2ubuntu2
2008-12-19 07:43:23 status installed man-db 2.5.2-2
2008-12-19 07:43:25 status installed avahi-autoipd 0.6.23-2ubuntu2.1
2008-12-19 07:43:25 status installed libavahi-common-data 0.6.23-2ubuntu2.1
2008-12-19 07:43:25 status installed libavahi-common3 0.6.23-2ubuntu2.1
2008-12-19 07:43:25 status installed libavahi-core5 0.6.23-2ubuntu2.1
2008-12-19 07:43:25 status installed avahi-daemon 0.6.23-2ubuntu2.1
2008-12-19 07:43:26 status installed libavahi-client3 0.6.23-2ubuntu2.1
2008-12-19 07:43:26 status installed avahi-utils 0.6.23-2ubuntu2.1
2008-12-19 07:43:26 status installed libavahi-compat-libdnssd1 0.6.23-2ubuntu2.1
2008-12-19 07:43:26 status installed libavahi-glib1 0.6.23-2ubuntu2.1
2008-12-19 07:43:26 status installed libavahi-gobject0 0.6.23-2ubuntu2.1
2008-12-19 07:43:26 status installed libavahi-ui0 0.6.23-2ubuntu2.1
2008-12-19 07:43:28 status installed libc6 2.8~20080505-0ubuntu7
2008-12-19 13:38:16 status half-installed libartsc0 1.5.10-0ubuntu1
2008-12-19 13:38:17 status half-installed libfaac0 1.26-0.1ubuntu2
2008-12-19 13:38:17 status half-installed libfreebob0 1.0.11-0ubuntu1
2008-12-19 13:38:18 status half-installed libgii1 1:1.0.2-2
2008-12-19 13:38:18 status half-installed libgii1 1:1.0.2-2
2008-12-19 13:38:19 status half-installed libglide2 2002.04.10-16ubuntu2
2008-12-19 13:38:19 status half-installed libsvga1 1:1.4.3-27
2008-12-19 13:38:20 status half-installed libsvga1 1:1.4.3-27
2008-12-19 13:38:20 status half-installed libggi2 1:2.2.2-1ubuntu1
2008-12-19 13:38:20 status half-installed libggi2 1:2.2.2-1ubuntu1
2008-12-19 13:38:21 status half-installed libgii1-target-x 1:1.0.2-2
2008-12-19 13:38:21 status half-installed libggi-target-x 1:2.2.2-1ubuntu1
2008-12-19 13:38:21 status half-installed libggi-target-x 1:2.2.2-1ubuntu1
2008-12-19 13:38:22 status half-installed libjack0 0.109.2-3ubuntu1
2008-12-19 13:38:22 status half-installed liblzo2-2 2.03-1
2008-12-19 13:38:23 status half-installed libmp3lame0 3.98-0.0
2008-12-19 13:38:23 status half-installed libxvidcore4 2:1.1.2-0.1ubuntu3
2008-12-19 13:38:23 status half-installed libxvmc1 2:1.0.4-2ubuntu1
2008-12-19 13:38:24 status half-installed libopenal1 1:1.3.253-4ubuntu1
2008-12-19 13:38:24 status half-installed mplayer-skins 2-7
2008-12-19 13:38:24 status half-installed ttf-dejavu-extra 2.25-1
2008-12-19 13:38:26 status half-installed ttf-dejavu 2.25-1
2008-12-19 13:38:26 status half-installed mplayer 2:1.0~rc2-0ubuntu17
2008-12-19 13:38:27 status half-installed mplayer 2:1.0~rc2-0ubuntu17
2008-12-19 13:38:30 status half-installed mozilla-mplayer 3.55-1ubuntu2
2008-12-19 13:38:49 status installed man-db 2.5.2-2
2008-12-19 13:38:51 status installed libartsc0 1.5.10-0ubuntu1
2008-12-19 13:38:51 status installed libfaac0 1.26-0.1ubuntu2
2008-12-19 13:38:51 status installed libfreebob0 1.0.11-0ubuntu1
2008-12-19 13:38:51 status installed libgii1 1:1.0.2-2
2008-12-19 13:38:57 status installed libglide2 2002.04.10-16ubuntu2
2008-12-19 13:38:58 status installed libsvga1 1:1.4.3-27
2008-12-19 13:38:58 status installed libggi2 1:2.2.2-1ubuntu1
2008-12-19 13:38:58 status installed libgii1-target-x 1:1.0.2-2
2008-12-19 13:38:58 status installed libggi-target-x 1:2.2.2-1ubuntu1
2008-12-19 13:38:58 status installed libjack0 0.109.2-3ubuntu1
2008-12-19 13:38:58 status installed liblzo2-2 2.03-1
2008-12-19 13:38:58 status installed libmp3lame0 3.98-0.0
2008-12-19 13:38:59 status installed libxvidcore4 2:1.1.2-0.1ubuntu3
2008-12-19 13:38:59 status installed libxvmc1 2:1.0.4-2ubuntu1
2008-12-19 13:38:59 status installed libopenal1 1:1.3.253-4ubuntu1
2008-12-19 13:38:59 status installed mplayer-skins 2-7
2008-12-19 13:39:15 status installed ttf-dejavu-extra 2.25-1
2008-12-19 13:39:16 status installed ttf-dejavu 2.25-1
2008-12-19 13:39:16 status installed mplayer 2:1.0~rc2-0ubuntu17
2008-12-19 13:39:17 status installed mozilla-mplayer 3.55-1ubuntu2
2008-12-19 13:39:17 status installed libc6 2.8~20080505-0ubuntu7
2008-12-19 13:47:04 status half-installed freepats 20060219-1
2008-12-19 13:47:11 status half-installed libcdaudio1 0.99.12p2-5
2008-12-19 13:47:11 status half-installed libdc1394-22 2.0.2-1
2008-12-19 13:47:13 status half-installed libgmyth0 1:0.7.1-1
2008-12-19 13:47:13 status half-installed libiptcdata0 1.0.2+libtool01-2
2008-12-19 13:47:14 status half-installed libmms0 0.4-2
2008-12-19 13:47:15 status half-installed libneon27-gnutls 0.28.2-2build1
2008-12-19 13:47:16 status half-installed libfftw3-3 3.1.2-3.1ubuntu1
2008-12-19 13:47:17 status half-installed libofa0 0.9.3-3
2008-12-19 13:47:18 status half-installed libopenspc0 0.3.99a-2
2008-12-19 13:47:18 status half-installed libsoundtouch1c2 1.3.1-2
2008-12-19 13:47:19 status half-installed libwildmidi0 0.2.2-2
2008-12-19 13:47:20 status half-installed gstreamer0.10-plugins-bad 0.10.8-1
2008-12-19 13:47:25 status installed freepats 20060219-1
2008-12-19 13:47:25 status installed libcdaudio1 0.99.12p2-5
2008-12-19 13:47:25 status installed libdc1394-22 2.0.2-1
2008-12-19 13:47:26 status installed libgmyth0 1:0.7.1-1
2008-12-19 13:47:26 status installed libiptcdata0 1.0.2+libtool01-2
2008-12-19 13:47:26 status installed libmms0 0.4-2
2008-12-19 13:47:26 status installed libneon27-gnutls 0.28.2-2build1
2008-12-19 13:47:26 status installed libfftw3-3 3.1.2-3.1ubuntu1
2008-12-19 13:47:26 status installed libofa0 0.9.3-3
2008-12-19 13:47:27 status installed libopenspc0 0.3.99a-2
2008-12-19 13:47:27 status installed libsoundtouch1c2 1.3.1-2
2008-12-19 13:47:27 status installed libwildmidi0 0.2.2-2
2008-12-19 13:47:27 status installed gstreamer0.10-plugins-bad 0.10.8-1
2008-12-19 13:47:27 status installed libc6 2.8~20080505-0ubuntu7
2008-12-19 16:55:14 status half-installed gstreamer0.10-ffmpeg 0.10.5-1
2008-12-19 16:55:14 status half-installed libsidplay1 1.36.59-5
2008-12-19 16:55:15 status half-installed gstreamer0.10-plugins-ugly 0.10.9-1ubuntu0.1
2008-12-19 16:55:19 status installed gstreamer0.10-ffmpeg 0.10.5-1
2008-12-19 16:55:19 status installed libsidplay1 1.36.59-5
2008-12-19 16:55:19 status installed gstreamer0.10-plugins-ugly 0.10.9-1ubuntu0.1
2008-12-19 16:55:19 status installed libc6 2.8~20080505-0ubuntu7
2008-12-19 21:23:39 status half-installed libglib2.0-dev 2.18.2-0ubuntu2
2008-12-19 21:23:41 status half-installed libglib2.0-dev 2.18.2-0ubuntu2
2008-12-19 21:23:41 status half-installed libmono-dev 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:43 status half-installed libmono-peapi2.0-cil 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:43 status half-installed mono-2.0-devel 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:43 status half-installed mono-2.0-devel 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:44 status half-installed mono-gmcs 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:44 status half-installed mono-gmcs 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:50 status installed man-db 2.5.2-2
2008-12-19 21:23:55 status installed libglib2.0-dev 2.18.2-0ubuntu2
2008-12-19 21:23:55 status installed libmono-dev 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:55 status installed libmono-peapi2.0-cil 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:55 status installed mono-2.0-devel 1.9.1+dfsg-4ubuntu2
2008-12-19 21:23:55 status installed mono-gmcs 1.9.1+dfsg-4ubuntu2
remix@mini:~$ 
```

I just installed ubuntu a week or so ago.  So there have been tons of updates.  Then a friend of mine helped install the Ubuntu Netbook Remix (I have an HP mini 1000).

---

### Post by unutbu on 2008-12-22
This seems like an excellent thing to try:
> **albinootje said:**
> 
And can you boot with an older kernel version in the grub menu at boot time ?
You might have to press <escape> before you see the full grub menu,
and then choose one of the other options (other than the default), but not the recovery mode ones.

Can you say with certainty that ethernet was working on Thursday 2008-12-18? Knowing the last day ethernet was working will help us round up the likely suspects.

---

### Post by SwooshOU on 2008-12-22
I hit esc at startup and loaded a kernel with the last three numbers of 27-9.  The eth0 showed up under wired network!  However, I plugged the network cable in, turned off wifi and waited.  Unless there is something I have to do to activate it, it wasn't automatically recognized.  While wired networks shows up in the connection information, it's just greyed out.  So, I wasn't able to connect to the internet.

I've been able to get online using the ethernet port only once in the week that I've had this.  That was on Friday.

---

### Post by unutbu on 2008-12-22
Okay, how about post
```

ifconfig
sudo ifdown eth1
sudo ifup eth0
sudo /etc/init.d/networking restart
ifconfig
route -n

```

PS: Linux kernel 2.6.27-9 is the latest Ubuntu kernel. It should have been made the default when you installed it. I wonder what you were booting before...

---

### Post by albinootje on 2008-12-22
> **SwooshOU said:**
> I hit esc at startup and loaded a kernel with the last three numbers of 27-9.  The eth0 showed up under wired network!  However, I plugged the network cable in, turned off wifi and waited.  Unless there is something I have to do to activate it, it wasn't automatically recognized.  While wired networks shows up in the connection information, it's just greyed out.  So, I wasn't able to connect to the internet.

I've been able to get online using the ethernet port only once in the week that I've had this.  That was on Friday.

So, you're saying that eth0 turned up after booting an older kernel ?
Can you try :
```

sudo dhclient eth0

```

---

### Post by SwooshOU on 2008-12-22
> **unutbu said:**
> Okay, how about post
```

ifconfig
sudo ifdown eth1
sudo ifup eth0
sudo /etc/init.d/networking restart
ifconfig
route -n

```

PS: Linux kernel 2.6.27-9 is the latest Ubuntu kernel. It should have been made the default when you installed it. I wonder what you were booting before...

I dunno...

```
remix@mini:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:64:69:f1:a0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

remix@mini:~$ sudo ifdown eth1
[sudo] password for remix: 
ifdown: interface eth1 not configured
remix@mini:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
remix@mini:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                  [ OK ] 
remix@mini:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:64:69:f1:a0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

remix@mini:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

---

### Post by SwooshOU on 2008-12-22
> **albinootje said:**
> So, you're saying that eth0 turned up after booting an older kernel ?
Can you try :
```

sudo dhclient eth0

```

```
remix@mini:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:22:64:69:f1:a0
Sending on   LPF/eth0/00:22:64:69:f1:a0
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by unutbu on 2008-12-22
What is the IP address of the gateway at work?
For example, if it is 192.0.0.192, then edit your /etc/hosts file:
```

gksu gedit /etc/hosts
```
Add this line:
```

192.0.0.192  workgateway

``` (Change 192.0.0.192 to the actual IP address).
Save and exit.

Now try
```

sudo /sbin/route add -host workgateway eth0
sudo dhclient eth0
```

---

### Post by SwooshOU on 2008-12-22
OK, I restarted with the network cord plugged in and logged into the other user (luke) that I have setup.  It's the one that doesn't have the Ubuntu Netbook Remix "skin" on it.  Just a regular desktop.  The network is up and running on the internet with that setting.  So, now I'm really confused.

Are there any commands I can run that may indicate why this user (luke) may work and the remix won't?

---

### Post by unutbu on 2008-12-22
SwooshOU, unfortunately I'm out of ideas. 

If the problem has to do with configuration of Netbook Remix, then I'm clueless about what to do. I have zero experience there and don't know how it is set up. From what I gather from searching on the web, Netbook Remix adds some apps but uses the same Ubuntu kernel. None of the apps seem to specifically address networking, so I'm without any guess why Netbook should make a difference.

Tying up my other loose end, I've looked at the list of packages that were installed on 2008-12-19. If any of them are the culprit, my guess would be avahi-autoipd or one of the other avahi packages. However, even if it was one of these packages, it would not explain why the luke account works. Furthermore, I was hoping it was a linux-kernel package that was at the base of the problem. I know you can remove such a package and use an older kernel without serious consequence, but I don't know enough about avahi to feel confident recommending any fiddling there.

---

### Post by unutbu on 2008-12-23
SwooshOU, have you found a way to get wired networking while using Netbook? I was just reading this thread

[http://ubuntuforums.org/showpost.php?p=6423235&postcount=12](http://ubuntuforums.org/showpost.php?p=6423235&postcount=12)

and wonder if adding "auto eth0" to your /etc/network/interfaces
might make Network Manager activate the eth0 interface instead of leaving it greyed.

---

### Post by SwooshOU on 2008-12-23
I come into work today and plug in the ethernet under "luke" which has worked before and it works today.  I decided to shut down and then login to "remix" and lo and behold the ethernet works there too.  And THAT is where I've had most of the problems.

So, I have no clue as to what it is that is causing the sporadic-ness of the connection.  I'm just thankful that the wifi has been solid.

---

### Post by SwooshOU on 2008-12-23
> **unutbu said:**
> SwooshOU, have you found a way to get wired networking while using Netbook? I was just reading this thread

[http://ubuntuforums.org/showpost.php?p=6423235&postcount=12](http://ubuntuforums.org/showpost.php?p=6423235&postcount=12)

and wonder if adding "auto eth0" to your /etc/network/interfaces
might make Network Manager activate the eth0 interface instead of leaving it greyed.

See, when everything is working (like it is now) I'm afraid to change anything.  However, I will remember this if it stops working again.

---

### Post by unutbu on 2008-12-23
No problem; I don't like changing a working system either :)
Hope everything stays working.
Happy Holidays,
unutbu

---

### Post by mshipman on 2008-12-23
If the kernel has been updated since the port was working, you may want to try booting a previous kernel from the GRUB menu.

---

### Post by jswinner on 2009-01-03
I have the same problem, but cannot get the port to show at all

---

### Post by Space-Age on 2009-02-10
I'm in the same situation here...the wireless (eth1) works fine, but the wired ethernet port (what should be eth0) isn't there.  It doesn't show in the network configuration or lshw -C network...Anybody else have any progress on this?

---

### Post by theDaveTheRave on 2009-02-14
Hi all

this is really strange... I'm troublshooting a sudden death of my wifi in this thread [here]("http://ubuntuforums.org/showthread.php?p=6736169&posted=1#post6736169").

What is strange is that I remember everything working just fine before I headed back to the UK for chritmas, so I can say fairly happily pre December 20th.

This seems to tie in far too nicely with the update that SwooshOU recieved!

I may try unutbu's idead of manually adding the lines

auto wmaster0

to my /etc/network/interfaces file.

SwooshOU, could you post the contents of your file for both the logon names (ie under both remix and luke), the easy way to do this is the following code

```

more /etc/network/interfaces

```

then there is no danger of if going "wrong", it would be interesting to see if they do contain the line that unutbu's is suggesting.

here is mine...

```

davem@Dartagnon:~$ more /etc/network/interfaces
auto lo
iface lo inet loopback



iface eth0 inet dhcp

auto eth0

```

I'll add in the exta line tomorrow morning, after I boot up (if the overnight reboot doesn't change it!?)

speak to you all in the am...

David

---

### Post by Space-Age on 2009-02-15
So...Not sure if the latest updates took care of this, but after running them this moring, my previously non-existant eth0 interface now happily exists.   Is this the case for others w/ the same issue?

---

