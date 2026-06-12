---
title: "centrino intel pro wireless problem on fresh install"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by jewbolt on 2008-09-03
Thanks in advance.

I've installed the latest Ubuntu onto my Old Targa C50 Intel Centrino laptop, with an Intel Pro/Wireless. The wireless does not work. In fact, I'm not sure that the installed driver has any notion of it's wireless abilities.

Getting the wireless to work in XP required an ezButton utility to get the easy buttons to work (which seemed to power on/off the wireless device). I assume it's the antenna that is being powered on/off. Anyway, looking through the Ubuntu FAQ presented a number of options to explore, but I'm not sure which avenue to pursue. 

Here is some Ubuntu info from my laptop:
======
jewbolt@jewbolt-laptop:/var/log$ uname -a
Linux jewbolt-laptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
======
jewbolt@jewbolt-laptop:/var/log$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
======
jewbolt@jewbolt-laptop:/var/log$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:01.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
02:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
02:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 02)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
======

I read that hwinfo was a useful utility to install, so here is some info from that:

  81: udi = '/org/freedesktop/Hal/devices/pci_8086_1043'
  pci.device_subclass = 128 (0x80)
  pci.device_protocol = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0'
  info.subsystem = 'pci'
  pci.vendor = 'Intel Corporation'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2448'
  info.vendor = 'Intel Corporation'
  info.product = 'PRO/Wireless LAN 2100 3B Mini PCI Adapter'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0'
  pci.product = 'PRO/Wireless LAN 2100 3B Mini PCI Adapter'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1043'
  info.linux.driver = 'ipw2100'
  pci.subsys_vendor = 'Intel Corporation'
  pci.product_id = 4163 (0x1043)
  linux.hotplug_type = 2 (0x2)
  pci.vendor_id = 32902 (0x8086)
  linux.subsystem = 'pci'
  pci.subsys_product_id = 9511 (0x2527)
  pci.subsys_product = 'MIM2000/Centrino'
  pci.subsys_vendor_id = 32902 (0x8086)
  pci.device_class = 2 (0x2)

  82: udi = '/org/freedesktop/Hal/devices/ipw_wlan_switch'
  org.freedesktop.Hal.Device.KillSwitch.method_names = { 'SetPower', 'GetPower' }
  org.freedesktop.Hal.Device.KillSwitch.method_signatures = { 'b', '' }
  info.subsystem = 'unknown'
  org.freedesktop.Hal.Device.KillSwitch.method_argnames = { 'power', '' }
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1043'
  info.product = 'Intel PRO/Wireless WLAN Switch'
  org.freedesktop.Hal.Device.KillSwitch.method_execpaths = { 'hal-system-killswitch-set-power', 'hal-system-killswitch-get-power' }
  info.udi = '/org/freedesktop/Hal/devices/ipw_wlan_switch'
  info.capabilities = { 'killswitch' }
  info.category = 'killswitch'
  killswitch.type = 'wlan'
  killswitch.access_method = 'ipw'
  info.interfaces = { 'org.freedesktop.Hal.Device.KillSwitch' }
======

Any direction on how to proceed would be greatly appreciated.

---

### Post by pytheas22 on 2008-09-03
The card seems to be detected and up, according to iwconfig, although as you say it's possible that the radio is switched off.  Are you unable to see networks?  Please post the output of these commands:
```

dmesg | grep -e ipw -e iwl -e eth1
lshw -C Network
iwlist scan
```

---

### Post by jewbolt on 2008-09-03
Thanks for you help. Here is the output you requested:

jewbolt@jewbolt-laptop:~$ dmesg | grep -e ipw -e iwl -e eth1
[   30.247469] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   30.247474] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   30.593555] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   33.275444] eth1: Radio is disabled by RF switch.
======

jewbolt@jewbolt-laptop:~$ sudo lshw -C Network
  *-network:0 DISABLED    
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth1
       version: 04
       serial: 00:04:23:73:d9:22
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 link=no maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:40:ca:c5:b7:7f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.24.90 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
======

jewbolt@jewbolt-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
======

If the network driver and config is correct, then I guess the RF switch is what I should focus on.

