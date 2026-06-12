---
title: "ipw3945 Install Problems"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by mfmbcpman on 2006-11-23
I am trying to install ipw3945 and I get the problem below. What do I do?```
michael@Michaellaptop:~$ cd '/home/michael/Desktop/ipw3945-1.1.2'
michael@Michaellaptop:~/Desktop/ipw3945-1.1.2$ make
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
sed: can't read net/ieee80211.h: No such file or directory
/bin/sh: [[: not found
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e  Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1

```

---

### Post by jacoby on 2006-11-23
If you are using Dapper or Edgy, you shouldn't have to install it.  It's already there.

I refer you here:
[http://www.ubuntuforums.org/showthread.php?t=305662]("http://www.ubuntuforums.org/showthread.php?t=305662")

Works on my laptop.

---

### Post by mfmbcpman on 2006-11-23
> **jacoby said:**
> If you are using Dapper or Edgy, you shouldn't have to install it.  It's already there.

I refer you here:
[http://www.ubuntuforums.org/showthread.php?t=305662]("http://www.ubuntuforums.org/showthread.php?t=305662")

Works on my laptop.

I followed that but on the last step it says to change to eth1 but all I have is eth0 and it still  doesn't work when I select that

---

### Post by jacoby on 2006-11-23
Did you activate the wireless in networking? (The checkbox next to the adapter)

Also, make sure your wireless switch is turned on.

I'm lurking about here so I'll look a bit more and get back.

---

### Post by jacoby on 2006-11-23
> **jacoby said:**
> Did you activate the wireless in networking? (The checkbox next to the adapter)

Also, make sure your wireless switch is turned on.

I'm lurking about here so I'll look a bit more and get back.

EDIT: As an afterthough, obviously the wireless switch is on if the adapter is detected.  In the adapter properties though, make sure the "Enable this Connection" box is checked.

---

### Post by mfmbcpman on 2006-11-23
The Enable box is checked but the Wi-Fi light above my keyboard is not on. However, when I go into Windows everything works fine.

---

### Post by jacoby on 2006-11-24
That sounds like a kernel module issue.  I'm fairly newbish myself, and I'm not quite there yet.  You need to get the module to load on startup, which it should by default (from everything I've read, and I have the same wireless).  So, I guess it goes back to installing a kernel module, like you were doing in the first place.  Do you use Dapper (v6.06) or Edgy (v6.10)?

EDIT: And another thing, the light on your keyboard isn't always correct.  That's one thing I've learned.  Sometimes the lights, special keys, and indicators don't work in a 'nix system as they would in windows.  Thats a driver issue in itself.  Most laptops are made with windows in mind.  And since the wireless connection is visible in networking, but not lighting up your indicator, it is probably on.  One other thing, go into System menu > Administration > Networking > Wired Connection Properties and make sure it is not enabled.  That might be an issue.  I've heard reports that Ubuntu sometimes doesn't like multiple cards, be they wired, wireless, or mixed.

---

### Post by mfmbcpman on 2006-11-24
I'm using Edgy

---

### Post by Celeborn74 on 2006-11-26
Hello mfmbcpman, hello Jacoby,

I'm a Kubuntu user, and I have exactly the same problem. The issue is that eth1 won't appear if you have the following in dmesg:
[17179586.556000] ipw3945: Unknown symbol ieee80211_wx_get_encodeext
[17179586.556000] ipw3945: Unknown symbol ieee80211_wx_set_encode
[17179586.556000] ipw3945: Unknown symbol ieee80211_wx_get_encode
[17179586.556000] ipw3945: Unknown symbol ieee80211_txb_free
[17179586.556000] ipw3945: Unknown symbol ieee80211_wx_set_encodeext
[17179586.560000] ipw3945: Unknown symbol ieee80211_wx_get_scan
[17179586.560000] ipw3945: Unknown symbol escape_essid
[17179586.560000] ipw3945: Unknown symbol ieee80211_freq_to_channel
[17179586.560000] ipw3945: Unknown symbol ieee80211_set_geo
[17179586.560000] ipw3945: Unknown symbol ieee80211_rx
[17179586.560000] ipw3945: Unknown symbol ieee80211_get_channel
[17179586.560000] ipw3945: Unknown symbol ieee80211_channel_to_index
[17179586.560000] ipw3945: Unknown symbol ieee80211_rx_mgt
[17179586.560000] ipw3945: Unknown symbol ieee80211_get_geo
[17179586.560000] ipw3945: Unknown symbol free_ieee80211
[17179586.560000] ipw3945: Unknown symbol ieee80211_tx_frame
[17179586.560000] ipw3945: Unknown symbol ieee80211_is_valid_channel
[17179586.560000] ipw3945: Unknown symbol ieee80211_get_channel_flags
[17179586.560000] ipw3945: Unknown symbol alloc_ieee80211

I have checked out the following links but still did not get it to work:
[http://www.ubuntuforums.org/showthread.php?t=140085&page=2&highlight=3945](http://www.ubuntuforums.org/showthread.php?t=140085&page=2&highlight=3945)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_get_ipw3945_and_wep.2Fwpa_to_work](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_get_ipw3945_and_wep.2Fwpa_to_work)

It seems to be an ieee80211 problem as I have installed and uninstalled the ieee80211 module and haven't - in both cases I still get the dmesg output.

This is the last thing I need to get to work on my WMLi5256 so I'm as well getting desperate... ](*,) 

Maybe someone can help? All my searches in various forums did not prove to be helpful...

BTW, System is Edgy.

Cheers,

Celeborn

---

### Post by Lucky on 2006-11-27
I also got the same error as Celeborn74. When I make ieee80211-1.2.15, it asked if I wanted to already present files. I replaced it. How can I go back to original?

---

### Post by Celeborn74 on 2006-11-27
Hi Lucky,

partial success here from my side. As I installed in a quick night session, I may have made a mistake. Now, surprisingly, it worked the following way:
1. With "sudo make" and "sudo make install" I simply added again the ieee80211 files. No idea what I had originally but it seems okay.
2. After (re-)installation of the "linux-restricted-modules-generic" from repos I tried re-loading ipw3945 ("sudo modprobe -r ipw3945" and "sudo modprobe ipw3945")
3. Surprise! "lsmod" shows:
ieee80211              51436  1 ipw3945
ieee80211_crypt         7808  1 ieee80211

"dmesg" error messages disappeared.

So far the good news. So a simple re-installation would be good for you?

Problem now is that eth1 does not appear. "iwconfig" only shows up eth0, sit0 and lo. The following line shows:
celeborn@celeborn-laptop:~$ sudo /sbin/ipw3945d-2.6.17-10-generic
Password:
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2006-11-27 23:00:06: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

Interesting is what appears in "dmesg" after unloading and reloading of the ipw3945 module:
[17180440.516000] ieee80211_crypt: unregistered algorithm 'NULL'
[17180458.016000] ieee80211_crypt: registered algorithm 'NULL'
[17180458.020000] ieee80211: 802.11 data/management/control stack, 1.2.15
[17180458.020000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17180458.028000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0mp
[17180458.028000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17180458.028000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[17180458.028000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[17180458.032000] ipw3945: ipw3945.ucode load failed: Reason -2
[17180458.032000] ipw3945: Could not read microcode: -2
[17180458.032000] ipw3945: probe of 0000:05:00.0 failed with error -2

In research I found this error also in case of manual installation via the Intel Drivers so the fixes did not work for me (as I use the restricted modules package).

Anybody had the same behaviour? I also tried to boot via pci=noacpi but without success... :-k 

Maybe it works better for you? In any case, comments would be helpful, and after solution I would recommend to put this into a WIKI as there seems to be a lot of trouble with this out there.

Cheers,

Celeborn

---

### Post by Celeborn74 on 2006-11-27
OK, another update from my side:
From the Intel packages I copied the firmware files to the /lib/firmware files: 
sudo cp Programme/ipw3945-linux-1.1.0/ipw3945-ucode-1.13/ipw3945.ucode /lib/firmware/2.6.17-10-generic/

Now the message of missing firmware in "dmesg" has disappeared but it looks strange, and there is no eth1 still:

[17179686.532000] ACPI: PCI interrupt for device 0000:05:00.0 disabled
[17179686.536000] ieee80211_crypt: unregistered algorithm 'NULL'
[17179691.664000] ieee80211_crypt: registered algorithm 'NULL'
[17179691.672000] ieee80211: 802.11 data/management/control stack, 1.2.15
[17179691.672000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno                    @linux.intel.com>
[17179691.672000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver                     for Linux, 1.1.0mp
[17179691.672000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179691.672000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 19 (level, low) ->                     IRQ 193
[17179691.672000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[17179691.672000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connectio                    n

I have really two questions now:
1. Why do I have to manually copy the firmware file from the Intel driver package when I use "linux-restricted-modules-generic"? This does not sound right somehow... :confused: 
2. I'm not sure but the dmesg sounds like an ACPI problem.

Any help from somebody? Any hint is welcome!!

Cheers,

Celeborn

---

### Post by Lucky on 2006-11-28
hey Celeborn74,
For me it stared working. I just reinstalled linux-restricted-modules-generic  and linux-restricted-modules-2.6.17-10-generic. 
After this I was able to see wireless connection in System>Administration>Networking. 
Just see if this works for you.

---

### Post by Celeborn74 on 2006-11-28
Hi Lucky,

thanks for this posting and congratulations. I have been successful as well, trying again after your posting. I followed this bug report:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/62452](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/62452)

The last posting there brought me to the fact that in /etc/modprobe.d folder the ipw3945 file was missing. I remember that I have removed it in the course of fixing another issue. After the manual start of /sbin/ipw3945d-ipw3945d-2.6.17-10-generic eth1 turned up. Fixed it by adding manually a file.

Anyway, thanks! Still I wonder why I had to manually copy the firmware in spite of the linux-restricted-modules-generic?

Anyway, works now and that's all I want to know! Yesterday I even went to the length of manually fixing the dsdt for my Acer Aspire 5652 as I thought of an ACPI problem. What a waste of time...

Cheers,

Celeborn

---

### Post by pokeyflan on 2006-12-10
Hi!

I'm hoping someone can help me; I've been trying to get my ipw3945 working without success.  As I'm a semi-noob, i'm not sure if i am making things worse by mis-following instructions or not.

I tried installing the driver, daemon, firmware & ieee files from sourceforge.  Late last night, eth0 finally appeared in my networking menu and on iwconfig.  Today, not.  I'm afraid i'm really CLUELESS about this, so detailed instructions are necessary.  I'm running Dapper.

Something strange, when I run:
'sudo lshw -C network' it returns:

 *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@05:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:d4000000-d4000fff irq:10

dmesg gives me all those ipw3945 disagree messages that Celeborn74 reported.

Appreciate all suggestions......chris
](*,)  -- my head feels like this now!

---

### Post by Celeborn74 on 2006-12-12
Hi Pokeyflan,

understand your frustration. Currently I have no access to my Notebook for some more days, and on top I am running Edgy so I cannot say whether Dapper has a different way.

I had two kind of error messages. If the ieee error message type appears, a reinstallation of the ieee files from sourcefourge helped.
The second one came afterwards to copy the firmware file (though I installed the default Ubuntu package.

Are you sure that there is no default Ubuntu package for Dapper as well in the repositories? You should definitely google with "Dapper" and "ipw3945" in case you are not sure but with the installations, you always can uninstall.

Have a look at the attached links as well, if I remember correctly they had some also Dapper related stuff.

Sorry, cannot say more at the moment. If you don't get any answers, I recommend to open a new thread as Dapper and Edgy might be different.

Good luck, sorry not to be more specific.

Cheers,

Celeborn

---

### Post by zish on 2006-12-31
In response to the very first entry in this thread, I resolved the issue by making the "/bin/sh" symlink to point to "/bin/bash" instead of "/bin/dash". It seems to me that either A) the Makefile was made to work with bash, instead of bourne shell, or B) the Debian Almquist SHell isn't 100% compatible. I haven't verified either myself.

---

### Post by aquaxbat on 2007-01-01
I am stuck way before all of you guys on this issue with no wireless. I am running Edgy 6.10 and I have a Mobile AMD Sempron 3500+ (1.8GHz/512KB) with a newly installed Intel 3945ABG card in my laptop.

SO, i reloaded Edgy back onto my laptop in hopes that it would recognize it but when i enter in: lspci ... i still seem the lameazz Broadcom ethernet controller. Now is this due to the fact that there is an RJ-45 connection?? I can get online with my laptop as long as it is wired.

How do I, from scratch or whatever, start installing all needed dependencies (drivers, other programs needed) to at least be where you guys are. Is there a good wiki to follow?? I have a fresh copy of Edgy and installing updates as we speek.

Also are there any issues with AMD boards and chips with Intel wireless cards??:confused:

---

### Post by Celeborn74 on 2007-01-02
Hi aquaxbat,

it sounds to me that you may not have installed the drivers yet. You may try first to follow this link:
[Edgy Inoffical Guide iwp3945]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_get_ipw3945_and_wep.2Fwpa_to_work")

After that you don't have to reboot but open a bash and type "sudo modprobe ipw3945" and after that "iwconfig". eth1 should appear. If not, I would recommend to try "dmesg" to find out what the issue is. If they are similar than mine, a reinstallation of the ieee module may help as in my case.
Another possibility is (as you spoke of newly installed) to check /etc/network/interfaces after the steps above and see if a line for eth1 appears. If not you may try first "sudo ifconfig eth1 up" in the bash. If this works, you should update the above mentioned file. However, this should be a check step only in the first place as starting point if you still have trouble. 

As for the Broadcom ethernet controller (eth0), it should appear, right?

If it works, you might try the following howto for WAP afterwards. I did not try it myself yet:
[http://www.martinhenze.de/2006/06/02/wpa-with-ipw2200-on-ubuntu-dapper-drake/](http://www.martinhenze.de/2006/06/02/wpa-with-ipw2200-on-ubuntu-dapper-drake/)

Cheers,

Celeborn

---

### Post by aquaxbat on 2007-01-02
So maybe i am just a newb. I am not even sure i installed the ieee module. I've gone to so many different places to try and get my wireless to work i am so confused. I have ndiswrapper installed. I replaced the Broadcom wireless with the intel 3945.

I have the linux-restricted-modules-generic.

This is what my /etc/network/interfaces says:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

Now ifconfig does see eth0 which i am guessing is my hardwired connection since i am online. But there is no eth1.

iwconfig says:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

...

dmesg:

[22078.375024] eth0: no IPv6 routers present
[22143.609919] ieee80211_crypt: registered algorithm 'NULL'
[22143.620553] ieee80211: 802.11 data/management/control stack, git-1.1.13
[22143.620558] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[22143.661197] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0mp
[22143.661202] ipw3945: Copyright(c) 2003-2006 Intel Corporation

I downloaded the stupid drivers from intel, both the windows driver and the one that is packaged for linux. I am confused on where the heck this driver goes. (ndiswrapper i know uses it, tried that)
 
So thus far, there is no eth1, nothing wiresless is detected. System > Admin > Networking doesn't show wireless. Help??](*,)

---

### Post by Celeborn74 on 2007-01-03
Hi aquaxbat,

the drivers look all right so there seems to be no issues there. Did the ipw3945 load automatically on boot or only after "sudo modprobe ipw3945"? Does the ipw3945 appear directly after booting when you type "lsmod" in the bash?

If it does load automatically AND your lspci still shows the previous Broadcom wireless (misunderstanding from my side firstly, sorry), I would recommend to open a new thread as this seems to me like an entirely different set of problems compared to this one.

AFAIK Edgy is running scripts on boot to detect hardware but in your case this seems to fail... :-k 

Cheers,

Celeborn

---

