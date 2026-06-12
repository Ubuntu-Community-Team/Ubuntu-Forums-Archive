---
title: "[SOLVED] How do I get on line"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by barnowl13 on 2007-04-14
Hi I installed Ubuntu 6.10 to my computer a while ago with only one problem and that was I can not get on line. I have tried different Ethernet cards and when I check my Ethernet cards are detected.

But when I go into network nothing, when I look at the monitors it shows lo and loopback I have had no problems getting on line with windows XP.

I have just tried Ubuntu 7.10 hoping that this may solve my problem but again it still does not come with a network connection?

As any one got any ideas?

---

### Post by gonzalov on 2007-04-15
Do you know your network card make?

Can you post the output from "ifconfig"

A little more info (or as much as you can give) will make answers easier and more accurate.

---

### Post by gonzalov on 2007-04-15
Also, are you on a LAN or connecting directly to internet on some modem? Can you ping some other computer?

---

### Post by barnowl13 on 2007-04-18
Hi sorry I have taken so long to get back to you.

I have cable broadband connection  (10 mbit) and a Webstar EPC2100 series 2 cable modem. 

Below is what came up when I put in ifconfig and some more information that I have picked when read other posting in the forum, I hope that this will help you too help me.

I am a newbie to all of this but if you tell me exactly what to write and were I will do it as I would really like to get Linux up and running. I have tried different distro's but have always come up with the same problem.

 chris@chris-desktop:~$ sudo ifconfig -a

 lo Link encap:Local Loopback

 inet addr:127.0.0.1 Mask:255.0.0.0

 inet6 addr: ::1/128 Scope:Host

 UP LOOPBACK RUNNING MTU:16436 Metric:1

 RX packets:2 errors:0 dropped:0 overruns:0 frame:0

 TX packets:2 errors:0 dropped:0 overruns:0 carrier:0

 collisions:0 txqueuelen:0

 RX bytes:100 (100.0 b) TX bytes:100 (100.0 b)


 sit0 Link encap:IPv6-in-IPv4

 NOARP MTU:1480 Metric:1

 RX packets:0 errors:0 dropped:0 overruns:0 frame:0

 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

 collisions:0 txqueuelen:0

 RX bytes:0 (0.0 b) TX bytes:0 (0.0 b) 

chris@chris-desktop:~$ sudo lspci

 00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate]
 System Controller (rev 25)

 00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate]
 AGP Bridge (rev 01)

 00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA
 (rev 01)

 00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper]
 IDE (rev 07)

 00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)

 00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper]
 USB (rev 06)

 00:08.0 Communication controller: Conexant HCF 56k Data/Fax/Voice
 Modem (rev 08)

 00:09.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit
 Ethernet Adapter (rev 10)

 00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-724F [DS-1
 Audio Controller] (rev 03)

 01:05.0 VGA compatible controller: ATI Technologies Inc 3D Rage IIC
 AGP (rev 7a) 