When I press the button that turns the wireless on/off the LED associated with the button does not turn on and the following is reported in /var/logs/messages:
jewbolt@jewbolt-laptop:~$ tail -f /var/log/messages
Sep  4 10:23:43 jewbolt-laptop kernel: [  661.668796] atkbd.c: Unknown key pressed (translated set 2, code 0x66 on isa0060/serio0).
Sep  4 10:23:43 jewbolt-laptop kernel: [  661.668811] atkbd.c: Use 'setkeycodes 66 <keycode>' to make it known.
Sep  4 10:23:43 jewbolt-laptop kernel: [  661.896541] atkbd.c: Unknown key released (translated set 2, code 0x66 on isa0060/serio0).
Sep  4 10:23:43 jewbolt-laptop kernel: [  661.896555] atkbd.c: Use 'setkeycodes 66 <keycode>' to make it known.
Sep  4 10:23:48 jewbolt-laptop kernel: [  666.654584] atkbd.c: Unknown key pressed (translated set 2, code 0x66 on isa0060/serio0).
Sep  4 10:23:48 jewbolt-laptop kernel: [  666.654599] atkbd.c: Use 'setkeycodes 66 <keycode>' to make it known.
Sep  4 10:23:48 jewbolt-laptop kernel: [  666.897502] atkbd.c: Unknown key released (translated set 2, code 0x66 on isa0060/serio0).
Sep  4 10:23:48 jewbolt-laptop kernel: [  666.897514] atkbd.c: Use 'setkeycodes 66 <keycode>' to make it known.
======

Should I focus on the RF switch? If so, how do I do this?

---

### Post by pytheas22 on 2008-09-04
Yes, it's definitely the RF switch at fault, since dmesg says:
```

eth1: Radio is disabled by RF switch.
```

All those complaints about "unknown key code" suggest that for some reason the system doesn't recognize the button that you're pressing to enable the wireless.  I googled a bit and couldn't find anything useful--this seems to be a generic error not related specifically to wireless.

There may be a way to force the radio to come on without using the switch--the documentation [here]("http://www.hr.kernel.org/pub/linux/kernel/people/akpm/patches/2.6/2.6.13-rc4/2.6.13-rc4-mm1/broken-out/git-netdev-ieee80211-wifi.patch") mentions some things about power management on ipw2200 and how to control it.  Please try running these commands and see if they help (you may want to look at 'dmesg' and 'iwlist scan' after each command to see what they say):
```

sudo iwconfig eth1 power off
sudo iwpriv eth1 set_power 1
```

Also, what is the output of:
```

sudo iwpriv eth1 get_power
```

And is this a physical on/off switch on your computer, or a software switch (i.e., a switch that you toggle by pressing keys on your keyboard, like function+F2 for example)?

---

### Post by jewbolt on 2008-09-04
Thanks for the quick reply.

I tried the following commands on at a time and looked at dmesg and iwlist after each time:
sudo iwconfig eth1 power off
sudo iwpriv eth1 set_power 1

Afterwards, the result of 'iwlist scan' and 'dmesg | grep -e ipw -e iwl -e eth1' produced nothing different than before.

ie. 
dmesg:
33.317872] eth1: Radio is disabled by RF switch

iwlist scan:
eth1      No scan results

Here is the output of the other command that you suggested;
jewbolt@jewbolt-laptop:~$ sudo iwpriv eth1 get_power
eth1      get_power:Power save level: 1 (Timeout 350ms, Period 400ms)

After running 'sudo iwconfig eth1 power off', it the output changed to the following:
jewbolt@jewbolt-laptop:~$ sudo iwpriv eth1 get_power
eth1      get_power:Power save level: 1 (Off)

This looked promising, but the result of dmesg and iwlist was unchanged.

You asked whether I have a physical on/off switch on your computer, or a software switch. I don't know for sure, but looking at the git-netdev-ieee80211-wifi.patch link you mentioned, it seems to suggest that its software. Certainly in Windows XP, the ezButton utility needed to be installed before I could turn on the wireless. This utility enabled the use of three buttons situated above the keyboard (next to the Power button). One button was for the wireless (as previously mentioned and assumed to be the RF kill switch), the other two were programable (ie, could be configured to launch applications).

