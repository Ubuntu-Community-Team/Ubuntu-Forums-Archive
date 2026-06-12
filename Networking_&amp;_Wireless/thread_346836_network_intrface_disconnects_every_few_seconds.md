---
title: "network intrface disconnects every few seconds"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by manokaran on 2007-01-26
Hi,

Have been using Ubuntu for more than a year now. Am on Edgy now. I have a strange network problem. Every few seconds the network interface goes down and up again all by itself and because of this the internet connection is very slow. I have tried disabling ipv6 (by editing the /etc/modprobe.d/aliases file and also having a blacklist-ipv6 file) as explained in other forum posts but to no avail. 

Till 31st Dec, 2006 our DSL connections were 384Kbps and I used to get around 240Kbps average. From 1st Jan, 2007 the ISP increased the speed to 2Mbps and thats when I started noticing this problem. I still only get around 200-240Kbps! Strangely, if I boot using the live CD then there is absolutely no problem. I get around 600-1500 Kbps. And the network interface never goes down. 

In fact I was on 6.06 earlier. To upgrade I tried downloading 6.10 using prozilla - the download accelerator. The speed was around 150-250Kbps. Then I rebooted my system using the Ubuntu 5.04 live CD, installed prozilla and tried downloading from the same location again. This time the entire distro - 700MB was downloaded in 70mins!! The avg speed was around 1.3Mbps. Then I installed 5.04 on my machine (thinking it is faster than 6.06). *But after installation the same disconnection problem and speed problem appeared*. I have tried the 5.04. 6.06 and 6.10 live CD boots and in all of them there are no problems. Only when I install the OS to the hdd and boot from it does the problem arise.

I'm in Chennai, India. The ISP is BSNL and I use a Huawei SmartAX MT882 dsl router/modem. Not the best of DSL h/w but it works without problems when booting from the live CD!! Also there are no problems when connecting to the net from WinXP (have a multi boot system).

I posted about this in the local linux user group and a couple of other users too reported similar problems. The situation is some what unfortunate because BSNL is quite a popular ISP here and many people are trying out Ubuntu now. They all find the live CD fast and install the OS. But after that they observe the slowness and might be thinking 'linux is slow'  and (horrors) WinXP is better!!!!! This is an unacceptable situation! After all, the live CD boot just works great.

Am absolutely confounded now. Looks like the kernel image on the live cd is different from the one installed on the HDD. I diffed the live cd kernel config and the hdd image and found very few differences - nothing related to net anyway. The diff out put is given below.

Could some one help me solve this? If anyone can suggest tests/experimentsI can do it and post the results here.

Thanks,
mano

diff config-livecd /boot/config-2.6.17-10-generic gives:

4c4
< # Fri Oct 13 16:13:36 2006
---
> # Tue Dec  5 21:20:15 2006
28c28
< CONFIG_VERSION_SIGNATURE="Ubuntu 2.6.17-10.33-generic"
---
> CONFIG_VERSION_SIGNATURE="Ubuntu 2.6.17-10.34-generic"
1293a1294
> CONFIG_PATA_MARVELL=m
1337c1338,1339
< # CONFIG_SCSI_QLA_FC is not set
---
> CONFIG_SCSI_QLA_FC=m
> # CONFIG_SCSI_QLA2XXX_EMBEDDED_FIRMWARE is not set

---

### Post by jskasia on 2007-01-26
I seem to find very similar problem but a bit different. By eth0 disconnect every time transfer rate go higher than 100 k bps.
But when I switch to wireless, it 's not happen.

---

### Post by manokaran on 2007-01-26
I think I have stumbled on a (inelegant) solution for this!

No need to comment out ipv6 in /etc/modprobe.d/aliases nor include a blacklist-ipv6 file. Please note I have static ip address for the interface. I have not tested but it should work for DHCP served interfaces too.

#Shutdown the offending interface
sudo ifconfig eth1 down (it was eth1 in my case - yours could be different)

#Bring it back up again
sudo ifconfig eth1 up

#That shutting down would've removed the default gateway entry in your routing table. So add it again:
sudo route add default gw 192.168.1.1 eth1

Thats it. Try this and if it works, put this in your rc.local file so that it gets done automatically every time you boot your box. Now you should be cruising comfortably in the infobahn instead of sputtering to the roadside every few seconds :-)

I think the advice of turning ipv6 seemed to work initially because it required a reload of the interfaces. This excited many (including yours truly) and most shot of immediate 'WOW' mails acknowledging the speed increase. Only to be disappointed after a reboot.

Now I have removed the suggested modifications to the aliases file, removed the blacklist-ipv6 file and also set the firefox network.dns.disableIPv6 variable to flase (the original value). 

The live CD boot worked perhaps because the network restarted after an initial boot!!! Don't know. 

Perhaps the distro maintainers should take note and fix this aberration.

regards,
mano

---

### Post by zubrug on 2007-01-26
Try this as you may have more than one running,
sudo poff -a && sudo pon dsl-provider

---

