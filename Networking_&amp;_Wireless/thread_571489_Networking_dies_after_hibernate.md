---
title: "Networking dies after hibernate"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by Xyhthyx on 2007-10-09
After coming back from hibernate, my eth0 is gone and /etc/init.d/networking restart doesn't bring it back, forcing me to reboot to get back up (making hibernating in the first place pointless).

Contents of /etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth1
iface eth1 inet dhcp

```

Is it me, or is that missing an "iface eth0 inet dhcp"? Note: I have a wireless card (bcm4306) but I currently have the bcm43xx module blacklisted.

---

### Post by KaYnemO on 2007-10-09
> **Xyhthyx said:**
> After coming back from hibernate, my eth0 is gone and /etc/init.d/networking restart doesn't bring it back, forcing me to reboot to get back up (making hibernating in the first place pointless).

Contents of /etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth1
iface eth1 inet dhcp

```

Is it me, or is that missing an "iface eth0 inet dhcp"? Note: I have a wireless card (bcm4306) but I currently have the bcm43xx module blacklisted.

Actually the same thing happens with me when I am wireless. When I have a wired connection, after resturning from hybernation, it just takes a few seconds for the machine to relogin to the network, but if I was on WiFi - system never actually returns to the network. I would love for some one to help us both out with this, 'cause you're right, this situation renders the hybernation completely pointless.! This is what my /etc/network/interfaces show:
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp

auto eth0

