---
title: "Ubuntu Wi-Fi problem."
date: 2011-09-06
forum: New to Ubuntu
---

### Post by bbno3 on 2011-09-06
*sorry for miss spellings im on a weird keyboard*

Ever since i uninstyalled ubuntu i have to push the hatrdware wifi button next to my power buttotn on my laptop. The internet only works in windows if i do this. My newly reinstalled ubuntu Shows no wireless networks In black under the menu enable wireless and enable networking are enabled but above it there is wireless is disabled in black. I have formatted my drive and freshly reinstalled ubuntu and it still comes up. I have to press the wireless button near my power button to turn on the internet for windows. but in ubuntu it dosn't even connect? I was told on howtogeek that this could be a linux problem and i should ask on here.
I uninstalled ubuntu by deleteing the partion getting the grub recovery> error then using a system image to restore windows to a point it worked, with ubuntu partion deleted. i have formatted my drive and windows now no longer exists and my £100 windows 7 does not work. So i can only do it on ubuntu.
:confused:

---

### Post by sanderd17 on 2011-09-06
can you give us the output of the commands
```

iwconfig
lspci

```

Please put them between CODE tags (click on the # in edit mode)

---

### Post by ruseriousb511 on 2011-09-06
what distro are you using ? I had the same problem on mine when I did a fresh install of Ubuntu 11.04. I had to manually installl the driver for the wireless network to work. What distro are you using and what wireless card does your pc have in it ?

---

### Post by bbno3 on 2011-09-06
Whats a distro? Im using the newest one from the website i think it was called natty narwhale or something...

---

### Post by bbno3 on 2011-09-06
Sanerd i dont get it it says no such thing as 1psci

but the first one said.
LO NO WIRELESS EXTENSION

ETH0 NO WIRELESS EXTENSION

WLAN0 IEE 802.11BG ESSID:OFF/ANY
MODE:MANAGED ACESS POINT:NOT ASSOCIATED TX-POWER=OFF RETRY LONG LIMITS:7 RTS THR:OFF FRAGMENT THR:OFF POWER MANAGEMENT:OFF

Im no expert but all the offs sound bad...

---

### Post by sanderd17 on 2011-09-06
I believe the power is off with a hardware switch. Try using that keyboard shortcut again and try again.

And the command is LSPCI (in small letters). So not a 1 but an l. It stands for "List PCI devices".

For the CODE tag: edit your post, go in advanced mode, select the part that is code (the terminal output) and click on the #-symbol).

---

### Post by bbno3 on 2011-09-06
That lspci command is too long to write by hand, how do you copy it to notepad or something and save it to a usb? and the wireless button is refusing to turn off...

in terminal when i copy it says ^c
right click copy
 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)


*edit
Im impressed at how fast your responding i dont often see it that fast

---

### Post by sanderd17 on 2011-09-06
> **bbno3 said:**
> That lspci command is too long to write by hand, how do you copy it to notepad or something and save it to a usb? and the wireless button is refusing to turn off...

in terminal when i copy it says ^c

copy with right click or with CTRL+SHIFT+C (CTRL+C stands for interrupt current program, it has been this way long before people could copy-paste)

---

