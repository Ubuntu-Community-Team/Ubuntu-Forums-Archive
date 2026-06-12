---
title: "Wireless Connection problem"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by NoTG on 2008-03-03
Hello, Ubuntu Newbie here

Ive been searching the forum for an answer to my problem, but no luck, so here it is.

I just recently installed Ubuntu on my hard drive, multi-boot with Windows XP.

I am having problems connecting to my Router, Ubuntu has reconized my wireless adapter (NETGEAR WG111v2) and i can see my router, but when i go to connect, it wont, well, connect. :lolflag:

I have searched around and have tried disabling WEP, MAC filtering and so on, but still no luck.


I am using a NETGEAR WG111v2 Apapter, and a NETGEAR DG384G Router. I have no other wireless adapters or cards plugged in so i doubt its a conflict issue. ( could be wrong since im a newbie )

I am using Ubuntu Desktop Edition 7.10. 

Please help!!:)

---

### Post by NoTG on 2008-03-03
Ok, i have successfully connected to my router now, BUT, im not getting any internet. I cant even login to my router to change settings.
Ive had a look at my connection stats, and everything is 0.0.0.0 ( IP, Subnet, and so on)

My router is configured to automaticly asign an IP address, and its working fine from windows.

Any ideas?:confused::confused::confused:



EDIT: Ok its stopped working again :confused:

---

### Post by sennep on 2008-03-03
Is your SSID hidden?

Are you using your WG111v2 with ndiswrapper?

---

### Post by NoTG on 2008-03-04
No and No, im not using Ndiswrapper, I just installed Ubuntu and my WG111v2 was working since it could pick up my router, but it just wont connect.

---

### Post by sennep on 2008-03-04
I had a similiar problem with mine, it could see the network but it wouldn't connect to the router at all. I ended up using ndiswrapper and I got it working. Some people have got it working without ndiswrapper though.

See the link in my signature if you want to try it the way I did it.

---

### Post by NoTG on 2008-03-04
Thanks, i shall try it out!:)

---

### Post by NoTG on 2008-03-04
I have followed the guide and still no luck.

Any other suggestions?

---

### Post by sennep on 2008-03-05
> **NoTG said:**
> I have followed the guide and still no luck.

Any other suggestions?

That's not a good a sign. 
Let me see that everything went as it should though, could you post the output of these commands?

```
ndiswrapper -l
```

```
lsusb
```

```
lsmod
```

```
iwconfig
```

and the contents of this file: /etc/modprobe.d/blacklist

---

### Post by NoTG on 2008-03-05
I had another go at that guide, and i have now got my adapter working, i can connect to my router with no problems, EXCEPT that i dont seem to have internet. I have checked the connection stats and everything is 0.0.0.0, IP, Subnet, Gateway and so on.

Mr router is a DHCP ( is that right?) so i should be automaticly assigned a IP address i belive, obviosuly this  is not happening since it works fine from wthin Windows.

Any ideas whats wrong now? :lolflag:

---

### Post by Hightide on 2008-03-05
Hi

lets have a look at the output from

```
sudo ifconfig
```

regards

:)

---

### Post by schmildo on 2008-03-05
I've been manually connecting to the net in another flavour of linux. and to use DHCP i need to run the command:

dhclient

from the console, give it a whirl?

---

### Post by NoTG on 2008-03-06
I tried the "dhclient" command, no luck, thanks for the suggestion though.
For some reason i cant connect to my router again!! 

Anyway here are the output to the commands:

ndiswrapper -l

Displayed no output

lsusb

Bus 005 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1532:0101  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

