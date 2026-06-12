---
title: "atheros and 1390 wireless cards"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by dirtsnake on 2007-04-14
ok here is the situation I had my dlink wna 2330 atheros card up and running then I tried to use ndiswrapper to get my internal ipw 1390 running and finally that worked but now my ath0 if gone from the list in iwconfig. If more info is needed to help me just let me know what and how to find it. Thanks \btw I would like to use them both.

---

### Post by dirtsnake on 2007-04-15
bump btw the amount of questions asked is overwhelming here glad to see that linux is growing though

---

### Post by josephus on 2007-04-15
can you post 

```
lshw -class Network
ifconfig -a
```

---

### Post by dirtsnake on 2007-04-16
as soon as I get off work Ill post what the results from that are

---

### Post by dirtsnake on 2007-04-16
here is lshw -class Network```
root@dirtsnake-laptop:~# lshw -class Network
  *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:1a:92:4f:bd:11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.41 firmware=Broadcom,10/12/2006, 4.100.15.5 ip=192.168.1.64 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:efdfc000-efdfffff irq:177
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:55:91:ec
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:efcfe000-efcfffff irq:177
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:32000000-3200ffff irq:185

```
and here is ifconfig -a
```
root@dirtsnake-laptop:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:B9:55:91:EC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:1A:92:4F:BD:11  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe4f:bd11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1319044 (1.2 MiB)  TX bytes:219460 (214.3 KiB)
          Interrupt:177 Memory:efdfc000-efe00000 

```

---

### Post by josephus on 2007-04-16
there's no driver for the ath0 loaded. try:

```
sudo modprobe ath_pci
```

---