### Post by sanderd17 on 2011-09-06
What version of Ubuntu are you using? there seems to be problems with your card and 10.04 at least. Check this thread: [http://ubuntuforums.org/showthread.php?t=1466201](http://ubuntuforums.org/showthread.php?t=1466201)

Don't do this if you are using another version.

---

### Post by bbno3 on 2011-09-06
No matter how hard i press the wireless button or how fast etc etc... it wont turn off. but by default Its turned off at start up and i have to manually turn it on.

---

### Post by bbno3 on 2011-09-06
11.04 im using.

---

### Post by ruseriousb511 on 2011-09-06
Yeah thats what I have as well, go to applications and see if there is an app called " additional drivers ",  install any drivers there and if there are none lemme kno. I am looking for the link to get you what you need to get it going. I think i will just send you to my help page and you can see all the help I got and you can try all the tricks in there.

---

### Post by bbno3 on 2011-09-06
It would help if i could acess the internet to find the drivers...

"Please check your network status"

---

### Post by sanderd17 on 2011-09-06
> **bbno3 said:**
> It would help if i could acess the internet to find the drivers...

"Please check your network status"

Don't you have a cable? or another dongle?

---

### Post by bbno3 on 2011-09-06
Thats a good idea. But i wish i had an Ethernet cable...

---

### Post by ruseriousb511 on 2011-09-06
yeah can you hook up with an ethernet cable ? also can you run this command and show it ?

rf kill list

type that into terminal and copy and paste here please.

---

### Post by bbno3 on 2011-09-06
Rf: command not found. 

Il have to do the ethernet thing in the morning as i dont feel like going out at this time and buying a cable*8pm*

---

### Post by ruseriousb511 on 2011-09-06
im sorry, no space beween rf and kill, just copy and paste this into your terminal :

rfkill list

copy and past results please

---

### Post by bbno3 on 2011-09-06
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

---

### Post by zero2xiii on 2011-09-06
Dont mean to bud in but,

according to this:
> WLAN0 IEE 802.11BG ESSID:OFF/ANY
MODE:MANAGED ACESS POINT:NOT ASSOCIATED TX-POWER=OFF RETRY LONG LIMITS:7 RTS THR:OFF FRAGMENT THR:OFF POWER MANAGEMENT:OFF

The device is off. Wont 

```
sudo ifconfig wlan0 up
```

turn on the device, making it usable?

---

### Post by bbno3 on 2011-09-06
@zero OPERATION NOT POSSIBLE DUE TO RF-KILL

---

### Post by ruseriousb511 on 2011-09-06
you can try that but it says that there is a hard and soft block on some of those, and that means that something is not being recognized as being on or running; try this in your terminal and then post results again please (its worth a shot) :

sudo rf kill unblock all

then do :

rfkill list 

copy and paste here

---

### Post by bbno3 on 2011-09-06
bran@superslow:~$ sudo rfkill unblock all
[sudo] password for bran: 
bran@superslow:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
bran@superslow:~$

---

### Post by bbno3 on 2011-09-06
Going to bed guys iv had a long day be back in the morning dont be afraid to post any suggestions il read tomorrowl.

---

### Post by ruseriousb511 on 2011-09-06
im sorry I did it again, its no space between rf and kill :

sudo rfkill unblock all

then :

rfkill list

---

### Post by ruseriousb511 on 2011-09-06
just lemme kno when you are back on, i may need som more info, we'll get this figured out

---

### Post by john_abq on 2011-09-06
I'm having the same problem with my Pangolin laptop. When I do rfkill list I get the message that the hardware is blocked. I updated to 11.04 a couple of weeks ago and everything worked fine. I did an upgrade three days ago and thats when I lost my wireless. I'm interested in solution to this as well.

---

### Post by bbno3 on 2011-09-07
bran@superslow:~$ sudo rfkill unblock all
[sudo] password for bran: 
bran@superslow:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
bran@superslow:~$

i can no longer enable wireless under enable networking.

---

### Post by bbno3 on 2011-09-07
Bump

---

### Post by bbno3 on 2011-09-07
Guys please tell me...

---

### Post by wildmanne39 on 2011-09-07
Hi, there often problems setting up these cards, let see if you have the driver installed and a few other things please post the results of these commands here:
```
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
dmesg | grep wlan0
```
```
dmesg | egrep 'ath|firm'
```
```
lsmod | grep ath
```
by clicking on new reply and click # and paste the information between the brackets.

I know you have ran some of these commands before but I need them all in one place so I can refer back to them.
Thank you

---

### Post by DogMatix on 2011-09-07
I have this issue on an acer One netbook. Turns out my main issue lay with acer-wmi causing hard blocks. My work around ATM moment is to run

```


sudo rmmod acer-wmi


```

to get the wireless working. Looking for a way to make this permanent. Hope this helps

---

### Post by wildmanne39 on 2011-09-07
Hi DogMatix, to make it permanent do this please:
```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```
Thank you

---

### Post by DogMatix on 2011-09-08
> **wildmanne39 said:**
> Hi DogMatix, to make it permanent do this please:
```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```
Thank you

Ah! magic. Thank you.

---

### Post by wildmanne39 on 2011-09-08
Hi DogMatix, glad I could help! enjoy ubuntu.

---

### Post by a77ssii on 2011-10-04
I'm in the same boat.  Updated 10.04, 3 days ago and now no wireless.  If I revert back to previous before the update my wireless works fine but I have no audio.  But everything was 100% from wireless to audio before the last update.  According to my hardware drivers the wireless driver Realtek RTL819x wi fi cards is activated but not currently in use.  Here are the answers to your questions wildmanne39 in the order you requested.


*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth3
       version: 05
       serial: 10:1f:74:bd:1d:b5
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.80 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:2000(size=256) memory:f0004000-f0004fff(prefetchable) memory:f0000000-f0003fff(prefetchable)

:KS

NetworkManager Tool

State: connected

- Device: eth3  [Auto eth3] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        10:1F:74:BD:1D:B5

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.80
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

:KS

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)

