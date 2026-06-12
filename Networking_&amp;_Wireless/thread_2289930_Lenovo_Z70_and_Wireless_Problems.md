---
title: "Lenovo Z70 and Wireless Problems"
date: 2015-08-08
forum: Networking &amp; Wireless
---

### Post by jadmr on 2015-08-08
Hello. I have recently installed Ubuntu 14.04 on a Lenovo Z70, specifically, [this model purchased from Amazon]("http://www.amazon.com/Lenovo-17-3-Inch-Laptop-Drive-80FG0036US/dp/B00SB4AHJG/ref=sr_1_3?ie=UTF8&qid=1439021418&sr=8-3&keywords=Lenovo+Z70"). I knew beforehand that this model has wireless issues, specifically that the laptop cannot connect to a WiFi network (see [this post]("http://askubuntu.com/questions/639331/ubuntu-wi-fi-not-working-on-lenovo-z70-ideapad-fresh-15-04-install") as well as [this one]("http://askubuntu.com/questions/621345/lenovo-z70-wifi-with-14-04-2-and-kernel-3-16-not-working")). Knowing this, I bought [a WiFi adapter]("http://www.amazon.com/gp/product/B00LWE14TO?psc=1&redirect=true&ref_=oh_aui_detailpage_o01_s00") from Net-Dyn, but am confused as to how to install the drivers for this adapter. When plugged in, I do not see the option to connect to my wireless home network. So in essence I have two questions,

1) Does anyone know how to fix the wireless issue for the Z70 (moonshot question, but here goes)?

2) Alternatively, how do I install the drivers for my WiFi adapter? 



Here is m wireless information:

```
########## wireless info START ##########


Report from: 08 Aug 2015 01:14 PDT -0700


Booted last: 08 Aug 2015 00:35 PDT -0700


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3819]
    Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:003e] (rev 20)
    Subsystem: Lenovo Device [17aa:3044]


04:00.0 3D controller [0302]: NVIDIA Corporation GM108M [GeForce 840M] [10de:1341] (rev a2)


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 004: ID 5986:0249 Acer, Inc 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 008: ID 148f:7601 Ralink Technology, Corp. 
Bus 001 Device 007: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:156435 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88093 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:209089559 (209.0 MB)  TX bytes:7217403 (7.2 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       778     1  0 00:35 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


Sorry, try again.
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


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


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


########## wireless info END ############



```

Having the ability to connect wirelessly to a network is critical for me, and I would appreciate any help or suggestions. Thank you.

---

### Post by praseodym on 2015-08-08
Currently, the necessary driver ath10k_pci is not part of the kernel. You can try this:

[https://forum.ubuntuusers.de/topic/wlan-funktioniert-nicht-an-acer-laptop/#post-7677683](https://forum.ubuntuusers.de/topic/wlan-funktioniert-nicht-an-acer-laptop/#post-7677683)

---

### Post by jadmr on 2015-08-09
Hello, thanks for replying. I have a few questions if you don't mind me asking. 

I am stuck at the step where I i[nstall the backports for ath10k]("https://wireless.wiki.kernel.org/en/users/drivers/ath10k/backports"). When trying to run [COLOR=#333333][FONT=Consolas]make defconfig-ath10k[/FONT][/COLOR], I get the following warnings:

[I]Generating local configuration database from kernel ... done.
[B]cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c[/B]
cc   conf.o zconf.tab.o   -o conf
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#[/I]


And then when I try to compile with make, I get:


[I]make[5]: `conf' is up to date.
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
arch/x86/Makefile:129: CONFIG_X86_X32 enabled but no binutils support
[B]Makefile:669: Cannot use CONFIG_CC_STACKPROTECTOR_REGULAR: -fstack-protector not supported by compiler
[/B][B]make[4]: *** No rule to make target `Files/WirelessDriver/backports-4.1.1-1'.  Stop.
[/B]make[3]: *** [modules] Error 2
make[2]: *** [modules] Error 2
make[1]: *** [modules] Error 2
make: *** [default] Error 2[/I]


My kernel version is 3.19.0-25 and I checked my version of GCC, which is 4.8.4. I have tried this with both 4.1.1-1 and 4.2-rc1-1 backports, but I'm getting the same error. I'm fairly novice at using make files, but it seems like I am missing a step, especially since make is throwing an error that it cannot find a target. However, I followed all the steps [on the provided website]("https://wireless.wiki.kernel.org/en/users/drivers/ath10k/backports"). Are the back ports for kernels that are less than version 4? Or am I okay with ignoring this step and [proceeding to clone the repository on step 5?]("https://forum.ubuntuusers.de/topic/wlan-funktioniert-nicht-an-acer-laptop/#post-7677683")

---

### Post by praseodym on 2015-08-15
Tried 4.0.1?

---

### Post by chili555 on 2015-08-15
This will get the USB working: [http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adapter-installation/554278#554278](http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adapter-installation/554278#554278)

---

