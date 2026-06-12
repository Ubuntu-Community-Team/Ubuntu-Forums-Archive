---
title: "Wi-Fi is disabled by hardware switch, how to turn in on?"
date: 2014-04-29
forum: Networking &amp; Wireless
---

### Post by Katzwinkel on 2014-04-29
Hi,
I recently installed Xubuntu on my old Medion desktop PC (on a seperate hard disk) on which I already had installed WinXP (as Multi-Boot System). 
Now, in Xubuntu my WiFi does not work. In the network-menu I get "Ethernet Network" --> "disconnected" and under "Wi-Fi Networks" --> "Wi-Fi is disabled by hardware switch".

I read that this can sometimes be caused by the WiFi having been disabled in Windows, but the WiFi works just fine under WinXP.

I tried running "sudo ifconfig wlan0 up" but i just get the message "SIOCSIFFLAGS: Operation not possible due to RF-kill"

Running "lshw -class network" gives me this:
> *-network
 description: Ethernet interface
 product: VT6105/VT6106S [Rhine-III]
 vendor: VIA Technologies, Inc.
 physical id: 6
 bus info: pci@0000:03:06.0
 logical name: eth0
 version: 8b
 serial: 00:0c:76:71:02:09
 size: 10Mbit/s
 capacity: 100Mbit/s
 width: 32 bits
 clock: 33MHz
 capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
 configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
 resources: irq:18 ioport:d100(size=256) memory:d0001000-d00010ff
*-network DISABLED
 description: Wireless interface
 physical id: 2
 bus info: usb@1:8.1
 logical name: wlan0
 serial: 00:11:08:50:7e:7e
 capabilities: ethernet physical wireless
 configuration: broadcast=yes driver=rt2500usb driverversion=3.13.0-24-generic firmware=N/A link=no multicast=yes wireless=IEE 802.11bg

Can somebody hekp me?

---

### Post by ian-weisser on 2014-04-29
Push the button or flip the switch or use the FN-key combo to manually enable your wireless.

---

### Post by Katzwinkel on 2014-04-30
thanks, but I can't find a hardware switch onb my PC to turn it on and I don't know of any Fn-Key combo for this. Please remember, I am talking about a PC NOT a Laptop here. 
Also, The WiFi is working perfectly when I log into Windows on the same PC, so it can't be PHYSICALLY turned off, can it?
Any other suggestions, anyone?

---

### Post by chili555 on 2014-04-30
From the terminal, may we see:```
rfkill list all
lsmod
```Thanks.

---

### Post by Katzwinkel on 2014-05-05
Hi chili555 and everybody else,
Sorry for my late reply.
here is the outpur you requested:

