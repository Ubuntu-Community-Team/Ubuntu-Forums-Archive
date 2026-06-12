---
title: "Wireless woes"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by LinkRJH on 2005-10-14
Sorry about the newb-ness of this question (I know, great way to start a thread), but I have no idea how to get my wireless going at all.  On other distributions such as Knoppix, the automatic wireless stuff did not recognize my card.  I'm currently on a Dell Inspiron 600m.  Any suggestions?

Thanks in advance,

Rich

---

### Post by insitu on 2005-10-14
Question is a bit too general, maybe. 

There are at least two ways : 
 - use the GUI system -> administration -> network
 - use the command line tool iwconfig

For a start, do you see the wifi card with
$> ifconfig -a
or in the control panel of network config gui ?

If so, then you should be able to configure it given some informations on your wifi network. AFAIK, the two most important parameters are : 
 - essid, the network identification for preventing various  networks to mingle, 
 - key for WEP or WPA acces control. I know only WEP and you should put in the appropriate field the hexadecimal (or ascii equivalent) value of the key. This should be the one stored in the router.

Good luck

---

### Post by spd106 on 2005-10-14
The best thing to do first is see if your card is supported by Ubuntu ie look [here]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards")
and hope that you don't need to use ndiswrapper. Don't worry if you do it's not the end of the world. It's just that you need to do more work.

Here's another useful [link]("https://wiki.ubuntu.com/WiFiHowto") 

Good luck

---