:KS

lo        no wireless extensions.

eth3      no wireless extensions.

:KS

rfkill list all, nothing

:KS

dmesg | grep wlan0, nothing
:KS

[    1.798764] device-mapper: multipath: version 1.1.0 loaded
[    1.798768] device-mapper: multipath round-robin: version 1.0.0 loaded

:KS

[    1.798764] device-mapper: multipath: version 1.1.0 loaded
[    1.798768] device-mapper: multipath round-robin: version 1.0.0 loaded

:KS

lsmod | grep ath  Nothing



Also, it's booting into Linux generic 2.6.32-36 that has no wireless.  Booting into Linux generic 2.6.32-33 has wireless but no audio.

---

### Post by wildmanne39 on 2011-10-04
Hi, please see here:
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667)
Especially see the last three posts.
Thank you

---

### Post by a77ssii on 2011-10-04
story of my life.  Page not found.

---

### Post by wildmanne39 on 2011-10-04
Hi, I fixed it in the last post, just removed and added back, sometime that happens and I do not know why.
Thank you

---

### Post by a77ssii on 2011-10-04
Didn't work, I can connect cable ethernet but not wireless.  Double checked and I can still connect if I boot via 2.6.32.33 I have wireless.  My hardware drivers still states:
This driver is active but not currently in use
Going back to .33 I can turn my wireless on and off with the f12 key, in .34 it shows off and regardless of what I do it will not turn on.

---

### Post by wildmanne39 on 2011-10-04
Hi, do not worry about it saying it is not in use that is a known but in natty, let's just work on what the results of the commands say.

Use synaptic and install rfkill.
Then run these commands please:
```
lsmod | grep rtl
```
```
dmesg | egrep 'rtl|firm|wlan0'
```
```
sudo iwlist scan
```

Did you get any errors when you ran the commands in the link?
Thank you

---

### Post by a77ssii on 2011-10-05
Sorry, took me a bit to respond.  Had to run to Denver today and pick up one of my Scout II's and it's 160 miles round trip.  Anyway, see below.

> **wildmanne39 said:**
> Hi, do not worry about it saying it is not in use that is a known but in natty, let's just work on what the results of the commands say.

Use synaptic and install rfkill.
Then run these commands please:
```
lsmod | grep rtl
``` [COLOR=Red]nothing, another command prompt[/COLOR]

```
dmesg | egrep 'rtl|firm|wlan0'
``` [COLOR=Red]nothing, another command prompt[/COLOR]

