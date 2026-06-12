---
title: "Cannot connect to WPA Wlan using WICD and Feisty"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by alex77 on 2007-04-23
Heya,

Having some problems getting connected to my router. I am using an Asus P5W DH Deluxe Mobo, with integrated Realtek RTL8187 Wireless network adapter. I am using feisty and wicd. I have uninstalled the network manager and removed rtl8187 from the blacklist, and modprobed rtl8187.

I am attempting to connect to a WPA encrypted network.

Using wicd, the network can be seen, and i can attempt to connect to it. However, it cannot get past the obtaining IP address stage. What is causing this? How can i fix it? I have checked the psk is correct.

This is the output I get from iwlist scan:

```

wlan0     Scan completed :
          Cell 01 - Address: 00:30:54:42:14:36
                    ESSID:"22Castle"
                    Mode:Master
                    Frequency:2.462 GHz
                    Quality=55/64  Signal level=37/65  
                    Encryption key:on
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    Extra:tsf=0000013882e8fe51
```

This is my output from lsmod:

```
Module                  Size  Used by
isofs                  36284  1 
udf                    85252  0 
ipv6                  268704  10 
binfmt_misc            12680  1 
ppdev                  10116  0 
cpufreq_stats           7360  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
container               5248  0 
video                  16388  0 
asus_acpi              17308  0 
button                  8720  0 
dock                   10268  0 
battery                10756  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
ac                      6020  0 
backlight               7040  1 asus_acpi
af_packet              23816  6 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               6784  1 ecb
rc80211_simple          6400  1 
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
rtl8187                34944  0 
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
mac80211              175364  2 rc80211_simple,rtl8187
cfg80211               22920  1 mac80211
snd_seq_dummy           4740  0 
xpad                    9988  0 
snd_seq_oss            32896  0 
eeprom_93cx6            4352  1 rtl8187
sr_mod                 17060  1 
cdrom                  37664  1 sr_mod
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sky2                   43528  0 
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
serio_raw               7940  0 
pcspkr                  4224  0 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
psmouse                38920  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  3 
pata_jmicron            7808  1 
ata_piix               15492  2 
ata_generic             9092  0 
usbhid                 26592  0 
hid                    27392  1 usbhid
generic                 5124  0 [permanent]
floppy                 59524  0 
ahci                   22020  0 
libata                125720  4 pata_jmicron,ata_piix,ata_generic,ahci
scsi_mod              142348  5 sbp2,sr_mod,sg,sd_mod,libata
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  6 rtl8187,xpad,usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

I attach a screenshot of wicd before I press connect.

Thanks
Alex :)

---

### Post by alex77 on 2007-04-23
Quick update:

I have now installed ndiswrapper and am using the win98 drivers from my mobo cd. Exact same as before- cant obtain an IP address.

 I have looked on my router at associated stations, and it gives the status of my connection as "auth key", whereas all the other computers (windows) on the network are "Authorized". This leads me to believe that the password is wrong, but I  have checked and see it is correct. Is there anything else that would prevent my router from letting my computer connect?

---

### Post by p252 on 2007-04-23
Are you using WPA2 or just WPA? I couldn't get WPA2 to work so I resorted to WPA which let me connect. Also, I'm not sure how you are set up, but, does your router use MAC filtering for wireless? If you laptops MAC isn't listed in there than you would also get a problem similar to what you are describing.

---

### Post by alex77 on 2007-04-23
No, just bog standard WPA. Also Mac filtering is off.

---

### Post by alex77 on 2007-04-23
By the way, everything works with WPA off, but thats not really desirable. Can anyone think of what i'm doing wrong?

---

### Post by alex77 on 2007-04-23
Update on iwlist scan output

it does this now:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:30:54:42:14:36
                    ESSID:"22Castle"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
```

---

### Post by shakma on 2007-06-21
> **alex77 said:**
> Heya,

Having some problems getting connected to my router. 

I am attempting to connect to a WPA encrypted network.

Using wicd, the network can be seen, and i can attempt to connect to it. However, it cannot get past the obtaining IP address stage. What is causing this? How can i fix it? I have checked the psk is correct.


Thanks
Alex :)

I am having the *excact* same problem with a D-Link DWL-G510 (rev. B1).  I could connect fine without any encryption, but with WPA I cannot get past the "Obtaining IP Adress" point.  PSK is definitely correct, and at least three other (Windoze) laptops all connect fine.

Thanks in advance.  Peace.
shakma

---

### Post by kgr132 on 2007-06-27
Same problem here. If I turn off encryption on the router for my wireless link, I can connect fine. As soon as I enable WPA encryption, Wicd fails to connect. My router lists my laptop by the wireless card's MAC ID and says that it's "Unauthorized". Just in case, I've even tried a very simple (only letters and numbers) pass phrase for the WPA. Yes, I also tried using quotes around the pass phrase, like I read in a different thread. These changes made no difference. I can't very well leave my network wide open. Any suggestions?

---

