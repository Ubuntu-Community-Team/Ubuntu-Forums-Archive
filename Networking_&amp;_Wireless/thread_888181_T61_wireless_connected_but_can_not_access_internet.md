---
title: "T61 wireless connected but can not access internet"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by lnthai2002 on 2008-08-12
Hi guys,
This is very strange, I have connected to the wireless network at my office (i see the bar on Network Manager), I can access the internet for a while bu then randomly, i can not access the internet anymore although network manager still show that I am connected to the network. I am sure that the network is not down because my friend sitting next to me has no problem on his laptop. I tried to restart networking , stop iptable but nothing changed. I have to reboot to fix the problem. It happen at random and today it happened a few times, it's quite annoying. If anyone has experienced the problem and found the fix, please share 
Thank you
Thai

---

### Post by pytheas22 on 2008-08-12
It sounds like your wireless driver is crashing, which does happen.  The next time it crashes, please immediately open a terminal and post the output of these commands:
```

dmesg | tail
lshw -C Network
iwconfig
iwlist scan
```

That should help figure out what's going on and lead to a solution.

---

### Post by lnthai2002 on 2008-08-16
Thank you for your debug instructions, here is the info after i get the crash
```

dmesg | tail

[ 1332.776649] wlan0: CTS protection disabled (BSSID=00:11:95:73:24:f6)
[ 1345.298755] wlan0: CTS protection enabled (BSSID=00:11:95:73:24:f6)
[ 1345.584787] wlan0: CTS protection disabled (BSSID=00:11:95:73:24:f6)
[ 1556.405227] wlan0: CTS protection enabled (BSSID=00:11:95:73:24:f6)
[ 1557.713930] wlan0: CTS protection disabled (BSSID=00:11:95:73:24:f6)
[ 1866.323809] wlan0: CTS protection enabled (BSSID=00:11:95:73:24:f6)
[ 1866.850943] wlan0: CTS protection disabled (BSSID=00:11:95:73:24:f6)
[ 2117.141734] wlan0: CTS protection enabled (BSSID=00:11:95:73:24:f6)
[ 2117.841194] wlan0: CTS protection disabled (BSSID=00:11:95:73:24:f6)
[ 2177.559024] iwl4965: Microcode SW error detected.  Restarting 0x2000000.
------------------------------
lshw -C Network
  *-network
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1c:25:74:47:2a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-0 latency=0 module=e1000 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:27:78:d9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.64.115 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
------------------------------
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Cas"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:95:73:24:F6   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=79/100  Signal level=-55 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

------------------------------
iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:11:95:73:24:F6
                    ESSID:"Cas"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=74/100  Signal level=-60 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000002a0fab36d2


```
Is there anything I can do about the disconnect thing? BTW, I notice that when i run a media player, there is more chance to crash. I guess it has something to do with my sound driver. I am not quite familiar with the driver come with ubuntu since when i used gentoo, I use only alsa but ubuntu give me many choices: AD198x Digital, AD198x Analog, ALSA, OSS, Pulse Audio sound server. All of them can produce sound but the AD198x digital so I choose Alsa for sound event, AD198x analog for audio/video. I wonder if there is a direct cause to wireless driver crash
Hope you can help
Thai

---

### Post by pytheas22 on 2008-08-16
I think you're affected by this [bug]("https://bugs.launchpad.net/linux/+bug/200509").  Unfortunately, even though some of the developers seem to think that it was fixed a long time ago, people are still reporting the issue this month.

The first thing to do is to update the system.  Go to System>Administration>Software Sources and click on the "Updates" tab.  Make sure the box for "Unsupported updates (hardy-backports)" is checked (see the screenshot).  Then close that window and reload the sources list when prompted.

After that, apply all of the updates, reboot and see if it helps.  If the problem persists, let me know and I can give you instructions for using ndiswrapper with your card instead of the iwl4965 driver.

---

### Post by lnthai2002 on 2008-08-19
Thank you for your help pytheas, i read the bug report and noted that I have experienced the vpn problem too. I guess it's random. I'm doing remote development which requires sycn with cvs from the headquarter network but i wouldnt be able to keep vpn connection alive for more than 3 mins, so after a few times reconnect, disconnect my wireless if down. I'm trying your suggestion, i'll let you know if the problem happen again.
Cheers
Thai
BTW, i wonder if there is any difference between using ndiswrapper with windows driver and native linux driver. Since I have once tried it on gentoo on my "unbrand" wireless PC card and it work great just the config is a bit anoying