```
sudo iwlist scan
```
[COLOR=Red]lo        Interface doesn't support scanning.

eth3      Interface doesn't support scanning.[/COLOR]


Did you get any errors when you ran the commands in the link?
Thank you

---

### Post by wildmanne39 on 2011-10-05
Hi, post the results of:
```
lsmod
```
it looks like you do not have a driver installed, also try this please:
```
sudo modprobe 8192ce
```

Did you download the driver in the link and install it with those 3 lines of code?
Thank you

---

### Post by a77ssii on 2011-10-05
[QUOTE=wildmanne39;11314191]Hi, post the results of:
```
lsmod
```it looks like you do not have a driver installed, also try this please:
[COLOR=Red]Module                  Size  Used by
binfmt_misc             6587  1 
iptable_nat             3543  0 
nf_nat                 15560  1 iptable_nat
nf_conntrack_ipv4      10346  3 iptable_nat,nf_nat
snd_hda_codec_atihdmi     2367  1 
ppdev                   5259  0 
snd_hda_codec_idt      52042  1 
nf_conntrack           60943  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
iptable_mangle          1549  0 
snd_hda_intel          22069  2 
snd_pcm_oss            35308  0 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
iptable_filter          1369  0 
snd_hwdep               5412  1 snd_hda_codec
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_pcm_oss,snd_hda_codec
fbcon                  35102  71 
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
ip_tables               9899  3 iptable_nat,iptable_mangle,iptable_filter
snd_seq_midi            4557  0 
tileblit                1999  1 fbcon
snd_rawmidi            19056  1 snd_seq_midi
x_tables               14175  2 iptable_nat,ip_tables
font                    7557  1 fbcon
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
fglrx                2092908  32 
bitblit                 4707  1 fbcon
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
agpgart                31724  1 fglrx
video                  17375  0 
softcursor              1189  1 bitblit
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_piix4               8335  0 
psmouse                63677  0 
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_pcm_oss,snd_hda_codec,snd_hwdep,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
uvcvideo               57406  0 
vga16fb                11385  1 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
vgastate                8961  1 vga16fb
output                  1871  1 video
videodev               34425  1 uvcvideo
serio_raw               3978  0 
v4l1_compat            13251  2 uvcvideo,videodev
shpchp                 28835  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169[/COLOR]

```
sudo modprobe 8192ce
```Did you download the driver in the link and install it with those 3 lines of code?
[COLOR=Red]FATAL: Module 8192ce not found.[/COLOR]
According to what I'm seeing, it is installed.   If I revert to Ubuntu version 2.6.32-33 my wireless works fine and I can turn it on/off via the F12 key.  When I boot into 2.6.32-34 I lose wireless. Everything worked perfectly until 6 days ago when I did a big update and had to reboot, then it all came undone.
Thanks for all your help thus far.

---

### Post by wildmanne39 on 2011-10-05
Hi, you have to install the driver for each kernel, so there is not one installed for this kernel.

Run these commands please:
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```
one at a time when they are done installing unplug your wired connection and restart your computer.
Thank you

---

### Post by a77ssii on 2011-10-05
> **wildmanne39 said:**
> Hi, you have to install the driver for each kernel, so there is not one installed for this kernel.

Run these commands please:
```
sudo add-apt-repository ppa:lexical/hwe-wireless
[COLOR=Red]Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 88B3CE2CE934D5F973CC26C80C5CE27EA088FF1E
gpg: requesting key A088FF1E from hkp server keyserver.ubuntu.com
gpg: key A088FF1E: "Launchpad Keng-Yu's PAA" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1[/COLOR]