```
lsmod


Module                  Size  Used by
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  0 
cpufreq_userspace       5280  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
container               5504  0 
ac                      6148  0 
sbs                    19592  0 
dock                   10656  0 
button                  8976  0 
video                  18060  0 
battery                11012  0 
lp                     12580  0 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
rc80211_simple          6912  1 
snd_hda_intel         263712  0 
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_ca0106             34720  1 
snd_ac97_codec        100644  1 snd_ca0106
snd_rawmidi            25728  2 snd_seq_midi,snd_ca0106
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
rtl8187                35328  0 
snd_pcm                80388  4 snd_hda_intel,snd_ca0106,snd_ac97_codec,snd_pcm_oss
mac80211              171016  2 rc80211_simple,rtl8187
cfg80211                7304  1 mac80211
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
atl1                   36108  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
snd_timer              24324  2 snd_pcm,snd_seq
eeprom_93cx6            3200  1 rtl8187
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
agpgart                35016  0 
mii                     6528  1 atl1
ac97_bus                3200  1 snd_ac97_codec
snd                    54660  13 snd_hda_intel,snd_seq_oss,snd_ca0106,snd_ac97_codec,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_seq_device,snd_timer
soundcore               8800  1 snd
i2c_viapro             10004  0 
serio_raw               8068  0 
psmouse                39952  0 
snd_page_alloc         11400  3 snd_hda_intel,snd_ca0106,snd_pcm
k8temp                  6656  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
i2c_core               26112  1 i2c_viapro
pcspkr                  4224  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  5 
pata_marvell            8064  0 
via82cxxx              10372  0 [permanent]
ide_core              116804  2 ide_cd,via82cxxx
sata_via               12548  3 
floppy                 60004  0 
ehci_hcd               36492  0 
ata_generic             8452  0 
uhci_hcd               26640  0 
usbcore               138632  5 rtl8187,usbhid,ehci_hcd,uhci_hcd
libata                125168  3 pata_marvell,sata_via,ata_generic
scsi_mod              147084  3 sg,sd_mod,libata
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
```


iwconfig (idle)

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


iwconfig (while trying to connect to my router)

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:AF:33:DA   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=35/64  Signal level=13/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by sennep on 2008-03-06
let's see now...the lsusb command tells me that you have the excact same version of the WG111v2 as I have, so at least we know it's possible to make it work.:)