"rfkill list all" gives me this:
```
rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

"lsmod" gives me this:
```
lsmod
Module                  Size  Used by
rfcomm                 53664  12 
bnep                   18895  2 
arc4                   12536  2 
rt2500usb              30861  0 
rt2x00usb              20041  1 rt2500usb
snd_hda_codec_cmedia    13668  1 
rt2x00lib              48886  2 rt2x00usb,rt2500usb
mac80211              545990  2 rt2x00lib,rt2x00usb
snd_hda_intel          42730  3 
cfg80211              409394  2 mac80211,rt2x00lib
snd_hda_codec         164067  2 snd_hda_intel,snd_hda_codec_cmedia
snd_hwdep              13272  1 snd_hda_codec
rc_medion_x10_digitainer    12496  0 
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
ati_remote             18163  0 
usb_storage            48417  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
rc_core                26724  3 ati_remote,rc_medion_x10_digitainer
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                91033  0 
snd_rawmidi            25135  1 snd_seq_midi
serio_raw              13230  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
adt7475                22020  0 
hwmon_vid              12687  1 adt7475
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
lpc_ich                16864  0 
snd_timer              28584  2 snd_pcm,snd_seq
btusb                  27580  0 
bluetooth             342263  22 bnep,btusb,rfcomm
snd                    60871  15 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
nouveau               969577  3 
soundcore              12600  1 snd
mxm_wmi                12893  1 nouveau
parport_pc             31981  1 
wmi                    18673  2 mxm_wmi,nouveau
video                  18903  1 nouveau
ppdev                  17391  0 
ttm                    72698  1 nouveau
drm_kms_helper         46907  1 nouveau
lp                     13299  0 
drm                   243792  5 ttm,drm_kms_helper,nouveau
parport                40836  3 lp,ppdev,parport_pc
mac_hid                13037  0 
i2c_algo_bit           13197  1 nouveau
firewire_ohci          35529  0 
firewire_core          61867  1 firewire_ohci
via_rhine              27653  0 
mii                    13654  1 via_rhine
crc_itu_t              12627  1 firewire_core
floppy                 55378  0 
```

so the wireless is listed as "Hard Blocked". But as I've said before, it works perfectly well under windows on trhe same machine without me flipping any kind of physical switch (I would not even know were that would be)

---

### Post by chili555 on 2014-05-05
Please let us see:```
cat /sys/class/rfkill/rfkill0/hard
```I suspect the result is 1. If so, please try:```
sudo -i
echo 0  >  /sys/class/rfkill/rfkill0/hard
exit
rfkill list all
```If that works, we'll write a quick file to make it persistent.

---

### Post by Katzwinkel on 2014-05-05
@chili5555:
sadly, the result to "cat /sys/class/rfkill/rfkill0/hard" is NOT 1 as you expected, but 0.
what does that mean?

---

### Post by chili555 on 2014-05-05
> **Katzwinkel said:**
> @chili5555:
sadly, the result to "cat /sys/class/rfkill/rfkill0/hard" is NOT 1 as you expected, but 0.
what does that mean?It means the system doesn't think your wireless is hard-blocked. From my system:> chili@T410:~$ cat /sys/class/rfkill/rfkill0/hard
[COLOR="#FF0000"]0[/COLOR]
chili@T410:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	[COLOR="#FF0000"]Hard blocked: no[/COLOR]Let's also see:```
cat /sys/class/rfkill/rfkill0/state
```

---

### Post by Katzwinkel on 2014-05-05
> Let's also see:
Code:

cat /sys/class/rfkill/rfkill0/state


Now **this** returns "1"

---

### Post by chili555 on 2014-05-05
> **Katzwinkel said:**
> Now **this** returns "1"Also the reading we'd expect in a perfect system.

Let's try a different approach. ```
sudo rmmod -f rt2500usb
sudo rfkill unblock all
sudo modprobe rt2500usb
rfkill list all
```Also, please let us see:```
sudo dpkg -s rfkill | head -n5
```

---

### Post by Katzwinkel on 2014-05-05
Thanks for taking the time for helping me!
I did as you suggested, and now the output of "rfkill list all" is:
```
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
2: phy1: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```
So it's still listed as hardblocked

---

### Post by chili555 on 2014-05-05
How about the other command? I am wondering if we removed the package rfkill and rebooted that we may have a different result.

---

### Post by Katzwinkel on 2014-05-05
Sorry, I had missed the second command in your post.
"sudo dpkg -s rfkill | head -n5" gives me this:
```
Package: rfkill
Status: install ok installed
Priority: optional
Section: utils
Installed-Size:60
```

Just as a thought, though: 
I read that the wirelless-drivers can be an issue sometimes in xubuntu installations. and in my first post you can see that the driver responsible for the Wi-Fi seems to be "rt2500usb". Does that mean that Xubuntu thinks I am using an externally plugged-in usb-WiFi-Adapter? Because I'm actually using an integrated WiFi-Card. However I#ve no Idea where I would finf the correct driver for this, as the manufacturer of my pc (Medion) only supllies Windows-compatible drivers.

---

### Post by chili555 on 2014-05-05
Not necessarily. There are a few devices in the wild that are actually attached to internal USB buses on the motherboard.> *-network DISABLED
description: Wireless interface
physical id: 2
[COLOR="#FF0000"]bus info: usb@1:8.1[/COLOR]
logical name: wlan0
serial: 00:11:08:50:7e:7e
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=rt2500usb driverversion=3.13.0-24-generic firmware=N/A link=no multicast=yes wireless=IEE 802.11bgLet's have a look at some additional diagnostics before we get out the heavy equipment:```
dmesg | grep -e rt2 -e 1:8.1
rfkill --version
```

---

### Post by Katzwinkel on 2014-05-05
"dmesg | grep -e rt2 -e 1:8.1" gives me this:
```
[   10.472496] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2570, rf: 0005, rev: 0003
[   10.556867] usbcore: registered new interface driver rt2500usb
[ 5316.768232] usbcore: deregistering interface driver rt2500usb
[ 5354.765879] ieee80211 phy1: rt2x00_set_chip: Info - Chipset detected - rt: 2570, rf: 0005, rev: 0003
[ 5354.770750] usbcore: registered new interface driver rt2500usb
```

"rfkill --version" gives me this:
```
rfkill 0.5-1ubuntu1 (Ubuntu)
```

---

### Post by chili555 on 2014-05-05
We have sadly descended to the 'kitchen sink' phase of our thread. We have tried many things and none have worked or even show much promise, so we'll start throwing anything and everything at the problem, including the kitchen sink.

I am very reluctant to remove *rfkill *because apt-get says it will also remove ubuntu-desktop!!!

Have you checked in the computer's BIOS to see if there is an option to enable/disable wireless?

---

### Post by Katzwinkel on 2014-05-05
Sadly I can't clearly identify such a function in the BIOS. I thought I might get lucky under the category "Integrated Periphals" but these are the only options I can see:

```
USB Controller [enabled]
Onboard USB Mode [USB 2.0]
USB Keyboard Support [Enabled]
USB Mouse Support [Enabled]
Azalia/AC97 Selection [Auto]
Onboard VIA 1394  [Enabled]
Onboard Lan Boot ROM [Disabled]
IO Devices Confiuration [Press Enter]
IDE Devices Configuration [Press Enter]
SATA Devices Configuration [Press Enter]
```

However, another thought:
WIndows (where the WiFi works) and Xubuntu (where it doesn't) are installed on two physically seperate hard-disks.  I only just recently installed and formatted the hard-disk my Xubuntu is now installed on. When I boot my computer, it first loads Grub from the MBR of the newly installed (Xubuntu) hard-disk. If I choose WIndows from the Grub-menu, then it boots WIndows from my old (windows) hard-disk. Could it be that somehow, if the system is booted from the new hard disk (Xubuntu),some of the devices are not recognized in the same way than when i boot from my old hard disk (windows)?   
I'll try out a Xubuntu live-version or so to check this out (or do you think this is highly improbable/impossible?)

If nothing works, then I may try out if the same things happen also with Kubuntu, Lubuntu and Ubuntu or if it's a Xubuntu specific problem.

---

### Post by Katzwinkel on 2014-05-05
I've tried out a xubuntu Live version after I#ve changed the Boot priority back to my old (Windiws) hard disk: No Change. So the boot seqeunce and the new harddrive are apparently NOT the problem

---

### Post by chili555 on 2014-05-05
Googling this whole mess, I see that rfkill and your driver rt2500usb have had a long history. I thought the issue was fixed. Perhaps it has reverted in kernel version 3.13.0-xx.  [https://bugzilla.kernel.org/show_bug.cgi?id=15679](https://bugzilla.kernel.org/show_bug.cgi?id=15679)

I see this in the driver code:```
 /*
         * Enable rfkill polling by setting GPIO direction of the
         * rfkill switch GPIO pin correctly.
         */
        rt2500usb_register_read(rt2x00dev, MAC_CSR19, &reg);
        rt2x00_set_field16(&reg, MAC_CSR19_DIR0, 0);
        rt2500usb_register_write(rt2x00dev, MAC_CSR19, reg);