### Post by dirtsnake on 2007-04-16
results are as follows ```
root@dirtsnake-laptop:~# sudo modprobe ath_pci
WARNING: Error inserting ath_rate_sample (/lib/modules/2.6.17-10-generic/net/ath_rate_sample.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath_pci (/lib/modules/2.6.17-10-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
then according to dmesg
```
[17179603.804000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179603.804000] IPv6 over IPv4 tunneling driver
[17179613.920000] wlan0: no IPv6 routers present
[17179892.132000] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[17179892.132000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[17179892.132000] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[17180101.404000] video bus notify
[17191704.480000] video bus notify
[17191788.912000] ath_rate_sample: disagrees about version of symbol ath_hal_computetxtime
[17191788.912000] ath_rate_sample: Unknown symbol ath_hal_computetxtime
[17191788.912000] ath_pci: Unknown symbol ath_rate_tx_complete
[17191788.912000] ath_pci: disagrees about version of symbol _ath_hal_attach
[17191788.912000] ath_pci: Unknown symbol _ath_hal_attach
[17191788.912000] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[17191788.912000] ath_pci: Unknown symbol ath_hal_process_noisefloor
[17191788.912000] ath_pci: Unknown symbol ath_rate_attach
[17191788.912000] ath_pci: Unknown symbol ath_rate_newassoc
[17191788.912000] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[17191788.912000] ath_pci: Unknown symbol ath_hal_computetxtime
[17191788.912000] ath_pci: Unknown symbol ath_rate_dynamic_proc_register
[17191788.912000] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[17191788.912000] ath_pci: Unknown symbol ath_hal_mhz2ieee
[17191788.912000] ath_pci: disagrees about version of symbol ath_hal_detach
[17191788.912000] ath_pci: Unknown symbol ath_hal_detach
[17191788.916000] ath_pci: Unknown symbol ath_rate_node_cleanup
[17191788.916000] ath_pci: Unknown symbol ath_rate_detach
[17191788.916000] ath_pci: Unknown symbol ath_rate_node_init
[17191788.916000] ath_pci: Unknown symbol ath_rate_findrate
[17191788.916000] ath_pci: disagrees about version of symbol ath_hal_init_channels
[17191788.916000] ath_pci: Unknown symbol ath_hal_init_channels
[17191788.916000] ath_pci: Unknown symbol ath_rate_newstate
[17191788.916000] ath_pci: Unknown symbol ath_rate_setupxtxdesc
[17191788.916000] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[17191788.916000] ath_pci: Unknown symbol ath_hal_getwirelessmodes

```

---

### Post by josephus on 2007-04-16
not sure if this is related
[http://madwifi.org/ticket/327](http://madwifi.org/ticket/327)

Can you try to disable your broadcom drivers first before trying to load up the atheros drivers again.
```
sudo modprobe -r ndiswrapper
sudo modprobe ath_pci
```

To load up the ndiswrapper again use : sudo modprober ndiswrapper

Also post the results of lsmod

---

### Post by dirtsnake on 2007-04-17
all that did was give me the same error as before  and then I couldnt get back online but i figured that out and here is the results form lsmod 
```
root@dirtsnake-laptop:~# lsmod
Module                  Size  Used by
ipv6                  272288  10 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
i915                   21632  3 
drm                    74644  4 i915
speedstep_centrino      9760  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  2 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dock                    8716  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
ieee80211              35272  0 
ieee80211_crypt         7552  1 ieee80211
ndiswrapper           206228  0 
fuse                   43912  2 
af_packet              24584  4 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
wlan                  212284  0 
ath_hal               192976  0 
pcmcia                 40380  0 
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
joydev                 11200  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
yenta_socket           28812  2 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_timer              25348  1 snd_pcm
b44                    26764  0 
mii                     6912  1 b44
sg                     37404  0 
tsdev                   9152  0 
intel_agp              26012  1 
hw_random               7320  0 
agpgart                34888  3 drm,intel_agp
serio_raw               8452  0 
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
evdev                  11392  2 
psmouse                41352  0 
pcspkr                  4352  0 
ext3                  142728  1 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  4 ndiswrapper,ehci_hcd,uhci_hcd
ide_generic             2432  0 
sd_mod                 22656  4 
sr_mod                 18212  0 
cdrom                  38944  1 sr_mod
generic                 5764  0 
ata_piix               11780  3 
libata                 74892  1 ata_piix
scsi_mod              144648  5 sbp2,sg,sd_mod,sr_mod,libata
thermal                15624  0 
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability
root@dirtsnake-laptop:~# 

```

---

### Post by josephus on 2007-04-17
Sorry I guess I figured I should have been more explicit about getting your interface back up after bringing it down.  If you hadn't figured it out already:

```
sudo modprobe ndiswrapper
sudo ifdown wlan0
sudo ifup wlan0
```

which first reinserts the ndiswrapper, brings the the wlan0 interface (you shouldn't need to do this step, but just in case), and brings up the wlan0 interface again.

But in any case, none of the commands do anything to the configuration files, and so in the worse case a simple reboot will get you running again.

---------------

Anyway,  I still think that we were on track with the last post (did you by any chance read through the madwifi ticket).  I think that the problem was that we weren't explicit enough in unloading the other modules before loading up ath_pci again.

```
sudo modprobe -r ndiswrapper
sudo modprobe -r ath_hal
sudo modprobe -r ath_pci
sudo modprobe -r wlan

```

then make sure you've unloaded all these modules by looking through the list of modules by calling lsmod.  you can use the grep command to help filter through the list.  for instance if you want to only list name which include 'ath'

```
lsmod | grep ath
```

once you've made sure that the modules are unloaded then try loading up ath_pci once again.

```
sudo modprobe ath_pci
```

---------

when you were getting your other wireless card to work did you mess around with the atheros/madwifi drivers, or are these the same drivers that you started with (just in case there is something weird with the drivers themselves).

---

### Post by dirtsnake on 2007-04-17
dont think i messed with the other drivers but then again I dont know half the stuff im doing just following instructions ill try this then ill post my results

---

### Post by dirtsnake on 2007-04-17
root@dirtsnake-laptop:~# sudo modprobe ath_pci
WARNING: Error inserting ath_rate_sample (/lib/modules/2.6.17-10-generic/net/ath_rate_sample.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath_pci (/lib/modules/2.6.17-10-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

that is with everything removed  even.

---

### Post by josephus on 2007-04-18
can you post me your entire dmesg.  you can just add it as an attachment.  the file is found in /var/log/dmesg

-------

maybe you can explain to me what you've done from the last time you remember your atheros card to be working up to the point in time when it stopped working.  either something has changed with the drivers or something is conflicting with the drivers.

------

another thing to try is stop the ndiswrapper from loading up at boot, then rebooting and see if that clear things up.  (right now i'm still assuming that it's related to a conflict with ndiswrapper, unless you give me indication otherwise base my second point.)  

```
sudo gedit /etc/modprobe.d/blacklist

```
add to the end of the file
```

blacklist ndiswrapper

```
if that doesn't work check dmesg and see if you are getting the same message as before.  also to go back to the ndiswrapper, just comment out or delete the line and reboot (if you don't want to reboot right away, then using sudo modprobe ndiswrapper should do the trick.

---

### Post by dirtsnake on 2007-04-18
i believe this is the method i used to make the  internal card work [http://pervasivecomputing.net/ubuntu_edgy_on_dell_inspiron_e1505](http://pervasivecomputing.net/ubuntu_edgy_on_dell_inspiron_e1505)
and my whole dmesg is included
also i trie what you suggested in the last post with no success

---

### Post by dirtsnake on 2007-04-18
bingo got it I just redownloaded the madwifi drivers and re installed then [http://www.marlow.dk/site.php/tech/madwifi](http://www.marlow.dk/site.php/tech/madwifi)
  thank you for your help though dont worry Ill be back with more questions

---

### Post by josephus on 2007-04-18
good.  i was just about to suggest that you reinstall the madwifi drivers, but i'm still unclear as to what actually went wrong.  anyway, glad to hear things work.

---

### Post by dirtsnake on 2007-04-19
ok now if i turn the computer off i have to go through the whole process again how do i make it permanent???

---

### Post by josephus on 2007-04-19
can you tell me which commands you need to use to get the system working each time?

---

### Post by dirtsnake on 2007-04-20
first i sudo modprobe -r ndiswrapper  
then sudo modprobe ath_hal
        sudo modprobe ath_pci as long as there is no errors 
        sudo modprobe ndiswrapper

then they both work but now all of a sudden my wireless signal is crap. and another quick question 
 where can i find the patch for packet injection on my card? or will I need it?

**the wireless signal on the Atheros card that is***

---

### Post by dirtsnake on 2007-04-20
bump this back up front soon as feisty hit i got pushed back 5 pages

---

### Post by dirtsnake on 2007-04-21
bump again page 10 today already

---

### Post by dirtsnake on 2007-04-23
come on guys please

---

### Post by josephus on 2007-04-23
haven't been ignoring your post, just not sure how to help.

are you trying to run both wireless cards at the same time?  that doesn't sound like a good idea to me.

-------------

right now what doesn't work after boot up? is it both wireless cards, or just one wireless card?  which wireless drivers are being loaded up at boot time?  check if you have blacklisted any of the drivers and check dmesg to see what errors are occurring.

---