your lsmod command lists the rtl8187 driver, this is a driver that comes with ubuntu that's supposed to make the WG111v2 work, but in my case it didn't, so I installed a new driver through ndiswrapper. To ensure the rtl8187 driver doesn't conflict with the new driver, the rtl8187 driver needs to be blacklisted. This is done by simply adding it to the blacklist (a document called blacklist found in /etc/modprobe.d/). 
Since the rtl8187 shows up on your lsmod command, I assume the rtl8187 is not blacklisted on your computer? Check your blacklist to see if it's blacklisted. You can gain administrative access to the document either by typing ```
sudo gedit /etc/modprobe.d/blacklist
``` in the terminal, or by typing ```
sudo nautilus
``` in the terminal and locate the document yourself with the file browser that pops up.  (be very careful with this, you can easily damage your system with administrative rights)


Also, check in system-->Administration-->Synaptic package manager that the packages named "ndiswrapper-common" and "ndiswrapper-utils-1.9" are installed on your computer. There should be a checkbox to the left of them and it should be green. If they are not installed, install them.

Also check in synaptic package manager that "ndisgtk" is installed.

---

### Post by NoTG on 2008-03-06
Ok, I have added the rtl8187 driver to the blacklist again, I restarted Ubuntu, and now my router is not being detected so i assume the correct driver has been disabled.

What shall i do now?

I know im an annoying noob. :)

---

### Post by sennep on 2008-03-06
type ```
lsmod
```
and make sure rtl8187 is not listed. If it isn't, then you've sucessfully blacklisted it.

Next step would be to install these packages in synaptic package manager: "ndiswrapper-common",  "ndiswrapper-utils-1.9" and "ndisgtk". The two first you don't need an internet connection for, but the third one you must either get from a wired connection or by downloading it on a computer with internet and putting it on a CD or something like that. Here's the download link: [http://packages.ubuntu.com/gutsy/i386/ndisgtk/download](http://packages.ubuntu.com/gutsy/i386/ndisgtk/download) (you must choose a location to download from). You also need to download [this driver]("http://www.majorgeeks.com/Realtek_RTL8187_USB_Wireless_LAN_ME2000XP_d5165.html") (choose a location). Doubleclick on the ndisgtk file once you have it on your ubuntu computer, then choose "install package".

---

### Post by NoTG on 2008-03-06
Ok, Ndiswrapper and Ndisgtk successfully installed.
rtl8187  is blacklisted.

Downloaded the driver.

I followed your guide again, and when i add the .INF file from the win98 folder, it dosnt appear on the list to the left, it does the same with all the other .INF files aswell.

Any ideas? :confused:

---

### Post by sennep on 2008-03-06
are there any spaces in any folder names in the path to the .inf file? ndisgtk can have some trouble with that. Any non-English characters perhaps?

if you can't get it working, you can also point ndiswrapper to the .inf file manually with the terminal.

just type ```
sudo ndiswrapper -i wherever_your_driver_is.inf
```
"wherever_your_driver_is" is the path to and name of your driver.

Example: sudo ndiswrapper -i /home/sennep/RTL8187/WIN98/Netrtuw.inf

capitalization does matter.

then type ```
sudo depmod -a
```

then type ```
sudo modprobe ndiswrapper
```

and check if it was installed by typing ```
ndiswrapper -l
```

---

### Post by NoTG on 2008-03-06
Alright,  I have now got the driver installed and working, turns out there was a space in the path.

But it still does not connect to my router, i have checked my encryption and password and they are correct, but i CAN connect to my router when Roaming mode is enabled , except i cant access the internet or even the configuration panel of my router.

Ndiswrapper showed the output that the driver was installed and working.

What else can i try?

---

### Post by sennep on 2008-03-07
Are you absolutely positive you cannot connect when roaming is off?

Network manager can take more than a minute to connect, and sometimes it won't succeed until the third or fourth try. In the manual configuration menu, (the one you get by clicking on netwok manager and selecting manual configuration) Try to retype your password and click OK, as this will make it try to connect again. Try a couple times (give it a minute or two each time) and while you do this look in System-->Administration-->Systemlog (and in daemon) to see what dhclient is doing while you are connecting. Is it getting a DHCP offer? How far does it get?

Have you altered any settings other than roaming, SSID (if you can't select this, type it instead), encryption type, password and setting DHCP in that box underneath the password box?

Note that when the connection is manually configured, there is no animation telling you that it is connected since the whole network manager symbol changes, so it will seem like it isn't connected. You can tell if it is connected by looking in the systemlog. (look if you got a DHCPOFFER)

---

### Post by NoTG on 2008-03-07
No  i cannot connect when roaming is off, in the syslog nothing happens.

But with roaming enabled, i can connect to my router, and in the syslog it sends DHCPDISCOVERY about 5 times, then it says NO DHCP offer. That is as far as it gets.

---

### Post by sennep on 2008-03-09
this is getting mighty strange.. When roaming is off, are you able to connect by typing ```
sudo dhclient
``` in the terminal? try a couple times.

Have you altered any settings other than roaming, SSID, encryption type, password and setting DHCP in that box underneath the password box?

Have you tried using different encryption types? Mine works with WPA-PSK (TKIP) at least, I haven't tried others.

Since the driver should be working, this is hopefully just a settings problem.

Just to check something, could you post the output of these commands?

```
sudo lshw -C network
```

```
iwconfig
```

```
ifconfig
```

```
lsmod
```

---

### Post by NoTG on 2008-03-09
I tried the "sudo dhclient" and again it came up with NO DHCPOFFERS, i tried it a couple of times like you said.
I have tried different encryption, even turned it off and it didnt work, and i have not changed any settings other than that in the Network manager.

Here is the output to the commands:

```
sudo lshw -C network

*-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: b0
       serial: 00:1a:92:70:24:4b
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.0.7 firmware=N/A latency=0 link=no module=atl1 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:4d:aa:db:6f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netrtuw driverversion=1.45+Realtek Semiconductor Corp. link=no multicast=yes wireless=IEEE 802.11g
```

```

