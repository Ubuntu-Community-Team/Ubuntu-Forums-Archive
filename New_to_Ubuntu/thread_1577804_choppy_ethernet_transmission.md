---
title: "choppy ethernet transmission"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by bnhrobotics on 2010-09-19
I have been having a lot of network issues with my desktop computer which has 10.04 x64 on it. I no longer use the onboard Realktek ethernet controller due to issues I have had with it. I have found that using a PCI ethernet adapter is more reliable (the connection is always recognized). The issue that I have is that my connection is choppy. I see large bursts of packets being transmitted and then nothing. This happens in cycles. If, for example, I type in "www.google.com" into the browser during the zero transmission part of the cycle, the page will not begin to load for a couple of seconds until the packet burst starts up again. This is not a debilitating problem, but it is certainly frustrating. The problems seem to have occurred for me with 10.04. Any help would be appreciated. Thanks =)

Oh and, my laptop which is also using 10.04 x64 on wireless or wired connections does not seem to have the same problem.


```

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, fast devsel, latency 0, IRQ 27
	I/O ports at de00 [size=256]
	Memory at fdfff000 (64-bit, prefetchable) [size=4K]
	Memory at fdff8000 (64-bit, prefetchable) [size=16K]
	[virtual] Expansion ROM at fdf00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

03:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at ce00 [size=256]
	Memory at fdeff000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at fdd00000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

```

---

### Post by MooPi on 2010-09-19
Can you post the results of this  ```
ifconfig -a
``` I remember having a similar issue and I made certain that the unused connection was disabled and not interfering.

---

### Post by termin on 2010-09-19
this is posted in the wrong topic, its supposed to go in networking and wireless.
also do what the above post says and post back

---

### Post by bnhrobotics on 2010-09-19
eth0      Link encap:Ethernet  HWaddr 00:24:1d:1d:e2:dd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:0e:2e:b0:ea:aa  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:feb0:eaaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:127822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97955 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:164851697 (164.8 MB)  TX bytes:10483119 (10.4 MB)
          Interrupt:21 Base address:0xce00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4446653 (4.4 MB)  TX bytes:4446653 (4.4 MB)

---

### Post by MooPi on 2010-09-19
Looks as if eth0 is unused. Try disabling and see if that helps.
```
ifdown eth0
```

---

### Post by jtarin on 2010-09-19
Nevermind about the lsmod command...I see now what modules your using.
I'm curious as to what issues you had with your onboard card?

---

### Post by bnhrobotics on 2010-09-19
```

bryan@bryan-desktop:~$ sudo ifdown eth0
[sudo] password for bryan: 
ifdown: interface eth0 not configured

```

What do I do now?


The onboard was doing the same thing, but much worse. Plus, it was glitchy and would need to be disconnected from power if the computer ever was turned off incorrectly. Ultimately, it was just too much of a hassle, and the PCI card works better, but not perfectly.

---

### Post by MooPi on 2010-09-19
Can you post the contents of ```
/etc/network/interfaces
```

---

### Post by jtarin on 2010-09-19
Let's see if your using the right module. What kernel version are you using?

---

### Post by jtarin on 2010-09-19
I notice with your RTL-8139 you had the option to use Kernel modules: 8139too, 8139cp. Did you try the 8139cp also? With your other card it is reported by Hardware for Linux that modules 8169 and 8168 will work.

---

### Post by bnhrobotics on 2010-09-19
auto lo
iface lo inet loopback

Linux bryan-desktop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux


Are you speaking about the onboard Giga-byte ethernet controller? I dont think I used 8139cp, and I am not really sure how to go about that. I currently am not using this controller because it is too flaky under 10.04. I am using the PCI one: 03:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by MooPi on 2010-09-19
Try adding this to your /etc/network/interfaces, because your missing this from the file.
```
# The primary network interface
auto eth1
iface eth1 inet dhcp
```

---

### Post by bnhrobotics on 2010-09-19
I did that and then this:

bryan@bryan-desktop:/$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth1=eth1.

---

### Post by MooPi on 2010-09-19
This is a head scratcher if I've ever seen. Okay switch to eth0. But I'm stumped. Make certain to delete last entry.

```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```
After you edit add this command in terminal ```
sudo ifup eth0
```

---

### Post by bnhrobotics on 2010-09-19
```
bryan@bryan-desktop:~$ sudo nano /etc/network/interfaces 
[sudo] password for bryan: 

bryan@bryan-desktop:/$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth1=eth1.
                                                                         [ OK ]
bryan@bryan-desktop:/$ less /etc/network/interfaces
```


[B]From earlier ^
And then just now:[/B]


```
bryan@bryan-desktop:/$ sudo nano /etc/network/interfaces
[sudo] password for bryan: 
bryan@bryan-desktop:/$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
```

---

### Post by MooPi on 2010-09-19
I failed to ask if your connection status changed due to these changes ? If nothing has worked so far revert to your previous state so that things work at least. My final idea is to enter the bios and disable your onboard network adapter. Other than that I'm out of ideas.
Try this documentation: [https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html]("https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html")

---

### Post by bnhrobotics on 2010-09-19
I remained connected with the same connection the whole time. Nothing ever seemed to change.

---

### Post by jtarin on 2010-09-19
[A trail of breadcrumbs....]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/574281")

---

### Post by bnhrobotics on 2010-09-20
Cool thanks. Ill look into that more tomorrow (or when I have some free time.. could be a while. Career fair and GRE this week among other things). I'll see if I can do a bios update, but that may take some thinking. Dont they usually come packaged as executables? I am not familiar with apic either, so I'll need to read up on that too. I assume this may potentially fix the PCI ethernet, but not necessarily the onboard?

---

### Post by bnhrobotics on 2010-09-26
I got stuck at figuring out the proper syntax to add noapic to grub2. Any suggestions?

---

### Post by jtarin on 2010-09-26
> **bnhrobotics said:**
> I got stuck at figuring out the proper syntax to add noapic to grub2. Any suggestions?
[URL="https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation"]Scroll down and read thoroughly.
[/URL]

---

### Post by bnhrobotics on 2010-09-26
I see where that fits for grub, but can I just throw that into /etc/default/grub for grub2? I am not sure what other configuration file to edit in grub2.

---

### Post by jtarin on 2010-09-26
Sorry....wrong Grub....[HERE]("https://help.ubuntu.com/community/Grub2")

---

### Post by bnhrobotics on 2010-09-26
Thats the page that I looked at before and was stuck.

My grub.cfg looks like this:

```
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_rel
GRUB_CMDLINE_LINUX_DEFAUL
GRUB_CMDLINE_LINUX=""
```

Not sure where/how to stick the noapic and I couldn't figure it out from that link.

---

### Post by jtarin on 2010-09-26
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"
```
You can remove the "quiet splash" if you don't want it.
No changes made in the configuration files will take effect until the update-grub command is also run. You will be responsible for reading the accompanying documentation.

---

### Post by bnhrobotics on 2010-10-02
I gave that a try, and unfortunately, it did not fix the problem. It actually messed up the nvidia graphics driver so ubuntu booted in low graphics mode. As soon as I removed noapic, the graphics driver was found again.

---

### Post by bnhrobotics on 2011-01-15
Has anything new developed on this topic in the last few months? I have been putting up with the problem for a while now and still can't figure it out. I am about ready to give up on Ubuntu and switch distros unless I can get internet to be stable. Almost all of my computer time is online. I may switch back to 8.10 or whichever version was the last to not give me problems. Any input? Thanks

---