---

### Post by pytheas22 on 2008-08-20
> BTW, i wonder if there is any difference between using ndiswrapper with windows driver and native linux driver. Since I have once tried it on gentoo on my "unbrand" wireless PC card and it work great just the config is a bit anoying

Yes, ndiswrapper lets you drive your card using the Windows driver, instead of using iwl4965, the native Linux driver.  I found this [tutorial]("http://ubuntuforums.org/showthread.php?t=471794") that tells you how to use ndiswrapper for your card, if you want to try that.

In order for ndiswrapper to work, you need to add the iwl4965 module to the blacklist:
```

sudo -s
echo 'blacklist iwl4965' >> /etc/modprobe.d/blacklist
```

The tutorial doesn't mention this because it was written for an older version of Ubuntu.  Otherwise the instructions in the tutorial should be correct.  And you can install ndiswrapper easily with:
```

sudo apt-get install ndiswrapper* ndisgtk
```

(you don't need to use Automatix like the tutorial says).

---

### Post by lnthai2002 on 2008-08-20
> **pytheas22 said:**
> Yes, ndiswrapper lets you drive your card using the Windows driver, instead of using iwl4965, the native Linux driver.  I found this [tutorial]("http://ubuntuforums.org/showthread.php?t=471794") that tells you how to use ndiswrapper for your card, if you want to try that.


Would it be slower than iwl4965 or have any performance impact? BTW, I have ubuntu 64 and as far as i know, intel/lenovo does not provide 64bit driver for this card on XP-64b (not sure if they have it on vista 64). Can I still use ndiswrapper with the windows 32b driver?

It's been a day since I have tried your suggestion with backports updates and it has not crash yet but pidgin crash every single time someone PM me, is there anyway to fix this?
Thanks 4 your help
Thai

---

### Post by pytheas22 on 2008-08-20
> Would it be slower than iwl4965 or have any performance impact?

No, there's no performance impact.  It should work as well under ndiswrapper as it would on Windows.  ndiswrapper doesn't support monitor mode or packet injection, but if you just need a normal connection, it will work fine, barring any weird problems.

> BTW, I have ubuntu 64 and as far as i know, intel/lenovo does not provide 64bit driver for this card on XP-64b (not sure if they have it on vista 64). Can I still use ndiswrapper with the windows 32b driver?

Good question.  No, you can't use ndiswrapper on 64-bit Linux with a 32-bit Windows driver.  Look around though--Lenovo is supposed to be high-end; I'd be very surprised if it doesn't support 64-bit Vista, meaning that either it or Intel would have to have a 64-bit driver on its site.
> 
It's been a day since I have tried your suggestion with backports updates and it has not crash yet but pidgin crash every single time someone PM me, is there anyway to fix this?

If the Internet itself is working, then I'd blame pidgin for this problem before the iwl4965 driver (but I wouldn't rule iwl4965 out).  You could try a different instant-messaging client, like [Kopete]("http://kopete.kde.org/"), to see if you have the same problems.  You can install Kopete with:
```

sudo apt-get install kopete
```

If it happens on Kopete as well as pidgin, then it most likely is the iwl4965 driver that's at fault, and you should check the output of:
```

dmesg | grep iwl
```

to see if you can tell why.

---

### Post by lnthai2002 on 2008-08-27
pidgin from backport is buggy, i rolled back to hardy update and the problem is gone. However, this morning, i have  a wireless  crash again. I guess they didnt completely fix it.

---

### Post by lnthai2002 on 2008-08-29
Hi Pytheas,
After a few crash I have last week, I finally decided to give ndiswrapper a try. I installed it as the instruction in the tutorial U give me. However, after the reboot, my Network Manager does not show Wireless Network anymore. As far as i remeber, I had to use wpa-suplicant with ndiswrapper and wpa-sup uses a config file that has the wireless network spec declared in it to know how to connect to a given network, it can not browse the network as Network  Manager. Is there anyway I can use Network Manager with the ndiswrapper?
Thanks in advance
Thai

---

### Post by pytheas22 on 2008-08-30
Network Manager should work with ndiswrapper with no problems.  I suspect that for some reason ndiswrapper is not working correctly on your system, either because you chose a bad Windows driver, the ndiswrapper module is not inserted or some other problem.  Please post the output of these commands so that we can figure it out:
```

lshw -C Network
dmesg | grep -e ndis -e wlan
ndiswrapper -l
```

---