iwconfig / ifconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


eth0      Link encap:Ethernet  HWaddr 00:1A:92:70:24:4B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0:avah Link encap:Ethernet  HWaddr 00:1A:92:70:24:4B  
          inet addr:169.254.4.150  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:4D:AA:DB:6F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:18:4D:AA:DB:6F  
          inet addr:169.254.8.72  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
```

```
lsmod

Module                  Size  Used by
ipv6                  273892  10 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  0 
cpufreq_userspace       5280  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
container               5504  0 
ac                      6148  0 
sbs                    19592  0 
af_packet              24840  10 
dock                   10656  0 
button                  8976  0 
video                  18060  0 
battery                11012  0 
ndiswrapper           185240  0 
lp                     12580  0 
snd_ca0106             34720  0 
snd_ac97_codec        100644  1 snd_ca0106
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_hda_intel         263712  1 
snd_rawmidi            25728  2 snd_ca0106,snd_seq_midi
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_ca0106,snd_ac97_codec,snd_hda_intel,snd_pcm_oss
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
usbhid                 29536  0 
hid                    28928  1 usbhid
agpgart                35016  0 
i2c_viapro             10004  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  13 snd_ca0106,snd_ac97_codec,snd_seq_oss,snd_hda_intel,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ac97_bus                3200  1 snd_ac97_codec
atl1                   36108  0 
snd_page_alloc         11400  3 snd_ca0106,snd_hda_intel,snd_pcm
mii                     6528  1 atl1
pcspkr                  4224  0 
i2c_core               26112  1 i2c_viapro
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
serio_raw               8068  0 
psmouse                39952  0 
k8temp                  6656  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  5 
pata_marvell            8064  0 
via82cxxx              10372  0 [permanent]
sata_via               12548  3 
ide_core              116804  2 ide_cd,via82cxxx
floppy                 60004  0 
ata_generic             8452  0 
libata                125168  3 pata_marvell,sata_via,ata_generic
scsi_mod              147084  3 sg,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

---