### Post by alex77 on 2007-07-15
Saw this posted on my other thread, not tried it out yet, but i guess its worht a shot.

Anyone else got any success stories?


> **bollix47 said:**
> I also have the Asus P5 deluxe wifi and mine is working so I'll list the changes I made to a clean install.

First, ensure the wpasupplicant is installed.  Check in synaptic or in a terminal type:

```
sudo apt-get install wpasupplicant
```

Edit /etc/network/interfaces

```
sudo gedit /etc/network/interfaces
```

Ensure your wlan0 portion looks like:

```
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

```


Edit /etc/wpa_supplicant.conf

```
sudo gedit /etc/wpa_supplicant.conf
```

Insert the following into the above file:

```
network={
        ssid="YourEssid"
        proto=WPA
        key_mgmt=WPA-PSK
        psk=Your wpa key
}
```

You could try this with or without Network Manager enabled.

System > Preferences > Sessions

Insert or remove checkmark next to Network Manager.

I've never tried wicd.


Hope this helps.

---

### Post by odiseo77 on 2007-07-15
Maybe either way should work, but this is the way I've managed to connect to my router using WPA encryption: edit /etc/network/interfaces: ***gksu gedit /etc/network/interfaces*** and put something like this in it:

```
auto eth1
iface eth1 inet dhcp
pre-up iwconfig eth1 essid YOUR_ESSID
pre-up iwconfig eth1 mode Managed
pre-up iwpriv eth1 set Channel=11
pre-up iwpriv eth1 set AuthMode=WPAPSK
pre-up iwpriv eth1 set EncrypType=TKIP
pre-up iwpriv eth1 set WPAPSK=YOUR_HEX_OR_ASCII_PASSWD
pre-up iwpriv eth1 set TxRate=0
```

Change eth1 for your wireless device (wlan0, I think). Then run:

 ```
/etc/init.d/networking start
```

Hope it works for you.

---

### Post by imdano on 2007-07-15
The problem in many of these cases is that ralink cards don't support wpasupplicant properly, which wicd uses to handle wpa connections.  The good news is we've got a fix for it that's working for the people who have tested it, and it will be included in the next release.

---

### Post by alex77 on 2007-07-16
Next release? So october then? I'm still fairly new to all this, so just wondering, is there any way to get the fix early? Where would i find it?

Thanks :)

---

### Post by imdano on 2007-07-16
No, wicd releases new versions much quicker than that, usually every couple of months.  We just released a stable version, and a new experimental one should be coming along soon that will have the fix for ralink cards.  You can use it early though, you'll just have to replace a few files.  I've attached the 2 files you'll need, gui.py and networking.py (you'll need to unzip them).  Put them in the /opt/wicd/ directory.  Before you try the fix, make sure it will work to you by running the command ```
iwpriv <wireless interface> get_site_survey
```  If you don't receive an error than this will probably work for you.  Also make sure you're using version 1.3.1.  Then follow these instructions:

1. Close the wicd tray.
2. Kill the wicd daemon by opening a terminal and running ```
sudo /etc/init.d/wicd stop
```
3. Put the new files in the /opt/wicd/ directory.
4. Run /opt/wicd/tray.py, which will automatically launch the daemon for you.
5. Open up the gui, click preferences, and change "WPA Supplicant Driver" to "ralink legacy".
6. Try to connect

Keep in mind this is still in the testing phase and it may not work properly or be buggy.  Let me know if you have trouble and I'll to help you figure out what's going wrong.

---

### Post by alex77 on 2007-07-16
You are an awesome person- I will go try this now :)

Thanks very much!

---

### Post by shakma on 2007-07-16
Just a quickie.  My WPA w/PSK has been working _beautifully_ since the 1.3.1 release.  Thanks, Wicd!

Peace.
shakma

---

### Post by alex77 on 2007-07-16
Hmmm, no joy. I'm sure its an easy fix though, but as i am totally useless at this Linux stuff I appear to have broken things that worked fine before, for example iwlist scan no longer works.

I installed the latest wicd and then tried to connect, which didnt do anything - tho wicd automatically detected the network and that it was using wpa...

anyway, here is some output of things i tried:

```
bash3.2 User alex on host blue in dir ~
Mon Jul 16 18:12:07>  /opt/wicd/tray.py
attempting to connect daemon...
daemon not running, running gksudo ./daemon.py...
daemon still not running, aborting.
Traceback (most recent call last):
  File "/opt/wicd/tray.py", line 7, in <module>
    import edgy
  File "/opt/wicd/edgy.py", line 44, in <module>
    wireless = dbus.Interface(proxy_obj, 'org.wicd.daemon.wireless')
NameError: name 'proxy_obj' is not defined
```

