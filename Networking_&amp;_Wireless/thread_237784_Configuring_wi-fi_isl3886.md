---
title: "Configuring wi-fi: isl3886"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by brazzy on 2006-08-16
Hello!!
I'm completely new to Linux; I am tired of Windows so I'm trying to use Ubuntu 6.06 as much as I can. I had tried Suse 10.1 before, but I had some problems with my wi-fi chipset. I thought that maybe Ubuntu would have been easier, but I was wrong...:cry: 
I've got a Fujitsu-Siemens Amilo D1845 and it has a 
Intersil isl3886 Prism Javelin/Prism Xbow
integrated.
In my house I've made a wireless network, with no Wep or Wpa, and I would like to surf on the web also with Linux.
I've looked for solutions on the forums of all the web, but my knowledge isn't enough to understand where I commit mistakes with ndiswrapper and the .inf driver I use with XP.
Isl3886 gave problems to many, many users: I've searched all across the web and there could be a community only of people in my situation!!!
If it's possible could someone explain me what to do step by step? You would help not just me but a lot of people!!

I don't want to give up on Linux and use Xp forever...
:cry: :cry: :cry: :cry: :cry: 

Thanks a lot!!!

---

### Post by Darkhack on 2006-08-16
If you search for ANY Linux issues online you will find that their could be an entire community for just that bug.  Anyways, it appears as though you are attempting to use ndiswrapper and you do infact have the .inf driver file.  Maybe I can help...

**1.** Applications->Add/Remove Software->Advanced
**2.** Search for "ndiswrapper"
**3.** Install ndiswrapper or ndiswrapper-utils, whatever is displayed
**4.** Open a terminal and do "sudo ndiswrapper -i driver.inf" for whatever the name of the file is and be sure you are in the current directory of where this file is located
**5.** Type "ndiswrapper -l".  You should see "hardware present" next to your device
**6.** "sudo depmod -a"
**7.** "sudo modprobe ndiswrapper"
**8.** You may now configure your device with iwconfig or use the Network Manager under System->Administration.

---

### Post by brazzy on 2006-08-16
Thanks a lot for your reply.

I did exactly as you said, and what I obtained is that after point 4 I was told

**prisma00 is already installed**

(maybe I succeeded in a previous attempt)

then after point 5

[b]Installed ndis drivers:
prisma00        invalid driver![/b]

(I don't understand why... I used XP driver downloaded from Fujitsu-Siemens website)

At last, after point 7,

**FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-23-386/kernel/drivers/ne t/ndiswrapper/ndiswrapper.ko): Invalid argument**

Why??:confused: 

I really don't understand. I see that there's something wrong with my XP driver but I am afraid it's the only one available for my chipset!

---

### Post by brazzy on 2006-08-18
I hope that this can help someone to better understand my problem.
Here's my lspci:

[i]
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 51)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 14)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:09.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
0000:00:09.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
0000:00:09.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
**0000:00:0b.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)**
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
[/i]

And this is lsmod:

[i]
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
radeon                116000  1
drm                    73236  2 radeon
acpi_cpufreq            6792  1
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 acpi_cpufreq,cpufreq_stats
ipv6                  265728  6
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
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
dm_mod                 58936  1
af_packet              22920  2
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
scsi_mod              139496  2 sr_mod,sbp2
lp                     11844  0
irda                  187068  0
joydev                 10048  0
tsdev                   8000  0
usbhid                 39904  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
snd_intel8x0           33692  2
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  2 snd_pcm_oss
islsm_pci              22152  0
islsm_device           12040  1 islsm_pci
islsm                  37644  2 islsm_pci,islsm_device
ieee80211softmac       29696  1 islsm
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
ieee80211              37064  2 islsm,ieee80211softmac
ieee80211_crypt         6272  1 ieee80211
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  2 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
crc_ccitt               2304  2 irda,islsm
pcmcia                 40508  0
pcspkr                  2180  0
rtc                    13492  0
psmouse                36100  0
sis900                 22912  0
yenta_socket           28428  2
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw               7300  0
mii                     5888  1 sis900
i2c_sis96x              5764  0
i2c_core               21904  2 i2c_acpi_ec,i2c_sis96x
sis_agp                 8708  1
agpgart                34888  2 drm,sis_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci1394               35124  0
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130692  4 usbhid,ehci_hcd,ohci_hcd
ieee1394              299832  2 sbp2,ohci1394
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  3
sis5513                17032  1
generic                 5124  0
thermal                13576  0
processor              23360  2 acpi_cpufreq,thermal
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
[/i]