```The trouble is, I don't quite know what to do with it! I don't know for sure, but we might try to remove that section altogether and recompile the driver. Unexpected results are...well, expected!

Please see: [https://gitorious.org/ac100/marvin24s-kernel/commit/af79b6e2ebf46235f9a90e990fc3d674317d8301](https://gitorious.org/ac100/marvin24s-kernel/commit/af79b6e2ebf46235f9a90e990fc3d674317d8301)> We need to program the rfkill switch GPIO pin direction to input at device initialization time, not only when the interface is brought up. Doing this only when the interface is brought up c**ould lead to rfkill detecting the switch is turned on erroneously and inability to create the interface and bringing it up.**Sound familiar?

Before we go crazy, I'd suggest you first try a live DVD or USB for an Ubuntu version with an earlier kernel such as 12.04 LTS. Be careful not to get 12.04.4, as it also uses kernel version 3.13.0-xx.

---

### Post by Katzwinkel on 2014-05-05
Thanks Chili555, that sounds good. It may take a while till i downloaded and burned an earlier xubuntu version on my old gear (and it's getting rather late in my home region), but I'll post the results as soon as it's done.
Luckily my Xubuntu installation is still fresh, and without WiFi i could not put much work on it yet. So at least, when we try to change rfkill, we cannot really break anything.
If it turns out that what you are expecting now is indeed the problem, could you tell me what exactly to state in the bug-report to the developers (Not sure if I understand enough of the details to give a complete and correct report)? I guess this kind of thing should be reported as feedback.

---

### Post by chili555 on 2014-05-05
I encourage you to file a bug report. I'd simply say that, even though you have a desktop system with no wireless switch or key combination at all, 'rfkill list all' reports it as hard blocked. You will be asked for lots of additional information about your kernel, driver, hardware, etc. that will help the developers find a solution.

---

### Post by Katzwinkel on 2014-05-05
@Chili555: Turns out I can't download any xubuntu version before 12.04.4 anymore! The download link at the xubuntu website automatically redirects from 12.04 to 12.04.4.
I guess that means I'll just have to go on and remove the section of the driver code you suggested. But I'll do that tomorrow and then post the results. I MAY have to come back to you (or anybody who reads this) inbetween on how to recompile the driver, IF this is not covered in the links you supplied (or can I just run 'make' in the driver-folder?)
Thanks a lot, already!

---

### Post by chili555 on 2014-05-05
> MAY have to come back to you (or anybody who reads this) inbetween on how to recompile the driver, IF this is not covered in the links you supplied (or can I just run 'make' in the driver-folder?)It is far from that simple. I will write up a guide and post it in a few hours.

---

### Post by chili555 on 2014-05-05
Please download this file to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.14/backports-3.14-1.tar.xz](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.14/backports-3.14-1.tar.xz) Right-click it and select 'Extract Here.' Now, with a working internet connection, open a terminal and do:
    ```
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop/backports-3.14-1
make defconfig-wifi
make
sudo make install
```

We haven't changed anything yet; let's see if this later version fixes the issue. Reboot.

    ```
rfkill list all
sudo rfkill unblock all
rfkill list all
```

Any improvement? If not, let's change the code:

    ```
cd ~/Desktop/backports-3.14-1
make clean
gedit drivers/net/wireless/rt2x00/rt2500usb.c
```

Scroll down to line 1787, where it says:


	> /*
	 * Enable rfkill polling by setting GPIO direction of the
	 * rfkill switch GPIO pin correctly.
	 */
	rt2500usb_register_read(rt2x00dev, MAC_CSR19, &reg);
	rt2x00_set_field16(&reg, MAC_CSR19_DIR0, 0);
	rt2500usb_register_write(rt2x00dev, MAC_CSR19, reg);


Change it to:

> /*
	   * Enable rfkill polling by setting GPIO direction of the
	   * rfkill switch GPIO pin correctly.
	   * rt2500usb_register_read(rt2x00dev, MAC_CSR19, &reg);
	   * rt2x00_set_field16(&reg, MAC_CSR19_DIR0, 0);
	   * rt2500usb_register_write(rt2x00dev, MAC_CSR19, reg);
          */

...so that the entire section is now commented out. The asterisks must be perfectly aligned. Proofread carefully, save and close gedit. Now re-compile:

    ```
make defconfig-wifi
make
sudo make install.
```


Reboot. 

    ```
rfkill list all
sudo rfkill unblock all
rfkill list all
```

Any improvement?

---

### Post by Katzwinkel on 2014-05-08
Hi, its me again. Sorry for the late reply, but I was very busy the last days. 
Thanks for the instructions, chili555. They could not have been any more straightforward and clear. However, this still did not solve the problem. My WiFi is still being hardblocked in xubuntu.
Here the results of "rfkill list all" after i edited and recompiled the driver:
> 0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

---

### Post by Katzwinkel on 2014-05-08
By the way, I've just checkedwith the live version of Kubuntu, and the problem persists (so its not just a problem if xubuntu).
I really hope it's not the case that my wireless card can only ever work with windows systems. That would really suck!

---

### Post by chili555 on 2014-05-08
I am afraid I have no more suggestions aside from the obvious; replace the card or get 30 feet of CAT5 cable. I suggest you file a bug here: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

I deeply regret that I have no better answer.

---

### Post by Katzwinkel on 2014-05-09
Thats ok. You're probably right, and you were a great help anyway (but a network cable is sadly not a permanent option in my case).
However I still have some hope that i may be able to implement the original windows driver using Ndiswrapper or something similar. I'll see.
Thanks and bye.

---

### Post by nagendra_rao on 2014-07-23
> **Katzwinkel said:**
> Thats ok. You're probably right, and you were a great help anyway (but a network cable is sadly not a permanent option in my case).
However I still have some hope that i may be able to implement the original windows driver using Ndiswrapper or something similar. I'll see.
Thanks and bye.

Hey give this a shot,
Just Suspend the system and then resume back in, this will enable the wifi drivers if its not already enabled. 

This is very weird but it worked for me! [Ubuntu 14.04 LTS AMD64 on Asus laptop]

Let me know if it worked for you too.

---

### Post by gus_pappas on 2014-07-25
in "Software Center", type B43 in the search column, then download all three available items.

---

### Post by chili555 on 2014-07-25
> **gus_pappas said:**
> in "Software Center", type B43 in the search column, then download all three available items.The original poster doesn't have a Broadcom card. As well, some of the drivers conflict with the others. Downloading all three randomly without knowing the identity of the card is only likely to create a conflict that will have to be diagnosed and corrected later. I therefore find your post unproductive.

---

### Post by roland6 on 2014-08-17
As I have the same hardware (MachineType: MEDIONPC MS-7091 ) like  the  original poster,   I solved this issue by patching source code of module rt2500usb.c

```

