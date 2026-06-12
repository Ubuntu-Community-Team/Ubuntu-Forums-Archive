---
title: "Wireless card problems"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by rigg-a-mortice on 2009-08-18
I am a refugee from MS Windows XP and the only thing stopping me making the break is the fact that my wifi on my laptop will not connect to my router, but the Ethernet works just fine.


[LIST=1]
[*]Symptoms -
[LIST=1]
[*]When I boot up it does not recognise the wireless router
[*]If I create a wireless network in the network manager and then select it it after a while I am told that the network is disconnected
[/LIST]
[*]Things that I have tried or observed
[LIST=1]
[*]Removing the fire wall makes no difference
[*]I am not currently using security but I am using MAC
[*]I have tried removing the MAC codes from the router but to no avail
[*]It works just fine under Windows XP
[*]When I return to Windows I have to force it to start looking for the Wireless Router
[*]I have tried using the midwifi driver but no different
[*]I have located the windows driver and down loaded it but have no idea at how to find the file with the extension .if
[/LIST]
[*]Information that may help you
[LIST=1]
[*]Computer ASUS X50RL laptop
[*]OS Windows XP Professional
[*]02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
[*]iwconfig = lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
[*]ubuntu-admin@Laura-Laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
radeon                342816  2 
ppdev                  15620  0 
drm                    96424  3 radeon
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434228  6 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  4 snd_hda_intel,snd_pcm_oss
arc4                    9856  2 
ecb                    10752  2 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
ath5k                 107520  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217592  1 ath5k
psmouse                61972  0 
snd                    62756  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  25360  0 
pcspkr                 10496  0 
serio_raw              13444  0 
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
i2c_piix4              18448  0 
output                 11008  1 video
shpchp                 40212  0 
asus_laptop            24440  0 
atl2                   34328  0 
cfg80211               38288  2 ath5k,mac80211
ati_agp                14988  0 
agpgart                42696  2 drm,ati_agp
led_class              12036  2 ath5k,asus_laptop
usbhid                 42336  0 
usb_storage            99648  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
compcache              12876  1 
lzo_decompress         10880  1 compcache
lzo_compress           10880  1 compcache
tlsf                   14092  1 compcache
[*]ubuntu-admin@Laura-Laptop:~$  sudo lshw -C network
[sudo] password for ubuntu-admin: 
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:71:6e:c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: a0
       serial: 00:1e:8c:4f:98:05
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 duplex=full firmware=L2 ip=192.168.1.4 latency=0 link=yes module=atl2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:9d:a4:44:03:42
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[*]iwlist scan wlan0     No scan results
[*]ubuntu 9.04
[/LIST]
[/LIST]
I hope that this information helps, I am at my very limited wits end. Any help greatly appreciated.

---

### Post by PGScooter on 2009-08-18
Hi rigg,

What a nice, organized post. Have you tried searching on google? I did a google search with the following as the query: "ASUS X50RL" ubuntu wireless

It came up with some useful links. See here for example: [http://ubuntuforums.org/showthread.php?t=1074440](http://ubuntuforums.org/showthread.php?t=1074440)

One of the links said that 8.04 worked fine. I would try a 8.04 live cd to see if that does the trick. Even if you don't want to use 8.04, just knowing that it works with it might help.

I wish I could give you better advice, but that's all I have. I really hope things work out! If you get a solution, be sure to post back.

Best of luck!

---

### Post by rigg-a-mortice on 2009-08-20
HI found the answer eventually I needed to chnage a setting as per another post on same topic viz
 				 				**Re: No wifi in 8.10 on ASUS X50RL** 			
 			I did the following:- gksudo gedit /etc/acpi/start.d/60-asus-wireless-led.sh

Then I switched the 1 and 0

The forums are really good if a bit daunting to search
Regards

---

### Post by PGScooter on 2009-08-20
great! I'm glad it worked out for you.

The thing that makes the search less daunting is when the poster with the problem posts back with what worked for him, like you just did!

---

### Post by LewRockwell on 2009-08-20
> **PGScooter said:**
> great! I'm glad it worked out for you.

The thing that makes the search less daunting is when the poster with the problem posts back with what worked for him, like you just did!

yes, kudos for actually providing the solution that worked for you!

many times someone starts a thread and issues a trouble-call, only to receive many replies and various answers/solutions/tests/trials/etc and then there isn't any final disposition from the original poster

and a good, precise, descriptive title and specific specifications are always best!

again, thanks!

.

---

