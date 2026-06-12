---
title: "ndiswrapper/bcm43 wireless issue"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Dark006 on 2009-04-19
Hi, I'll try to keep this brief and not confusing. I've used ndiswrapper many times before (I use it on my own desktop and installed it on other PC's as well). I recently helped my roommate make the switch from Windows to Ubuntu. After the Ubuntu install, I then installed ndiswrapper by disc through synaptic. I've got the correct driver installed through ndiswrapper (it says "Driver installed, device present" when I type 'ndiswrapper -l') BUT...it doesn't work for some reason. There are also NO link lights on the PCI wireless card also. Now for some copy/pasting. Below will be the output of a few commands to hopefully help us figure out why this isn't working.

First up, the output of "lshw -C network"
```
  
*-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb

```
Here is "lspci -nn"
```

00:0d.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

```
Here's "ifconfig"
```

eth0      Link encap:Ethernet  HWaddr 00:11:d8:47:85:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

```
And lastly, heres the output of "iwconfig"
```

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Please, if someone has experience with this or has had this issue please help. This is the last place I've turned to, so any help is greatly appreciated.

---

### Post by pspsampsp on 2009-04-19
i think there is a linux version of the bcm43 wireless driver , go into system -> administration -> Hardware drivers. to enable it

---

### Post by anewguy on 2009-04-19
It's possible that the "built-in" driver in stepping on the driver from ndiswrapper.  I don't know if there are others as well, but I believe you need to do the following:

- open a terminal window

- cd /etc/modprobe.d

- sudo gedit blacklist

- go to the bottom of the file and add a new line containing the following:

b43

- save the file and exit

Also, is it possible that the module is not getting loaded at boot?  If you haven't already, do the following:

- open a terminal window

- cd /etc

- sudo gedit modules

- go to the end of the file, and if it does not exist, add the following:

ndiswrapper

- save the file and exit


After either of the above changes, it's easiest just to reboot.

Let us know what happens, if you have more problems, etc.! 

Dave :)

EDIT:  another post came in before mine.  If you use the built-in driver, be sure to remove ndiswrapper from the modules file.

---

### Post by Dark006 on 2009-04-19
@pspsampsp: I'm guessing that will need an Internet connection though correct? I'll have to do it tomorrow because I'll have to bring it upstairs to our router.

@anewguy: I've already blacklisted everything I think I needed to. bcm43, bcm43xx etc. I've also already had ndiswrapper added to the /etc/modules and rebooted with no success.

---

### Post by divague on 2009-04-19
Maybe this guide will help you find out why it doesn't work.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

---

### Post by lkraemer on 2009-04-19
Please open a Terminal Window, cut and paste each line to prevent
mistakes and do the following:
```

lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig


```
Post the output results of the above, as it will give us
more information.


Then when you know the Routers essid do:
```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid "youressidofrouter"
sudo iwconfig wlan0 mode Managed
sudo ifconfig wlan0 up
sudo dhclient wlan0
iwconfig


```
Post the output of iwconfig from the above command

Try to surf.

lkraemer

---

### Post by Dark006 on 2009-04-20
@lkraemer: I tried what you said and it still didn't work. Also below is the output of those commands you listed.

**LSMOD**
```

Module                  Size  Used by
ipv6                  263972  8 
isofs                  40100  0 
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
udf                    88356  1 
crc_itu_t              10112  1 udf
usb_storage            81728  1 
libusual               27156  1 usb_storage
af_packet              25728  4 
rfkill_input           12672  0 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
container              11520  0 
pci_slot               12552  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
video                  25104  0 
output                 11008  1 video
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
snd_via82xx            32536  3 
gameport               19468  1 snd_via82xx
snd_mpu401_uart        15360  1 snd_via82xx
evdev                  17696  7 
psmouse                45200  0 
snd_seq_dummy          10884  0 
serio_raw              13444  0 
snd_via82xx_modem      19464  0 
snd_ac97_codec        111652  2 snd_via82xx,snd_via82xx_modem
ac97_bus                9856  1 snd_ac97_codec
arc4                    9984  2 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_pcm                83204  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_viapro             15764  0 
i2c_core               31892  1 i2c_viapro
snd                    63268  18 snd_via82xx,snd_mpu401_uart,snd_via82xx_modem,snd_ac97_codec,snd_seq_oss,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         16136  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore              15328  1 snd
b43                   131356  0 
rfkill                 17176  2 rfkill_input,b43
mac80211              216820  1 b43
cfg80211               32392  1 mac80211
led_class              12164  1 b43
input_polldev          11912  1 b43
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
button                 14224  0 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
via_agp                16256  1 
agpgart                42184  1 via_agp
ndiswrapper           196380  0 
ext3                  133256  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  1 
cdrom                  43168  1 sr_mod
sd_mod                 42264  6 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
pata_acpi              12160  0 
pata_via               16132  1 
sata_via               15492  3 
libata                177312  4 ata_generic,pata_acpi,pata_via,sata_via
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
uhci_hcd               30736  0 
ehci_hcd               43276  0 
ssb                    40580  1 b43
usbcore               148848  6 usb_storage,libusual,ndiswrapper,uhci_hcd,ehci_hcd
skge                   48144  0 
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

**ndiswrapper -l**
```

bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)

```

**cat /etc/modprobe.d/blacklist**
```

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
blacklist bcm43
blacklist bcm43legacy
blacklist ssb
# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
# PC Speaker
blacklist pcspkr

```

**iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"2WIRE220"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

### Post by Dark006 on 2009-04-20
**UPDATE**

Every time I try to run "sudo ifconfig wlan0 up" it gives me this error
**SIOCSIFFLAGS: No such file or directory**

Any ideas??

I've also uninstalled ndiswrapper and reinstalled it from source.

---

### Post by anewguy on 2009-04-20
Notice in your blacklist that it says the following are replaced by b43 and ssb, then it blacklists the bcm43 stuff and ssb.  I think you still need to add b43 to that list to get rid of the built-in driver.  let me know what happens.

Dave :)