static int rt2500usb_rfkill_poll(struct rt2x00_dev *rt2x00dev)
{
    u16 reg;

    rt2500usb_register_read(rt2x00dev, MAC_CSR19, &reg);
//     return rt2x00_get_field16(reg, MAC_CSR19_BIT7);
    return (int) 1;
}

```

recompiling kernel module is well explained here:
[http://www.codewhirl.com/2012/04/how-to-compile-a-single-module-in-ubuntu-linux/](http://www.codewhirl.com/2012/04/how-to-compile-a-single-module-in-ubuntu-linux/)

If your wifi card may become unaccessible very often, not allowing any data transfer, you have to disable power management also.
pls, see here:
[http://bernaerts.dyndns.org/linux/74-ubuntu/276-ubuntu-precise-ralink-rt2572](http://bernaerts.dyndns.org/linux/74-ubuntu/276-ubuntu-precise-ralink-rt2572)

---

### Post by kaspar42 on 2014-11-07
> **chili555 said:**
> Please let us see:```
cat /sys/class/rfkill/rfkill0/hard
```I suspect the result is 1. If so, please try:```
sudo -i
echo 0  >  /sys/class/rfkill/rfkill0/hard
exit
rfkill list all
```If that works, we'll write a quick file to make it persistent.

Hi

I have the same problem as OP:

```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

But in my case 
```
cat /sys/class/rfkill/rfkill0/hard
```
returns 1

and

```
sudo -i
echo 0  >  /sys/class/rfkill/rfkill0/hard

```

Returns permission denied.
No problem, chmod 744 should fix that..

But now I get this:

```
echo 0  >  /sys/class/rfkill/rfkill0/hard
-bash: echo: write error: Input/output error

```

Which almost sounds like a scary hardware error. 
What precipitated this problem was simply that I clicked on the wifi icon and unchecked 'enable wifi'. When after a reboot I tried to reenable it using the same method, it was greyed out.

---

### Post by jeremy31 on 2014-11-07
```
sudo rfkill unblock wifi
``` might work, if not run the wireless script and post the results.  The script can be found [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) run the command that begins with wget if you have internet access

---

### Post by kaspar42 on 2014-11-07
> **jeremy31 said:**
> ```
sudo rfkill unblock wifi
``` might work, if not run the wireless script and post the results.  The script can be found [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) run the command that begins with wget if you have internet access

```
sudo rfkill unblock wifi
```

Only works on the soft block.
I tried the script, and here are the results:

```

########## wireless info START ##########

Report from: 07 Nov 2014 13:41 CET +0100

Booted last: 07 Nov 2014 10:19 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

GNOME Flashback (Metacity)

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 05)
	Subsystem: Fujitsu Limited. Device [10cf:1574]
	Kernel driver in use: e1000e

10:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)
	Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1301]
	Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 004: ID 04f2:b186 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 08ff:2550 AuthenTec, Inc. AES2550 Fingerprint Sensor
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0458:0133 KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1="O2Micro
"
PRODID_2="SmartCardBus Reader
"
PRODID_3="V1.0
"
PRODID_4=""
MANFID=ffff,0001
FUNCID=255

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

##### lsmod #############################

iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:172.20.3.12  Bcast:172.20.255.255  Mask:255.255.0.0
          inet6 addr: fe80::8e73:6eff:feda:dcfc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:790863 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122023 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:342129220 (342.1 MB)  TX bytes:28491242 (28.4 MB)
          Interrupt:17 Memory:f2400000-f2420000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.20.0.1      0.0.0.0         UG    0      0        0 eth0
172.20.0.0      0.0.0.0         255.255.0.0     U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search fys.ku.dk

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         172.20.3.12
    Prefix:          16 (255.255.0.0)
    Gateway:         172.20.0.1

    DNS:             130.225.102.254
    DNS:             130.225.212.46

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/guesthouse]] (600 root)
[connection] id=guesthouse | type=802-11-wireless
[802-11-wireless] ssid=guesthouse | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/lps_EXT]] (600 root)
[connection] id=lps_EXT | type=802-11-wireless
[802-11-wireless] ssid=lps_EXT | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Copenhagen (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     CC4D1BA11C1EF73A6ABDE53
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     C2D0F3DFCA289585C100E36
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

rfkill block bluetooth
exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x10ea (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x422c (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   13.240740] iwlwifi 0000:10:00.0: Direct firmware load failed with error -2
[   13.240747] iwlwifi 0000:10:00.0: Falling back to user helper
[   13.241293] iwlwifi 0000:10:00.0: Direct firmware load failed with error -2
[   13.241296] iwlwifi 0000:10:00.0: Falling back to user helper
[   13.394345] iwlwifi 0000:10:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[   13.831725] iwlwifi 0000:10:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   13.831730] iwlwifi 0000:10:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   13.831732] iwlwifi 0000:10:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   13.831735] iwlwifi 0000:10:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   13.831782] iwlwifi 0000:10:00.0: L1 Enabled; Disabling L0S
[   13.831971] iwlwifi 0000:10:00.0: RF_KILL bit toggled to disable radio.
[   13.904064] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.892751] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```

