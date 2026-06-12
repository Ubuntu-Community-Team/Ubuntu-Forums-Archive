---
title: "[SOLVED] ndiswrapper + intel pro 3945 agb wireless"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by bash4fun on 2008-08-20
Hi dear forum readers.

I've got a problem. Unfortunately the **iwl3945** module does not work as expected on my installation. 

I already removed **gnome-network-manager** and installed the **linux-backports-modules-hardy-generic** package because i read that this would solve all the problems with the LED and also will improve performance. But as I already said it doesn't work with my installation. I am able to connect to an AP using WEP via **"iwconfig wlan0..."** and the connection is beiing established and works out pretty good for a while. But as my AP is a little bit far away from my room i lose connection every now and then. But then I am not able to reconnect to my AP again. I even can't find my wireless network using **"iwlist wlan0 scan"** while standing nearby my router anymore. So I decided to install the Windows drivers using **ndiswrapper** as I had pretty good experiences with my previous installation and ndiswrapper. But also this does not work anymore.

This is what I've done so far:

1. downloaded ndiswrapper-1.53.tar.gz from SourceForge.net and compiled and installed it.

2. downloaded the appropriate Windows driver for my Intel 3945 AGB Wireless Card > 12.0.4.0_X_Drivers.zip

3. i installed the downloaded Windows driver and entered following commands

```
ndiswrapper -i NETw5x32.inf
```

```
disputer@disputerlinux:~$ ndiswrapper -l
netw5x32 : driver installed
	device (8086:4222) present (alternate driver: iwl3945)

```

seems to be installed correctly...

```
rmmod iwl3945
```

```
modprobe ndiswrapper
```

but unfortunately my wifi does not show up on **iwconfig**...

here is the debug output from dmesg...

```
disputer@disputerlinux:~$ cat /var/log/syslog
syslog       syslog.0     syslog.1.gz  syslog.2.gz  
disputer@disputerlinux:~$ cat /var/log/syslog | grep ndis
Aug 20 19:24:44 disputerlinux kernel: [ 1829.018688] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Aug 20 19:24:44 disputerlinux kernel: [ 1829.058438] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
Aug 20 19:24:44 disputerlinux kernel: [ 1829.058827] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5x32'
Aug 20 19:24:44 disputerlinux loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver netw5x32 
Aug 20 19:24:44 disputerlinux kernel: [ 1831.355819] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5x32; check system log for messages from 'loadndisdriver'
Aug 20 19:24:44 disputerlinux kernel: [ 1831.357994] usbcore: registered new interface driver ndiswrapper
```

Can anybody help me?
Thx in advance.

---

### Post by bash4fun on 2008-08-21
Ok, now I installed a previous version of the Windows XP Intel Wireless driver and my wireless network interface shows up again. But unfortunately I am not able to change any wireless settings. When I try to set ESSID via **iwconfig** no changes are made to my interface.

```
disputer@disputerlinux:~$ iwconfig wlan0 
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          RTS thr=1600 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Can anybody help me?

---

### Post by bash4fun on 2008-08-21
Here is some additional output from now:

```
disputer@disputerlinux:~$ dmesg | grep ndis
[   20.860220] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   25.121998] ndiswrapper: driver netw4x32 (Intel,03/13/2008,11.5.1.15) loaded
[   25.122402] ndiswrapper (NdisWriteErrorLogEntry:191): log: 40001B7C, count: 2, return_address: f8e0c5e2
[   25.122405] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x56524457
[   25.122407] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xe3
[   25.137096] ndiswrapper: using IRQ 16
[   25.415045] usbcore: registered new interface driver ndiswrapper