```
bash3.2 User alex on host blue in dir ~
Mon Jul 16 18:14:41>  lsmod
Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
isofs                  36284  1 
udf                    85252  0 
ipv6                  268704  10 
binfmt_misc            12680  1 
ppdev                  10116  0 
fglrx                 540004  11 
agpgart                35400  1 fglrx
cpufreq_stats           7360  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
container               5248  0 
video                  16388  0 
asus_acpi              17308  0 
button                  8720  0 
dock                   10268  0 
battery                10756  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
ac                      6020  0 
backlight               7040  1 asus_acpi
af_packet              23816  10 
ndiswrapper           194608  0 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
sr_mod                 17060  1 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
cdrom                  37664  1 sr_mod
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 26592  0 
hid                    27392  1 usbhid
xpad                    9988  0 
serio_raw               7940  0 
psmouse                38920  0 
sky2                   43528  0 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pcspkr                  4224  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  4 
usb_storage            72256  1 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  5 
libusual               17936  1 usb_storage
pata_jmicron            7808  1 
ata_piix               15492  2 
ata_generic             9092  0 
uhci_hcd               25360  0 
floppy                 59524  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ahci                   22020  0 
libata                125720  4 pata_jmicron,ata_piix,ata_generic,ahci
scsi_mod              142348  6 sbp2,sr_mod,usb_storage,sg,sd_mod,libata
ehci_hcd               34188  0 
generic                 5124  0 [permanent]
usbcore               134280  8 ndiswrapper,usbhid,xpad,usb_storage,libusual,uhci_hcd,ehci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 

```

This did work before, i must have done something to break it:

```
bash3.2 User alex on host blue in dir ~
Mon Jul 16 18:14:57>  iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable
```

Thanks for helping :)

Also, my card is a realtek one, not ralink. is that important? I'm using ndiswrapper with the windows 98 drivers for my card (realtek rtl8187).

---

### Post by walkerk on 2007-07-16
if you can connect with wireless w/out wpa your wireless driver and ndiswrapper are working correctly. try changing your wpa driver in wicd..

maybe try 'ndiswrapper' instead of 'wext' ... here are a few more:
```
hostap
(default) Host AP driver (Intersil Prism2/2.5/3). (this can also be used with Linuxant DriverLoader). 
hermes
Agere Systems Inc. driver (Hermes-I/Hermes-II). 
madwifi
MADWIFI 802.11 support (Atheros, etc.). 
atmel
ATMEL AT76C5XXx (USB, PCMCIA). 
wext
Linux wireless extensions (generic). 
ndiswrapper
Linux ndiswrapper. 
broadcom
Broadcom wl.o driver. 
ipw
Intel ipw2100/2200 driver. 
wired
wpa_supplicant wired Ethernet driver 
bsd
BSD 802.11 support (Atheros, etc.). 
ndis
Windows NDIS driver.
```

---

### Post by alex77 on 2007-07-16
Yeah, it all works fine without WPA.

