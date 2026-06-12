---
title: "madwifi wireless problems - atheros 5212 chipset"
date: 2005-10-18
forum: Networking &amp; Wireless
---

### Post by rhinomite on 2005-10-18
UPDATE FIX:
*****************

It seems the problem was hotplug!

Quick Test:
*Stop hotplug
# /etc/init.d/hotplug stop
# /etc/init.d/hotplug-net stop
*Edit /etc/network/interfaces to remove hotplug auto mappings
Comment out the lines immediately under "mapping hotplug"
*Try and connect to your AP

If this works, then its a hotplug issue, if not - i cant help you.

Here are the steps I used to get wireless working again:

(a) Blacklist wifi modules
1. Edit /etc/hotplug/blacklist
2. add your network related modules to the file, in my case they were ath_* and wlan* modules
ath_pci
ath_hal
ath_rate_sample
wlan
wlan_wep
wlan_acl

(b) Change hotplug default policy
1. Edit /etc/default/hotplug
2. Change the line that reads "NET_AGENT_POLICY=hotplug" to "NET_AGENT_POLICY=auto"
Restart and see if you can connect.

Hopefully that will help some of you having issues with wifi under breezy (but had connections in hoary...)

*Don't forget with WEP to use HEX keys directly in the interfaces file. ASCII keys have issues..

Michael.












****************
Hi,

I am having troubles getting wireless working in Breezy after performing clean install from Hoary.

I was previously running hoary with custom kernel from source and the madwifi CVS drivers, which all worked fine using WEP. Now the wireless modules are installed by default in breezy, but I cannot seem to associate with my AP.

I've tried building a custom kernel with madwifi CVS drivers, but I get exactly the same issue (2.6.13.4).

My hardware is as follows:
Sony Laptop - P4 2.4 (PCG-GRZ20)
Gigabyte Wireless PCMCIA (Atheros 5212 chipset)

Assistance would be much appreciated.. :)

Output of **lsmod** gives:
```

wlan_wep                5760  1
ath_pci                69276  0
ath_rate_sample        14088  1 ath_pci
wlan                  122268  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148176  3 ath_pci,ath_rate_sample
nfs                   183624  1
lockd                  55560  2 nfs
sunrpc                129604  3 nfs,lockd
rfcomm                 34972  0
l2cap                  22276  5 rfcomm
bluetooth              41604  4 rfcomm,l2cap
cpufreq_powersave       1920  0
cpufreq_stats           5124  0
cpufreq_userspace       4444  1
cpufreq_ondemand        6172  0
cpufreq_conservative     6948  0
pcmcia                 34576  4
firmware_class          9728  1 pcmcia
sonypi                 21840  0
radeon                 67968  1
drm                    58644  2 radeon
video                  16260  0
battery                 9732  0
container               4608  0
fan                     4868  0
button                  6672  0
thermal                13576  0
processor              23100  1 thermal
ac                      4996  0
pcspkr                  3672  0
rtc                    11576  0
e100                   32512  0
mii                     5120  1 e100
ohci1394               30516  0
yenta_socket           22540  5
rsrc_nonstatic         10880  1 yenta_socket
pcmcia_core            37392  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           30016  1
snd_ac97_codec         72572  1 snd_intel8x0
snd_pcm_oss            45728  0
snd_mixer_oss          16000  1 snd_pcm_oss
snd_pcm                77832  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21636  1 snd_pcm
snd                    45412  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               8800  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
tpm_nsc                 6528  0
tpm_atmel               5504  0
tpm                     9632  2 tpm_nsc,tpm_atmel
hw_random               5268  0
usb_storage            64192  0
uhci_hcd               28560  0
usbcore               104188  3 usb_storage,uhci_hcd
shpchp                 80612  0
pci_hotplug            24756  1 shpchp
intel_agp              21148  1
agpgart                31688  2 drm,intel_agp
tsdev                   7232  0
evdev                   8704  1
joydev                  8896  0
p4_clockmod             4744  0
speedstep_lib           4228  1 p4_clockmod
freq_table              4484  2 cpufreq_stats,p4_clockmod
sbp2                   21384  0
ieee1394               87480  2 ohci1394,sbp2
psmouse                29700  0
mousedev               10528  1
parport_pc             32196  1
lp                     10820  0
parport                31944  2 parport_pc,lp
unix                   24496  638

```

Output of **iwconfig** gives:
```

lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:"<myESSID>"
          Mode:Managed  Frequency:2.457 GHz  Access Point: <myAP>
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Output of **ifconfig** gives:
```

ath0      Link encap:Ethernet  HWaddr <macAddr>
          inet addr: <myIP>  Bcast: <myBcast>  Mask:<myMask>
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:19 dropped:0 overruns:0 frame:19
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Memory:f11c0000-f11d0000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17717 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17717 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1604656 (1.5 MiB)  TX bytes:1604656 (1.5 MiB)

```

Relevant section of **dmesg** gives:
```