If I install my Win driver with ndiswrapper I'm told it's already installed, if I uninstall it that there's no PRISMA00.inf installed...](*,) 
In Synaptic manager I've installed ndiswrapper-utils only, but there are no other packages in Ubuntu...

Do you know what should I do?

---

### Post by brazzy on 2006-08-18
Finally!!!
I was able to configure my wi-fi card correctly!!
Now I get a
[i]
Installed ndis drivers:
prisma00                driver present, hardware present
[/i]

when I type ndiswrapper -l!!!

How I did it?
From here:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndisgtk&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndisgtk&searchon=names&subword=1&version=dapper&release=all)
I've downloaded a GUI for ndiswrapper (useful for someone like me).
I've uninstalled ndiswrapper and deleted /etc/ndiswrapepr/ folder.

Next step was to delete some mods, islsm_pci, islsm_device and islsm 
so I wrote 
sudo rmmod islsm_pci islsm_device islsm

Then I've installed ndisgtk that I downloaded before and reinstalled ndiswrapper.

This way with the new Windows Wireless Driver GUI I finally made it!!


Now I cannot connect to my wi-fi router, I don't know why!! Both are working, here's my ifconfig with eth0 down:

eth2      Link encap:Ethernet  HWaddr 00:90:4B:89:53:EE
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0xe000 Memory:e0a50000-e0a52000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3324 (3.2 KiB)  TX bytes:3324 (3.2 KiB)

(eth2 is the wireless connection)

and here's iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:"daniele"
          Mode:Auto  Channel=1  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

What's wrong???

---

### Post by brazzy on 2006-08-19
Still no wi-fi connection!! Any idea? Can you suggest any GUI that could help me?

If I write ndiswrapper -l I see that the hardware and driver are ok.
But iwlist scan shows:

[i]lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

_**eth2      No scan results _**

sit0      Interface doesn't support scanning.[/i]

Why? My router is on and it's working: if I use Win XP I have no problems.
I noticed that islsm, islsm_pci and islsm_device mods are back on, althought I had uninstalled them previously (maybe it's ok to have them again 'cause I've installed ndiswrapper once again).

I really don't understand what's the problem: if it was something like ESSID or wep maybe I was able to solve it, but my wi-fi card cannot find any wireless connection...

Maybe it's due to this: when I type iwconfig I get

[i]lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:"daniele"
          Mode:Auto  Channel=14  **Access Point: Invalid**
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.[/i]

Could it be because of the access point?

---

### Post by brazzy on 2006-08-24
I've understood what is the problem with prism54 driver and its islsm, islsm_pci and islsm_device mods: I just cannot get rid of them, everytime I restart my PC they're loaded again and this makes impossible for ndiswrapper to work.
In the beginning I put those mods in the blacklist, I restarted and it seemed to work: wifi card name changed from "eth2" to "wlan0" and ndiswrapper was working correctly. The problem was at the next restart, during "configuring network" Ubuntu freezes.
I restored the situation before, now I wonder if there's another way to unload those mods. A friend suggested to write a script in init.d but I'm afraid I'm not able, or compiling a kernel without prism54.

What do you think? Any help?

---

### Post by bitguy on 2006-10-11
Did you manage to get any further on this? I'm using a Netgear Wg111 but I'm having exactly the same problems as your output and descriptions show - I can't use ndiswrapper becuase islsm gets in the way, yet if I blacklist them the computer hangs at configuring network in the bootup - did you get anywhere on this or did you have to surrender?
thanks in advance!

---