I did try all the different options for drivers that were in WICD, but to no avail. :(

---

### Post by imdano on 2007-07-16
Ah ok, if you're using nsdiswrapper then you don't need that ralink fix, I should have read the thread more carefully.  Also, did you get that error running the modified version of wicd I sent you, or the default 1.3.1?  It looks like daemon.py is failing to start based on the message, probably due to an error in the code I sent you (my fault again).  You might want to try connecting to a wpa network using the command line, so that you can see what error message you're getting during the connection process.  First, check your /opt/wicd/encryption/configurations folder for files.  There should be one in there with your WPA network's BSSID (MAC address) on it.  Open it up (you'll probably need to use sudo because of the persmissions on the file).  It should look a little like this:```
ap_scan=1

network={
       ssid="<your networks essid>"
       scan_ssid=0
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=<really long string of hex characters>
}
```If it doesn't, then something is going wrong trying to create the wpa_supplicant configuration file.  If it does appear, try running these commands ```
ifconfig wlan0 down
ifconfig wlan0 0.0.0.0
sudo killall dhclient wpa_supplicant dhclient3
sudo wpa_supplicant -B -D ndiswrapper -i wlan0 -c /opt/wicd/encryption/configurations/<your config 
file>
ip route flush dev wlan0
ifconfig wlan0 up
iwconfig wlan0 mode managed
iwconfig wlan0 essid <your network's essid>
iwconfig wlan0 channel <you network's channel>
sudo dhclient wlan0
```Be sure to post any error you get while trying that.  If the wpa_supplicant command fails try using "-D wext" instead of "-D ndiswrapper". If you don't see a configuration file for your network, let me know and we'll see if we can figure out why it's not getting generated.  A good place to start would be to check and see if it's able to generate your psk by running ```
wpa_passphrase <your network's essid> <your ascii password>
```

---

### Post by ittiam on 2007-07-16
This works. This is how I set up my WPA.
> **alex77 said:**
> Saw this posted on my other thread, not tried it out yet, but i guess its worht a shot.

Anyone else got any success stories?

---

### Post by alex77 on 2007-07-16
Nope, did all that but it still hangs at obtaining IP address...

The config file is being made fine, but i did get a couple errors trying those commands:

```
bash3.2 User alex on host blue in dir ~
Mon Jul 16 21:41:45>  sudo killall dhclient wpa_supplicant dhclient3
dhclient3: no process killed
```

```
bash3.2 User alex on host blue in dir ~
Mon Jul 16 21:44:13>  ip route flush dev wlan0
Nothing to flush.
```

```
bash3.2 User alex on host blue in dir ~
Mon Jul 16 21:45:47>  sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6680
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:15:af:03:59:7d
Sending on   LPF/wlan0/00:15:af:03:59:7d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```


Also, iwlist scan works again:

```
bash3.2 User alex on host blue in dir ~
Mon Jul 16 21:46:41>  iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:30:54:42:14:36
                    ESSID:"22Castle"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
```

Also, i'm guessing this means ndiswrapper was installed ok?

```
bash3.2 User alex on host blue in dir ~
Mon Jul 16 22:10:32>  ndiswrapper -l
netrtuw : driver installed
        device (0BDA:8187) present (alternate driver: rtl8187)
```

---

### Post by imdano on 2007-07-16
All of that output is normal, except that you're not able to get a dhcp offer.  Is your wpa key really long, or are you entering the psk (hex version of the key that's a bunch of random characters) instead of the passphrase?

---

### Post by alex77 on 2007-07-16
I am using the ASCII version of the key for everything, but it is quite long: 64 characters. The key works fine for all the windows computers on the network though...

---

### Post by imdano on 2007-07-16
if you run ```
wpa_passphrase <your essid> <your passphrase>
``` does it output a psk?  Linux wants a passphrase 8-63 characters, so that might be your problem.  Windows for some reason is able to use keys (like ones with non-alphanumeric characters) that Linux can't.

---

### Post by alex77 on 2007-07-17
No, it doesn't work, gets an error. Though it does seem to work in the config file...

Will try changing my key to something simpler now.

---

### Post by alex77 on 2007-07-17
Nope, still doesn't get past obtaining IP address. I will leave it using the simpler passphrase though.

---

### Post by ittiam on 2007-07-17
Ok. 

You did run this, right?

> sudo wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf

After running this can you post the output of > iwconfig

---

### Post by imdano on 2007-07-17
That new passphrase worked with wpa_passphrase I take it?  Ittiam, his wpa_supplicant config file is in another folder (/opt/wicd/encryption/configurations/), I don't think he has one (at least not one with anything in it) in /etc/.

---

### Post by ittiam on 2007-07-17
Sorry should have made my post more clearer. 

So you have to start wpa_supplicant using the command I had already mentioned.

/etc/wpa_supplicant.conf is where usually people have their conf file. If you have it in some other path..just add it after the -c option of wpa_supplicant.

I am not sure whether you are connected to access point or ur wireless router before you do your dhcp.

---

### Post by alex77 on 2007-07-17
> **imdano said:**
> That new passphrase worked with wpa_passphrase I take it?  Ittiam, his wpa_supplicant config file is in another folder (/opt/wicd/encryption/configurations/), I don't think he has one (at least not one with anything in it) in /etc/.

Yeah, new passphrase works with wpa_passphrase

---

### Post by alex77 on 2007-07-17
> **ittiam said:**
> Ok. 

You did run this, right?



After running this can you post the output of

```
bash3.2 User alex on host blue in dir ~
Tue Jul 17 18:33:28>  sudo wpa_supplicant -Bw -Dwext -iwlan0 -c/opt/wicd/encryption/configurations/003054421436

bash3.2 User alex on host blue in dir ~
Tue Jul 17 18:33:32>  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr=2432 B   Fragment thr=2432 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Also, iwlist scan stopped working after i did this- says that the resource is temporarily unavailable

---

### Post by ittiam on 2007-07-17
Well as suspected you are not associated with ur router or AP. Since you are using WICD there is sometimes problem with the password, in your conf file try enclosing the password within quotations and then re run the wpa_supplicant command. and after this post iwconfig again.

---

### Post by ittiam on 2007-07-17
If the above suggestion fails, one more thing, make ur conf  file for wpa_supplicant has these

```

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="your_ssid"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk="your_psk"
}
```

---

### Post by imdano on 2007-07-17
Does running the wpa supplicant file by itself associate you with the access point?  I thought you also had to provide iwconfig/ifconfig commands to do that?

---

### Post by ittiam on 2007-07-17
Yea running wpa_supplicant associates you with the access point. You can see that happening when you run it without -Bw option (ie not as daemon). iwconfig and ifconfig just enlist the interfaces

---

### Post by walkerk on 2007-07-17
> **imdano said:**
> Does running the wpa supplicant file by itself associate you with the access point?  I thought you also had to provide iwconfig/ifconfig commands to do that?

no.. wpasupplicant only sets up your wpa.. you still need something such as wicd or wifi-radar that uses ifup/ifdown..


i wrote [this thread on setting up wpa with wifi radar awhile ago]("http://ubuntuforums.org/showthread.php?t=478612").. though no one seemed to like it.. probably because network-manager worked ok for them.. also this was before wicd..

i have my wpa_supplicant set up just like the above link.. being that i did this before installing wicd.. wifi-radar still works great but i find wicd more user friendly. i only wanted a daemon that brought my wlan nic up and connected automatically.. which both do..

---

### Post by alex77 on 2007-07-17
ok, just done what you said, still no change i'm afraid :(

```


bash3.2 User alex on host blue in dir ~
Mon Jul 16 18:14:41>  lsmod
bash3.2 User alex on host blue in dir ~
Tue Jul 17 20:15:35>  sudo wpa_supplicant -Bw -Dwext -iwlan0 -c/opt/wicd/encryption/configurations/003054421436

bash3.2 User alex on host blue in dir ~
Tue Jul 17 20:16:08>  iwconfiglo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr=2432 B   Fragment thr=2432 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


bash3.2 User alex on host blue in dir ~
Tue Jul 17 20:16:11>  iwlist scanlo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:30:54:42:14:36
                    ESSID:"22Castle"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK


```

also, added that second bit to the config file

Thanks for helping :)

---

### Post by kevdog on 2007-07-17
I take it you have seen the WPA instructions from the ndiswrapper website:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/)