More info on my laptop is available on the web site [http://www.targahk.com/Service/index.asp](http://www.targahk.com/Service/index.asp), within the 'Traveller C50' section. The manual didn't mention whether it was a hardware or software switch specifically. It just mentioned the need for the ezButton utility.

Looking at the git-netdev-ieee80211-wifi-patch link, I thought looking for rfkill might be a good thing:
jewbolt@jewbolt-laptop:~$ sudo find / -name rf_kill -print
/sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/rf_kill

I found it, but I'm not sure what to do with it.
The value within this file is 2. Does this value need to be 0 (zero)? 
If so, how can I do that? Manually changing values in obscure files seems a tad risky.

---

### Post by pytheas22 on 2008-09-04
I did more googling but still don't have any concrete answer.  There's a kernel patch mentioned [here]("http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/acer-4100lmi-wireless-kill-switch-problem-331179/") regarding what appears to be the exact same problem, but the link to the patch seems dead--and anyway I doubt you want to have to recompile the kernel.

I would try editing the file at /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/rf_kill.  It could potentially cause problems, but I doubt it would do anything serious, and I'm not sure what else to try.

Also, check your BIOS just to make sure there's not some option to force the wireless radio (antenna) to always be on or something.  And boot your computer with the power cord plugged in--it's possible that the radio would not be turned off at all if the laptop is running on AC power (because it only turns it off to save energy).

Finally, do you still have Windows on this computer?  If so, see if you have any options in any wireless utility in Windows for switching the radio on and off.  It could be the case that Windows is turning the radio off and for some reason Linux can't turn it back on (similar things happen with certain ethernet cards).

---

### Post by jewbolt on 2008-09-10
Hi, been away for a bit. Continuing from your last advice...

I no longer have Windows installed, but by default, when Windows booted, the kill switch was on, as I'd always need to press the button to activate the wireless. 

I checked the BIOS and saw no options relating to wireless card or rf power.

I tried to change the rf_kill file, but I get permission denied errors.
jewbolt@jewbolt-laptop:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0$ sudo echo 0 > rf_kill
bash: rf_kill: Permission denied

As far as I can see, there is no process writing to this file:
cd /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0 
sudo fuser rf_kill  ( =>  returns nothing )

Trying another avenue, I emailed targa support and have got no reply yet. Possibly wishful thinking, but you never know your luck. 

Doing some reading, it seems that my previous assumption that the kill switch was software, may be inacurate. The value in the rf_kill file is 2.

The possible values are;
0 = RF kill not enabled (radio on)
1 = SW based RF kill active (radio off)
2 = HW based RF kill active (radio off)
3 = Both HW and SW kill active (radio off)

This suggests that Ubuntu has determined that my laptop has a hw based rf kill switch. Which is disabled. Could Ubuntu be wrong about this? If it was hardware based, then why would the ezButton utility be required in Windows?
I assumed that the ezButton utility simply installed a hardware driver that allowed the laptop button to activate/deactivate the software switch. In which case, the rf_kill module should be able to bypass the button. Correct?

I looked at the laptop matrix at rfswitch.sourceforge.net and saw that my laptop was not there. Only one Targa laptop was, and that used a function key + F2 key combination. I wonder if my laptop is a rebadged something else? A google hasn't suggested that it is.  

I'm happy to recompile the kernel if that is what is required. I assume there are lots of tips on doing this in ubuntu. 

Are there any utilities or things I can play with to get a clearer picture of what is required to activate the wireless card / deactivate the kill switch?

---

### Post by pytheas22 on 2008-09-10
Try running:
```

sudo -s
echo '0' > /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/rf_kill
```

I think it wasn't working before because sudo only applies to the first command, not the pipe.  So that should successfully change the rf_kill file and hopefully force the radio to always be on.  If that doesn't work, we can look at other options.

EDIT: another thing to try if the above fails: take a look at this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/193970"). I think it deals with the same problem you're having (can't turn radio on using iwl3945 driver).  The suggested fix there is to turn the radio on by hitting the kill switch, then reinsert the iwl3945 module again by running:

```
sudo rmmod iwl3945; sudo modprobe iwl3945
```

Does that help?

Also FYI I'm working in [another thread]("http://ubuntuforums.org/showthread.php?p=5762735#post5762735") that we recently discovered to apparently be dealing with the same issue.

---

### Post by jewbolt on 2008-09-10
Hi, Thanks for your continued help. I tried your suggestions. Unfortunatly, still no joy. I got no permissions errors with the echo 0 > rf_kill, but the value of the file remained unchanged. Either the command was quitely ignored, or something else changed it back straight away. 

$ sudo -s
# cd /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0
# more rf_kill
2
# echo 0 > rf_kill
# more rf_kill
2
With the rmmod and modprobe solution, I have a different module which I think is ipw2100.

# lsmod | grep ipw
ipw2100                73264  0 
ieee80211              35528  1 ipw2100

tried sudo rmmod ipw2100; 
# rmmod ipw2100
# modprobe ipw2100
# dmesg | grep -e ipw -e iwl -e eth1
(snip)
[  143.838672] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[  143.841260] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[  143.915008] eth1: Radio is disabled by RF switch.
[  407.998727] ADDRCONF(NETDEV_UP): eth1: link is not ready

# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

You advised that I press the kill switch after the rmmod.I did this, but just as before, the kill switch button has no affect (other than logging the previously mentioned "unknown keycode" messages). Here is an extract from the /var/log/messages that illustrates what was logged:

Sep 11 08:50:02 jewbolt-laptop kernel: [  435.200949] ACPI: PCI interrupt for device 0000:02:01.0 disabled
Sep 11 08:50:30 jewbolt-laptop kernel: [  154.566700] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
Sep 11 08:50:30 jewbolt-laptop kernel: [  154.566708] ipw2100: Copyright(c) 2003-2006 Intel Corporation
Sep 11 08:50:30 jewbolt-laptop kernel: [  154.568632] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
Sep 11 08:50:30 jewbolt-laptop kernel: [  154.569302] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
Sep 11 08:50:30 jewbolt-laptop kernel: [  154.645747] eth1: Radio is disabled by RF switch.
Sep 11 08:50:30 jewbolt-laptop kernel: [  438.433681] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep 11 08:50:56 jewbolt-laptop kernel: [  439.989592] ACPI: PCI interrupt for device 0000:02:01.0 disabled
Sep 11 08:50:58 jewbolt-laptop kernel: [  441.189606] atkbd.c: Unknown key pressed (translated set 2, code 0x66 on isa0060/serio0).
Sep 11 08:50:58 jewbolt-laptop kernel: [  441.189621] atkbd.c: Use 'setkeycodes 66 <keycode>' to make it known.
(translated set 2, code 0x66 on isa0060/serio0).
... (snip) ...
Sep 11 08:51:01 jewbolt-laptop kernel: [  441.437005] atkbd.c: Unknown key released (translated set 2, code 0x66 on isa0060/serio0).
Sep 11 08:51:01 jewbolt-laptop kernel: [  441.437019] atkbd.c: Use 'setkeycodes 66 <keycode>' to make it known.
Sep 11 08:51:11 jewbolt-laptop kernel: [  155.998870] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
Sep 11 08:51:11 jewbolt-laptop kernel: [  155.998878] ipw2100: Copyright(c) 2003-2006 Intel Corporation
Sep 11 08:51:11 jewbolt-laptop kernel: [  156.003534] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
Sep 11 08:51:11 jewbolt-laptop kernel: [  156.004352] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
Sep 11 08:51:11 jewbolt-laptop kernel: [  442.251736] eth1: Radio is disabled by RF switch.
Sep 11 08:51:11 jewbolt-laptop kernel: [  442.414881] ADDRCONF(NETDEV_UP): eth1: link is not ready

In short, my assessment of the problem is as follows:
 - kill switch button has no affect (no button driver, which was part of ezButton in Windows)
 - rf_kill switch is refusing to be deactivated via other attempts.

Where to next my very helpful friend?

---

### Post by pytheas22 on 2008-09-11
I wonder if the value of rf_kill wasn't changed because of permission issues or something (even though you were root, maybe it wasn't writeable).  You could try this, which should force the file to be written with the desired value, then immediately remove write permissions from it, so that if a daemon is restoring the default value automatically, hopefully it wouldn't have time to do so:
```

sudo -s
cd /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0
rm -rf rf_kill
echo '0' > rf_kill; chmod -w rf_kill; chmod -w rf_kill;
```