### Post by lnthai2002 on 2008-09-01
Thank you pytheas for your suggestion,
Here is the output from the command you suggested:
```

sudo lshw -C Network 
[sudo] password for administrator:  
  *-network                
       description: Ethernet interface 
       product: 82566MM Gigabit Network Connection 
       vendor: Intel Corporation 
       physical id: 19 
       bus info: pci@0000:00:19.0 
       logical name: eth0 
       version: 03 
       serial: 00:1c:25:74:47:2a 
       capacity: 1GB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-0 latency=0 link=no module=e1000 multicast=yes port=twisted pair 
  *-network UNCLAIMED 
       description: Network controller 
       product: PRO/Wireless 4965 AG or AGN Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 61 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0



 dmesg | grep -e ndis -e wlan 
[   33.973481] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
[   34.562660] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck' 
[   34.562929] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5x64' 
[   34.564574] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5x64; check system log for messages from 'loadndisdriver' 
[   34.581272] usbcore: registered new interface driver ndiswrapper

	
 ndiswrapper -l 
netw5x64 : driver installed 
	device (8086:4230) present (alternate driver: iwl4965)



```
The driver was downloaded from intel website [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2753&DwnldID=16617&strOSs=109&OSFullName=Windows*%20XP%20Professional%20x64%20Edition&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2753&DwnldID=16617&strOSs=109&OSFullName=Windows*%20XP%20Professional%20x64%20Edition&lang=eng). There are a 32bits  and a 64bits version. I tried the 32 bits version(netw5x32) with ndisgtk but it say "invalid driver", so i tried the 64bits (netw5x64) but although ndisgtk says "device present" Network Manager does not show any option to enable wireless. From the error message, I guess I have to copy the driver into a place that ndiswrapper can access.
I hope you have give a hint
Thanks again
Thai

---

### Post by pytheas22 on 2008-09-01
Are you using 64-bit Linux?  If so, you need to use the 64-bit Windows driver with ndiswrapper.  Otherwise, you should use the 32-bit drivers.  Please let me know and I'll find drivers that should work.  It seems that the 64-bit drivers that you loaded have some weird problem; that's why they're not bringing the interface up.

---

### Post by lnthai2002 on 2008-09-01
Thanks for your quick reply pytheas
Yes, I am using 64bit ubuntu on T61 with intel 4965AGN. The driver i found on intel website is for windows xp pro 64bits. I think intel use the same driver for vista 64 and xp 64 and that's what I have. 
Please let me know if you know any other driver that work 
Thank you for helping me out in labor day :D
Thai

---

### Post by pytheas22 on 2008-09-01
hmmm, I did a bit of research and it seems like the Windows driver that you loaded should be the right one, but ndiswrapper gives this weird message (according to the dmesg output that you posted above):
```

unknown symbol: ntoskrnl.exe
```

You might want to try compiling the latest version of ndiswrapper from source.  It's not guaranteed to solve the problem, but it might.  To compile from source, run:
```

sudo -s
apt-get remove --purge ndiswrapper*
apt-get install build-essential
wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005&big_mirror=0
tar -xzvf ndiswrapper*
cd ndiswrapper*
make
make install
```