Not sure if this will help you!

---

### Post by imdano on 2007-07-17
Your wicd is broken!  It's probably because of the networking.py I sent you.  Reinstall it (or just replace the networking.py and gui.py files with the ones from the 1.3.1 source you can get from the wicd website) and it should be all set.  If you haven't been able to run wicd since you changed your wpa key that might be your problem, since the key in the configuration file in opt/wicd/encryption/configurations/<your bssid> never got updated to the new one, so while you've been trying to manually connect it's been using the old psk.

---

### Post by alex77 on 2007-07-17
No, its not from that file. After that file you sent didnt work i completeley removed wicd and reinstalled it...

---

### Post by ittiam on 2007-07-17
Are you using ASCII or the hex dump using wpa_passphrase in your conf file? If you are using ASCII can you try using the hex dump as your psk. Remember  enclose the key with quotes and also can u show how ur conf file looks like?

---

### Post by imdano on 2007-07-17
He said earlier that he was giving the ascii key to wicd, which converts to the hex version automatically.  I think his problem might be that the key in there right now is the wrong one.

---

### Post by alex77 on 2007-07-17
I am using the hex with added quotes in the conf file, and the ascii in wicd. I will post copy of conf file in couple mins, need to reboot out of windows

---

### Post by imdano on 2007-07-17
Whoa, am I losing it or did you have an error message from the tray.py in a post on the previous page that's not there anymore?

edit: Oh I see you edited.  So wicd is working then?  And the psk you get when running "wpa_passphrase <your essid> <your passphrase>" matches the key in your /opt/wicd/encryption/configurations file?

---

