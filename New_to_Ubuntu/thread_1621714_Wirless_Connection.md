---
title: "Wirless Connection"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by komatsu100 on 2010-11-14
I have a new Acer Aspire 5251 with Atheros Communication Inc AR928X wireless N card, and when I loaded Ubuntu 10:10 the Wirless Manager is hard to connect to my wireless connection which is a Belkin Play and has been dropping the connection. I has now started not working in any way about every other time I start up have to shut down and load again and most times will connect for a few minutes and then drop out have to load web pages quickly before it drops.  I would like to down load or reload the drivers for it.

---

### Post by Hippytaff on 2010-11-14
What does
```

rfkill list

```
return?

also you might want to post the output to this commands to help people help you diagnose the problem.
```

iwconfig

```

---

### Post by myao on 2010-11-14
I have a Dell studio and I am facing a wireless connection problem in Ubuntu. It is not connecting after I give the wireless authentication key. I tried to search the solution in ubuntu forum but it did not work. Any suggestion will be highly appreciated.

---

### Post by Hippytaff on 2010-11-14
Try the same as the post above^^ and we can have a look :-)

---

### Post by komatsu100 on 2010-11-14
rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
ron@ron-laptop:~$ rfkill
Usage:	rfkill [options] command
Options:
	--version	show version (0.4)
Commands:
	help
	event
	list [IDENTIFIER]
	block IDENTIFIER
	unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
	<idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm

---

### Post by Hippytaff on 2010-11-14
What does
```

lspci

```
return with regards to wireless
also
```

iwconfig

```
:-)

---

### Post by komatsu100 on 2010-11-14
rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
ron@ron-laptop:~$ rfkill
Usage:	rfkill [options] command
Options:
	--version	show version (0.4)
Commands:
	help
	event
	list [IDENTIFIER]
	block IDENTIFIER
	unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
	<idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
ron@ron-laptop:~$ ^C
ron@ron-laptop:~$ ^C
ron@ron-laptop:~$ config
No command 'config' found, did you mean:
 Command 'fconfig' from package 'redboot-tools' (main)
 Command 'vconfig' from package 'vlan' (main)
 Command 'mconfig' from package 'mono-2.0-devel' (main)
config: command not found

---

### Post by komatsu100 on 2010-11-14
This is the return
rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
ron@ron-laptop:~$ rfkill
Usage:	rfkill [options] command
Options:
	--version	show version (0.4)
Commands:
	help
	event
	list [IDENTIFIER]
	block IDENTIFIER
	unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
	<idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
ron@ron-laptop:~$ ^C
ron@ron-laptop:~$ ^C
ron@ron-laptop:~$ config
No command 'config' found, did you mean:
 Command 'fconfig' from package 'redboot-tools' (main)
 Command 'vconfig' from package 'vlan' (main)
 Command 'mconfig' from package 'mono-2.0-devel' (main)
config: command not found

Here is the iwfig
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Belkin.5D84"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 94:44:52:55:3D:84   
          Bit Rate=243 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by komatsu100 on 2010-11-14
Here is the return on lspci
lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

Sorry I have so many of the same replys but with the connection acting up I wasn't sure what I was getting uploaded and what I wasn't.

---

### Post by Hippytaff on 2010-11-14
Having had a read it looks as though you need to use the windows driver with Ndiswrapper
[http://ubuntuforums.org/showthread.php?t=1498245](http://ubuntuforums.org/showthread.php?t=1498245)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
post back if you need some more help

Edit -> this is the info you need to use for searching etc
08:00.0 Network controller: Atheros Communications Inc. [COLOR=Red]AR928X[/COLOR] Wireless Network Adapter (PCI-Express) (rev 01)
[COLOR=Red]AR928X - [COLOR=Black]This is your chipset, so search this to get the correct driver :-)[/COLOR][/COLOR]

---

### Post by anewguy on 2010-11-14
And remember - Windows XP drivers only, and they must match the OS type -> if 32-bit Ubuntu, driver must be 32-bit, 64-bit Ubuntu, driver must be 64-bit.

As Happytaff said, just post back if you need help.  Everything for ndiswrapper can be installed without being online.  If you go to get it online, use Synaptic Package Manager and get ndiswrapper common and utils as well as ndisgtk.  Do not follow old posts that say you have to download the source for ndiswrapper, etc. as they are way out of date and you'll just create a mess for yourself.

Dave ;)

---