---

### Post by chili555 on 2014-11-07
Jeremy and I also want to see all of:```
lsmod
```Also, we wonder if you've pressed the wireless key combination; Fn+F4 or some such, and if it, in any way, changes:```
rfkill list all
```

---

### Post by kaspar42 on 2014-11-07
Thanks for your answers.

Here is lsmod:
```
Module                  Size  Used by
btusb                  32412  0 
rfcomm                 69160  8 
bnep                   19624  2 
bluetooth             391136  22 bnep,btusb,rfcomm
binfmt_misc            17468  1 
nvidia              11334886  42 
arc4                   12608  2 
uvcvideo               80885  0 
iwldvm                232285  0 
intel_powerclamp       14705  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
coretemp               13435  0 
snd_hda_codec_hdmi     46368  4 
mac80211              630653  1 iwldvm
kvm_intel             143148  0 
kvm                   451729  1 kvm_intel
gpio_ich               13476  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
snd_hda_codec_realtek    65580  1 
iwlwifi               169932  1 iwldvm
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
pcmcia                 62299  0 
snd_hda_intel          56451  5 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
gf128mul               14951  1 lrw
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
glue_helper            13990  1 aesni_intel
yenta_socket           41027  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lpc_ich                21080  0 
snd_rawmidi            30144  1 snd_seq_midi
joydev                 17381  0 
mei_me                 18627  0 
intel_ips              18664  0 
serio_raw              13462  0 
mei                    82276  1 mei_me
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
mac_hid                13205  0 
pcmcia_rsrc            18407  1 yenta_socket
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
ppdev                  17671  0 
snd_timer              29482  2 snd_pcm,snd_seq
fujitsu_laptop         18947  0 
lp                     17759  0 
parport_pc             32701  1 
parport                42348  3 lp,ppdev,parport_pc
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
video                  19476  0 
soundcore              12680  1 snd
pcmcia_core            23592  3 pcmcia,pcmcia_rsrc,yenta_socket
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
psmouse               106714  0 
ahci                   25819  2 
libahci                32716  1 ahci
firewire_ohci          40409  0 
firewire_core          68769  1 firewire_ohci
e1000e                254433  0 
crc_itu_t              12707  1 firewire_core
sdhci_pci              23172  0 
sdhci                  43015  1 sdhci_pci
ptp                    18933  1 e1000e
pps_core               19382  1 ptp
```

There is no key combo printed on the keyboard, but there is a physical switch on the side.
 Switching that off and back on changes rfkill to:

```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```

However icon still says wifi disabled by hardware switch, and the enable button is greyed out.

---

### Post by kaspar42 on 2014-11-07
Ok, flipping the switch on and off, and then rebooting solved it. Now I feel silly for not think off that before I posted..

---

### Post by chili555 on 2014-11-07
We're happy it's working by whatever means!

---

### Post by christian-ribe-p on 2014-12-18
> **kaspar42 said:**
> ```
sudo rfkill unblock wifi
```

Only works on the soft block.
I tried the script, and here are the results:

```

########## wireless info START ##########

Report from: 07 Nov 2014 13:41 CET +0100

Booted last: 07 Nov 2014 10:19 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

GNOME Flashback (Metacity)

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 05)
    Subsystem: Fujitsu Limited. Device [10cf:1574]
    Kernel driver in use: e1000e

10:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1301]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 004: ID 04f2:b186 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 08ff:2550 AuthenTec, Inc. AES2550 Fingerprint Sensor
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0458:0133 KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1="O2Micro
"
PRODID_2="SmartCardBus Reader
"
PRODID_3="V1.0
"
PRODID_4=""
MANFID=ffff,0001
FUNCID=255

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:172.20.3.12  Bcast:172.20.255.255  Mask:255.255.0.0
          inet6 addr: fe80::8e73:6eff:feda:dcfc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:790863 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122023 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:342129220 (342.1 MB)  TX bytes:28491242 (28.4 MB)
          Interrupt:17 Memory:f2400000-f2420000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.20.0.1      0.0.0.0         UG    0      0        0 eth0
172.20.0.0      0.0.0.0         255.255.0.0     U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search fys.ku.dk

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         172.20.3.12
    Prefix:          16 (255.255.0.0)
    Gateway:         172.20.0.1

    DNS:             130.225.102.254
    DNS:             130.225.212.46

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/guesthouse]] (600 root)
[connection] id=guesthouse | type=802-11-wireless
[802-11-wireless] ssid=guesthouse | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/lps_EXT]] (600 root)
[connection] id=lps_EXT | type=802-11-wireless
[802-11-wireless] ssid=lps_EXT | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Copenhagen (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     CC4D1BA11C1EF73A6ABDE53
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     C2D0F3DFCA289585C100E36
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

rfkill block bluetooth
exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x10ea (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x422c (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   13.240740] iwlwifi 0000:10:00.0: Direct firmware load failed with error -2
[   13.240747] iwlwifi 0000:10:00.0: Falling back to user helper
[   13.241293] iwlwifi 0000:10:00.0: Direct firmware load failed with error -2
[   13.241296] iwlwifi 0000:10:00.0: Falling back to user helper
[   13.394345] iwlwifi 0000:10:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[   13.831725] iwlwifi 0000:10:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   13.831730] iwlwifi 0000:10:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   13.831732] iwlwifi 0000:10:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   13.831735] iwlwifi 0000:10:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   13.831782] iwlwifi 0000:10:00.0: L1 Enabled; Disabling L0S
[   13.831971] iwlwifi 0000:10:00.0: RF_KILL bit toggled to disable radio.
[   13.904064] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.892751] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```

It seems running the command:
sudo rfkill unblock wifi

Solved my problem  !!!! Thanks !!!!

---

### Post by janeeps on 2014-12-31
Hi! I'm also having the problem in Lenovo G40-30 as I'm trying to install Xubuntu 14.04 LTS.
First, here's some information on my wireless card.
```
sudo lshw -class network
```
  *-network               
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: b8:ee:65:7d:cf:dd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-32-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:90500000-9057ffff memory:90580000-9058ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 28:d2:44:8b:da:e0
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.2.41 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:105 ioport:1000(size=256) memory:90404000-90404fff memory:90400000-90403fff
```

