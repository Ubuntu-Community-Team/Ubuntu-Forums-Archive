---
title: "Ubuntu 710/ Intel 3945 ABG Wireless Cars"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by lawrencius on 2008-04-19
Hey all,
I am completely new to linux and I have a problem with my intel wireless card (3945 ABG).
I know that there are some threads concerning this topic already, but I have problems implementing the solutions. (When I try to install the ieee.1.2.18 subsystem I can't "sudo make check_old")
Can somebody please give me a straight forward solution on how to install the driver.
Thanks

---

### Post by prshah on 2008-04-19
> **lawrencius said:**
> Hey all,
I am completely new to linux and I have a problem with my intel wireless card (3945 ABG).
I know that there are some threads concerning this topic already, but I have problems implementing the solutions. (When I try to install the ieee.1.2.18 subsystem I can't "sudo make check_old")
Can somebody please give me a straight forward solution on how to install the driver.
Thanks

Try [http://ubuntuforums.org/showthread.php?t=756260&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=756260&highlight=ndiswrapper). It is specifically for the WG311v3 (NetGear), but the basic commands and outputs should allow you to setup your specific wireless.

---

### Post by lawrencius on 2008-04-19
I'm sory I tried it, but it doesn't help me

---

### Post by chili555 on 2008-04-19
What about the built-in driver didn't work for you? I am using ipw3945 to reply to this post. It has been perfect from day one. Can we help you get it going?

---

### Post by lawrencius on 2008-04-19
yes any help is appreciated, so on my "restricted drivers manager"  is my intel wireless card but the status is "not in use".Maybe this helps

---

### Post by chili555 on 2008-04-19
Is *Enabled* checked? Is the card enabled in the BIOS? Is it turned on with the key combination, Fn+F4 maybe? Is the wireless switch turned on on the laptop? Let's see:```
sudo lshw -C network
iwconfig
```We can do it!

---

### Post by lawrencius on 2008-04-19
[B]This is the problem I was so vague about:
//This is from the tutorial[/B]

First, we build and install the ieee80211 subsystem.  You can obtain 
the latest ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net).  We 
recommend version 1.1.12 or newer:


% tar xzvf ieee80211-1.2.16.tgz
	% cd ieee80211-1.2.16
	% make 
	# make install   <--- You may need to be root
	% cd ..

lawrence@lawrence-laptop:~/Desktop/X60 Wireless/ieee80211-1.2.18$ sudo make check_old
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
/bin/sh: Can't open /home/lawrence/Desktop/X60
Old ieee80211 references found.  In order to build the ieee80211
subsystem, prior versions must first be removed.  You can perform
this task by running this makefile as root via:

    % sudo make check_old

and answering Y to remove the file references.
Aborting make.
make: *** [check_old] Error 1

**Yet whenever I type sudo make check_old I get the same message.**

**2. This is the output when I enter the commands you gave me:**

**lawrence@lawrence-laptop:~$ sudo lshw -C network**
SCSI                      
  *-network UNCLAIMED
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
lawrence@lawrence-laptop:~$ 
**lawrence@lawrence-laptop:~$ iwconfig**
lo        no wireless extensions.

irda0     no wireless extensions.

lawrence@lawrence-laptop:~$

**Hope this helps**

---

### Post by Zorael on 2008-04-19
[This](http://linuxwireless.org/en/users/Download) fixed my 7.10 3945 woes. I couldn't manage to compile the driver myself, and neither the ipw3945 nor the iwl3945 modules did the trick. But upon running that script thingy and installing its drivers, it worked flawlessly. I just had to add a line with 'iwl3945' in /etc/modules and a line with 'ipw3945' in /etc/modprobe.d/blacklist to make it load on boot.

---

### Post by chili555 on 2008-04-19
If you :```
sudo modprobe ipw3945
sudo ifconfig eth1 up
iwconfig
```Then does your wireless appear?

---

### Post by lawrencius on 2008-04-20
No it can't find it...

---

### Post by Zorael on 2008-04-20
Huh. Output of this?
```
$ modinfo ipw3945
$ modinfo iwl3945
```

---

### Post by chili555 on 2008-04-20
May I please also see:```
ifconfig
```Thanks.

---

### Post by lawrencius on 2008-04-20
**lawrence@lawrence-laptop:~$ modinfo ipw3945**
filename:       /lib/modules/2.6.22-14-generic/ubuntu/wireless/ipw3945/ipw3945.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2mp.ubuntu1
description:    Intel(R) PRO/Wireless 3945 Network Connection driver for Linux
srcversion:     04FD04D6570525365D93930
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
depends:        ieee80211
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default 0 off) (int)
parm:           auto_create:auto create adhoc network (default 1 on) (int)
parm:           led:enable led control (default 1 on)
 (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
**lawrence@lawrence-laptop:~$ modinfo iwl3945**
filename:       /lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl3945.ko
license:        GPL
author:         Copyright(c) 2003-2007 Intel Corporation
version:        1.1.0
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     B019B21F27D52A5DCDDA000
depends:        iwlwifi_mac80211
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           hwcrypto:using hardware crypto engine (default 0 [software])
 (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)
**lawrence@lawrence-laptop:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:16:D3:B2:3A:B3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x2000 Memory:ee000000-ee020000 

eth0:avah Link encap:Ethernet  HWaddr 00:16:D3:B2:3A:B3  
          inet addr:169.254.8.58  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Base address:0x2000 Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by chili555 on 2008-04-20
We're going to solve this if I have to fly out there with my sledgehammer!

If, in System -> Administration -> Network, when you highlight the wired connection and see Roaming enabled, uncheck it. Then please let me see:```
sudo ifup eth1
cat /etc/network/interfaces
```I feel like I am looking right at the answer, but my old trifocals are just not seeing it. The ipw3945 should just fall into place.

---

### Post by lawrencius on 2008-04-20
**AWESOME ATTITUDE!**

**lawrence@lawrence-laptop:~$ sudo ifup eth1**
Ignoring unknown interface eth1=eth1.
**lawrence@lawrence-laptop:~$ cat /etc/network/interfaces **
auto lo
iface lo inet loopback




iface eth0 inet dhcp

auto eth0

---

### Post by chili555 on 2008-04-20
Ah haaaaa! Now we are getting there, I....think. Please do:```
sudo gedit /etc/network/interfaces
```Amend it to look like this:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```Then, be sure to save your changes and close gedit. Now do:```
sudo /etc/init.d/networking restart
```Did your wireless interface, eth1, finally appear?

---

### Post by lawrencius on 2008-04-20
**lawrence@lawrence-laptop:~$ sudo gedit /etc/network/interfaces** //Changed file
**lawrence@lawrence-laptop:~$ sudo /etc/init.d/networking restart**
 * Reconfiguring network interfaces...                                          eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
                                                                         [ OK ]

**I don't know if this helps but yesterday when I looked at the status of my restricted drivers my wireless card said "Online/ or something like that" and after I tried tutorials and did stuff the card says: Not in use and has a red dot next to it.**

---

### Post by chili555 on 2008-04-20
> Not in use and has a red dot next to it.Please check the box to enable the driver. It will ask you to restart your computer. Please do so and then look at:```
iwconfig
```See if your eth1 has finally emerged from hibernation.

---

### Post by lawrencius on 2008-04-20
THis is what i meant

---

### Post by chili555 on 2008-04-20
Are you sure you have *linux-restricted-modules* installed?```
sudo apt-get install linux-restricted-modules
```

---

### Post by lawrencius on 2008-04-20
**lawrence@lawrence-laptop:~$ sudo apt-get install linux-restricted-modules**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-modules

---

### Post by chili555 on 2008-04-20
Dang! You **have** to have it, based on your modinfo results. Before I turn off this computer and enroll in 6th grade, let's see a few other things:```
lsmod | grep 3945
ps aux | grep ipw3945d
sudo cat /var/log/messages | grep 3945
```Thanks.

---

### Post by unicynic on 2008-04-23
On my Lenovo 3000 / IdeaPad Y410 (and maybe other notebooks like this), this driver is loaded but you won't get eth1 because the RF Kill switch is On (check dmesg). It's the ACPI problem and also involves the bluetooth and sound (sound works but you hear nothing).

However, once you put the notebook into sleep mode (mine is Fn+F1), and wake it up again, all wifi, bluetooth, and sound works. No need for other workarounds. I've tested this in Ubuntu 7.10, Mandriva 2008.1, and Mint 4.0.

It seems that the load order during boot does not create the proper proc devices and so the wifi detects that the hardware switch is on. Workarounds by writing to the rf_kill file does not work as it's a hardware switch.

However, the ACPI sleep script properly creates the proc devices and so when you wake it up (it runs the resume.d scripts), you can now use the wifi hardware keys (Fn+F5 for my notebook) and it will just work. Before sleep, none of the keys.

You can also boot with acpi=off but then the performance suffers - and still the Fn+F5 does not work where you need to reboot to Windows first to enable it and then reboot to Ubuntu. Even then, when you shutdown ubuntu, somehow the switch is back on and wifi doesn't work again. So, you're better off putting it in sleep mode and wake it up again...

Try it. Maybe it will work for you too.

Now, can anyone tell me how to get the same script (the parts that creates the proc devices) to run during boot? I don't even know where to find although I can see the script in /etc/acpi. So, any ACPI gurus here?

---

### Post by lawrencius on 2008-04-25
Hey everyone,
chilli555 helped me fix this problem.
Here is what to do:
1.) The Wireless button on my X60 lenovo, which had to be turned on with windows to connect to a wireless network is useless with linux ubuntu.
(the old Fn+F5 combo can be ignored)
Here is what to do: 
Go to your restricted drivers: check the wireless card to enable
Go to Terminal and enter: sudo modprobe iwl3945 disable=0 
Now you have to put it on your blackmail list do : sudo gedit /etc/modules 
add the iwl3945 to the list and your done!
Thanks for all the help!

---

### Post by unicynic on 2008-04-26
Good! I'd like to try that. But would this works with Hardy Heron?
Well, I still have to press suspend anyway to enable bluetooth and sound in hardy... BTW, in gutsy, after suspend and the wifi works, the wifi lights blinks. In hardy, I think there's a regression because now the wifi lights don't work anymore although the bluetooth (red color on same LED) works there. I am just confused now... Why suspend? Hahah... I still couldn't find the answer. I'll try the one you mentioned chili helped you with. At least, on those times where I don't care about the sound, I can use the wifi without having to suspend first.
Thanks everyone.

Update: I tried and now not only it doesn't work anymore after suspend, the whole system is unstable. I cannot even shutdown properly anymore. Sigh... a fresh install, I guess..

---

### Post by chili555 on 2008-04-26
Small edit: add to your /etc/modules file:```
iwl3945 disable=0
```Be sure to save and close.

---

