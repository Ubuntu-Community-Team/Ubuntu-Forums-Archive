---
title: "IBM think pad T43's ipw2200 error - 62"
date: 2016-01-24
forum: Networking &amp; Wireless
---

### Post by starsfart_ on 2016-01-24
&#65279;Hello, was wondering if anyone can help. I'm on mobile and I'm expecting some formatting or readability issues, sorry in advance. I copy pasted the output from my terminal into a text file to post from my phone, and it lags.

My wireless isn't working. Yesterday, it didn't work, but  I rebooted the computer a handful of times and it ran just fine for the rest of the day. This hasn't worked today.

I'm running ubuntu 14.04, on an IBM Thinkpad T43, and haven't done any recent updates. During bootup there, a quick error message that ipw2200 is unable to load firmware -62, failed with error -5. 

I've found similar [solved] threads here, so these are what I've tried and the outputs. 


Ran:
```
sudo modprobe -r ipw2200 && sudo modprobe ipw2200
```

No reaction

Ran:
```
iwconfig
```

Returned:
```
irda0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.
```

Ran: 
```
dmesg | grep ipw
```

Returned: 
```
[   33.204966] libipw: 802.11 data/management/control stack, git-1.1.13
[   33.204972] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   33.482659] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   33.482666] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   33.594098] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   34.597149] ipw2200: device failed to start within 500ms
[   34.597246] ipw2200: Unable to load firmware: -62
[   34.766863] ipw2200: probe of 0000:04:02.0 failed with error -5
```


```
sudo lshw -C network
```
                    
 ```
 *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: 00:10:c6:c0:37:78
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 firmware=5751m-v3.40a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:90100000-9010ffff
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:04:02.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
       resources: memory:90301000-90301fff
```


```
ls -al /lib/firmware/ | grep ipw
``````

-rw-r--r--  1 root root  209190 Jan  6 23:40 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 Jan  6 23:40 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 Jan  6 23:40 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 Jan  6 23:40 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 Jan  6 23:40 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 Jan  6 23:40 ipw2200-sniffer.fw


```
```
rfkill list all 
```
returned no result


```
lspci
``````

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
04:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
04:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
```

```
ifconfig
```
```
eth0      Link encap:Ethernet  HWaddr 00:10:c6:c0:37:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14622 (14.6 KB)  TX bytes:14622 (14.6 KB)
```

the firmware exists:
```
ls -al /lib/firmware/ipw2200-bss.fw
```
```
-rw-r--r-- 1 root root 191154 Jan  6 23:40 /lib/firmware/ipw2200-bss.fw
```
I saw that chili555 offered an attached file for firmware once, but i wasn't able to download it (because mobile? My android is my troubleshooting resource now that my laptop is down.)

couldn't download firmware from ipw2200.sf.net (unavail/returns error in download link)

