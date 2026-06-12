---
title: "wifi problem"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by talib on 2009-11-06
hi guys !!
i have Acer Aspire 5315.
and i am a newbie as far as Ubuntu in ubuntu :lolflag:

I just wanted to install the wifi on my ubuntu.. 
while I search the net for howto. 
they suggest to download and install madwifi-ng-r3366+ar5007.tar.gz

but I am having difficulty to find that driver. coz the site is down, can anyone tell me is there any other method !!!

zoro@linux:~$ sudo lspci | grep Atheros
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


thanx in advance

---

### Post by Scunnered on 2009-11-06
Have you actually tried to connect to the wireless network.  I like you have the AR242x802.11 and was able to connect immediately to my wireless network without seeking drivers etc.

You should have no bother effecting a connection. On the top right there is the wireless network connection symbol which if you left click on it will show all the wireless networks available.  Select yours and take things from there.   The symbol might be pale to view but if you pass the cursor along the symbols all will be revealed.

Trust this assists

---

### Post by samh785 on 2009-11-06
> **Scunnered said:**
> I like you have the AR242x802.11 and was able to connect immediately to my wireless network without seeking drivers etc.

You should have no bother effecting a connection. On the top right there is the wireless network connection symbol which if you left click on it will show all the wireless networks available.  Select yours and take things from there.   The symbol might be pale to view but if you pass the cursor along the symbols all will be revealed.

Trust this assists
+1
Normally (at least for me) Ubuntu just recognizes the connection and all I have to do is click the network connection applet to choose my network.

---

### Post by talib on 2009-11-06
> **Scunnered said:**
> Have you actually tried to connect to the wireless network.  I like you have the AR242x802.11 and was able to connect immediately to my wireless network without seeking drivers etc.

You should have no bother effecting a connection. On the top right there is the wireless network connection symbol which if you left click on it will show all the wireless networks available.  Select yours and take things from there.   The symbol might be pale to view but if you pass the cursor along the symbols all will be revealed.

Trust this assists



thanx for ur reply
well there is no wireless networks available for me... 
I have only 2 option to chose there in network connection panel 
1: Wired Netwrok ( which I am using currently )
2:Manual Configration


i will be waiting for ur reply
thanx

---

### Post by teward on 2009-11-06
Could it be a bad wifi card?  Could it be there literally **are no wifi networks nearby**?

Did this computer come with Ubuntu already, or did you install it yourself?

---

### Post by uberg on 2009-11-06
I know this might be a silly question but do you have a wireless connection to connect to?

---

### Post by teward on 2009-11-06
> **uberg said:**
> I know this might be a silly question but do you have a wireless connection to connect to?
-1, I already asked this.

---

### Post by uberg on 2009-11-06
Check the time.  We asked at the same time.  ;-)

---

### Post by talib on 2009-11-06
> **uberg said:**
> Check the time.  We asked at the same time.  ;-)

loooooooool 

yes there are more than 5 according to vista and xp. and one belongs to me and the 4 to my neighbors... 


and my system has 3 OS installed in it.. 
XP 
Vista 
and now ubuntu 
I bet they call it trioboot but I am not sure

:O

---

### Post by lkraemer on 2009-11-07
Here is the link I use:
[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)
and the latest version is:
[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)

Before you try to compile the drivers, Open a Terminal Window and do:
```

lsmod
ifconfig
iwconfig
cat /etc/modprobe.d/blacklist     #(OR for 9.04 and above use:
                                  #cat /etc/modprobe.d/blacklist.conf)


```
and look for the modules that should have loaded, and review the information
for ifconfig, and iwconfig.  Post all the output from all four commands.

To compile you are going to have to make sure all the headers and build essential
items have been installed.  You can try and see if you get any errors.