### Post by LinkRJH on 2005-10-15
linkrjh@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:A4:45:17
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fea4:4517/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:207946433 (198.3 MiB)  TX bytes:6882286 (6.5 MiB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3352071 (3.1 MiB)  TX bytes:3352071 (3.1 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

linkrjh@ubuntu:~$

I don't know if that means it's working or not.  I'm a total n00b to network and to Linux.

As for if it's supported, it looks like it is...I don't know though, I don't know how to even check what the card is.  I'm on an Inspiron 600m.

Thanks in advance,

Richard

---

### Post by LinkRJH on 2005-10-15
Also:

linkrjh@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

linkrjh@ubuntu:~$

---

### Post by LinkRJH on 2005-10-15
I need wireless. :( :???:

---

### Post by AgenT on 2005-10-15
You need to tell us what your network card is! Because you probably do not know specifics, please do this:

Run this command: ```
sudo lspci
``` and also this: ```
sudo lspci -n
``` and post the output of both. And use the code tags around your posted text!!

---

### Post by LinkRJH on 2005-10-15
Ahh!  Thanks for putting up with me and helping. 

```

linkrjh@ubuntu:~$ sudo lspci
Password:
0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Radeon Mobility 9000 M9] (rev 02)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
0000:02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
0000:02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
linkrjh@ubuntu:~$ sudo lspci -n
0000:00:00.0 0600: 8086:3340 (rev 03)
0000:00:01.0 0604: 8086:3341 (rev 03)
0000:00:1d.0 0c03: 8086:24c2 (rev 01)
0000:00:1d.1 0c03: 8086:24c4 (rev 01)
0000:00:1d.2 0c03: 8086:24c7 (rev 01)
0000:00:1d.7 0c03: 8086:24cd (rev 01)
0000:00:1e.0 0604: 8086:2448 (rev 81)
0000:00:1f.0 0601: 8086:24cc (rev 01)
0000:00:1f.1 0101: 8086:24ca (rev 01)
0000:00:1f.5 0401: 8086:24c5 (rev 01)
0000:00:1f.6 0703: 8086:24c6 (rev 01)
0000:01:00.0 0300: 1002:4c66 (rev 02)
0000:02:00.0 0200: 14e4:165d (rev 01)
0000:02:01.0 0607: 1217:7113 (rev 20)
0000:02:01.1 0607: 1217:7113 (rev 20)
0000:02:03.0 0280: 14e4:4320 (rev 03)
linkrjh@ubuntu:~$

```

Richard

---

### Post by AgenT on 2005-10-15
You are using a Broadcom wireless card then. This is a good start because the first thing needed is the knowledge of what hardware you are trying to get working. Most likely this card is called Dell TrueMobile or something like that, but that does not matter because it is just Dell's name for it. You can see a detailed list of cards that use the Broadcom chipset you have [here]("http://pci-ids.ucw.cz/iii/?i=14e44320"). That list is helpful because you can see by what other "name brand" names your chipset can go by. Do note that a lot of times a company likes to be annoying and can actually use multiple chipsets under the same name (which can be tricky and which is why you always need to find out the chipset name, not the card "brand name").

Searching this forum for your chipset ("broadcom bcmwl5") revealed multiple threads, but they are outdated. 

In terminal, do this:
```
sudo lsmod
```and ```
sudo modinfo bcmwl5
``` and report your results. 

Bascially, your problem is probably due to ndswrapper not installing your driver correctly. What you want to do is just reinstall the driver. Follow the how-to's in those forums but skip over anything that asks you to remove ndswrapper and install and newer version. The reason for this is that you are now running Breezy that has the newest version already installed.

The steps you basically want to take is this:
```
sudo rmmod bcmwl5
sudo rmmod ndiswrapper
``` then copy your bcmwl5.inf that comes with the Windows drivers to your desktop and do this:
```
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
``` then possibly edit your configuration file in /etc/ndiswrapper/ and change from Radionstate 1 to Radiostate 0. Note that using ndiswrapper should probably be your last resort. It's emulating Windows which is not the optimum thing to do. After this, reboot and then edit your network settings using the network-admin provided in Breezy.

Others may be able to help you better.

---

### Post by ingenious on 2005-10-16
Hi,

I have a netgear MA521 wireless card...  Installed breezy and updated nsidwrapper, got the correct driver from the list, but need help patching wireless extention to v18.  See this post in the new user forum:
[http://www.ubuntuforums.org/showthread.php?t=77268](http://www.ubuntuforums.org/showthread.php?t=77268)

Any help is appreciated.

---

### Post by dayal_78 on 2005-10-16
[QUOTE=ingenious]Hi,

I have a netgear MA521 wireless card...  Installed breezy and updated nsidwrapper, got the correct driver from the list, but need help patching wireless extention to v18.  See this post in the new user forum:
[http://www.ubuntuforums.org/showthread.php?t=77268](http://www.ubuntuforums.org/showthread.php?t=77268)

Any help is appreciated.[/QUOTE]
Hi,
I have a related problem and I have opened a separate thread, but I am just wondering if you guys can help me.
I have installed ubuntu 5.10 on my new dell inspiron 6000 and my wireless card is recognized. But everytime I boot I have to deactivate and then activate my wireless network interface to connect to internet.
Please help
Thanks
Dayal

---

### Post by LinkRJH on 2005-10-16
Reporting results:

```
linkrjh@ubuntu:~$ sudo lsmod
Password:
Module                  Size  Used by
isofs                  32824  1
udf                    75524  0
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_centrino      7380  1
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  4
radeon                 68352  1
drm                    58004  2 radeon
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
pcspkr                  3652  0
rtc                    11832  0
yenta_socket           22540  3
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  2 drm,intel_agp
nls_iso8859_1           4224  1
vfat                   12288  1
fat                    46492  1 vfat
nls_cp437               5888  3
ntfs                   92016  1
dm_mod                 50364  1
joydev                  9280  0
tsdev                   7616  0
evdev                   9088  1
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0
usbhid                 30688  0
tg3                    83716  0
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 36996  1
cdrom                  33952  1 ide_cd
ide_disk               16128  5
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  772
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
linkrjh@ubuntu:~$ sudo modinfo bcmwl5
modinfo: could not find module bcmwl5
linkrjh@ubuntu:~$

```

I didn't continue with your instructions because the bcmwl5 wasn't found, and I didn't want to mess anything up...

Thanks for your patience with me.

Richard

---