rfkill list all
```
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```
lsmod
```
Module                  Size  Used by
dm_crypt               22589  0 
intel_rapl             18301  0 
coretemp               13195  0 
arc4                   12536  2 
snd_hda_codec_hdmi     45342  1 
kvm                   388083  0 
snd_hda_codec_conexant    47785  1 
ath9k                 144602  0 
crc32_pclmul           12967  0 
ath9k_common           13359  1 ath9k
snd_hda_intel          42730  6 
rts5139               269330  0 
snd_hda_codec         164067  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
dm_multipath           22402  0 
uvcvideo               71309  0 
scsi_dh                14458  1 dm_multipath
ath9k_hw              438205  2 ath9k_common,ath9k
snd_hwdep              13272  1 snd_hda_codec
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
ath3k                  13110  0 
videodev              108503  2 uvcvideo,videobuf2_core
snd_pcm                85501  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
mac80211              546051  1 ath9k
btusb                  27580  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
serio_raw              13230  0 
cfg80211              409394  3 ath,ath9k,mac80211
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
ideapad_laptop         17872  0 
sparse_keymap          13708  1 ideapad_laptop
snd                    60871  23 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
rfcomm                 53664  12 
bnep                   18895  2 
bluetooth             342206  23 bnep,ath3k,btusb,rfcomm
soundcore              12600  1 snd
mac_hid                13037  0 
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
squashfs               42874  1 
overlayfs              27158  1 
nls_iso8859_1          12617  1 
dm_mirror              21756  0 
dm_region_hash         20121  1 dm_mirror
dm_log                 18072  2 dm_region_hash,dm_mirror
hid_generic            12492  0 
usbhid                 46997  0 
usb_storage            48417  1 
hid                    87604  2 hid_generic,usbhid
i915                  705659  3 
r8169                  61562  0 
ahci                   25579  0 
psmouse                91329  0 
i2c_algo_bit           13197  1 i915
drm_kms_helper         47182  1 i915
mii                    13654  1 r8169
drm                   244037  4 i915,drm_kms_helper
libahci                27082  1 ahci
video                  18903  1 i915

I have tried these steps so far but still can't solve the problem.
[I]
1) Searching for additional drivers in Software & Updates[/I]
It simply says "No additional drivers are available."

*2) Pressing the Fn+F7 key (I think it's Airplane Mode since it displays an airplane on the button.)*
From airplane mode on to off, **rfkill list all** displays:
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes -> no
    Hard blocked: yes 
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: yes -> no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

*3) Switching the Wireless in my BIOS on/off.*
ideapad_wlan will not be displayed in **rfkill list all** if Wireless is off in BIOS. Turning it on doesn't solve the problem.

*4) I tried code posted by **@chili555**.*```
xubuntu@xubuntu:~$ cat /sys/class/rfkill/rfkill0/hard
1
xubuntu@xubuntu:~$ cat /sys/class/rfkill/rfkill0/state
2
xubuntu@xubuntu:~$ sudo echo 0 > /sys/class/rfkill/rfkill0/hard
bash: /sys/class/rfkill/rfkill0/hard: Permission denied
```



This leads me to think that the wireless card is blocked in other operating systems except for Windows 8. Since the wireless interface has width: 64 bits, I'll try to get a 64 bit version of Xubuntu and see if I still have the problem. If anyone can provide some input, especially about the code in #4, please do. Thanks!

---

### Post by jeremy31 on 2014-12-31
> **janeeps said:**
> Hi! I'm also having the problem in Lenovo G40-30 as I'm trying to install Xubuntu 14.04 LTS.
First, here's some information on my wireless card.
```
sudo lshw -class network
  *-network               
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: b8:ee:65:7d:cf:dd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-32-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:90500000-9057ffff memory:90580000-9058ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 28:d2:44:8b:da:e0
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.2.41 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:105 ioport:1000(size=256) memory:90404000-90404fff memory:90400000-90403fff
```
```

rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```
```
lsmod
Module                  Size  Used by
dm_crypt               22589  0 
intel_rapl             18301  0 
coretemp               13195  0 
arc4                   12536  2 
snd_hda_codec_hdmi     45342  1 
kvm                   388083  0 
snd_hda_codec_conexant    47785  1 
ath9k                 144602  0 
crc32_pclmul           12967  0 
ath9k_common           13359  1 ath9k
snd_hda_intel          42730  6 
rts5139               269330  0 
snd_hda_codec         164067  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
dm_multipath           22402  0 
uvcvideo               71309  0 
scsi_dh                14458  1 dm_multipath
ath9k_hw              438205  2 ath9k_common,ath9k
snd_hwdep              13272  1 snd_hda_codec
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
ath3k                  13110  0 
videodev              108503  2 uvcvideo,videobuf2_core
snd_pcm                85501  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
mac80211              546051  1 ath9k
btusb                  27580  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
serio_raw              13230  0 
cfg80211              409394  3 ath,ath9k,mac80211
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
ideapad_laptop         17872  0 
sparse_keymap          13708  1 ideapad_laptop
snd                    60871  23 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
rfcomm                 53664  12 
bnep                   18895  2 
bluetooth             342206  23 bnep,ath3k,btusb,rfcomm
soundcore              12600  1 snd
mac_hid                13037  0 
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
squashfs               42874  1 
overlayfs              27158  1 
nls_iso8859_1          12617  1 
dm_mirror              21756  0 
dm_region_hash         20121  1 dm_mirror
dm_log                 18072  2 dm_region_hash,dm_mirror
hid_generic            12492  0 
usbhid                 46997  0 
usb_storage            48417  1 
hid                    87604  2 hid_generic,usbhid
i915                  705659  3 
r8169                  61562  0 
ahci                   25579  0 
psmouse                91329  0 
i2c_algo_bit           13197  1 i915
drm_kms_helper         47182  1 i915
mii                    13654  1 r8169
drm                   244037  4 i915,drm_kms_helper
libahci                27082  1 ahci
video                  18903  1 i915

