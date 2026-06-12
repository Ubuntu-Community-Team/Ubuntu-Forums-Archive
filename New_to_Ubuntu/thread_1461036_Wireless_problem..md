---
title: "Wireless problem."
date: 2010-04-23
forum: New to Ubuntu
---

### Post by Sarnie109 on 2010-04-23
Hi guys and gals. I'm totally new to Ubuntu and Linux based software and have just installed Ubuntu on an unused laptop I had laying around.
I've done a stand alone install (just Ubuntu, no windows) and I'm very very pleased with the package. The only problem I'm having is getting the laptop to connect to my wireless router. I've used the help within Ubuntu and tracked the problem to the wireless being deactivated within the laptop.
In short, how do I get it turned on? Please remember you're explaining to a complete novice.
Cheers in advance peeps.

---

### Post by arrrghhh on 2010-04-23
Assuming the wifi switch is ON...

Please give us the output of (from a terminal window):
```
lspci
```
and
```
lsusb
```

I guess I should ask, is the card internal?  If so, no need for lsusb.

---

### Post by P4man on 2010-04-23
just in case: to open a terminal, go to applications > accessoiries > terminal

(and note those commands are LSPCI and LSUSB in lowercase)

---

### Post by anewguy on 2010-04-23
And.....

Since you are new, what we are trying to do is find the maker and chipset for your wireless adapter to see if we need to help you install a driver for it or in some other way help you set it up.  The 2 commands listed above help us in that in the following ways:

lspci -> List PCI devices.  This asks Ubuntu to list it's known devices that use the PCI interface.  A lot of adapters use this interface, so if your wireless adapter does we will see it.

lsusb -> List USB devices.  This asks Ubuntu to list it's known devices that use the USB interface.  Some wireless adapters on laptops are actually connected internally to the USB interface.  In addition, some adapters are external and plug in to the USB interface.  If your wireless adapter uses the internal USB interface then we will see it.

Didn't know if you were interested, but sometimes it doesn't hurt to explain what it is we are asking you to do and why.

Dave ;)

---

### Post by archkidd on 2010-04-23
I also am a newbie and when I instlled ubuntu 9.1 within windows using wubi it absolutely woudl not recognize the wiireless.  As soon as I did a full install repalcing windows it recognized my wireless immediately. 2 things, as 'arrrgh' said are you sure the physical wireless switch is on.  I think all laptops have one.  Secondly, as a newbie I had to find out that  the wireless is found under the connections icon in the top right panel of the screen.  If not on it is probably very light grey and hard to see.  But when the menu drops your wireless should be there and needs to be activated using the network id and security key.  Hope this isn't too simple.  I don't mean to insult but as a newbie I know the  obvious things get forgotten when you become an 'expert'.

---

### Post by Sarnie109 on 2010-04-24
Hi Guys. Sorry for the delay in answering. Work gets in the way of life. Yes it is an internal card in an hp pavilion laptop. Put in lsusb as suggested and it gives the following:

Bus 002 Device 001: ID ld6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID ld6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID ld6b:0002 Linux Foundation 2.0 root hub

Hope this gives you guys some ideas. Cheers.

---

### Post by Sarnie109 on 2010-04-24
oops, must read your replies more carefully. Now done lspci and got lots of info. What exactly do you need to know?

I can see network controller Broadcom Corporation BCM4318 (Airforce One 54g) 802.11g wireless LAN controller (rev 02)

---

### Post by The Thunder Chimp on 2010-04-24
> **Sarnie109 said:**
> oops, must read your replies more carefully. Now done lspci and got lots of info. What exactly do you need to know?

Dude, before doing anything fancy, could you just check in System>Administration>Hardware Drivers? If there is anything related to wireless in there, download and activate it (it will do so automatically). By the way, the path I have given you is followed by clicking on the particular buttons on the left of the upper panel (if using GNOME, which you probably are).

Tell us what happened when doing that.