sudo apt-get update
[COLOR=Red]Get:1 http://dl.google.com stable Release.gpg [198B]
Ign http://dl.google.com/linux/earth/deb/ stable/main Translation-en_US        
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Get:2 http://dl.google.com stable Release [1,338B]
Get:3 http://security.ubuntu.com lucid-security Release.gpg [198B]             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                       
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com lucid-updates Release.gpg [198B]  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                                 
Get:5 http://dl.google.com stable/main Packages [464B]                         
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Translation-en_US
Get:6 http://security.ubuntu.com lucid-security Release [44.7kB]               
Hit http://ppa.launchpad.net lucid Release                                     
Get:7 http://us.archive.ubuntu.com lucid-updates Release [44.7kB]              
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Get:8 http://security.ubuntu.com lucid-security/main Packages [211kB]
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Get:9 http://us.archive.ubuntu.com lucid-updates/main Packages [517kB]
Get:10 http://us.archive.ubuntu.com lucid-updates/restricted Packages [3,240B] 
Get:11 http://us.archive.ubuntu.com lucid-updates/main Sources [202kB]         
Get:12 http://security.ubuntu.com lucid-security/restricted Packages [14B]     
Get:13 http://security.ubuntu.com lucid-security/main Sources [64.6kB]         
Get:14 http://security.ubuntu.com lucid-security/restricted Sources [14B]      
Get:15 http://security.ubuntu.com lucid-security/universe Packages [86.2kB]    
Get:16 http://us.archive.ubuntu.com lucid-updates/restricted Sources [1,443B]  
Get:17 http://us.archive.ubuntu.com lucid-updates/universe Packages [230kB]    
Get:18 http://security.ubuntu.com lucid-security/universe Sources [25.8kB]     
Get:19 http://security.ubuntu.com lucid-security/multiverse Packages [4,559B]  
Get:20 http://security.ubuntu.com lucid-security/multiverse Sources [1,751B]   
Get:21 http://us.archive.ubuntu.com lucid-updates/universe Sources [81.0kB]    
Get:22 http://us.archive.ubuntu.com lucid-updates/multiverse Packages [10.5kB] 
Get:23 http://us.archive.ubuntu.com lucid-updates/multiverse Sources [5,070B]  
Fetched 1,536kB in 13s (112kB/s)                                               
Reading package lists... Done
[/COLOR]
sudo apt-get install rtl8192ce-dkms
[COLOR=Red]Reading package lists... Done
Building dependency tree       
Reading state information... Done
rtl8192ce-dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.[/COLOR]

```one at a time when they are done installing unplug your wired connection and restart your computer.
Thank you
Here's the results of that.  I'm rebooting now, I'll let you know in a minute if it worked or not.

---

### Post by a77ssii on 2011-10-05
Still not working. I did notice in -33 when I left click on the connection it comes up with eth3 and wireless whereas in -34 it does not give me the wireless option, only eth3 if that helps any.  I've also tried various key combinations to try and activate my wireless via the button on the keyboard, nothing will turn it on.
If it's any consolation your making me feel like and idiot that needs to learn code;).  I'm running Ubuntu on this machine and PCLinux on another and only know enough to REALLY screw things up.  Bad.

---

### Post by wildmanne39 on 2011-10-05
Hi, sometimes we have to work for it like pulling teeth.

Please post the results of these commands.
```
cat /etc/lsb-release; uname -a
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
```
dmesg | egrep 'rtl|firm|wlan0|eth1|eht2|eth3'
```
```
ls /lib/firmware
```
Please copy and paste the commands into the terminal, we may have to go a different route on the driver and firmware.
Thank you

---

### Post by a77ssii on 2011-10-05
> **wildmanne39 said:**
> Hi, sometimes we have to work for it like pulling teeth.

Please post the results of these commands.
```
cat /etc/lsb-release; uname -a
```
[COLOR=Red]DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux laptop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux[/COLOR]

```
lspci -nnk | grep -iA2 net
```
[COLOR=Red]02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
    Kernel modules: r8192ce_pci
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Kernel driver in use: r8169
    Kernel modules: r8169[/COLOR]