[17182713.236000] ath_hal: module license 'Proprietary' taints kernel.
[17182713.260000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17182713.300000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17182713.332000] ath_rate_sample: 1.2
[17182713.388000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17182713.412000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[17182713.412000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKF] -> GSI 9 (level, low) -> IRQ 9
[17182713.868000] Build date: Oct 18 2005
[17182713.868000] Debugging version (IEEE80211)
[17182713.868000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17182713.868000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17182713.868000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17182713.868000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17182713.868000] ath0: mac 5.9 phy 4.3 radio 4.6
[17182713.868000] ath0: Use hw queue 1 for WME_AC_BE traffic
[17182713.868000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17182713.868000] ath0: Use hw queue 2 for WME_AC_VI traffic
[17182713.868000] ath0: Use hw queue 3 for WME_AC_VO traffic
[17182713.868000] ath0: Use hw queue 8 for CAB traffic
[17182713.868000] ath0: Use hw queue 9 for beacons
[17182713.868000] Debugging version (ATH)
[17182713.868000] ath0: Atheros 5212: mem=0x34000000, irq=9

```

Can anyone help me with this one??
Thanks.

---

### Post by netdance on 2005-10-18
And the error you get is?

I'm assuming that you simply can't connect?

You interface file looks like?

I may not be able to help, but I don't see anything indicative in any of your stuff...

---

### Post by rhinomite on 2005-10-18
Thats exactly the point - I can't see any issues with my config. There are no error messages indicating anything being wrong...

I've checked issues with kismet from another computer on the WLAN, i've run ethereal off the server and client, I've also done stupind things like trawl through proc and strace - no indication of anything weird.

:confused:

---

### Post by netdance on 2005-10-20
[QUOTE=rhinomite]Thats exactly the point - I can't see any issues with my config. There are no error messages indicating anything being wrong...

I've checked issues with kismet from another computer on the WLAN, i've run ethereal off the server and client, I've also done stupind things like trawl through proc and strace - no indication of anything weird.

:confused:[/QUOTE]

Check that your WEP password is correct.

If it's wrong, it'll silently fail just like it is for you right now.

I made that mistake and lost a day over it.

BTW - check your old interfaces file and new interfaces file.  If the passkey in the new file starts with "s:" it is not the same as the old file without...

---

### Post by ubutthead on 2005-10-23
I am having the same issue.  All of my configuration's are identical to the one stated above, yet I am unable to do anything with my card.

I'm using the D-Link DWL-G520 in my desktop connecting to a Linksys WRT54-G router/hub.  I know that my WEP encryption key is correct as I typed it in looking directly at it while typing it in.

I have the newest update of madwifi and I'm still lost.  Any help would be greatly appreciated.

---

### Post by malegria on 2005-10-23
Well if it seems all is well then run:
sudo dhclient ath0

It may be just what you needed!

---

### Post by BruceFreeburger on 2005-10-23
I am having the same problem. Madwifi in Breezy 5.10 will not work with WEP encription. I turned WEP off on the router and the wireless connection works again.

  Madwifi and Ubuntu 5.04 worked just fine with 108 wireless and WEP encription, so this is a bug that needs to be fixed.

---

### Post by rhinomite on 2005-10-23
Good to see that I'm not the only one having wierd issues...

I use static routing, but I may give DHCP a go to see if I can associate - worth a go. Will update you with how it goes.

On the weekend I:
*Verified that the WEP keys were identical. Even set up new WEP keys and tested - same issue where laptop won't associate to AP.
*Tried setting up with no security (No WEP) - could not associate to AP.
*Reinstalled fresh O/S (Just in case..) - set up wirelesss and same issue again with no association.

The problem is that everything else in Breezy is working really well on the laptop,  and is significantly faster for this laptop due to what I believe was 'bugginess' with Gnome 2.10 and video drivers. I don't want to roll back if I can afford it...

For those people having troubles, can you post your relevant hardware specs and setup specs (lets see if we can find a common point of failure) - eg:
AP: WRT54g
Crypto: WEP 128bit
Routing: Static
Chipset: Atheros 5212

Michael.

---

### Post by ubutthead on 2005-10-23
Router/Hub - Linksys WRT54G
Wifi Card - D-Link DWL-G520
Chipset - Atheros 5212
IP - static and I've also tried DCHP
Encryption - WEP 128 bit key (tried it with AND without)


I've also tried the : "sudo dhclient ath0"

And I get the following:

```
sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/MAC ADDRESS
Sending on LPF/ath0/MAC ADDRESS
Sending on Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent databse - sleeping.
```

---

### Post by ubutthead on 2005-10-23
I was checking out the "Network Tools" snap-in and for my wireless card - ath0 - under "network device" the card is listed as "Unknown Interface (ath0)"

Also, for the IP Information it had listed IPv6 rather than IPv4 which should be running.  Could this be the root of my problems?

---

### Post by ubutthead on 2005-10-23
ok, so how would one go about editing the configuration file for the WEP key settings?

I realized that I am using the TX key #2 and not #1 - so I would need to go in and change that value, correct?  Even though I did put in the correct Hex key in "iwconfig ath0 key *hex key here*" I would still need to add which TX key to be searching for, like in a Windows environment.

How would I do that?

EDIT:   AHAHAHAHHAHAHA I FIXED IT!!! woohoo!!! now I hope to freaking God I don't have to do this everytime I reboot, lol.  Oh damn this is a good feeling.  First time in Linux and I get this shit working on my own without really getting help.


Just to let you all know.  I had to change the TX key to the default of "1" in my router settings and then manually go in and change the iwconfig ath0 key entry.  Then upon doing so, sudo dhclient ath0 worked and I'm now on the 'net.  :D

---

### Post by rhinomite on 2005-10-24
Ubutthead - do you mind posting the output of:
**lsmod**,
**iwconfig**,
**ifconfig** and
**dmesg**?

Thanks.

---

### Post by claco on 2005-10-24
I'm having the same problems I believe.

My Cisco Aeronet card works like a champ using DHCP and WEP 128 under Breezy.

My DLink DWL-650 does absolutely everything except get a DHCP address with those sames messages:

```

DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3

```

I know it's not the card because that card works under windows, and I know it's not the router because it's the same router that the cisco card connects too.

I've tried every setting I can think of and it just won't get an IP.

You mentioned the key number...is this possibly a difference between how the non madwifi and the madwifi cards config themselfs?

On my cisco card in interfaces, I just specify the key, I don't specify the key number. I wonder if specefying the key number for madwifi cards is required...

**Updated**: I've tried specifying the key number, and that made no difference.

---

### Post by ubutthead on 2005-10-24
[QUOTE=claco]I'm having the same problems I believe.

My Cisco Aeronet card works like a champ using DHCP and WEP 128 under Breezy.

My DLink DWL-650 does absolutely everything except get a DHCP address with those sames messages:

```

DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3

```

I know it's not the card because that card works under windows, and I know it's not the router because it's the same router that the cisco card connects too.

I've tried every setting I can think of and it just won't get an IP.

You mentioned the key number...is this possibly a difference between how the non madwifi and the madwifi cards config themselfs?

On my cisco card in interfaces, I just specify the key, I don't specify the key number. I wonder if specefying the key number for madwifi cards is required...

**Updated**: I've tried specifying the key number, and that made no difference.[/QUOTE]


I don't know if specifying the key number will make a difference if you run "sudo iwlist ath0 key" are there four values in place for the TX key or just one?  If there is only one key in place, then no matter what you specify after TX key #1 will most likely return a null value to the router.

I am still trying to find a way to enter four keys and be able to specify on my router which TX key to use.  If that makes any sense, lol.  Can you tell me which TX key you have your router set to using and if it's the same as the Current TX key listed with the above command?

---

### Post by ubutthead on 2005-10-24
[QUOTE=rhinomite]Ubutthead - do you mind posting the output of:
**lsmod**,
**iwconfig**,
**ifconfig** and
**dmesg**?

Thanks.[/QUOTE]

Not a problem to list these - please note that all pertinent information pertaining to my IP or MAC address will be edited out.  :D

lsmod

```

wlan_wep                5888  1
  ...
ath_pci                69148  0
ath_rate_sample        14344  1 ath_pci
wlan                  120988  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148432  3 ath_pci,ath_rate_sample

```

iwconfig

```

 IEEE 802.11g  ESSID:"udontneedtoknow"
          Mode:Managed  Frequency:2.437 GHz  Access Point: uu:vv:ww:xx:yy:zz
          Bit Rate:18 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=16/94  Signal level=-79 dBm  Noise level=-95 dBm
          Rx invalid nwid:452589  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:30  Invalid misc:30   Missed beacon:24

```

ifconfig

```

 Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:192.168.x.xxx  Bcast:1xx.xxx.x.xxx  Mask:xxx.xxx.xxx.xxx
          inet6 addr: xx00::000:00xx:xx0x:x0x0/00 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:158296 errors:7985797 dropped:0 overruns:0 frame:7985797
          TX packets:113414 errors:30 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:205249517 (195.7 MiB)  TX bytes:15225168 (14.5 MiB)
          Interrupt:17 Memory:f8ee0000-f8ef0000

```

---

### Post by rhinomite on 2005-11-01
*bump - hope this helps..

---

### Post by finni on 2005-11-02
Did not help, was not a hot plug problem at all!

I downloaded the latest wpa supplicant (0.4.6) from universe repo and now my wlan  (atheros 5212 chipset) works again.

EDIT: Well, today after reboot I found out that I dont have wlan anymore. Needed to start dhclient manually and now it started breaking connection every 20 seconds. My wlan used to work flawlessly on hoary. This needs a fix!! :(

PS. I've got HP nc6000 laptop with atheros 5212 chipset wireless.

---