---

### Post by Dark006 on 2009-04-20
@anewguy: I do have those blacklisted, not sure if I should have "ssb" blacklisted or not (I have it blacklisted right now)

Well, I'm not sure what I did, but now it at least shows the available wireless networks. But it wont' connect to them for some reason. Anyone run into this??

---

### Post by anewguy on 2009-04-20
Are any of those open networks with no security?

Dave :)

BTW - just to make sure, not trying to argue or anything, so please don't take this the wrong way - the blacklist you provided doesn't show b43, but all of the bcm stuff.  Did you add b43 to the blacklist?  I think it is separate from the others that are listed in your post. :)

---

### Post by Dark006 on 2009-04-21
> **anewguy said:**
> Are any of those open networks with no security?

Dave :)

BTW - just to make sure, not trying to argue or anything, so please don't take this the wrong way - the blacklist you provided doesn't show b43, but all of the bcm stuff.  Did you add b43 to the blacklist?  I think it is separate from the others that are listed in your post. :)

Oooh snap! Your right, I don't have the b43 blacklisted. I'll have to do that tomorrow when my roommate is awake.

---

### Post by anewguy on 2009-04-21
Don't know if it will solve your problems or not - just saw on another post about a month ago that it had to be blacklisted as well.

Good luck!  Let us know what happens!

Dave :)

---

### Post by lkraemer on 2009-04-21
Dark006,
It appears that b43 is attempting to find the firmware for the Broadcom
Ethernet card.  It's looking for *.fw in /lib/firmware, but you are trying
to use ndiswrapper.

ref:
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/siocsifflags-no-such-file-or-directory-184147/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/siocsifflags-no-such-file-or-directory-184147/)

So, you probably need to blacklist the following:
b43
mac80211
cfg80211
ssb

Then reboot.

You are still trying to use ndiswrapper with a Windows driver like
bcmwl5.inf & bcmwl5.sys aren't you?

```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid "youressidofrouter"
sudo iwconfig wlan0 mode Managed
sudo ifconfig wlan0 up
sudo dhclient wlan0
iwconfig


```
Then post the output of iwconfig again.

Maybe you will be able to surf.

lkraemer

---

### Post by Dark006 on 2009-04-21
I tried blacklisting the things you recommended above and still no luck. It can see other wireless networks but won't connect to them for some reason. There was even an open network that I tried to get on but that didnt' work either. 

Yes this is for the bcmwl5.inf driver also.

Here is the current output of iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by lkraemer on 2009-04-21
Dark006,
You don't have an essid assigned from the looks of the
iwconfig post.

Let's assume the name of your Wifi Router is Airlink.
Then in a Terminal window you need to do:
```

sudo iwconfig wlan0 essid "Airlink"
iwconfig


```
Then post the output of iwconfig.  It should show Airlink as the essid.
Assuming that it is not WPA or WEP protected, in which case you will need to add the key.

Ref:
```

man iwconfig

```

lkraemer

---

### Post by anewguy on 2009-04-22
With roaming enabled, I didn't think you specified an ESSID, as it is picked up when you actually connect to a network.  Am I wrong on that (would like to know really so I don't have misconceptions on how things work)?

Thanks
Dave :)

---

### Post by lkraemer on 2009-04-22
Dave,
You are correct, but that assumes that the drivers are correct,
or nidswrapper is used with the correct Windows Drivers.  But, what
happens if you never get Wifi working.  ie. Then do a Manual setup,
within a Terminal so you can see what each command is doing for you
and you can search for error codes/messages.

lkraemer

---

### Post by lkraemer on 2009-04-22
Dark006,
It's been well over a day, and not one word from you.  What is going on?
Is it working or not?  If you give up, at least tell us.

lkraemer

---

### Post by Dark006 on 2009-04-23
Sorry I didn't reply sooner. My roommate put windows back on his desktop and the wireless card is still not working..so it looks like we found the problem haha (he kept taking it out without wearing any ESD strap so I think he might have shocked it). He's going to exchange it for the same thing or buy a new one. Thank you to all that helped.

---

