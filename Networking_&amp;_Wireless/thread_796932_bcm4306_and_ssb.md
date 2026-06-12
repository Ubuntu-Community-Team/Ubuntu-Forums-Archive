---
title: "bcm4306 and ssb"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by backdoc on 2008-05-16
I have seen quite a few posts like mine.  But, none of them have a solution that works for me.  I didn't want to start a new thread, but it looks like it was time.

First off, I'm not a newbie.  And, I'm no stranger to setting up my wifi on Ubuntu (maybe not an expert, but pretty handy none-the-less).  Anyway, I had my bcm4306 wifi card working fine on Gutsy.  Then, I upgraded.  Since then, I have not been able to get it working again.  

I have tried rmmod'ing the modules, b44, b43, ssb, ohci_hcd and reloading the ndiswrapper before the ssb module.  I have scripted it and put it in init.d, as other threads have suggested.

I have uninstalled ndiswrapper from the repositories and installed an older version from source.  I have removed the bcmwl5 driver and reinstalled it.  Interestingly, when I do ndiswrapper -l, the driver says it's installed and something about an alternate driver: ssb.  But, when I was on Gutsy, it only stated that the driver was installed.  Now, it says:
[INDENT]bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
[/INDENT]

Something else that I find interesting is the output of lshw -C network.  If I install just the ndiswrapper module, it does not have a configuration entry for the wifi card, but if I install the b44 module, it shows
[INDENT]configuration: driver=b43-pci-bridge latency=32 module=ssb[/INDENT]

If I grep my modules to see which ones are present, it now shows the ssb module (b44 requires it).  And, it seems to take over my network configuration for my wifi card.  Here's the results of my grep:
[INDENT]lsmod |grep -i -e ssb -e b44 -e b43 -e ndis
b44                    28432  0 
ssb                    32260  1 b44
ndiswrapper           193564  0 
usbcore               146028  4 ehci_hcd,uhci_hcd,ndiswrapper
mii                     6400  1 b44
[/INDENT]
Something else odd about running lshw -C network is that the first network device (the hard wired one) has a logical name, which is eth0.  The second device (the wifi card) does not have logical name.  Here's the full output of lshw -C network:

[INDENT]lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:9a:46:96
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5705-v3.11 ip=192.168.1.11 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
[/INDENT]

To test if my wifi card is being picked up, I use iwconfig and look for my eth1 device.  It used to show up when I installed the ndiswrapper module.  Now, it never shows up.

At this point, I'm confused as to what the b44 and ssb modules are used for.  And, why is the card stuck on ssb?  And, why does ndiswrapper now have a reference to ssb?

Any suggestions?

---

### Post by backdoc on 2008-05-16
A hugely interestingly bit of information.  I was looking over the following thread and thought, it sounded a lot like my problem.  Turns out, if I reboot to an old kernel, I can get it working.  So, the issue is with the kernel.  I still don't quite get what it is about the new kernel.  I did see something about ndiswrapper mentioned in a thread on kernel.org where Linus said he didn't care about ndiswrapper.  But, technically, what's the problem?  I would prefer to stay with the new kernel so that I don't have to recompile my nvidia drivers.  But, at least I'm on to something now.

[http://ubuntuforums.org/showthread.php?t=793488]("http://ubuntuforums.org/showthread.php?t=793488")

---

### Post by Ayuthia on 2008-05-16
Just to get things started, you don't need b44.  If you look at your wired card from your lshw -C network, it us using tg3 instead of b44.  Because of this, you should not even need the ssb driver if you are using NDISwrapper.  If you are not sure about this, remove b44 and ssb and see if you can still use your wired connection.  The only people that need to put the extra code are the people with the BCM44* ethernet cards.

Which script did you use to reload the ssb module?  Most likely, that needs to be removed.  It is not needed.  ssb should just be blacklisted in /etc/modprobe.d/blacklist.  I say this because if you look at your lsmod results, you will see that ssb is only tied to b44.  If you really want to, you could blacklist b43, b44, bcm43xx, and ssb.

---

### Post by backdoc on 2008-05-16
Thanks for your help.

> **Ayuthia said:**
> Just to get things started, you don't need b44.  If you look at your wired card from your lshw -C network, it us using tg3 instead of b44.  Because of this, you should not even need the ssb driver if you are using NDISwrapper.  If you are not sure about this, remove b44 and ssb and see if you can still use your wired connection.  


I removed them and have no problem with my wired card.

> **Ayuthia said:**
> The only people that need to put the extra code are the people with the BCM44* ethernet cards.

Which script did you use to reload the ssb module?  Most likely, that needs to be removed.  It is not needed.  ssb should just be blacklisted in /etc/modprobe.d/blacklist.  I say this because if you look at your lsmod results, you will see that ssb is only tied to b44.  If you really want to, you could blacklist b43, b44, bcm43xx, and ssb.

The only script I'm using is the one I created in /etc/init.d/ndiswrapper.  There could be another script running somewhere but, not something that I am aware of.  The script is just a series of rmmod's and modprobes.  I wasn't sure what b44 and ssb might be used for.  So, I just followed the other thread's advice.  The script looks like:

[INDENT]cat /etc/init.d/ndiswrapper 
#! /bin/sh
### BEGIN INIT INFO
# Provides: ndiswrapper
# Required-Start:
# Required-Stop:
# Default-Start: S
# Default-Stop:
# Short-Description: enable to load ndiswrapper
# Description: enable to load ndiswrapper
### END INIT INFO
rmmod ohci_hcd
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe ohci_hcd
[/INDENT]

I'm already blacklisting many modules:
[INDENT]# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist b44
blacklist ssb
[/INDENT]

If ssb and b44 are not required, I can remove them from the init script.

---

### Post by Ayuthia on 2008-05-16
I don't really think that you need the script.  You just need to have ndiswrapper in /etc/modules.  That script was used mainly to load any modules that uses ssb.

I have not seen ohci_hcd use ssb since about March.  I think it was used once, but then removed prior to the final release of Hardy.  The person who created that script probably caught wind of it being with that module because of the bug lists and posts talked about it.  Most of the ones I have seen are dated back in March have not been mentioned since.

Does ndiswrapper load now?

---

### Post by backdoc on 2008-05-16
> **Ayuthia said:**
> I don't really think that you need the script.  You just need to have ndiswrapper in /etc/modules.  That script was used mainly to load any modules that uses ssb.

I have not seen ohci_hcd use ssb since about March.  I think it was used once, but then removed prior to the final release of Hardy.  The person who created that script probably caught wind of it being with that module because of the bug lists and posts talked about it.  Most of the ones I have seen are dated back in March have not been mentioned since.

Does ndiswrapper load now?
I do have ndiswrapper in /etc/modules.  I removed the call/reference to the init.d script in rc2.d.  It should not run automatically anymore.  I left the script in for historical reference.

I can load the ndiswrapper module now.  But, still no sight of eth1 (my wireless card).
[INDENT]cat /etc/modules 
[INDENT]# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ndiswrapper[/INDENT]


root@laptop:/home/backdoc# iwconfig
[INDENT]lo        no wireless extensions.
eth0      no wireless extensions.
[/INDENT]
[/INDENT]

Here's my current details:

[INDENT]lsmod |grep -i -e ssb -e b44 -e b43 -e ndis
[INDENT]ndiswrapper           193564  0 
usbcore               146028  5 ndiswrapper,ohci_hcd,ehci_hcd,uhci_hcd
[/INDENT]
root@laptop:/home/backdoc# lshw -C network
[INDENT]  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:9a:46:96
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5705-v3.11 ip=192.168.1.11 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32[/INDENT][/INDENT]

As I stated in one of my previous posts, there's something going on with this kernel version.  I can do the same things I'm doing now and get wireless to work, **if I boot to the kernel prior to the one I'm using now**.

---

### Post by Ayuthia on 2008-05-17
> **backdoc said:**
> I do have ndiswrapper in /etc/modules.  I removed the call/reference to the init.d script in rc2.d.  It should not run automatically anymore.  I left the script in for historical reference.

I can load the ndiswrapper module now.  But, still no sight of eth1 (my wireless card).
[INDENT]cat /etc/modules 
[INDENT]# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ndiswrapper[/INDENT]


root@laptop:/home/backdoc# iwconfig
[INDENT]lo        no wireless extensions.
eth0      no wireless extensions.
[/INDENT]
[/INDENT]

Here's my current details:

[INDENT]lsmod |grep -i -e ssb -e b44 -e b43 -e ndis
[INDENT]ndiswrapper           193564  0 
usbcore               146028  5 ndiswrapper,ohci_hcd,ehci_hcd,uhci_hcd
[/INDENT]
root@laptop:/home/backdoc# lshw -C network
[INDENT]  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:9a:46:96
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5705-v3.11 ip=192.168.1.11 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32[/INDENT][/INDENT]

As I stated in one of my previous posts, there's something going on with this kernel version.  I can do the same things I'm doing now and get wireless to work, **if I boot to the kernel prior to the one I'm using now**.

What version of ndiswrapper are you using?  2.6.24 usually needs versions 1.50 or higher.  I want to say that I had problems with 1.50 and 1.51, but I could be wrong.  It has been a few months since I have used it.

I am sure that there are some changes that had to be made in ndiswrapper so that it will work for 2.6.24.  So just that combination can create odd things to happen.

---

### Post by backdoc on 2008-05-17
> **Ayuthia said:**
> What version of ndiswrapper are you using?  2.6.24 usually needs versions 1.50 or higher.  I want to say that I had problems with 1.50 and 1.51, but I could be wrong.  It has been a few months since I have used it.

I am sure that there are some changes that had to be made in ndiswrapper so that it will work for 2.6.24.  So just that combination can create odd things to happen.

I was using the verion in the repository, which is I guess 1.5.  But, since I was having trouble, I downloaded 1.52 and compiled it.  That raises a couple of questions though.  Could I have the wrong kernel-headers?  The reason that I ask is because, if I'm not mistaken, ndiswrapper will only work with the kernel it's compiled against, right?  If so, and I can reboot to my previous kernel and load my wifi, maybe when I compiled ndiswrapper it found old headers and therefore generated the wrong version, do you think that's possible?  According to the output below, it doesn't look like this is the case, but ....

ndiswrapper -v
[INDENT]
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586[/INDENT]

uname -r
[INDENT]2.6.24-16-generic[/INDENT]

---

### Post by Ayuthia on 2008-05-17
> **backdoc said:**
> I was using the verion in the repository, which is I guess 1.5.  But, since I was having trouble, I downloaded 1.52 and compiled it.  That raises a couple of questions though.  Could I have the wrong kernel-headers?  The reason that I ask is because, if I'm not mistaken, ndiswrapper will only work with the kernel it's compiled against, right?  If so, and I can reboot to my previous kernel and load my wifi, maybe when I compiled ndiswrapper it found old headers and therefore generated the wrong version, do you think that's possible?  According to the output below, it doesn't look like this is the case, but ....

ndiswrapper -v
[INDENT]
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586[/INDENT]

uname -r
[INDENT]2.6.24-16-generic[/INDENT]

It looks like it found the right header files because the .ko file was moved to the correct place.  What does dmesg say when you do a sudo modprobe ndiswrapper?

---

### Post by backdoc on 2008-05-17
Here you go:

dmesg
[INDENT][25712.967320] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[25713.010137] ndiswrapper: driver bcmwl5 (Broadcom,06/13/2003, 3.20.23.0) loaded
[25713.010922] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[25713.022087] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: e0d0cb02
[25713.022096] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x104
[25713.022187] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[25713.022197] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[25713.022216] ndiswrapper (mp_halt:259): device dec29480 is not initialized - not halting
[25713.026009] ndiswrapper: device eth%d removed
[25713.026039] ACPI: PCI interrupt for device 0000:02:03.0 disabled
[25713.026065] ndiswrapper: probe of 0000:02:03.0 failed with error -22
[25713.026126] usbcore: registered new interface driver ndiswrapper
[/INDENT]

---

### Post by Ayuthia on 2008-05-17
> **backdoc said:**
> Here you go:
[25713.022197] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)

As odd as this sounds, it seems like it does not like the driver.  You might try to see if you can find another driver.  I am thinking that something might have changed in NDISwrapper.

---

### Post by backdoc on 2008-05-17
> **Ayuthia said:**
> As odd as this sounds, it seems like it does not like the driver.  You might try to see if you can find another driver.  I am thinking that something might have changed in NDISwrapper.