A search of the forum finds this HOWTO:
[http://ubuntuforums.org/showthread.php?t=1142199&highlight=madwifi](http://ubuntuforums.org/showthread.php?t=1142199&highlight=madwifi)
(cut and paste all commands)

lk

---

### Post by talib on 2009-11-07
> **lkraemer said:**
> Here is the link I use:
[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)
and the latest version is:
[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)

Before you try to compile the drivers, Open a Terminal Window and do:
```

lsmod
ifconfig
iwconfig
cat /etc/modprobe.d/blacklist     #(OR for 9.04 and above use:
                                  #cat /etc/modprobe.d/blacklist.conf)


```
and look for the modules that should have loaded, and review the information
for ifconfig, and iwconfig.  Post all the output from all four commands.

To compile you are going to have to make sure all the headers and build essential
items have been installed.  You can try and see if you get any errors.

A search of the forum finds this HOWTO:
[http://ubuntuforums.org/showthread.php?t=1142199&highlight=madwifi](http://ubuntuforums.org/showthread.php?t=1142199&highlight=madwifi)
(cut and paste all commands)

lk



here is the output of the all 4 commands. and thanx for the reply



zoro@linux:~$ lsmod
Module                  Size  Used by
ipv6                  264356  10 
af_packet              25856  2 
i915                   38656  2 
drm                    86056  3 i915
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20352  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              62180  6 rfcomm,sco,bnep,l2cap
ppdev                  15748  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace      11396  0 
container              11520  0 
pci_slot               12680  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39332  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
acer_wmi               19008  0 
led_class              12164  1 acer_wmi
evdev                  17696  11 
pcspkr                 10624  0 
psmouse                45200  0 
serio_raw              13444  0 
ath_pci                99096  0 
wlan                  212336  1 ath_pci
ath_hal               198864  1 ath_pci
video                  25488  0 
output                 11008  1 video
snd_hda_intel         385072  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
battery                18436  0 
snd_seq_dummy          10884  0 
wmi                    14504  1 acer_wmi
ac                     12292  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 14224  0 
snd                    63396  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
intel_agp              33980  1 
agpgart                42184  3 drm,intel_agp
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133384  1 
jbd                    55956  1 ext3
mbcache                16004  1 ext3
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ata_generic            12932  0 
ata_piix               24708  2 
pata_acpi              12160  0 
libata                178336  3 ata_generic,ata_piix,pata_acpi
scsi_mod              155468  4 sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
tg3                   129924  0 
libphy                 27520  1 tg3
ehci_hcd               43788  0 
uhci_hcd               30864  0 
usbcore               149616  3 ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60956  3 
zoro@linux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:cc:33:53  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fecc:3353/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104136397 (104.1 MB)  TX bytes:2989577 (2.9 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

zoro@linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

zoro@linux:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
zoro@linux:~$

---

### Post by lkraemer on 2009-11-07
Well, now you just need the location that you downloaded the madwifi
drivers to.  insert that path into the following commands to compile
the drivers.  I'd suggest that you cut and paste to prevent errors.

There are two conditions where the MadWifi Drivers might need
to be updated.

1. When a new Kernel has been downloaded and your Wifi doesn't
work.......DO:
(The first two lines will be according to our path to the drivers)
```

cd ~/madwifi_ar5007
cd madwifi-hal-0.10.5.6-r4003-20090416
make clean
make
sudo make install
sudo modprobe ath_pci
sudo /etc/init.d/networking restart

```
Or you can reboot.....If you get errors you will need to install the build essential
and headers.

Now you should be able to connect.  Be advised that a new Kernel download
will require you to repeat the above steps to compile the code again.

lk

---

### Post by talib on 2009-11-09
> **lkraemer said:**
> Well, now you just need the location that you downloaded the madwifi
drivers to.  insert that path into the following commands to compile
the drivers.  I'd suggest that you cut and paste to prevent errors.

There are two conditions where the MadWifi Drivers might need
to be updated.

1. When a new Kernel has been downloaded and your Wifi doesn't
work.......DO:
(The first two lines will be according to our path to the drivers)
```

cd ~/madwifi_ar5007
cd madwifi-hal-0.10.5.6-r4003-20090416
make clean
make
sudo make install
sudo modprobe ath_pci
sudo /etc/init.d/networking restart

```
Or you can reboot.....If you get errors you will need to install the build essential
and headers.

Now you should be able to connect.  Be advised that a new Kernel download
will require you to repeat the above steps to compile the code again.

lk



thanx boss


its working now!!! HEHEHE 
i really  appreciate :) :popcorn:

---

