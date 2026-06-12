---
title: "wireless install in asus netbook u10.04"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by al loomis on 2011-06-30
i bought a asus netbook and installed ubuntu 10.04 over the win7.

have not succeeded in establishing link to our wireless modem. i klik on the icon, get vpn configure, choose 'wireless,' and see 3 text boxes, 2 choice drops.

ssid: name of network

mode: left at 'infrastructure'

bssid: name of wireless modem, from the bottom of the box, 'admin' (?)

MAC address: 12 digit number off the bottom of wireless modem

MTU: left at 'automatic'

at this point, 'apply' does not become live, so i klik 'wireless security' 'none' is default, so  i leave it

on to 'ipv4 settings', no idea about dhcp so leave 'automatic', and klik 'routes'


insert 192.168.0.1    255.255.255.0    192.168.1.1    1    in 'wireless connection 1' as they are address of wireless modem, net mask, wan modem, but not at all confident about any of them

get an 'ok' and go back to dhcp screen, but 'apply' is not active.


so can not create a 'wireless connection.'

help,please.

---

### Post by bkratz on 2011-06-30
> **al loomis said:**
> i bought a asus netbook and installed ubuntu 10.04 over the win7.

have not succeeded in establishing link to our wireless modem. i klik on the icon, get vpn configure, choose 'wireless,' and see 3 text boxes, 2 choice drops.

ssid: name of network

mode: left at 'infrastructure'

bssid: name of wireless modem, from the bottom of the box, 'admin' (?)

MAC address: 12 digit number off the bottom of wireless modem

MTU: left at 'automatic'

at this point, 'apply' does not become live, so i klik 'wireless security' 'none' is default, so  i leave it

on to 'ipv4 settings', no idea about dhcp so leave 'automatic', and klik 'routes'


insert 192.168.0.1    255.255.255.0    192.168.1.1    1    in 'wireless connection 1' as they are address of wireless modem, net mask, wan modem, but not at all confident about any of them

get an 'ok' and go back to dhcp screen, but 'apply' is not active.


so can not create a 'wireless connection.'

help,please.

You do need the name of the network (whatever yours is called) that s the ssid. Infrastructure is correct. You don't need the bssid or mac address. MTU automatic is ok. You do need to set wireless security in case your network is wep or wpa or wpa2. Nothing if unsecured. You don't need any of those other number in the 'wireless connection 1'; that is just what you want to call it. Mine is just called wireless network! But have you checked to see if any additional drivers are available for your card. In the terminal type in 

lspci -nn

(that is LSPCI in lower case). Post back what it says about your network (wireless card) especially the xxxx:xxxx or just the name.

---

### Post by al loomis on 2011-06-30
thx for prompt action. 
i went to 'accessories' and kliked terminal: al@al-laptop:-$ lspci - nn (return) and got
[a screenful of configuration keys. but no names.]  i did see 'atheros' during an attempt to look at the bios. but it just flashed past with a note that 'shift + f10' would allow configuration. i don't know in what mode that is active.

there is a lan boot rom which i have set to 'enabled,' as that might be useful

none of this appears directly useful.

at this point, i can edit the 1st wireless screen, but can not get the security screen to light up 'apply'. the other screens will 'apply' although that just says the numbers are possible, not necessarily right.

maybe if i can get the security system on the wireless router and mirror it on the netbook something good will happen. this will take some time... will let you know results, and thx for efforts to date.

al loomis

---

### Post by wildmanne39 on 2011-07-01
> **al loomis said:**
> thx for prompt action. 
i went to 'accessories' and kliked terminal: al@al-laptop:-$ lspci - nn (return) and got
[a screenful of configuration keys. but no names.]  i did see 'atheros' during an attempt to look at the bios. but it just flashed past with a note that 'shift + f10' would allow configuration. i don't know in what mode that is active.

there is a lan boot rom which i have set to 'enabled,' as that might be useful

none of this appears directly useful.

at this point, i can edit the 1st wireless screen, but can not get the security screen to light up 'apply'. the other screens will 'apply' although that just says the numbers are possible, not necessarily right.

maybe if i can get the security system on the wireless router and mirror it on the netbook something good will happen. this will take some time... will let you know results, and thx for efforts to date.

al loomisHi run this command from a terminal again
```
lspci -nn
```
```
iwconfig
```
```
lsmod

```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets. You need to be connected to a wired network so you can post those results.

---

### Post by al loomis on 2011-07-01
wildmanne, will have to work on that: i have the readout for those commands and can copy, but will need some time to organize a wire link. i may have been a bit precipitous in overwriting win7 with u10.04.

bkratz, have found reference to 'wep' in wireless modem docs and selecting wep40/120 lights up the 'apply.' but no improvement, either with my guess about the addresses, or wiping them as you suggested.