```
iwconfig
```
[COLOR=Red]lo        no wireless extensions.

eth3      no wireless extensions.[/COLOR]
```
rfkill list all
```
[COLOR=Red]nothing and I did go through synaptic and install it earlier.[/COLOR]
```
lsmod
```
[COLOR=Red]Module                  Size  Used by
snd_hda_codec_atihdmi     2367  1 
binfmt_misc             6587  1 
snd_hda_codec_idt      52042  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_pcm_oss            35308  0 
snd_hwdep               5412  1 snd_hda_codec
snd_mixer_oss          13746  1 snd_pcm_oss
ppdev                   5259  0 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
iptable_nat             3543  0 
snd_seq_oss            26722  0 
nf_nat                 15560  1 iptable_nat
snd_seq_midi            4557  0 
nf_conntrack_ipv4      10346  3 iptable_nat,nf_nat
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
fbcon                  35102  71 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nf_conntrack           60943  3 iptable_nat,nf_nat,nf_conntrack_ipv4
tileblit                1999  1 fbcon
snd_timer              19098  2 snd_pcm,snd_seq
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
font                    7557  1 fbcon
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_mangle          1549  0 
bitblit                 4707  1 fbcon
fglrx                2092908  32 
iptable_filter          1369  0 
uvcvideo               57406  0 
agpgart                31724  1 fglrx
softcursor              1189  1 bitblit
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_hwdep,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vga16fb                11385  1 
soundcore               6620  1 snd
videodev               34425  1 uvcvideo
ip_tables               9899  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               14175  2 iptable_nat,ip_tables
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
vgastate                8961  1 vga16fb
psmouse                63677  0 
v4l1_compat            13251  2 uvcvideo,videodev
shpchp                 28835  0 
video                  17375  0 
i2c_piix4               8335  0 
serio_raw               3978  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
[/COLOR]
```
dmesg | egrep 'rtl|firm|wlan0|eth1|eht2|eth3'
```
[COLOR=Red][   14.987710] udev: renamed network interface eth0 to eth3
[   16.659054] r8169: eth3: link down
[   16.659208] ADDRCONF(NETDEV_UP): eth3: link is not ready
[   76.519098] r8169: eth3: link up
[   76.519256] ADDRCONF(NETDEV_CHANGE): eth3: link becomes ready
[   86.580090] eth3: no IPv6 routers present[/COLOR]

