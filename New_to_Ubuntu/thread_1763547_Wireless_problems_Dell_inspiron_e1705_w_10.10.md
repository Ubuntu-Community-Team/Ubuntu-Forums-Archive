---
title: "Wireless problems: Dell inspiron e1705 w/ 10.10"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by eeeark1 on 2011-05-20
I just installed Ubuntu 10.10 on my wife's Dell Inspiron e1705.  I'm having problems making the wireless work.  When plugged in everything works fine.  When unplugged the little "wifi" light is on above the keyboard (actually that light is on whether I'm plugged in or not) but the network manager notification deal has a little red exclamation point and says "no network connection".  I've tried many solutions I've found by googling but nothing has worked.  

I was using 11.04 but while attempting to make the wireless work using the command line I messed something up and I couldn't get a connection, wired or not.  I just re-installed 10.10 and I'd like someone to help if at all possible.  At least point me in the right direction PLEASE.

Thanks in advance.

---

### Post by jramshu on 2011-05-20
When you click on the network manager icon it doesn't show any available wireless networks?

Right click it and make sure enable wireless is checked.

---

### Post by eeeark1 on 2011-05-20
Clicked on it and "enable wireless" is checked.  I unchecked and re-checked.  It does not show any wireless networks.

---

### Post by josephmills on 2011-05-20
could you please open your terminal and type in ```
lspci -nn
``` and then ```
rfkill list all 
``` and paste here thanks

---

### Post by eeeark1 on 2011-05-20
:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

-------------------------

:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by josephmills on 2011-05-20
could we see a ```
lsmod | grep b43 
``` and a ```
dmesg | grep b43 
``` if it gives you nothing just say so thanks

---

### Post by eeeark1 on 2011-05-20
nothing doing when I enter either of those.

---

### Post by josephmills on 2011-05-20
ok try this ```
sudo apt-get install b43-fwcutter && firmware-b43-installer && bcmwl-kernel-source
``` then reboot and give us the info I asked about before thanks

---

### Post by eeeark1 on 2011-05-20
it says at the end "...command not found":

:~$ sudo apt-get install b43-fwcutter && firmware-b43-installer && bcmwl-kernel-source
[sudo] password for meredith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 326 not upgraded.
Need to get 16.3kB of archives.
After this operation, 81.9kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main b43-fwcutter i386 1:013-2 [16.3kB]
Fetched 16.3kB in 0s (20.0kB/s) 
Selecting previously deselected package b43-fwcutter.
(Reading database ... 121417 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-2_i386.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-2) ...
**firmware-b43-installer: command not found**

Is this a problem?

---

### Post by josephmills on 2011-05-20
> **eeeark1 said:**
> it says at the end "...command not found":

:~$ sudo apt-get install b43-fwcutter && firmware-b43-installer && bcmwl-kernel-source
[sudo] password for meredith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 326 not upgraded.
Need to get 16.3kB of archives.
After this operation, 81.9kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main b43-fwcutter i386 1:013-2 [16.3kB]
Fetched 16.3kB in 0s (20.0kB/s) 
Selecting previously deselected package b43-fwcutter.
(Reading database ... 121417 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-2_i386.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-2) ...
**firmware-b43-installer: command not found**

Is this a problem?
yes I wonder what is going on ohhh ok you need to open up ubuntu software center then go to edit-->software sources 
then make sure all are ticked see pic after that you are going to have to update to do this just do a ```
sudo apt-get update
``` the firmware is a 3rd party thing so ubuntu can not see it right now then retry post 8 again

---

### Post by jramshu on 2011-05-20
This may be a stupid question. Have you ran 
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by josephmills on 2011-05-20
> **jramshu said:**
> This may be a stupid question. Have you ran 
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

you should tell this person that this upgrades there whole system and put a new operating system on there computer I know it is still ubuntu but it is 11.04 and that is a new os too me (unity)

---

### Post by jramshu on 2011-05-20
It doesn't change my OS. I'm running 10.10.

---

### Post by eeeark1 on 2011-05-20
Ok I opened software sources and checked off all that appeared under "other software" however there were only 4 listed:
-Canonical Partners
-Canonical Partners (source code)
-Independent
-Independent (source code)

you seem to have a lot more listed on your screen shot.

I then went back to the terminal and entered:

sudo apt-get install b43-fwcutter && firmware-b43-installer && bcmwl-kernel-source

again and it said the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 326 not upgraded.
firmware-b43-installer: command not found

again "command not found" am I doing something wrong?
do I need to restart?

---

### Post by jramshu on 2011-05-20
Have you ran your update, upgrade, and dist-upgrade? I see 326 not upgraded.
EDIT: If 'dist-upgrade" makes you uncomfortable just run ```
sudo apt-get update && sudo apt-get upgrade
```
From the man pages.

 dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade
           command may remove some packages. The /etc/apt/sources.list file
           contains a list of locations from which to retrieve desired package
           files. See also apt_preferences(5) for a mechanism for overriding
           the general settings for individual packages.

---

### Post by josephmills on 2011-05-20
yes try and restart the reason I have so many is because I have alot of repos on this machine you should only have 4

---

### Post by josephmills on 2011-05-20
> **jramshu said:**
> Have you ran your update, upgrade, and dist-upgrade? I see 326 not upgraded.

From the man pages.

 dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade
           command may remove some packages. The /etc/apt/sources.list file
           contains a list of locations from which to retrieve desired package
           files. See also apt_preferences(5) for a mechanism for overriding
           the general settings for individual packages.

I am sorry my bad I thought that dist-upgrade upgraded your distro :confused: im an idiot

---

### Post by josephmills on 2011-05-20
also when you reboot try to add each one line by line 
so 
```
 sudo apt-get install b43-fwcuttter 
```
```
sudo apt-get install firmware-b43-installer 
```
```
sudo apt-get install bcmwl-kernel-source 
``` 
I highly suggest updateing and upgrading after we get this wireless figured out

---

### Post by jramshu on 2011-05-20
> **josephmills said:**
> I am sorry my bad I thought that dist-upgrade upgraded your distro :confused: im an idiot

It's nothing cuz. I thought the same thing before. I think the one you are thinking is "do-release-upgrade"


One reason I think the OP may be having some issues is his distro needs some serious updating. Probably is a couple kernels behind the current one for 10.10. 326 packages not upgraded is a lot.

---

### Post by eeeark1 on 2011-05-20
ok, I've restarted and did the three seperate install things you listed.  First and third said already the newest edition.  second installed. 

restart again?

---

### Post by jramshu on 2011-05-20
What about the third?

EDIT: My bad you said you did the third.

---

### Post by josephmills on 2011-05-20
> **jramshu said:**
> It's nothing cuz. I thought the same thing before. I think the one you are thinking is "do-release-upgrade"


One reason I think the OP may be having some issues is his distro needs some serious updating. Probably is a couple kernels behind the current one for 10.10. 326 packages not upgraded is a lot.

lets do it then 
```
sudo apt-get update 
``` then ```
sudo apt-get upgrade
``` see you in an hour or so...

---

### Post by eeeark1 on 2011-05-20
> **eeeark1 said:**
> ok, I've restarted and did the three seperate install things you listed.  First **and third **said already the newest edition.  second installed. 

restart again?

I think it's good to go.  Now what should I do?

---

### Post by josephmills on 2011-05-20
If you are upgrading right now please open anther terminal and type in ```
lsmod | grep b43 
``` and paaste here and also a ```
dmesg | grep b43 
``` anything come up this time ? if so please paste here thanks

---

### Post by eeeark1 on 2011-05-20
> **josephmills said:**
> If you are upgrading right now please open anther terminal and type in ```
lsmod | grep b43 
``` and paaste here and also a ```
dmesg | grep b43 
``` anything come up this time ? if so please paste here thanks

still nothing

currently upgrading...

---

### Post by josephmills on 2011-05-20
```
 rfkill list all
``` and a ```
lsmod | grep dell
``` thanks

---

### Post by eeeark1 on 2011-05-20
:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
meredith@meredith:~$ lsmod | grep dell
dell_wmi                2852  0 
dell_laptop             5730  0 
dcdbas                  5402  1 dell_laptop

---

### Post by josephmills on 2011-05-20
bingo I have seen this before ```
sudo rmmod -f dell-laptop
``` then let us see a ```
lsmod 
```

---

### Post by eeeark1 on 2011-05-20
> **josephmills said:**
> bingo I have seen this before ```
sudo rmmod -f dell-laptop
``` then let us see a ```
lsmod 
```

~$ lsmod
Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_idt      54887  1 
binfmt_misc             6599  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
joydev                  8735  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
i915                  290938  3 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30200  1 i915
b44                    26253  0 
ssb                    39288  1 b44
mii                     4425  1 b44
snd_timer              19067  2 snd_pcm,snd_seq
lib80211_crypt_tkip     7736  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  4 i915,drm_kms_helper
r852                    9536  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
wl                   1959533  0 
dell_wmi                2852  0 
dcdbas                  5402  0 
mtd                    18877  2 sm_common,nand
intel_agp              26360  2 i915
snd                    49006  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5168  1 i915
psmouse                59033  0 
soundcore                880  1 snd
video                  18712  1 i915
serio_raw               4022  0 
lib80211                5058  2 lib80211_crypt_tkip,wl
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
firewire_ohci          21106  0 
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
led_class               2633  1 sdhci
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core

---

### Post by eeeark1 on 2011-05-20
Not that we've finished yet but I really appreciate all your help guys.

---

### Post by josephmills on 2011-05-20
```
sudo modprobe b43 
``` then let us see a ```
lsmod | grep b43 
``` and a ```
dmesg | grep b43 
``` thanks again

---

### Post by eeeark1 on 2011-05-20
sorry for the delay.  Had to restart after upgrade.

sudo modprobe b43 asked for password then seemed to do nothing
lsmod | grep b43 ~$ lsmod | grep b43
b43                   168681  0 
mac80211              231541  1 b43
cfg80211              144470  2 b43,mac80211
ssb                    39288  2 b43,b44
led_class               2633  2 b43,sdhci
dmesg | grep b43 didn't seem to do anything

---

### Post by josephmills on 2011-05-20
getting closer before we do the next step do you care if you only have wireless and no eth0 (ethernet ) also try to install the firmware again ```
sudo apt-get install firmware-b43-installer 
``` then could we see a ```
dmesg | grep b43 
```

---

### Post by eeeark1 on 2011-05-20
I'd like both to be usable but if you are sick of helping me I understand, and actually I have to go to work in 20 minutes anyway...so can we make just wireless work for now?

thanks again

---

### Post by eeeark1 on 2011-05-20
h:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
meredith@meredith:~$ dmesg | grep b43
meredith@meredith:~$ 

second seemed to do nothing again

---

### Post by josephmills on 2011-05-20
> **eeeark1 said:**
> I'd like both to be usable but if you are sick of helping me I understand, and actually I have to go to work in 20 minutes anyway...so can we make just wireless work for now?

thanks again

yes do this 
```
sudo su 
```
```
echo >> b43  /etc/modules
``` 
```
exit 
``` then reboot with out the cat5 (ethernet) cable not in do you have wireless ? I need some beer and I like to help people out on ubuntu forums it is nice to see more people using ubuntu and linux for that matter :)

---

### Post by eeeark1 on 2011-05-20
still a no go = (

---

### Post by eeeark1 on 2011-05-20
I have to go to work now.  I can't tell you how much I appreciate your help even if we haven't gotten it working yet.  What should I try when I get home tonight?  I'd be more than happy to buy you some beers if it's possible. you have a way to take donations?

---

### Post by josephmills on 2011-05-20
> **eeeark1 said:**
> I have to go to work now.  I can't tell you how much I appreciate your help even if we haven't gotten it working yet.  What should I try when I get home tonight?  I'd be more than happy to buy you some beers if it's possible. you have a way to take donations?

hi there no gratuity is necessary, but thanks :) any ways I wrote this a little while ago and I think that It could help you. **Please see section on Installing b43fwcutter with out the internet connection ** this will work 100%

---

### Post by josephmills on 2011-05-20
hi there guys and girls:D 
If you think that you need the b43 or the b43sta, these are two different mods/drivers the first thing that you want to do is type in  
```
lspci -vnn | grep 14e4 
```
this is what this code will do  
**ls** stands for list 
**pci** stands for pci cards in the computer 
**-vnn ** stands for find the model number 
**grep** grep is a filter so it filters out the 14e4 thats why it is in a different color 
**14e4** is what grep (the filter)is looking for 
so ls-->+<--pci=list pci cards 
lspci -vnn= list pci cards with model number 
lspci -vnn | = listpci cards with model number and stop 
lspci -vnn | grep = list all pci cards with a model number and filter with grep 
lspci -vnn | grep 14e4 = list all pci cards with model number and a filter with grep using 14e4 for the filter.


So what does this all mean well the** b43fwcutter only**works for the model numbers [b]
14e4:4307
14e4:4311
14e4:4312 IMPORTANT if you have this card you need the firmwareb43-lpphy-installer for your firmware 
14e4:4318
14e4:4319
14e4:4320
14e4:5354
[/b]


If you have model number[b]
14e4:0576
14e4:4313
14e4:4315 
14e4:4328
14e4:4329
14e4:432a
14e4:432b
14e4:432c
14e4:432d       
14e4:4353
14e4:4357
14e4:4358
14e4:4359
14e4:435a
14e4:4727
14e4:a99d
[/b]
then you are going to need the **broadcom-sta-source + broadcom-sta-common** 

both the b43fwcutter and the b43sta use the firmware-b43-installer
unless noted 

If you have the model number 
[b]
14e4:4301
14e4:4306
14e4:4320 
14e4:4324
[/b]
Then you are going to need the **b43-fwcutter with the firmware-b43legacy-installer **

**IMPORTANT** all of these card also need the bcmwl-kerrnel-source

Ok now that we have found our card and its model number and we know what mod/driver and firmware we need. Its time to install all of it. 
**Important** for these next steps you will need a internet connection using a cat5 cable(ethernet) or whatever as long as you are on line. If are dealing only with wireless see section installing b43fwcutter with out internet connection. 

First before installing we need to remove anything that is there right now so open up synaptic package manager and type in bcm into the search bar then click on the green box's and mark for removal then press the apply button now reboot the computer 
after rebooting start to install the things that you need by opening up synaptic package manger and type in bcm follow the chart above to install the correct mods/driver and firmware then reboot again is your wireless working. 


If not lets do some diagnostics please open your terminal and type in 
```
rfkill list 
``` where **rf**stands for Radio frequency kill stands for umm... and list is to list all the Radio frequency
if there is a soft block or a hard block please do a ```
rfkill unblock all 
``` if that wont work try ```
rfkill unblock wifi or rfkill unblock wlan
```

Now that we know that nothing is blocked lets look at your mods/drivers 
 ```
lsmod | grep b43
``` this will **ls=list-->+<--mod=mods/driver** so ls+mod=list all mods | means stop and grep is the filter and b43 is what grep is looking for 
do you see you mods listed it would be nice if some of the people with working wireless could post there lsmod + there model number of there card 

If lsmod looks good lets move on to the firmware 
```
dmesg | grep b43 
``` so dmesg looks up what the linux kernel sees and grep is the filter **IMPORTANT if you are useing the b43sta then you need top type in wl instead of b43 **

Are you geting any errors go re-install the firmware again this is the part that seems to be "the bug in the gar" 

**Installing b43fwcutter with out the internet connection** 

Ok so you have no internet connection on your Ubuntu box for what ever reason. but you need it. Well here is how to get it. These are the things that you are going to need.  

1) a blank cd/dvd or a penn drive or external hard drive or some way to transfer files (phone?) whatever. 

2) you are going to need another computer of some sorts to download your mods/firmware 


Ok, now that you have thous two things lets move on.

download this file  [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)

Then transfer it over to your Ubuntu box 

Now in  your Ubuntu Box [computer]  please make your way to your **Home folder ** 

Once you are at your home folder right click on your home folder and ** make a new folder and call it wireless**

Now that you have made a new folder called wireless in your home directory. It is time to **move the downloaded file into the new folder called wireless** 

Next we need to move that folder to the firmware directory to do this open your terminal and type in 
```
sudo cp -r ~/wireless/* /lib/firmware/
``` 

Now lets double check to make sure the download made it to the firmware directory. Too do this type this into the terminal 
```
ls /lib/firmware
```
Do you see it there ? Good if not it did not moved. Go back to the last step and try again. But if you do see it lets move on to the next step

Ok so now that the download is in the firmware dir we are going to have to go there. To go there open your terminal and type in. 
```
cd /lib/firmware 
```
Now that you have moved lets double check to make sure this next code tells us where we are in the computer file dir. This next code stands for "print working directory" ```
pwd
``` are you at /lib/firmware if so good if not go back one step 

Now that we are in the firmware directory. We have to extract the download to do this type in 
```
sudo -s
``` then enter your password then 
```
tar -xzf b43-all-fw.tar_.gz
```
then 
```
exit
```

Now it is time to reboot 
```
sudo reboot 
```

Do you have wireless now ? If not you did some thing wrong. 
If you have some troubles please post here and some one will help you out 


Well I hope that this clears some stuff up about the b43fwcutter and the b43sta and also the b43-legacy have fun with your wire less! Please don't forget if you have one of these cards and they are working please post your lsmod and dmesg with model number of the card thanks again also I would like to say that I am working on a how to install with out the internet for the b43sta but do not have the hardware for it yet I am working on it. give me a couple of days thanks again and happy wireless :D
Joseph

---

### Post by eeeark1 on 2011-05-21
JosephMills,
Just wanted to say thanks for all your help with my wireless.  Finally got it working this morning after using the guide you posted for me.  Thank you, thank you, thank you.

---

### Post by fredboy on 2012-10-29
> **josephmills said:**
> hi there guys and girls:D 
If you think that you need the b43 or the b43sta, these are two different mods/drivers the first thing that you want to do is type in  
```
lspci -vnn | grep 14e4 
```
this is what this code will do  
**ls** stands for list 
**pci** stands for pci cards in the computer 
**-vnn ** stands for find the model number 
**grep** grep is a filter so it filters out the 14e4 thats why it is in a different color 
**14e4** is what grep (the filter)is looking for 
so ls-->+<--pci=list pci cards 
lspci -vnn= list pci cards with model number 
lspci -vnn | = listpci cards with model number and stop 
lspci -vnn | grep = list all pci cards with a model number and filter with grep 
lspci -vnn | grep 14e4 = list all pci cards with model number and a filter with grep using 14e4 for the filter.


So what does this all mean well the** b43fwcutter only**works for the model numbers [b]
14e4:4307
14e4:4311
14e4:4312 IMPORTANT if you have this card you need the firmwareb43-lpphy-installer for your firmware 
14e4:4318
14e4:4319
14e4:4320
14e4:5354
[/b]


If you have model number[b]
14e4:0576
14e4:4313
14e4:4315 
14e4:4328
14e4:4329
14e4:432a
14e4:432b
14e4:432c
14e4:432d       
14e4:4353
14e4:4357
14e4:4358
14e4:4359
14e4:435a
14e4:4727
14e4:a99d
[/b]
then you are going to need the **broadcom-sta-source + broadcom-sta-common** 

both the b43fwcutter and the b43sta use the firmware-b43-installer
unless noted 

If you have the model number 
[b]
14e4:4301
14e4:4306
14e4:4320 
14e4:4324
[/b]
Then you are going to need the **b43-fwcutter with the firmware-b43legacy-installer **

**IMPORTANT** all of these card also need the bcmwl-kerrnel-source

Ok now that we have found our card and its model number and we know what mod/driver and firmware we need. Its time to install all of it. 
**Important** for these next steps you will need a internet connection using a cat5 cable(ethernet) or whatever as long as you are on line. If are dealing only with wireless see section installing b43fwcutter with out internet connection. 

First before installing we need to remove anything that is there right now so open up synaptic package manager and type in bcm into the search bar then click on the green box's and mark for removal then press the apply button now reboot the computer 
after rebooting start to install the things that you need by opening up synaptic package manger and type in bcm follow the chart above to install the correct mods/driver and firmware then reboot again is your wireless working. 


If not lets do some diagnostics please open your terminal and type in 
```
rfkill list 
``` where **rf**stands for Radio frequency kill stands for umm... and list is to list all the Radio frequency
if there is a soft block or a hard block please do a ```
rfkill unblock all 
``` if that wont work try ```
rfkill unblock wifi or rfkill unblock wlan
```

Now that we know that nothing is blocked lets look at your mods/drivers 
 ```
lsmod | grep b43
``` this will **ls=list-->+<--mod=mods/driver** so ls+mod=list all mods | means stop and grep is the filter and b43 is what grep is looking for 
do you see you mods listed it would be nice if some of the people with working wireless could post there lsmod + there model number of there card 

If lsmod looks good lets move on to the firmware 
```
dmesg | grep b43 
``` so dmesg looks up what the linux kernel sees and grep is the filter **IMPORTANT if you are useing the b43sta then you need top type in wl instead of b43 **

Are you geting any errors go re-install the firmware again this is the part that seems to be "the bug in the gar" 

**Installing b43fwcutter with out the internet connection** 

Ok so you have no internet connection on your Ubuntu box for what ever reason. but you need it. Well here is how to get it. These are the things that you are going to need.  

1) a blank cd/dvd or a penn drive or external hard drive or some way to transfer files (phone?) whatever. 

2) you are going to need another computer of some sorts to download your mods/firmware 


Ok, now that you have thous two things lets move on.

download this file  [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)

Then transfer it over to your Ubuntu box 

Now in  your Ubuntu Box [computer]  please make your way to your **Home folder ** 

Once you are at your home folder right click on your home folder and ** make a new folder and call it wireless**

Now that you have made a new folder called wireless in your home directory. It is time to **move the downloaded file into the new folder called wireless** 

Next we need to move that folder to the firmware directory to do this open your terminal and type in 
```
sudo cp -r ~/wireless/* /lib/firmware/
``` 

Now lets double check to make sure the download made it to the firmware directory. Too do this type this into the terminal 
```
ls /lib/firmware
```
Do you see it there ? Good if not it did not moved. Go back to the last step and try again. But if you do see it lets move on to the next step

Ok so now that the download is in the firmware dir we are going to have to go there. To go there open your terminal and type in. 
```
cd /lib/firmware 
```
Now that you have moved lets double check to make sure this next code tells us where we are in the computer file dir. This next code stands for "print working directory" ```
pwd
``` are you at /lib/firmware if so good if not go back one step 

Now that we are in the firmware directory. We have to extract the download to do this type in 
```
sudo -s
``` then enter your password then 
```
tar -xzf b43-all-fw.tar_.gz
```
then 
```
exit
```

Now it is time to reboot 
```
sudo reboot 
```

Do you have wireless now ? If not you did some thing wrong. 
If you have some troubles please post here and some one will help you out 


Well I hope that this clears some stuff up about the b43fwcutter and the b43sta and also the b43-legacy have fun with your wire less! Please don't forget if you have one of these cards and they are working please post your lsmod and dmesg with model number of the card thanks again also I would like to say that I am working on a how to install with out the internet for the b43sta but do not have the hardware for it yet I am working on it. give me a couple of days thanks again and happy wireless :D
Joseph


Thank you very much for your guide. Using this along with [Post 31]("http://ubuntuforums.org/showpost.php?p=10842469&postcount=31"), I was able to get my wifi working. 

I found one caveat however... it seems that when I restart my laptop, I no longer have wifi (& it doesn't appear in the top network options). I've discovered that if I enter 
sudo modprobe b43
it becomes active again. Any idea's into what would cause that or how I could go about adding that to a startup routine. I'm attempting to understand linux better, so thank you for your help!

---

### Post by wildmanne39 on 2012-10-30
Please do:
```
sudo su 
echo b43 >> /etc/modules 
exit
```

---

### Post by wildmanne39 on 2012-10-30
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