---

### Post by al loomis on 2011-07-01
wild, hope i have the dump you need here.


i have also managed to catch the atheros config screen. there is only one articulation, a choice of 'pke' or' 'rpl'  on boot.  but the 'choice' doesn't work: choose 'rpl' and save/exit with f4, then restart and 'pke'  has been reinserted.  hmmm...

if all else fails i can buy another net cable, and return this one to my wife before she gets grouchy. but it would be nice to utilize the main function of this netbook. hope you can see an easy fix, i think even moderate difficulty looks too hard for me right now.

i am surprised three little screens and half dozen text boxes can be so difficult. 

thx for any help you can give me, al loomis






al@al-laptop:~$ lspci - nn
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
al@al-laptop:~$ 
al@al-laptop:~$ 
al@al-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

al@al-laptop:~$ 
al@al-laptop:~$ 
al@al-laptop:~$ lsmod
Module                  Size  Used by
ppp_async               6734  0 
crc_ccitt               1339  1 ppp_async
binfmt_misc             6587  1 
rfcomm                 33421  4 
ppdev                   5259  0 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
snd_hda_codec_realtek   203168  1 
joydev                  8708  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  4 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29297  1 i915
uvcvideo               56990  0 
btusb                  10925  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
soundcore               6620  1 snd
drm                   162471  5 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24177  2 i915
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63245  0 
serio_raw               3978  0 
video                  17375  1 i915
atl1c                  28083  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32008  2 
al@al-laptop:~$

---

### Post by wildmanne39 on 2011-07-01
Hi, run this command again please just copy and paste it so you make sure it is correct.
```
lspci -nn
```
Thank you.

---

### Post by Wim Sturkenboom on 2011-07-02
In case you don't understand what wildmanne39 is aiming at:

there is not supposed to be a space between the dash and the 'nn' in the lspci command

---

### Post by al loomis on 2011-07-02
sure enough, every little space makes a difference. i hope this is the real list, sorry about that.  -al

al@al-laptop:~$ 
al@al-laptop:~$ 
al@al-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:002c] (rev 01)
al@al-laptop:~$

---