```
I have tried these steps so far but still can't solve the problem.
[I]
1) Searching for additional drivers in Software & Updates[/I]
It simply says "No additional drivers are available."

*2) Pressing the Fn+F7 key (I think it's Airplane Mode since it displays an airplane on the button.)*
From airplane mode on to off, **rfkill list all** displays:
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes -> no
    Hard blocked: yes 
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: yes -> no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

*3) Switching the Wireless in my BIOS on/off.*
ideapad_wlan will not be displayed in **rfkill list all** if Wireless is off in BIOS. Turning it on doesn't solve the problem.

*4) I tried code posted by **@chili555**.*```
xubuntu@xubuntu:~$ cat /sys/class/rfkill/rfkill0/hard
1
xubuntu@xubuntu:~$ cat /sys/class/rfkill/rfkill0/state
2
xubuntu@xubuntu:~$ sudo echo 0 > /sys/class/rfkill/rfkill0/hard
bash: /sys/class/rfkill/rfkill0/hard: Permission denied
```



This leads me to think that the wireless card is blocked in other operating systems except for Windows 8. Since the wireless interface has width: 64 bits, I'll try to get a 64 bit version of Xubuntu and see if I still have the problem. If anyone can provide some input, especially about the code in #4, please do. Thanks!

You might want to try this ```
sudo modprobe -r ideapad_laptop
``````
sudo rfkill unblock all
``` and see if the rfkill state changes

Edit, this might not work without patching the ideapad_laptop

---

### Post by janeeps on 2014-12-31
> **jeremy31 said:**
> You might want to try this ```
sudo modprobe -r ideapad_laptop
``````
sudo rfkill unblock all
``` and see if the rfkill state changes

Edit, this might not work without patching the ideapad_laptop

Wow, I can't believe those two lines of code fixed the problem. Thank you very much!

---

### Post by jeremy31 on 2014-12-31
> **janeeps said:**
> Wow, I can't believe those two lines of code fixed the problem. Thank you very much!

Since it works, you might want to do this ```
echo "blacklist ideapad_laptop" | sudo tee /etc/modprobe.d/ideapad_laptop.conf
```

---

### Post by janeeps on 2015-01-02
> **jeremy31 said:**
> Since it works, you might want to do this ```
echo "blacklist ideapad_laptop" | sudo tee /etc/modprobe.d/ideapad_laptop.conf
```

Already done. Thank you!

---

### Post by aqualeak2 on 2015-02-01
> **nagendra_rao said:**
> 
[FONT=Verdana]Just Suspend the system and then resume back in, this will enable the wifi drivers if its not already enabled. [/FONT]

[FONT=Verdana]This is very weird but it worked for me! [Ubuntu 14.04 LTS AMD64 on Asus laptop][/FONT]

[FONT=Verdana]Let me know if it worked for you too.[/FONT]

[FONT=Verdana]Worked for me but I have to do it each time I turn the computer on.[/FONT]
[FONT=Verdana]tried [/FONT][COLOR=#000000][FONT=Ubuntu Mono]sudo rfkill unblock all[/FONT][/COLOR][FONT=Verdana] : it turns the wifi back off (with the wifi is disables by hardware switch message)[/FONT]
[COLOR=#000000][FONT=Ubuntu Mono]
cat /sys/class/rfkill/rfkill0/hard[/FONT][/COLOR][FONT=Verdana] does return 1 [/FONT][FONT=Verdana]on start up but 0 after suspending and wakeup
[/FONT]
echo 0  >  /sys/class/rfkill/rfkill0/hard
-bash: /sys/class/rfkill/rfkill0/hard: Permission non accordée

[FONT=arial]any ideas for a permanent fix? I don't want to recompile the kernel because this isn't my own laptop[/FONT] and it's owner insn't tech-savvy.
[FONT=Verdana]

[/FONT]

---

### Post by chili555 on 2015-02-01
> **aqualeak2 said:**
> [FONT=Verdana]Worked for me but I have to do it each time I turn the computer on.[/FONT]
[FONT=Verdana]tried [/FONT][COLOR=#000000][FONT=Ubuntu Mono]sudo rfkill unblock all[/FONT][/COLOR][FONT=Verdana] : it turns the wifi back off (with the wifi is disables by hardware switch message)[/FONT]
[COLOR=#000000][FONT=Ubuntu Mono]
cat /sys/class/rfkill/rfkill0/hard[/FONT][/COLOR][FONT=Verdana] does return 1 [/FONT][FONT=Verdana]on start up but 0 after suspending and wakeup
[/FONT]
echo 0  >  /sys/class/rfkill/rfkill0/hard
-bash: /sys/class/rfkill/rfkill0/hard: Permission non accordée

[FONT=arial]any ideas for a permanent fix? I don't want to recompile the kernel because this isn't my own laptop[/FONT] and it's owner insn't tech-savvy.
[FONT=Verdana]

[/FONT]Does it work if you do:```
sudo -i
echo 0  >  /sys/class/rfkill/rfkill0/hard
exit
```Also, what kind of laptop is it? May we see:```
lsmod
```

---

### Post by Kendon_Bell on 2015-02-26
I am having the same problem:

```