```
ls /lib/firmware
```
[COLOR=Red]2.6.32-28-generic         i2400m-fw-usb-1.3.sbcf   rt2561.bin
2.6.32-33-generic         i2400m-fw-usb-1.4.sbcf   rt2561s.bin
2.6.32-34-generic         intelliport2.bin         rt2661.bin
3com                      ipw2100-1.3.fw           rt2860.bin
acenic                    ipw2100-1.3-i.fw         rt2870.bin
adaptec                   ipw2100-1.3-p.fw         rt3070.bin
advansys                  ipw2200-bss.fw           rt3071.bin
agere_ap_fw.bin           ipw2200-ibss.fw          rt73.bin
agere_sta_fw.bin          ipw2200-sniffer.fw       RTL8192E
aic94xx-seq.fw            iwlwifi-1000-3.ucode     RTL8192SE
ar7010_1_1.fw             iwlwifi-3945-2.ucode     sb16
ar9170-1.fw               iwlwifi-4965-2.ucode     scripts
ar9170-2.fw               iwlwifi-5000-1.ucode     slicoss
ar9170.fw                 iwlwifi-5000-2.ucode     sun
asihpi                    iwlwifi-5000-5.ucode     sxg
ath3k-1.fw                iwlwifi-5150-2.ucode     tehuti
atmel_at76c502_3com.bin   iwlwifi-6000-4.ucode     ti_3410.fw
atmel_at76c502.bin        iwlwifi-6000g2a-5.ucode  ti_5052.fw
atmel_at76c502d.bin       iwlwifi-6000g2b-5.ucode  tigon
atmel_at76c502e.bin       iwlwifi-6050-4.ucode     tr_smctr.bin
atmel_at76c504_2958.bin   iwlwifi-6050-5.ucode     ttusb-budget
atmel_at76c504a_2958.bin  kaweth                   usbdux
atmel_at76c504.bin        keyspan                  usbduxfast_firmware.bin
atmel_at76c506.bin        keyspan_pda              usbdux_firmware.bin
atmsar11.fw               korg                     v4l-cx231xx-avcore-01.fw
av7110                    libertas                 v4l-cx23418-apu.fw
bnx2                      matrox                   v4l-cx23418-cpu.fw
bnx2x-e1-4.8.53.0.fw      mts_cdma.fw              v4l-cx23418-dig.fw
bnx2x-e1-5.2.7.0.fw       mts_edge.fw              v4l-cx2341x-dec.fw
bnx2x-e1h-4.8.53.0.fw     mts_gsm.fw               v4l-cx2341x-enc.fw
bnx2x-e1h-5.2.7.0.fw      mwl8k                    v4l-cx2341x-init.mpg
cis                       myricom                  v4l-cx23885-avcore-01.fw
cpia2                     NPE-B                    v4l-cx23885-enc.fw
cxgb3                     NPE-C                    v4l-cx25840.fw
dabusb                    ositech                  v4l-pvrusb2-24xxx-01.fw
dsp56k                    ql2100_fw.bin            v4l-pvrusb2-29xxx-01.fw
dvb-fe-xc5000-1.6.114.fw  ql2200_fw.bin            vicam
dvb-usb-dib0700-1.20.fw   ql2300_fw.bin            whiteheat.fw
e100                      ql2322_fw.bin            whiteheat_loader.fw
ea                        ql2400_fw.bin            yam
edgeport                  ql2500_fw.bin            yamaha
emi26                     qlogic                   zd1201-ap.fw
emi62                     r128                     zd1201.fw
ess                       radeon                   zd1211
[/COLOR]
Please copy and paste the commands into the terminal, we may have to go a different route on the driver and firmware.
Thank you

Ok, here's this batch.

---

### Post by wildmanne39 on 2011-10-06
Hi, please unplug your wired connection or usb connection and try this:
```
sudo modprobe rtl8192ce
```
Thank you

---

### Post by a77ssii on 2011-10-06
> **wildmanne39 said:**
> Hi, please unplug your wired connection or usb connection and try this:
```
sudo modprobe rtl8192ce
```
[COLOR=Red]FATAL: Module rtl8192ce not found.[/COLOR]

Thank you

I also noted that on boot I'm seeing "Unable to Query Synaptic", it flashes on the screen very briefly.

---

### Post by wildmanne39 on 2011-10-06
Hi, please post the results of:
```
modinfo rtl8192ce_pci
```
Please do not use red it hurts my eyes.
Thank you

---

### Post by a77ssii on 2011-10-06
> **wildmanne39 said:**
> Hi, please post the results of:
```
modinfo rtl8192ce_pci
```Please do not use red it hurts my eyes.
Thank you


ERROR: modinfo: could not find module rtl8192ce_pci


No prob on the red, trying to differentiate between your code and my answer.  I'll use black unless you tell me otherwise.

Sidenote, your sig shows a link for the cube in 11.04, I've been playing with it and had some issues your instructions appear to remedy.  Is your tutorial all applicable to 10.04?

---

### Post by wildmanne39 on 2011-10-06
Hi, the guide for the cube can be used for 10.04 just ignore the part about disabling the plugins.

Please post the results of this command.
```
dmesg | grep -e wlan -e 8192
```
Thank you

---

### Post by a77ssii on 2011-10-06
> **wildmanne39 said:**
> Hi, the guide for the cube can be used for 10.04 just ignore the part about disabling the plugins.

