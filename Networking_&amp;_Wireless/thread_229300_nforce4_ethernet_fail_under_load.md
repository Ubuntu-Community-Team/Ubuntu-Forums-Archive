---
title: "nforce4 ethernet fail under load"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by cutterjohn on 2006-08-04
Hello,

I've recently installed the x86-32 version of Dapper on a:
Biostar TForce4 U (latest BIOS)
AMD Athlon 64 3200+
WD 250G Caviar SATA2
Geforce 6200 in the XGP slot temporarily
2G Mushkin RAM

(no overclocking, run at stock 2G)
currently using the k7 version(latest) of the kernel + restricted modules
Linux ubuntu32 2.6.15-26-k7 #1 SMP PREEMPT Mon Jul 17 20:36:04 UTC 2006 i686 GNU/Linux
nvidia glx is loaded
forcedeth.ko is loaded/used
100M speed connected to LAN through 100M unmanaged switch

I'm using the onboard 1G ethernet controller which works fine and great for intermittent low load activities like ssh, web browsing, mail, new, etc.  However when the ehternet subsystem is stressed(multi-meg file transfers any protocol) the ethernet flakes out(i.e. fails to operate at a useful level). ALSO it will eventually hang under light usage conditions, the first occurrence of which happened to me earlier today.  Something is dreadfully wrong with forcedeth at a fairly low level.  The maintainer has speculated that it may be due to a lack of expected interrupts on some hardware(see 0.54 comments top).  His current "fix" does not work for me.


Typical symptoms:
network operations stall

attempts to ping, etc. result in either very high latency c. 15s(!) or no route to host

attempts to ping ubuntu box from another machine result in no response.

Attempted "fix":
Tried activate/de-active (network restart) howver that does not reset the controller apparenlty.  5:17p EDT using ifdown eth0 followed by an ifup eth0 resets the controller and allows "normal" net access again. (fault happened while running a synaptic update and rather than reboot I decided to try this...)

The only way that I've found to correct this problem ATM is a full system restart.

Anyone have any ideas or experienced this before?

*LATEST EDIT* (few min later)
OK, rebooted, checked synaptic and that k7 kernel was the only k7 specific(latest) kernel that I saw available, apparently intentionally with SMP support compiled in.

Rebooted, this time selecting the 386 version of the same kernel:
Linux ubuntu32 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686 GNU/Linux

Restarted the same multi-meg file xfer under ssh, and have gone through c. 300M so far with no stalls, although throughput is c. half of what I had been getting with the k7 specific kernel.  c. 930kbps v. 1.7Mbps

The k7 specific kernel is borked?

---

### Post by cutterjohn on 2006-08-04
Well, the 386 version of the kernel fared a little better, but finally petered out after xferring c. 340M.  Throughput continuously dropped throughout the transfer starting off as noted above at around 950kbps decreasing to c. 200kbps after which the xfer ended up stalling, and taking out the ethernet controller.

Ping times were not as severe as generally noted, only being around 1s after the failure.

BTW:
These transfers are between a server 160M RAM, Celeron 500(IIRC Katmai PII class slot 1), FreeBSD connected through a 100M switch, literally sitting inches apart from each other.

Other network traffic is not interfering as there is none.  

This celeron server has worked fine as a simple file/mail server, and router for years.  My notebooks continue to see it after the Ubuntu machine kills the ethernet controller on the ubuntu machine(i.e. linux is doing something funky is what this tells me).

Other random notes:  works fine under win2k, although I did have to jump through hoops to get it to see the WD as a 250G drive, but thats another story.

Oh well, since no one else apparently has any ideas, I continue searching through the mess that is these forums... (I wish that the mods would kill threads that have no useful purpose/info, e.g. [http://www.ubuntuforums.org/showthread.php?t=210629&highlight=nforce+ethernet](http://www.ubuntuforums.org/showthread.php?t=210629&highlight=nforce+ethernet) as it sure would make searching the forums a more worthwhile, if not easier experience...)

When I have checked more threads or just give up, I'll give IRC a shot then.

(On a pseudo-related note has anyone tried nVidia's own platform drivers?)

---

### Post by cutterjohn on 2006-08-04
sigh replying to myself, but I've just decided to use this thread as a placeholder for what I've tried and found.  So, here are some what appear to be related bugs but with a different chipset/controller:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37164](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37164)
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37784](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37784)
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37771](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37771)
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/45800](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/45800)
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/33230](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/33230)

Most of these have to do with Marvel controllers while the Biostar uses a Vitesse... (some of these are noted as fixed, however with my specs I exhibit the same problems, esp see 33230)

While not exactly the same, they do have some similarities if symtoms though not as severe in my particular case apparently...