root@kendon-Qosmio-X500:~# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@kendon-Qosmio-X500:~# lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39835  1 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391196  10 bnep,rfcomm
snd_hda_codec_hdmi     46254  4 
arc4                   12608  2 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_hda_codec_conexant    57441  1 
snd_hda_intel          52355  4 
coretemp               13435  0 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
kvm_intel             143060  0 
snd_seq_midi           13324  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
kvm                   451511  1 kvm_intel
snd_seq_midi_event     14899  1 snd_seq_midi
rtl8192se              63196  0 
snd_rawmidi            30144  1 snd_seq_midi
rtl_pci                26690  1 rtl8192se
rtlwifi                63475  2 rtl_pci,rtl8192se
joydev                 17381  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192se
serio_raw              13462  0 
i7core_edac            24122  0 
edac_core              62291  1 i7core_edac
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
nvidia              10744943  43 
lpc_ich                21080  0 
cfg80211              484040  2 mac80211,rtlwifi
snd                    69238  19 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   303102  2 nvidia
soundcore              12680  1 snd
toshiba_acpi           22901  0 
sparse_keymap          13948  1 toshiba_acpi
shpchp                 37032  0 
toshiba_bluetooth      12852  0 
wmi                    19177  1 toshiba_acpi
parport_pc             32701  0 
video                  19476  0 
mac_hid                13205  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
firewire_ohci          40409  0 
psmouse               106678  0 
ahci                   25819  3 
sdhci_pci              23172  0 
firewire_core          68769  1 firewire_ohci
atl1c                  46086  0 
libahci                32560  1 ahci
sdhci                  43015  1 sdhci_pci
crc_itu_t              12707  1 firewire_core

```

Doing sudo rfkill unblock wifi does not work.

---

### Post by chili555 on 2015-02-26
> **Kendon_Bell said:**
> I am having the same problem:

```

root@kendon-Qosmio-X500:~# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@kendon-Qosmio-X500:~# lsmod
Module                  Size  Used by
<snip>
toshiba_acpi           22901  0 
sparse_keymap          13948  1 toshiba_acpi


```

Doing sudo rfkill unblock wifi does not work.Does it change to unload the acpi driver?```
sudo modprobe -r toshiba_acpi
sudo rfkill unblock all
rfkill list all
```If it helps, we'll blacklist it.

---

### Post by jeremy31 on 2015-02-27
> **Kendon_Bell said:**
> I am having the same problem:

```

root@kendon-Qosmio-X500:~# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@kendon-Qosmio-X500:~# lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39835  1 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391196  10 bnep,rfcomm
snd_hda_codec_hdmi     46254  4 
arc4                   12608  2 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_hda_codec_conexant    57441  1 
snd_hda_intel          52355  4 
coretemp               13435  0 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
kvm_intel             143060  0 
snd_seq_midi           13324  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
kvm                   451511  1 kvm_intel
snd_seq_midi_event     14899  1 snd_seq_midi
rtl8192se              63196  0 
snd_rawmidi            30144  1 snd_seq_midi
rtl_pci                26690  1 rtl8192se
rtlwifi                63475  2 rtl_pci,rtl8192se
joydev                 17381  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192se
serio_raw              13462  0 
i7core_edac            24122  0 
edac_core              62291  1 i7core_edac
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
nvidia              10744943  43 
lpc_ich                21080  0 
cfg80211              484040  2 mac80211,rtlwifi
snd                    69238  19 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   303102  2 nvidia
soundcore              12680  1 snd
toshiba_acpi           22901  0 
sparse_keymap          13948  1 toshiba_acpi
shpchp                 37032  0 
toshiba_bluetooth      12852  0 
wmi                    19177  1 toshiba_acpi
parport_pc             32701  0 
video                  19476  0 
mac_hid                13205  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
firewire_ohci          40409  0 
psmouse               106678  0 
ahci                   25819  3 
sdhci_pci              23172  0 
firewire_core          68769  1 firewire_ohci
atl1c                  46086  0 
libahci                32560  1 ahci
sdhci                  43015  1 sdhci_pci
crc_itu_t              12707  1 firewire_core

```

Doing sudo rfkill unblock wifi does not work.

There appears to be a switch on the front left near the built in memory card slot, does this change the rfkill results?
[IMG]http://cdn.slashgear.com/wp-content/uploads/2009/09/Qosmio-X500_straight.jpg[/IMG]

---

### Post by bharat10 on 2015-02-28
Hi, I have ubuntu 14.04 installed. All was going well untill I changed the hostname and then wifi stopped working with the error "wifi is disabled by hardware switch". I had changed the host name in the following files

/etc/hosts
/etc/hostname

Any solution to the problem.

---

### Post by bellera on 2015-03-24
Sometimes not button problem... So, no solution using/testing with rfkill

I don't know why but I found some machines with Network Manager state [B]WirelessEnabled=false
[/B]
Solution:

sudo gedit /var/lib/NetworkManager/NetworkManager.state

Change line **WirelessEnabled=false** by **WirelessEnabled=True**

Save changes and restart NetworkManager service:

sudo service network-manager restart

That's all!

---

### Post by ian-weisser on 2015-03-24
If you discover any error message that falsely indicates 'hardware switch' when the real cuplrit is a Network Manager setting, please file a bug report with enough detail for us to reproduce the event. We can fix that.

Petty stuff: [Avoid instructions with 'sudo gedit']("http://ubuntuforums.org/showthread.php?t=2269093").

---

### Post by user_frank on 2015-07-27
If the BIOS does not have the on/off option for the WiFi module you can try loading the default configuration and save the settings. Generally the WiFi module is enabled by default.

---

### Post by Ermyas on 2015-12-25
first check that its manually disable with function key "fn + f12" before you proced to other steps.

---