```

---

### Post by rustybronco on 2007-10-09
I'm not the best but until they come, See if anything in this may help.

[https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=wireless+hibernation&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=wireless+hibernation&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

or provide details on your os of choice and nic card.

***edit***
Paying attention to...
```
Please include the following additional information, if you have not already done so (please pay attention to lspci's additional options), as required by the Ubuntu Kernel Team:
1. Please include the output of the command 'uname -a' in your next response. It should be one, long line of text which includes the exact kernel version you're running, as well as the CPU architecture.
2. Please run the command 'dmesg > dmesg.log' and attach the resulting file 'dmesg.log' to this bug report.
3. Please run the command 'sudo lspci -vvnn > lspci-vvnn.log' and attach the resulting file 'lspci-vvnn.log' to this bug report.
For your reference, the full description of procedures for kernel-related bug reports is available at https://wiki.ubuntu.com/KernelTeamBugPolicies . Thanks in advance!
```

---

### Post by KaYnemO on 2007-10-09
hey hey!
here we go.

1. uname -a :
> Linux kaynemo-lappie 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

2. with the acttachments - no go - the files are too big for the forum.. :(

---

### Post by rustybronco on 2007-10-09
bare with me please it's not something I normally do (noobie)...

post the output of lspci in a terminal.

---

### Post by KaYnemO on 2007-10-09
no problem:

> ~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


---

### Post by rustybronco on 2007-10-09
"...if only there was an UNDO in real life..."

You don't know how true that is, my father lives in Crandon, Wi. I just got off the phone with him, he knew all the kids that were shot and the Police officer that shot them.

In between things I have to do, let me see what I can find out to help.

---

### Post by KaYnemO on 2007-10-09
> **rustybronco said:**
> "...if only there was an UNDO in real life..."

You don't know how true that is, my father lives in Crandon, Wi. I just got off the phone with him, he knew all the kids that were shot and the Police officer that shot them.

In between things I have to do, let me see what I can find out to help.

I am so shocked to read about that! That is sooo nuts! My condolences. Take your time and thanx

---

### Post by rustybronco on 2007-10-09
I'm back!

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/130457](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/130457)

> 

I have this same bug. Occasional SysRq hard locks or suspend failures. 3945ABG specific as it does not occur with a different wireless card in same laptop.

LSPCI:
 0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

HAL quirck checker output
./quirk-checker.sh
-e Checking your system...

WARNING: You have no quirks!
WARNING: Using broadcom network driver.
CRITICAL ERROR: Use the mac80211 based iwl3945 driver instead. ipw3945d is closed source sometimes hangs on resume.

Let me know if there is any additional info needed.

It's in gutsy, but it's a start , more to come when I can ( working on my x's atv).


didn't get to the atv yet (wife wanted to go shopping and I needed more cd's)
[http://ubuntuforums.org/showthread.php?t=461294&highlight=hibernation+3945ABG](http://ubuntuforums.org/showthread.php?t=461294&highlight=hibernation+3945ABG)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107636](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107636)
looks like the kernel acpi team knows about it.

very similar to your spec's
[http://klamstwo.org/evad/archives/3](http://klamstwo.org/evad/archives/3)
> Power management

Battery life is a bit dissapointing. Fully charged battery allow to work about 2.5 hours away from AC power, with WiFi/BT switched on, LCD backlight dimmed and CPU speed managed by Ondemand governor (mostly at 1 GHz speed per CPU). Well, I must say I expected around 3 hours at least&#8230;

Hibernation works! Hibernating process takes a while and is a bit confusing - screen is switched off initially and then switched back on after some time, while some messages are flooding screen, and then finally switched off together with whole machine. After restarting, screen is flooded with bunch of error-like messages, but after a while&#8230; desktop hops back on the screen with all applications running. NetworkManager also picks up wireless network back, so the system is back in the business!
[UPDATE] My second approach to hibernation revealed it does not work properly. After displaying some messages about &#8217;shrinking memory&#8217; (afair), screen went off but machine was still on&#8230; forever. I mean, after few minutes anything changed, so basically I had to reset it manually. :(
Suspend mode is working, but not perfectly. Computer suspends and resumes quite quickly, but after resume wireless adapter doesn&#8217;t work. However, getting it back is just matter of restarting ipw3495d and NetworkManager services.
[UPDATE] Actually, there&#8217;s no need for restarting services. Easier and faster way is just right-click on NetworkManager tray-icon, disable networking and enable back again. There&#8217;s also one small issue with sound driver after resume, but i.e. changing volume one step up or down brings sound back.
[UPDATE2] After I stopped using NetworkManager, in favour of WiFi Radar, I don&#8217;t have to restart anything at all, in order to have wireless connection back after resume! It just works straight away. NetworkManager was problematic (not only in matter of resuming after suspend), so I just dumped it.

What is you laptop model?

---

### Post by rustybronco on 2007-10-09
Time to update gutsy and look for bugs.
until tommorow...

---

### Post by rustybronco on 2007-10-10
Today is tommorow.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114490](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114490)

>  Thomas de Graaff wrote on 2007-06-17: (permalink) 
My computer with Xubuntu feisty had a problem with getting an ip-adress after waking from hibernation. I´ve solved this problem by changing /etc/default/acpi-support

Editing this file, look for the line below, where to add [networking] after that no problems anymore:

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="networking"

Hope this will work for you to,
Thomas.

>  NT wrote on 2007-06-22: (permalink) 
This worked for me. Thanks!
 lalaland wrote on 2007-07-22: (permalink) 
Seems to have fixed the issue for me, too. But I think the real problem is somewhere else...
 GGrigsby wrote on 2007-07-23: (permalink) 
I'm running Feisty on a Dell Inspiron 9300 with a Intel 2200BG radio. When Feisty recovers from hibernate I have the exact same problem. When I try to connect to via wireless I get a eth1 not ready. rmmod'ing the module and re-adding it does not resolve the issue. Neither does restarting networking. Adding the STOP_SERVICES="networking" does resolve the issue.

I would suspect that networking is not properly stopped  upon suspend. 

your turn now...
changing /etc/default/acpi-support
Adding the STOP_SERVICES="networking"

---

### Post by KaYnemO on 2007-10-10
> **rustybronco said:**
> Today is tommorow.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114490](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114490)





I would suspect that networking is not properly stopped  upon suspend. 

your turn now...
changing /etc/default/acpi-support
Adding the STOP_SERVICES="networking"

You know - I tried all of the above. And it is still a bit buggy - the only way to get the network back on is to manually shut down the wifi (ther is a button for that on my notebook) and then turn it on - the network manager restarts and I am back - that is actually good enough for me!

---

### Post by rustybronco on 2007-10-10
If you would like to go further with it post the model of your laptop.

---

### Post by KaYnemO on 2007-10-10
> **rustybronco said:**
> If you would like to go further with it post the model of your laptop.

Acer Aspire 5670

---

### Post by blu3ness on 2007-10-11
I'll second this post also, it appears that my BCOM4318 Wireless card just dies after hibernation..

Have to go into windows to restart it...

I have a compaq presario v5100 laptop.

---

### Post by rustybronco on 2007-10-11
> **KaYnemO said:**
> Acer Aspire 5670

> **blu3ness said:**
> I'll second this post also, it appears that my BCOM4318 Wireless card just dies after hibernation..

Have to go into windows to restart it...

I have a compaq presario v5100 laptop.
I'll see what I can do when time permits, todays project ROOT CANAL.

---

### Post by rustybronco on 2007-10-11
> **KaYnemO said:**
> Acer Aspire 5670 And the problem is in hibernate NOT suspend, correct?

also how about with the wireless switch on or off before hibernation?

---

### Post by KaYnemO on 2007-10-11
> **rustybronco said:**
> And the problem is in hibernate NOT suspend, correct?

also how about with the wireless switch on or off before hibernation?
 You know, man, I just realized with horror that all this time I actually meant SUSPEND and not HYBERNATE. hmmm

---

### Post by blu3ness on 2007-10-11
Hmm... Let's see if suspend helps it.. then :O, i guess i can work with suspend for the time being.

---

### Post by rustybronco on 2007-10-12
> **KaYnemO said:**
> You know, man, I just realized with horror that all this time I actually meant SUSPEND and not HYBERNATE. hmmmIt's a whole different animal, I wanted to make sure before I put time in it.

OP, are you still with us?

---

### Post by rustybronco on 2007-10-12
[https://bugs.launchpad.net/ubuntu/+source/powersave/+bug/94133](https://bugs.launchpad.net/ubuntu/+source/powersave/+bug/94133)

Check... Also a patch which fixes the script at   "  /usr/lib/powersave/scripts/sleep_helper_functions   "   to use modprobe -r instead of rmmod: 
and see what yours says.

Reading material,  [https://bugzilla.novell.com/show_bug.cgi?id=212696](https://bugzilla.novell.com/show_bug.cgi?id=212696)

---

### Post by KaYnemO on 2007-10-12
> **rustybronco said:**
> [https://bugs.launchpad.net/ubuntu/+source/powersave/+bug/94133](https://bugs.launchpad.net/ubuntu/+source/powersave/+bug/94133)

Check... Also a patch which fixes the script at   "  /usr/lib/powersave/scripts/sleep_helper_functions   "   to use modprobe -r instead of rmmod: 
and see what yours says.

Reading material,  [https://bugzilla.novell.com/show_bug.cgi?id=212696](https://bugzilla.novell.com/show_bug.cgi?id=212696)

Thanks for the clues - started reading through all that and had to stop - no time right now. Maybe when my family sleeps I'll try to get on it. I'll post the outcome.

---

### Post by rustybronco on 2007-10-12
Great... if not I'll have to study a lot more to help, but help I will.

---