### Post by sennep on 2008-03-09
does your router support IPv6? I see in your lsmod that this is being used, I disabled it a long time ago (but I can't remember why I did it though)

If you want to try disabling it, you can type this in the terminal:

```
sudo gedit /etc/modprobe.d/aliases
```

find the line

alias net-pf-10 ipv6

and change it to read:

alias net-pf-10 off

and save. Then restart.

---

### Post by NoTG on 2008-03-09
I think it is supported, how would i find out? Either way i edited the specific line and restarted, and it didnt work, same thing as always, dosnt connect with Roaming off, and when Roaming is on it gets as far as DHCPDISCOVERY and then a few seconds later i get NO DHCPOFFERS RECIEVED.


So unless you have anything else to suggest, im lost :confused:

EDIT: Could it be possible that my Router does not support Linux at all? ( Probably a stupid question, but might aswell ask)

---

### Post by sennep on 2008-03-12
I don't know much about routers, so I can't really answer your question, I don't think it should matter what router you use, as long as it uses the 802.11 standard, but I might be wrong.



hmmmm... I'm getting really clueless now. It is possible to try to connect at the command line, and this is better for troubleshooting, but it takes an awful lot of typing, so I would try a couple things first before such drastic measures are taken:

I would try to use Wicd instead of network manager. Wicd is easily installed when you have an internet connection, so if you have an ethernet cable that would be the easist way to do it. [Here]("http://wicd.sourceforge.net/download.php") is the guide to install wicd with an internet connection.
If you don't have a cable, I guess you could download a package and install it like you did with ndisgtk. Here's the sourceforge page: [http://sourceforge.net/projects/wicd/](http://sourceforge.net/projects/wicd/)

Both methods should disable network manager automatically, if it doesn't you have to do it manually.

After install, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For the command, enter "/opt/wicd/tray.py".




Second I would try different drivers, not being able to connect to the AP seems like a driver problem to me, but I might be wrong. I noticed our adapters had different MACs, and that made me wonder whether there are more differences between the adapters, and thereby explaining why the driver I use doesn't work on yours. I did a google search and I saw some people reported they had success with [this driver]("ftp://downloads.netgear.com/files/wg111v2_3_3_0_setup.zip"), and [this driver]("ftp://downloads.netgear.com/files/wg111v2_1_3_0.zip") instead of the win98 driver I gave you a link to. I would give it a try, one guy reported having success with the win98 driver, another with the winME and one with winXP driver, so I guess you could try all of them.




I really hope Ubuntu 8.04 that comes out in a month has out-of-the-box support for WG111v2....

---

### Post by NoTG on 2008-03-12
I tried all that, and guess what, it does not work!! :lolflag:

I guess this is turning out to be a real mystery.:(

---

### Post by sennep on 2008-03-12
A mystery indeed.

what does your "/etc/network/interfaces" file look like?

EDIT: Also, what are the first four letters/numbers in your adapter's serial number?

And is there an ethernet cable plugged into your machine?

---

### Post by ugokcu on 2008-03-12
&#305; m using ubuntu 7.10. &#305; m conneting &#305;nternet with cabe. I &#305;nstalled wireless adapter. But network manager didnt see my wireless device. what can I do:(

---

### Post by sennep on 2008-03-12
> **ugokcu said:**
> &#305; m using ubuntu 7.10. &#305; m conneting &#305;nternet with cabe. I &#305;nstalled wireless adapter. But network manager didnt see my wireless device. what can I do:(

What adapter do you have? Do you know the chipset?

---

### Post by ugokcu on 2008-03-12
bcm 4321 ag 802.11a/b/g draft-n wi-fi my device. There is no problem with wire.

---

### Post by sennep on 2008-03-12
I'm not familiar with that specific adapter, I found this link though [http://ubuntuforums.org/showthread.php?t=572005&highlight=broadcom+4321](http://ubuntuforums.org/showthread.php?t=572005&highlight=broadcom+4321)

maybe it is of some help, it seems like a pretty normal ndiswrapper install.

---

### Post by ugokcu on 2008-03-12
thanks a lot my friend. thats nearly same as my laptop. &#305; will try these settings.

---

### Post by NoTG on 2008-03-13
> **sennep said:**
> A mystery indeed.

what does your "/etc/network/interfaces" file look like?

EDIT: Also, what are the first four letters/numbers in your adapter's serial number?

And is there an ethernet cable plugged into your machine?

Interfaces reads:

```
auto lo
iface lo inet loopback
```


4 Letters are: 1AC1

And there is no Ethernet cable plugged in.

---

### Post by sennep on 2008-03-13
that's the same as mine..

I guess I only have this one left for you then: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by NoTG on 2008-03-13
PROBLEM SOLVED.

I switched off encryption, and out of a random thought, i decided to switch MAC Filtering ON.
And it worked!!! :guitar::guitar:


So now i have a working internet connection and a secure wireless Network!!!!

Thanks for all your help its greatly appreciated!!

---

### Post by sennep on 2008-03-13
> **NoTG said:**
> PROBLEM SOLVED.

I switched off encryption, and out of a random thought, i decided to switch MAC Filtering ON.
And it worked!!! :guitar::guitar:


So now i have a working internet connection and a secure wireless Network!!!!

Thanks for all your help its greatly appreciated!!

Thank god for random thoughts:lolflag:

Congratz with internet, finally you can enjoy ubuntu to the max:popcorn:

Remember to turn on updates now that you have internet:grin:

---

### Post by NR1224 on 2008-03-13
First, if you are running 7.10, your stick should be supported natively. I have the same one. :) I was also having trouble logging on until entered the hex phrase instead of the passphrase. hope this helps

---

### Post by NR1224 on 2008-03-13
use the hex key instead of a passphrase. worked for me:guitar:

---