---

### Post by Sarnie109 on 2010-04-24
Hi. Just done as suggested and it's telling me there are no proprietary drivers in use on the system.

---

### Post by bkratz on 2010-04-24
> **Sarnie109 said:**
> Hi. Just done as suggested and it's telling me there are no proprietary drivers in use on the system.

See this page, your card is mentioned.

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

See the section labeled Ubuntu/Debian

---

### Post by lkraemer on 2010-04-24
You didn't give a clue as to what version of Ubuntu you are running???????

Open a Terminal Window and Copy & Paste these commands to get
more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted.
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf   

(for=< 9.04 use cat /etc/modprobe.d  /blacklist)

iwconfig
cd /
cd /lib/firmware
ls -alt
cd /b43
ls -alt

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Post the output of each command........

(You are looking for any *.fw files in /lib/firmware/b43 or
/lib/firmware/b43legacy and if you had a Wired LAN connection and
went to SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS and enabled the
Hardware Drivers with a LAN connection there should have been folders
created and files inserted for the Restricted Drivers to work.)

Your options that can be used:
1. Ndiswrapper and a Windows Driver....bcmwl5.inf & sys
2. bcm43xx module and some Firmware.... B43 & B43legacy *.fw
3. b43 and some Firmware that was downloaded/extracted when you
enabled the Driver.  B43 is the default driver for 9.10 if I
remember correctly.  Your output of the above commands will help
determine what is already installed by default.

Once you have the Manuf & Hardware info, use Search or Google for
"HOWTO: & 4318" or whatever your Broadcom model is to find a good guide.

It will be your decision on what to use.

For #2 above:
If you just need the Broadcom firmware for b43xx it can be found on
the internet. Are you using b43, b43xx, or ndiswrapper?

