---
title: "Can't access Internet from a fresh install of Ubuntu 6.06"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by kentl on 2006-08-11
Hi!

I just installed Ubuntu 6.06 Dapper and found to my surprise that I couldn't access the Internet. It's a surprise because it worked  out-of-the-box when I installed Kubuntu 6.06 Dapper earlier.

My system is dual-boot and I'm in Windows XP at the moment. It all works well in here. I'm on an IPV4-network, have a public IP-address and I get my settings through DHCP.

**ipconfig /all in Windows XP says:**
> Windows IP Configuration

        Host Name . . . . . . . . . . . . : badmother
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
        Physical Address. . . . . . . . . : 00-50-8D-D9-0B-88
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 193.11.128.62
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 193.11.128.1
        DHCP Server . . . . . . . . . . . : 10.11.5.81
        DNS Servers . . . . . . . . . . . : 130.243.76.15
                                            130.243.76.14
        Lease Obtained. . . . . . . . . . : den 11 augusti 2006 20:18:11
        Lease Expires . . . . . . . . . . : den 11 augusti 2006 21:18:11


**ifconfig in my newly installed Ubuntu 6.06 Dapper says:**
> eth0      Link encap:Ethernet  HWaddr 00:50:8D:D9:0B:88  
          inet6 addr: fe80::250:8dff:fed9:b88/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:540 (540.0 b)  TX bytes:468 (468.0 b)
          Interrupt:233 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)


I hope someone can help me as I don't know much about Linux. So I don't think I'm able to fix it by myself.

---

### Post by spd106 on 2006-08-11
There's a known problem with some chipsets, have a look in this thread for some ideas [http://www.ubuntuforums.org/showthread.php?t=217223](http://www.ubuntuforums.org/showthread.php?t=217223).

---

### Post by kentl on 2006-08-12
First I tried disabling IPV6 but it didn't matter. By looking at that thread and trying out things I figured out a way to get networking running.

First have to issue **sudo ifdown eth0** in a terminal. Then I issue **sudo ifup eth0**.

Here is the log: (My comment is marked /* like this */ ):

> kent@kents:~$ sudo ifdown eth0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:50:8d:d9:0b:88
Sending on   LPF/eth0/00:50:8d:d9:0b:88
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.11.5.81 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
kent@kents:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:50:8d:d9:0b:88
Sending on   LPF/eth0/00:50:8d:d9:0b:88
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 10.11.5.81
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.11.5.81
bound to 193.11.128.155 -- renewal in 1568 seconds.
/* 4-6 second wait here before the prompt is given back. Even though it looks like the command is finished already. */
kent@kents:~$


Perhaps of interest?
**lsmod**
> 
kent@kents:~$ lsmod
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
powernow_k8            12680  0
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ac                      5252  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
psmouse                36100  0
af_packet              22920  2
nvidia               4550772  0
agpgart                34888  1 nvidia
rtc                    13492  0
floppy                 62148  0
pcspkr                  2180  0
serio_raw               7300  0
snd_intel8x0           33692  1
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
i2c_nforce2             6912  0
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
i2c_core               21904  3 i2c_acpi_ec,nvidia,i2c_nforce2
sg                     37920  0
evdev                   9856  1
tsdev                   8000  0
ext3                  135688  1
jbd                    58772  1 ext3
usbhid                 39904  0
ide_generic             1536  0
forcedeth              30732  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130692  4 usbhid,ehci_hcd,ohci_hcd
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
generic                 5124  0
amd74xx                15260  0 [permanent]
sd_mod                 19984  3
sata_nv                 9732  5
libata                 78992  1 sata_nv
scsi_mod              139496  5 sr_mod,sbp2,sg,sd_mod,libata
thermal                13576  0
processor              23360  2 powernow_k8,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
kent@kents:~$


Has anyone got any ideas now? Doing those two simple commands results in recieved settings through DHCP. Why doesn't this work during boot? It works in Windows XP *and* when I ran Kubuntu 6.06 Dapper.

---

### Post by kentl on 2006-08-13
Any one?

---

### Post by azmrb on 2006-08-13
This looks like the documented problem with the forcedeth 0.48 driver on a dual-boot machine with windoze.  Windoze leaves the NIC in an unusable state.
Download all of the updates and it should update forcedeth to 0.54 and solve the problem.

---

### Post by drtvasudevan on 2006-08-13
did you go the system>admin>networking way to see the settings and correct them?
after the updates ther eis a bug that does not allow the values to be retained.

---

### Post by kentl on 2006-08-14
azmrb: No it didn't help to upgrade. I still have this problem. It works sometimes though, but that's not very often.

drtvasudevan: They seem pretty much correct in that I'm using DHCP which it is set to. One strange thing is that many information lines talk about IPV6 which I have deactivated (I'm on an IPV4 network). Perhaps I should upload a screenshot?

---

### Post by nefertini on 2006-08-14
it was my problem a couple of minutes ago. just installed fresh copy of ubuntu lst. i got all config right, it connects to wifi but i can't browse. what i did is I installed ndiswrapper. After that my connectivity is OK

---

### Post by mc^2 on 2006-08-14
I have an ethernet card integrated on MB with nVidia nForce5 chipset. The only solution that's proved working is to plug the cord off the computer for some 10 seconds during reboot WinXP->Ubuntu. Windows does something to nForce cards that the kernel module forcedeth can't undo. Maybe there's something similar in your case

---

### Post by kentl on 2006-08-14
I have an nForce4 ethernet card, so I guess we share the same problem. Let's hope that it's something which will be fixed eventually.

---

### Post by tappad on 2006-08-14
Same problem here..

So, there's no "fix" for it yet?

regards

---

### Post by kentl on 2006-08-14
Has anyone of you with the same problem tried [the properiatary drivers](http://www.nvidia.com/object/unix.html) from Nvidia? Perhaps they would work better.

---

### Post by mc^2 on 2006-08-14
If you have a nForce4, there might be a solution -> try to switch to nvnet kernel module instead of forcedeth. Check out: 
[https://wiki.ubuntu.com/NvNetInstallationHowTo](https://wiki.ubuntu.com/NvNetInstallationHowTo)
and thread discussion:
[http://www.ubuntuforums.org/showthread.php?t=86125](http://www.ubuntuforums.org/showthread.php?t=86125)
I didn't manage to make it work on my hardware but nVidia's website says it supports nForce4. nvnet is widely considered a worse driver than forcedeth but if it works...

---