```

---

### Post by bash4fun on 2008-08-21
So for everyone who is interested, I actually solved the problem. I found out the the version of the downloaded drivers is not compatible yet with **ndiswrapper**. So when I downloaded an older version and installed it, everything works fine - performance is really good and **network-manager** even works now.

---

### Post by ShaiI769 on 2008-08-26
> **bash4fun said:**
> So for everyone who is interested, I actually solved the problem. I found out the the version of the downloaded drivers is not compatible yet with **ndiswrapper**. So when I downloaded an older version and installed it, everything works fine - performance is really good and **network-manager** even works now.

I'm having a similar problem! My card is Intel 4965AGN. How did you find out whether ndiswrapper is compatible with the driver version or not?

---

### Post by bash4fun on 2008-08-26
I found out because i correctly installed and loaded the **ndiswrapper** module but the wlan0 connection didn't show up using **ifconfig** or **iwconfig**. Therefore i tried and older version of the Windows driver as i knew it worked before for me.

---

### Post by jruden on 2008-08-28
I just tested netw5x32 and ran into the same problem. I think it was version 12 something.

May I ask where I can find an older version of the intel drivers?

---

### Post by puller on 2008-08-30
Same problem for me with that wireless card and Hardy. Ndiswrapper doesn't work with the latest intel driver.
I have found this one:
[http://support.euro.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=it&cs=itdhs1&l=it&s=dhs&~mode=popup&file=220545](http://support.euro.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=it&cs=itdhs1&l=it&s=dhs&~mode=popup&file=220545)

I hope it helps!
Bye.

---

### Post by bash4fun on 2008-08-31
Version 12.x also didn't work for me. Here is where you can find previous versions of the Windows XP  driver:

[Link: Previous Versions of Intel Wireless Drivers]("http://downloadcenter.intel.com/Filter_Results.aspx?strOSs=44&strTypes=all&ProductID=2259&OSFullName=Windows*%20XP%20Professional&lang=eng&sType=prev")

Hope this helps you out.

---

### Post by puller on 2008-08-31
Did you experienced troubles with wpa2 encryption?
With older intel drivers, my NIC is up and i can see my network (using wicd), but when i try to connect, it works only for an instant and then suddenly stops!

---

### Post by bash4fun on 2008-09-10
No never tried with WPA2 encryption. Sorry...

---

### Post by ALainONE on 2008-09-10
Thanks a lot!  This one worked for me!!!
Installed using older version [here]("http://downloadcenter.intel.com/Filter_Results.aspx?strOSs=44&strTypes=all&ProductID=2259&OSFullName=Windows*%20XP%20Professional&lang=eng&sType=prev")...

---

### Post by jasonkirk2006 on 2008-09-12
Could anyone of you please tell what is the .sys file name and version?

I think it must be something like Netw4x32.sys/inf but which specific version did you use?

When did this 3945 chip released? It's year 2008 and we are still falling back on ndiswrapper.

---

### Post by fishyf on 2008-09-21
I agree it's strange that there is no working native driver. I wrote about my experiences here: [http://ubuntuforums.org/showthread.php?t=818128](http://ubuntuforums.org/showthread.php?t=818128)


The file I used was netw4x32.inf. I don't know if the name completely describes the version, but I can tell you that the md5 is 894ccd5a39001026013b1c839b9ac3c0.

In any event it has recently started to not connect on boot up and the computer has started to crash - completely unresponsive ... which I suspect is the fault of ndiswrapper (and the reason I came across your post).

---

### Post by jasonkirk2006 on 2008-09-21
Hi fishyf;

Thanks for sending the md5 hash. But searching for an md5 hash is quite difficult. Could you please send the output of

```

$ lshw -C network

```

By the way, what model is your laptop?

---

### Post by fishyf on 2008-10-11
lshw _C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netw4x32 driverversion=1.52+Intel,03/13/2008,11.5.1.15 ip=192.168.1.5 latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g

The laptop is a toshiba satelite pro, u200 model PLUA1E

By the way, I booted the Intripid Ibex beta live CD and the wireless worked straight off. (unencrypted).

---

### Post by Andre-D on 2008-11-03
even intripid ibex's 3945 drivers have same poor performance as other Ubuntus before, this ndi-drivers should have been standard.

File copy , 700MB over 54Mbit WLAN using iwl3945, = ubutu 8.10 = 7minutes21sec, windows, same hardware, same file=5minutes:7sec.

---

### Post by Xmister on 2010-03-20
Thanks!!
I could have never found this DELL driver which is actually works with ndiswrapper.

---