Please post the results of this command.
```
dmesg | grep -e wlan -e 8192
```Thank you

[   16.187701] r8192ce_pci: disagrees about version of symbol module_layout

Thanks, you don't know how much your help with this means...

---

### Post by wildmanne39 on 2011-10-06
Hi the error shows that the driver was compile against the wrong kernel version, what kernel were you using when you ran the commands to install the driver?

Did you update after you ran the commands to install the driver before you restarted your computer?

Do you have linux kernel header and build essentials installed for the kernel we are installing this driver for?
Thank you

---

### Post by a77ssii on 2011-10-06
> **wildmanne39 said:**
> Hi the error shows that the driver was compile against the wrong kernel version, what kernel were you using when you ran the commands to install the driver? 2.6.32-34

Did you update after you ran the commands to install the driver before you restarted your computer? yes

Do you have linux kernel header and build essentials installed for the kernel we are installing this driver for? double checked and yes

Thank you

The only time I've switched back to -33 was after I did the driver  install/update/reboot into -34 and found I still did not have wireless.   I wanted to verify it was still functional in -33.  I then went back to  -34 and have stayed there since.  All of the work you have had me do  thus far has all been in kernel -34.
If appears to me the drivers are installed and are being seen by the  system but for some reason my wireless hardware in the computer is not  turned on and I have been unable to turn it on/off like I can in -33.   Is this possible?

---

### Post by wildmanne39 on 2011-10-06
Hi, I assure you the driver and firmware is not installed, what do you see that makes you think otherwise, I am looking at the information from the commands that is where it counts and that information says it is not.

There is also a bug that can cause this I am going to ask a friend to take a look.
```
sudo apt-get install linux-firmware
```
Thank you

---

### Post by wildmanne39 on 2011-10-06
Hi, yes it is possible for it to be off and not to want to turn on that is what I was looking for with this command.
```

rfkill list all
```
but it does not show anything on your computer.
Thank you

---

### Post by a77ssii on 2011-10-06
> **wildmanne39 said:**
> Hi, I assure you the driver and firmware is not installed, what do you see that makes you think otherwise, I am looking at the information from the commands that is where it counts and that information says it is not.

There is also a bug that can cause this I am going to ask a friend to take a look.
```
sudo apt-get install linux-firmware
```Thank you

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

---

### Post by a77ssii on 2011-10-06
> **wildmanne39 said:**
> Hi, yes it is possible for it to be off and not to want to turn on that is what I was looking for with this command.
```

rfkill list all
```but it does not show anything on your computer.
Thank you

I checked synaptic again and rfkill is installed.  I ran the command again and it still lists nothing.

---

### Post by a77ssii on 2011-10-06
Tried to go in the back door and use a windows driver, it installed fine and tells me there is no hardware present.  So even going that route the driver/system isn't seeing the hardware.

---

### Post by wildmanne39 on 2011-10-06
Hi, we will have to remove any drivers like windows drivers that you install so please do not install anymore.

I am going to wait until tomorrow for my fried to be on here because he probably knows an easy way to make the driver compile and install.
Thank you

---

### Post by a77ssii on 2011-10-06
They are already gone.  I installed, checked to see what the result was and removed them so my system is still the same as before.

---

### Post by 450rOOST on 2011-10-06
is there a way to delete posts?

---

### Post by wildmanne39 on 2011-10-06
Hi, yes please start your own thread your card is not the same as his.
Thank you

---

### Post by chili555 on 2011-10-07
> 02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
Kernel modules: r8192ce_pciOn a stock system, rtl8192ce is correct for your device. Your system reports r8192ce_pci, a similar but different module. Let's find out what you have. Please run and post:```
sudo updatedb
locate 8192ce | grep .ko
```updatedb will take a few moments; please be patient.

Once we know what you have, we will modprobe it and check dmesg for errors or warnings.

---