1: lo: <LOOPBACK,UP,10000> mtu 1643 qdisc no queue
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: sit0: <NOARP> mtu 1480 qdisc noop
link/sit 0.0.0.0. brd 0.0.0.0.
lsmod

 Module Size Used by

 binfmt_misc 13448 1

 rfcomm 42260 0

 l2cap 27136 5 rfcomm

 bluetooth 53476 4 rfcomm,l2cap

 ipv6 272288 10

 cpufreq_userspace 5408 0

 cpufreq_stats 7744 0

 freq_table 6048 1 cpufreq_stats

 cpufreq_powersave 2944 0

 cpufreq_ondemand 8876 0

 cpufreq_conservative 8712 0

 video 17540 0

 tc1100_wmi 8324 0

 sony_acpi 6412 0

 sbs 16804 0

 pcc_acpi 14080 0

 i2c_ec 6272 1 sbs

 hotkey 11556 0

 dev_acpi 12292 0

 container 5632 0

 button 7952 0

 battery 11652 0

 asus_acpi 17688 0

 ac 6788 0

 af_packet 24584 0

 lp 12964 0

 tsdev 9152 0

 snd_ymfpci 64288 1

 gameport 17160 1 snd_ymfpci

 snd_ac97_codec 97696 1 snd_ymfpci

 snd_ac97_bus 3456 1 snd_ac97_codec

 usblp 15488 0

 snd_pcm_oss 47360 0

 snd_mixer_oss 19584 1 snd_pcm_oss

 snd_pcm 84612 3 snd_ymfpci,snd_ac97_codec,snd_pcm_oss

 snd_opl3_lib 12288 1 snd_ymfpci

 snd_timer 25348 3 snd_ymfpci,snd_pcm,snd_opl3_lib

 snd_hwdep 10756 1 snd_opl3_lib

 snd_page_alloc 11400 2 snd_ymfpci,snd_pcm

 snd_mpu401_uart 10240 1 snd_ymfpci

 snd_rawmidi 27264 1 snd_mpu401_uart

 snd_seq_device 9868 2 snd_opl3_lib,snd_rawmidi

 psmouse 41352 0

 serio_raw 8452 0

 floppy 63044 0

 evdev 11392 1

 snd 58372 13
 snd_ymfpci,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device

 parport_pc 37796 1

 parport 39496 2 lp,parport_pc

 amd_k7_agp 10252 0

 agpgart 34888 1 amd_k7_agp

 soundcore 11232 1 snd

 pcspkr 4352 0

 shpchp 42144 0

 pci_hotplug 32828 1 shpchp

 r8169 32136 0

 i2c_amd756 7556 0

 i2c_core 23424 2 i2c_ec,i2c_amd756

 ext3 142728 1

 jbd 62228 1 ext3

 ohci_hcd 22532 0

 usbcore 134912 3 usblp,ohci_hcd

 ide_generic 2432 0

 ide_cd 33696 0

 cdrom 38944 1 ide_cd

 ide_disk 18560 2

 generic 5764 0

 amd74xx 15260 0 [permanent]

 thermal 15624 0

 processor 31560 1 thermal

 fan 6020 0

 fbcon 41504 0

 tileblit 3840 1 fbcon

 font 9344 1 fbcon

 bitblit 7168 1 fbcon

 softcursor 3328 1 bitblit

 vesafb 9244 0

 capability 5896 0

 commoncap 8704 1 capability

 chris@chris-desktop:~$ sudo lspci

 00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate]
 System Controller (rev 25)

 00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate]
 AGP Bridge (rev 01)

 00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA
 (rev 01)

 00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper]
 IDE (rev 07)

 00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)

 00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper]
 USB (rev 06)

 00:08.0 Communication controller: Conexant HCF 56k Data/Fax/Voice
 Modem (rev 08)

 00:09.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit
 Ethernet Adapter (rev 10)

 00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-724F [DS-1
 Audio Controller] (rev 03)

 01:05.0 VGA compatible controller: ATI Technologies Inc 3D Rage IIC
 AGP (rev 7a) 

chris@chris-desktop:~$ sudo ip link show eth0

 Device "eth0" does not exist.

 chris@chris-desktop:~$ sudo ip link show eth1

 Device "eth1" does not exist. 

 into gedit and opened internet config this is what came up?
chris@chris-desktop:~$
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider
auto modconf
iface modconf inet manual
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

I don't know if this is of any help but I have just tried "BabelLinux" Started up with no problem but again I came up with the same problem it could see my Ethernet card no problem but it could not see that I am connected to a modem or that there was any signel there at all?

---

### Post by barnowl13 on 2007-04-29
I have tried using the live CD of the new version of Ubuntu that has just been released, hoping that it would solve my getting on line problem but no luck.

But could any one tell if I installed the new version from the live CD would it automaticily over write Ubuntu 6.10 or would I end up with 2 Ubuntu OS on my computer?

---