searching newsgroups via google turned up something very closely related but it applies to 2.4.x series of kernels, unfortunately:
[http://groups.google.com/group/linux.kernel/browse_thread/thread/4f697bc2768a7241/fb75f57ed2f57e7f?lnk=st&q=&rnum=19&hl=en#fb75f57ed2f57e7f](http://groups.google.com/group/linux.kernel/browse_thread/thread/4f697bc2768a7241/fb75f57ed2f57e7f?lnk=st&q=&rnum=19&hl=en#fb75f57ed2f57e7f)

...and from te horses mouth...
[http://bugzilla.kernel.org/show_bug.cgi?id=5632](http://bugzilla.kernel.org/show_bug.cgi?id=5632)

...and... even closer...(need to see what changed...)
[http://bugzilla.kernel.org/show_bug.cgi?id=4552](http://bugzilla.kernel.org/show_bug.cgi?id=4552)

(BTW in the forlorn hope that someone will actually reply, does anyone know of a globally searchable ubuntu mailing list archive?  The archives that I've found don't appear to have a search option...)

---

### Post by cutterjohn on 2006-08-04
For now, I am sick of wasting time on this.  The forcedeth drivers apparently aren't in very good shape, or at least the version with the latest ubuntu kernels isn't in very good shape, so I'm going to give nvnet a shot.

Perhaps some time later on, I'll try a custome built 2.6.17(or later) kernel, but only if the forcedeth driver has been updated.

If someone else has a similar problem, you probably could get an acceptable bug report in and get some attention(apparently this very same bug has been present in a variety of forcedeth revisions since it's existed but apparently gets continuously swept under the rug), but I wouldn't bother unless you have the spare time and/or need for the forcedeth version(e.g. nvnet no longer works, and nvidia hasn't updated it...).

Bottom line: if nvidia's glx driver are shippable, so too should be their platform drivers.

*EDIT*
aaaaahhhhhh... THAT did the trick.  1.9Mbps sustained transfers. No fuss, no muss.

Search for nvnet on the wiki for the install instructions.  Note that with the latest Dapper kernels that gcc-3.4 is NOT needed as gcc-4.0 was used.

caveat:
Did all the blacklisting, etc. but forcedeth is still loaded during the initial ramdisk boot, so that probably need to be rebuilt.  I didn't as even though forcedeth shows up is lsmod as loaded, it is NOT being used.

Maybe later on, I'll try an init ramdisk rebuild...

bottomline: put forcedeth where it belongs, in the trash(for now). nVidia does way too many screwy things with their network subsystem as also recall they were trying for an integrated hardware firewall offload, which I am wondering if forcedeth may be messing with.  Using it under windows totally borked my network there(failing DNS lookups, and not amount of modifying settings, tweaking etc. would fix it, only an entire nvidia driver set uninstall, then re-install sans firewall got everything back up... theoretically, nvidia is looking into fixing it, but with the 5XX chipset it's been given VERY low priority...)

---

### Post by mmcmonster on 2006-08-06
Hi.
  I'm not sure if I have the same problem, but I just posted my problem with output of some commands on [this forum]("http://www.ubuntuforums.org/showthread.php?t=230636").

I was wondering where you were able to download the forcedeth drivers (you mention about looking for nvnet on a wiki?), and was hoping if you could tell me if that's the same problem that I am having.  Unfortunately, I am not that experienced in network troubleshooting. :-(

---

### Post by alterpinguin on 2007-08-15
first, i suspect my motherboard eth is slowly getting worse or its the router connected too -
but the description of the symptoms may help others too:

what happens very rarely: after a cold boot the onboard eth could not be setup by forcedeth module. A warm reboot did not help, but a cold boot of the computer and the router (and wait a few minutes to get it really without any power) did always help. The mainboard is a asrock-k8 upgrade-NF3 with nforce3 250GB chipset.

Look at the ifconfig output and if the RX, TX bytes counters are 0 and you know there should be some ethernet traffic on this line (from the router for example), then its like dead.

One could try to manually unload the forcedeth module, as root enter
rmmod forcedeth
load it again to init the eth
modprobe forcedeth
and if using dhcp for the ip-address
dhclient

but if the eth-device is "dead" even a warm-boot with another linux-version (knoppix from cd, or older installed suse) did not help. 

then for those using an MSI-board K8-Neo-FSR nforce3-250GB - i had to install Windows-xp on it and the onboard eth did always fail until i forced it to use only 10MB instead of the 100MB setting. But the Linux version had no problems to operate it in 100MB mode. It could be a critical combination of router and computer-hardware.

The bad thing with such onboard-eth-devices, there are most times no lights indicating activity like on the good old nics.

---