### Post by wildmanne39 on 2011-07-02
Hi, ok try this command and 
```
rfkill unblock wifi
```
```
sudo ifconfig wlan0 down
```
followed by 
```
sudo ifconfig wlan0 up
```
post the outcome here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by al loomis on 2011-07-03
al@al-laptop:~$ rfkill unblock wifi
al@al-laptop:~$ sudo ifconfig wlan0 down
[[sudo] password for al: 
wlan0: ERROR while getting interface flags: No such device
al@al-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
al@al-laptop:~$ 

i have checked the lan boot rom status just before writing this, 'enabled'.

---

### Post by wildmanne39 on 2011-07-03
> **al loomis said:**
> al@al-laptop:~$ rfkill unblock wifi
al@al-laptop:~$ sudo ifconfig wlan0 down
[[sudo] password for al: 
wlan0: ERROR while getting interface flags: No such device
al@al-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
al@al-laptop:~$ 

i have checked the lan boot rom status just before writing this, 'enabled'.
Ok does your laptop have a function button to turn wireless on some are like fn or fn11? Because none of them command show a wireless card so it must be turned of, it is not a usb card right?

---

### Post by al loomis on 2011-07-03
asus netbook has a 'net' icon, configure offers a choice of 'wired' 'wireless' 'mobile broadband' 'vpn' and 'dsl.'

enter the wireless edit line and get a window like this:

SSID                  [homenet]

mode                 [infrastructure]

bssid                 [blank]

MAC address   [blank

MTU                 [automatic]

i have inserted the mac number of our wireless modem, to no avail.

then klik 'wireless security'

security             [WEP 128 bit passphrase] wep 40/128-bit key also lights up 'apply'

key                   [admin]

WEP index       [1 (default]

authentication  [open system]

then klik 'ipv4 settings'

method: auto dhcp

can add 'routes' or not, 'apply' not sensitive.

in 'routes

192.168.0.1  255.255.255.0 192168.1.1 1 for 'wireless modem,' mask, 'gate device,' label

sorry no scrnshot. active windows screenshot and openoffice picture editing outside my current range. will work on it.





 [IMG]file:///tmp/moz-screenshot-2.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG][IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by al loomis on 2011-07-05
attached screen shots: pictures of data i sketched above, previous post.

---

### Post by wildmanne39 on 2011-07-05
> **al loomis said:**
> attached screen shots: pictures of data i sketched above, previous post.Hi, under ipv4 tab then routes did you put the ip address in yourself? with dhcp checked you do not need to do that, in routes on mine it is blank and it works. Also where the SSID is, is that the real name of your network listed from your router? Still the commands you ran did not produce any wireless card that a am familiar with hopefully that is just an over  site on my part.

---

### Post by al loomis on 2011-07-05
the card, if it is a card, is internal, called 'atheros' and manages the wire link ok
i can get a config screen during boot  which offers 'network boot protocol' with a 2 position switch:

'pxe' or 'rpl'

but in fact this switch is overruled somewhere because the 'pxe' option always comes back on boot- change to  'rpl' and save/exit doesn't work.

'lan boot rom' is one of the options on the boot menu, 'enabled' seems best choice. perhaps it overrides the 'atheros' switch if they are not the same thing.

network name is likely to be right, it's in use with other machjines and was used on this machine before i wrote over the win7.

i have tried leaving the 'routes' blank, i'm sure you are right about optional.

it looks like i'm doing something wrong about the security protocol, i will have to talk to someone familiar with this wireless modem. more when i have some info....

---

### Post by wildmanne39 on 2011-07-05
> **al loomis said:**
> the card, if it is a card, is internal, called 'atheros' and manages the wire link ok
i can get a config screen during boot  which offers 'network boot protocol' with a 2 position switch:

'pxe' or 'rpl'

but in fact this switch is overruled somewhere because the 'pxe' option always comes back on boot- change to  'rpl' and save/exit doesn't work.

'lan boot rom' is one of the options on the boot menu, 'enabled' seems best choice. perhaps it overrides the 'atheros' switch if they are not the same thing.

network name is likely to be right, it's in use with other machjines and was used on this machine before i wrote over the win7.

i have tried leaving the 'routes' blank, i'm sure you are right about optional.

it looks like i'm doing something wrong about the security protocol, i will have to talk to someone familiar with this wireless modem. more when i have some info....Hi, I saw the atheros card but it is strange because it does not say what model, I suspect that the driver still needs installed but I do not know which one to tell you to install since the exact model of the card is not listed it is blank.

---

### Post by al loomis on 2011-07-07
yes, the atheros boot screen is also devoid of info on model number.

i have looked at a couple of ath drivers, but the installation procedure is over my head, even the explanations are too jargon heavy to help. this is depressing because it's likely this is the problem: installation of u10.04 didn't include config of the wireless card.
if ubuntu were not free, i would complain.

perhaps if i did a reinstall of u11.xx i would get something more advanced in the way of wireless management?

---

### Post by wildmanne39 on 2011-07-07
> **al loomis said:**
> yes, the atheros boot screen is also devoid of info on model number.

i have looked at a couple of ath drivers, but the installation procedure is over my head, even the explanations are too jargon heavy to help. this is depressing because it's likely this is the problem: installation of u10.04 didn't include config of the wireless card.
if ubuntu were not free, i would complain.

perhaps if i did a reinstall of u11.xx i would get something more advanced in the way of wireless management?
Hi, it is possible that if you reinstalled 11.04 with the wired internet connected and you chose to include updates and install third part software as part of the install it would help, but I am not going to say it will, only that it might. I have never seen one that did not show the complete model number of the card, that is strange, and makes it impossible to tell you which driver you need, plus as you said if the instructions confuse you that is also a problem.

---

### Post by wildmanne39 on 2011-07-08
> **al loomis said:**
> yes, the atheros boot screen is also devoid of info on model number.

i have looked at a couple of ath drivers, but the installation procedure is over my head, even the explanations are too jargon heavy to help. this is depressing because it's likely this is the problem: installation of u10.04 didn't include config of the wireless card.
if ubuntu were not free, i would complain.

perhaps if i did a reinstall of u11.xx i would get something more advanced in the way of wireless management?Hi, try this command in a terminal
```
sudo lspci
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by al loomis on 2011-07-08
i maybe ran 'sudo lspci' in response to answer from bkratz- see 1st response on page 1. not much point now: problem is not solved, but i evaded it by dloading u11.04 with only minor glitches.

presto!

thx for your sustained interest, it helped keep me trying things simple enough for me to do. merely getting an advanced version is not elegant, but i was about ready to modify my netbook with a hammer. 

regards, al loomis

---

### Post by wildmanne39 on 2011-07-08
> **al loomis said:**
> i maybe ran 'sudo lspci' in response to answer from bkratz- see 1st response on page 1. not much point now: problem is not solved, but i evaded it by dloading u11.04 with only minor glitches.

presto!

thx for your sustained interest, it helped keep me trying things simple enough for me to do. merely getting an advanced version is not elegant, but i was about ready to modify my netbook with a hammer. 

regards, al loomisHi, your welcome I am glad you got it working anyway, I have a hard time giving up, I think that last command might have told me what we need to know for some reason I had that problem with another user tonight and it took that command to see his card, because of root.

---