found ipw2200 .deb eventually somewhere (i forget where), then it wouldn't install. I extracted it onto the desktop, and tried running ```
sudo cp Desktop/2200/* /lib/firmware
```
cp: cannot stat ‘Desktop/2200/*’: No such file or directory
```
mihhargh@mihhargh-ThinkPad-T43:~$ cp: cannot stat ‘Desktop/2200/*’: No such file or directory
No command 'cp:' found, did you mean:
 Command 'cpm' from package 'cpm' (universe)
 Command 'cpp' from package 'cpp' (main)
 Command 'cp' from package 'coreutils' (main)
 Command 'cpu' from package 'cpu' (universe)
cp:: command not found
```

also couldn't install from the software centre, here's error message: 
```
(Reading database ... 985203 files and directories currently installed.)
Preparing to unpack .../firmware-ipw2x00_0.28+squeeze1_all.deb ...
Unpacking firmware-ipw2x00 (0.28+squeeze1) ...
dpkg: error processing archive /home/mihhargh/Desktop/firmware-ipw2x00_0.28+squeeze1_all.deb (--install):
 trying to overwrite '/lib/firmware/ipw2100-1.3-p.fw', which is also in package linux-firmware 1.127.20
dpkg-deb (subprocess): decompressing archive member: internal gzip write error: Broken pipe
dpkg-deb (subprocess): cannot copy archive member from '/home/mihhargh/Desktop/firmware-ipw2x00_0.28+squeeze1_all.deb' to decompressor pipe: failed to write (Broken pipe)
dpkg-deb: error: subprocess <decompress> returned error exit status 2
Errors were encountered while processing:
 /home/mihhargh/Desktop/firmware-ipw2x00_0.28+squeeze1_all.deb
```

I need help please, i've run out of previous thread's solutions to try. I don't have access to an ethernet, if there's something I need to download, please make it mobile-friendly? Let me know if there's more I can do before attempting to touch or replace the network card itself...

---

### Post by QIII on 2016-01-24
Please use code tags around your commands and the results.  This will make your posts much easier to read and preserve any formatting.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by starsfart_ on 2016-01-24
Sorry, I hadn't a clue how before,  thanks for fixing it.

---

### Post by chili555 on 2016-01-24
> cp:: command not foundThis is far more troubling to me than the wireless. Are you sure you typed the command properly? When I intentionally type an incorrect command, I get this:```
chili@T440p:~$ pggpgg
pggpgg: command not found

```...with just one colon after the command. Your quote above shows two colons, suggesting that you actually typed:```
sudo cp:  blah blah
```If, on the other hand the simple and common command *cp* doesn't work any longer, then you have bigger problems than wireless!

Let's test. First, write a text file from the terminal:```
echo "this is a test." >  test.txt
```Now let's create a new directory:```
mkdir chili
```Now copy the test.txt into the new directory:```
cp test.txt chili
```Any errors, warnings, smoke or sparks?!?

Can you interrupt the boot process and boot into an earlier kernel version? Does the wireless and *cp* work there?

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)> Hold down (right) SHIFT to display the menu during boot. In certain cases, pressing the ESC key may also display the menu.Then select 'Advanced Options', select any earlier kernel version and boot.

---

### Post by starsfart_ on 2016-01-25
Hi Chili! I went back and tried it again, you're right, I've typed it wrong. 

```
sudo cp Desktop/2200/* 
cp: missing destination file operand after 'Desktop/2200/*'
```

Ran your echo/text.txt tests with no reaction whatsoever too. So that's alright, right?

Also tried booting 3 earlier versions, still no reaction on the wireless front.

---

### Post by chili555 on 2016-01-25
You have the firmware that I have and with the same size and permissions. From my machine:```
chili@T440p:~$ ls -al /lib/firmware | grep ipw
-rw-r--r--  1 root root  209190 Nov 20 11:07 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 Nov 20 11:07 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 Nov 20 11:07 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 Nov 20 11:07 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 Nov 20 11:07 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 Nov 20 11:07 ipw2200-sniffer.fw

```My machine was a fresh install of 15.10 about one week ago and then fully updated. I doubt that the files you extracted from the .deb are any better, newer or different. You can certainly check:```
cd ~/Desktop/2200
ls -al
```Are the files the same size and permission?

You could also check the md5sums:```
md5sum /lib/firmware/ipw2200-bss.fw
```In my case, I get:```
chili@T440p:~$ md5sum /lib/firmware/ipw2200-bss.fw
[COLOR="#FF0000"]045a46163341514ef17490c76bd0c858[/COLOR]  /lib/firmware/ipw2200-bss.fw

```Now check the files you downloaded:```
md5sum ~/Desktop/2200/ipw2200-bss.fw
```Do they have the same md5sum?

If the downloaded files have the same size, permission and md5sum, then they are the same in every respect. Copying over the same, exact firmware file will do nothing.

Please check the files you downloaded and we'll proceed from there. 

I shall be polishing up my bugle preparing to play *Taps* for your old wireless card.

---

### Post by starsfart_ on 2016-01-26
Hey again chili555! Sorry I'm not re

---