I don't know about that.  It works if I reboot to my previous kernel.  That strikes me as weird because the ndiswrapper module was compiled against the kernel headers I've posted.  But, I'm not knowledgeable enough about that to really have an opinion.

I'm starting to think the kernel is fubar.  But, I'm willing to try another driver.  What driver would you suggest trying?

If another driver doesn't do the trick, maybe I can escalate this with the Ubuntu devs.

---

### Post by Ayuthia on 2008-05-17
Well, I am not for sure about which driver you are currently using.  It usually is better to grab the XP driver that is for your computer.  Another place to check out is this [one]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").

The other option is to try and go back to the Ubuntu repository version.  That would not be compiled under your kernel.

---

### Post by backdoc on 2008-05-18
> **Ayuthia said:**
> Well, I am not for sure about which driver you are currently using.  It usually is better to grab the XP driver that is for your computer.  Another place to check out is this [one]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").

The other option is to try and go back to the Ubuntu repository version.  That would not be compiled under your kernel.

I am using the XP driver.  It's the same one I've always used with ndiswrapper.

I will take a look at the url you posted.  But, I think I have the right driver.  

Thanks for all of your help and suggestions.

---

### Post by dmizer on 2008-05-18
i've seen this work in a number of situations where the b44 module is required for the wired network adapter.  since the ssb module is a part of the usb (as is ndiswrapper) tree, it interferes with ndiswrapper.

adding:
```
modprobe -r ndiswrapper
modprobe -r b44
modprobe ndiswrapper
modprobe b44
```
to /etc/rc.local fixes the load order so both the wired and wireless cards can work.