If this doesn't work, I don't know what to do next, since everything else has failed...although Google never runs out of suggestions if you look hard enough.

---

### Post by jewbolt on 2008-09-15
Hi. Thanks for you patients with this. 

I tried the rm -rf rf_kill from a sudo shell session, and I still got a permissions error. Very strange! from the sudo shell session, I tried fuser rf_kill and saw that nothing had the file open. 

root@jewbolt-laptop:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0# rm -rf rf_kill
rm: cannot remove `rf_kill': Operation not permitted

As a side note, when the module ipw2100 is removed with rmmod, the rf_kill file vanishes, and only returns once modprob is used to reload the ipw2100 module.

I guess there is some low level kernel stuff using the file. Otherwise, I'm at a loss to understand how a file that's now being used (acording to fuser) can't be deleted when I'm root. 

Anyway... by the sounds of things, and from my google investigation, it looks like I'm fast approaching a dead end :( 

If only there was some way to disable this RF kill switch. 

Is there any point in trying to use other's modules? Such as acerhk, FSAM, ipw2200 (which I see referenced in the rfswitch.sourceforge.net web page). 

I guess I should probably just bite the bullet and get a pcimca wireless card!

---

### Post by pytheas22 on 2008-09-15
Sorry that it's still not working.  I don't know what's going on any more than you do, unfortunately.

I'm not sure if ipw2200 would support your card, but it's worth a try.  It should already exist in the kernel.  If you type:
```

sudo rmmod ipw2100
sudo modprobe ipw2200
```

does it recognize the wireless interface (according to 'lshw -C Network')?

I can't believe that no one has solved this problem, because in my Google searches it did seem like you're hardly the only one who faces it.

---