After this, you will need to reinstall the 64-bit Intel driver into ndiswrapper.  The GUI utility, ndisgtk, will not be available, so you will need to install using the command-line (don't install ndisgtk or it will revert you back to the older version of ndiswrapper).  To install a Windows .inf file from the command line, you use a command like this:
```

sudo ndiswrapper -i /path/to/.inf/file.inf
```

So if you have the netw5x64.inf file to your desktop (make sure the .sys and .cat files are also there), you would run:
```

sudo ndiswrapper -i ~/Desktop/netw5x64.inf
```

You could also try installing the 64-bit [Vista driver]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2753&DwnldID=16618&strOSs=162&OSFullName=Windows%20Vista*%20Ultimate,%2064-bit%20version&lang=eng").  It has a slightly different name (netw5*v*64.inf), so it may or may not be different from the XP one.

Please let me know if this helps.  In the meantime I'll do some research and see if I can find anyone who has successfully used ndiswrapper with Intel 4965 on 64-bit Linux.

---

### Post by lnthai2002 on 2008-09-01
Hi pytheas,
I recompiled from source as you suggested, using the same xp 64 driver and Network Manager still show nothing. One thing i notice, when I did
```

ndiswrapper -m

```
I see a repeated message:
"module configuration already contains alias directive"
i gonna try vista driver now

---

### Post by lnthai2002 on 2008-09-01
hi pytheas,
I have no luck with vista 64 driver either. This is the output from dmesg
```

dmesg | grep -e ndis -e wlan
[   20.694410] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   21.046735] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[   21.046755] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   21.046762] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   21.046768] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   21.046772] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   21.046776] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   21.046781] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   21.046785] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   21.046789] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   21.046794] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   21.046798] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   21.046803] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   21.046812] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   21.046816] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   21.046820] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   21.046838] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   21.046844] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   21.046848] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   21.046852] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCopyFromNetBufferToNetBuffer'
[   21.046856] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   21.046861] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   21.046865] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   21.046869] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[   21.046873] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   21.046877] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   21.046881] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   21.046886] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   21.046890] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   21.046894] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   21.046898] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   21.046902] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[   21.046906] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   21.046910] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   21.046915] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   21.046919] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   21.046923] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   21.046928] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   21.046934] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5v64'
[   21.047419] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5v64; check system log for messages from 'loadndisdriver'
[   21.047478] usbcore: registered new interface driver ndiswrapper

```
Bothe xp and vista drivers cause ndis error in NDIS.SYS, i wonder if we can do anything about that
Thai

---

### Post by pytheas22 on 2008-09-01
I did some searching and found [this post]("http://ubuntuforums.org/showthread.php?t=447382"), which seems to address the problem you're having--namely, that ndiswrapper doesn't want to work with 4965 on 64-bit Linux.  There's a fix there that involves editing the netw5x64.inf file a little bit.

Please remove the drivers that you currently have installed (use *ndiswrapper -r netw5v64* or *ndiswrapper -r netw5x64* to do this), download the Windows XP .inf file and edit it as per the instructions in that thread.  Then reboot and look at the output from dmesg again.  Do you still get the strange errors?

---

### Post by cmcginty on 2008-10-28
Hey, I'm looking for some help with the NDISwrapper for 5300AGN wireless device. I'm running 64-bit Hardy, so this looks like the best way to get this working.

I'm using the XP-64bit drivers like above.

I followed all the steps above, and the ndisgtk app says the hardware was detected correctly, but the kernel logs are showing a minor problem.

```
Oct 28 17:16:37 casey kernel: [ 3170.949771] usbcore: deregistering interface driver ndiswrapper
Oct 28 17:16:37 casey kernel: [ 3170.949987] ndiswrapper (ntoskernel_exit:2708): object ffff8100a80b4230(2) was not freed, freeing it now
Oct 28 17:16:37 casey kernel: [ 3170.957286] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Oct 28 17:16:37 casey kernel: [ 3170.969902] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
Oct 28 17:16:37 casey kernel: [ 3170.969983] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5x64'
Oct 28 17:16:37 casey kernel: [ 3170.970555] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5x64; check system log for messages from 'loadndisdriver'
Oct 28 17:16:37 casey kernel: [ 3170.973127] usbcore: registered new interface driver ndiswrapper
```

Any advice on how to resolve the missing symbol?

---

### Post by pytheas22 on 2008-10-28
cmcginty: you don't need to use ndiswrapper for the Intel 5300 chipset, as it has a good native Linux driver.  Also I'm not sure if ndiswrapper will even work with it on 64-bit.

Please take a look at [these instructions]("http://ubuntuforums.org/showpost.php?p=5710211&postcount=4"); they should get your card running on Ubuntu 8.04. 

Alternatively, if you upgrade to Ubuntu 8.10, your card should have out-of-the-box support.  This might be the easiest option, unless you have a reason to want to stick with Ubuntu 8.04.

Let me know if you need more help.

---

### Post by cmcginty on 2008-10-29
pytheas22, thanks for the reply. I have tried the compat-wireless method, and was able to get the wireless card detected. The problem is that I can not associate to any access point with the driver. Eventually the connection times out. I even tried a few access points that had no security turned on.

The other downside is that the driver made my system unstable. For example, unloading the module with always hardlock the system.

I guess I will wait for the official Intrepid release, however I am still not sure what the state of the e1000e driver bug is on Intrepid. I need that driver above the wireless.

---

### Post by pytheas22 on 2008-10-29
Sorry that compiling the driver didn't help.

The e1000e issue has been resolved, and the official release of Intrepid is tomorrow, so I think that your best bet is to either wait till tomorrow and install the stable release of Intrepid, or install the [beta]("http://www.ubuntu.com/testing/intrepid/beta") today (it would automatically be updated via Ubuntu updates to the stable version).

If things still don't work on Intrepid, let me know.

---

