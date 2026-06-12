---
title: "Wifi drops out"
date: 2017-08-14
forum: Networking &amp; Wireless
---

### Post by ceponatia2 on 2017-08-14
(EDIT)Changed this post to only be about one question as suggested(/edit)
Hey all, don't mean to be a downer but this is my third attempt in my life of using Linux (every few years I forget how frustrating it is for me) and I'm running into the same problems I always do even though this is a completely different PC. Just wondering if anyone can point me to some help to get started with; I know Linux is a very DIY platform and I don't mind doing some work to fix my issues I just have no clue where to start.

First off - my internet connection drops every 5-10 minutes. I have 3 networks available in my house... one is my actual modem and two are different settings on my router (Netgear and Netgear 5G). I have to rotate to a different one every 10 minutes or so which makes doing pretty much anything on this computer ridiculous. I know I don't necessarily need the router since my modem has WiFi (my father set up the network and he's far from a pro) but the router networks seem to last longer than the modem one so I don't want to risk disconnecting the router and then not having any internet connection at all anymore.

Thanks for any help. I submit to your expertise!

---

### Post by vasa1 on 2017-08-14
If you limit your question to just one issue and give the thread an appropriate title, things will be less confusing. We also have some helpful hints on how to get your problems solved quickly: [https://ubuntuforums.org/showthread.php?t=2158945](https://ubuntuforums.org/showthread.php?t=2158945)

---

### Post by RobGoss on 2017-08-15
Hello and welcome to the forums, I don't think you really need luck to run Linux just a basic understanding how things work. You might want to also share what version of Ubuntu you're trying to install along with the specs for the machine in question

A good way to start is to research problem that may a rise there's a lot of good information out there that can help improve your Linux skills to make things easier

---

### Post by poorguy on 2017-08-15
I found this to be of great help.

Easy Linux Tips Project

[https://sites.google.com/site/easylinuxtipsproject/](https://sites.google.com/site/easylinuxtipsproject/)

Also if Ubuntu isn't working for you try other Linux distros such as Xubuntu or Lubuntu as these are lighter on resources.

Linux Mint 18 Sarah Xfce is also another good alternative imo.
I have found it to install and work where Ubuntu wouldn't.

Linux Mint

[https://www.linuxmint.com/download_all.php](https://www.linuxmint.com/download_all.php)

---

### Post by oldos2er on 2017-08-15
Please tell us your full hardware specs.

---

### Post by Tadaen_Sylvermane on 2017-08-15
Don't give up. I tried Linux off and on over the course of 10 years before I switched completely and have been Windows free for the last 4 years give or take. I had many "unsolvable" problems back then. Now it's nothing but a config file edit and away I go. It's worth it once you sort out the little issues.

*EDIT* I know this doesn't help the problem, just hoping to inspire

---

### Post by ceponatia2 on 2017-08-15
OK I will make separate posts for questions; in this post I'd like to focus on the internet connection issue as it is the most frustrating. Just in the time I've been typing this post and looking up my hardware specs I've had to switch my connection three times. I didn't have problems like this when running Windows (not saying anything about Linux vs Windows just thought that might be useful to mention; it's probably not a router issue).

Ubuntu version 16.04.2

Here's what I got when I ran lshw... a simplified list is at the end, just wanted to be as detailed as possible.
```

description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 7914MiB
     *-cpu
          product: Intel(R) Core(TM) i5-4460  CPU @ 3.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 3200MHz
          capacity: 3400MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts cpufreq
     *-pci
          description: Host bridge
          product: 4th Gen Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
          configuration: driver=hsw_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e8000000(size=167772160)
           *-display
                description: VGA compatible controller
                product: GK208 [GeForce GT 720]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:32 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: GK208 HDMI/DP Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f7080000-f7083fff
        *-usb:0
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:29 memory:f7200000-f720ffff
        *-communication
             description: Communication controller
             product: 8 Series/C220 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:33 memory:f721b000-f721b00f
        *-usb:1
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7218000-f72183ff
        *-multimedia
             description: Audio device
             product: 8 Series/C220 Series Chipset High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:34 memory:f7210000-f7213fff
        *-pci:1
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=4096) memory:e0000000-e01fffff ioport:e0200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:d000(size=4096) ioport:f2100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: enp3s0
                version: 09
                serial: 44:8a:5b:c1:dd:08
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168f-1_0.0.5 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:30 ioport:d000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff
        *-pci:3
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:c000(size=4096) memory:f7100000-f71fffff
           *-network
                description: Wireless interface
                product: RTL8821AE 802.11ac PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlp4s0
                version: 00
                serial: 9c:ad:97:59:f3:c9
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8821ae driverversion=4.10.0-32-generic firmware=N/A ip=10.0.0.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:35 ioport:c000(size=256) memory:f7100000-f7103fff
        *-usb:2
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7217000-f72173ff
        *-isa
             description: ISA bridge
             product: B85 Express LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:31 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:f7216000-f72167ff
        *-serial UNCLAIMED
             description: SMBus
             product: 8 Series/C220 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7215000-f72150ff ioport:f000(size=32)
     *-scsi
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM SW830
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             logical name: /media/brian/RF-MRBTAD
             version: 8.83
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /media/brian/RF-MRBTAD
                configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage

```

Intel i5-4460 3.2GHz
Geforce GT720
RTL8821AE wireless adapter
8GB RAM

---

### Post by ceponatia2 on 2017-08-15
> **Tadaen_Sylvermane said:**
> Don't give up. I tried Linux off and on over the course of 10 years before I switched completely and have been Windows free for the last 4 years give or take. I had many "unsolvable" problems back then. Now it's nothing but a config file edit and away I go. It's worth it once you sort out the little issues.

*EDIT* I know this doesn't help the problem, just hoping to inspire

Being positive does help, lol. I had gotten fairly fluent with the basics back in the day but I've forgotten all of it. If I remember correctly, my internet problem was a thing back then too and I'm pretty sure it's what drove me back to Windows. I'm committed to fixing it this time though! (especially since soon I will have an entirely different Windows gaming machine so there's no reason for me to give up and reinstall windows on this desktop)

---

### Post by wildmanne39 on 2017-08-15
Is it a wifi issue or ethernet?

---

### Post by wildmanne39 on 2017-08-15
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by ceponatia2 on 2017-08-15
It's a wifi issue.

---

### Post by wildmanne39 on 2017-08-15
Yes, any time you post output from a terminal command please use code tags.

Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by praseodym on 2017-08-15
Try these module parameters
```

echo "options rtl8821ae swenc=1 swlps=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl88821ae_options.conf

```Reboot

---

### Post by ceponatia2 on 2017-08-15
This happened... sorry I'm not very knowledgeable.

```
~$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \ chmod +x wireless-info && \> wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \ chmod +x wireless-info && \ .wireless-info
--2017-08-15 17:48:42--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 192.30.253.113, 192.30.253.112
Connecting to github.com (github.com)|192.30.253.113|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2017-08-15 17:48:43--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.44.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.44.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16540 (16K) [text/plain]
Saving to: &#8216;wireless-info&#8217;


wireless-info       100%[===================>]  16.15K  --.-KB/s    in 0.03s   


Last-modified header missing -- time-stamps turned off.
2017-08-15 17:48:43 (556 KB/s) - &#8216;wireless-info&#8217; saved [16540/16540]


No command ' chmod' found, did you mean:
 Command 'chmod' from package 'coreutils' (main)
 chmod: command not found

```

---

### Post by wildmanne39 on 2017-08-15
All you do is copy and paste the command into the terminal all at once then enter your password and it will create a wireless-info.text file in your home folder then you post the file here.

You may want to do what praseodym recommends it may fix the issue.

---

### Post by genericvii143 on 2017-08-15
Can you type in the terminal  "  rfkill list "  and post the result here so we can see it?

---

### Post by ceponatia2 on 2017-08-15
[http://paste.ubuntu.com/25322232/](http://paste.ubuntu.com/25322232/)

---

### Post by ceponatia2 on 2017-08-15
rfkill list: 0: phy0: Wireless LAN	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by ceponatia2 on 2017-08-15
(lol how do you delete posts?) Entered the command Praesodym suggested, rebooting now.

rebooted. Crap now I can't connect at all how do I undo that lol

---

### Post by wildmanne39 on 2017-08-16
Do:
```
sudo rm /etc/modprobe.d/rtl88821ae_options.conf
```
Reboot, that should return it to normal.

Did you copy and paste the command all as one command?

---

### Post by ceponatia2 on 2017-08-16
Yes I just copied and pasted the whole thing straight into terminal. The pastebin link is up 4 posts, ignore the one where it didn't work.

---

### Post by wildmanne39 on 2017-08-16
The directions I gave you to undo the commands you ran got your wifi working again? if so I will start listing the things that can help your issue.

---

### Post by ceponatia2 on 2017-08-16
I won't be home until after 5PM EST but I will hop on right away and let you know. :)

---

### Post by ceponatia2 on 2017-08-18
I didn't have to enter those commands, my wifi connected immediately upon turning my PC on today after being off for the whole day yesterday. Sorry it took me so long to get back to you guys, I had a bout of illness but I'll be here all day today as I'm taking off work.

---

### Post by ceponatia2 on 2017-08-18
I don't want to jinx myself but my PC has been on for about 30 minutes without losing connection since starting up this morning. Could be premature as something different happens every time I restart my computer.

(edit) False alarm, went down about 10 minutes after posting that. I did notice that when I connect to a different network a popup shows that says "network discovery disabled". Could that be part of the issue?

---

### Post by wildmanne39 on 2017-08-18
Did you already revert the changes you made to the driver? if not wait and run the wireless script again so we can have a look after the changes were made.

---

### Post by dw1-4 on 2017-09-20
What happens if you deactivate ("ignore") the IP-v6 in Network manager?
Ubuntu ethernet and WiFi is controlled by network manager (if you go with the standard stuff). 

For me it resolved the issue to deactivate IP-v6.

---