Now search through dmesg for any references to Broadcom firmware,
looking for missing firmware or what is causing the Wifi to
not function. There might be a clue. Is the firmware installed
in /lib/firmware or possibly in /lib/firmware/b43 Once again
dmesg might give you a clue. ie. [http://www.omattos.com/node/6](http://www.omattos.com/node/6)

If lsmod shows module b43 and others installed you will
need to blacklist them, since you are going to be using b43xx.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb

```
You can use sudo gedit /etc/modprobe.d/blacklist
and add the necessary modules to blacklist.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```
If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
Post the output of iwconfig above.

For #3 Above:
B43 doesn't appear to be supported by 9.04 according to searches of
the forum.  It most likely is the best way to go with 9.10 as B43 is
installed.  So all you would need to do is download the Firmware,
extract the folders/files and copy them to /lib/firmware and to  /lib/firmware/b43
[http://www.omattos.com/node/6](http://www.omattos.com/node/6)

You may need to Blacklist some driver to get it working.  Look at
the results of lsmod to see what was installed..........
If lsmod shows module b43xx, ndiswrapper, and others installed you
will need to remove them and blacklist them, since you are going to
be using b43. Be sure to insert a # at the beginning of the line if
any of the existing driver modules are blacklisted, and you will be
using them. You may have to remove the following depending on what lsmod
shows: (DON'T BLACKLIST SSB)
```

modprobe -r b44
modprobe -r b43legacy

```

This will help you finish up:
[http://ubuntuforums.org/showthread.php?p=8248919#post8248919](http://ubuntuforums.org/showthread.php?p=8248919#post8248919)
Posting #8


I just stuck with the windows drivers.

lk

---

### Post by ugm6hr on 2010-04-24
Do you have access to a wired internet connection from the laptop?

---

### Post by anewguy on 2010-04-25
As per ugm6hr, if you can hard-wire your PC temporarily to the router, you should only need to do the following:

sudo apt-get update

THEN look under drivers and see if one is listed - if so, enable it.

Disconnect your hard-wire cable, wait a few seconds, and check network manager to see if wireless is showing now (be sure "enable wireless" is clicked in network manager).

Dave ;)

---

### Post by Sarnie109 on 2010-04-28
Thanks guys. I've hardwired to the modem temporarily and thats fine. i've updated and activated b43 driver but still not got wireless. Many thanks for all the instructions but I'm a little daunted by it all. Seems very complicated. Is there anything else i can do or can some walk me through it, hold my hand. Cheers.

---

### Post by P4man on 2010-04-28
lkraemer wrote quite an extensive guide there, wow, nice! 
but I imagine it scares you and you probably only need to do one small step now (blacklisting the old driver)

 Lets take this one step a a time. Open a terminal (applications > accessoiries > terminal)

in there type

```
lsmod
```

Copy paste the output here

---

### Post by sadaruwan12 on 2010-04-28
OK bro it seems like you're using Ubuntu 9.10 Karmic Koala, I'd a similar kind of problem with my Netbook which have a Realtek 8187b network card.

Heres how I managed to solve my problem [Click Here To Go There]("http://slinuxworld.blogspot.com/2009/11/wifi-problem-solution-for-rtl8187b.html")

To get info on the ndsiwrapper [click me]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page")

For the instructions how to install it in Ubuntu [Click Me]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by Sarnie109 on 2010-04-28
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
arc4                    1660  2 
snd_atiixp_modem       11940  0 
ecb                     2524  2 
snd_atiixp             15720  2 
snd_pcm_oss            37920  0 
snd_ac97_codec        101216  2 snd_atiixp_modem,snd_atiixp
snd_mixer_oss          16028  1 snd_pcm_oss
ac97_bus                1532  1 snd_ac97_codec
snd_seq_dummy           2656  0 
snd_pcm                75296  4 snd_atiixp_modem,snd_atiixp,snd_pcm_oss,snd_ac97_codec
b43                   122200  0 
snd_seq_oss            28576  0 
pcmcia                 36808  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
mac80211              181140  1 b43
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
iptable_filter          3100  0 
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211               93052  2 b43,mac80211
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci_pci               7100  0 
sdhci                  17504  1 sdhci_pci
tifm_7xx1               5372  0 
i2c_piix4               9932  0 
led_class               4096  2 b43,sdhci
snd                    59204  15 snd_atiixp_modem,snd_atiixp,snd_pcm_oss,snd_ac97_codec,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_core               7832  1 tifm_7xx1
soundcore               7264  1 snd
snd_page_alloc          9156  3 snd_atiixp_modem,snd_atiixp,snd_pcm
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
shpchp                 32272  0 
k8temp                  4188  0 
joydev                 10240  0 
psmouse                56500  0 
serio_raw               5280  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
8139too                22620  0 
radeon                636000  2 
ttm                    36212  1 radeon
drm                   160032  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
ssb                    35524  1 b43
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
video                  19380  0 
output                  2780  1 video
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agp

---

### Post by Sarnie109 on 2010-04-28
Now gotta go out for a couple of hours. I'll check in again when I get back.

---

### Post by Sarnie109 on 2010-04-28
Right. I'm back. I've bin reading through some of the other info and keep getting bogged down in the lingo. Sorry if I sound like thicky...... but I'm starting to feel like one.

---

### Post by ugm6hr on 2010-04-28
After connecting to the internet via a wired connection in a terminal type:
```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

```
Reboot the machine. Afterwards you will see the driver installed and working.

---

### Post by Sarnie109 on 2010-04-28
> **ugm6hr said:**
> After connecting to the internet via a wired connection in a terminal type:
```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

```Reboot the machine. Afterwards you will see the driver installed and working.
Just done this. There doesn't appear to be any change. How will I know if the driver's running ok?

---

### Post by ugm6hr on 2010-04-28
> **Sarnie109 said:**
> Just done this. There doesn't appear to be any change. How will I know if the driver's running ok?

Check in Restricted Drivers.  Or try to connect by wifi.

---

