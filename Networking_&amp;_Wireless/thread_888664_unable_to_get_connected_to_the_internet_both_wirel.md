---
title: "unable to get connected to the internet both wirelessly and wired!"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by Mimiye on 2008-08-13
Hi everyone, I am new to linux i installed it two days ago on a brand new laptop which was previously connected to the internet wirelessly which means any of the problem i am facing is nat from the computer! so i believe it has got to do with ubuntu! the problem is I can't get connected to the internet either wirelessly or wired! my wireless card is Atheros Communication Inc.AR242x 802.11abg [/I][/B]and i am using ubuntu 8.04.  As i am new to Linux i'd really be happy if you can give me a detailed explanation to fix my connection problem. So please help me asap as  i need it to get it working to start my project and finish some background work! I'd really really appreciate your help!

Thanks!  

:confused: :(

---

### Post by chili555 on 2008-08-13
In order to get your AR242x wireless going, we are going to need internet connectivity. So, let's see if we can get your wired ethernet going first. Please open a terminal and run:```
sudo lshw -C network
```It will provide information about your wired and wireless hardware. Post both and we'll get going.

Keep this: [http://ubuntuforums.org/showthread.php?t=865971&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=865971&highlight=AR242x)  especially post #4 for future reference.

---

### Post by user440 on 2008-08-13
I have probably read no fewer than 20 threads on this same problem.

1.)  I do not wish to hijack, hopefully this will help others as well.

2.)  I do not know what NW cards I have in my system

3.)  System is a Dell D410 laptop with Kubuntu 8.04


Based on the other threads I have read, I have the following output:

```

eth0      Link encap:Ethernet  HWaddr 00:13:72:6c:d1:f1
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          
          
          
          user440@LT-D410:~$ sudo lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.12.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status
        -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)



```

Any assistance would be highly appreciated!

Thanks!

Mike

---

### Post by jimv on 2008-08-13
@Mike

We need to know what your network cards are.  Run this command and post the output:

```
lspci
```

---

### Post by user440 on 2008-08-13
> **jimv said:**
> @Mike

We need to know what your network cards are.  Run this command and post the output:

```
lspci
```

That's the command I was looking for.

Here is the result (thanks again!):


00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Proces
sor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Exp
ress Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Gr
aphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Ex
press Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US
B UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                                                              B UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                                                              B UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                                                              B UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                                                              B2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (IC                                                              H6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem                                                               Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev                                                               03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE                                                               Controller (rev 03)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethe                                                              rnet PCI Express (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
02:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.                                                              11g Wireless LAN Controller (rev 02)

---

### Post by jimv on 2008-08-13
Broadcom Corporation NetXtreme BCM5751 Gigabit Ethe rnet PCI Express (rev 01)

That should work ok in Ubuntu...hmmm.  Need more output ;)

Can you post the output of 

lshw -C network

THanks!

---

### Post by user440 on 2008-08-13
I executed that above, but I do not see anything of value in the output (probably not saying much):

To be clear, neither wired nor wireless is working on this particular LT.

Thanks again Jim!


Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.12.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status
        -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

---

### Post by chili555 on 2008-08-13
I think you *have* quite effectively hijacked the thread. Mimiye posted about his/her Atheros, not your Broadcom. By the way, that's a capital C in:```
sudo lshw -C network
```I suggest you start a new thread with this in the title:> Broadcom Corporation NetXtreme BCM5751

---

### Post by user440 on 2008-08-13
Sorry, since we were both having trouble with wired and wireless, I did not want to clutter up with a new thread.

Here's the link to the new thread:

[http://ubuntuforums.org/showthread.php?p=5582455#post5582455](http://ubuntuforums.org/showthread.php?p=5582455#post5582455)

---