troubleshooting source: [http://ubuntuforums.org/showthread.php?t=740632](http://ubuntuforums.org/showthread.php?t=740632)

---

### Post by backdoc on 2008-05-18
Thanks for helping.

> **dmizer said:**
> 
```
modprobe -r ndiswrapper
modprobe -r b44
modprobe ndiswrapper
modprobe b44
```

I tried adding that to rc.local and it did not help.

I don't understand what you are trying to say here:
> since the ssb module is a part of the usb (as is ndiswrapper) tree, it interferes with ndiswrapper

Could you elaborate on that?  

Can we break this down into baby steps and prove each step either works or does not work as we go?

---

### Post by backdoc on 2008-05-18
> **dmizer said:**
> i've seen this work in a number of situations where the b44 module is required for the wired network adapter.  since the ssb module is a part of the usb (as is ndiswrapper) tree, it interferes with ndiswrapper.

adding:
```
modprobe -r ndiswrapper
modprobe -r b44
modprobe ndiswrapper
modprobe b44
```
to /etc/rc.local fixes the load order so both the wired and wireless cards can work.

troubleshooting source: [http://ubuntuforums.org/showthread.php?t=740632](http://ubuntuforums.org/showthread.php?t=740632)

Apparently, I do not even need b44.  I just did an lshw -C network.  And, I could see the ssb module was bound to my wifi card.  Then, I rmmod'd my ndiswrapper and reran lshw.  It gave the same results.  So, I rmmod'd b44 and reran lshw again.  It was the same thing.  After removing the b44 module, I pinged yahoo.com and proved my network was still up.  I rmmod'd ssb and reran lshw again.  This time, it did not show my wifi card was bound to the ssb module.  So, I added the ndiswrapper module back to see if it would it would bind to the wifi card, it would not.  This is where my problem is.  Something is stopping ndiswrapper from gaining access to the card.  Here's the lshw -C network results before and after:

Before removing ssb (not showing eth0):
[INDENT]  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
[/INDENT]

After removing ssb (not showing eth0):
[INDENT]  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32
[/INDENT]

After adding ndiswrapper back in, it looks the same.

---

### Post by dmizer on 2008-05-18
okay ... if b44 is not needed for your wired nic, include these modules in your blacklist:
b43-pci-bridge
b44
b43
ssb

reload ndiswrapper and see if that gets your card working.

---

### Post by backdoc on 2008-05-18
> **dmizer said:**
> okay ... if b44 is not needed for your wired nic, include these modules in your blacklist:
b43-pci-bridge
b44
b43
ssb

reload ndiswrapper and see if that gets your card working.

I already had everything except for the b43-pci-bridge blacklisted.  So, I added it and rebooted.  Now my blacklist looks like:
[INDENT]blacklist bcm43xx
blacklist b43
blacklist b43-pci-bridge
blacklist b43legacy
blacklist b44
blacklist ssb
[/INDENT]

Upon reboot, I did an lsmod |grep -i ndis.  ndiswrapper was already loaded.  I checked iwconfig, and my eth1 wifi card wasn't listed.  So, I did an lshw -C network and could see my wifi card was bound to ssb.  So, I grep'ed my modules and discovered ssb was already loaded.  Nothing is shown to be using it and it's no using any other modules.
[INDENT]
lsmod |grep ssb
[INDENT]ssb                    32260  0 
[/INDENT]
[/INDENT]
I wondered if ndiswrapper loaded it.  So, I did the following:

[INDENT]root@laptop:/home/backdoc# rmmod ndiswrapper
root@laptop:/home/backdoc# rmmod ssb
root@laptop:/home/backdoc# modprobe ndiswrapper
root@laptop:/home/backdoc# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
[/INDENT]

I grep'd for ssb in my modules and it was NOT loaded.  So, something else is loading it, even though it was blacklisted.  Now, lshw -C network shows nothing bound to my wifi card.

Something I find odd is the result of ndiswrapper -l.  It shows:

[INDENT]bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
[/INDENT]

Before I upgraded, it never used to mention the "alternate driver: ssb" part.  I've tried removing and adding it back several times.  It always says this.

---

### Post by dmizer on 2008-05-18
please post the entire contents of your lsmod.

---

### Post by backdoc on 2008-05-18
OK.  Here's lsmod.  It doesn't have ssb in it because I removed prior to my last post:

Module                  Size  Used by
ndiswrapper           193564  0 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
ipv6                  267780  18 
speedstep_centrino      9152  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
af_packet              23812  2 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
sbp2                   24072  0 
lp                     12324  0 
joydev                 13120  0 
pcmcia                 40876  0 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
dcdbas                  9504  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
evdev                  13056  6 
snd_seq_dummy           4868  0 
video                  19856  0 
output                  4736  1 video
snd_seq_oss            35584  0 
serio_raw               7940  0 
snd_seq_midi            9376  0 
nvidia               4718832  22 
snd_rawmidi            25760  1 snd_seq_midi
psmouse                40336  0 
yenta_socket           27276  2 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
i2c_core               24832  1 nvidia
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
battery                14212  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                      6916  0 
pcspkr                  4224  0 
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25492  1 
agpgart                34760  2 nvidia,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
ext3                  136712  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  6 
ata_piix               19588  5 
ata_generic             8324  0 
pata_acpi               8320  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
ohci1394               33584  0 
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
uhci_hcd               27024  0 
tg3                   116228  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3

---

### Post by zhuqing123 on 2008-05-18
The fourth [wow power leveling](http://www.wow-powerleveling.org) latest game in [wow power leveling](http://www.xowow.com) Warcraft series is ‘[wow power leveling](http://www.powerlevelingweb.com)’. Also known as [wow power leveling](http://www.igsstar.com), it represents a [wow power leveling](http://www.wowgoldweb.com) multiplayer online [wow power leveling](http://www.powerleveling-wow.com/siteMap.asp) game, the best of [wow power leveling](http://www.powerleveling-wow.com) kind. Initially, it was [wow gold](http://www.wow-powerleveling.org) it be released in 2001, but [wow powerleveling](http://www.powerleveling-wow.com) was delayed [wow powerleveling](http://www.powerlevelingweb.com) 2004, thus [wow powerleveling](http://www.xowow.com) the 10 years of[wow powerleveling](http://www.wow-powerleveling.org) franchise of this[wow gold](http://www.xowow.com) series. The [world of warcraft power leveling](http://www.powerlevelingweb.com) was not [world of warcraft power leveling](http://www.wow-powerleveling.org/wow+power+leveling.html)fulfilling, because [wow power level](http://www.powerleveling-wow.com/siteMap.asp)problems with [wow power level](http://www.powerlevelingweb.com) server’s stability [power leveling wow](http://www.powerleveling-wow.com/siteMap.asp) performance occurred, but [power leveling wow](http://www.xowow.com) game still [power leveling wow](http://www.powerlevelingweb.com) a financial success [powerleveling wow](http://www.powerleveling-wow.com/siteMap.asp) the most [powerleveling wow](http://www.xowow.com) game of its kind. The number [cheap wow power leveling ](http://www.powerlevelingweb.com) users that play [Maple Story mesos](http://www.igsstar.com/Maple-Story-mesos-us/), exceeds 8.5 [MapleStory mesos](http://www.igsstar.com/Maple-Story-mesos-us/), worldwide.As a form [ms mesos](http://www.igsstar.com/Maple-Story-mesos-us/),recognition for [mesos](http://www.igsstar.com/Maple-Story-mesos-us/),outstanding popularity, the game [SilkRoad Gold](http://www.igsstar.com/Silkroad-Online-Gold/), received a[SRO Gold](http://www.igsstar.com/Silkroad-Online-Gold/), of awards. Now the question [eq2 plat](http://www.igsstar.com/EverQuest-2-gold-plat/), why is [eq2 gold](http://www.igsstar.com/EverQuest-2-gold-plat/), game [eq2 Platinum](http://www.igsstar.com/EverQuest-2-gold-plat/), popular? For anyone[EverQuest 2 Platinum](http://www.igsstar.com/EverQuest-2-gold-plat/), played the previous [EverQuest 2 gold](http://www.igsstar.com/EverQuest-2-gold-plat/), and [EverQuest 2 plat](http://www.igsstar.com/EverQuest-2-gold-plat/), already initiated [lotro gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), the mysterious world [lotr gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), the breathtaking [Lord of the Rings online Gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), this [Rolex Replica](http://www.watchreplicashop.com/) nothing but an [Replica Rolex](http://www.watchreplicashop.com/) adventure that continues the story of ‘Warcraft III: Frozen Throne’, four years after conclusion, in the world of Azeroth. The game is online role-playing, the previous versions being online and offline strategy games. The major thrills and unique features are present as in every Blizzard game.

---

### Post by Ayuthia on 2008-05-18
> **backdoc said:**
> 
Something I find odd is the result of ndiswrapper -l.  It shows:

[INDENT]bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
[/INDENT]

Before I upgraded, it never used to mention the "alternate driver: ssb" part.  I've tried removing and adding it back several times.  It always says this.
The older versions used to show (alternate driver: bc43xx) for some people.  I used to have it.  I now have (alternate driver: ssb).  Right now I am currently using ndiswrapper because I wanted to test out ssb.

If you really want to test out ssb, don't blacklist it.  Don't bother with anything else.  You have to make sure that you don't have any Hardy fixes for b44 and ssb, because if you do, it will show up.  Reboot your machine and see if it comes up.  Make sure that b43 and b44 do not show up.  If they do show up, then ssb will be there.

I have tried it out on mine and ssb does not show up.  

By any chance, did you load the firmware for the b43/b43legacy drivers?  I am pretty sure that yours is a b43legacy which I have only helped one person get that installed (did not use ndiswrapper).  If you did, we could try and move out the firmware for it and see if it makes a difference.

---

### Post by dmizer on 2008-05-18
humm
with ssb unloaded and ndiswrapper loaded what's the output of:
```
lshw -C network
```

perhaps it would be better to post your lsmod with ssb loaded.

i would double check your blacklist to make sure you have ssb

---

### Post by backdoc on 2008-05-18
> **Ayuthia said:**
> Right now I am currently using ndiswrapper because I wanted to test out ssb.

I don't understand the connection.  Why does using ndiswrapper have anything to do with ssb?

> **Ayuthia said:**
> 
If you really want to test out ssb, don't blacklist it.  

Oh.  I'm not trying to test ssb.  I don't know what it is.  I'm trying to get around it.

> **Ayuthia said:**
> You have to make sure that you don't have any Hardy fixes for b44 and ssb, because if you do, it will show up.  

How do I make sure I don't have any Hardy fixes for b44 and ssb?

> **Ayuthia said:**
> 
Reboot your machine and see if it comes up.  Make sure that b43 and b44 do not show up.  If they do show up, then ssb will be there.


By "it", I assume you mean ssb.  I'll reboot again and see if b43, b44 or ssb are there on boot.  I'll post back and let you know.

> **Ayuthia said:**
> By any chance, did you load the firmware for the b43/b43legacy drivers?  I am pretty sure that yours is a b43legacy which I have only helped one person get that installed (did not use ndiswrapper).  If you did, we could try and move out the firmware for it and see if it makes a difference.

Hmmmm.  We could take a look at this.  I haven't knowingly done this.  But, it is certainly possible possible.

---

### Post by backdoc on 2008-05-18
> **Ayuthia said:**
> The older versions used to show (alternate driver: bc43xx) for some people.  I used to have it.  I now have (alternate driver: ssb).  Right now I am currently using ndiswrapper because I wanted to test out ssb.

If you really want to test out ssb, don't blacklist it.  Don't bother with anything else.  You have to make sure that you don't have any Hardy fixes for b44 and ssb, because if you do, it will show up.  Reboot your machine and see if it comes up.  Make sure that b43 and b44 do not show up.  If they do show up, then ssb will be there.

I have tried it out on mine and ssb does not show up.  

By any chance, did you load the firmware for the b43/b43legacy drivers?  I am pretty sure that yours is a b43legacy which I have only helped one person get that installed (did not use ndiswrapper).  If you did, we could try and move out the firmware for it and see if it makes a difference.

On a fresh reboot, here we go:

lsmod |grep -e ndis -e ssb -e b44 -e b43
ndiswrapper           193564  0 
ssb                    32260  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd

Per dmizer's request, I'm going to post my entire lsmod again.  See my upcoming post.

---

### Post by backdoc on 2008-05-18
> **dmizer said:**
> humm
with ssb unloaded and ndiswrapper loaded what's the output of:
```
lshw -C network
```

perhaps it would be better to post your lsmod with ssb loaded.

i would double check your blacklist to make sure you have ssb

Since ssb was loaded on reboot, I'll post the entire lsmod in the state it's in before I do anything.  Then, I'll unload ssb and ndiswrapper and post the entire lshw -C network output.  Both below . . .

```
lsmod
```
[INDENT]
Module                  Size  Used by
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
ipv6                  267780  17 
speedstep_centrino      9152  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
af_packet              23812  2 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
ndiswrapper           193564  0 
sbp2                   24072  0 
lp                     12324  0 
joydev                 13120  0 
pcmcia                 40876  0 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
dcdbas                  9504  0 
evdev                  13056  6 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_seq_dummy           4868  0 
serio_raw               7940  0 
video                  19856  0 
output                  4736  1 video
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
nvidia               4718832  22 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
yenta_socket           27276  2 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_core               24832  1 nvidia
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                40336  0 
button                  9232  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
battery                14212  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                      6916  0 
pcspkr                  4224  0 
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25492  1 
agpgart                34760  2 nvidia,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
ext3                  136712  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  6 
ata_piix               19588  5 
ata_generic             8324  0 
ohci1394               33584  0 
pata_acpi               8320  0 
ieee1394               93752  2 sbp2,ohci1394
ssb                    32260  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
ehci_hcd               37900  0 
tg3                   116228  0 
uhci_hcd               27024  0 
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
[/INDENT]

```
root@laptop:/home/backdoc# rmmod ssb
root@laptop:/home/backdoc# rmmod ndiswrapper
root@laptop:/home/backdoc# lshw -C network
```
[INDENT]
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:9a:46:96
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5705-v3.11 ip=192.168.1.11 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32
[/INDENT]

---

### Post by Ayuthia on 2008-05-18
> **backdoc said:**
> On a fresh reboot, here we go:

lsmod |grep -e ndis -e ssb -e b44 -e b43
ndiswrapper           193564  0 
ssb                    32260  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd

Per dmizer's request, I'm going to post my entire lsmod again.  See my upcoming post.
Do you have ssb in your init.d script? 

I do have a new question--if you remove both ndiswrapper and b43, does ifconfig still show eth1?  If so, what happens when you do:
```
sudo ifconfig eth1 down
sudo modprobe ndiswrapper
```

I am going to go back and answer your other questions in the other post.

---

### Post by Ayuthia on 2008-05-18
> **backdoc said:**
> I don't understand the connection.  Why does using ndiswrapper have anything to do with ssb?
ssb has to be loaded after ndiswrapper or else ndiswrapper does not work.

> How do I make sure I don't have any Hardy fixes for b44 and ssb?The only Hardy fixes are the ones that you would have done on your own.  Right now, the only one that was mentioned in this post was your init.d script.  

> By "it", I assume you mean ssb.  I'll reboot again and see if b43, b44 or ssb are there on boot.  I'll post back and let you know.You were correct, as I asked in my previous post, I was thinking that ssb was being loaded because of the init.d script.  If it is no longer in the script, then we know that you need to have it.

> Hmmmm.  We could take a look at this.  I haven't knowingly done this.  But, it is certainly possible possible.If you did not run b43-fwcutter or activate it in System->Administration->Hardware Drivers then you did not load it.  You can confirm this by seeing if the b43 and b43legacy directories are out there in /lib/firmware.

---

### Post by backdoc on 2008-05-18
> **Ayuthia said:**
> Do you have ssb in your init.d script? 
Yes and No.  I have an ndiswrapper script that removed several modules and then added some back.  But, it should not be getting executed because I'm not calling it from my rc2.d directory.
```

root@laptop:/home/backdoc# grep -ir ssb /etc/init.d/*
/etc/init.d/ndiswrapper:rmmod ssb
/etc/init.d/ndiswrapper:modprobe ssb

```
But, there's no symlink to it.  I left it in for reference later.  I could delete it.  
```

root@laptop:/home/backdoc# ls /etc/rc2.d/ |grep ndiswrapper

```
[INDENT]returns nothing[/INDENT]

> **Ayuthia said:**
> 
I do have a new question--if you remove both ndiswrapper and b43, does ifconfig still show eth1?  If so, what happens when you do:
```
sudo ifconfig eth1 down
sudo modprobe ndiswrapper
```

OK.  ifconfig never shows eth1, neither does iwconfig.  If I try to do an "ifdown eth1", it just tells me that the device is not configured.  Then, modprobe'ing ndiswrapper does not make eth1 show up in ifconfig or iwconfig.
> **Ayuthia said:**
> 
I am going to go back and answer your other questions in the other post.
Cool.  First things first ;).

---

### Post by backdoc on 2008-05-18
> **Ayuthia said:**
> The only Hardy fixes are the ones that you would have done on your own.  Right now, the only one that was mentioned in this post was your init.d script.  

You were correct, as I asked in my previous post, I was thinking that ssb was being loaded because of the init.d script.  If it is no longer in the script, then we know that you need to have it.
 Yeah.  Per my last post, I think I will just delete that file to reduce confusion.  I don't need it any way.
> **Ayuthia said:**
> 
If you did not run b43-fwcutter or activate it in System->Administration->Hardware Drivers then you did not load it.  You can confirm this by seeing if the b43 and b43legacy directories are out there in /lib/firmware.

Well, we have stumbled onto something.  I have ran b43-fwcutter.  And, I do have quite a few references to some *.fw files, as well as some directories named after kernel versions.  Should I remove all of those *.fw files?  What about the kernel version directories?  They are loaded with stuff.

---

### Post by dmizer on 2008-05-19
> **Ayuthia said:**
> ssb has to be loaded after ndiswrapper or else ndiswrapper does not work.

i was not aware of this.  if that is the case, _remove ssb from the blacklist_.  then try this:
```
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
```

if that gets your card to come online, then add this to the /etc/rc.local script
```
modprobe -r ndiswrapper
modprobe -r ssb
modprobe ndiswrapper
modprobe ssb
```

---

### Post by backdoc on 2008-05-19
> **backdoc said:**
> Should I remove all of those *.fw files?  What about the kernel version directories?  They are loaded with stuff.

I went ahead and just moved all of those files out of that directory and deleted my init.d script (which wasn't being used).  Then, I rebooted.  No help.  ifconfig/iwconfig do not show my eth1 card.

Can I go ahead and delete those *.fw files?

---

### Post by Ayuthia on 2008-05-19
> **backdoc said:**
> Yeah.  Per my last post, I think I will just delete that file to reduce confusion.  I don't need it any way.


Well, we have stumbled onto something.  I have ran b43-fwcutter.  And, I do have quite a few references to some *.fw files, as well as some directories named after kernel versions.  Should I remove all of those *.fw files?  What about the kernel version directories?  They are loaded with stuff.
Don't remove those files.  What you are concerned with is if there is a b43 and b43 legacy directory in there.  If so, are there files in those directories (/lib/firmware/b43 and /lib/firmware/b43legacy)?  If there are any bcm43xx* files in /lib/firmware, then that means that bcm43xx-fwcutter was used.

The kernel version directories contain firmware for other things.

If we do have a b43/b43legacy directory with files or bcm43xx*.fw files, what we could try is to move them to your home directory.  Generally, they don't cause any problems.  I currently have them all so that I can see if I can bring up all the drivers.  I just figure if they are not there, the bcm43xx/b43/b43legacy drivers cannot work.

---

### Post by Ayuthia on 2008-05-19
> **dmizer said:**
> i was not aware of this.  if that is the case, _remove ssb from the blacklist_.  then try this:
```
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
```

if that gets your card to come online, then add this to the /etc/rc.local script
```
modprobe -r ndiswrapper
modprobe -r ssb
modprobe ndiswrapper
modprobe ssb
```
Actually, I need to clarify.  NDISwrapper does not need ssb.  What I was trying to say is that if ssb is needed in the system, it has to be loaded after NDISwrapper, not before.  If it is loaded before, NDISwrapper will have problems.

---

### Post by backdoc on 2008-05-19
> **dmizer said:**
> i was not aware of this.  if that is the case, _remove ssb from the blacklist_.  then try this:
```
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
```

if that gets your card to come online, then add this to the /etc/rc.local script
```
modprobe -r ndiswrapper
modprobe -r ssb
modprobe ndiswrapper
modprobe ssb
```

I tried this.  It did not help.

---

### Post by backdoc on 2008-05-19
> **Ayuthia said:**
> Don't remove those files. 
I've already moved them into my home directory.  Should I move them back?
> **Ayuthia said:**
> 
What you are concerned with is if there is a b43 and b43 legacy directory in there.  If so, are there files in those directories (/lib/firmware/b43 and /lib/firmware/b43legacy)?  If there are any bcm43xx* files in /lib/firmware, then that means that bcm43xx-fwcutter was used.

No.  I don't have any directories (or files) other than the kernel directories.

I've got to call it a night.  I'll be able to check this thread from work tomorrow. But, I won't be able to test anything until about 20+ hours from now.

I really appreciate all of you guy's help.  FWIW, keep in mind that if I reboot to my older kernel, I can get my wifi up.  It's just this kernel.  To me, that is a relatively important clue.

---

### Post by Ayuthia on 2008-05-19
> **backdoc said:**
> I've already moved them into my home directory.  Should I move them back?

No.  I don't have any directories (or files) other than the kernel directories.

I've got to call it a night.  I'll be able to check this thread from work tomorrow. But, I won't be able to test anything until about 20+ hours from now.

I really appreciate all of you guy's help.  FWIW, keep in mind that if I reboot to my older kernel, I can get my wifi up.  It's just this kernel.  To me, that is a relatively important clue.
Can you tell me the make and model of your computer?  I am going to research the dmesg error further.

---

### Post by backdoc on 2008-05-19
> **Ayuthia said:**
> Can you tell me the make and model of your computer?  I am going to research the dmesg error further.

Yes.  I have a Dell Latitude D800.  It's about 5 years old.

---

### Post by Ayuthia on 2008-05-19
> **backdoc said:**
> Yes.  I have a Dell Latitude D800.  It's about 5 years old.Are you using 32 or 64 bit?  Just to eliminate the headers question, I could compile the ndiswrapper.ko file for you and you can test it.

From the searches on the error in dmesg, I have found that one person say that it connects one out of five times, the developer did not have the card so was unable to test it therefore he could not fix it.

The other options that you have is to try and compile 1.50 or 1.51.  Did you try the Ubuntu repository version after removing the script?  We can even try using the b43/b43legacy driver. 

I am still looking into this further.

---

### Post by backdoc on 2008-05-19
> **Ayuthia said:**
> Are you using 32 or 64 bit?  
I am using 32 bit.
> **Ayuthia said:**
> Just to eliminate the headers question, I could compile the ndiswrapper.ko file for you and you can test it.
I'm game for that.
> **Ayuthia said:**
> 
The other options that you have is to try and compile 1.50 or 1.51. 
 
I have 1.52.  
```
ndiswrapper -v
```
[INDENT]
    utils version: '1.9', utils version needed by module: '1.9'
    module details:
    filename: /lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko
    version: 1.52
    vermagic: 2.6.24-16-generic SMP mod_unload 586[/INDENT]
> **Ayuthia said:**
> Did you try the Ubuntu repository version after removing the script?  We can even try using the b43/b43legacy driver. 
I tried Ubuntu version before downloading the source.
> **Ayuthia said:**
> 
I am still looking into this further.
Thanks.  I really appreciate it.  I hope this helps make Ubuntu a better distro and others can benefit from this.

---

### Post by Ayuthia on 2008-05-19
Before you do this, can you try one more thing:
```
sudo modprobe -r ndiswrapper
sudo depmod -ae 
sudo modprobe ndiswrapper
```
If the wireless does not work, go ahead and try the compiled .ko file.


Attached is the file.  There should already be a ndiswrapper.ko file located at /lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko.  Please make a backup copy of it in a folder in your home directory.  This is the compiled version of the .ko file.  Ubuntu has its own located at /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko.  That one comes with linux-ubuntu-restricted-modules if I recall correctly.

The file I attached does not have it's own folder so the file will be extracted in the directory that you do the extraction.  I am telling you this because if your backup file is kept in the same directory with the same name, it is going to be overwritten when you extract this file.

Once you have the file extracted, it will have to be copied to /lib/modules/2.6.24-16-generic/misc.  You will then need to the steps at the top of this post.

---

### Post by backdoc on 2008-05-19
> **Ayuthia said:**
> Before you do this, can you try one more thing:
```
sudo modprobe -r ndiswrapper
sudo depmod -ae 
sudo modprobe ndiswrapper
```

I'll be glad to try.  But, it will have to wait a few more hours until I get home.  I'm willing to continue trying things as long as necessary.
> **Ayuthia said:**
> 
If the wireless does not work, go ahead and try the compiled .ko file.

Is it attached?  I don't see it.

---

### Post by Ayuthia on 2008-05-19
Oops.

I just tried and found out that I can't get the file small enough to attach.  It is just a little over 1 Mb as a tar.bz2.

---

### Post by backdoc on 2008-05-19
> **Ayuthia said:**
> Oops.

I just tried and found out that I can't get the file small enough to attach.  It is just a little over 1 Mb as a tar.bz2.

I hate to say it, but it didn't work.  I took another look at lshw -C network, it showed ssb still had the wifi card.  So, I rmmod'd ssb and ndiswrapper and reloaded ndiswrapper.  Still no help.

---

### Post by Ayuthia on 2008-05-19
> **backdoc said:**
> I hate to say it, but it didn't work.  I took another look at lshw -C network, it showed ssb still had the wifi card.  So, I rmmod'd ssb and ndiswrapper and reloaded ndiswrapper.  Still no help.


Well, we can try other drivers.  Here is one from the NDISwrapper site:
[http://ftp.us.dell.com/network/R81433.EXE](http://ftp.us.dell.com/network/R81433.EXE)

And this one is from the no-fluff guide ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff):](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff):)
```
wget http://myspamb8.googlepages.com/WPC54Gv2_40826-pruned.zip
unzip WPC54Gv2_40826-pruned.zip
```

I am hoping that a different driver will work.  I am guessing that the changes made in 2.6.24 has created a problem in NDISwrapper.  I am thinking that this one might need to go to the NDISwrapper forum.

---

### Post by backdoc on 2008-05-19
> **Ayuthia said:**
> Well, we can try other drivers.  Here is one from the NDISwrapper site:
[http://ftp.us.dell.com/network/R81433.EXE](http://ftp.us.dell.com/network/R81433.EXE)

And this one is from the no-fluff guide ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff):](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff):)
```
wget http://myspamb8.googlepages.com/WPC54Gv2_40826-pruned.zip
unzip WPC54Gv2_40826-pruned.zip
```