### Post by ittiam on 2007-07-17
You can try having a look into this, [http://ubuntuforums.org/archive/index.php/t-424370.html](http://ubuntuforums.org/archive/index.php/t-424370.html)

---

### Post by alex77 on 2007-07-17
Yeah wicd works fine (just doesn't connect with WPA), i just pasted the wrong stuff into the reply window. sorry for any confusion ...

here is the contents of my conf file

```
ap_scan=1

network={
       ssid="22Castle"
       scan_ssid=0
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=14ee0ea91264dc6e9c7edb854161d09bbb199a987c00d1c80236a0b897471e1b
}
```

Also, i have a wpa_supplicant.conf file in etc/ that still has the old key in it. Is this file even used if i am using wicd?

```
ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="22Castle"
	key_mgmt=WPA-PSK
	proto=WPA
	pairwise=TKIP
	group=TKIP
	psk="OpT3nHg5%&oepr95f+==-:;@shcn!uiPPJfnc~?>393uyvhsUjj865$fg6jedQ"
}

```

---

### Post by alex77 on 2007-07-17
> **ittiam said:**
> You can try having a look into this, [http://ubuntuforums.org/archive/index.php/t-424370.html](http://ubuntuforums.org/archive/index.php/t-424370.html)

Thanks, I have wicd installed and have removed network manager, but sadly WPA still wont work. Wicd works fine without wpa, but thats not ideal.

---

### Post by ittiam on 2007-07-17
[This link]("http://xx.joeuser.com/index.asp?AID=156640") says it is important that we enclose the psk in quotes. In the conf file that you are using (not /etc/wpa_supplicant.conf) I dont see quotes for the psk. And also since wicd is supposed to take care of wpa_supplicant...whenver you are trying to set up wpa using wicd try gving quotes to psk. Other than this i feel hard to give other suggestions

---

### Post by alex77 on 2007-07-17
Yeah, I had enclosed the psk in quotes, and added that second chunk you told me too, but it seems that whenever i start wicd it re-creates that file automatically.

---

### Post by alex77 on 2007-07-17
> **ittiam said:**
> whenver you are trying to set up wpa using wicd try gving quotes to psk.

Haven't tried doing that in wicd yet, will do so now. Thanks for all your help :)

---

### Post by ittiam on 2007-07-17
So whenever you use WICD to specify the parameters for wpa put the ascii key in quotes and then check how the conf file is generated.

*edit: Sorry saw your reply after i posted this. Redundant.

---

### Post by ittiam on 2007-07-17
Just specify the wpa parameters as mentioned (ASCII key with quotes). Dont run wpa_supplicant command after that. Check iwconfig

---

### Post by alex77 on 2007-07-17
ok, just did that, no difference :(

---

### Post by imdano on 2007-07-17
Have you tried more than one type of driver with the new psk?

---

### Post by alex77 on 2007-07-17
nope, i was just using the ndiswrapper one. Will give that a go now.

---

### Post by imdano on 2007-07-17
Try wext.

---

### Post by ittiam on 2007-07-17
U havent tried wext till now?

---

### Post by alex77 on 2007-07-17
nope, tried the whole lot (including wext). no joy :(

---

### Post by ittiam on 2007-07-17
I think we have messed too much with configs. So my last suggestion is this, to start from scratch
```
[LIST=1]
[*]sudo pkill wpa_supplicant
[*]sudo modprobe -r ndiswrapper
[*]sudo modprobe ndiswrapper
[*]Use WICD set the driver to ndiswrapper, wpa config with ascii key within quotes
[*]iwconfig[/LIST]
```

---

### Post by alex77 on 2007-07-17
right, will do that now

thanks :)

---

### Post by alex77 on 2007-07-17
No joy :(

Oh well, thanks for all your help guys.

---

### Post by kevdog on 2007-07-17
Can you connect to your router manually???  Meaning without the use of WICD through the command line??

Update your wpa_supplicant.conf file to your new settings (I know you recently posted an older version)

You are going to need two command prompt windows, and just type your WPA-PSK password for now in plain ascii with quotes.

Something like this:

ctrl_interface=/var/run/wpa_supplicant
 network={
   ssid="myssid"
   psk="mysecret"
   key_mgmt=WPA-PSK
   proto=WPA
 }

should suffice. Note that psk given above can be plain text ASCII pass phrase that is used on the AP or hex digits (without quotes) that can be generated with wpa_passphrase from the same ASCII pass phrase. For simplicity, go with ASCII pass phrase.

Above configuration causes wpa_supplicant to negotiate which encryption scheme to use. Certain AP’s might not work with this negotiation procedure. So it can help to limit the scheme to the most basic WPA one: TKIP. Add this line to your config to do so: pairwise=TKIP

Now start the interface and then wpa_supplicant. For example, as

ifconfig wlan0 up
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd

Note: With ndiswrapper version 1.12 and older, use -Dndiswrapper instead of -Dwext.

Now configure the network interface; e.g., if you are using a DHCP you may need to run
dhclient wlan0 

The option -dd to wpa_supplicant gives lot of output so you can see if there is a problem. If everything works, you can drop -dd option.

---

### Post by ittiam on 2007-07-17
Yea i was about to give the same suggestion. Try connecting to the router manually without using WICD. you can follow the same steps in my previous post except for the 4th one where you have to use wpa_supplicant command

the command is sudp wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf

use wpa_supplicant.conf, dont use quotes for ur psk here.

---

### Post by alex77 on 2007-07-18
Sorry for late reply, heres the output of the stuff you told me to run:

Conf file with quotes:
```
bash3.2 User alex on host blue in dir /etc
Wed Jul 18 13:04:27>  cat /etc/wpa_supplicant.conf
# WPA-PSK/TKIP

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="22Castle"
        psk="h0lst3n15Ab3erN3thy"
        key_mgmt=WPA-PSK
        proto=WPA
        pairwise=TKIP
        group=TKIP
        }
```

```
bash3.2 User alex on host blue in dir /etc
Wed Jul 18 12:57:37>  sudo ifconfig wlan0 up

bash3.2 User alex on host blue in dir /etc
Wed Jul 18 12:57:46>  wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 5 - start of a new network block
ssid - hexdump_ascii(len=8):
     32 32 43 61 73 74 6c 65                           22Castle        
PSK (ASCII passphrase) - hexdump_ascii(len=19): [REMOVED]
key_mgmt: 0x2
proto: 0x1
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='22Castle'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: Operation not permitted
ioctl[SIOCSIWMODE]: Operation not permitted
Could not configure driver to use managed mode
SIOCSIFFLAGS: Permission denied
Could not set interface 'wlan0' UP
SIOCGIWRANGE: WE(compiled)=21 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
socket(PF_PACKET): Operation not permitted
Failed to add interface wlan0
State: DISCONNECTED -> DISCONNECTED
Segmentation fault (core dumped)

bash3.2 User alex on host blue in dir /etc
Wed Jul 18 13:01:36>  sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 6049
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:17:31:ee:e1:50
Sending on   LPF/eth1/00:17:31:ee:e1:50
Listening on LPF/eth0/00:17:31:e8:f0:59
Sending on   LPF/eth0/00:17:31:e8:f0:59
Listening on LPF/wlan0/00:15:af:03:59:7d
Sending on   LPF/wlan0/00:15:af:03:59:7d
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 
```

Conf file without quotes:

```
bash3.2 User alex on host blue in dir /etc
Wed Jul 18 13:05:48>  wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 5 - start of a new network block
ssid - hexdump_ascii(len=8):
     32 32 43 61 73 74 6c 65                           22Castle        
Line 7: Invalid PSK 'h0lst3n15Ab3erN3thy'.
Line 7: failed to parse psk 'h0lst3n15Ab3erN3thy'.
key_mgmt: 0x2
proto: 0x1
pairwise: 0x8
group: 0x8
Line 12: WPA-PSK accepted for key management, but no PSK configured.
Line 12: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface wlan0
Cancelling scan request

```

---

### Post by kevdog on 2007-07-18
Try the password in quotes, meaning the ascii password, not the hexidecimal equivalent. Also preface the wpa_supplicant command with sudo.

---

### Post by alex77 on 2007-07-18
ok, tried it with sudo, and it went into an infinite loop of almost getting there but not quite...

```
bash3.2 User alex on host blue in dir ~
Wed Jul 18 15:00:03>  sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 5 - start of a new network block
ssid - hexdump_ascii(len=8):
     32 32 43 61 73 74 6c 65                           22Castle        
PSK (ASCII passphrase) - hexdump_ascii(len=19): [REMOVED]
key_mgmt: 0x2
proto: 0x1
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='22Castle'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=21 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:15:af:03:59:7d
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
WEXT: Operstate: linkmode=0, operstate=6
Cancelling scan request


```

Thanks for helping, it seems like working network is just a step away. :)

---

### Post by kevdog on 2007-07-18
Can you change the password to something simple like an 8 digit word?  I would just like to troubleshoot something.

---

### Post by ittiam on 2007-07-18
Can you update your wpa_supplicant.conf as shown in [here]("http://ubuntuforums.org/showthread.php?t=263136") ?

I cant give u a good explanation of each parameter there, but all i can say is that config file works. It works for me. I see you have some values missing.

---

### Post by kevdog on 2007-07-18
Couple of questions??

What does
iwlist scan
show??

How did you install ndiswrapper -> from repository or from source compilation?

What driver are you using for your card??
lshw -C network

---

### Post by ittiam on 2007-07-18
This [Thread]("http://ubuntuforums.org/showthread.php?t=478588") on the forum has a post saying that ndiswrapper in feisty repo doesnt work well with WPA. I dont know how far it is true because i did not install it from the repoi...i did a make on source. So if adding those new values in wpa_supplicant.conf fails and If you have installed it from the repo, you know where to head next.

---

### Post by alex77 on 2007-07-19
Ok, installed ndiswrapper form source, but unfortunately still no joy. In fact, wlan0 isn't there anymore... 

Ndiswrapper installed ok, but it still show rtl8187 as alternate driver, even though it is blacklisted:

```
bash3.2 User alex on host blue in dir ~
Thu Jul 19 12:04:01>  ndiswrapper -lnetrtuw : driver installed
        device (0BDA:8187) present (alternate driver: rtl8187)

bash3.2 User alex on host blue in dir ~
Thu Jul 19 12:04:15>  rmmod rtl8187
ERROR: Module rtl8187 does not exist in /proc/modules
```

```
bash3.2 User root on host blue in dir ~/Desktop
Thu Jul 19 12:00:59>  tail /var/log/messages
Jul 19 11:45:04 blue gconfd (root-6786): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 19 11:45:04 blue gconfd (root-6786): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 19 11:45:04 blue gconfd (root-6786): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 19 11:46:04 blue gconfd (root-6786): GConf server is not in use, shutting down.
Jul 19 11:46:04 blue gconfd (root-6786): Exiting
Jul 19 11:46:51 blue kernel: [  644.262644] usbcore: deregistering interface driver ndiswrapper
Jul 19 11:46:51 blue kernel: [  644.327530] ndiswrapper: device wlan0 removed
Jul 19 11:46:54 blue kernel: [  647.231092] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
Jul 19 11:46:54 blue kernel: [  647.371910] usbcore: registered new interface driver ndiswrapper
Jul 19 11:47:18 blue syslogd 1.4.1#20ubuntu4: restart.

```

```
bash3.2 User alex on host blue in dir ~
Thu Jul 19 12:05:29>  dmesg | grep ndiswrapper
[   29.335387] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   29.823158] ndiswrapper: driver netrtuw (Realtek Semiconductor Corp.,05/18/2006,5.1230.0518.2006) loaded
[   32.982027] usbcore: registered new interface driver ndiswrapper
[  644.262644] usbcore: deregistering interface driver ndiswrapper
[  644.327530] ndiswrapper: device wlan0 removed
[  647.231092] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[  647.371910] usbcore: registered new interface driver ndiswrapper
[ 1731.319934] usbcore: deregistering interface driver ndiswrapper
[ 1757.744970] ndiswrapper version 1.47 loaded (smp=yes)
[ 1758.123947] ndiswrapper: driver netrtuw (Realtek Semiconductor Corp.,05/18/2006,5.1230.0518.2006) loaded
[ 1760.972694] usbcore: registered new interface driver ndiswrapper
```



Card not detected:
```
bash3.2 User root on host blue in dir ~/Desktop
Thu Jul 19 12:01:11>  ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:E8:F0:59  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 

eth1      Link encap:Ethernet  HWaddr 00:17:31:EE:E1:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17230 (16.8 KiB)  TX bytes:17230 (16.8 KiB)


bash3.2 User root on host blue in dir ~/Desktop
Thu Jul 19 12:02:00>  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.
```

---

### Post by kevdog on 2007-07-19
ndiswrapper by default sets up an interface on wlan0.  This means that any reference to you wireless card in /etc/iftab (if there is any reference) and in /etc/network/interfaces must be set to wlan0.  Sorry I dont remember your old interface name (eth1 perhaps??), but in these two files if eth1 is mentioned just change it to wlan0.

Sorry it looks like your old device was wlan0 --- what is the output of
lshw -C network

---

### Post by alex77 on 2007-07-20
ok, attatched is the output of lshw in html format

Also, having restarted iwconfig works again (wlan0 is there) but access point is still not associated.

thanks :)

---

### Post by alex77 on 2007-07-20
oops, heres the attatchment.

---

### Post by gr00 on 2007-07-25
im very much following up with this thread, ive done things step by step along with you, and i have to say that im getting almost every exact error that you are having. no matter what is changed or configured, there is no connection

hope this thread keeps going forth until there is resolution

---

### Post by alex77 on 2007-07-25
gr00, I'm sorry to hear you're having the same problem- but at least i now know I'm not the only one with this. If you do find a fix would you let me know?

Thanks

---

### Post by kevdog on 2007-07-25
What exactly is the error you are receiving??? 

Please in addition post (not as an attachment):
lshw -C network
/etc/network/interfaces
/etc/iftab
/etc/modprobe.d/ndiswrapper

---

### Post by alex77 on 2007-10-01
RESOLVED


ok, totally gave up on feisty and did a clean install of gutsy beta.
wireless connected straight away, with WPA enabled

I'm writing this from ubuntu now!

Big Thanks to everyone that helped me try and sort this out.:)

Anyone with asus p5w deluxe- get gutsy. its great.

---

### Post by vahnx on 2008-01-10
I am using Gutsy 7.10 and I began to use wicd, and I saw WPA etc. fine. But then I was messin' around and now I can only see the WEP points. Has anyone found a way to fix this yet? I dunno why this is happening! I used to be able to see WPA fine!

---

### Post by pana.corbului on 2008-05-03
I'm using that win98 driver on ndiswrapper. ```
network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:6f:2c:6d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187b driverversion=1.52+Realtek Semiconductor Corp. ip=192.168.0.122 multicast=yes wireless=IEEE 802.11g

```It connects to wep wireless but I have not succeded to connect using wpa 1. 
Here is the output of my network ```
iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1D:7E:E3:4E:E8
                    ESSID:"octavianus"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
``` and here is my wpa_supplicant.conf ```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="octavianus"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="Xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
        pairwise=TKIP
        group=TKIP
} 
```Any ideeas ?

Should I use instead linux realtek driver? Is it working with hardy? I can connect succesfuly to wep wireless but no to wpa1. 
 Here is the output ```
sudo wpa_supplicant -Dwext -iwlan0 -c /etc/wpa_supplicant.conf -w
Trying to associate with 00:1d:7e:e3:4e:e8 (SSID='octavianus' freq=2437 MHz)
Associated with 00:1d:7e:e3:4e:e8
WPA: Key negotiation completed with 00:1d:7e:e3:4e:e8 [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:1d:7e:e3:4e:e8 completed (auth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:1d:7e:e3:4e:e8 (SSID='octavianus' freq=2437 MHz)
^[[23~Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with 00:1d:7e:e3:4e:e8 (SSID='octavianus' freq=2437 MHz)
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with 00:1d:7e:e3:4e:e8 (SSID='octavianus' freq=2437 MHz)
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with 00:1d:7e:e3:4e:e8 (SSID='octavianus' freq=2437 MHz)
Authentication with 00:00:00:00:00:00 timed out.
cioctl[SIOCGIWSCAN]: Resource temporarily unavailable

```

LATER EDIT: 
**I've managed to connect using wpa and wpa2 [AES] on realtek 8187b! All from knetwork manager [I'm using kubuntu] Didn't worked from cli. All I had to do is to click 'connect to other network' [althought my network was displayed but when i was trying to connect it was letting me to select only wep encryption] and select the encryption type and there you go! **

---