I am hoping that a different driver will work.  I am guessing that the changes made in 2.6.24 has created a problem in NDISwrapper.  I am thinking that this one might need to go to the NDISwrapper forum.

OK.  We're getting somewhere.  The good news is that my card is being recognized.  The bad news is that it's not getting a signal.  What's weird is that now it's being recognized regardless of which driver I use.  I even tried my old drivers and they are working.  I could never find the driver on the No-Fluff website.  So, if that becomes an issue, I want to point that out.  

I have even gone back to my old ko file, reran depmod and I can still load my old drivers.  The same driver and ko file as when I started.  
```
iwconfig
```[INDENT]
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
         [INDENT] Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/INDENT]
[/INDENT]

I hate to stop while we're making progress.  But, I need to call it a night.

---

### Post by Ayuthia on 2008-05-20
> **backdoc said:**
> OK.  We're getting somewhere.  The good news is that my card is being recognized.  The bad news is that it's not getting a signal.  What's weird is that now it's being recognized regardless of which driver I use.  I even tried my old drivers and they are working.  I could never find the driver on the No-Fluff website.  So, if that becomes an issue, I want to point that out.  

I have even gone back to my old ko file, reran depmod and I can still load my old drivers.  The same driver and ko file as when I started.  
```
iwconfig
```[INDENT]
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
         [INDENT] Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/INDENT]
[/INDENT]

I hate to stop while we're making progress.  But, I need to call it a night.

I am trying to figure out how the links work in /etc/ndiswrapper/bcmwl5.  Can you post them:
```
ls -l /etc/ndiswrapper/bcmwl5*
lspci -nnm
```

---

### Post by backdoc on 2008-05-20
> **Ayuthia said:**
> I am trying to figure out how the links work in /etc/ndiswrapper/bcmwl5.  Can you post them:
```
ls -l /etc/ndiswrapper/bcmwl5*
lspci -nnm
```

Sure thing.  I'll do that when I get home.  

There were a couple of interesting things I noticed last night.  Not all of the drivers that I loaded last night gave the same results in iwconfig.  Some recognized the encryption key.  Some did not.  My wifi is encrypted.  You can see that the iwconfig output that I posted isn't aware of that.  None of them seemed to have any kind of signal though.  

Another thing that I noticed was that when I "installed" the driver with ndiswrapper -i, the output it generated while loading the driver differed between dirvers.

Oh.  And, after I loaded each driver, I tried bring the interface up with ifup.  They all timed out on the dhcp 'cause they aren't getting any signal.

---

### Post by backdoc on 2008-05-20
> **Ayuthia said:**
> I am trying to figure out how the links work in /etc/ndiswrapper/bcmwl5.  Can you post them:
```
ls -l /etc/ndiswrapper/bcmwl5*
lspci -nnm
```


Here ya go:

```
 ls -l /etc/ndiswrapper/bcmwl5/
```
[INDENT]total 316
-rw-r--r-- 1 root root    922 2008-05-19 22:41 14E4:4301:0002:1028.5.conf
-rw-r--r-- 1 root root    940 2008-05-19 22:41 14E4:4301:0407:1028.5.conf
-rw-r--r-- 1 root root    940 2008-05-19 22:41 14E4:4301.5.conf
-rw-r--r-- 1 root root    940 2008-05-19 22:41 14E4:4307.5.conf
-rw-r--r-- 1 root root    965 2008-05-19 22:41 14E4:4320:0001:1028.5.conf
-rw-r--r-- 1 root root    947 2008-05-19 22:41 14E4:4320:0002:1028.5.conf
-rw-r--r-- 1 root root    965 2008-05-19 22:41 14E4:4320.5.conf
-rw-r--r-- 1 root root   1025 2008-05-19 22:41 14E4:4324:0001:1028.5.conf
-rw-r--r-- 1 root root   1007 2008-05-19 22:41 14E4:4324:0002:1028.5.conf
-rw-r--r-- 1 root root   1025 2008-05-19 22:41 14E4:4324.5.conf
-rw-r--r-- 1 root root  17742 2008-05-19 22:41 bcmwl5.inf
-rw-r--r-- 1 root root 254208 2008-05-19 22:41 bcmwl5.sys[/INDENT]
```
lspci -nnm
```
[INDENT]00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "82855PM Processor to I/O Controller [3340]" -r03 "" ""
00:01.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82855PM Processor to AGP Controller [3341]" -r03 "" ""
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [24c2]" -r01 "Intel Corporation [8086]" "Latitude D400 [4541]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [24c4]" -r01 "Intel Corporation [8086]" "Latitude D400 [4541]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [24c7]" -r01 "Intel Corporation [8086]" "Latitude D400 [4541]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [24cd]" -r01 -p20 "Dell [1028]" "Unknown device [014e]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 Mobile PCI Bridge [2448]" -r81 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "82801DBM (ICH4-M) LPC Interface Bridge [24cc]" -r01 "" ""
00:1f.1 "IDE interface [0101]" "Intel Corporation [8086]" "82801DBM (ICH4-M) IDE Controller [24ca]" -r01 -p8a "Intel Corporation [8086]" "Latitude D400 [4541]"
00:1f.5 "Multimedia audio controller [0401]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [24c5]" -r01 "Dell [1028]" "Unknown device [014e]"
00:1f.6 "Modem [0703]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [24c6]" -r01 "Conexant [14f1]" "D480 MDC V.9x Modem [5422]"
01:00.0 "VGA compatible controller [0300]" "nVidia Corporation [10de]" "NV28 [GeForce4 Ti 4200 Go AGP 8x] [0286]" -ra1 "Dell [1028]" "Unknown device [0179]"
02:00.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "NetXtreme BCM5705M Gigabit Ethernet [165d]" -r01 "Dell [1028]" "Latitude D400 [865d]"
02:01.0 "CardBus bridge [0607]" "Texas Instruments [104c]" "PCI7510 PC card Cardbus Controller [ac47]" -r01 "Dell [1028]" "Latitude D800 [014e]"
02:01.1 "CardBus bridge [0607]" "Texas Instruments [104c]" "PCI7510,7610 PC card Cardbus Controller [ac4a]" -r01 "Dell [1028]" "Latitude D800 [014e]"
02:01.2 "FireWire (IEEE 1394) [0c00]" "Texas Instruments [104c]" "PCI7410,7510,7610 OHCI-Lynx Controller [802b]" -p10 "Dell [1028]" "PCI7410,7510,7610 OHCI-Lynx Controller (Latitude D800) [014e]"
02:01.3 "System peripheral [0880]" "Texas Instruments [104c]" "PCI7410,7510,7610 PCI Firmware Loading Function [8204]" "Dell [1028]" "Latitude D800 [014e]"
02:03.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r02 "Dell [1028]" "TrueMobile 1300 WLAN Mini-PCI Card [0001]"[/INDENT]

---

### Post by Ayuthia on 2008-05-20
> **backdoc said:**
> Here ya go:

```
 ls -l /etc/ndiswrapper/bcmwl5/
```
[INDENT]total 316
-rw-r--r-- 1 root root    922 2008-05-19 22:41 14E4:4301:0002:1028.5.conf
-rw-r--r-- 1 root root    940 2008-05-19 22:41 14E4:4301:0407:1028.5.conf
-rw-r--r-- 1 root root    940 2008-05-19 22:41 14E4:4301.5.conf
-rw-r--r-- 1 root root    940 2008-05-19 22:41 14E4:4307.5.conf
-rw-r--r-- 1 root root    965 2008-05-19 22:41 14E4:4320:0001:1028.5.conf
-rw-r--r-- 1 root root    947 2008-05-19 22:41 14E4:4320:0002:1028.5.conf
-rw-r--r-- 1 root root    965 2008-05-19 22:41 14E4:4320.5.conf
-rw-r--r-- 1 root root   1025 2008-05-19 22:41 14E4:4324:0001:1028.5.conf
-rw-r--r-- 1 root root   1007 2008-05-19 22:41 14E4:4324:0002:1028.5.conf
-rw-r--r-- 1 root root   1025 2008-05-19 22:41 14E4:4324.5.conf
-rw-r--r-- 1 root root  17742 2008-05-19 22:41 bcmwl5.inf
-rw-r--r-- 1 root root 254208 2008-05-19 22:41 bcmwl5.sys[/INDENT]
```
lspci -nnm
```
[INDENT]00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "82855PM Processor to I/O Controller [3340]" -r03 "" ""
00:01.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82855PM Processor to AGP Controller [3341]" -r03 "" ""
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [24c2]" -r01 "Intel Corporation [8086]" "Latitude D400 [4541]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [24c4]" -r01 "Intel Corporation [8086]" "Latitude D400 [4541]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [24c7]" -r01 "Intel Corporation [8086]" "Latitude D400 [4541]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [24cd]" -r01 -p20 "Dell [1028]" "Unknown device [014e]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 Mobile PCI Bridge [2448]" -r81 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "82801DBM (ICH4-M) LPC Interface Bridge [24cc]" -r01 "" ""
00:1f.1 "IDE interface [0101]" "Intel Corporation [8086]" "82801DBM (ICH4-M) IDE Controller [24ca]" -r01 -p8a "Intel Corporation [8086]" "Latitude D400 [4541]"
00:1f.5 "Multimedia audio controller [0401]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [24c5]" -r01 "Dell [1028]" "Unknown device [014e]"
00:1f.6 "Modem [0703]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [24c6]" -r01 "Conexant [14f1]" "D480 MDC V.9x Modem [5422]"
01:00.0 "VGA compatible controller [0300]" "nVidia Corporation [10de]" "NV28 [GeForce4 Ti 4200 Go AGP 8x] [0286]" -ra1 "Dell [1028]" "Unknown device [0179]"
02:00.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "NetXtreme BCM5705M Gigabit Ethernet [165d]" -r01 "Dell [1028]" "Latitude D400 [865d]"
02:01.0 "CardBus bridge [0607]" "Texas Instruments [104c]" "PCI7510 PC card Cardbus Controller [ac47]" -r01 "Dell [1028]" "Latitude D800 [014e]"
02:01.1 "CardBus bridge [0607]" "Texas Instruments [104c]" "PCI7510,7610 PC card Cardbus Controller [ac4a]" -r01 "Dell [1028]" "Latitude D800 [014e]"
02:01.2 "FireWire (IEEE 1394) [0c00]" "Texas Instruments [104c]" "PCI7410,7510,7610 OHCI-Lynx Controller [802b]" -p10 "Dell [1028]" "PCI7410,7510,7610 OHCI-Lynx Controller (Latitude D800) [014e]"
02:01.3 "System peripheral [0880]" "Texas Instruments [104c]" "PCI7410,7510,7610 PCI Firmware Loading Function [8204]" "Dell [1028]" "Latitude D800 [014e]"
02:03.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r02 "Dell [1028]" "TrueMobile 1300 WLAN Mini-PCI Card [0001]"[/INDENT]

Here is the information that I am trying to understand.  Your card shows 14e4:4320 and 1028 and 0001.  So in theory, there should be a file there that has 14E4:4320:0001:1028.5.conf

The other strange thing that I see is that your 14E4:4320.5.conf file is not a symbolic link.

Here is a snip of mine:
lrwxrwxrwx 1 root root     26 2008-05-19 02:42 14E4:4311.5.conf -> 14E4:4311:1363:103C.5.conf

03:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM94311MCG wlan mini-PCI [4311]" -r01 "Hewlett-Packard Company [103c]" "Unknown device [1363]"

This is not to say that it won't work.  I am just thinking that if there is an exact match, it should work.  I know that there are some that don't have a match and it still works.

Can you try using the Dell driver that you downloaded ([http://ftp.us.dell.com/network/R81433.EXE](http://ftp.us.dell.com/network/R81433.EXE)) and see what it shows when it is installed?

---

### Post by backdoc on 2008-05-20
> **Ayuthia said:**
> Can you try using the Dell driver that you downloaded ([http://ftp.us.dell.com/network/R81433.EXE](http://ftp.us.dell.com/network/R81433.EXE)) and see what it shows when it is installed?

There were two drivers in that Dell .exe file.  The first one extracted to a directory called /AR.  That is the first one I am posting.  I went ahead and grepped broadcom to make it easier for you.  If you need to see more, I can do it again:

```
ls -l /etc/ndiswrapper/bcmwl5/
```[INDENT]
total 1584
-rw-r--r-- 1 root root     989 2008-05-20 19:55 14E4:4320:0001:1028.5.conf
-rw-r--r-- 1 root root     989 2008-05-20 19:55 14E4:4320:0002:1028.5.conf
-rw-r--r-- 1 root root     992 2008-05-20 19:55 14E4:4320:0003:1028.5.conf
-rw-r--r-- 1 root root     992 2008-05-20 19:55 14E4:4320:0004:1028.5.conf
-rw-r--r-- 1 root root     989 2008-05-20 19:55 14E4:4320.5.conf
-rw-r--r-- 1 root root    1041 2008-05-20 19:55 14E4:4324:0001:1028.5.conf
-rw-r--r-- 1 root root    1041 2008-05-20 19:55 14E4:4324:0002:1028.5.conf
-rw-r--r-- 1 root root    1044 2008-05-20 19:55 14E4:4324:0003:1028.5.conf
-rw-r--r-- 1 root root    1044 2008-05-20 19:55 14E4:4324:0004:1028.5.conf
-rw-r--r-- 1 root root    1041 2008-05-20 19:55 14E4:4324.5.conf
-rw-r--r-- 1 root root 1255736 2008-05-20 19:55 bcmwl5.inf
-rw-r--r-- 1 root root  315392 2008-05-20 19:55 bcmwl5.sys[/INDENT]
```
lspci -nnm |grep -i broadcom
```
[INDENT]02:00.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "NetXtreme BCM5705M Gigabit Ethernet [165d]" -r01 "Dell [1028]" "Latitude D400 [865d]"
02:03.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r02 "Dell [1028]" "TrueMobile 1300 WLAN Mini-PCI Card [0001]"[/INDENT]

Here's the one that went into the /IR directory:

```
 ls -l /etc/ndiswrapper/bcmwl5/total 1584
```
[INDENT]-rw-r--r-- 1 root root     989 2008-05-20 20:01 14E4:4320:0001:1028.5.conf
-rw-r--r-- 1 root root     989 2008-05-20 20:01 14E4:4320:0002:1028.5.conf
-rw-r--r-- 1 root root     992 2008-05-20 20:01 14E4:4320:0003:1028.5.conf
-rw-r--r-- 1 root root     992 2008-05-20 20:01 14E4:4320:0004:1028.5.conf
-rw-r--r-- 1 root root     989 2008-05-20 20:01 14E4:4320.5.conf
-rw-r--r-- 1 root root    1041 2008-05-20 20:01 14E4:4324:0001:1028.5.conf
-rw-r--r-- 1 root root    1041 2008-05-20 20:01 14E4:4324:0002:1028.5.conf
-rw-r--r-- 1 root root    1044 2008-05-20 20:01 14E4:4324:0003:1028.5.conf
-rw-r--r-- 1 root root    1044 2008-05-20 20:01 14E4:4324:0004:1028.5.conf
-rw-r--r-- 1 root root    1041 2008-05-20 20:01 14E4:4324.5.conf
-rw-r--r-- 1 root root 1255306 2008-05-20 20:01 bcmwl5.inf
-rw-r--r-- 1 root root  315392 2008-05-20 20:01 bcmwl5.sys
[/INDENT]
```
lspci -nnm |grep -i broadcom
```
[INDENT]02:00.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "NetXtreme BCM5705M Gigabit Ethernet [165d]" -r01 "Dell [1028]" "Latitude D400 [865d]"
02:03.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r02 "Dell [1028]" "TrueMobile 1300 WLAN Mini-PCI Card [0001]"
[/INDENT]

---

### Post by Ayuthia on 2008-05-20
Can you check /etc/modprobe.d/ndiswrapper?  It should have similar information.  The alias lines should have the same numbers as /etc/ndiswrapper/bcmwl5.  If they don't, try doing sudo ndiswrapper -ma.

If this still doesn't work, we will try the symbolic link for it.  Move /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf to your home directory and then make the following symbolic link:
sudo /etc/ndiswrapper/bcmwl5/14E4:4320:0001:1028.5.conf /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf

After you do that, you will need to the modprobe -r/modprobe thing.

---

### Post by backdoc on 2008-05-20
> **Ayuthia said:**
> 
Can you try using the Dell driver that you downloaded ([http://ftp.us.dell.com/network/R81433.EXE](http://ftp.us.dell.com/network/R81433.EXE)) and see what it shows when it is installed?

Below is the same info from the driver I got from the wget script.  It has the symlink like yours.  I notice that when I installed the other inf files (plus another that I have) with ndiswrapper -i, most of them are generating a lot of messages.  This one doesn't.  

Here's what the noisy ones look like:

```
ndiswrapper -i BCMWL5.INF 
```
[INDENT]installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
[/INDENT]
Here's the quiet one:

```
ndiswrapper -i bcmwl5.inf
```
[INDENT]installing bcmwl5 ...[/INDENT]

Here's the other info you asked for on the quiet one.  It's the one with the symlink like yours.

```
[INDENT]ls -l /etc/ndiswrapper/bcmwl5/
```
total 292
-rw-r--r-- 1 root root    723 2008-05-20 20:13 14E4:4301:4301:1737.5.conf
lrwxrwxrwx 1 root root     26 2008-05-20 20:13 14E4:4301.5.conf -> 14E4:4301:4301:1737.5.conf
-rw-r--r-- 1 root root    735 2008-05-20 20:13 14E4:4320:0417:14E4.5.conf
-rw-r--r-- 1 root root    735 2008-05-20 20:13 14E4:4320:4320:1737.5.conf
-rw-r--r-- 1 root root    735 2008-05-20 20:13 14E4:4320.5.conf
-rw-r--r-- 1 root root  17742 2008-05-20 20:13 bcmwl5.inf
-rw-r--r-- 1 root root 254208 2008-05-20 20:13 bcmwl5.sys[/INDENT]
```
lspci -nnm |grep -i broadcom
```[INDENT]
02:00.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "NetXtreme BCM5705M Gigabit Ethernet [165d]" -r01 "Dell [1028]" "Latitude D400 [865d]"
02:03.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r02 "Dell [1028]" "TrueMobile 1300 WLAN Mini-PCI Card [0001]"
[/INDENT]

---

### Post by Ayuthia on 2008-05-20
> **backdoc said:**
> Below is the same info from the driver I got from the wget script.  It has the symlink like yours.  I notice that when I installed the other inf files (plus another that I have) with ndiswrapper -i, most of them are generating a lot of messages.  This one doesn't.  

Here's what the noisy ones look like:

```
ndiswrapper -i BCMWL5.INF 
```
[INDENT]installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
[/INDENT]


The noise I think is ok.  I want to say that I have seen them before.  I could be wrong though.  You could try them out first and see what happens.

---

### Post by backdoc on 2008-05-20
> **Ayuthia said:**
> Can you check /etc/modprobe.d/ndiswrapper?  It should have similar information.  The alias lines should have the same numbers as /etc/ndiswrapper/bcmwl5.  If they don't, try doing sudo ndiswrapper -ma.

If this still doesn't work, we will try the symbolic link for it.  Move /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf to your home directory and then make the following symbolic link:
sudo /etc/ndiswrapper/bcmwl5/14E4:4320:0001:1028.5.conf /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf

After you do that, you will need to the modprobe -r/modprobe thing.

I checked the /etc/modprobe.d/ndiswrapper file, it just had one alias line.  So, I did the ndiswrapper -ma thing and it added all of those other lines:
```
cat /etc/modprobe.d/ndiswrapper 
```[INDENT]
alias pci:v000014E4d00004301sv00004301sd00001737bc*sc*i* ndiswrapper
alias pci:v000014E4d00004301sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000417sd000014E4bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00004320sd00001737bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper[/INDENT]

Do you still want to do the symlink thing?  This driver has it.
```
ls -l /etc/ndiswrapper/bcmwl5/
```
[INDENT]total 292
-rw-r--r-- 1 root root    723 2008-05-20 20:19 14E4:4301:4301:1737.5.conf
lrwxrwxrwx 1 root root     26 2008-05-20 20:19 14E4:4301.5.conf -> 14E4:4301:4301:1737.5.conf
-rw-r--r-- 1 root root    735 2008-05-20 20:19 14E4:4320:0417:14E4.5.conf
-rw-r--r-- 1 root root    735 2008-05-20 20:19 14E4:4320:4320:1737.5.conf
-rw-r--r-- 1 root root    735 2008-05-20 20:19 14E4:4320.5.conf
-rw-r--r-- 1 root root  17742 2008-05-20 20:19 bcmwl5.inf
-rw-r--r-- 1 root root 254208 2008-05-20 20:19 bcmwl5.sys
[/INDENT]

---

### Post by Ayuthia on 2008-05-20
> **backdoc said:**
> I checked the /etc/modprobe.d/ndiswrapper file, it just had one alias line.  So, I did the ndiswrapper -ma thing and it added all of those other lines:
```
cat /etc/modprobe.d/ndiswrapper 
```[INDENT]
alias pci:v000014E4d00004301sv00004301sd00001737bc*sc*i* ndiswrapper
alias pci:v000014E4d00004301sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000417sd000014E4bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00004320sd00001737bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper[/INDENT]

Do you still want to do the symlink thing?  This driver has it.
```
ls -l /etc/ndiswrapper/bcmwl5/
```
[INDENT]total 292
-rw-r--r-- 1 root root    723 2008-05-20 20:19 14E4:4301:4301:1737.5.conf
lrwxrwxrwx 1 root root     26 2008-05-20 20:19 14E4:4301.5.conf -> 14E4:4301:4301:1737.5.conf
-rw-r--r-- 1 root root    735 2008-05-20 20:19 14E4:4320:0417:14E4.5.conf
-rw-r--r-- 1 root root    735 2008-05-20 20:19 14E4:4320:4320:1737.5.conf
-rw-r--r-- 1 root root    735 2008-05-20 20:19 14E4:4320.5.conf
-rw-r--r-- 1 root root  17742 2008-05-20 20:19 bcmwl5.inf
-rw-r--r-- 1 root root 254208 2008-05-20 20:19 bcmwl5.sys
[/INDENT]

It does have the symlink, but it is for the 4301 card instead of the 4320 card.  I would try the other one first.

---

### Post by santhony on 2008-05-20
Dam... I've been reading your thread... I have the same wireless card adapter in my Compaq Presario 2195US.. And haven't been able to get it to work either.....  

It looks like if you guys don't get this...neither will I.....

---

### Post by Ayuthia on 2008-05-20
Well, if this doesn't work, I am thinking that we try using wicd or turning off Network Manager and see what happens.

Just to add another thing, we can also try the b43legacy route.  I think that your wireless uses it.

---

### Post by backdoc on 2008-05-20
> **Ayuthia said:**
> Well, if this doesn't work, I am thinking that we try using wicd or turning off Network Manager and see what happens.

Just to add another thing, we can also try the b43legacy route.  I think that your wireless uses it.

I tried the symlink.  It didn't help.  What do you have in mind?

It will be tomorrow before I can try the next thing.

---

### Post by Ayuthia on 2008-05-20
> **backdoc said:**
> I tried the symlink.  It didn't help.  What do you have in mind?

It will be tomorrow before I can try the next thing.
I think we should try turning off Network Manager and try to connect through the Terminal:
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo iwconfig eth1 essid <name>
sudo dhclient eth1
```

---

### Post by backdoc on 2008-05-21
> **Ayuthia said:**
> I think we should try turning off Network Manager and try to connect through the Terminal:
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo iwconfig eth1 essid <name>
sudo dhclient eth1
```

Sorry.  That didn't work either.  I always connect through the terminal, btw.  So, unless networkmanager can interfere without me knowing about it, it shouldn't be a factor.

I didn't really think it would connect because I'm not getting any signal yet.  For whatever reason, I can load my driver where I couldn't before.  But, evidently, the drivers aren't working.  I have ran "ifup" on my card.  So, the encryption key is present, which I will obscure.  But, pay particular attention to the link quality and Signal Level.

```
iwconfig eth1
```
[INDENT]eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:secret   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/INDENT]

---

### Post by santhony on 2008-05-21
I just got my BCM4306 Broadcom wireless card working... Not sure how... But when I booted this morning and plugged in my SSID and WPA pass, the device started working... I originally followed this post below...

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)..

Let me know if you need any info from my setup..  Thanks

Maybe if we can this process nailed down... we can post an install process for other peeps...

---

### Post by backdoc on 2008-05-21
I was just thinking about something.  After running "ndiswrapper -i", do you think I should I always follow that with "ndiswrapper -ma"?  I think that I always rmmod/modprobe ndiswrapper between trying different drivers.  But, /etc/modprobe.d/ndiswrapper could have been out of synch with /lib/.../bcmwl5/.  Up until just the other day, I have always just run "ndiswrapper -m", as opposed to, "ndiswrapper -ma".  I've never had any trouble with that.  It just adds an entry like "alias eth1 ndiswrapper".  Consequently, I would not have to worry about keeping it synched with various drivers.  But, if I run "ndiswrapper -ma", maybe I do need to worry about it.

---

### Post by backdoc on 2008-05-21
> **santhony said:**
> I just got my BCM4306 Broadcom wireless card working... I originally followed this post below...

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)..
Cool.  Glad you got yours working.  Thanks for posting your results.

I have seen that thread.  I think I've followed parts of it, but not entirely.  At this point, maybe I should.  It seems to have worked for you.  I might should add that the reason that I haven't followed it entirely is because there were several steps that shouldn't be required for me.  For example, installing ndiswrapper-utils or downloading a driver from Compaq.  Not only that, but my setup had to be close.  It was working.  So, I didn't want to overboard modifying things.  Maybe I missed something important.

> **santhony said:**
> Let me know if you need any info from my setup..  Thanks

Thanks.  I will let you know.  

> **santhony said:**
> Maybe if we can this process nailed down... we can post an install process for other peeps...
Well, if the other HOWTO worked for you, maybe we don't need to.  What I'm more interested in, at this point, is preventing the problem.  My wireless was working fine in Gutsy, before upgrading to Hardy.  The upgrade/install process needs some improvement.

---

### Post by Ayuthia on 2008-05-21
> **backdoc said:**
> What I'm more interested in, at this point, is preventing the problem.  My wireless was working fine in Gutsy, before upgrading to Hardy.  The upgrade/install process needs some improvement.I think that the issue that we are running into are probably more related to the compiler or the new kernel headers.  There are people trying to compile the old drivers for their Intel cards but have to application.

I was thinking that network manager is interfering with trying to connect manually.  It is hard to tell though.  What happened when you tried to connect manually?  Did it just not connect at the dhclient stage?

Did you ever try the b43 driver?  That might still be an option.  However, I do want to see what is causing this to not work.  Another thing to try is the driver from santhony's link.

As for the ndiswrapper -ma, I have just recently done this.  I don't know how much of a difference it really makes, but I think that it helps.  But I have no evidence behind it. :)

---

### Post by backdoc on 2008-05-21
> **Ayuthia said:**
> What happened when you tried to connect manually?  Did it just not connect at the dhclient stage?
Yep.  It couldn't get an IP because it can't get a signal to hit the DHCP server.

> **Ayuthia said:**
> 
Did you ever try the b43 driver?  

Not yet.  

> **Ayuthia said:**
> 
Another thing to try is the driver from santhony's link.

I'll try that tonight.

---

### Post by backdoc on 2008-05-21
> **Ayuthia said:**
> 
Did you ever try the b43 driver?  That might still be an option.  However, I do want to see what is causing this to not work.  Another thing to try is the driver from santhony's link.

OK.  I tried that driver.  And, I did everything in the HOWTO, except for setting up the script and adding "ENABLED" to wpasupplicant.  I didn't know what that did.  But, I skipped it anyway.  The driver will load, but still it won't provide a signal.

I guess I will have to try the bcm43xx driver.  I'm still going to point my finger at the kernel as the problem.  We tried your ko file.  We know what headers it was built against.  If I reboot to my old kernel, I was able to get wireless working using everything the way it was before the upgrade.  I haven't tried it lately.  But, it's probably still true.  I think the Ubuntu kernel maintainers need to address this.  I hate to say it, but it's over my head.

I guess I can google that or search the forums for help on that.  I can post my results back here.

Do you have anything else you want me to try before I start on that?

---

### Post by Ayuthia on 2008-05-21
> **backdoc said:**
> OK.  I tried that driver.  And, I did everything in the HOWTO, except for setting up the script and adding "ENABLED" to wpasupplicant.  I didn't know what that did.  But, I skipped it anyway.  The driver will load, but still it won't provide a signal.

I guess I will have to try the bcm43xx driver.  I'm still going to point my finger at the kernel as the problem.  We tried your ko file.  We know what headers it was built against.  If I reboot to my old kernel, I was able to get wireless working using everything the way it was before the upgrade.  I haven't tried it lately.  But, it's probably still true.  I think the Ubuntu kernel maintainers need to address this.  I hate to say it, but it's over my head.

I guess I can google that or search the forums for help on that.  I can post my results back here.

Do you have anything else you want me to try before I start on that?

I can't think of anything else right now.  I am at a loss about you not being able to get a signal.  You can also check the NDISwrapper forum to see if they have any ideas.  I think that the developers read some of them so they might have a good idea about what to do.

If you are not concerned about Gutsy as much, you should try the b43-fwcutter instead of bcm43xx.  It will be the driver that will get the updates.  All you should need to do is make sure that the wireless script is out, that bcm43xx and ndiswrapper is blacklisted, and that b43 is in /etc/modules.  Of course you will need the firmware.  This is the bare minimum that you would need without having to uninstall or remove anything.

---

### Post by backdoc on 2008-05-22
You lost me a little here and there.  I need some clarification.
> **Ayuthia said:**
> I think that the developers read some of them... Not sure what you meant.

> **Ayuthia said:**
> If you are not concerned about Gutsy as much, ...  What do you mean "concerned about Gutsy"?

> **Ayuthia said:**
> All you should need to do is make sure that the wireless script is out, What wireless script?

---

### Post by Ayuthia on 2008-05-22
If you post the issue in the NDISwrapper forum, one of the developers of NDISwrapper might reply back telling you what to do.

I also asked about the Gutsy thing.  What I am trying to say is that the b43 driver does not run in kernels less than 2.6.24 so if you try to use it in the 2.6.22 kernel, it will most likely not work.  Shouldn't be too big of a deal.

As for the wireless script, it is the one that is in post #4.  I thought that you got rid of it, but was double checking.

---

### Post by backdoc on 2008-05-22
> **Ayuthia said:**
> If you post the issue in the NDISwrapper forum, one of the developers of NDISwrapper might reply back telling you what to do.

I also asked about the Gutsy thing.  What I am trying to say is that the b43 driver does not run in kernels less than 2.6.24 so if you try to use it in the 2.6.22 kernel, it will most likely not work.  Shouldn't be too big of a deal.

As for the wireless script, it is the one that is in post #4.  I thought that you got rid of it, but was double checking.

Thanks for clarifying.  I understand now.  I don't really care about running Gutsy.  If push comes to shove, I might revert back to the older kernel though.

Whatever I figure out, I'll post back to this thread.

I really appreciate you sticking with me so long.

Thanks!

---

### Post by santhony on 2008-05-24
BACKDOC... I recommend you follow that link... It does break off for each version of card that you have... I have BCM4306 ver. 2   

You really got nothing to loose at this point...  It does give the exact directions for BCM4306...

Check this one link out...  That's all I used...After doing them.. I then go into the System Network and set my WIFI card from there...

Here is the instructions that are more thorough:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by santhony on 2008-05-24
Here's the other link I've looked at also...

[http://ubuntuforums.org/showthread.php?t=340689&highlight=recommend+wireless](http://ubuntuforums.org/showthread.php?t=340689&highlight=recommend+wireless)

---

### Post by backdoc on 2008-05-27
> **santhony said:**
> BACKDOC... I recommend you follow that link... It does break off for each version of card that you have... I have BCM4306 ver. 2   

You really got nothing to loose at this point...  It does give the exact directions for BCM4306...

Check this one link out...  That's all I used...After doing them.. I then go into the System Network and set my WIFI card from there...

Here is the instructions that are more thorough:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

Thanks.  

Outside of a thing or two, I have pretty much followed that.  For example, I know for a 100% fact that my /etc/network/interfaces file is valid.  I only stand a chance of screwing it up if I follow that part.  And, there is no point in setting up a script to do what will not work manually by typing it on the command line.  Putting it in a script is only for convenience.  But, maybe I missed something.  So, I'll take your advice and try it line by line.

I just can't get over the fact that if I reboot into my old kernel, I can have wireless working simply by loading my ndiswrapper module and typing "ifup eth1".  So, I don't see how there can be anything wrong with 1. ndiswrapper 2. my interfaces file and 3. my drivers.  The only thing different is the kernel.  So, I intend to look at the kernel config and see if I can figure out what ssb is used for and see if I couldn't remove some cruft while I'm reconfiguring it.  I do wonder how ndiswrapper can work with the old kernel, if it is compiled for my current kernel.  Hmmmm....  I did try the version that Ayuthia compiled for me.  So, we should have eliminated any issues with compatibility between the kernel and the module.

I've been looking at the ndiswrapper FAQ and Troubleshooting pages when I have had time.  They do address the issue that I'm having where "ndiswrapper -l" reports an alternate driver is being used.  They say you must [COLOR="Red"][***unload the alternate driver***]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/").[/COLOR]  I figure that would be step one.

I have not had much time since my last post.  I will be working on this, but it will be 10 minutes at at time here and there. So, if you are subscribed to this thread and don't hear from me for awhile, don't think I've given up.  I may give up.  But, if I do, I will post back to this thread.  I have a couple of options.  I can roll back my kernel.  I can restore a backup from before the upgrade (back to Gutsy).  Or, if I have to dig into the kernel config, I may just dump Ubuntu and go to Debian or Slackware.  I find Ubuntu to be somewhat sluggish on my older laptop.  But, I tolerate it because I like the many conveniences that Ubuntu offers.  I've gotten too old and have had my fill of struggling to make my hardware work.  If I have to struggle to make my hardware work, what's the point of using Ubuntu?  If I have to recompile my kernel, I might as well be using a distro with a smaller footprint.

---

### Post by santhony on 2008-05-27
I reloaded my system last nite and installed the ndiswrapper from this link..

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851).


It did work for me... though I did have to run the commands twice in order for it to take...  I have a good feeling for what is going on and how this thing works...   

The final check point is when you run the command lshw -C, it should show you are using ndsiwrapper and not the ssb... 

The instructions from the link are not absolute, in that I don't always get the response they indicate. 

I'm not sure where in the file structure you should be when you run the lshw -C command... But if it doesn't take and gives the the usage.. Just run lshw without the -C option..  And look for the wirless output, should look like something like this:
*-network:0
             description: Wireless interface
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: wlan0
             version: 02
             serial: 00:90:4b:43:bf:ad
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,07/ ip=192.168.1.109 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

Notice module says ndiswrapper, it should not show ssb.. If it does, then it didn't take..

---

### Post by backdoc on 2008-05-27
> **santhony said:**
> I reloaded my system last nite and installed the ndiswrapper from this link..

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851).


It did work for me... though I did have to run the commands twice in order for it to take...  I have a good feeling for what is going on and how this thing works...   

The final check point is when you run the command lshw -C, it should show you are using ndsiwrapper and not the ssb... 

The instructions from the link are not absolute, in that I don't always get the response they indicate. 

I'm not sure where in the file structure you should be when you run the lshw -C command... But if it doesn't take and gives the the usage.. Just run lshw without the -C option..  And look for the wirless output, should look like something like this:
*-network:0
             description: Wireless interface
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: wlan0
             version: 02
             serial: 00:90:4b:43:bf:ad
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,07/ ip=192.168.1.109 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

Notice module says ndiswrapper, it should not show ssb.. If it does, then it didn't take..

Thanks.  That link looks more promising.  And, it acknowledges the module loading bug [***[COLOR="Purple"]here[/COLOR]***]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558").


I'll give that a try as soon as I can (may not be tonight).

---

### Post by santhony on 2008-05-27
Backdoc... Also.. what version of the bcm306 do you have?


run this command lspci

My output shows an entry like this:

00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

Then next, before you do anything run the lshw command and see if it is using ssb or ndiswrapper...

In that last link I sent you.. I says that ubuntu can be loading the ssb overtop of your ndiswrapper, even tho you have installed ndis properly..  

At the bottom of the instructions, it tells you have to remove the bcm4306 ssb drivers from loading...

Anyways.. tell me what you get from running those two commands above..  

thanks

---

### Post by jw5801 on 2008-05-27
Just a query, but you do only have one driver installed via ndiswrapper -i for each test yes? Having more than one will probably break things.

As far as ssb goes, if it's blacklisted and still being loaded for some reason, it's most probably being loaded in the initramfs, not entirely sure why however. For my setup it was being loaded along with b44 in order to bring up my wired interface for a network boot, I stopped that by changing the interface in /etc/initramfs-tools/initramfs.conf to lo rather than eth0. That shouldn't make a difference though, given you don't have a bcm44 wired card. Might want to experiment a bit with it if you want to stop ssb being loaded to make it easier to load ndiswrapper correctly.

That's mostly a non-issue though, since the main problem is getting ndiswrapper working properly before we worry about graceful loading. As for that I think it's just a matter of finding a happy driver and making sure there aren't any others floating around to interfere. If it were an issue with ndiwrapper being compiled against the wrong kernel headers then you'd get nasty dmesg errors on attempting to load it, since it's loading fine now I don't think that's the case.

---

### Post by backdoc on 2008-05-28
> **santhony said:**
> Backdoc... Also.. what version of the bcm306 do you have?


run this command lspci

My output shows an entry like this:

00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

Then next, before you do anything run the lshw command and see if it is using ssb or ndiswrapper...

In that last link I sent you.. I says that ubuntu can be loading the ssb overtop of your ndiswrapper, even tho you have installed ndis properly..  

At the bottom of the instructions, it tells you have to remove the bcm4306 ssb drivers from loading...

Anyways.. tell me what you get from running those two commands above..  

thanks

I'm going to try to make it through the link tonight.  I'll post when I get done.  It could be a day or so before I get time to finish it.  Here's the output you wanted to see.

```
lspci |grep -i broadcom
```
[INDENT]02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
[/INDENT]

```
lshw -C network
```
[INDENT]
<the first network device is my hard wired and not shown here>
       *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32
[/INDENT]

---

### Post by backdoc on 2008-05-28
> **santhony said:**
> I reloaded my system last nite and installed the ndiswrapper from this link..

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851).


It did work for me... though I did have to run the commands twice in order for it to take...  I have a good feeling for what is going on and how this thing works...   

The final check point is when you run the command lshw -C, it should show you are using ndsiwrapper and not the ssb... 

The instructions from the link are not absolute, in that I don't always get the response they indicate. 

I'm not sure where in the file structure you should be when you run the lshw -C command... But if it doesn't take and gives the the usage.. Just run lshw without the -C option..  And look for the wirless output, should look like something like this:
*-network:0
             description: Wireless interface
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: wlan0
             version: 02
             serial: 00:90:4b:43:bf:ad
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,07/ ip=192.168.1.109 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

Notice module says ndiswrapper, it should not show ssb.. If it does, then it didn't take..

This is still not working for me.  ssb is still taking control.  I went down to the line where it says "jump to here" if lshw shows ssb.  I did the rmmod/modprobe thing about 3 times.  On the first two, Ubuntu crashed when I loaded the module.  On the last time, it didn't crash, but it still showed ssb owning my wifi card:

[INDENT]  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
[/INDENT]

I'm about to my wits end on this.  I may try another thing or two.  But, if I can't get it worked out relatively soon, I'm going to have to throw in the towel.  I'm beginning to lose patience.

---

### Post by dmizer on 2008-05-29
something's really wrong here.  you've blacklisted all of the native modules, yet they're still loading.

either your blacklist is not working (unlikely), or something else is going on here.  in [post 19](http://ubuntuforums.org/showpost.php?p=4990044&postcount=19), you mentioned that you have all of the following modules blacklisted:

blacklist bcm43xx
blacklist b43
blacklist b43-pci-bridge
blacklist b43legacy
blacklist b44
blacklist ssb

this means that all of the above lines are in /etc/modprobe.d/blacklist.  this should not have been a new file, there should have already been a long list of commented blacklisted modules.  if you are absolutely certain (sometimes everyone misses very simple things), then also add the above list to the following file:
/etc/modprobe.d/blacklist.local

this file may not exist (i'm not sure, i don't have my hardy machine working correctly at the moment).  if it does not exist, create it.

you may also try this -
on boot, hit the <esc> key to enter the grub menu, and edit your kernel boot line.  add the following option to the end of your current kernel:
```
ssb.blacklist=yes
```
this may prevent your machine from booting properly, but it's worth a try because a reboot will reset the kernel to its former arangement.

if neither of these two solutions work for you, then your only option left at this point is to file a bug report against modprobe because the blacklist is not preventing the ssb module from loading.

---

### Post by backdoc on 2008-05-29
> **dmizer said:**
> something's really wrong here.  you've blacklisted all of the native modules, yet they're still loading.

either your blacklist is not working (unlikely), or something else is going on here.  in [post 19](http://ubuntuforums.org/showpost.php?p=4990044&postcount=19), you mentioned that you have all of the following modules blacklisted:

blacklist bcm43xx
blacklist b43
blacklist b43-pci-bridge
blacklist b43legacy
blacklist b44
blacklist ssb

this means that all of the above lines are in /etc/modprobe.d/blacklist.  this should not have been a new file, there should have already been a long list of commented blacklisted modules.  if you are absolutely certain (sometimes everyone misses very simple things), then also add the above list to the following file:
/etc/modprobe.d/blacklist.local

this file may not exist (i'm not sure, i don't have my hardy machine working correctly at the moment).  if it does not exist, create it.

you may also try this -
on boot, hit the <esc> key to enter the grub menu, and edit your kernel boot line.  add the following option to the end of your current kernel:
```
ssb.blacklist=yes
```
this may prevent your machine from booting properly, but it's worth a try because a reboot will reset the kernel to its former arangement.

if neither of these two solutions work for you, then your only option left at this point is to file a bug report against modprobe because the blacklist is not preventing the ssb module from loading.

Thanks.

I am absolutely capable of missing something simple or doing something boneheaded.  Don't be afraid to suggest anything.  But, yes that is exactly what my blacklist file contains (among the many other modules blacklisted by default).  I'm at work now.  I can ssh into my laptop and try some things (if I don't spend too much time on it).  

I don't believe (can't confirm right now) that ssb is not being loaded on reboot.  I don't think it loaded last night before executing the modprobe steps in the link posted by santhony, which specifically says to load ssb after ndiswrapper.  What I'm saying is that I don't think it loaded it behind my back or automatically. I've tried not loading ssb.  Which keeps "lshw -C network" from showing that ssb owns my wifi card.  But, it doesn't do anything to help ndiswrapper.

The blacklist file is not going to prevent ssb from being manually loaded after boot or loaded by another module that may require it if you load that module manually.  It just prevents it from loading during boot.  I think my problem is coming earlier.  I think that even though ssb is not loaded, it is somehow tied to the card or ndiswrapper.  The reason why I think this is because when I do an ndiswrapper -l, I get the "bcmwl5 loaded" followed by "using alternate driver ssb" message.  I can't quote it exactly now because I can't get on my laptop because I just rebooted my laptop and I forgot that I don't have eth0 coming up automatically -- see I did something boneheaded :-).  So, I am out of luck until tonight.

I rebooting so I could confirm which modules were loaded on reboot.  Oh, well.

---

### Post by backdoc on 2008-05-29
> **dmizer said:**
> something's really wrong here.  you've blacklisted all of the native modules, yet they're still loading.

either your blacklist is not working (unlikely), or something else is going on here.  in [post 19](http://ubuntuforums.org/showpost.php?p=4990044&postcount=19), you mentioned that you have all of the following modules blacklisted:

blacklist bcm43xx
blacklist b43
blacklist b43-pci-bridge
blacklist b43legacy
blacklist b44
blacklist ssb

this means that all of the above lines are in /etc/modprobe.d/blacklist.  this should not have been a new file, there should have already been a long list of commented blacklisted modules.  if you are absolutely certain (sometimes everyone misses very simple things), then also add the above list to the following file:
/etc/modprobe.d/blacklist.local

this file may not exist (i'm not sure, i don't have my hardy machine working correctly at the moment).  if it does not exist, create it.

you may also try this -
on boot, hit the <esc> key to enter the grub menu, and edit your kernel boot line.  add the following option to the end of your current kernel:
```
ssb.blacklist=yes
```
this may prevent your machine from booting properly, but it's worth a try because a reboot will reset the kernel to its former arangement.

if neither of these two solutions work for you, then your only option left at this point is to file a bug report against modprobe because the blacklist is not preventing the ssb module from loading.

I'm sitting her reading [[COLOR="Navy"]**this thread**[/COLOR]]("http://forums.debian.net/viewtopic.php?p=147609&sid=abf8c5a170fa9e07c58c6aae00e904dd").  Evidently, b44 requires ssb.  And, since my wired card doesn't use b44, I don't need ssb at all.  And, in [[COLOR="navy"]**this particular post**[/COLOR]]("http://forums.debian.net/viewtopic.php?p=146967&sid=046578a02412fb0fee81abe2cdf64967#146967"), he ditched the 2.6.24 kernel for the 2.6.25 kernel.  I think if I did that too, I would be OK.  Another reason that I think the problem is in the kernel, which I forgot to mention a minute ago is the fact that if I reboot to my old kernel, I can get my wireless to work, which I have mentioned.

---

### Post by backdoc on 2008-05-29
> **santhony said:**
> Backdoc... Also.. what version of the bcm306 do you have?


run this command lspci

My output shows an entry like this:

00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

Then next, before you do anything run the lshw command and see if it is using ssb or ndiswrapper...

In that last link I sent you.. I says that ubuntu can be loading the ssb overtop of your ndiswrapper, even tho you have installed ndis properly..  

At the bottom of the instructions, it tells you have to remove the bcm4306 ssb drivers from loading...

Anyways.. tell me what you get from running those two commands above..  

thanks

What hard wired card do you have?  Please, do "lspci |grep -i broadcom" and let me see the results.

---

### Post by backdoc on 2008-05-29
> **jw5801 said:**
> Just a query, but you do only have one driver installed via ndiswrapper -i for each test yes? Having more than one will probably break things.
Yes.  I always only have one driver installed.
> **jw5801 said:**
> 
As far as ssb goes, if it's blacklisted and still being loaded for some reason, it's most probably being loaded in the initramfs, not entirely sure why however. For my setup it was being loaded along with b44 in order to bring up my wired interface for a network boot, I stopped that by changing the interface in /etc/initramfs-tools/initramfs.conf to lo rather than eth0. That shouldn't make a difference though, given you don't have a bcm44 wired card. Might want to experiment a bit with it if you want to stop ssb being loaded to make it easier to load ndiswrapper correctly.

That's mostly a non-issue though, since the main problem is getting ndiswrapper working properly before we worry about graceful loading. As for that I think it's just a matter of finding a happy driver and making sure there aren't any others floating around to interfere. If it were an issue with ndiwrapper being compiled against the wrong kernel headers then you'd get nasty dmesg errors on attempting to load it, since it's loading fine now I don't think that's the case.

I've tried so many things over so many different sittings, I don't recall all of the details.  But, I'm starting to think ssb is not being loaded behind my back.  I'm thinking the only time it loads is when I follow the suggestions in one of the howto's, which specifically say to load it.  I'm also beginning to think that those howto's are for people who have the BCM4401-B0 100Base-TX (rev 02) card.  So, they need b44, which needs ssb.  I don't have that card.  My card is the BCM5705M Gigabit Ethernet (rev 01).  So, I never need to load b44 or ssb at all.  But, for some reason, and this is the part I can't figure out, ndiswrapper is getting associated with the ssb module before either one of those modules is loaded.  I am thinking that because when I check "ndiswrapper -l", it reports something about ssb and being an alternate driver.

---

### Post by santhony on 2008-05-29
Here's my Hardware Info:
  *-network:0
             description: Wireless interface
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: wlan0
             version: 02
             serial: 00:90:4b:43:bf:ad
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,07/ ip=192.168.1.100 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g



*-network:1
             description: Ethernet interface
             product: DP83815 (MacPhyter) Ethernet Controller
             vendor: National Semiconductor Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 00
             serial: 00:0b:cd:7a:54:7c
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=natsemi driverversion=2.1 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes

---

### Post by backdoc on 2008-05-29
> **santhony said:**
> Here's my Hardware Info:
  *-network:0
             description: Wireless interface
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: wlan0
             version: 02
             serial: 00:90:4b:43:bf:ad
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,07/ ip=192.168.1.100 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g



*-network:1
             description: Ethernet interface
             product: DP83815 (MacPhyter) Ethernet Controller
             vendor: National Semiconductor Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 00
             serial: 00:0b:cd:7a:54:7c
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=natsemi driverversion=2.1 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes

Hmmm.  I see your wifi card is getting loaded first.  And, your hardwired card is not a broadcom.  Do you need ssb for your natsemi driver?  I wonder if order is playing a role here.

---

### Post by dmizer on 2008-05-29
i looked through this entire thread very carefully, and didn't see this posted.  please see this link: [http://ubuntuforums.org/showthread.php?p=1169984](http://ubuntuforums.org/showthread.php?p=1169984)

a page or two back, i started to realize that your card is being labeled as eth1.  the link above has a post which addresses this potential show stopper.  look for the solution under "problem 2" toward the end of the first post.

the thread is current and active.  if you are unsuccessful after following the first post, then go to the very last page in the thread and start working backwards for possible solutions.  your card DOES work in hardy according to that thread.

---

### Post by backdoc on 2008-05-29
> **dmizer said:**
> i looked through this entire thread very carefully, and didn't see this posted.  
Bless your heart ;).
> **dmizer said:**
> 
please see this link: [http://ubuntuforums.org/showthread.php?p=1169984](http://ubuntuforums.org/showthread.php?p=1169984)

a page or two back, i started to realize that your card is being labeled as eth1.  the link above has a post which addresses this potential show stopper.  look for the solution under "problem 2" toward the end of the first post.

the thread is current and active.  if you are unsuccessful after following the first post, then go to the very last page in the thread and start working backwards for possible solutions.  your card DOES work in hardy according to that thread.

Yeah.  I was starting to think that either being the second card loaded might or the accompanying hard wired card might have something to do with why my results being different that santhony's, and many others.  Look at [[COLOR="SandyBrown"]**my post**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5070282&postcount=87"), just before yours.  I will look at the link you posted tonight.

---

### Post by backdoc on 2008-05-30
I learned a couple of things last night.  First, when I do a reboot, ssb is loaded, even though it is in the blacklist.  Second, the step 2 in the [**[COLOR="Orange"]link dmizer sent[/COLOR]**]("http://ubuntuforums.org/showthread.php?p=1169984") does not help.  

For reference, here's step 2 from the link:
```
sudo gedit /etc/modeprobe.d/ndiswrapper
sudo gedit /etc/network/interfaces
sudo gedit /etc/iftab
```

I followed it as good as I could by replacing the eth1 with wlan0 in the interfaces file, but ndiswrapper did not have a reference to eth1 and I did not have an iftab file.

I didn't have time to go from the end of the thread and work backwards, as was suggested.  But, I will try that as soon as I can.  I'll knock out a couple of the smaller tasks first, such as dmizer's suggestion to:
```
ssb.blacklist=yes
```

I also rebooted back into my old kernel.  ssb does not load automatically.  Since all of the same files (like blacklist and modules) exist regardless of which kernel I'm booting into, this confuses me.  BTW, I did an "ndiswrapper -l" while running the older kernel.  It still had the ssb reference.  So, I unloaded it with "ndiswrapper -r".  Then, I reloaded my original drivers (the ones that worked with this kernel before the upgrade).  This time it referenced bcm43xxx as an alternate driver.  I noticed the b43xxx-fwcutter config files were still installed.  So, I purged them.  I never got wireless working again with that kernel before I had to stop working on it.

The next chance I get to work on it, I'm going to get wireless working with the old kernel again.  That seems to be a solid place to start.  Then, after trying the "ssb.blacklist=yes" suggestion, I'm going to take a hiatus from trying all of the easier things mentioned and look into rebuilding my kernel without all of the junk I don't need.

There have been several suggestions over the last day or so.  And, I've tried to try them all.  But, I'm sure I may have missed something.  I do not intentionally mean to ignore any of them.  My apologies, if I miss one.

---

### Post by backdoc on 2008-06-02
I am posting back to let everyone know that I have to throw in the towel on this one, at least for now.

I blew a backup image back down to my laptop.  So, I'm back at Gutsy.  The odd thing is, my wifi isn't working.  I'm sure it was working when I took that image.  

Anyway, I sincerely appreciate everyone's help and suggestions.  But, I just don't have time to beat my head against the wall with it anymore.  If I decide to do anything different, I'll try and post back.

---

### Post by dmizer on 2008-06-02
> **backdoc said:**
> I blew a backup image back down to my laptop.  So, I'm back at Gutsy.  The odd thing is, my wifi isn't working.  I'm sure it was working when I took that image.  

perhaps the card's gone bad?

---

### Post by backdoc on 2008-06-04
I'm not tagging this thread as [SOLVED] because I'm back in Gutsy.  But, if I had tried what I just tried, it might have worked in Hardy, too.  Never the less, I do have wireless working again.  dmizer, you were half right with your last post regarding my wireless card having gone bad.  It wasn't bad, it was turned off.  I actually thought about that many days ago.  And, I tried turning it back on.  It didn't work, though.  Here's why it was hard to figure out and how I finally did figured it out.

To turn the wireless card Off and On, you have to use the function keys on the keyboard (not the F1-F12 keys, but the dual function keys on the regular letter keys).  Way back in this thread, I don't know if I posted it or not but, I tried using the function keys to turn it On.  There's no visual indication as to whether the card is powered Off or On.  So, I couldn't tell if I was turning it from Off to On or On to Off.  So, I tried unloading and reloading the modules and drivers both ways.  I figured I would cover it either way.  I wondered if my function keys were even having an effect.  But, I figured that if I tried it both ways, I should be OK.  And, if the keys weren't working, I couldn't have accidentally turned it Off anyways.  And, if they were working, I would have got it back on.  Eventually, I discounted that as a potential problem.

Fast forward to today....

After rolling back to an image of my Gutsy install, and then doing most all of the things that we talked about in in this thread.  I still couldn't get it to work.  It looked like everything was loading correctly.  But, I just couldn't get a signal, which was the same situation as I mentioned before.  I was beginning to think the wireless side of my router was not working.  So, I thought, I would reboot into Windows and see if I could get wireless working in Windows.  Well.....  I couldn't.  I couldn't even see any wireless networks.  If I hadn't already let the cat out of the bag, you'd be thinking, "Aha!  It was his router."  Nope.  My router was working.  Then, you'd be thinking, "Aha! His card *was* dead."  Nope.  It was just turned off.  I hit the function key combo to toggle my wireless card to On and refreshed the available networks.  I could see two of them.  So, I knew I had the card turned back on.  I quickly rebooted back into Linux.  And, Bam!.  My wireless was working.

So, here's some food for thought.  Even restoring an image didn't reset my card to the On position.  That means the setting is probably stored in the bios, not in the user space as I would have guessed.  Not all function key combos do not work on Ubuntu out of the box.  Some, like volume, do work.  But, the one that turns my card On and Off does not.  Don't make the assumption that I did.  Is there a way in Ubuntu to verify if the card has power?  What if I didn't have Windows installed to turn my card back on, does Ubuntu have a way?

The moral of the story for all of you kids out there:  Just because you can see your card with lspci and load a driver for it, that doesn't mean that it is turned on (something else I wouldn't have thought to be true).  If you are not using a card that has a light on it, make Damn sure you have your card powered on before you pull your last two hairs out trying everything under the sun (like me).  How do you do that?  I don't know.  I suspect there is a way.  But, I haven't looked yet.  As soon as I got wireless back up and running, I updated this thread.

I may get brave again and try upgrading to Hardy again to see if I can't get wireless working on it.  But, I'm too beat up to take on that challenge right now.  And, as stated, I just don't have time for at least a month.  When or if I do, I'll come back and mark this thread officially [SOLVED].

Thanks again for all you wonderful people who stuck with me, reading tortuous convoluted threads and offering suggestions.

---

### Post by dmizer on 2008-06-04
wow ... how painful was that.  sorry.

glad you're at least online now though.

---

### Post by jw5801 on 2008-06-04
I have a shiny LED that tells me whether the card has power or not. I'm willing to bet there's probably a setting somewhere in the bios to toggle it. My hotkey will work in Ubuntu, but only if the card is active when I boot. Otherwise it won't work at all until I've reset it in the bios.

---

### Post by backdoc on 2008-06-04
> **dmizer said:**
> wow ... how painful was that.  sorry.

glad you're at least online now though.

Yeah... And, it should be the "A" number one thing that all wireless HOWTO's check.  Ubuntu should detect if you are attempting to use a wireless device that is powered off and warn you about it.

Hopefully someone else will benefit from this.

---

### Post by Ayuthia on 2008-06-05
> **backdoc said:**
> Is there a way in Ubuntu to verify if the card has power?  What if I didn't have Windows installed to turn my card back on, does Ubuntu have a way?I don't know if I have found it or not, but it seems to work with my card.  Try the following:
```
cat /sys/class/rfkill/rfkill*/state
```
It will return a 1 if it is on and a 0 if it is off.  I am not for sure about how it works yet, but I do know that it is linked to my card.

EDIT: I just realized that it is pointing to the ssb portion so you might not be able to find it in Gutsy since you are using ndiswrapper...

---

