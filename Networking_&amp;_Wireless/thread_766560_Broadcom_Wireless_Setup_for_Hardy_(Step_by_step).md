---
title: "Broadcom Wireless Setup for Hardy (Step by step)"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by alex_kent_18 on 2008-04-25
I used the following steps to enable my _*Broadcom Wireless BCM4312 (rev 02)*_.

**Step 1 (run in terminal)**

[COLOR="Blue"]echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx[/COLOR]

[COLOR="Red"]**For Step 2, You can check your Broadcom wireless version with this command in terminal : [B][COLOR="Red"]"_*lspci | grep Broadcom\ Corporation*_"[/COLOR]**,if your wireless device is different from BCM4312 (rev 02), please refer to the following link for this step and you can continue again with step 3 onwards:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851")[/B][/COLOR]


**Step 2 (run in terminal)**

[COLOR="Blue"]sudo apt-get install cabextract
wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
cabextract sp34152.exe[/COLOR]

**Step 3 (run in terminal)**

[COLOR="Blue"]sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant[/COLOR]

**Step 4  (run in terminal)**

[COLOR="Blue"]sudo aptitude remove b43-fwcutter[/COLOR]

**Step 5  (run in terminal)**

[COLOR="Blue"]sudo gedit /etc/init.d/wirelessfix.sh[/COLOR]

**Step 6**

Paste the followings in the opened file(wirelessfix.sh)and **make sure you save it before continuing Step 7**

[COLOR="Blue"]#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
[/COLOR]
**Step 7  (run in terminal)**

Run this :

[COLOR="Blue"]cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh[/COLOR]

**Step 8  (run in terminal)**

finally run this:

[COLOR="Blue"]sudo update-rc.d wirelessfix.sh defaults [/COLOR]

**Step 9**

[COLOR="Blue"]Restart your machine[/COLOR] and enjoy the freedom from those wires....

---

### Post by jyanek on 2008-04-25
THANK YOU THANK YOU THANK YOU.  Several sleepless nights solved here.  Wireless works fine on my WMP54GS card now (4306 v3) thanks to you.  Well done.

Jay

---

### Post by bfkeats on 2008-04-27
That worked for my broadcom 4306 rev 03. Thanks a ton. asside: What the hell kind of an upgrade breaks both my wireless and ipod support?

---

### Post by mlaird on 2008-04-27
Which driver did you guys use for the 4306 rev 03? I see a download for the 4306 and the 4306 rev 02 on the linked page, but not the rev 03. Do either of you have and AMD 64 machine? And is your wireless interface wlan0, eth1, something else?

---

### Post by bfkeats on 2008-04-27
I used Step 2b from the link provided.

---

### Post by mlaird on 2008-04-27
> **bfkeats said:**
> I used Step 2b from the link provided.
Me too, but with no luck. Ubuntu AMD 64 or 32?

---

### Post by kevdog on 2008-04-27
Please post the exact steps and output from the steps you tried.  Without this its going to be hard for someone to help you.

---

### Post by mlaird on 2008-04-28
Actually, it seems to be working now. Not sure why it wasn't before. I've rebooted, tried switching between no security and WPA and it seems to work consistently. 

One thing I can't get to work that worked really well in 7.10 is a static IP. Anyone have any luck setting a static IP?

Edit: Static IP does work.

---

### Post by compwiz18 on 2008-04-28
Great post, thanks :) My previous ndiswrapper driver was locking up my computer but this one seems to work fine.:KS

---

### Post by biodiesel-bri on 2008-04-28
Thanks for this, I got it all to work after trying many other methods.  I wasn't able to see wireless until I issued this command:

```
sudo iwconfig wlan0
```

---

### Post by cyclingman on 2008-04-28
I presume there are several methods within this that require an internet connection (which is quite hard for me, hence the desperation for the drivers). 

I tried it, and got some errors, so I'll scavenge around for that old cable. Can someone just confirm this please.

(I get the error when trying to install cabextract - enabling the resporitries - refresh :()

---

### Post by kevdog on 2008-04-28
Search for a post written by Jamie Jackson about installation of broadcom drivers in 5 minutes.  He has links to all different types of drivers depending on your chipset.  Its really useful.

---

### Post by drs305 on 2008-04-29
Alex,

Thanks for this post. I was installing Hardy via wireless with no wired connection and (of course) lost my internet connection during the installation (very frustrating). Fortunately this laptop had windows on it so I was able to piece it together and got it working with your instructions. 

Oddly enough, after I got things working again I found similar notes in my old Gutsy installation memory joggers, but I forgot to look there first.
Anyway, a suggestion that might help out real newbies: Either change step 5 to read:
```
sudo gedit /etc/init.d/wirelessfix.sh &
```
and/or remind them to save and close gedit before accomplishing step 7. Otherwise they will return to the original terminal window to enter the command but it will still be awaiting the closure of gedit before it will do anything else. I understand this is pretty basic stuff but I can imagine when I was new to ubuntu not really understanding all the basics and getting hung up here.

Thanks again for helping getting my broadcom working again.

---

### Post by kevdog on 2008-04-29
Wouldn't a script similar to the following be more appropriate (I need some other testers besides myself on this one!!)

Follow original instructions Steps 1-4 and then do the following (NOTE - I included a restart option in case the modules somehow needed to be reloaded after hibernation or any such behavior in which you might need to reload the modules -- Strange things have happened in the past -- would reload modules with 
sudo /etc/init.d/wireless-broadcom-ndiswrapper restart
):




gksu gedit /etc/init.d/wireless-broadcom-ndiswrapper &

#!/bin/bash

#wireless-broadcom-ndiswrapper - This script takes care of loading ndiswrapper
#with broadcom chipsets to avoid the associated b44/ssb bug

case "$1" in
  start)
    # Unload conflicting modules
    echo "Unloading conflicting broadcom/ndiswrapper conflicting modules.."
	modules=`lsmod`
    echo $modules | grep -q b44 && rmmod b44
	echo $modules | grep -q b43 && rmmod b43
	echo $modules | grep -q b43legacy && rmmod b43legacy
	echo $modules | grep -q ssb && rmmod ssb
	echo $modules | grep -q ndiswrapper && rmmod ndiswrapper
	
	echo "Loading ndiswrapper/Broadcom modules.."
	modprobe ndiswrapper
	modprobe b44
    ;;
  stop)
    # I dont believe there is anything to do here.

    ;;
  restart)
    # $0 stop
    $0 start
    ;;
  *)
    echo "Usage: wireless-broadcom-ndiswrapper {start|stop|restart}"
    exit 1
  esac
 
exit 0 

Make file executable
cd /etc/init.d && sudo chmod 755 wireless-broadcom-ndiswrapper

Add the script to the rc levels
#To the best of my knowledge networking scripts are completed at runlevel 40
#Default is runlevel 20
#I need this script to be run after the wired/wireless modules have loaded in order 
#to reload the ndiswrapper kernel module prior to the ssb module
#Unclear if script needs to be run in runlevel =1 

sudo update-rc.d wireless-broadcom-ndiswrapper start 50 2 3 4 5 .

Restart your machine

---

### Post by sakid on 2008-04-29
I followed the steps in the first post and now when I log on to the machine it seems to lock up. It looks like its trying to load something because there is a white square in the top corner of the screen, it is about 1/4 of the screen.

Any ideas?

---

### Post by thefrozenpenguin on 2008-04-29
I have followed the instructino in post one to no avail and have trid various others from threads during hardy development, all with no joy.  I am really disappointed that 8.04 has lost what 7.10 had out of the box.  I have re-installed Mint4.0 which has the same driver install gui as 8.04 at it works without a hitch.  I think I'll wait for 8.10 for my next attempt.:(

---

### Post by Fuorigrottese on 2008-04-29
:lolflag:

THANKS FRIEND!!! REALLY THANKS !!! YUO'VE SOLVED MY PROBLEM WITH THIS STEP BY STEP GUIDE!!! YOU'RE GREAT !!! LONG LIFE TO YOU !! RESPECT!!! :guitar::)

---

### Post by jhmiller42 on 2008-04-29
OK -- I´m apparently an idiot. Trying to install ndiswrapper either through a terminal or Synaptics calls for my Hardy installation CD. I provide it, press Enter. It asks again. I press Enter. And so forth.

I´m beginning to think Linux is an anger-management training tool.

---

### Post by tmada on 2008-04-29
At first I was using the kernel 2.6.22-16-generic kernel and performed your ndiswrapper steps and it was unsuccessful. It would not recognize a device.
I then switched to the kernel 2.6.22-14-generic kernel and then it recognized the device and was able to connect to my network.

I have a 4318 Card (Asus WLan138v2) for reference.

---

### Post by drewcoon on 2008-04-29
THANK YOU!

I was SO sick of having to use my fallback wireless receiver that overheats and drops connection sporadically :o

I've tried multiple ndiswrapper install guides, but none of them worked until I found this one. Thanks again!! :)

---

### Post by alex_kent_18 on 2008-04-29
> **drs305 said:**
> Alex,

Thanks for this post. I was installing Hardy via wireless with no wired connection and (of course) lost my internet connection during the installation (very frustrating). Fortunately this laptop had windows on it so I was able to piece it together and got it working with your instructions. 

Oddly enough, after I got things working again I found similar notes in my old Gutsy installation memory joggers, but I forgot to look there first.
Anyway, a suggestion that might help out real newbies: Either change step 5 to read:
```
sudo gedit /etc/init.d/wirelessfix.sh &
```
and/or remind them to save and close gedit before accomplishing step 7. Otherwise they will return to the original terminal window to enter the command but it will still be awaiting the closure of gedit before it will do anything else. I understand this is pretty basic stuff but I can imagine when I was new to ubuntu not really understanding all the basics and getting hung up here.

Thanks again for helping getting my broadcom working again.
Hi,

Thanks for your suggestion. I was in my rush to go to bed as I needed to take a rest early for my work in the next morning. I have just amended my post according to your suggestion. Thank you very much for your reply indeed. 

Best regards,
Alex Kent

---

### Post by ravnistic on 2008-04-29
Hello, I'm very new to Ubuntu and I put a fresh install on my laptop today.

Its a dell inspiron 4100, p3 866, pretty basic. I have a broadcom minipci card I took from an HP, its a bcm94306mp.

I checked in terminal and it recognizes it as a Broadcom 4306 (rev 2)

I followed the directions, but when I got to the step "sudo modprobe ndiswrapper"
It said "FATAL ERROR -ndiswrapper not present" or something to that effect.

Everything seemed to go well up until that point, any ideas?

Thanks in advance

---

### Post by josel777 on 2008-04-30
Thank you, thank you, thank you! I have spent a ton of hours trying to get my wireless card to work correctly on hardy. It finally working thanks to you.

---

### Post by exactopposite on 2008-04-30
This works great for my Dell 1395 card which shows up as BC4310 rev1. I'm not sure why they don't work with the restriced drivers manager (i guess it's not called that anymore). I already ordered an intel card earlier today, but it's great to know there is a way to make this card work.

---

### Post by arden667 on 2008-04-30
> **sakid said:**
> I followed the steps in the first post and now when I log on to the machine it seems to lock up. It looks like its trying to load something because there is a white square in the top corner of the screen, it is about 1/4 of the screen.

Any ideas?

The same thing happened to me and it eventually booted up after I left it for a few minutes.

When it did boot, it gave me an error message.  My apologies for not having taken down the text of the error, but the gist of it was that something didn't load properly with the gnome desktop and it was disabled and would be tried again on my next login.  When my desktop loaded it had reverted itself to the default theme.  Any idea what's conflicting?

On the plus side -- the wireless is up!!  And it's working better for me than it was in Gutsy.  Hurrah!

EDIT:  Didn't have the same problem on the next boot.  Everything seems to be up and running just fine.

---

### Post by MelancholyStoo on 2008-04-30
Thanks for such a great post Alex, took me ages trying to get wireless working for my Broadcom 4306 rev 3.  In the end all I had to do was follow your instructions to the letter!  

Thanks again,
Stoo.

---

### Post by cyclingman on 2008-04-30
After failing to install my drivers via "hardware driver" I was pleased to see this post. I followed all steps successfully, and this is what I got:

The light of my Broadcom B43 wireless card turns on soon after my machine is switch on, but the second gnome is loaded, all lights switch off.

I have no internet connection (seeing as the lights aren't even showing). But strangely (or not), if I pull out the card, then put it back in, the lights return, yet still no connection.

Have I done something wrong? Is there a way of uninstalling, and stating the whole process again? Is there anything I have to change to the settings?

??? HELP! (I'm a bit of a beginner)

---

### Post by Bannor on 2008-04-30
please sticky this broadcom support is so all over the place

some I had to try 4 methods before this one finnaly worked

---

### Post by ronaldv2li on 2008-04-30
I LOVE YOU!!!!!!!!!!!! Had probems with wireless for soooo long... gave up with gutsy. THANK YOU! :D (K)

---

### Post by Feenix3k on 2008-04-30
> **jhmiller42 said:**
> OK -- I´m apparently an idiot. Trying to install ndiswrapper either through a terminal or Synaptic calls for my Hardy installation CD. I provide it, press Enter. It asks again. I press Enter. And so forth.

I´m beginning to think Linux is an anger-management training tool.

In synaptic Package manager click on setting then repositories, Under the Ubuntu Software tab theirs a window at the bottom that lists the Cdrom with Ubuntu 8.04, uncheck the box. Close window and click on reload , this will make you computer check repositories and not ask for the cdrom.

---

### Post by Feenix3k on 2008-04-30
If "modprobe -r b44" means to remove b44 this would kill my wired conection.

I am a newbie to termanal coding, and I am not sure what -r does.

---

### Post by matchstick on 2008-04-30
thanks.  i used the b43-fwcutter when i first updated to 8.04, but it seemed really slow.  after some looking around i found this guide and now the internet seems to be going much faster.

for the others that have the BCM4306 (rev 3) thats what i have, and i used step 2f (the same for rev 2), and it worked fine.

---

### Post by kevdog on 2008-04-30
modprobe -r = remove module == rmmod command
mdoprobe = insert module

---

### Post by togo59 on 2008-05-01
I've been trying to get this wireless thing working since November 2007! I swear I have faithfully followed every step in God knows how many tutorials*. *(see below)

I have a Viglen P4 with a Linksys wireless card using the BCM4306 chipset.

The driver file copied from Windows is BCMWL5.SYS (plus its companion, which I've called linksys.inf, since I'm told it doesn't matter what its called).

In response to $lspci -n | grep '14e4:43', I get: 14e4:4320 (rev 03)
In response to $sudo ndiswrapper - l, I get:
linksys driver installed
   device (14e4:4320) present (alternative driver: bcm43xx)

Why the alternative? I read somewhere else that this was a BAD THING. But I don't know why it keeps appearing.

I am running WPA encryption as when I'm in Windows mode I can see both my neighbours' wireless networks and no doubt they can see mine.

*As a result of all these attempts, when I follow the very clear instructions in this thread, I get warnings about driver already installed etc. So could you tell me what I have to delete or undo to go back to where I can start from line 1?

Also why don't I see wlan0? only eth1? Does it matter?

The current state is, if I look at Connection Properties, eth1:avahi Disconnected

Thank you.

---

### Post by alex_kent_18 on 2008-05-01
> **togo59 said:**
> I've been trying to get this wireless thing working since November 2007! I swear I have faithfully followed every step in God knows how many tutorials*. *(see below)

I have a Viglen P4 with a Linksys wireless card using the BCM4306 chipset. In response to $lspci -n | grep '14e4:43' I get 14e4:4320 (rev 03)

The driver file copied from Windows is BCMWL5.SYS (plus its companion .inf)

I am running WPA encryption as when I'm in Windows mode I can see both my neighbours' wireless networks and no doubt they can see mine.

*As a result of all these attempts, when I follow the very clear instructions in this thread, I get warnings about driver already installed etc. So could you tell me what I have to delete or undo to go back to where I can start from line 1?

Also why don't I see wlan0? only eth1? Does it matter?

The current state is, if I look at Connection Properties, eth1:avahi Disconnected

Thank you.
Hi, 

I could understand how hard you had tired during those several months and I do appreciate that you don't give up easily. 

Well, for your problem, run the following commands one by one in the terminal first before you are going to start the instructions of this thread:

[B][COLOR="Blue"]sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper[/COLOR][/B]

I hope to hear the good news from you soon.... Good Luck! 

Best regards,
Alex Kent

---

### Post by togo59 on 2008-05-01
Many thanks for your quick response. I followed all the steps, including the preliminary steps, got no errors or warnings. I remember seeing something about a wlan0 alias appearing, which filled me full of hope but it's still in the same state.

$iwconfig wlan0
no such device

Otherwise identical state to the above.

HOWEVER :redface:, I have all the time been trying to wrap the known-to-be-working-under-windows BCMWL5.SYS driver by pointing ndiswrapper at its .inf file. (As per your instructions.) I have assumed that the download step will only get me the latest driver. So that must be where I'm wrong. Since I don't have wireless, I have to keep switching between windows to get stuff and Ubuntu to try it. Long process. I will post back once I have tried again with the Step 2f driver.

---

### Post by togo59 on 2008-05-01
Well, something worked! I'm not out of the woods yet but I'm pretty sure, thanks to your help, that the driver is now working.

What I did different was
*sud apt-get remove ndiswrapper-util[COLOR="Red"]-1.9[/COLOR]* 
[The -1.9 was missing before]

And I used the BCMWL5.SYS from the download plus I didn't rename the .INF file (though I'm sure that doesn't matter).

The *sudo ndiswrapper -m* step gave a warning about a deprecated command. However, a later *iwconfig wlan0* still gave: No such device.:confused:

I am curious to know why, every time I run
*sudo aptitude remove b43-fwcutter*
it gets removed. How does it get put back?:confused:

I am now struggling with connectivity. The only wireless device I've managed to connect to so far is the wireless mouse!!:lolflag: (At least I think that's what it was.)

Now I'm on to it: The system reverts to its original state when I try to configure the network using Administration -> Network. I put in the ssid and password and all the wireless options disappear from the Network Configuration icon (two computers that get replaced by a signal strength icon).:confused: :confused:

Thanks again for your help. Now on to worry another thread about manually setting up WPA-PSK

---

### Post by kevdog on 2008-05-01
You either want nidswrapper(sys,inf) or bcm43xx.  You can't have both.  Id pick ndiswrapper -- the bcm43xx driver is loaded in the kernel and by default the bcm43xx driver is loaded into the kernel at boot.  To prevent this process you blacklist the bcm43xx driver during ndiswrapper installation.  ndiswrapper is still going to list this as an alternative driver, however b/c its not loaded, it will not conflict with ndiswrapper.

---

### Post by togo59 on 2008-05-01
> **kevdog said:**
> You either want nidswrapper(sys,inf) or bcm43xx.  You can't have both.  Id pick ndiswrapper -- the bcm43xx driver is loaded in the kernel and by default the bcm43xx driver is loaded into the kernel at boot.  To prevent this process you blacklist the bcm43xx driver during ndiswrapper installation.  ndiswrapper is still going to list this as an alternative driver, however b/c its not loaded, it will not conflict with ndiswrapper.

It IS blacklisted. I don't understand why it still says device (14e4:4320) present (alternative driver: bcm43xx)
:(

---

### Post by kevdog on 2008-05-01
If its blacklist dont worry about it -- it will always say its an alternative driver -- its a fyi.  You can always discover all the modules loaded at a given time with the 
lsmod
command.  If you do lsmod and dont find the bcm driver (or lsmod | grep bcm) then the module is not loaded and there will be no conflict.

---

### Post by WiredRogue on 2008-05-01
:guitar: You rock dood!
I spent 4 days trying every possible how-to out there. It would get so close but I knew that there must be something missing. Once I found this one all things changed. You created a great (and complete) how-to that worked 1st time out!
Many thanks

---

### Post by togo59 on 2008-05-01
I second that Kevdog! Thanks for your help. :)

(But I'm still stuck -- now reading/posting on the WPA threads.)

---

### Post by deviant on 2008-05-01
OK, I did everything step by step, but I still don`t have a working wireless.
My ndiswrapper module is loaded: 
```

itch@Sisif:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:a0:3d:2a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=ndiswrapper+bcmwl5 driverversion=1.52** 
```

I used metode 2a and 2b. None of the worked for me.
When I do "ifconfig -a" I can see my wlan0 connection, but in wicd (my connection manager) there is no active wifi connction.

```
itch@Sisif:~$ ifconfig -a
wlan0     Link encap:Ethernet  HWaddr 00:19:7e:a0:3d:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:efdfc000-efe00000

```

---

### Post by kevdog on 2008-05-01
*-network DISABLED 

Is there a switch or a place in the BIOS to activate the wireless interface.

What happens when you post
sudo ifconfig wlan0 up

Are you dual booting?

If you type dmesg -- getting any errors related to wlan0

---

### Post by cyclingman on 2008-05-01
I posted the following but got no reply, I just wouldn't mind a bit of response. Sorry if this is seen as spamming. Thanks again:

> After failing to install my drivers via "hardware driver" I was pleased to see this post. I followed all steps successfully, and this is what I got:

The light of my Broadcom B43 wireless card turns on soon after my machine is switch on, but the second gnome is loaded, all lights switch off.

I have no internet connection (seeing as the lights aren't even showing). But strangely (or not), if I pull out the card, then put it back in, the lights return, yet still no connection.

Have I done something wrong? Is there a way of uninstalling, and stating the whole process again? Is there anything I have to change to the settings?

??? HELP! (I'm a bit of a beginner)
__________________
Hardy Herron 8.04 - Dell Latitude C610 (pretty old laptop) 

---

### Post by deviant on 2008-05-01
> **kevdog said:**
> *-network DISABLED 

Is there a switch or a place in the BIOS to activate the wireless interface.

What happens when you post
sudo ifconfig wlan0 up

Are you dual booting?

If you type dmesg -- getting any errors related to wlan0

There is a place in BIOS from where I can enable / disable the wifi connection, but that was the 1st thing I checked.
When I do "sudo ifconfig wlan0 up", it shows ```
 May  1 23:48:37 Sisif kernel: [ 1151.877804] ADDRCONF(NETDEV_UP): wlan0: link is not ready

``` in /var/log/syslog.
And the network is now enabled (I had to load the ndiswrapper module before ssb).
```
itch@Sisif:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:a0:3d:2a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/23/2006, 4.40.1 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g 
```


LATER EDIT:
OK, the weirdest thing is happening: If I let ssb module register wlan0 before ndiswrapper, I can see my wifi connection, set it up, etc. Only that I can`t actually connect to my router (i reckon because it is WPA2 encrypted). But if I load ndiswrapper before ssb, the wifi connection is no longer available. And one other thing: when i try to unload ndiswrapper module via "sudo rmmod ndiswrapper", this is happening:
```
May  2 00:41:44 Sisif kernel: [ 2916.355277] ndiswrapper: device wlan0 removed
May  2 00:41:44 Sisif kernel: [ 2916.355337] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
May  2 00:41:44 Sisif kernel: [ 2916.355540] usbcore: deregistering interface driver ndiswrapper
May  2 00:41:44 Sisif kernel: [ 2918.445509] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
May  2 00:41:44 Sisif kernel: [ 2916.439043] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
May  2 00:41:44 Sisif kernel: [ 2916.439355] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
May  2 00:41:44 Sisif kernel: [ 2916.439420] PCI: Setting latency timer of device 0000:0b:00.0 to 64
May  2 00:41:44 Sisif kernel: [ 2916.447436] ndiswrapper: using IRQ 16
May  2 00:41:44 Sisif kernel: [ 2916.803064] wlan0: ethernet device 00:19:7e:a0:3d:2a using NDIS driver: bcmwl5, version: 0x4281300, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
May  2 00:41:44 Sisif kernel: [ 2916.803150] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
May  2 00:41:44 Sisif kernel: [ 2918.826615] usbcore: registered new interface driver ndiswrapper 
```

---

### Post by racin on 2008-05-01
BCM 4306 working on Gateway 7326 laptop. Thank You :guitar:

---

### Post by gcalca on 2008-05-01
Thanks for the guide!!! Got my Wireless working on Hardy (8.04), with step 2a, for HP Pavilion dv6408nr with BCM94311MCG wlan mini-PCI (rev 02). Thanks agains,

Gustavo.

---

### Post by IAmMe1 on 2008-05-01
Hm. I have the 4306 chipset, and I followed your instructions, but it's not seeing my network. 

iwconfig:
```
iwconfig eth1
eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lshw -C network:
```
network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth1
       version: 03
       serial: 00:0f:66:6e:a1:66
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,07/ latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

Anyone have any ideas? I've been messing with this for the past few days... *sigh*

Thanks... I hope someone will be able to resolve this frustration.

---

### Post by lowwie1 on 2008-05-01
Thank you!  After many unsuccessful attempts from other methods, I stumbled upon your well written procedure and was connected in 5 minutes.

Here is my chipset info:
> lspci -nn |grep Network 
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)

---

### Post by jhmiller42 on 2008-05-02
To be on the safe side, or so I thought, in Step 2 I substituted the location of the wireless driver from my manufacturer. But when I run cabextract on the executable, it tells me "no valid cabinets found".

Under WinXP, I can unpack the executable using WinRAR, and sure enough the .inf and other files are there. So what's up with cabextract?

---

Can I extract the necessary files under WinXP and skip cabextract altogether? All I need is the .inf, right?

---

Answer: Yes! Thanks for this tutorial, worked like a charm!

---

### Post by TrevP on 2008-05-03
Hi,

Just wanted to join everyone else in thanking you for this excellent post. I had completely given up on getting wireless to work under Hardy. I was previously running my card under the B43 firmware on 7.10 and it was VERY slow.Using the card now with ndiswrapper and the bcmwl5.inf driver I'm getting download speeds of up to 12 Mb/s!

The chipset on my card is 4306 rev3.

Thanks again :),
Trev

---

### Post by park8b156 on 2008-05-03
I didn't need all this I did like in 7.10 threw restricted drivers install.

---

### Post by watar on 2008-05-03
Thank you :) works like a charm with my 4318 rev02

I've gone from 150k/s to 8-10M/s

---

### Post by proud2bcdn on 2008-05-03
> **alex_kent_18 said:**
> I used the following steps to enable my _*Broadcom Wireless BCM4312 (rev 02)*_.

[COLOR="Blue"]Restart your machine[/COLOR] and enjoy the freedom from those wires....

Many thanks Alex, I've tried 7.10 and the Hardy beta with no success on my HP DV9000, your instructions worked very well with the Hardy release :-) I'll be dual booting for a while with Vista but hope to go full Hardy within a couple of weeks once I know I'm 100% functional.

Thanks again!!

James

---

### Post by RequinB4 on 2008-05-03
This fix is confirmed on Broadcom 4306 rev 03

The one note I would like to add - if you have been trying things other than what is on the first post, get rid of it if you can.  This is especially true for getting the right drivers - always re-download based on the link in the first post, even if you think you already have the right one.

---

### Post by ktb on 2008-05-03
Thanks for the instructions!

---

### Post by doriard on 2008-05-03
I started out using this method, but it failed twice right at the beginning.  First, the wget failed ... it hung and never seemed to find the sp34152.exe file.  It showed "===> PASV ..." for a long time with no wired network activity so I gave up.  So I searched the HP/Compaq site for that file and downloaded it via http. Second, the cabextract failed with the message "not a valid cab file".  So what can I do next? I have never gotten one of these ndiswrapper methods to work because there are always errors when running the instructions.  I tried using b43-fwcutter, but my adapter still isn't recognized.  Anyone care to offer some help?

UPDATE:
I finally found the right version of sp34152.exe on the HP website.  The correct one is 4.3MB.  After that it worked.  Now my adapter is finally being recognized.  I now have a wireles.  The next step is to figure out how to recognize my wireless router with SSID broadcast turned off.  Now it only recognizes it when SSID broadcast it on.

UPDATE 2:
Speed test for wireless: 6171Kbs downlink / 1594Kbs uplink, so speed is good.

---

### Post by matthorr on 2008-05-03
Thanks, Alex - this worked perfectly for my BCM4309 (rev 02).

The only problem is I can't connect with WPA (non-secure connections work fine).  Any suggestions?

---

### Post by brentb37043 on 2008-05-03
Thank You,
Tried 3-4 other ways with no luck. This worked with the a/b/g/n Broadcom AG4321 card from the HP TX1320US.

---

### Post by DoubleU29 on 2008-05-04
Thank you this worked with my Broadcom BCM4312 (rev 01)!! Thank you!!!

---

### Post by pdugas on 2008-05-04
Hi,

I am new to Linux and struggling to set up my Linksys 54G wireless card (a Broadcom 4306). 

A bit of background.  I had the card working on version 7.04 using FWCUTTER and BCM43xx driver (by following various posted threads) when I first loaded Ubuntu last month. I upgraded to version 7.10 and continued to use the BCM43xx drivers as it worked right from the upgrade point (i.e. did not use B43 drivers). When I upgraded to version 8.4 the wireless stopped working after first boot. I tried to invoke both the B43 drivers and Ndiswrapper based on this tutorial but to no avail.

I then tried a clean install and another tutorial to get the B43 drivers. I got the drivers to load and was able to get some communication to the card (the card was able to see the SSID broadcast, recognize whether PKA or no security was on, but never connected possibly by timing out). I know the card works (works in Windows XP and was working before the Hardy upgrade / clean install).

I am now trying this tutorial but I am having some problems getting it to work:

First problem:  in step 3, when I entered the command "sudo modprobe ndiswrapper" I got the response: module not found. I entered instead "sudo modprobe /usr/sbin/ndiswrapper" and continued following the instructions.

In the end, the wireless connection did not work and in response to lshw command I saw that the B43 drivers still owned the network card.

I then ran wirelessfix.sh script standalone and it had fatal error as it could not find module ndiswrapper. I changed ndiswrapper to /usr/sbin/ndiswrapper but to no avail it still could not find the module.

I am hoping someone can tell me what is wrong.


Thanks ....... Paul

---

### Post by sh00t on 2008-05-04
AWESOME! Worked seamlessly for my 4306 ver 3...just remember use step 2b! Thanks!

---

### Post by azhtar on 2008-05-05
Thanks a lot alex_kent_18, you're going to heaven, this totally worked, b43 just sucks, i had a very poor connection with B43, I mean, very friggin slow speeds, with ndiswrapper i have lower connection rate but i don't care as long as my internet connection don't give me 10 Kb/s as it did with B43.

THANK YOU!!!


BTW.- My system is a Pavilion Dv9074cl with a broadcomm BCM4312 Rev 02, I didn't have to download anything, i just looked for the inf file on my drivers disk and cabextracted it.

---

### Post by nivesh on 2008-05-05
alex_kent

thanks a million ! the device finally shows up and connects to my router !!


im having some connectivity issues though, it connects, authenticates me just fine, but there seems to be no data transfer, i can't even ping my router successfully

wireless_card_ip says destination host unreachable.

is the error i get, any ideas ?

I checked im getting an up from dhcp just fine.

---

### Post by andybob on 2008-05-05
Thanks for the guide but I am a little confused with this step:

> Step 6

***Paste the followings in the opened file(wirelessfix.sh)***and make sure you save it before continuing Step 7

#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

My Card is a BCM 4318 (rev02) and I have tried lots of stuff with no avail.  I would like to try this but I am confused with step 6.  Thanks for any help.



Andybob

---

### Post by Izzard on 2008-05-05
Hey there.

as many of you, I'm total newbie. I will gladly use guide from first post and cheer the author up _if_ I had internet. Can any of you post tutorial for non connected user (loser) for chip 4306 (rev 2) (compaq presario 2500)? Assume that I can download all required drivers using my other vista machine and move them to Ubuntu desktop using regular USB flash card.

Thanks.

---

### Post by andybob on 2008-05-05
What is the (wirelessfix.sh) file and where do I find it?



Andybob

---

### Post by andybob on 2008-05-05
> **andybob said:**
> What is the (wirelessfix.sh) file and where do I find it?



Andybob

Anyone????

---

### Post by pototo on 2008-05-05
> **andybob said:**
> What is the (wirelessfix.sh) file and where do I find it?



Andybob

When you get to step 5 you run:
```

[COLOR=Black][COLOR=Gray]sudo gedit /etc/init.d/wirelessfix.sh[/COLOR]
[/COLOR]
```[COLOR=Black]This creates an empty file named wirelessfix.sh, and opens it with gedit. All you have to do is paste this:
```


```[/COLOR]```
 [COLOR=Black][COLOR=Gray]#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44[/COLOR]
[/COLOR]
```[COLOR=Blue][COLOR=Black]in the opened file, then save it and continue with step 6.[/COLOR]
[/COLOR]

---

### Post by andybob on 2008-05-05
Thanks potato, I will give that a try when I get the chance.



Andybob

---

### Post by andybob on 2008-05-05
One more nOOb question:

When I run the commands can I copy and paste them all (as in step 1) or do I have to do each line seperetly?

Thanks,


Andybob

---

### Post by pdugas on 2008-05-05
New to Linux, I am happing problems with some steps in this tutorial. 

Specifically in STEP 3 with command:

[INDENT]sudo **modprobe** ndiswrapper [/INDENT]

[INDENT]returns:  **module not found**.[/INDENT]  

However I ran "ndiswrapper -l" successfully in the command just before it?? I don't understand whats happening.


Module not found is also happening after creating the "wirelessfix.sh" shell. When I run it, it returns **module not found** for both _modprobe -r_ and _modprobe_ ndiswrapper.


Also is ndiswrapper file suppose to be a shell script (which it is on my system) or a compiled module (which it is not)?


Appreciate any help.

........Paul

---

### Post by Izzard on 2008-05-05
> **Izzard said:**
> Hey there.

as many of you, I'm total newbie. I will gladly use guide from first post and cheer the author up _if_ I had internet. Can any of you post tutorial for non connected user (loser) for chip 4306 (rev 2) (compaq presario 2500)? Assume that I can download all required drivers using my other vista machine and move them to Ubuntu desktop using regular USB flash card.

Thanks.
Anyone? I need to know how to show in step 2 that drivers are not in the web, but on the desktop.

---

### Post by Ayuthia on 2008-05-05
> **Izzard said:**
> Anyone? I need to know how to show in step 2 that drivers are not in the web, but on the desktop.

Are you referring to this step?
> sudo apt-get install cabextract
wget [ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe)
cabextract sp34152.exe

Were you able to get cabextract?  If so:
```
cd ~/Desktop
cabextract sp34152.exe
```

If you don't have cabextract, I think that you can just execute the sp34152.exe in Vista and just copy the extracted files over.  I think that is what I did in XP, but that was a few months ago.

---

### Post by jorluiseptor on 2008-05-06
sudo thanks!


I've spent so many days figuring this out.

---

### Post by NE Key on 2008-05-06
> **andybob said:**
> One more nOOb question:

When I run the commands can I copy and paste them all (as in step 1) or do I have to do each line seperetly?

Thanks,


Andybob

You can copy and past (copy from web page - paste into terminal) but do it one line at a time.
(I do it - I think it avoids typos with complicated commands).

---

### Post by andybob on 2008-05-06
I did everything in the tutorial and I still cannot get it to work.

Here is my iwconfig output:

> andybob@andybob-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Also, here is the sudo lshw -C network output:

> andybob@andybob-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:8e:be:d8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.103 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:3e:50:e3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

I am at my wits end and not sure what to do.  Any help is appreciated.



Andybob

---

### Post by joplass on 2008-05-06
one of the best Linux wireless threads
great job mate.
thanks for sharing

---

### Post by DoubleU29 on 2008-05-09
Hello alex_kent_18! Your method works but i'd like to try the linux drivers for broadcome again, this time using CompactWireless.
What is the procedure to return to the original drivers?
Thank you very much again!

---

### Post by vigyani on 2008-05-09
I upgraded from 7.10 to 8.04 using 8.04 i386 DVD on HP NX6310 laptop. Earlier wireless interface was working fine using Ndiswrapper (installed using 'Windows Wireless Driver' in Admin menu) on Broadcom BCM4312 chipset. After upgrade (Kernel 2.6.22-16)there was no wireless network interface detected, whereas it shows that ndiswrapper is installed.

I rebooted using Kernel 2.6.22-14 and it recognizes Wireless interface correctly and connects to the wireless network fine.

It seems there is a problem with Kernel 2.6.22-16.
Any inputs?

regards
Vig

---

### Post by Ayuthia on 2008-05-09
> **vigyani said:**
> I upgraded from 7.10 to 8.04 using 8.04 i386 DVD on HP NX6310 laptop. Earlier wireless interface was working fine using Ndiswrapper (installed using 'Windows Wireless Driver' in Admin menu) on Broadcom BCM4312 chipset. After upgrade (Kernel 2.6.22-16)there was no wireless network interface detected, whereas it shows that ndiswrapper is installed.

I rebooted using Kernel 2.6.22-14 and it recognizes Wireless interface correctly and connects to the wireless network fine.

It seems there is a problem with Kernel 2.6.22-16.
Any inputs?

regards
Vig
Can you go to a Terminal and post your ndiswrapper -v and ndiswrapper -l?  There is a chance that you might have to reload your driver in 2.6.24-16.

---

### Post by tehMalone on 2008-05-09
You are now my official god!!!

---

### Post by TitanTiger on 2008-05-09
Can I just say you rock?

Thanks for the great instructions.  Worked on the first try with no problem.  What a great community. (Yeah, I'm a complete n00b to Linux).  My main system is a Mac but I'm excited to learn something new.

---

### Post by kevdog on 2008-05-09
Just to set the record straight -- WHICH THE ORIGINAL POSTER DID NOT DO -- these instructions were directly copied from this post as first written by Mazza558:
[http://ubuntuforums.org/showthread.php?t=734003&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=734003&highlight=ndiswrapper)

As a General Rule: People should no claim credit for another person's work without giving them credit.  A link to the original thread should be put in the main page.

---

### Post by hoarsecourser on 2008-05-09
Lots of good information here...I did the step-by-step...had it working, BUT now it won't. Not entirely true; I can connect to unsecured wireless.  The Network Manager taskbar dealie can see my secured wireless (WPA and WEP) and gives me network strength, but won't connect.  iwscan sees the same things. 

Basically, I want to un-do and re-do...any pointers on how to go about doing so?

---

### Post by TitanTiger on 2008-05-09
Not to nitpick, but this version was a lot better organized than the other one, at least for me.  But you're right, at least partial credit should have been given.  Either way, I'm happy.

---

### Post by Merrickk on 2008-05-09
Dell Latitude D830
Truemobile 1505 Wireless, detected as: 
Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

Working great, per first page instructions, used step 2d period per link to original help thread from Mazza558.

Step 2d: R151517 Driver Download/Extraction
wget [http://myspamb8.googlepages.com/R151517-pruned.zip](http://myspamb8.googlepages.com/R151517-pruned.zip)
unzip R151517-pruned.zip

Thank you Alex, Mazza, and everyone.  I'm breaking away, and this was my first roadblock into the new open source world.  Wish me luck, and thanks again.

---

### Post by Espionage724 on 2008-05-10
Worked like a charm thanks. No matter what I did I could never get the firmware driver off my system but I eventually figured out why 

(bcm43xx is older then the b43 driver, and I was using b43 when most guides told me to only mess with the bcm43xx driver)

Hint: Broadcom 4318 drivers can be found on the acer europe website (acer travelmate 2480 is the computer your looking for)

---

### Post by Laeth on 2008-05-10
I just wanted to say THANK YOU! Very, very much.

I had wireless working under 7.10, but when I upgraded, I lost the capabilities. After trying many methods, and even yours a few times, I remembered that even though the steps were familiar, if I used the drivers off my CD, it might work. Lo and behold it did.

For those of you having BCM4306 (rev 03), double check to see if your using WMP54GS wireless card, and use the drivers for that. It sounds simple, but when you're frustrated and trying to follow the instructions, you don't think about it. After reinstalling fresh and following these steps to a "T" with those drivers, my wireless started working right after the reboot.

---

### Post by stoneofshadow on 2008-05-10
how do i know if my wirless card is rev 02?

---

### Post by kevdog on 2008-05-10
lspci -nn

This should tell you!  If it is not check out this link since it basically tells you where to download the windows driver for whatever version card you have:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by cptaletsam on 2008-05-10
Finally, after three days and countless hours in search of a solution for this dreaded Broadcom issue I have found it. I really tried avoiding the ndiswrapper method because I wanted to try to get a native driver to work but all those methods failed miserably. Thank you for those clear and concise instructions.

---

### Post by stoneofshadow on 2008-05-10
i checked and i think mine is rev 03
but i still cant get those instructions to work for me
can someone make it more clear
like when to enter what and i should see when i do that
im sorry i cant figure out the simple instructions but im new here.

---

### Post by kevdog on 2008-05-11
See this guide --- its a lot more comprehensive:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

The solution posted in this guide is a lot more elegant:
```

echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```

Just read the guide!

---

### Post by nlstone123 on 2008-05-11
Thank you very much for this.  I had decided to give Ubuntu a try and for the life of me I could not get the wireless to work.  This worked perfectly the first time I tried it.

---

### Post by stoneofshadow on 2008-05-11
do i need the internet to install some of those packages it tells me to install or i dont really need it?

---

### Post by kevdog on 2008-05-11
Yes you will need an internet connection -- if not on the computer on another that you can transfer the driver file via USB to your ubuntu setup.  That's how I did it (and still do) when I reinstall.

---

### Post by n0m0reg0dz on 2008-05-11
i am having problems in step 2...i cant get the file in the dir so i can move on. i got the error, went on, but wireless aint working (obviously).
Can someone help me? i am on ubuntu 8.04 on a HP laptop

---

### Post by Leo9s on 2008-05-11
thank you so much. Wireless works great now.

---

### Post by tachibana on 2008-05-12
Thank you so much, this is very helpful. My wireless is working now.

---

### Post by snl2587 on 2008-05-12
On the step where you make the shell script, shouldn't it read:

#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe b44

so that ssb still loads?

---

### Post by Vinux75 on 2008-05-12
Thanks to Alex, following the steps has solved the problems I had with wl138 asus wireless lan card (Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)) with Hardy heron 8.04.

---

### Post by Otto-C on 2008-05-12
Using Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)). On Dell Inspiron B130.
Used 2a from the link

Everything went well till I got here:

bill@laptop:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
bill@laptop:~/bcm43xx$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: bcm43xx)
bill@laptop:~/bcm43xx$ sudo depmod -a
bill@laptop:~/bcm43xx$ sudo modprobe ndiswrapper
bill@laptop:~/bcm43xx$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
bill@laptop:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

bill@laptop:~/bcm43xx$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

bill@laptop:~/bcm43xx$ 

If I must re-do please step me through.
I have halted for now.
tia
Otto-C

---

### Post by germclown on 2008-05-13
w00t with capital zeros on this one!

I can verify this method for a BCM4318 (AirForce One 54g) after a fresh Hardy install (alt. CD) plus all standard updates available online prior to this post. I'm using an internal PC card on a typical year-old desktop.

Best of luck on future workarounds! But here's hoping (very sceptically) that I won't need one again...

===

PS: A tip: I have no way to connect this box via cable, so I borrowed a friends USB WiFi dongle. His worked fine OotB in Hardy so I had secondary wireless access throughout the install. Hardy actually shows an 'available network' list for each wireless card, so I could still tell which was connecting.

---

### Post by germclown on 2008-05-13
I got the same warning. I soldiered on and now I'm posting quick replies through my resurrected wireless connection!

I think it's probably just a note from the lib devs to people like the OP (who might want to look into it in case the command is removed someday, breaking his workaround)

---

### Post by germclown on 2008-05-13
Sorry for the multiposts. #106 was directed at Otto-C (I thought it was going to appear underneath his post and not down here)

---

### Post by gattopi on 2008-05-13
I have use the guide step by step but: ```

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.[LEFT][/LEFT]

lspci -n | grep '14e4:43'
10:00.0 0280: 14e4:4315 (rev 01)
10:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
 ndiswrapper -l
bcmwl5 : driver installed
 ndiswrapper -v
module details:
filename:       /lib/modules/2.6.24-17-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-17-generic SMP mod_unload 586 

 uname -r
2.6.24-17-generic




```

I have wifi hardware attivacted...
I use Ubuntu Hardy 32...


Help me Please

---

### Post by Ayuthia on 2008-05-13
> **gattopi said:**
> 
 ndiswrapper -l
bcmwl5 : driver installed

This message is telling you that the driver is installed, but it does not display that the device is present.  That generally means that it does not like the driver.  You might try to see if you can find another driver.  You might check this site for a driver:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Ayuthia on 2008-05-13
> **snl2587 said:**
> On the step where you make the shell script, shouldn't it read:

#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe b44

so that ssb still loads?
You do not need to have the modprobe ssb before modprobe b44.  This is because b44 needs ssb and will load it automatically.

---

### Post by Otto-C on 2008-05-13
I'm similar to Gattopi above. I used 2a, in step 2. I on a Dell Inspiron
B130 dual boot. I do not understand I previously used bcmwl5.inf on the
Ubuntu Dapper side and bcmwl5a.inf on the PCLOS .93 version. Here is my
information.
What to do next?
tia
otto-c
        iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

        lspci -vvnn
        02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

        ndiswrapper -l
        bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: bcm43xx)
        ndiswrapper -v
        utils version: '1.9', utils version needed by module: '1.9'
        module details:
        filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
        version:        1.52
        vermagic:       2.6.24-16-generic SMP mod_unload 586 

       uname -r
       2.6.24-16-generic

---

### Post by gattopi on 2008-05-14
THATS'WORK!!!

I have used the last driver form the list!!
Thanks!!

---

### Post by Otto-C on 2008-05-14
Since I had a no go using step 2a, can I delete/remove
dir bcm43xx and start over. Or is there an easier way?
tia
otto-c

---

### Post by Ayuthia on 2008-05-14
> **Otto-C said:**
> Since I had a no go using step 2a, can I delete/remove
dir bcm43xx and start over. Or is there an easier way?
tia
otto-c
At this point, it looks like you have a working install.  The key part is to make sure that you have the right modules removed before loading ndiswrapper.  You can do this by:
```
lsmod|grep -i e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
```
This checks to see what modules are currently active.  You should either see nothing or only ndiswrapper.  If you see any of the other modules, you will have to remove them by:
```
sudo modprobe -r <module>
```Replace <module> with the module that currently exists (ex. sudo modprobe -r bcm43xx).  As an extra note, ssb cannot be removed unless b43 and b44 are removed first.

Just to play it safe, you should remove ndiswrapper also.  Then we can load ndiswrapper back and check to see if the module loaded and nothing else:
```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
lsmod|grep -i e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
```
If ndiswrapper is there, then you should be able to test the connection.  If you cannot connect, you could try another driver. 

If ndiswrapper is not there, we need to figure out why it is not loading.

I would try this before deleting things and starting over.  Once you start trying to remove and restart, things could get messy.

---

### Post by Otto-C on 2008-05-14
Ayuthia,
Thanks for the reply here is what I got.

Your first step showed:

otto@desktop:~/bcm43xx$ lsmod|grep -i e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
grep: e: No such file or directory
grep: bcm43xx: No such file or directory

************

Did a locate ndiswrapper and find its onboard.
/home/otto/.local/share/Trash/files/tmp/ndiswrapper-1.52
Shows lengthy listing of ndiswrapper items.

Next?

Thanks
O

---

### Post by razzieboy on 2008-05-14
I was up and running with my wireless nightmare in no time. Thanks a lot. your step by step instruction is truly... a "step by step" solution.

---

### Post by Ayuthia on 2008-05-14
> **Otto-C said:**
> Ayuthia,
Thanks for the reply here is what I got.

Your first step showed:

otto@desktop:~/bcm43xx$ lsmod|grep -i e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
grep: e: No such file or directory
grep: bcm43xx: No such file or directory

************

Did a locate ndiswrapper and find its onboard.
/home/otto/.local/share/Trash/files/tmp/ndiswrapper-1.52
Shows lengthy listing of ndiswrapper items.

Next?

Thanks
O

Sorry, I missed a -.  It should have read:
```
lsmod|grep -i -e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
```

---

### Post by Otto-C on 2008-05-14
Now reads:

otto@desktop:~/bcm43xx$ lsmod|grep -i -e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
b44                    28432  0 
ssb                    32260  1 b44
mii                     6400  1 b44
ndiswrapper           192920  0 
usbcore               146028  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd

---

### Post by Ayuthia on 2008-05-14
> **Otto-C said:**
> Now reads:

otto@desktop:~/bcm43xx$ lsmod|grep -i -e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
b44                    28432  0 
ssb                    32260  1 b44
mii                     6400  1 b44
ndiswrapper           192920  0 
usbcore               146028  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
Do you know for  sure if you have a Broadcom **wired** card?  From you lspci -nn, did you  see another Broadcom card that had something like BCM44 in it?  I just want to confirm that you do need the b44 driver.  You might want to test your wireless without b44 to see if ndiswrapper works without it.

EDIT:
By the way, your wired card will not work if you disable b44.  You will have to enable your wired card again by doing sudo modprobe b44.

---

### Post by SurferGTO on 2008-05-14
i havent really seen anyone have any success with bcm4310 (my card) everything apparently installs fine no problem but i just dont have wireless.

---

### Post by Otto-C on 2008-05-14
Below is complete listing.
hth
otto-c

   lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 [8086:2666] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

---

### Post by Ocyberbum on 2008-05-14
i have the 4306 rev3 in a Hp zv5000 laptop. I tried to use the proprietary drivers in the Hardware Drivers Manager and had no luck. I followed the steps in this post and now after a reboot, i am able to see my network using KNetwork Manager and using Wireless Assistant to find my router and setup my WPA key but during the activation it sticks at 28% during the configuring stage and eventually gives me Connection Failure..

Does anyone have an idea,
Thanks

---

### Post by SirLawrence on 2008-05-14
> **SurferGTO said:**
> i havent really seen anyone have any success with bcm4310 (my card) everything apparently installs fine no problem but i just dont have wireless.

I was able to get my BCM4310 working using this step by step, but I also used another guide to recompile and load the latest ndiswrapper version.  

The problem I had was that ndiswrapper would see the driver but no device present:

bcmwl5 : driver installed


But now i got it to recognize the wireless device.

bcmwl5 : driver installed
	device (14E4:4315) present

Is this the same problem you're having?

---

### Post by Ayuthia on 2008-05-14
> **SirLawrence said:**
> I was able to get my BCM4310 working using this step by step, but I also used another guide to recompile and load the latest ndiswrapper version.  

The problem I had was that ndiswrapper would see the driver but no device present:

bcmwl5 : driver installed


But now i got it to recognize the wireless device.

bcmwl5 : driver installed
	device (14E4:4315) present

Is this the same problem you're having?

Can you share what you did? I am interested in how you resolved it though.

---

### Post by Ayuthia on 2008-05-14
> **Ocyberbum said:**
> i have the 4306 rev3 in a Hp zv5000 laptop. I tried to use the proprietary drivers in the Hardware Drivers Manager and had no luck. I followed the steps in this post and now after a reboot, i am able to see my network using KNetwork Manager and using Wireless Assistant to find my router and setup my WPA key but during the activation it sticks at 28% during the configuring stage and eventually gives me Connection Failure..

Does anyone have an idea,
Thanks
Have you already been successful in connecting without encryption?  If I recall it is at 56% when it is has reached the dhclient stage.  I think that 28% means that it is having problems at the iwconfig stage.  I could be wrong though.

---

### Post by Aaronb2245 on 2008-05-15
> **mlaird said:**
> Me too, but with no luck. Ubuntu AMD 64 or 32?

Step 2a worked for me and I'm running AMD 64bit on the 32 bit buntu 8.04 my card is a dell 1390 output from fiesty

---

### Post by germclown on 2008-05-15
Well... my joy has been mitigated. The connection is s l o w . . .

Just started redownloading EVE Online. Can't get more than 20kB/s from the downloader. Normally I'd chalk this up to EVE server load, but I've got no extra bandwidth. Everything else inernet-related is dead slow with that download running. I tried some package installation over top and Synaptic splits the 20kB/s with EVE. 

Normally I can expect at least 150kB/s (usually more if I find a good torrent). Needless to say: 20 < 150

Any ideas? I'm glad it's working and all, but full bandwidth will stop me from turning to the elephant in the room for bigger downloads.

---

### Post by germclown on 2008-05-15
I should have mentioned that I just put my laptop's USB WiFi into the desktop and now I've got 170kB/s for the EVE download. I guess I could do things this way, but it's less than ideal since my wife takes the laptop elsewhere fairly often.

---

### Post by i59b on 2008-05-15
> **bfkeats said:**
> That worked for my broadcom 4306 rev 03. Thanks a ton.

Worked on my 4306 rev 03 too.  Thanks very much for an excellent guide.

---

### Post by Landscapeman on 2008-05-15
Im unable to do the first step. Asks if I want to proceed Y/n, type Y and its abort?

---

### Post by Ayuthia on 2008-05-15
> **Landscapeman said:**
> Im unable to do the first step. Asks if I want to proceed Y/n, type Y and its abort?Can you post the abort message?

If you just want a guess, I am thinking it is because you don't have an internet connection right now.  If this is the case, you will need to add the install CD to your list of repositories:
```
sudo apt-cdrom add
sudo apt-get update
```From there you should be able to get it installed.

---

### Post by Landscapeman on 2008-05-15
I got it to work with not one bit of success. Tried the instructions and then after it still did not work I installed the B34 driver.I have tried both of them twice. No luck. Any ideas?

---

### Post by Ayuthia on 2008-05-15
> **Landscapeman said:**
> I got it to work with not one bit of success. Tried the instructions and then after it still did not work I installed the B34 driver.I have tried both of them twice. No luck. Any ideas?
Let me start by asking some questions:
1. Do you have a working internet connection in Ubuntu?
2. Can you attach your /etc/apt/sources.list?  It will help in figuring out what might be happening.
3. What is the error message that you are getting?
4. Can you post your lspci -nn|grep '14e4:43'?

---

### Post by sir4taye on 2008-05-16
Compaq presario f730us
amd64x2 (1.6ghz) tk-55
Broadcom 4311 rev 2
nVidia chipset & video
Hardy Heron


Much easier than post previously used and passed on. Running beautiful! Thank you for the nicely written step by step. It was much needed by many. We need more fixes listed like this for this movement to flourish. 
I used 2a without a hitch.

---

### Post by carverguy on 2008-05-16
try this simple fix for wireless

[http://ubuntuforums.org/showpost.php?p=4858558&postcount=40](http://ubuntuforums.org/showpost.php?p=4858558&postcount=40)

---

### Post by kingair_six on 2008-05-16
this worked perfect for me. i was about to quit with my broadcom 4318, but now it's fine. THANKS!

xubuntu:

one additional problem i had was that nm-applet (network manager) would not start up. the problem is solved by right-clicking into the star bar, selecting "Add New Item". Then you choose "System Tray".
Run ```
sudo nm-applet
``` in a command line, and the tray icon should appear. Happy:)

---

### Post by Landscapeman on 2008-05-16
what is a star bar?

---

### Post by Ayuthia on 2008-05-16
> **Landscapeman said:**
> what is a star bar?

I think that kingair_six is referring to the start bar (the panel).

---

### Post by Zlatan on 2008-05-17
> **DoubleU29 said:**
> Thank you this worked with my Broadcom BCM4312 (rev 01)!! Thank you!!!

same type of card, but did not work for me... I can see my card, but it can not find any wireless network...

---

### Post by germclown on 2008-05-17
Gah! This is horrible! I mentioned a littele ways above that my connection through the AirForce was slow in Ubuntu. Now it's also slow in windows! can't beat 40 kB/s now (I could normally average 180 from a good source). I'll ask elsewhere as well but does anyone know how to completely reverse this procedure? How can I get my old firmware back? It's nowhere to be found online.

...:(

---

### Post by kevdog on 2008-05-17
Reverse the process -- I'm basically taking this as meaning uninstall ndiswrapper?

---

### Post by kornel on 2008-05-18
Hi,
I follow all the steps and the wlan is working.
After restart the wlan not working and i receive the following dmesg message:

ADDRCONF(NETDEV_UP): wlan0: link is not ready

What is the problem?
Thanks

---

### Post by Feenix3k on 2008-05-18
I used step 2a and got wireless working. But after I did the steps to change the temporary changes to permanent I some how lost the b44 drive for my wired card. 

Any ideas what is going on?

---

### Post by kevdog on 2008-05-18
What happens you just type 

sudo modprobe b44

Does that load the driver at least??

---

### Post by freddymaertens on 2008-05-18
Thank you for your help. Unfortunately, it didn't work for me. Here are the vital stats -

Acer Aspire 5570Z

  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:6c:4b:5e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

iwconfig gives me this

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lspci | grep Network  gives me this

03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan
mini-PCI (rev 01)

My wireless adapter used to work. Then I installed Hardy. Now it won't
work. Help!!

---

### Post by Feenix3k on 2008-05-18
[QUOTE=kevdog;4990695]What happens you just type 

sudo modprobe b44

Does that load the driver at least??[/Q

The active connection information shows interface, speed ip and broadcast address , primary dns and hardware address. The spot the shows driver is blank. sudo modprobe b44 appears to do nothing.

lshw

     *-network:0 
                description: Ethernet interface 
                product: BCM4401 100Base-T 
                vendor: Broadcom Corporation 
                physical id: 1 
                bus info: pci@0000:02:01.0 
                logical name: eth0 
                version: 01 
                serial: 00:0b:db:9d:04:98 
                width: 32 bits 
                clock: 33MHz 
                capabilities: bus_master cap_list ethernet physical 
                configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.213.31 latency=32 module=ssb multicast=yes 
           *-network:1 
                description: Wireless interface 
                product: BCM4309 802.11a/b/g 
                vendor: Broadcom Corporation 
                physical id: 2 
                bus info: pci@0000:02:02.0 
                logical name: wlan0 
                version: 02 
                serial: 00:90:4b:63:82:b2 
                width: 32 bits 
                clock: 33MHz 
                capabilities: bus_master cap_list ethernet physical wireless 
                configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,12/04/2006, 4.10.4 latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

---

### Post by kevdog on 2008-05-18
What are you talking about, the wired interface is associated with the b44 module, look at the last line:

*-network:0
description: Ethernet interface
product: BCM4401 100Base-T
vendor: Broadcom Corporation
physical id: 1
bus info: pci@0000:02:01.0
logical name: eth0
version: 01
serial: 00:0b:db:9d:04:98
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.213.31 latency=32 module=ssb multicast=yes

---

### Post by Feenix3k on 2008-05-18
sudo modprobe ssb and sudo modeprob b44 are active, but something is keeping me from getting to the internet by wire. Also if i switch to wireless then back to wire the wired card is not connecting backto the network.

---

### Post by kevdog on 2008-05-18
You have to bring down both of the interfaces, and then only bring up the interface you want to work with.  It sounds like from your configuration (since you are not mentioning doing something different), that you can't have both up and connected using dhcp at the same time.

---

### Post by Ayuthia on 2008-05-18
> **freddymaertens said:**
> Thank you for your help. Unfortunately, it didn't work for me. Here are the vital stats -

Acer Aspire 5570Z

  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:6c:4b:5e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

iwconfig gives me this

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lspci | grep Network  gives me this

03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan
mini-PCI (rev 01)

My wireless adapter used to work. Then I installed Hardy. Now it won't
work. Help!!
Can you also show your ndiswrapper -v and ndiswrapper -l?

---

### Post by Feenix3k on 2008-05-18
> **kevdog said:**
> You have to bring down both of the interfaces, and then only bring up the interface you want to work with.  It sounds like from your configuration (since you are not mentioning doing something different), that you can't have both up and connected using dhcp at the same time.

In 7.10 I could switch quickly between wired and unwired. Looking at device network tools the hardware is running but not linking to the network.

The network card is unable to get the ip address from the dhcp server. If I turn roam off the wired connection and put it as a dhcp connection, wire disappears as a choice of connection. I also am not getting a defalt gateway, which I am told is suppose to be set by dhcp. 

Its so funny, I start wit 6.06 and it takes me a month to get wireless. I get wireless going in 8.04 and now I have to figure out how to get wired connection back.

---

### Post by kevdog on 2008-05-19
Ok, just try this assuming eth0 and wlan0 are your wired and wireless connections

sudo ifconfig wlan0 down
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0

What does the output state?

---

### Post by Feenix3k on 2008-05-19
And the data is


down

feenix@James-Laptop:~$ sudo ifconfig wlan0

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:63:82:b2  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:19 Memory:faffc000-faffe000 



down

eth0      Link encap:Ethernet  HWaddr 00:0b:db:9d:04:98  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:102 errors:0 dropped:0 overruns:0 frame:0

          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:11767 (11.4 KB)  TX bytes:19191 (18.7 KB)

          Interrupt:17 




up
feenix@James-Laptop:~$ sudo ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:0b:db:9d:04:98  

          inet6 addr: fe80::20b:dbff:fe9d:498/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:72 errors:0 dropped:0 overruns:0 frame:0

          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:7751 (7.5 KB)  TX bytes:12808 (12.5 KB)

          Interrupt:17 




Listening on LPF/eth0/00:0b:db:9d:04:98

Sending on   LPF/eth0/00:0b:db:9d:04:98

Sending on   Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4

No DHCPOFFERS received.

No working leases in persistent database - sleeping.

---

### Post by pallavis11 on 2008-05-19
See the info below:

[http://a2zhowto](http://a2zhowto) .blogspot.com/

[http://learnphpwithme](http://learnphpwithme) .blogspot.com/

---

### Post by kevdog on 2008-05-19
please post lshw -C network -- something is crazy here.

---

### Post by Feenix3k on 2008-05-19
> **kevdog said:**
> please post lshw -C network -- something is crazy here.

root@James-Laptop:/home/feenix# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:9d:04:98
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full latency=32 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlan0
       version: 02
       serial: 00:90:4b:63:82:b2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,12/04/2006, 4.10.4 ip=192.168.213.97 latency=32 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g

---

### Post by Feenix3k on 2008-05-19
The ifconfig

feenix@James-Laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:db:9d:04:98  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42306 (41.3 KB)  TX bytes:13370 (13.0 KB)
          Interrupt:17 

eth0:avahi Link encap:Ethernet  HWaddr 00:0b:db:9d:04:98  
          inet addr:169.254.6.161  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1398266 (1.3 MB)  TX bytes:1398266 (1.3 MB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:63:82:b2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:869832 (849.4 KB)  TX bytes:158031 (154.3 KB)
          Interrupt:19 Memory:faffc000-faffe000 


I have no idea whast this line is or what it does, I have never seen it befor in ifconfig



eth0:avahi Link encap:Ethernet  HWaddr 00:0b:db:9d:04:98  
          inet addr:169.254.6.161  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17

---

### Post by darkoptix on 2008-05-19
Works like a charm with Broadcom 4318 on a compaq v2710ca, thank you very much!

---

### Post by aczar on 2008-05-19
Hi,
I followed all the instructions and didn't seem to run into any problems.. until the restart when my feeling that this was too good to be true turned out to be right. I'm VERY new to ubuntu, and have been battling with my wireless card ever since.. I have scoured the forums for days and tried everything and it continues not to work. I will be eternally grateful for any help! 
I don't quite know what info to post.. but I ran iwconfig and saw this:

alex@alex-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

thanks..:s

---

### Post by Ayuthia on 2008-05-19
> **aczar said:**
> Hi,
I followed all the instructions and didn't seem to run into any problems.. until the restart when my feeling that this was too good to be true turned out to be right. I'm VERY new to ubuntu, and have been battling with my wireless card ever since.. I have scoured the forums for days and tried everything and it continues not to work. I will be eternally grateful for any help! 
I don't quite know what info to post.. but I ran iwconfig and saw this:

alex@alex-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

thanks..:s

Can you post the results of the following:
```
lshw -C network
lsmod|grep -i -e b43 -e b44 -e ssb -e ndiswrapper
cat /etc/modules|grep -i -e b43 -e b44 -e ssb -e ndiswrapper
```

---

### Post by John The Bad on 2008-05-19
Thank you so much for your brilliant step-by-step.  I now have wireless connectivity.

---

### Post by aczar on 2008-05-20
Thanks so much for quick reply. These are the results:

alex@alex-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth1
       version: 02
       serial: 00:90:4b:48:49:0f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,07/ latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0d:9d:82:5a:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.1.35 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes

alex@alex-laptop:~$ lsmod|grep -i -e b43 -e b44 -e ssb -e ndiswrapper
b44                    28432  0 
ssb                    32260  1 b44
mii                     6400  1 b44
ndiswrapper           192920  0 
usbcore               146028  3 ndiswrapper,ohci_hcd

alex@alex-laptop:~$ cat /etc/modules|grep -i -e b43 -e b44 -e ssb -e ndiswrapper
ndiswrapper

Alright thats it.. thanks!

---

### Post by Ayuthia on 2008-05-20
> **aczar said:**
> Thanks so much for quick reply. These are the results:

alex@alex-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth1
       version: 02
       serial: 00:90:4b:48:49:0f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,07/ latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0d:9d:82:5a:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.1.35 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes

alex@alex-laptop:~$ lsmod|grep -i -e b43 -e b44 -e ssb -e ndiswrapper
b44                    28432  0 
ssb                    32260  1 b44
mii                     6400  1 b44
ndiswrapper           192920  0 
usbcore               146028  3 ndiswrapper,ohci_hcd

alex@alex-laptop:~$ cat /etc/modules|grep -i -e b43 -e b44 -e ssb -e ndiswrapper
ndiswrapper

Alright thats it.. thanks!

From this information, it shows that you do not need the b44 driver and it does not look like you need ssb since you are using NDISwrapper.    I say this because your wired driver is netsemi and not b44.  So you really don't need to have the fix applied.  

However, Your wireless is still showing up as disabled.  Can you post your ndiswraper -v and ndiswrapper -l

---

### Post by aczar on 2008-05-20
here it is:

alex@alex-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586 

alex@alex-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)

---

### Post by Ayuthia on 2008-05-20
> **aczar said:**
> here it is:

alex@alex-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586 

alex@alex-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)

I am thinking that it does not like your driver.  More for research purposes, can you post your lspci -nm and:
```
ls -l /etc/ndiswrapper/bcmwl5*
```  
There are links for ndiswrapper and there are some that will match your card id numbers.  I am trying to see if this is the case.

---

### Post by aczar on 2008-05-20
alex@alex-laptop:~$ lspci -nm
00:00.0 "0600" "1002" "cab0" -r13 "" ""
00:01.0 "0604" "1002" "700f" -r01 "" ""
00:02.0 "0c03" "10b9" "5237" -r03 -p10 "103c" "0024"
00:06.0 "0401" "10b9" "5451" -r02 "103c" "0024"
00:07.0 "0601" "10b9" "1533" "10b9" "1533"
00:08.0 "0703" "10b9" "5457" "103c" "0024"
00:09.0 "0280" "14e4" "4320" -r02 "0e11" "00e7"
00:0a.0 "0607" "1217" "6972" "103c" "0024"
00:0c.0 "0c00" "104c" "8026" -p10 "103c" "0024"
00:10.0 "0101" "10b9" "5229" -rc4 -pb0 "103c" "0024"
00:11.0 "0680" "10b9" "7101" "103c" "0024"
00:12.0 "0200" "100b" "0020" "103c" "0024"
01:05.0 "0300" "1002" "4336" "103c" "0024"

alex@alex-laptop:~$ ls -l /etc/ndiswrapper/bcmwl5*
total 292
-rw-r--r-- 1 root root    723 2008-05-19 22:00 14E4:4301:4301:1737.5.conf
lrwxrwxrwx 1 root root     26 2008-05-19 22:00 14E4:4301.5.conf -> 14E4:4301:4301:1737.5.conf
-rw-r--r-- 1 root root    735 2008-05-19 22:00 14E4:4320:0417:14E4.5.conf
-rw-r--r-- 1 root root    735 2008-05-19 22:00 14E4:4320:4320:1737.5.conf
-rw-r--r-- 1 root root    735 2008-05-19 22:00 14E4:4320.5.conf
-rw-r--r-- 1 root root   9846 2008-05-19 22:00 bcmwl5.inf
-rw-r--r-- 1 root root 265728 2008-05-19 22:00 bcmwl5.sys

---

### Post by FredKratt on 2008-05-20
Everything is installed as per instructions but wireless will not turn on. It worked a couple of days ago before I tried to load Hardy.

R3000 loading Hardy - full disk install. Any ideas?

---

### Post by FredKratt on 2008-05-20
How do you disable Network:0?

---

### Post by Ayuthia on 2008-05-20
> **FredKratt said:**
> Everything is installed as per instructions but wireless will not turn on. It worked a couple of days ago before I tried to load Hardy.

R3000 loading Hardy - full disk install. Any ideas?
Can you post your ndiswrapper -l, ndiswrapper -v, and lshw -C network?

---

### Post by Ayuthia on 2008-05-20
> **aczar said:**
> alex@alex-laptop:~$ lspci -nm
00:00.0 "0600" "1002" "cab0" -r13 "" ""
00:01.0 "0604" "1002" "700f" -r01 "" ""
00:02.0 "0c03" "10b9" "5237" -r03 -p10 "103c" "0024"
00:06.0 "0401" "10b9" "5451" -r02 "103c" "0024"
00:07.0 "0601" "10b9" "1533" "10b9" "1533"
00:08.0 "0703" "10b9" "5457" "103c" "0024"
00:09.0 "0280" "14e4" "4320" -r02 "0e11" "00e7"
00:0a.0 "0607" "1217" "6972" "103c" "0024"
00:0c.0 "0c00" "104c" "8026" -p10 "103c" "0024"
00:10.0 "0101" "10b9" "5229" -rc4 -pb0 "103c" "0024"
00:11.0 "0680" "10b9" "7101" "103c" "0024"
00:12.0 "0200" "100b" "0020" "103c" "0024"
01:05.0 "0300" "1002" "4336" "103c" "0024"

alex@alex-laptop:~$ ls -l /etc/ndiswrapper/bcmwl5*
total 292
-rw-r--r-- 1 root root    723 2008-05-19 22:00 14E4:4301:4301:1737.5.conf
lrwxrwxrwx 1 root root     26 2008-05-19 22:00 14E4:4301.5.conf -> 14E4:4301:4301:1737.5.conf
-rw-r--r-- 1 root root    735 2008-05-19 22:00 14E4:4320:0417:14E4.5.conf
-rw-r--r-- 1 root root    735 2008-05-19 22:00 14E4:4320:4320:1737.5.conf
-rw-r--r-- 1 root root    735 2008-05-19 22:00 14E4:4320.5.conf
-rw-r--r-- 1 root root   9846 2008-05-19 22:00 bcmwl5.inf
-rw-r--r-- 1 root root 265728 2008-05-19 22:00 bcmwl5.sys

Are you using the driver that was in the first post([ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)?](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)?)  If not, you might try that one.  I think the driver is the issue.

The information above seems to point that the link does not match with your driver.

---

### Post by aczar on 2008-05-21
no i used a driver that was posted on the link.. should i do the whole process over with the driver you mentioned?

---

### Post by BCtom on 2008-05-21
[LEFT]I've been battling a loosing battle with my lap-top trying to get the wireless connection to connect.  To no avail, and to add salt to the wound, I have no wired connection either.

So I downloaded all the necessary files and programs from your "How To" list and tried to manually install them, hoping that everything would go smoothly with all the terminal commands--NOT!

My biggest problem is installing the Cabextract_1.1-2.deb software that you specified. I downloaded it from my PC, transferred it to Memery-Stick, then copied it onto the Lap-Top. I get a message that says thomething like, I should used the repositieryes instead. I click on Install, and it closes the window. 

I was just wondering if anyone here had a workaround for that. I have no way of conectiong it to the wired network. Actaully it did for a breaf moment, but when I rebooted, it went back to normal--no conection.
. 

[/LEFT]

---

### Post by Ayuthia on 2008-05-21
> **aczar said:**
> no i used a driver that was posted on the link.. should i do the whole process over with the driver you mentioned?

The driver that I mentioned is the same as the suggested driver in the post.  Unfortunately, I don't have a driver suggestion for you right now.  I have been working with another person who has the same driver as you and has the exact problem.  We have tried compiling ndiswrapper from source, tried a few different drivers and even changed links within NDISwrapper to point to a specific piece and have not been able to get it to work.  Not trying to discourage you, but just letting you know that I have not had much luck with the NDISwrapper route on this card.

You might try using the b43 driver instead.  It is the native Linux driver for the Broadcom cards.

---

### Post by Ayuthia on 2008-05-21
> **BCtom said:**
> [LEFT]I've been battling a loosing battle with my lap-top trying to get the wireless connection to connect.  To no avail, and to add salt to the wound, I have no wired connection either.

So I downloaded all the necessary files and programs from your "How To" list and tried to manually install them, hoping that everything would go smoothly with all the terminal commands--NOT!

My biggest problem is installing the Cabextract_1.1-2.deb software that you specified. I downloaded it from my PC, transferred it to Memery-Stick, then copied it onto the Lap-Top. I get a message that says thomething like, I should used the repositieryes instead. I click on Install, and it closes the window. 

I was just wondering if anyone here had a workaround for that. I have no way of conectiong it to the wired network. Actaully it did for a breaf moment, but when I rebooted, it went back to normal--no conection.
. 

[/LEFT]

Where did you get the file from?  Here is a link for Ubuntu:
[http://packages.ubuntu.com/hardy/utils/cabextract](http://packages.ubuntu.com/hardy/utils/cabextract)
You will need to pick the one that is for you (i386 for 32-bit and amd64 for 64-bit)

---

### Post by BCtom on 2008-05-21
> **Ayuthia said:**
> Where did you get the file from?  Here is a link for Ubuntu:
[http://packages.ubuntu.com/hardy/utils/cabextract](http://packages.ubuntu.com/hardy/utils/cabextract)
You will need to pick the one that is for you (i386 for 32-bit and amd64 for 64-bit)

Thank you for responding Ayuthia.

That was the same file I originally downloaded,  the cabextract_1.2-2_i386.deb-what I need anyway. I typed in the wrong version number--my bad--as I'm working from my PC, back and forth to my lap-top. Thank goodness USB memory sticks work with Hardy!

What seems to be happening is that when I call up the package manager, it tells me that I should go to the above link, and when I click "to install" it closes right away. I've tried several times....

So I was wondering if there was an alternative to loading the cabextract_1.2-2_i386.deb, say by way of using the Terminal, with some sort of command line? My command-line skills are very limited. I have the file on the lap-top ready to go though.

---

### Post by Ayuthia on 2008-05-21
> **BCtom said:**
> Thank you for responding Ayuthia.

That was the same file I originally downloaded,  the cabextract_1.2-2_i386.deb-what I need anyway. I typed in the wrong version number--my bad--as I'm working from my PC, back and forth to my lap-top. Thank goodness USB memory sticks work with Hardy!

What seems to be happening is that when I call up the package manager, it tells me that I should go to the above link, and when I click "to install" it closes right away. I've tried several times....

So I was wondering if there was an alternative to loading the cabextract_1.2-2_i386.deb, say by way of using the Terminal, with some sort of command line? My command-line skills are very limited. I have the file on the lap-top ready to go though.
You should be able to install it at the Terminal.  If the file is on your Desktop:
```
cd ~/Desktop
sudo dpkg -i cabextract_1.2-2_i386.deb
```

---

### Post by BCtom on 2008-05-22
> **Ayuthia said:**
> You should be able to install it at the Terminal.  If the file is on your Desktop:
```
cd ~/Desktop
sudo dpkg -i cabextract_1.2-2_i386.deb
```


Thank you, Thank you, Thank you, Thank you, Thank you!!!!!!!!!

YES! Thank you!

I appreciate your time and your knowledge and your willingness to help Ayuthia. I AM WIRELESS!!!!! Thank you!

---

### Post by Feenix3k on 2008-05-22
> **darkoptix said:**
> Works like a charm with Broadcom 4318 on a compaq v2710ca, thank you very much!

My roommate decided to duel boot his compaq with 8.04. The wireless worked like a dream, he also did not lose his wired connection for his wired card was a non-BCM card.

---

### Post by weekdaysailor on 2008-05-22
I got it working on my HP w/o ndiswrapper or any of the above magic - but stumbled on it, so not sure which trick...and may have missed something...

noticed everyone whining was also running wifi-radar so removed it...(didnt help but wait...)
removed b43 and bcm43xx per other threads
removed blacklist for bwm43xx
reinstalled b43-fwcutter (didnt help)
re-installed wifi-radar (hmm...) 
launched wifi-radar - got DHCP!! 

Now...have not rebooted yet - if Im not back in 10 minutes, send help...

...phew reboot worked - still running. 


keith@izzybuntu:~$ !lsp
lspci -nn | grep Network
02:06.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
keith@izzybuntu:~$

---

### Post by aczar on 2008-05-22
> **Ayuthia said:**
> The driver that I mentioned is the same as the suggested driver in the post.  Unfortunately, I don't have a driver suggestion for you right now.  I have been working with another person who has the same driver as you and has the exact problem.  We have tried compiling ndiswrapper from source, tried a few different drivers and even changed links within NDISwrapper to point to a specific piece and have not been able to get it to work.  Not trying to discourage you, but just letting you know that I have not had much luck with the NDISwrapper route on this card.

You might try using the b43 driver instead.  It is the native Linux driver for the Broadcom cards.

Alright :(. Maybe I should just go buy a usb wifi adapter...Anyways, if you do have any luck with this card please let me know. Thanks so much for your help!

---

### Post by zzw007008 on 2008-05-22
I've followed the guide and it works quite well in the process. However, the light on my notebook which indicates wireless card was still off when I finished the guide.

I think the problem is how to activate the wireless card. 

The following graphs shows the details about the problem. Someone please help me...

many thanks
[IMG]http://byfiles.storage.live.com/y1p7WvxuxrNyOmHi4UdSud_JOQDkG82VekiSbviMBhM_xtiDa456_JqEAnNvH0LzuS6fyaogLmnqRY[/IMG]
[IMG]http://byfiles.storage.live.com/y1p7WvxuxrNyOnjxEtvupkbD72bCJhD5QD8ln5DVNUEFfN3KRbdlsk2oVnYFWscA_YqgnihKCbIErg[/IMG]

---

### Post by xkaliburx on 2008-05-22
:: Problems with BCM4312 :: 

With all the inline threads, thought I would let people know this was a new case, I saw one person confirm the how-to worked on the card; so here is a lot of info, hope someone spots an easy fix, I will try to make commands in bold and my comments in itallics to help as this is going on 3 day's and I really need this working, so here goes;

**lspci** shows it as;
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

On Install: (*step 3, got about 20 or so of the below force parameter comment*)
 **sudo ndiswrapper -i bcmwl5.inf**
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2

**ndiswrapper -l**
bcmwl5 : driver installed
	device (14E4:4312) present (alternate driver: bcm43xx)

**sudo ndiswrapper -m**
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

After the restart, nothing, so here is all the debugging it seems people have asked for, if you guys need more, will gladly provide (just tell me what/how)

**lshw -C network**
 *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:1e:4c:5a:24:b5
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/23/2006, 4.40.1 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11a

(*not sure why the 802.11a as it's a g card and g network*)



**sudo dmesg |grep bcm**
[   30.991077] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[   31.137770] wlan0: ethernet device 00:1e:4c:5a:24:b5 using NDIS driver: bcmwl5, version: 0x4281300, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4312.5.conf

**ifconfig -a**
wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:5a:24:b5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f9ffc000-fa000000 

**modprobe -l |grep bcm**
/lib/modules/2.6.24-16-generic/kernel/drivers/media/dvb/frontends/bcm3510.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/bluetooth/bcm203x.ko

**ndiswrapper -l**
bcmwl5 : driver installed
	device (14E4:4312) present (alternate driver: bcm43xx)


**ndiswrapper -v**
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586 

----------------------------------------------------------

Well I use a simple app called wlassistant to view/connect to wireless networks but they all show no networks (it uses the /sbin/iwlist wlan0 scan command) but I get no network found.  I am broadcasting as are 2 of my neighbors and I can't see any.

Thanks for all the hard work I have already seen / worked through.

Lr

---

### Post by Ayuthia on 2008-05-22
> **xkaliburx said:**
> 
**ndiswrapper -l**
bcmwl5 : driver installed
	device (14E4:4312) present (alternate driver: bcm43xx)



Can you also provide your:
lsmod|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper -e b44

Lately, it seems that the alternate driver is ssb.  This is just going to verify that only ndiswrapper is loaded.

---

### Post by xkaliburx on 2008-05-22
**lsmod|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper -e b44**
b44                    28432  0 
ssb                    32260  1 b44
mii                     6400  1 b44
ndiswrapper           192920  0 
usbcore               146028  5 ndiswrapper,uvcvideo,ehci_hcd,uhci_hcd

I thought I knew alot into stepping into the wireless realm, man, my head hurts!  Thanks though.

---

### Post by Feenix3k on 2008-05-22
> **Ayuthia said:**
> Can you also provide your:
lsmod|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper -e b44

Lately, it seems that the alternate driver is ssb.  This is just going to verify that only ndiswrapper is loaded.


In 8.04 it is ssb, for bcm43xx is blacklisted on the install.

---

### Post by Ayuthia on 2008-05-22
> **Feenix3k said:**
> In 8.04 it is ssb, for bcm43xx is blacklisted on the install.

Is bcm43xx blacklisted also on upgrades?  I have not had a chance to confirm it.

---

### Post by Ayuthia on 2008-05-22
> **xkaliburx said:**
> **lsmod|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper -e b44**
b44                    28432  0 
ssb                    32260  1 b44
mii                     6400  1 b44
ndiswrapper           192920  0 
usbcore               146028  5 ndiswrapper,uvcvideo,ehci_hcd,uhci_hcd

I thought I knew alot into stepping into the wireless realm, man, my head hurts!  Thanks though.

Well, everything looks fine.  The only thing that looks odd is the alternate driver.  The only other comment is that if you are using NDISwrapper, you only need to add the b44 driver only if your wired connection uses the b44 driver.  Otherwise all you had to do is blacklist b43.  Having it there does not hurt anything, but it is an extra step that is not always needed.

---

### Post by xkaliburx on 2008-05-22
> **Ayuthia said:**
> Is bcm43xx blacklisted also on upgrades?  I have not had a chance to confirm it.

Not sure if it matters, this was a clean 8.04 install, no upgrade.

---

### Post by Feenix3k on 2008-05-22
> **Ayuthia said:**
> Is bcm43xx blacklisted also on upgrades?  I have not had a chance to confirm it.

When I went to 8.04, I already had it blacklisted to get my bcm4309 to work with ndiswrapper. In the forum I read the drivers were changed around. One of the changes was the dropping of bcm43xx.  So if you upgraded it may leave it or blacklist it. The only way to know for sure is to check the blacklist.

In case of a clean install of 8.04 it is blacklisted.

---

### Post by xkaliburx on 2008-05-22
Sorry if I am a bit vague but didn't need to use ndiswappers for wireless (nor 2 Ubuntu savvy), but this thread, the 2nd thing to do was;
"echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist"

so if you cat the blacklist file it is there.  Not sure if that's saying don't load it and it should or vise versa, but that's a bit more .02.

Thanks

---

### Post by Feenix3k on 2008-05-23
> **xkaliburx said:**
> Sorry if I am a bit vague but didn't need to use ndiswappers for wireless (nor 2 Ubuntu savvy), but this thread, the 2nd thing to do was;
"echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist"

so if you cat the blacklist file it is there.  Not sure if that's saying don't load it and it should or vise versa, but that's a bit more .02.

Thanks
The above command puts bcm43xx on the blacklist.

---

### Post by thejem on 2008-05-23
Thank guys finally got my HP dv6701 working wirelessly.....

---

### Post by jhmoralesr on 2008-05-23
Thanks for the post, I have a dell inspiron 1720, my broadcom version is BCM4328 (rev 03), tried the steps listed in the post and link and it worked perfectly.

---

### Post by aggiemarine07 on 2008-05-23
I still can not get it to work on my dell 1525. I have spent the better part of two weeks trying to get wireless to work with this laptop and I have had no success at all. I even did a clean install of 8.04 and followed these instructions and now I can not even see other networks at all. Could anyone tell me what I am doing wrong? I'll provide an outputs you need. Thanks!

---

### Post by Ayuthia on 2008-05-23
> **aggiemarine07 said:**
> I still can not get it to work on my dell 1525. I have spent the better part of two weeks trying to get wireless to work with this laptop and I have had no success at all. I even did a clean install of 8.04 and followed these instructions and now I can not even see other networks at all. Could anyone tell me what I am doing wrong? I'll provide an outputs you need. Thanks!
Can you post the following:
```
lshw -C network
lsmod|grep -i -e b43 -e b44 -e ssb -e bcm43xx -e ndiswrapper
ndiswrapper -l 
ndiswrapper -v
```

---

### Post by aggiemarine07 on 2008-05-23
Thanks for responding to my post, here are my outputs for the following commands that you requested. Thanks!

**lshw -C network**

  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:3a:e5:14
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.2.6 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0


[B]
lsmod|grep -i -e b43 -e b44 -e ssb -e bcm43xx -e ndiswrapper[/B]

b44                    28432  0 
ssb                    32260  1 b44
mii                     6400  1 b44
ndiswrapper           192920  0 
usbcore               146028  5 ndiswrapper,uvcvideo,ehci_hcd,uhci_hcd
[B]
ndiswrapper -l[/B] 

bcmwl5 : driver installed

[B]
ndiswrapper -v[/B]

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586

---

### Post by Ayuthia on 2008-05-23
> **aggiemarine07 said:**
> 
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

You might want to try this out:
[http://ubuntuforums.org/showthread.php?t=786397](http://ubuntuforums.org/showthread.php?t=786397)
This one seems to work for some 4310 cards.  You will most likely need to use the driver in step 0 and make sure that you do step 2.  That seems to be the helping factor.

---

### Post by aggiemarine07 on 2008-05-24
Sweet! thanks, now I can see networks (more than before) and I can successfully connect to them. I will play with it for the next day or two and post back on here if it continues to be successful. Thank you for your posts and patience!

edit: for anyone in the future, I called up Belkin (people who made my wireless router) and they said that if your having difficulty connecting to a wireless network to try using WEP because in their words "WPA/WPA2 is a very heavy protocol and cant cause a lot of timeouts when connecting." Dont know how much truth there is to it but just thought I would put that out there for those who are having a difficult time getting wireless working.

---

### Post by rksingh54 on 2008-05-25
I followed your instructions and find that WLAN light on my computer is on but I am still unable to get Wireless LAN. 

My Computer is HP Pavalion dv6225us and Wirles card is Broadcom with chip BCM4311 (rev 01).

Could you please help me solve this problem?

RKS

---

### Post by Mainiak Blaniak on 2008-05-25
Thank you, Thank you, Thank you.  After about 16 hours of trying various how-to's, I finally got my wireless working (I now avoid the wrath of my wife, who would go nuts if I were to spend 16 hours on the computer if she were'nt out of town for the weekend :) )  This is actually the third time I tried this particular how-to, the second with the specific driver I used, and the first on an absolutely clean install of Hardy (this was the absolute first thing I did after taking the disc out after reinstalling for the 5th time).

At any rate, I ended up changing the procedure in the original post very slightly, so I'll go through what I did and what I am using for hardware to hopefully help the next guy.

Hardware is a Linksys wifi card with Broadcom 4306 rev. 3 chipset

After installing Hardy, and WITHOUT using the restricted drivers manager to install the drivers for my wifi card (which did NOT work the 3 times I tried it...but did work well in Gutsy) I did:

(sorry, I don't know how to make the neat code boxes in a post, so...)

code: lsmod | grep -i -e b43 -e b44 -e ssb -e b43legacy -e bcm43xx -e ndiswrapper

and noted that both b43 and ssb were in use.  Therefore I did:

code: echo 'blacklist b43' | sudo tee -a /etc/modprobe.d/blacklist
      echo 'blacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist
      sudo modprobe -r b43
      sudo modprobe -r ssb

I then proceeded from the first step of the first post of this thread to the letter.  For step 2 I used 2b

When I got to step 6, I left the last line "modprobe b44" out of the wirelessfix.sh file as I don't have a wired connection on my wireless card and therefore don't need b44.

Other than those minor changes, everything was line for line, and I am now running wirelessly.

Hope this helps someone out!

MB

---

### Post by mimiko on 2008-05-25
Thank you for this great walk-through!:)

I'd like to provide some info for those who may have odd Broadcom drivers.

I got wireless to work on a **Dell Latitude D610** which has this driver:  *Broadcom Corporation BCM4309 802.11a/b/g (rev 03)*

As such, when I got to step to and was redirected to the wifi documentation page, I then followed step 2a on that page **([here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-dfa35a08da26002d337e79d528efb0c4ed5a127f"))**

Good luck everyone!

---

### Post by nutpants on 2008-05-27
the directions worked great for my dell xps m1210 with a Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

thank you for all your hard work..

nutz

---

### Post by bryan6376 on 2008-05-27
I have a BCM4306 card, ver 03.  This post was extremely helpful for me.  Here's how I got my card working.

After numerous failures, I finally reinstalled Heron, figuring I'd messed up my wireless settings beyond repair.  Now, here are my steps:

Step 1:  Install all updates via Update Manager  (about 102 of those)

Step 2: DO NOT USE THE DRIVER IN system->Admin->Hardware!!!!!!

Step 3: Follow this post to the letter.  During Mr. Kant's step two, I clicked the link under the red lettering, and followed step 2b (the general bcm4306 step.  For every step, I literally copied and pasted the lines into my terminal.

Step 4: Don't forget to restart

---

### Post by rksingh54 on 2008-05-27
Thanks, I have just been able to set up my WLAN on HP pavilion dv6225us and it seems to be working so well now.

RKS

---

### Post by gspaulding on 2008-05-28
Many thanks.  My e-machines M6805, amd 64, hardy i386, broadcom 4306 (rev 03) is connected wirelessly as wlan0 using 2f for step 2.

---

### Post by angelsguitar on 2008-05-29
Thanks, finally got working a bcm4318 rev02 from a friends laptop with your howto.  Thank you very much.

---

### Post by kirkcudbright on 2008-05-29
No success with bcm4306 on desktop computer

Computer is a pentium 4 at 3 gHz with 57.5 Gb of disk ( 55.4 free)

Wireless brand is 06:02.0 Network Controller Broadcom Corp bcm4306 802.11b/g rev (03)

Wireless chipset is 06:02.0 0280 : 14e4 4320 (rev 03)

ubuntu version 7.10

kernel 2.6.22-14-generic i686

no compile ndiswrapper

step 2f used

ndiswrapper -l gave 
bcwl5:driver installed
device (14e4:4340) present (alternative driver bcm43xx)

at first iwconfig said no wlan0 but i changed /etc/udev/rules.d/70-persistent-net.rules  to wlan0 instead of eht0

iwconfig then presented some data however the mode is 'managed' and looking at the various options in man i cannot find 'infrastructure' which is the mode i use in windows.  (it works in windows)

also if i set the essid etc then it reverts to the intial setting on start up.

help !!!  terry

---

### Post by Ayuthia on 2008-05-29
> **kirkcudbright said:**
> No success with bcm4306 on desktop computer

Computer is a pentium 4 at 3 gHz with 57.5 Gb of disk ( 55.4 free)

Wireless brand is 06:02.0 Network Controller Broadcom Corp bcm4306 802.11b/g rev (03)

Wireless chipset is 06:02.0 0280 : 14e4 4320 (rev 03)

ubuntu version 7.10

kernel 2.6.22-14-generic i686

no compile ndiswrapper

step 2f used

ndiswrapper -l gave 
bcwl5:driver installed
device (14e4:4340) present (alternative driver bcm43xx)

at first iwconfig said no wlan0 but i changed /etc/udev/rules.d/70-persistent-net.rules  to wlan0 instead of eht0

iwconfig then presented some data however the mode is 'managed' and looking at the various options in man i cannot find 'infrastructure' which is the mode i use in windows.  (it works in windows)

also if i set the essid etc then it reverts to the intial setting on start up.

help !!!  terry

You might want to check and be sure that you updated eth1 to wlan0 instead of eth0 (unless you don't have a wired connection).  Can you post your lshw -C network information?  It will help see the driver and hardware information.

---

### Post by tim_watson on 2008-05-29
Hi

Ran through this step by step guide but with no joy. I am running -or at least attempting to- a broadcom 4306 rev 03 and followed through with step 2d as indicated. when I run lshw -C network the wireless card is listed under *-network:0 with driver driver=b43-pci-bridge, however after listing my 3Com card which is not connected to my router,

*-network DISABLED
description wireless interface
physical id: 3
logical name: wlan0

I loaded the graphical wireless interface, this shows the installed driver bcmlw5 and hardware present yes

My blacklist file lists bcm43xx

What am I doing wrong?

ran rmmod b43 and b44, then ssb, now showing driver as ndiswrapper+bcml5 .... removed driver and reinstalled through the graphical interface and take me sideways with a spanner all seems to work... until rebooted.

Following reboot process of module removal has to be repeated. Can I blacklist b43, b44, and ssb?

---

### Post by jamesmorad on 2008-05-29
Ok I got this to work for barely even a day and now my connection suddenly stopped working. I was using it last night and browsing the net fine, then i turned off my computer.

I was having problems logging into gnome, so i had to login to gnome safemode and i turned off all the desktop modifications i set earlier, and then i could log back into gnome.

now the network manager detects my network, but it wont associate

---

### Post by Ayuthia on 2008-05-29
> **tim_watson said:**
> Hi

Ran through this step by step guide but with no joy. I am running -or at least attempting to- a broadcom 4306 rev 03 and followed through with step 2d as indicated. when I run lshw -C network the wireless card is listed under *-network:0 with driver driver=b43-pci-bridge, however after listing my 3Com card which is not connected to my router,

*-network DISABLED
description wireless interface
physical id: 3
logical name: wlan0

I loaded the graphical wireless interface, this shows the installed driver bcmlw5 and hardware present yes

My blacklist file lists bcm43xx

What am I doing wrong?

ran rmmod b43 and b44, then ssb, now showing driver as ndiswrapper+bcml5 .... removed driver and reinstalled through the graphical interface and take me sideways with a spanner all seems to work... until rebooted.

Following reboot process of module removal has to be repeated. Can I blacklist b43, b44, and ssb?

It depends.  The b44 driver is used for the wired internet connection but it only needed for the Broadcom BCM44xx series.  If your laptop does not have a Broadcom wired card, it might work.  If you are not sure, post your lshw -C network information and we can determine if you need it or not.  

The other option is to use version 0.3 of Making it Permanent from this [link]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-6a90c0182f807f29d1a2f55e8654ac07689542bb").

---

### Post by fiaf1 on 2008-05-30
Great stuff... simple, clean... thank you.

---

### Post by gspaulding on 2008-05-30
To Tim_Watson:
Use step 2f (worked for my 4306 rev 03) or 2b (worked for others).  Step 2d is not the right one.

---

### Post by uinarffraniu on 2008-05-30
Hi,

I've set it up following above steps, but no luck.

My wireless card is:

**Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)**

everything seems to work, but I cannot connect to wireeless, no matter wether encrypted or not. tried with **nm** and **wicd**.

now, when I **rmmod** **ndisvrapper** and **modprobe** it again in **dmesg** I get this:

[ 2698.918077] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[ 2698.918156] udev: renamed network interface wlan0 to eth1
[ 2698.973854] ADDRCONF(NETDEV_UP): eth1: link is not ready

don't know if it's relevant.

I remember I got an error installing **bcmwl5** but the installation continued. and

**ndisvrapper -l** gives me this output:

bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)

**ndiswrapper -v**:

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-17-generic/misc/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-17-generic SMP mod_unload 

**lsmod|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper -e b44**

ndiswrapper           193564  0 
ssb                    32260  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd


**lshw -C network**

 *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:02:d2:41
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5787m-v3.23 ip=192.168.1.11 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:1d:d9:69:04:08
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

in the last line it says 'link=no' so probably this is the problem. how do I fix this?

and:

**ls -l /etc/ndiswrapper/bcmwl5**

throws WAY to much stuff, think it's remainigs from all those attempts, but being a newbie I don't know what to delete

**PLEASE HELP**

---

### Post by kirkcudbright on 2008-05-30
> **Ayuthia said:**
> You might want to check and be sure that you updated eth1 to wlan0 instead of eth0 (unless you don't have a wired connection).  Can you post your lshw -C network information?  It will help see the driver and hardware information.

terry@terry-desktop:/etc/udev/rules.d$ sudo lshw -C network  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wlan0
       version: 03
       serial: 00:0f:66:74:a4:64
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+The Linksys Group, Inc.,07/ latency=32 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:06:03.0
       logical name: eth0
       version: 00
       serial: 00:50:bf:2f:7d:27
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=192.168.1.3 latency=0 module=ne2k_pci multicast=yes


yes i have a wired connection

copy of 70-persistent-net.rules

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8029 (ne2k-pci)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:50:bf:2f:7d:27", NAME="eth0"

# PCI device 0x14e4:0x4320 (bcm43xx)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:0f:66:74:a4:64", NAME="wlan0"

thanks terry

---

### Post by travislucas on 2008-05-30
Try this driver set, I've got the same broadcom set in my compaq c500 and this setup seemed to work for me... hope it help's...

1.) Removing b43-fwcutter

Sudo aptitude remove b43-fwcutter

2.) Getting Ndiswrapper working in Hardy

sudo gedit /etc/init.d/wirelessfix.sh

and paste this:

Quote:
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
into the file. Close and save it.

Next, run this:

Code:

cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

and finally, this:

Code:

sudo update-rc.d wirelessfix.sh defaults

3.) Getting the Newst Ndiswrapper

sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

4.) Getting the right broadcom driver

wget [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)

or just open your web browser and copy and paste 

[ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe) 

in the address window and save to the desktop when asked.

5.) Getting ride of bcm43xx

sudo rmmod bcm43xx
sudo modprobe ndiswrapper

6.) Extracting .exe
unzip -a sp33008.exe (or if you saved it to your desktop just navigate to your Desktop directory and apply extract command.)

Once unziped Enter the following: (make sure your still in the Desktop directory while applying these command)

sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo echo ndiswrapper >> /etc/modules

Note you don't need to blacklist your bcm43xx because you did the workaround with Ndiswrapper for hardy!

Restart and things should be working fine for you!

---

### Post by freackout on 2008-05-30
> **biodiesel-bri said:**
> Thanks for this, I got it all to work after trying many other methods.  I wasn't able to see wireless until I issued this command:

```
sudo iwconfig wlan0
```

i tried a step for 4318 but it was 7.10, then put in the hardy as upgrade worked ok but now trying for hardy without the 7.10 as other things have settings to consider...wish me luck

---

### Post by moose4204l on 2008-05-30
so this isnt working for me, i tried a few times already and i still get locked up with two boxes left to load for the ubuntu load bar on start up. basically i have a bcm4309 and i followed all instructions. i wet from this too the other page and followed 2a, then i popped out back to here and finished the step 4 and on. everytime though i get stuck at the load screen. i have to load in under the root command shell thing bye pressing esc and removing the init.d file that the directions say to create. what should i do.

i have a dell inspiron 5100 bcm4309

---

### Post by Ayuthia on 2008-05-31
> **uinarffraniu said:**
> 
**lsmod|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper -e b44**

ndiswrapper           193564  0 
ssb                    32260  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd

ssb is still there.  You will want to remove it.  Just to play it safe, try the following:
```
sudo modprobe -r b43 b44 ssb
sudo modprobe ndiswrapper
```That should be able to bring it up.  If not, we might try to change eth1 back to wlan0 to see if it does anything.

---

### Post by Ayuthia on 2008-05-31
> **kirkcudbright said:**
> 
iwconfig then presented some data however the mode is 'managed' and looking at the various options in man i cannot find 'infrastructure' which is the mode i use in windows.  (it works in windows)

also if i set the essid etc then it reverts to the intial setting on start up.Are you saying that you are able to connect but you cannot connect on reboot?

---

### Post by Ayuthia on 2008-05-31
> **moose4204l said:**
> so this isnt working for me, i tried a few times already and i still get locked up with two boxes left to load for the ubuntu load bar on start up. basically i have a bcm4309 and i followed all instructions. i wet from this too the other page and followed 2a, then i popped out back to here and finished the step 4 and on. everytime though i get stuck at the load screen. i have to load in under the root command shell thing bye pressing esc and removing the init.d file that the directions say to create. what should i do.

i have a dell inspiron 5100 bcm4309
Can you post your 'lshw -C network' information and the init.d file?  The init.d file sounds like it has something that the system doesn't like.

---

### Post by uinarffraniu on 2008-05-31
> ssb is still there. You will want to remove it. Just to play it safe, try the following:
Code:

sudo modprobe -r b43 b44 ssb
sudo modprobe ndiswrapper

That should be able to bring it up. If not, we might try to change eth1 back to wlan0 to see if it does anything

Thanks for an answer. Removed ssb (I should remove it from /etc/modules, rigt?) but no change.

Holly cow. It was a MAC addres filter on my router, everything seems to work just fine now.

Thanks a lot for advice, Ayuthia, and patience. I'm so glad it works.

---

### Post by moose4204l on 2008-05-31
lshw -C network
 *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: <took out>
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: <took out>
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

----------------------------------------------------------------------------------------------------

/etc/init.d$ ls
acpid              hotkey-setup                     rcS
acpi-support       hwclockfirst.sh                  readahead
alsa-utils         hwclock.sh                       readahead-desktop
anacron            keyboard-setup                   README
apmd               killprocs                        reboot
apparmor           klogd                            rmnologin
apport             laptop-mode                      rsync
atd                linux-restricted-modules-common  screen-cleanup
avahi-daemon       loopback                         sendsigs
bluetooth          module-init-tools                single
bootclean          mountall-bootclean.sh            skeleton
bootlogd           mountall.sh                      stop-bootlogd
bootmisc.sh        mountdevsubfs.sh                 stop-bootlogd-single
brltty             mountkernfs.sh                   stop-readahead
checkfs.sh         mountnfs-bootclean.sh            sysklogd
checkroot.sh       mountoverflowtmp                 udev
console-screen.sh  mtab.sh                          udev-finish
console-setup      networking                       ufw
cron               nvidia-kernel                    umountfs
cupsys             pcmciautils                      umountnfs.sh
dbus               policykit                        umountroot
dhcdbd             powernowd                        urandom
dns-clean          powernowd.early                  usplash
gdm                pppd-dns                         vbesave
glibc.sh           procps                           waitnfs.sh
hal                pulseaudio                       wpa-ifupdown
halt               rc                               x11-common
hostname.sh        rc.local                         xserver-xorg-input-wacom

----------
i deleted the wirelessfix.sh

---

### Post by kirkcudbright on 2008-05-31
> **Ayuthia said:**
> Are you saying that you are able to connect but you cannot connect on reboot?

hello again

no cannot connect at all and settings in iwconfig get reset on boot.

thanks terry

---

### Post by moose4204l on 2008-05-31
bump

---

### Post by speedy1906 on 2008-05-31
This thread is great.  I followed the instructions for my HP Pavilion dv2000 with my Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02).  Just follow the instructions line by line!  less than an hour for a novice!  Now on to barrel!

Peace!

---

### Post by Ayuthia on 2008-05-31
> **moose4204l said:**
> lshw -C network
 *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: <took out>
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: <took out>
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


Let's try this version.  It comes from this [link]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-6a90c0182f807f29d1a2f55e8654ac07689542bb"):
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```
If this does not work, do you know if you are able to get the wireless to work without the script?

---

### Post by auquista on 2008-05-31
Thanks a lot, it worked for me also. It took two tries (and a fair share of frustration), with fully uninstalling everything and trying it again. I have a Compaq Presario V500 amd64, bcm4318. I am finally free from the cables.
:popcorn:

---

### Post by Lori Whitty on 2008-06-03
GOD BLESS YOU!!!!!!!!!!!!   You have NO idea how many "fixes" I've Googled and tried to no avail.  THANK YOU SO MUCH!!!!  Your instructions were very explicit and I had no trouble following them.  I am a new ubuntu user and now I'm a VERY happy one!

(In case anyone is wondering, I have an HP dv6500 laptop with a BCM94311mcg mini pci rev 02 that this fix worked on.)

---

### Post by rksingh54 on 2008-06-03
I have installed WLAN with your step by step process on three laptops, HP Pavillion dv6225US, zv6203cl Compaq Pressario F700, all with Broadcom WLAN card. 

Thank you for the article without which my notebooks were actually paper weight in my home office.

I also must say, I would not buy another HP or recommned an HP to any of my freind and/or foe becaue their technical service leaves a world to be desired.

RKS

---

### Post by Tizzy on 2008-06-03
This has just been breaking my pc over and over... I have a broadcom BCM4306 card, ver 03, and have been following step 2b, as other users with the same card have said.
As soon as I get to the
```
sudo modprobe ndiswrapper
```

part, when I issue the command, I get a message saying

```
killed
```

then, if I dare going on, when i restart the PC the system locks up, therefore rendering me unable to boot ubuntu. Any ideas why?

My specs:

AMD64 6000+ processor
MSI k9a platinum motherboard
ATi HD 2900XT videocard
4GB DDR2 800 PC 6400 memory (4 1gb sticks)
500GB WD SATA hard drive
1 DVD/CD IDE reader
1 DVD/CD IDE burner
1 SATA Blu-Ray reader, DVD/CD Burner [Have this deactivated because it's been giving me issues with Ubuntu]

Can anyone help me? It's driving me crazy :s

---

### Post by FrenchyFungus on 2008-06-03
I have what i think is a weird problem.

I cannot select WEP as an option in the Enter Passphrase window, only WPA and LEAP.

But my router uses WEP, so what do I do?

---

### Post by vigyani on 2008-06-04
I have been running Ubuntu 7.10 on HP NX6310 Laptop (Wireless card Boradcom  BCM4312) and using Ndiswrapper driver and it was working fine.

Upgraded to Ubuntu 8.04 and wireless card was not detected.

I rebooted the system using Kernel 2.6.22-14, wireless worked. If system was booted using Kernel 2.6.22-16 or later wireless card was detected.
Today (June 4th 2008), I updated the Kernel to 2.6.24-18 and again wireless did not work.

Since I was using Ndiswrapper earlier I used the guide on page #1 from Step 4 to 9.

> [INDENT]Step 4 (run in terminal)

sudo aptitude remove b43-fwcutter

Step 5 (run in terminal)

sudo gedit /etc/init.d/wirelessfix.sh

Step 6

Paste the followings in the opened file(wirelessfix.sh)and make sure you save it before continuing Step 7

#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

Step 7 (run in terminal)

Run this :

cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

Step 8 (run in terminal)

finally run this:

sudo update-rc.d wirelessfix.sh defaults

Step 9

Restart your machine and enjoy the freedom from those wires....

[/INDENT]

Rebooted in Kernel 2.6.24.-18 and Wireless works fine. I am writing it using wireless.
Thanks a lot.
with regards
Vig.:)

---

### Post by LeGollemux on 2008-06-04
Just something that worked for me. Perhaps very obvious to others. But until I used the exact driver that came with my card, none of the above worked for me. I tried various suggested downloads, but until I found the disk that came with my card I had no joy. 

Card used, Asus WL-138G V2. Chipset BCM4318 (rev 02)

oh, and don't be shy to use the "/etc/init.d/networking restart" command either. :)

---

### Post by maffix on 2008-06-04
"""""To Alex_Kent_18"""""""
Latest news from southern Italy!!!!!!!!
Thank you very much for your wonderful advice,my wireless network goes like a bomb. My pc is a Compaq nc4200 with Broadcom4318 (rev 02) installed, even if the driver reported to your post were for another wireless card, everything worked magically and more better than the official driver for 4318'HP. The signal level is much more intense than before. What do you think about this? It's the same thing?
Thank you once again,and I hope that you have much luck in your life.:guitar:

---

### Post by hangar_18 on 2008-06-06
thanks a lot, wirelles was only non-functional thing on my HP pavilion dv6000 with hardy :P

---

### Post by rchardblvd on 2008-06-06
Hello everyone, I'm new to Ubuntu and I've been trying to get my wireless to work with this guide, but it still doesn't seem to be working. I followed step 1, 2e, and 3. I can see my wireless SSID but I can't connect to it. I also noticed that the guide said under the configuration line it should say 'module=ndiswrapper' as opposed to 'module=ssb' but mine shows 'module=wl'. I'm not sure what this all means though. 

**lspci -n | grep '14e4:43'**
02:00.0 0280: 14e4:4315 (rev 01)

**lshw -C network**
  *-network               
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:10:60:28
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11


This is for an HP 2133 Mininote. Please let me know if there is anything else that might be useful in helping to get my wireless up and running. Thanks!

---

### Post by tooloose on 2008-06-07
Thank you.  Now, if I can learn to read what is written.

tooloose

---

### Post by newton64 on 2008-06-07
Ahem. "Me too."

Thanks a ton, this worked flawlessly.

---

### Post by Misha__ on 2008-06-07
Did anything step by step. It works. In principle.
However, I wonder if anyone succeed in 
1) running this 4318 in master mode? Because it does not want to switch:
```
$ sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

```
For b43 driver the same. In M$ it can be configured as AP. 
2) make it work in ad-hoc mode? For me there is no ping. I found a couple of threads here where people complain about the same problem. The question is: has anyone who had this problem successfully solved it?

---

### Post by rellis3 on 2008-06-09
Thank you very much for this setup information. I was about to give up. It works beautifully.

Raney Ellis (New Xubuntu user)

---

### Post by whorush on 2008-06-09
i'm really stuck.  thanks in advance!  i'm running hardy 8,04 on amd64.

using this chipset:    (output of lspci -nn)
```
3:07.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```

my card should work, the **[COLOR="Green"]ASUS WL-138g V2[/COLOR]** is #65 in this list, [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/)

i followed alex kent's instructions in the first post of this thread.  first i tried it with 2a, then i read someones post who had my card and said he just used the winxp asus drivers here... [http://support.asus.com/download/download.aspx?SLanguage=en-us&model=WL-138g%20V2](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=WL-138g%20V2).  so i think i successfully removed it and installed the asus drivers and then repeated steps 3-9.

i restart and its supposed to work?  but nothing happens.  where can i find the networks?  ifconfig finds eth0 and lo but nothing else.  i dont think its working at all?  how will i know if its working?  will i be able to see the networks in network manager?

maybe the problem is i'm using amd64?  maybe i should get 1.53 of ndiswrapper from the site instead of 1.50 from the ubuntu repositories?

thanks so much!!
bradley

---

### Post by Ayuthia on 2008-06-09
> **whorush said:**
> i'm really stuck.  thanks in advance!  i'm running hardy 8,04 on amd64.

using this chipset:    (output of lspci -nn)
```
3:07.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```

my card should work, the **[COLOR="Green"]ASUS WL-138g V2[/COLOR]** is #65 in this list, [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/)

i followed alex kent's instructions in the first post of this thread.  first i tried it with 2a, then i read someones post who had my card and said he just used the winxp asus drivers here... [http://support.asus.com/download/download.aspx?SLanguage=en-us&model=WL-138g%20V2](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=WL-138g%20V2).  so i think i successfully removed it and installed the asus drivers and then repeated steps 3-9.

i restart and its supposed to work?  but nothing happens.  where can i find the networks?  ifconfig finds eth0 and lo but nothing else.  i dont think its working at all?  how will i know if its working?  will i be able to see the networks in network manager?

maybe the problem is i'm using amd64?  maybe i should get 1.53 of ndiswrapper from the site instead of 1.50 from the ubuntu repositories?

thanks so much!!
bradley

You might first check out ndiswrapper -l from the Terminal.  It should show that the hardware is present.  You should also check ndiswrapper -v.  It will give you the version number of ndiswrapper and tell you if it has any errors.  You can also check lshw -C network.  It will tell you driver information for the wireless card.  It should say that it is using ndiswrapper + bcmwl5.  It should also give you a version number and possibly some information about the driver being wrapped.  If you are not sure of any of this, please post the information to:
```
ndiswrapper -l
ndiswrapper -v
lshw -C network
```

---

### Post by whorush on 2008-06-09
> **Ayuthia said:**
> 
```
ndiswrapper -l
ndiswrapper -v
lshw -C network
```

here are the commands:

```
daniels@daniels-desktop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: bcm43xx)
```

```
daniels@daniels-desktop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-18-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-18-generic SMP mod_unload
```

```
daniels@daniels-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:55:5f:b3
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.105 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:03:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb

```

---

### Post by Ayuthia on 2008-06-09
> **whorush said:**
> here are the commands:

```
daniels@daniels-desktop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: bcm43xx)
```

```
daniels@daniels-desktop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-18-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-18-generic SMP mod_unload
```

```
daniels@daniels-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:55:5f:b3
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.105 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:03:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb

```

Let's go ahead and try the following:
```
sudo modprobe -r bcm43xx b43 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist scan
```
I am seeing that the alternate driver is showing bcm43xx instead of ssb.  So to play it safe, we will remove the module.  Then lshw -C network is showing that it is trying to use the b43 driver so I am thinking that either b43 or ssb is still there.

---

### Post by whorush on 2008-06-09
> **Ayuthia said:**
> Let's go ahead and try the following:
```
sudo modprobe -r bcm43xx b43 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist scan
```
I am seeing that the alternate driver is showing bcm43xx instead of ssb.  So to play it safe, we will remove the module.  Then lshw -C network is showing that it is trying to use the b43 driver so I am thinking that either b43 or ssb is still there.

thanks!  here you go.

```
daniels@daniels-desktop:~$ sudo modprobe -r bcm43xx b43 ssb ndiswrapper
FATAL: Module ssb is in use.
```

this one returns nothing...
```
daniels@daniels-desktop:~$ sudo modprobe ndiswrapper
```

```
daniels@daniels-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

---

### Post by Ayuthia on 2008-06-09
> **whorush said:**
> thanks!  here you go.

```
daniels@daniels-desktop:~$ sudo modprobe -r bcm43xx b43 ssb ndiswrapper
FATAL: Module ssb is in use.
```

Forgot that this guide has you load b44.  Try:
```
sudo modprobe -r bcm43xx b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist scan
```

---

### Post by whorush on 2008-06-09
> **Ayuthia said:**
> Forgot that this guide has you load b44.  Try:
```
sudo modprobe -r bcm43xx b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist scan
```

the first two ran without output, here is the last one.

```
daniels@daniels-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

---

### Post by Ayuthia on 2008-06-09
> **whorush said:**
> the first two ran without output, here is the last one.

```
daniels@daniels-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```
Can you provide the information for:
dmesg|grep ndiswrapper
For some reason your wireless is not switching on when you load the ndiswrapper module.

---

### Post by whorush on 2008-06-09
> **Ayuthia said:**
> Can you provide the information for:
dmesg|grep ndiswrapper
For some reason your wireless is not switching on when you load the ndiswrapper module.

```
daniels@daniels-desktop:~$ sudo dmesg|grep ndiswrapper
[   37.398386] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   37.683696] usbcore: registered new interface driver ndiswrapper
[   43.481476] usbcore: deregistering interface driver ndiswrapper
[   43.496792] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   43.536579] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   43.536587] ndiswrapper (load_sys_files:210): couldn't prepare driver 'bcmwl5'
[   43.537345] ndiswrapper (load_wrap_driver:112): couldn't load driver bcmwl5; check system log for messages from 'loadndisdriver'
[   43.537405] usbcore: registered new interface driver ndiswrapper
[ 2729.273152] usbcore: deregistering interface driver ndiswrapper
[ 2729.273347] ndiswrapper (ntoskernel_exit:2708): object ffff81006cf16630(2) was not freed, freeing it now
[ 2732.695168] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 2732.720421] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 2732.720432] ndiswrapper (load_sys_files:210): couldn't prepare driver 'bcmwl5'
[ 2732.721165] ndiswrapper (load_wrap_driver:112): couldn't load driver bcmwl5; check system log for messages from 'loadndisdriver'
[ 2732.721244] usbcore: registered new interface driver ndiswrapper
```

---

### Post by Ayuthia on 2008-06-10
> **whorush said:**
> [CODE]daniels@daniels-desktop:~$ sudo dmesg|grep ndiswrapper
[   43.536579] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B

You need to find a new magician!!!!  Actually, if you did not catch it, the driver that you are using is a 32-bit bcmwl5 driver.  You need to see if you can find a 64-bit bcmwl5 driver.

---

### Post by whorush on 2008-06-10
huh.  i think i should reinstall with 32 bit.  64 bits just seems like too much of a pain in the ***!!!!

thanks for being my magician, i think i can pull this off tomorrow, otherwise, i'll be back :-).

---

### Post by whorush on 2008-06-10
> **FrenchyFungus said:**
> I have what i think is a weird problem.

I cannot select WEP as an option in the Enter Passphrase window, only WPA and LEAP.

But my router uses WEP, so what do I do?

i just went through this.  just say none, then it will ask you for WEP.  i think :-)

---

### Post by whorush on 2008-06-10
great, i switched to 32 bit ubuntu (from 64) and now this howto works, almost perfectly!!!!

problem is i can connect to my network when the security is off, but not when WEP is on?

thanks!
bradley

---

### Post by sultanoswing on 2008-06-10
Step 1) Buy an intel card

The End.

:p

---

### Post by Ayuthia on 2008-06-10
> **whorush said:**
> great, i switched to 32 bit ubuntu (from 64) and now this howto works, almost perfectly!!!!

problem is i can connect to my network when the security is off, but not when WEP is on?

thanks!
bradley
You could try using wicd or wifiradar.  They are a replacement for Network Manager.  They seem to work better for WEP.

---

### Post by Kevbert on 2008-06-10
This method works well for me with a Broadcomm BCM4306 Rev 03 and Kubuntu 8.04 (method 2b in Step 2).  The only difference I had was using nano instead of gedit when creating the script.
Excellent Howto!!!

---

### Post by funkmonkey on 2008-06-11
Total newb here.  I installed 8.04 a couple weeks back and have been struggling to get my wireless card up and running with various howtos from around the internet.  I got a lot of experience with the command line, which was the main reason for installing a Linux OS in the first place, but nothing worked until now.  I have the luxury of a spare machine, so I did a clean install (I have no idea what kind of mess I had made due to the failed attempts), and thanks to this fantastic howto, things are going great.

I'm using a Dell Inspiron 8500 and have a BCM4306 v1.

---

### Post by whorush on 2008-06-11
Ayuthia, thanks!

this method worked for me.

1) i needed to use 32 bit ubuntu, 64 didnt work because the drivers i needed were 32 only.

2) ndiswrapper seemed to work much better, faster, better reception, etc. than b43-fwcutter.  and the instructions in this thread worked, except that i used the windows xp asus drivers for my asus WL-138g v2 card.

3) then i found network manager a bit annoying, asking me for a key everytime i logged in, so i used wicd, now i startup and it connects automatically.

summary) 32 bit ubuntu, this howto with asus winxp drivers, then wicd.

any questions, private message me.

thanks again!
bradley

---

### Post by robrown on 2008-06-15
> **rchardblvd said:**
> Hello everyone, I'm new to Ubuntu and I've been trying to get my wireless to work with this guide, but it still doesn't seem to be working. I followed step 1, 2e, and 3. I can see my wireless SSID but I can't connect to it. I also noticed that the guide said under the configuration line it should say 'module=ndiswrapper' as opposed to 'module=ssb' but mine shows 'module=wl'. I'm not sure what this all means though. 

**lspci -n | grep '14e4:43'**
02:00.0 0280: 14e4:4315 (rev 01)

**lshw -C network**
  *-network               
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:10:60:28
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11


This is for an HP 2133 Mininote. Please let me know if there is anything else that might be useful in helping to get my wireless up and running. Thanks!

I have the same issue with the module=wl

Running 8.04 on Inspiron 1525 BCM4310 ver 01

Also, when I go to System>Administration>Windows Wireless Drivers it says the driver bcmwl5 is loaded, but no hardware detected.

I too am sort of new to ubuntu, but I've been learning a lot in the last couple of months, so any help is greatly appreciated.

---

### Post by Ayuthia on 2008-06-15
> **robrown said:**
> I have the same issue with the module=wl

Running 8.04 on Inspiron 1525 BCM4310 ver 01

Also, when I go to System>Administration>Windows Wireless Drivers it says the driver bcmwl5 is loaded, but no hardware detected.

I too am sort of new to ubuntu, but I've been learning a lot in the last couple of months, so any help is greatly appreciated.
There is a special driver made for your card.  From what I read, you will have to install linux-restricted-modules.  I think that the new driver is in kernel 2.6.24-18 or higher.  You will have to blacklist the b43, ndiswrapper, and bcm43xx driver to get it to work.

I have not seen anyone try it yet (I don't have the card, but I have a good idea about how it needs to be configured), but if you want to do this, please open up another thread with the topic of BCM4310 and wl driver (so that others with your card can see what needs to be done).  Please PM me with the thread so that I can find it.  If you don't want to create the thread, I might create one with some kind of guide to try.  

If you want to try it out right now, download linux-restricted-modules and make sure that your kernel is greater than 2.6.24-18 (check this by typing uname -r in the Terminal).  Then try the following:
```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
sudo depmod -ae
sudo modprobe wl
sudo ifconfig wlan0 up
sudo iwlist scan
```
Hopefully you will be able to see some wireless access points.

Here is also a link for your card using ndiswrapper.  This one seems to help those that have had similar problems as you with your chipset:
[http://ubuntuforums.org/showthread.php?t=786397](http://ubuntuforums.org/showthread.php?t=786397)

---

### Post by robrown on 2008-06-15
> **Ayuthia said:**
> There is a special driver made for your card.  From what I read, you will have to install linux-restricted-modules.  I think that the new driver is in kernel 2.6.24-18 or higher.  You will have to blacklist the b43, ndiswrapper, and bcm43xx driver to get it to work.

I have not seen anyone try it yet (I don't have the card, but I have a good idea about how it needs to be configured), but if you want to do this, please open up another thread with the topic of BCM4310 and wl driver (so that others with your card can see what needs to be done).  Please PM me with the thread so that I can find it.  If you don't want to create the thread, I might create one with some kind of guide to try.  

If you want to try it out right now, download linux-restricted-modules and make sure that your kernel is greater than 2.6.24-18 (check this by typing uname -r in the Terminal).  Then try the following:
```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
sudo depmod -ae
sudo modprobe wl
sudo ifconfig wlan0 up
sudo iwlist scan
```
Hopefully you will be able to see some wireless access points.

Here is also a link for your card using ndiswrapper.  This one seems to help those that have had similar problems as you with your chipset:
[http://ubuntuforums.org/showthread.php?t=786397](http://ubuntuforums.org/showthread.php?t=786397)

Thanks for you help, that makes a lot of sense.  I checked it, and my kernel is 2.6.24-16 generic.

I downloaded and installed linux-restricted-modules, but when I tried to run your code there the first command gave me an error:  FATAL: Module ssb is in use.

I saw that thread you linked already, that's how I got here, heh.  There's a link in that thread to this thread...

By the way, I can see the access points, I just can't connect to any of them

---

### Post by moose4204l on 2008-06-17
*******************

ok i finally got my wireless working.

 lspci | grep BCM
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)


 lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:38:81:f6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:16:7a:a9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.6 multicast=yes wireless=IEEE 802.11g


I followed everything in the instructions. I believe i tried a bunch of different step 2's. i know i did 2a and 2f, i just dont know which one was last. if there is anyway to figure out which one i did lemme know so i can post it for people. when i rebooted, the wirelessfix.sh didnt allow for my laptop to boot up so i rooted in with the escape key during load up and removed it. i was also seeing an error message when i booted up right before the login screen so i checked my boot log and went to the [URL]("http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy") they suggested. then i rebooted and now i have wireless!!!

---

### Post by s1337m on 2008-06-17
I have a BCM43XX and have tried a lot of guides (including this) with no luck!  I can detect networks but cannot connect to them, if someone could please help I would much appreciate it!

sean@sean-laptop:~$ lspci | grep BCM
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)
sean@sean-laptop:~$ 
sean@sean-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:3d:0d:69
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:4a:16:69
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.101 latency=64 module=ssb multicast=yes
sean@sean-laptop:~$ 
sean@sean-laptop:~$ uname -r
2.6.24-19-generic
sean@sean-laptop:~$

---

### Post by pwhitted on 2008-06-18
I have an HP zd7010 with the Broadcom 4306 rel2 card, running Hardy with all the latest updates. I've been able to get it to work using the nidswrapper, but it only works in ROAM mode. If I use the network applet and configure the wlan0 connection with my ESSID and WEP key, it doesn't connect. But if I set the network applet to enable roaming for wlan0, then configure other wireless networks, it connects just fine. The problem with this is that every time the computer reboots or comes out of sleep mode, I have to reenter the ESSID and WEP key. That's fine for me, but my wife uses this laptop, too, and she can't handle having to do that every time she gets on the network. How can I get this configuration to "stick" so I don't have to manually enter it each time? Or get the card to work when it's not in roaming mode?

---

### Post by Big_PhiL on 2008-06-18
Hey Guys, bear with me cause I'm a newb. I have a Broadcom 4318 wireless card in an acer cpu. Installed Hardy 8.04 last week, and have been having problems with my wireless ever since to the point where if I download an update, its gone. I have followed all the steps in [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)
and it worked, but with each update, its gone. Now I can't find my network at all. here's my lshw -C network:

 *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:a9:ea:2f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.2.11 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 02
       serial: 00:0e:9b:d3:a8:86
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

and my iwconfig:
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and ifconfig: wlan0     Link encap:Ethernet  HWaddr 00:0e:9b:d3:a8:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Memory:e2000000-e2002000 

I would really like some help on this guys. I've been a 13 year windows user (I'm 26, so since '95) and like Ubuntu, but if it means I have wireless, I have to give in, please help.

---

### Post by Ayuthia on 2008-06-18
> **Big_PhiL said:**
> Hey Guys, bear with me cause I'm a newb. I have a Broadcom 4318 wireless card in an acer cpu. Installed Hardy 8.04 last week, and have been having problems with my wireless ever since to the point where if I download an update, its gone. I have followed all the steps in [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)
and it worked, but with each update, its gone. Now I can't find my network at all. here's my lshw -C network:

 *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:a9:ea:2f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.2.11 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 02
       serial: 00:0e:9b:d3:a8:86
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

and my iwconfig:
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and ifconfig: wlan0     Link encap:Ethernet  HWaddr 00:0e:9b:d3:a8:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Memory:e2000000-e2002000 

I would really like some help on this guys. I've been a 13 year windows user (I'm 26, so since '95) and like Ubuntu, but if it means I have wireless, I have to give in, please help.

When it disconnects, can you open up a terminal and type dmesg.  If you are not for sure do the following:
```
dmesg>~/Desktop/dmesgforum.txt
```
The file will be created in your desktop called dmesgforum.txt.  Please attach the document to your post.  The message will most likely tell you what happened.

Can you also tell us which driver you used?  Also, please post the results of the following from the Terminal:
```
lspci -nnm
```I am seeing that there are differences in the 4318 card and I am trying to see the pattern so that the documentation can be updated.

---

### Post by MichaëlVD on 2008-06-21
Thanks! The guide in the first post of this thread worked for my intel imac.

---

### Post by deathsushi on 2008-06-22
Hello,

I was having a problem with the native broadcom drivers, in that I could occasionally see my network, but at a very weak signal strength, and usually would have the connection dropped.

I installed ndiswrapper after reading about the problem online, and followed this how-to.  Ndiswrapper definitely seems to work better with the card (Broadcom 4318), as I can now see many more present networks, and the strength of mine in particular is much stronger.

HOWEVER, I cannot actually connect to any of the detected networks.  Everytime I try to, the two little balls in the nm-applet swirl for a while before giving up.

Can anyone help me figure this out?  Let me know what commands I should run and post and I'll get'er going.

Thanks in advance!

--Adam

---

### Post by huntis619 on 2008-06-23
I know how you feel. I'm having the same problem. balls swirl and then stop argghhhhhhh. Please HELP.

---

### Post by Ayuthia on 2008-06-23
huntis and deathsushi-
Have you tried installing another network manager (wicd or wifiradar)?

The 4318 and the 4306 rev 02 cards are having the hardest times connecting at this point.  I have not seen what is causing it.

---

### Post by Apipote on 2008-06-23
Hello, sorry for my bad English

I use hardy 32 bits( full updated ), but my broadcom 4311 rev 2 can´t works with the last native driver. I have a Compaq f566la ( amd turion 64 bits )

The light is blue, but 0% activity. I can see all conections, but nothing happen.

What can i do ??

Best regards.

---

### Post by Momof9Blessings on 2008-06-23
For the 1st time in 3 weeks - since getting ubuntu... I finally have wireless!!! WOOHOO!!

In one line - step 2.... you need to manually copy the link location - and write in.... "wget"  or it will have "..." in the url....

THANK YOU!!!  Mom

---

### Post by Moozikku25 on 2008-06-24
I need help.  I did everything but I don't know if I had messed up a step. I have a 4318 (Rev 02) broadcom wireless card on a dell inspiron 1300/b130.  I restarted and now it seems that my card isn't even recognizable after doing those steps.:confused:

---

### Post by Ayuthia on 2008-06-24
> **Apipote said:**
> Hello, sorry for my bad English

I use hardy 32 bits( full updated ), but my broadcom 4311 rev 2 can´t works with the last native driver. I have a Compaq f566la ( amd turion 64 bits )

The light is blue, but 0% activity. I can see all conections, but nothing happen.

What can i do ??

Best regards.

Did you try using the ndiswrapper steps in the first post of this thread?  If so, can you open a terminal and type:
```
lshw -C network
```

---

### Post by Ayuthia on 2008-06-24
> **Moozikku25 said:**
> I need help.  I did everything but I don't know if I had messed up a step. I have a 4318 (Rev 02) broadcom wireless card on a dell inspiron 1300/b130.  I restarted and now it seems that my card isn't even recognizable after doing those steps.:confused:
Can you post the results of the following from the Terminal:
```
cat /etc/modules|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper
cat /etc/init.d/wirelessfix.sh
```

---

### Post by Moozikku25 on 2008-06-24
moozikku25@B130:~$ cat /etc/modules|grep -i -e bcm43xx -e ssb -e ndiswrapper
ndiswrapper
ndiswrapper
moozikku25@B130:~$ cat /etc/init.d/wirelessfix.sh
#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

---

### Post by Apipote on 2008-06-24
> Did you try using the ndiswrapper steps in the first post of this thread?

Mmmmmm...no, but i would like use native drivers.

Can you help me?

Tnx

---

### Post by Moozikku25 on 2008-06-24
Sorry to bump, but I think some of these broadcom thread should either be stickied or merged together.

Ayuthia, I have posted up what you have told me so far.

---

### Post by Ayuthia on 2008-06-24
> **Moozikku25 said:**
> Sorry to bump, but I think some of these broadcom thread should either be stickied or merged together.

Ayuthia, I have posted up what you have told me so far.

That information looks fine.  Can you post the results of:
```
lshw -C network
ndiswrapper -l
```
The first will tell us what driver your card is using and the second will tell us if the driver was wrapped ok.

---

### Post by Ayuthia on 2008-06-24
> **Apipote said:**
> Mmmmmm...no, but i would like use native drivers.

Can you help me?

Tnx
I thought that I read that your card works with 2.6.24-18, but I have not heard whether it works with 2.6.24-19.  As for any other kernel version in Hardy, I have not seen it work at all.  Can you check your kernel version in the Terminal:
```
uname -r
```

---

### Post by Moozikku25 on 2008-06-25
Here you go Ayuthia:
moozikku25@B130:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:a9:f9:f2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=10.0.0.2 latency=64 module=ssb multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:8e:53:89
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
moozikku25@B130:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)

---

### Post by xXOtherPeoplesWasteXx on 2008-06-25
Went thru countless how-tos and this is the one that works....for now



**Thanks alot**

---

### Post by donjuanmarxist on 2008-06-25
Post 1. What it be like? I have a E1405 Dell inspiron Dell 1500 Draft802.11n WLAN minicard. I have a dual boot but unfortunately its 2 copies of XP. I'm trying to get the wireless working; its all i have on this computer; before i install so I'm using the cd. NO encryption

I have what I think are the right files from the dell R151519 driver. I try to add bcmwl5 in Ubuntu but it says not a valid driver. What to do? When i follow the guide it says make check system > preferences> hardware information. There is no hardware information listing. 

Can i easily erase ubuntu if i download it to windows or will it leave all kinds of hidden files behind?

---

### Post by Apipote on 2008-06-25
> I thought that I read that your card works with 2.6.24-18, but I have not heard whether it works with 2.6.24-19. As for any other kernel version in Hardy, I have not seen it work at all. Can you check your kernel version in the Terminal:

I have a 2.6.24-19, but, don´t works. I can see my acces point , but 0% activity.

Ethernet...Ok.

How can i do?

---

### Post by Ayuthia on 2008-06-25
> **Apipote said:**
> I have a 2.6.24-19, but, don´t works. I can see my acces point , but 0% activity.

Ethernet...Ok.

How can i do?

You might try and see if you can go back to 2.6.24-18 and see if it works.  By any chance, do you have that kernel?

---

### Post by Ayuthia on 2008-06-25
> **Moozikku25 said:**
> Here you go Ayuthia:
moozikku25@B130:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:a9:f9:f2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=10.0.0.2 latency=64 module=ssb multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:8e:53:89
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
moozikku25@B130:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)
Can you do the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
sudo modprobe b44
dmesg|grep ndiswrapper
```
The first few commands are removing the conflicting modules and reloading ndiswrapper for your wireless and b44 for your wired connection.  The last part is going to see if ndiswrapper is coming up with any error messages.  It looks like the card wants to use the wireless card, but it is currently disabled.  If you are not already, you should unplug the wired connection so that it does not interfere when you are trying the wireless connection.

---

### Post by Moozikku25 on 2008-06-25
Okay I have done the steps without plugging in the wired internet.  Unfortunately, my there was no light that turned on for the internet card, nor was the enabled wireless was working either.

Here was the result I saved into OpenOffice before I restarted, and inputted the commands you gave me:

moozikku25@B130:~$ sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx 
[sudo] password for moozikku25: 
moozikku25@B130:~$ sudo depmod -ae 
moozikku25@B130:~$ sudo modprobe ndiswrapper 
moozikku25@B130:~$ sudo modprobe b44 
moozikku25@B130:~$ dmesg|grep ndiswrapper 
[   21.925330] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
[   22.021706] usbcore: registered new interface driver ndiswrapper 
[   23.888768] usbcore: deregistering interface driver ndiswrapper 
[   23.920735] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
[   23.942681] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded 
[   23.951617] ndiswrapper: using IRQ 18 
[   23.963416] usbcore: registered new interface driver ndiswrapper 
[17013.878839] ndiswrapper: device wlan0 removed 
[17013.878984] usbcore: deregistering interface driver ndiswrapper 
[17014.095932] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
[17014.110066] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded 
[17014.119219] ndiswrapper: using IRQ 18 
[17014.140355] usbcore: registered new interface driver ndiswrapper

I am re-thinking if I should restart this whole thing over again.  If so, how do I remove all the stuff I installed like ndiswrapper and fw-cutter.  If there is a possibility still for it to work without me re-doing it, that would be great.  But thanks so much for helping me so far.

---

### Post by Ayuthia on 2008-06-25
> **Moozikku25 said:**
> Okay I have done the steps without plugging in the wired internet.  Unfortunately, my there was no light that turned on for the internet card, nor was the enabled wireless was working either.

Here was the result I saved into OpenOffice before I restarted, and inputted the commands you gave me:

moozikku25@B130:~$ sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx 
[sudo] password for moozikku25: 
moozikku25@B130:~$ sudo depmod -ae 
moozikku25@B130:~$ sudo modprobe ndiswrapper 
moozikku25@B130:~$ sudo modprobe b44 
moozikku25@B130:~$ dmesg|grep ndiswrapper 
[   21.925330] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
[   22.021706] usbcore: registered new interface driver ndiswrapper 
[   23.888768] usbcore: deregistering interface driver ndiswrapper 
[   23.920735] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
[   23.942681] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded 
[   23.951617] ndiswrapper: using IRQ 18 
[   23.963416] usbcore: registered new interface driver ndiswrapper 
[17013.878839] ndiswrapper: device wlan0 removed 
[17013.878984] usbcore: deregistering interface driver ndiswrapper 
[17014.095932] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
[17014.110066] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded 
[17014.119219] ndiswrapper: using IRQ 18 
[17014.140355] usbcore: registered new interface driver ndiswrapper

I am re-thinking if I should restart this whole thing over again.  If so, how do I remove all the stuff I installed like ndiswrapper and fw-cutter.  If there is a possibility still for it to work without me re-doing it, that would be great.  But thanks so much for helping me so far.
The information that you posted all looks like it should work.  The only part that is the issue is the DISABLED part in lshw -C network.  That could mean that your card is turned off.  Is there a way for you to turn it on (a switch or a button on the keyboard)?  Are you dual-booting?  If so, can you see if you can turn it on with the other operating system?

As for removing the installation, there are a lot of steps to back out for ndiswrapper.  The fwcutter would just be a matter of uninstalling the b43-fwcutter if I recall correctly.  However, the information that you posted does seem to show that everything is installed correctly, but the wireless card might not be turned on.

---

### Post by Moozikku25 on 2008-06-25
I think I may have screwed up something, the light won't turn on as I usually press (Fn+F2) to turn on my wireless signal.  I am going to start over.  I will refer back to this and ask more (if that is okay).  When problems arise again.  Thanks Ayuthia:)

---

### Post by Lumpy da Moose on 2008-06-26
Mad props! [I]Sehr Danke!  Muchos Gracias! Kudos!
[/I]
However one says it:  thanks a bunch for posting and helping us poor folks get our wireless working.

Using a Dell M1530 with Dell 1490 Wireless (detected as Broadcom BCM 4310). Used the XP Dell drivers as recommended in your link and followed the instructions to the letter.  Hot Dxxx!  It works, even with WPA!  Excellent!!

---

### Post by iption on 2008-06-26
Please help, I have acer aspire with Broadcom 4318, and Hardy amd64. The wireless just won't work. Here is some info:

lshw -C network
```
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: wlan0
       version: 02
       serial: 00:14:a4:38:f0:3b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:e7:06:45
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes

```

iwconfig wlan0
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ndiswrapper -l
```
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: bcm43xx)

```

lsmod|grep -i -e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
```
b44                    33168  0 
mii                     7552  1 b44
ssb                    37252  1 b44
ndiswrapper           243872  0 
usbcore               169904  6 ndiswrapper,ftdi_sio,usbserial,ehci_hcd,ohci_hcd

```

---

### Post by owlgorithm on 2008-06-27
iption, read this thread:
[http://ubuntuforums.org/showthread.php?p=5021672]("http://ubuntuforums.org/showthread.php?p=5021672")

---

### Post by Lyk4n on 2008-06-27
Alex, I want to thank you so much. I'm finally free of the tether of doom!
Also, your directions work perfectly with BCM4312 (rev 03) without referring to the other page (rev 03 is not present on that page)

---

### Post by iption on 2008-06-27
> **owlgorithm said:**
> iption, read this thread:
[http://ubuntuforums.org/showthread.php?p=5021672]("http://ubuntuforums.org/showthread.php?p=5021672")

The first thing I tried before i tried this thread was to use b43 and bcm43xx.

---

### Post by Ayuthia on 2008-06-27
> **iption said:**
> Please help, I have acer aspire with Broadcom 4318, and Hardy amd64. The wireless just won't work. Here is some info:

lshw -C network
```
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: wlan0
       version: 02
       serial: 00:14:a4:38:f0:3b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:e7:06:45
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes

```

iwconfig wlan0
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ndiswrapper -l
```
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: bcm43xx)

```

lsmod|grep -i -e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
```
b44                    33168  0 
mii                     7552  1 b44
ssb                    37252  1 b44
ndiswrapper           243872  0 
usbcore               169904  6 ndiswrapper,ftdi_sio,usbserial,ehci_hcd,ohci_hcd

```

Can you try the following in the Terminal with your router not having any encryption set:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid <name>
sudo dhclient wlan0
```
Please replace <name> with the name of your router.

---

### Post by iption on 2008-06-27
> **Ayuthia said:**
> Can you try the following in the Terminal with your router not having any encryption set:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid <name>
sudo dhclient wlan0
```
Please replace <name> with the name of your router.

Last command did this:
```
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:14:a4:38:f0:3b
Sending on   LPF/wlan0/00:14:a4:38:f0:3b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

And still nothing

---

### Post by Ozdemon on 2008-06-27
Thank you so much.  Wireless now working.  Spec's
 
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Compaq nx6125 AMD Turion 64

Ubuntu 8.04

WPA enabled.
[Edit] 
I lost the connection after hiding the ssid.  No matter what I did after that (including enabling ssid)I could not get it back with WPA, but WEP worked.

So I tried wicd.  Neither wep or wpa worked with that.  So I am back to network-mgr with WEP.

---

### Post by Ayuthia on 2008-06-27
> **iption said:**
> Last command did this:
```
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:14:a4:38:f0:3b
Sending on   LPF/wlan0/00:14:a4:38:f0:3b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

And still nothing
I forgot to add one thing to the list of commands.  Are you able to see any wireless networks:
```
sudo iwlist scan
```

---

### Post by iption on 2008-06-28
> **Ayuthia said:**
> I forgot to add one thing to the list of commands.  Are you able to see any wireless networks:
```
sudo iwlist scan
```

Nope i try this often after i type a couple of new commands... No scan results.

---

### Post by Yondergod22 on 2008-06-28
thank you!:) I tried a few other ways but they didn't work.
and for anyone that this doesn't work for try manually connecting without network manager: [http://ubuntuforums.org/showthread.php?t=571188&highlight=manually+connect+wireless+network](http://ubuntuforums.org/showthread.php?t=571188&highlight=manually+connect+wireless+network)

---

### Post by kg4cxl on 2008-06-30
Thanks for the help on setting up a broadcom chip...Works great!

---

### Post by SpaceMaster on 2008-06-30
Thanks, it worked like a charm!  I'm now enjoying my internal Broadcom Wireless LAN Adapter.

the only trouble I had was connecting to the ftp servers at compaq and hp.  I eventually replaced Step 2 with:

 wget [http://myspamb8.googlepages.com/WPC54Gv2_40826-pruned.zip](http://myspamb8.googlepages.com/WPC54Gv2_40826-pruned.zip)
 unzip WPC54Gv2_40826-pruned.zip

This worked well with my BCM4309 802.11a/b/g (rev 3), and is also suggested for BCM4306 802.11b/g (rev 2).

---

### Post by DWRZ on 2008-07-02
Worked for me (HP zd8000, B4318), I too had to do a "sudo iwconfig wlan0" before it worked though.

Any instructions on removal in case a new kernel fixes b43 so we don't have to use ndiswrapper?

---

### Post by revidnus on 2008-07-04
This worked out nice on my HP dv9610 notebook. Thanks a bunch!

---

### Post by SeanBlader on 2008-07-05
I'd send my thanks that this worked for my Dell Inspiron 8500, but the thanks link doesn't show up for older threads I guess, that's kinda dumb.

THANKS KENT!

---

### Post by koslayn on 2008-07-07
Thank You

---

### Post by DAllenSmith on 2008-07-08
out of all of the ways ive tried to get my broadcom wifi to work and all the trouble ive had this is the best way and works perfectly if u follow the instructions which are very easy, thank you so so so much

---

### Post by DAllenSmith on 2008-07-08
out of all of the ways ive tried to get my broadcom wifi to work and all the trouble ive had this is the best way and works perfectly if u follow the instructions which are very easy, thank you so so so much:lolflag:

---

### Post by Tony Flury on 2008-07-08
May not be related but my wireless now works but my laptop does not seem to want to boot without the wired connection.

what can i do to make Connectivity being optional ?

IGNORE ME - doh ! - I had the wired connection set to dhcp in network manager (rather than roaming) - obviously that means you have to have a connection.

---

### Post by hobs on 2008-07-08
**HELP!**

lspci | grep Broadcom\ Corporation spits out: 

05:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

I followed the steps and used 2b for my wireless BCM4312 (rev 01) 

Nothing has changed except now I don't see the card under Hardware Drivers.  I still can't see any wireless networks.

lshw -C network spits out:

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:1c:26:1a:15:e5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/23/2006, 4.40.1 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11a
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:84:0d:c9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.101 latency=64 module=ssb multicast=yes


Is there something I'm completely overlooking? 
Thanks for the help!

---

### Post by deathsushi on 2008-07-08
> **Ayuthia said:**
> huntis and deathsushi-
Have you tried installing another network manager (wicd or wifiradar)?

The 4318 and the 4306 rev 02 cards are having the hardest times connecting at this point.  I have not seen what is causing it.
Hi Ayuthia,

I tried installing wifiradar but the package configuration (once installed) is a little bit beyond my range of expertise.  I can't track down a wicd package, unless this is the default, in which case, yes, I've tried with that, but the range that it tracks wifi connections is next to useless in my house.

Any other suggestions?

--Adam

---

### Post by zedmondU on 2008-07-08
Thank You

---

### Post by iption on 2008-07-10
I tried every possible solution, but I couldn't find a way to enable my wireless. Drivers work perfectly, just like it says in the how to how they should work, but I can't see any networks. 
In windows I enable my card by pressing the button and light goes up and the card works. In ubuntu it doesn't do that, instead the button has function like one of the shortcut buttons like play, next track, launch browser. This makes me belive that the card is software controlled. 
I've been poking arund with windows drivers and it appers if I disable a program called Launch Manager that comes with my acer laptop, my card can't be enabled, although the drivers for the card work and the card itself shows itself like enabled (like in linux). 
Is there a way to fix that, to get some Launch manager for linux?

I've been searching and I ran into something called acerhk. It looks like something old that might be installed into kernel, because I couldn't find any pages how to install it. Is this something useful and how do I install this?

---

### Post by Mecandes on 2008-07-11
Thank you, the Ubuntu Linux wireless network setup outlined here worked for my Dell Inspiron 8500 notebook with Dell TrueMobile 1300 WLAN Mini-PCI Card (Broadcom BCM4306 rev 02) -- by replacing step 2 with step 2f.
 
The next step, not in your post, is to set up wireless security -- [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) -- after a lot of messing around, I found WPA2/AES doesn't work with my driver, but WPA/TKIP does... which isn't too bad of a compromise, I suppose.
 
Now, if only I could get it to stop asking for the keyring password every time I boot up. (Tried all the recommended fixes to no avail.)

---

### Post by Mysterious_Name on 2008-07-11
This setup worked for me running Broadcom 4310 (rev 1).  Now I can see wireless networks in Network Settings > Wireless settings but I can't successfully connect to one.

---

### Post by tawnos on 2008-07-11
I have this same wireless, but i used system>administration>hardware drivers displayed  my Broadcom B43 wireless driver. selected it, installed, rebooted and was able to see wireless networks but i have issues connecting to most of them.  Also, i'm using WCID to connect to wirless networks. should i use this method to reinstall my wireless car? would this fix my problem?

Thanks:)


EDIT: Not most.. actually all of them... I tried static IP, and their unsecurred... i also tried a secured one with the correct passcode and nothing. WCID just hangs when it tries to obtain IP.

---

### Post by alsan on 2008-07-11
Help please!

I can't find the WLAN device on my HP Compaq 6515d after installing Hardy, which was work properly under CentOS 5.1.

lspci -nn | grep network shows nothing.

Any hint on the issue is appreciated.

---

### Post by Lazy-buntu on 2008-07-11
It's about time Ubuntu, and Linux in general, made wireless easier. Please take a look at this link:

[http://ubuntuforums.org/showthread.php?p=5366748#post5366748](http://ubuntuforums.org/showthread.php?p=5366748#post5366748)

Let the community know what you think!

---

### Post by jeff_ro on 2008-07-12
Thank you very much worked a treat.

---

### Post by scottuss on 2008-07-12
Fantastic! Great walkthrough.

I'm confused though, there's hardly any mention of using acer-acpi to switch the actual hardware on. Surely I can't have the only laptop in the world that needs this? (and always has on any distro / any release / any architecture)


NICE ONE!!!

:guitar:

---

### Post by shantzg001 on 2008-07-12
Thanks. Pitched in to report success with a BCM4306 (Rev 03) with this method. Used BCM43xx earlier with feisty but with hardy, b43 no longer worked so went back (forward??) to using ndiswrapper.
(Note to others: the modprobe b44 is important. without it ur card will not be detected)

---

### Post by Demios101 on 2008-07-15
As much as I would love to be able to do this, the computer I am working on, only has the wireless card, hence I cannot install anything from the repositories. Can someone explain how do do this on a computer that is grounded offline? Of if I could put the needed files on a cd and what I would do from there.

---

### Post by DWRZ on 2008-07-15
Demios101-- had to do offline install a couple of times.

Can't give a detailed walkthrough, but FYI it can be done. I recall the first time I downloaded every package (+ dependencies) I needed on another PC. The second time I simply acquired a DVD with the packages on it. I used the DVD instead of the repos following the same instructions.
 
The third time (had to do a lot of this) I just bought an express card with gigabit ethernet and went to an internet cafe.

---

### Post by Lunks on 2008-07-15
For you who have been trying to use B43 wireless driver and had some weird hiccups from it, try setting iwconfig wlan0 rate auto, it seems to improve connection a bit.

---

### Post by yello_ubu on 2008-07-15
Sadly, I'm giving up;

Acer Aspire 7004WSMi
Broadcom BCM94311MCG (Rev 01)

Out of the box, 8.04 std updates as of today, kernel 2-6-24-19-generic, it SEEMED to look okay, saw the wireless network but just wouldn't log on (unencrypted) and timed out (according to dmesg). I have another laptop running 8.04 that logs on okay so checked DNS & hosts against that, all was okay. I guessed it might be drivers for the Broadcom.

So, I tried fw-cutter (no joy) and then ndiswrapper - 3 different drivers (bcmwl6 from Acer, bcmwl5 as per step 2a, then bcmwl5 per step 2b). 

ndiswrapper & bcmwl5 looked to be configured okay, but didn't see the network. Current state is step 2b. 

$ lshw -C network

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:42:e1:b2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/23/2006, 4.40.1 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

$  ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)

$  sudo iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wlan0     No scan results

$ lspci -nn | grep BCM
01:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

I *think* it's actually not a problem with drivers, or fw-cutter, or ndiswrapper. I *think* it probably could have worked with the out-of-box + bc43 + fw-cutter ... I *think* there's simply a problem connecting to the wireless network... but I don't **know**.

Any ideas what I can do next... except bin the lot and go back to Vista? :(:(

Edit: It might be the laptop... but I don't know what/why exactly. 

I have a Netgear wireless card (WG511T) and configured that (ath0) on the Acer... but have exactly the same problem, i.e. can't see network though everything looks configured okay. 

So I installed PCLinuxOS 2007 (a straight forward process when it came to setting up ndiswrapper and the broadcom driver!).... but the same problem! Instals okay but no networks on 'iwlist scan'... I'm stumped.

RESOLVED: Solved by switching regions on my router from 'France' (where I live) to 'Europe' and using a different channel. For some weird and wonderful reason, none of the 3 'French' channels would work in Ubuntu but would in MS Vista.

For more info, see here [http://ubuntuforums.org/showthread.php?t=864456](http://ubuntuforums.org/showthread.php?t=864456)

---

### Post by Wyer on 2008-07-17
I have a WMP54GS wireless card, I followed all the steps in post1, and used path 2b as that seemed to be the path oters were using for the same card. I'm completely new to linux by the way. so I think the drivers installed alright, but I'm still having no luck connecting to my house's wireless network (which is WEP protected)

I've noticed on some other boards that there are usually a few outputs one can post to help troubleshoot the problem, so if someone could let me know what info you need from me, I'd really like to be able to get this up and running!

---

### Post by jefferybeene on 2008-07-17
Holy Crap, I have wireless!  Had a IBM T23 with a crap card on 7.10 and could never get it working.  Now I have a Compaq Presario V3000 with a the dreaded Broadcom wireless...AND IT'S WORKING!  THANKS A TON.

---

### Post by kyledawg on 2008-07-17
I got the router to show up but the WEP password doesn't work... any suggestions?

---

### Post by Jeremiah478 on 2008-07-17
Thanks for the HowTo, I used this and it worked perfectly; first try, no problems.

And just so it is known I have a:

Broadcom BCM4328 802.11a/b/g/n installed in an HP dv2622ca laptop.

---

### Post by Poteighteau on 2008-07-18
I'm currently using the LiveCD because I don't want to install Ubuntu on this computer until I know for sure that I can get wireless to work. 
Is there any way to make it work without rebooting the computer?
I also seem to have the problem where it will detect networks but is unable to connect to them. Any suggestions?

---

### Post by moebius10 on 2008-07-18
> **Jeremiah478 said:**
> Thanks for the HowTo, I used this and it worked perfectly; first try, no problems.

And just so it is known I have a:

Broadcom BCM4328 802.11a/b/g/n installed in an HP dv2622ca laptop.

I have the same card. But having trouble.
Followed the instructions exactly. Everything worked, even the wireless worked. Then i shut down, went to bed and fired it up the next morning and no wireless. It detects the router but just won't connect. I've just about given up.

---

### Post by Boodah on 2008-07-19
Awesome.. i spent days trying to get wireless working on my DELL 1420. Thanks!!

---

### Post by zggame on 2008-07-20
Thank you.   I just got an Acer 5620-4025 (Pentium Dual 2370 1.7G/1G RAM/120G).  It has a broadcom BCM94311MCG wireless, which works out of box with this proprietary driver but very slowly. It only works in 1Mb/s mode most of the time even within a very close to the router. The wireless works fine within Vista (dual-boot), so it is likely the problem with the software. In iwlist scan, the noise level is very high, 50dBm, while other laptop shows 90dBm.  I used your how-to and it detects the signal correctly with noise at 96dBm and the speed shows up 54M.  Thank you very much.

---

### Post by NotoriousMOK on 2008-07-22
Thank you so much -- what a big help -- this one seems to be running pretty sharp now.

Compaq Presario V2000
Broadcom BCM4318

* Used step 2A from the link provided
** Had to issue the following as recommended by biodiesel bri to see networks, then I was all set

sudo iwconfig wlan0

---

### Post by LunaEqualsLuna on 2008-07-25
> **moebius10 said:**
> I have the same card. But having trouble.
Followed the instructions exactly. Everything worked, even the wireless worked. Then i shut down, went to bed and fired it up the next morning and no wireless. It detects the router but just won't connect. I've just about given up.


Sometimes I find a router restart does the trick, I dunno if you tried that yet though.

I have the same card and this method worked perfectly on two fresh installs. This post save me a MASSIVE headache.

:guitar:

---

### Post by xandr55 on 2008-07-29
Wow am I frustrated, this was about the fifth different way that I tried to get my wireless card to work (BCM4309 chipset on a Dell inspiron 5100). The first time that I tried this method it seemed to cause me to loose all internet connections, so I reinstalled Hardy Heron (which I am starting to loose a lot of faith in...) SO after trying other things I gave it another shot, and this time the computer failed to boot at all, it would always hangup, so I am reinstalling again! Everything just works? Really?:mad::confused: I think that the ideas for this software are great and the aspects of it that work seem to do so fantastically, but I think this area definitely needs improvement, in order to gain a wider appeal base... Especially since not everyone is going to want to learn how to use this to the extent that all of this requires.....

---

### Post by smiley1962 on 2008-07-29
Hello you guys, I seem to need some help on my broadcom 4310 (rev01) i have the native hardy broadcom driver installed, I can connect to my ap WPA/WPA2 but after a few minutes it drops the connection. the only message the system gives me is:
 Jul 29 07:53:35 roelof-laptop kernel: [  778.533290] eth1: no IPv6 routers present

any idea&#347; or is the only solution to give ndwrapper a try?
thnx in advance 
Smiley

---

### Post by dlfuller on 2008-08-01
Thank you for taking the time to create this valuable how-to.

I have a Compaq Presario R3000 laptop with the Broadcom BCM 4306 (rev 03) wireless chipset. I started with a clean install of 8.04 and the default options immediately provided a wired network connection. But then I spent days following various forum post suggestions in an attempt to get a wireless network connection.

The default B43 setup as installed provided wlan0 but nothing I could do would make a network connection. Testing with the older bcm43xx setup as suggested in several posts was worse. No wlan0 and no connection.

Then I ventured into your ndiswrapper approach and carefully followed the step-by-step instructions. I used a Step 2b sp33008 driver download that had worked for bfkeats. But no success for me with more frustration. wlan0 was there but all the configuration setups I tried in Network Settings just would not connect. With or without WEP, different ESSIDs, different channels, etc.

Out of frustration I then clicked on "Enable roaming mode" to get back to normal and quit. Wow! A named connection and a dialog. I entered the WEP key and connected to a network. Even the wireless connection blue indicator and on-off switch on the R3000 also work. And the connection is rock solid staying connected.

I bring this experience up in case someone else is facing the same. My newb missteps along the way plus being sidetracked in the details of manual configuring contributed to overlooking a minimal solution that "just works.". I assume if roaming mode had been selected previously, a connection would have been made on restart, just as stated in Step 9 of your how-to.

---

### Post by oniichan on 2008-08-01
Thanks. Worked perfectly. 

The system is a Dell Inspiron 6000 with an up-to-date Hardy 8.04. Command 'lspci' shows the wireless card as: 

Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02). 

The driver sp34152.exe (wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)) works well with this card. And I did need to include a permanent fix to load ndiswrapper properly.

When using the 'b43' driver, the network connection gui indicated a connection speed of 1MB/s. And the connection was slow even though 'iwconfig' indicated a higher connection speed. Now the connection is noticeably faster and the gui indicates the correct rate.

Thanks again,

jim

---

### Post by soccerush10 on 2008-08-02
Worked for my tx1320us.  I highly reccomend using the link that Alex_Kent_18 provides:  

[https://help.ubuntu.com/community/Wi...f971ca757b2851]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202:%20Download%20and%20Extract%20Drivers")

---

### Post by dthomas08 on 2008-08-02
Hi there, is there any way to do this without being connected to the net with that computer. ie. my laptop with broadcom cannot connect to the LAN by wire anymore (it's dying) is there any way to accomplish this without the internet being connected directly to my laptop? In addition, my laptop does not appear to have "ndiswrapper", what is the reason for this? Thanks for your help. I'm sorry that I'm such a newbie

---

### Post by bdfoster on 2008-08-05
I did get this to work, however I had to do a little bit messing around with settings in order to get it to work properly. I was having another program manage networks than what came with it. Reinstalled and enabled roaming and it was set! Thank you very much for your post.

---

### Post by JeremyC4 on 2008-08-09
FINALLY got it!! I'm a brand new Hardy User. Just did a fresh install the other night:

Acer Aspire 3002LCi (Circa 2004)
AMD Sempron 2800+
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02

Used step 2A on the other list

When I completed everything, I finally got the "bars" for the wireless status on my top panel after my restart. It wasn't connecting though. I restarted again and restarted the Belkin router and now I am zooming on the interweb!

Thank you everyone. I am looking forward to getting as much value as I can out of this community. 

WILD STALLIONS!
:guitar:

---

### Post by veenakj on 2008-08-09
Hi,

I have Hardy 8.04.1 on a presario 2500 laptop. wireless card is

00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

I followed your how-to (used setp 2f) and it shows the following in iwconfig, but will not connect. Here are some details, please do help if you have an idea how to get it to connect to my Netgear router. Wired connection to the same router works, I'm wrting from my wired conn now.

root@veena-laptop:~# ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: bcm43xx)

root@veena-laptop:~# ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/misc/ndiswrapper.ko
version:        1.53
vermagic:       2.6.24-19-generic SMP mod_unload 586 

root@veena-laptop:~# lsmod|grep -i -e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
ndiswrapper           193436  0 
usbcore               146028  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd


root@veena-laptop:~# lshw -C network
  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wlan0
       version: 02
       serial: 00:90:4b:4b:0d:84
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+The Linksys Group, Inc.,07/ latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0e:7f:ec:95:1b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.0.4 latency=90 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=100MB/s

root@veena-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@veena-laptop:~# iwlist wlan0 scanning 
wlan0     Scan completed :
          Cell 01 - Address: 00:30:AB:20:EE:43
                    ESSID:"Wireless"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


Any help is much appreciated, I've been trying to get this to work for over a week. Ubuntu has been good otherwise, though it says my laptop battery is broken and has only 18% capacity. Getting wireless to work seems to be the biggest problem atm.

---

### Post by veenakj on 2008-08-09
UPDATE: I disabled roaming mode and chose dhcp and it got the ip fine and finally! wireless is up and running. A huge thanks to you, whoever made this tutorial :) I tried b43cutter and my old linuxant driverloader drivers etc before trying ndiswrapper, none of them WORKED for me.

My netgear router shows an ip is assigned to my wireless MAC address, but no ip is showing in ifconfig for wlan0 on my laptop. In /var/log/messages, it shows this too:

ADDRCONF(NETDEV_UP): wlan0: link is not ready

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:4b:0d:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Memory:d0002000-d0004000 

I am hoping it is something simple I am overlooking.

Veena

---

### Post by Popoi on 2008-08-13
It worked on Hardy Heron oven a Compaq Presario V2000. From the deep of my heart... I love man! Now my girl will be super happy :D

---

### Post by tonycm1 on 2008-08-15
Thank you so much!!! Worked like a charm on a fresh install of Ubuntu 8.04 using a Dell Inspiron 1300 (Broadcom 4318 rev02).... i used 2a btw.... all set up in less than 5 mins :) thanks again

---

### Post by Dipper on 2008-08-16
I followed the steps in the first post EXACTLY.  Now I am completely screwed.  I cannot enable either the wireless or the ethernet.  What now?

I had to go to my Windows boot to post this because my Linux boot is totally offline. Please help.

---

### Post by Ayuthia on 2008-08-16
> **Dipper said:**
> I followed the steps in the first post EXACTLY.  Now I am completely screwed.  I cannot enable either the wireless or the ethernet.  What now?

I had to go to my Windows boot to post this because my Linux boot is totally offline. Please help.

It sounds like you might have a Broadcom wired ethernet card.  You might try the following to see if it gets your wired connection up:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl bcm43xx
sudo depmod -ae
sudo modprobe b44
sudo ifconfig eth0 up
sudo dhclient eth0
```
This will remove all the wireless card modules and the b44 (Broadcom wired module).  It will then reload the Broadcom wired module and then try to connect.  If that works, then there is a configuration problem.

---

### Post by Dipper on 2008-08-16
This worked to get my wired back up.  But now I'm back to square one with the wireless.  I think the original post is bad advice.  It completely hosed my system.  I will probably re-install my entire system (again) and search for better tutorials.  Thanks anyway.

---

### Post by johnnyresponsible on 2008-08-16
Thank you!  This was the third fix I tried and the first one that worked for me!

---

### Post by bhavin66 on 2008-08-23
Thank you! This was the fifth fix I tried and the first one that worked for me!

---

### Post by jarome on 2008-08-24
It was NetworkManager!! I spent a week pulling out my hair trying everything to get my BCM4312 to work on WPA2. The problem was the #$%^& Gnome NetworkManager. I installed wicd ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) and the wireless worked the first time I rebooted. Amazing.

---

### Post by alphakaya on 2008-08-29
Thank you. This worked for me on my HP L2000 Lance Armstrong Special Edition Laptop, booted of a Hardy 8.04 USB Flash drive.

---

### Post by Lambsauce on 2008-08-30
I've used this guide three times to get my wireless running, and it's worked flawlessly each time.
Until now, anyway--now, when I get to the step wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe) , I get the following:

```

--20:10:41--  ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
           => `sp34152.exe'
Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp34001-34500 ... done.
==> PASV ... 


```

It hangs at ==> PASV ... for a good while (I'd guess 5 minutes? 10?) and then goes back to lambsauce@lambsauce-laptop:~/bcm43xx$ .

Then when I try to run the next step, cabextract sp34152.exe, it tells me there's no such file or directory as sp34152.exe. By that I'm assuming sp34152.exe never finished installing. Anyone know what I can do to make this work? Thank you.

**EDIT:** I need to learn how to search the thread for a solution BEFORE posting my own reply. Problem has been solved. Apologies.

---

### Post by zeitler on 2008-09-11
Hi,

And another one to thank you. Finnaly I can go to sleep. It's 1:30 am and I have to get up at 7:00 am to go to work!

This is the last night I spend tring "to awake" my Broadcom 4306. 

Thanks again. 

zeitler

---

### Post by zeitler on 2008-09-17
Hi!

I used this tutorial and it worked (Thanks again!)

Now I have a new problem: I have gnome and kde installed. If I start session with gnome and after I change to kde the wireless works, but if my first session is with kde the wireless won't work, I have to change to gnome and after change to kde. 

Does anyone knows how to solve this?

Thanks
Zeitler

---

### Post by Ayuthia on 2008-09-17
> **zeitler said:**
> Hi!

I used this tutorial and it worked (Thanks again!)

Now I have a new problem: I have gnome and kde installed. If I start session with gnome and after I change to kde the wireless works, but if my first session is with kde the wireless won't work, I have to change to gnome and after change to kde. 

Does anyone knows how to solve this?

Thanks
Zeitler

It sounds like the gnome version of NetworkManager is being used.  Because of this, it only gets loaded when gnome is started up.  You might need to find the network-manager command to activate it.  Unfortunately, I am using only KDE so I am not too familiar with the name of the app that is used.

---

### Post by Scott-271 on 2008-09-17
I got it working on a fresh install of 8.04 on a multi-boot system (Dell Dimension 4300) with Linksys WMP54GS - 4318 rev 2. Thanks!!! The only problem I'm having now is that after about a day or a day and a half, the wireless drops out; seems like a reboot is the only option. I've read this entire thread and haven't found anything similar.

Actually, I can't even get it up any more since I hooked wired back up, so I may just do another clean install with wired connected and try this method again. Although, any ideas are surely welcome.

Scott

P.S. Much thanks to Kevdog and Ayuthia for all the help they've given in this thread!!!!!!

---

### Post by TechLife on 2008-09-17
@OP: After 2 days of ridiculous ideas I found your post.  It was as easy as that.  TYVM!!!

---

### Post by sam_delta on 2008-09-18
does this procedure works with encryption (WPA , WEP etc) cuz im having a hard time making my bcm4312 rev2 to work with encryption 

i followed another thread and ndiswrapper is working fine on open networks, but not on encrypted ones.


thanks.

---

### Post by bpurvis on 2008-09-24
> **biodiesel-bri said:**
> Thanks for this, I got it all to work after trying many other methods.  I wasn't able to see wireless until I issued this command:

```
$ sudo iwconfig wlan0
```


I want to half-thank Biodiesel-bri for this comment as it stands, I I boot up, then I have to enter this code in the terminal, wait about a minute, manually switch on my one-direction wireless switch, and then it will recognize the wireless networks (roaming is enabled), but it won't actually connect to any network!
I see the network, it says it connects, but has 0% strength and doesn't let me use the internet.
It's a BCM4311 (rev 01) on dedicated ubuntustudio fully updated Hardy Acer Aspire 3680

Any insight is GREATLY appreciated,

- Brandon Purvis

---

### Post by aaamos on 2008-09-25
Sorry, haven't read through the full thread (it's late and I tried LOTS of stuff... ;) ), so apologies if this has already been posted here, but for those with a BCM4322 or similar (4311, 4312, 4321, 4322, or 4328 to be precise) rather than the ones mentioned in the OP, [this thread]("http://ubuntuforums.org/showthread.php?t=880218") worked for me... :)

---

### Post by timbalisto on 2008-09-26
Thank you so much. I tried many other tutorials before this that didn't work. This one worked first time. Thanks:)

---

### Post by adramalech on 2008-09-26
okay so i have been having difficulties with getting my 4318 working...i used the step 2a from the wifidoc...also did /etc/modprobe.d/blacklist and added b43xx, b43, b44, and ssb...

also did the version 3 hotfix on how to stop ndiswrapper from even doing anything with ssb, b44, b43xx etc..

still have the bug...still have not be able to hit FN + F2 and have the wireless working...

am i doing something wrong??:confused:

i also added the wirelessfix.sh file and did all it said in the thread to how to get it to do its thing but still no help...

i did ndiswrapper -l and it shows the bcmwl5.inf module installed correctly...

PLEAZZZEEEEE need help!!!

---

### Post by Specks on 2008-09-26
> **arden667 said:**
> The same thing happened to me and it eventually booted up after I left it for a few minutes.

When it did boot, it gave me an error message.  My apologies for not having taken down the text of the error, but the gist of it was that something didn't load properly with the gnome desktop and it was disabled and would be tried again on my next login.  When my desktop loaded it had reverted itself to the default theme.  Any idea what's conflicting?

On the plus side -- the wireless is up!!  And it's working better for me than it was in Gutsy.  Hurrah!

EDIT:  Didn't have the same problem on the next boot.  Everything seems to be up and running just fine.

This has happened to me, after logging in, it takes along time for the desktop to load, the default theme gets loaded. I do have wireless with WPA2 working. The error states
```

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did no receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Gnome will try to restart the Settings Daemon next time you log in.

```

Any ideas on how to fix this problem?

---

### Post by Ayuthia on 2008-09-27
> **adramalech said:**
> okay so i have been having difficulties with getting my 4318 working...i used the step 2a from the wifidoc...also did /etc/modprobe.d/blacklist and added b43xx, b43, b44, and ssb...

also did the version 3 hotfix on how to stop ndiswrapper from even doing anything with ssb, b44, b43xx etc..

still have the bug...still have not be able to hit FN + F2 and have the wireless working...

am i doing something wrong??:confused:

i also added the wirelessfix.sh file and did all it said in the thread to how to get it to do its thing but still no help...

i did ndiswrapper -l and it shows the bcmwl5.inf module installed correctly...

PLEAZZZEEEEE need help!!!

Can you post the results of:
```
lshw -C network
lsmod|grep -i -e bcm43xx -e b43 -e ssb -e b44 -e ndiswrapper -e wl
```
It will help us see what drivers your card is trying to use.

---

### Post by adramalech on 2008-09-28
here is the result...

```

adramalech@adramalech:~$ sudo lshw -C network
[sudo] password for adramalech: 
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:03:25:28:02:da
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.131 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:07:1c:cf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
adramalech@adramalech:~$ lsmod|grep -i -e bcm43xx -e b43 -e ssb -e b44 -e ndiswrapper -e wl
b44                    33168  0 
mii                     7552  1 b44
ssb                    39428  1 b44
ndiswrapper           243872  0 
usbcore               169904  4 ndiswrapper,ehci_hcd,ohci_hcd

```

---

### Post by mn_goutham on 2008-09-28
[LEFT]Hi Thnks a ton for your suggestions.
Your steps helped me to solve the firs half of the problem, i,e getting my wireless card detected.
But now i can see the wireless networks around but am unable to connect to it.
I am unable to connect to a secured wireless network inspite of giving a valid password.
Can you please let me know if i need to do some more modifications ?

i ran this cmd  sudo lshw -C network and got the following output

 *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e0:08:13
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.5 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:22:68:cc:27:2b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

[/LEFT]

---

### Post by Ayuthia on 2008-09-28
> **adramalech said:**
> here is the result...

```

adramalech@adramalech:~$ sudo lshw -C network
[sudo] password for adramalech: 
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:03:25:28:02:da
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.131 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:07:1c:cf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
adramalech@adramalech:~$ lsmod|grep -i -e bcm43xx -e b43 -e ssb -e b44 -e ndiswrapper -e wl
b44                    33168  0 
mii                     7552  1 b44
ssb                    39428  1 b44
ndiswrapper           243872  0 
usbcore               169904  4 ndiswrapper,ehci_hcd,ohci_hcd

```

It all looks ok.  The script that you used is going to load the b44 and ssb modules after ndiswrapper loads.  Since your wired card uses a sky2 module, you did not really need to use the script.  Please try the following and let us know what happens:
```
sudo modprobe -r b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist scan
```

---

### Post by Ayuthia on 2008-09-28
> **mn_goutham said:**
> [LEFT]Hi Thnks a ton for your suggestions.
Your steps helped me to solve the firs half of the problem, i,e getting my wireless card detected.
But now i can see the wireless networks around but am unable to connect to it.
I am unable to connect to a secured wireless network inspite of giving a valid password.
Can you please let me know if i need to do some more modifications ?

i ran this cmd  sudo lshw -C network and got the following output

 *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e0:08:13
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.5 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:22:68:cc:27:2b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

[/LEFT]
You have a 14e4:4315 chipset (if you type lspci -nn in the Terminal, you will see a line that shows your wireless card and [14e4:4315]).  What this means is that this guide is probably not going to help you.  You might want to try this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

There is a driver there that should help you.  The driver should be 2e.  Your card was initially listed as a 4310, but is now updated to be a 4312.

---

### Post by kolibri on 2008-09-28
[ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)

step two returns:

~$ wget [ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe)
--16:51:59--  [ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe)
           => `sp34152.exe'
Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp3...00 ... 
No such directory `pub/softpaq/sp3...00'.

but I seem to be able to right click and save as- where would I save as to get the rest working?

thanks

---

### Post by Ayuthia on 2008-09-28
> **kolibri said:**
> [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)

step two returns:

~$ wget [ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe)
--16:51:59--  [ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe)
           => `sp34152.exe'
Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp3...00 ... 
No such directory `pub/softpaq/sp3...00'.

but I seem to be able to right click and save as- where would I save as to get the rest working?

thanks

Based on the info in the guide, you will want to store it in the bcm43xx folder in the home directory (~/bcm43xx or /home/<user>/bcm43xx where <user> is replaced with your username without the <>).

---

### Post by adramalech on 2008-09-28
nope because it says on lspci-nn:

```
03:07.0 Network Controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```

for sudo modprobe -r b44 ssb ndiswrapper && sudo modprobe ndiswrapper && sudo iwlist scan :

lo interface doesn't support scanning.   neither does eth0, wlan0 no scan results.

---

### Post by kolibri on 2008-09-28
I've now got a wireless network manager working, and it sees all the local networks, but when I try to connect, it just hangs up and says 'waiting for network key",  then it pops  up with the connection asking me to enter my network key (it's an open network), I enter the key, and it restarts.

I've seen a few other posts on this, but none seem generic enough, nor resolved to help me.

---

### Post by Ayuthia on 2008-09-28
> **adramalech said:**
> nope because it says on lspci-nn:

```
03:07.0 Network Controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```

for sudo modprobe -r b44 ssb ndiswrapper && sudo modprobe ndiswrapper && sudo iwlist scan :

lo interface doesn't support scanning.   neither does eth0, wlan0 no scan results.

Can you check the following:
```
dmesg|grep ndiswrapper
```We are looking for any error messages for ndiswrapper.

---

### Post by Ayuthia on 2008-09-28
> **kolibri said:**
> I've now got a wireless network manager working, and it sees all the local networks, but when I try to connect, it just hangs up and says 'waiting for network key",  then it pops  up with the connection asking me to enter my network key (it's an open network), I enter the key, and it restarts.

I've seen a few other posts on this, but none seem generic enough, nor resolved to help me.

There should be an application somewhere for network manager that will allow you to manually configure your network instead of clicking on the access point to connect.  I think that the issue might be with the encyprtion type when it asks for your password.  Sorry for not being too descriptive on this one.  I am a KDE user and I can't seem to remember how to get to that screen.

---

### Post by kolibri on 2008-09-28
> **Ayuthia said:**
> There should be an application somewhere for network manager that will allow you to manually configure your network instead of clicking on the access point to connect.  I think that the issue might be with the encyprtion type when it asks for your password.  Sorry for not being too descriptive on this one.  I am a KDE user and I can't seem to remember how to get to that screen.

I can right click and get to manually edit, but I have the correct encryption type.  I even checked on another laptop in the house.  I had everything set up right on this computer, but then my harddrive fried and i had to do a clean install on a new hard drive, and I can't reproduce what I did before.

I can connect to a neighbors unsecured network, but not ours.

I'm not sure what to try to do to trouble shoot this anymore, when I try this:

kolibri@xxxx:~$ sudo iwconfig wlan0
wlan0     No such device

---

### Post by ralph7777 on 2008-09-29
RE: Need help with wifi connection for laptop COMPAQ Presario V3637AU

Hi there! =)

I installed Ubuntu 8.04 on my Compaq V3637AU laptop with AMD sempron processor.

I was unable to connect via wifi so I tried using wired DSL but I encountered the same problem.

Here are my findings so far which I hope would be of help.

I noticed the wifi indicator does not turn on.
The device driver profile does not show the wifi driver.
I did the hardware test and 
it showed two devices: 

Broadcom Corp BCM94311MCG wlan mini PCI (rev02)
nVidiaCorp MCP67 Ethernet (vera2)

But the hardware driver profile revealed the NVIDIA accelerated graphics driver (latest cards) 

I am such a greenhorn with Ubuntu yet I am driven to master it and promote it those laptop users I know.

I looked at the forums and the Ubuntu help guides like:

[http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/](http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/)

yet I can't make my wifi or the wired dsl connection work on my laptop. =(

I hope someone can help me out on this. I am in the San Diego Calif area somewhere in National City.

I would greatly appreciate the help from any Ubuntu expert at this time so I can get my laptop connected to the internet.

Thank you very much and more power!



Ralph

---

### Post by Ayuthia on 2008-09-29
> **ralph7777 said:**
> RE: Need help with wifi connection for laptop COMPAQ Presario V3637AU

Hi there! =)

I installed Ubuntu 8.04 on my Compaq V3637AU laptop with AMD sempron processor.

I was unable to connect via wifi so I tried using wired DSL but I encountered the same problem.

Here are my findings so far which I hope would be of help.

I noticed the wifi indicator does not turn on.
The device driver profile does not show the wifi driver.
I did the hardware test and 
it showed two devices: 

Broadcom Corp BCM94311MCG wlan mini PCI (rev02)
nVidiaCorp MCP67 Ethernet (vera2)

But the hardware driver profile revealed the NVIDIA accelerated graphics driver (latest cards) 

I am such a greenhorn with Ubuntu yet I am driven to master it and promote it those laptop users I know.

I looked at the forums and the Ubuntu help guides like:

[http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/](http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/)

yet I can't make my wifi or the wired dsl connection work on my laptop. =(

I hope someone can help me out on this. I am in the San Diego Calif area somewhere in National City.

I would greatly appreciate the help from any Ubuntu expert at this time so I can get my laptop connected to the internet.

Thank you very much and more power!



Ralph

I think that 8.04.1 works with the b43 driver, but 8.04 did not.  Since you don't have a working internet connection, that complicates things a little.  I say this because this guide needs you to have cabextract and I don't recall that being on the install CD.  You might be better off trying the Broadcom wl driver.  If you have a computer that has a working internet connection, you can try this link:
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)
You might also need to install build-essential.  To do this, you will need your install CD.  In the Terminal:
```
sudo apt-cdrom add
```It will ask you for your install CD.  Once that is complete, do the following in the Terminal:
```
sudo apt-get update
sudo apt-get install build-essential
```
What these commands will do is add the CD package information into your computer.  It will then update your computer and then install build-essential.  Build-essential contains packages that will allow your computer to compile some programs.  

If you don't want to do this from the Terminal, you should be able to do this through Synaptic (the Ubuntu package manager).  There should be a menu item that will allow you to manage repositories.  Once it is selected, there should be an option to add the CD.  Unfortunately, I can't guide you too well in there.  I currently don't have Synaptic installed (KDE desktops don't use Synaptic).

If you get stuck, you might want to post where you are stuck in the other link.  This is because you are using the wl option instead of ndiswrapper.

---

### Post by Paultergeist on 2008-09-29
Hi there!

I have a HP Pavilion dv5-1050ep with a Broadcom BCM4312 wireless card.
i tried to do the step by step tutorial, but i still don't have wireless. It detects the wireless, tries to connect, but fails always...

Can anyone help me?
What should i do?

I appreciate your replies.

Thanks

---

### Post by Ayuthia on 2008-09-29
> **Paultergeist said:**
> Hi there!

I have a HP Pavilion dv5-1050ep with a Broadcom BCM4312 wireless card.
i tried to do the step by step tutorial, but i still don't have wireless. It detects the wireless, tries to connect, but fails always...

Can anyone help me?
What should i do?

I appreciate your replies.

Thanks

Can you go into the Terminal and check to see the wireless chipset:
```
lspci -nn
```
If it says [14e4:4315] you will need to try either the wl driver or else this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Otherwise, have you tried removing the encryption from your router?

---

### Post by adramalech on 2008-09-29
well here is the result to dmesg | grep ndiswrapper:

```
adramalech@adramalech:~$ dmesg | grep ndiswrapper
[   39.680713] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   39.823469] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   39.824892] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   39.833388] ndiswrapper: using IRQ 11
[   40.179903] usbcore: registered new interface driver ndiswrapper
[   44.660025] ndiswrapper: device wlan0 removed
[   44.660411] usbcore: deregistering interface driver ndiswrapper
[   44.716300] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   44.730874] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   44.732363] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   44.741210] ndiswrapper: using IRQ 11
[   45.086258] usbcore: registered new interface driver ndiswrapper
adramalech@adramalech:~$ 

```

---

### Post by Paultergeist on 2008-10-01
> **Ayuthia said:**
> Can you go into the Terminal and check to see the wireless chipset:
```
lspci -nn
```
If it says [14e4:4315] you will need to try either the wl driver or else this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Otherwise, have you tried removing the encryption from your router?

You are right, my wirelesse chipset says [14e4:4315].
I give a look at the link you gave me and there is the same chipset working, but for BCM4310 and mine is BCM4312.
Is there any diference? If i install that drivers do you think it's going to work?

Thanks for the replies!

---

### Post by Ayuthia on 2008-10-01
> **Paultergeist said:**
> You are right, my wirelesse chipset says [14e4:4315].
I give a look at the link you gave me and there is the same chipset working, but for BCM4310 and mine is BCM4312.
Is there any diference? If i install that drivers do you think it's going to work?

Thanks for the replies!

The 4310 and 4312 are the same.  It was just labeled incorrectly before.  You should try using that driver and see what happens.  It has worked for some.

---

### Post by adramalech on 2008-10-01
could it be i am using the wrong version of the driver???  because everything seems to do what it should do....but it seems that the lights are on but no one is home kindof thing...

---

### Post by Ayuthia on 2008-10-01
> **adramalech said:**
> could it be i am using the wrong version of the driver???  because everything seems to do what it should do....but it seems that the lights are on but no one is home kindof thing...

You might try another driver.  The 4318 cards are hard to configure in Ubuntu for some reason.

You might even try posting on this thread:
[http://ubuntuforums.org/showthread.php?t=870086](http://ubuntuforums.org/showthread.php?t=870086)

The driver for this thread is the same as the no-fluff thread but I can't seem to see why it is not working.  I suggest posting on the other thread because Jamie Jackson might be able to see something that I am missing.

---

### Post by jal111 on 2008-10-01
thanks alex  wireless works now.

---

### Post by UnixFan11 on 2008-10-04
Great post THANK YOU VERY MUCH
I owe you a beer buddy!

---

### Post by elj4176 on 2008-10-04
My wifi has been working fine until recently - last 2 weeks or so.
It is a:
 Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)

 Here is the output of: dmesg | grep ndiswrapper

[   48.399465] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   48.970680] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   48.972751] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   48.980303] ndiswrapper: using IRQ 9
[   49.348123] usbcore: registered new interface driver ndiswrapper
[   50.246797] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   70.790676] ndiswrapper: device eth1 removed
[   70.790842] usbcore: deregistering interface driver ndiswrapper
[   70.811106] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   70.839259] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   70.841141] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   70.847972] ndiswrapper: using IRQ 9
[   71.169920] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   71.169908] usbcore: registered new interface driver ndiswrapper

The wireless works but it bounces bad. I ping another machine on the network and the response varies between 95ms and 4ms, 

I have checked by pinging the same local machine from another laptop (intel wireless chipset) and the response is consistently under 2ms so it is the wireless on my laptop. 
I have also switched from networkmanager to wifi-radar with no change in response.
The issue is that I cannot watch content from my mythtv machine because the wireless on this machine is jumping all over.
any help would be appreciated.

---

### Post by Ayuthia on 2008-10-04
> **elj4176 said:**
> My wifi has been working fine until recently - last 2 weeks or so.
It is a:
 Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)

 Here is the output of: dmesg | grep ndiswrapper

[   48.399465] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   48.970680] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   48.972751] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   48.980303] ndiswrapper: using IRQ 9
[   49.348123] usbcore: registered new interface driver ndiswrapper
[   50.246797] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   70.790676] ndiswrapper: device eth1 removed
[   70.790842] usbcore: deregistering interface driver ndiswrapper
[   70.811106] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   70.839259] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   70.841141] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   70.847972] ndiswrapper: using IRQ 9
[   71.169920] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   71.169908] usbcore: registered new interface driver ndiswrapper

The wireless works but it bounces bad. I ping another machine on the network and the response varies between 95ms and 4ms, 

I have checked by pinging the same local machine from another laptop (intel wireless chipset) and the response is consistently under 2ms so it is the wireless on my laptop. 
I have also switched from networkmanager to wifi-radar with no change in response.
The issue is that I cannot watch content from my mythtv machine because the wireless on this machine is jumping all over.
any help would be appreciated.

Not for sure if I can help here or not.  How far away are you from the router?  Is the mythtv machine wired to the router or is it also wireless?  If it is also wireless, you can have some bandwidth issues.  You might try the driver in the no-fluff link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
It might produce better results.

I am not for sure about the status of the wl driver that is in hardy-proposed because I have not updated my laptop in a while.  The wl driver connects well and has a great range, but it had problems with making remote mysql connections.  I think that the Ubuntu developers might have fixed the issue, but I have not had a chance to test it out.

---

### Post by strikton on 2008-10-04
Thanks very much for your efoort! You solved my problem. After 2 weeks of trying it&#347; working now at 100% (with Hardy default 70% and not connecting)!

---

### Post by elj4176 on 2008-10-04
> **Ayuthia said:**
> Not for sure if I can help here or not.  How far away are you from the router?  Is the mythtv machine wired to the router or is it also wireless?  If it is also wireless, you can have some bandwidth issues.  You might try the driver in the no-fluff link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
It might produce better results.


I get a strong signal (89%) from the router so that is not the issue. The other laptop is the same distance and connects fine and had consistent ping times (with intel wireless though). 
Mythtv is wired. I have been using this laptop to watch stuff on my mythtv machine for over 2 years w/o problems until now.

The other thing to note is that I just booted into the previous kernel and it works much better. The highest ping time is 3 ms and it is fairly consistent. I'll boot back into the latest kernel and see if it works better.

---

### Post by dforbes on 2008-10-06
I used to run LINUX a while ago, new job using Windows which I hate, anyhow wanting to go back to LINUX.. Yea, however forgot some stuff :(  

I have installed Ubuntu on my laptop that was running VISTA as well. Setup the dual boot and it seems to work great. I am trying to get my BCM4312 802.11 wireless driver installed and having issue. 

uname -a 2.6.24-19-generic

I have done the following steps:

reate a new directory:                 mkdir hybrid_wl
2.  Go to that directory:                   cd hybrid_wl
3.  Untar the appropriate 32/64 bit file
      to that directory
        32 bit:                             tar -xzf <path>/hybrid-portsrc.tar.gz

Cleanup (optional):                  make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
5.  Build the LKM, i.e. wl.ko:           make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`

When doing step number 4 I get the following message:
make: Nothing to be done for `/home/dforebs/wdriver

I did an ls -l in the directory and see the following
lib Makefile src 

please help me. I want to get my wireless card working.

---

### Post by Ayuthia on 2008-10-06
> **dforbes said:**
> I used to run LINUX a while ago, new job using Windows which I hate, anyhow wanting to go back to LINUX.. Yea, however forgot some stuff :(  

I have installed Ubuntu on my laptop that was running VISTA as well. Setup the dual boot and it seems to work great. I am trying to get my BCM4312 802.11 wireless driver installed and having issue. 

uname -a 2.6.24-19-generic

I have done the following steps:

reate a new directory:                 mkdir hybrid_wl
2.  Go to that directory:                   cd hybrid_wl
3.  Untar the appropriate 32/64 bit file
      to that directory
        32 bit:                             tar -xzf <path>/hybrid-portsrc.tar.gz

Cleanup (optional):                  make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
5.  Build the LKM, i.e. wl.ko:           make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`

When doing step number 4 I get the following message:
make: Nothing to be done for `/home/dforebs/wdriver

I did an ls -l in the directory and see the following
lib Makefile src 

please help me. I want to get my wireless card working.

This is acutally a thread for NDISwrapper and not the Broadcom wl driver.  You should start another thread so that people who know more about the wl driver can help you out. 

However, the step that you are on is actually ok.  The make ... clean is only removing anything in that directory that might have been compiled earlier.  Since you are most likely doing this for the first time, there should not be anything to clean out.  But if you are having problems with the second part of the step where you do the build, you might try the following:
```
make -C /lib/modules/`uname -r`/build M=`pwd`
```
The ` is a back quote and not a single quote '.  To make sure that you are using the correct quote, try the following:
```
echo `uname -r`
```
It should return 2.6.24-something.  If it returns uname -r, you are using the single quote.

If this doesn't help, please create another thread about this and we can try to help you out over there.  It is not that I don't want to help you, it is mainly that I want to make sure that you are able to get the help that you are requesting.

By the way, welcome!

---

### Post by elj4176 on 2008-10-07
I fixed it for now. I removed and reinstalled the driver and it is now connecting at 54 Mb/s instead of the 18 Mb/s it was stuck on.
Well - that didn't fix it. Here's a ping to my wireless router:
64 bytes from 192.168.3.1: icmp_seq=1 ttl=255 time=7.37 ms
64 bytes from 192.168.3.1: icmp_seq=3 ttl=255 time=4.06 ms
64 bytes from 192.168.3.1: icmp_seq=4 ttl=255 time=4.04 ms
64 bytes from 192.168.3.1: icmp_seq=5 ttl=255 time=96.0 ms
64 bytes from 192.168.3.1: icmp_seq=6 ttl=255 time=24.0 ms
64 bytes from 192.168.3.1: icmp_seq=7 ttl=255 time=20.0 ms
64 bytes from 192.168.3.1: icmp_seq=8 ttl=255 time=8.03 ms
64 bytes from 192.168.3.1: icmp_seq=9 ttl=255 time=8.15 ms

The intel wireless laptop is consistently under 2ms per ping. I downloaded an updated driver from hp and installed it with ndiswrapper and I get the same results. I booted into the XP partition and I get pings under 2ms consistently. This is driving me nuts and makes me want to avoid hp and broadcom in the future.

---

### Post by adinfinitum on 2008-10-16
Hello  all,

New to the forum but have been reading for a long time and have learned much from you all. I have set up a desktop media centre using ubuntu hardy and love the switch. I have only been using Linux for about 2 months and the learning curve is steep.

Anyways,
Have just decided to run my Dell Latitude D410 on Ubuntu. No problems except my Broadcom BC4318 won't activate. I have run through all the steps on this forum thread and have managed to detect the hardware but still no active WiFi connection.
iwconfig results:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lpcsi results
> 
...
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

I have ndiswrapper installed and configured as per this thread.

I'm out of ideas. every google comes back to this thread or others with the same answers.

Regards,
Tony

---

### Post by jes-13 on 2008-10-18
Just sharing my experiences...

I have a laptop with a BCM4306, rev 02, running Hardy 2.6.24-21 and Network Manager. Wireless works OK with WPA, but it is capped at 1M. Kind of annoying when your Internet connection is 10M...  I tried this method as an attempt to fix the performance problem.  I followed the "recipe" step by step, but used the Broadcom driver archive that works at full speed on my laptop in Windows 2K & XP. The result would not connect to my Wireless Access Point.

I have changed back to my previous slow configuration that works. IMHO this method is not the solution for a BCM4306, rev 02.  

slow working config:
>   *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:02:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:cd:74:0a:57
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.**.** multicast=yes wireless=IEEE 802.11g

The config after using this thread's recipe showed:
> ... driver=ndiswrapper+bcmwl5 ... module=ndiswrapper

I guess I will have to continue searching elsewhere for the performance fix...  :|

---

### Post by Ayuthia on 2008-10-18
> **jes-13 said:**
> Just sharing my experiences...

I have a laptop with a BCM4306, rev 02, running Hardy 2.6.24-21 and Network Manager. Wireless works OK with WPA, but it is capped at 1M. Kind of annoying when your Internet connection is 10M...  I tried this method as an attempt to fix the performance problem.  I followed the "recipe" step by step, but used the Broadcom driver archive that works at full speed on my laptop in Windows 2K & XP. The result would not connect to my Wireless Access Point.

I have changed back to my previous slow configuration that works. IMHO this method is not the solution for a BCM4306, rev 02.  

slow working config:

The config after using this thread's recipe showed:


I guess I will have to continue searching elsewhere for the performance fix...  :|

You might try the ndiswrapper driver from this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Hope that helps.

---

### Post by jes-13 on 2008-10-19
> **Ayuthia said:**
> You might try the ndiswrapper driver from this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Hope that helps.
Tried that one too...  The driver version IDed the same except it said Linksys instead of Broadcom...

---

### Post by adinfinitum on 2008-10-21
Hello again,

I discovered my problem was not, in fact, the driver. It was that I had to re-install WPAsupplicant - at least, that's what I did and everything works great now. I originally installed it before I went through all the other steps here but I couldn't get connection.

The drivers issue with Hardy makes it difficult to pin down cause/effect, but I believe that installing WPA supplicant AFTER activating the wireless card and drivers was the key.

Thanks to all here for a very informative forum.

---

### Post by bcwilson on 2008-10-21
Hi,
The step by step worked well on my dell xps 1330 to get the wireless going on 8.04 (thanks a ton). But I've lost the wireless on my Vista partion (ever since the upgrade that knocked out the ubuntu wifi). In Vista the light is on, driver ok, card enabled, but I can't see any networks. 

Anyone else lose their wifi in Vista like this? Got a fix (aside losing Vista - I need it for work)? 

Thanks,
BC.

---

### Post by cheenky on 2008-10-26
to OP: thank you soooo much for the help, worked like a charm!

---

### Post by alaya.zied on 2008-11-04
I have the same Broadcom card in HP Pavilion dv6420em, it works for me with Ubuntu 8.04

Note that with Ubuntu 8.10 I tried Broadcom STA wireless driver and know it works fine and much better then before.

---

### Post by tr777ple on 2008-11-06
New to Linux and your step by step guide worked wonders...I really appreciate the help.Thank you!

Currently running Hardy 1.9 Ultimate Edition on a HP zv6130us laptop

---

### Post by zancoste on 2008-11-08
Hey Thanks! It all works fine now. Apparently I had a wrong driver or not the right wrapper. I am using the Air Force Broadcom. After following your guide, I could see Wireless networks but I couldn't connect to any. I had to remove Network Manager (Gnome) and install Wicd here ( [http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html](http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html))

Thanks a lot :)
Now I am wire free hehehe

---

### Post by kingleer on 2008-11-09
I have a bcm4311 rev 01, I followed the instructions from page 1 to the letter (substituting step 2a for my particular card). And I got nothing. 

> 
Step 1 (run in terminal)

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx

For Step 2, You can check your Broadcom wireless version with this command in terminal : "lspci | grep Broadcom\ Corporation",if your wireless device is different from BCM4312 (rev 02), please refer to the following link for this step and you can continue again with step 3 onwards:

[https://help.ubuntu.com/community/Wi...f971ca757b2851](https://help.ubuntu.com/community/Wi...f971ca757b2851)


Step 2 (run in terminal)

sudo apt-get install cabextract
wget [ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe)
cabextract sp34152.exe

Step 3 (run in terminal)

sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

Step 4 (run in terminal)

sudo aptitude remove b43-fwcutter

Step 5 (run in terminal)

sudo gedit /etc/init.d/wirelessfix.sh

Step 6

Paste the followings in the opened file(wirelessfix.sh)and make sure you save it before continuing Step 7

#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

Step 7 (run in terminal)

Run this :

cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

Step 8 (run in terminal)

finally run this:

sudo update-rc.d wirelessfix.sh defaults

Step 9

Restart your machine and enjoy the freedom from those wires....



And I got nothing. My wireless card simply doesn't work. PLEASE, I'm in need of some serious help here. 

I'm running the 64 bit version of Ubuntu 8.10.

---

### Post by Arabiest on 2008-11-09
thank u all

---

### Post by Ayuthia on 2008-11-11
> **kingleer said:**
> I have a bcm4311 rev 01, I followed the instructions from page 1 to the letter (substituting step 2a for my particular card). And I got nothing. 




And I got nothing. My wireless card simply doesn't work. PLEASE, I'm in need of some serious help here. 

I'm running the 64 bit version of Ubuntu 8.10.

You might try changing wirelessfix.sh to:
```
#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe -r wl
modprobe ndiswrapper
modprobe b44
```

---

### Post by Sunsangnim on 2008-11-20
Thank you so much! I tried everything before I came across your post. This is my Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02). Lots of people have had trouble with this one...Now my gOS is up and running perfectly.:)

---

### Post by jago25_98 on 2008-11-22
No worky for me, but mine's rev01...

I see the network, but it comes up with TKIP option. WPA is mixed in with WPA2 and that's the only option. Why?

Not too impressed. Real bummer. I'm on ibex and still the same problems.

---

### Post by patanjali on 2008-12-07
I would like to thank alex_kent_18 for his step by step.  My wireless works flawlessly.  Thanks again!

Patanjali  :-)

---

### Post by alex_kent_18 on 2008-12-09
This article is exclusive to ubuntu 8.04. For 8.10 users, please use the STA Driver that can find in "Restricted Driver Manager". You will not need to config ur wireless driver setup from terminal anymore with that driver. Here, take a look : [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom")

---

### Post by deadbug159 on 2008-12-12
my wired connection is unavailable. but i have another computer to download what i need... what steps need to be taken to get what i need. is it possible to copy a package from one computer to another?

---

### Post by leartec on 2008-12-18
I have been looking all over for instructions on how to patch my bcm4312 driver to get it working with aircrack-ng so it will support injection. I think I can get the rest figured out if I knew how to patch the driver. Will this post get me the correct driver to support injection for aircrack-ng? If not, can anyone steer me into the right direction? Just so you know I am actually using Ubuntu 8.10

---

### Post by Ayuthia on 2008-12-18
> **leartec said:**
> I have been looking all over for instructions on how to patch my bcm4312 driver to get it working with aircrack-ng so it will support injection. I think I can get the rest figured out if I knew how to patch the driver. Will this post get me the correct driver to support injection for aircrack-ng? If not, can anyone steer me into the right direction? Just so you know I am actually using Ubuntu 8.10

As far as I know, you will need to use the b43 module, not NDISwrapper or wl.  Since you are using Intrepid, I am not for sure if you need any patches or not.  The site only lists patches for 2.6.24 and 2.6.25 not for 2.6.27.

If you need help with installing b43, you should create another thread that lists your card and the b43 module so that it can be easy to find.  This thread is for NDISwrapper so you might not get the assistance as quickly.

---

### Post by leartec on 2008-12-19
Thanks for the reply. I thought I might need to post a new thread. I will get one up ASAP. Thanks for the help.

---

### Post by nitestar on 2008-12-26
Alex
I tried 5 times following your instructions in the Absolutly  . Evidently something else is wrong. what I want is for the Ubuntu to be able to communicate with my printer. **NOT the internet**. I have a wireless system in the house to allow us to print and other stuff remotely.
Still trying to fix the problem.

thanks for the help, well done. Now I know where to go if I ever have a problem.

---

### Post by sburris on 2009-02-03
I tried the fix several times without success. I am trying to get a WMP54gs version 1.1 to work on 8.04. My CPU is an AMD 64 Athlon 64x2 on a 32 bit platform. Do you have any other suggestions?
P>S> When I use the alternate to step 2, I find my card is listed a a BCM4318

---

### Post by sburris on 2009-02-03
I guess the 6th time is a charm. Apparently I was doing something wrong the other 5 times but I got it to work this time. Thanks for the help.
This forum is great!

---

### Post by wcasper on 2009-02-05
Thanks for the info. I have a BCM4328 rev03 & these instructions worked perfectly.

---

### Post by java_flex on 2009-02-24
I went through all the steps suggested by you, but still wireless isn't working. I can see the available wireless networks but cannot connect to any.

I'm using broadcom 4312(rev 02) on amd 64. any suggestions ?

---

### Post by java_flex on 2009-02-24
bump

---

### Post by flex- on 2009-02-25
I've followed the instruction in first post of this tread to get the wireless working.
Currently it detects the wireless network but am unable to connect, the wireless has a wep shared key/passphares.

The following are all the info i could gather ( in the light to narrow the possible issue or even better to resolve this once and for all)

@ this is a compaq presario v3700, amd64, on newly installed Hardy Heron 32Bit, wifi Card BCM4312, wired card non B44.

@4Real:~$ uname -a
Linux 4Real 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux

@4Real:~$ lspci -nn | grep Network
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)
 

@4Real:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:40:01:d5
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=10.1.1.2 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan1
       version: 02
       serial: 00:1a:73:dc:43:20
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g



@4Real:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


@4Real:~$ lsmod|grep -i -e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
b44                    28432  0 
ssb                    34308  1 b44
mii                     6400  1 b44
ndiswrapper           192920  0 
usbcore               146412  7 ndiswrapper,hci_usb,uvcvideo,usbhid,ehci_hcd,ohci_hcd


@4Real:~$ cat /etc/modules|grep -i -e b43 -e b44 -e ssb -e ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper
---> Yes there was three identical listing after running the above command 
 
@4Real:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-23-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-23-generic SMP mod_unload 586 

@4Real:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4312) present (alternate driver: ssb)


4Real:~$ lspci -nm
00:00.0 "0500" "10de" "0547" -ra2 "103c" "30d6"
00:01.0 "0601" "10de" "0548" -ra2 "103c" "30d6"
00:01.1 "0c05" "10de" "0542" -ra2 "103c" "30d6"
00:01.2 "0500" "10de" "0541" -ra2 "103c" "30d6"
00:01.3 "0b40" "10de" "0543" -ra2 "103c" "30d6"
00:02.0 "0c03" "10de" "055e" -ra2 -p10 "103c" "30d6"
00:02.1 "0c03" "10de" "055f" -ra2 -p20 "103c" "30d6"
00:04.0 "0c03" "10de" "055e" -ra2 -p10 "103c" "30d6"
00:04.1 "0c03" "10de" "055f" -ra2 -p20 "103c" "30d6"
00:06.0 "0101" "10de" "0560" -ra1 -p8a "f03c" "30d6"
00:07.0 "0403" "10de" "055c" -ra1 "103c" "30d6"
00:08.0 "0604" "10de" "0561" -ra2 -p01 "" ""
00:09.0 "0101" "10de" "0550" -ra2 -p85 "103c" "30d6"
00:0a.0 "0200" "10de" "054c" -ra2 "103c" "30d6"
00:0c.0 "0604" "10de" "0563" -ra2 "" ""
00:0d.0 "0604" "10de" "0563" -ra2 "" ""
00:12.0 "0300" "10de" "0531" -ra2 "103c" "30d6"
00:18.0 "0600" "1022" "1100" "" ""
00:18.1 "0600" "1022" "1101" "" ""
00:18.2 "0600" "1022" "1102" "" ""
00:18.3 "0600" "1022" "1103" "" ""
01:09.0 "0c00" "1180" "0832" -r05 -p10 "103c" "30d6"
01:09.1 "0805" "1180" "0822" -r22 "103c" "30d6"
01:09.2 "0880" "1180" "0843" -r12 "103c" "30d6"
01:09.3 "0880" "1180" "0592" -r12 "103c" "30d6"
01:09.4 "0880" "1180" "0852" -rff -pff "" ""
04:00.0 "0280" "14e4" "4312" -r02 "103c" "1371"


4Real:~$ ls -l /etc/ndiswrapper/bcmwl5*
total 1524
-rw-r--r-- 1 root root    905 2009-02-24 21:36 14E4:4311:1363:103C.5.conf
-rw-r--r-- 1 root root    905 2009-02-24 21:36 14E4:4311:1364:103C.5.conf
-rw-r--r-- 1 root root    905 2009-02-24 21:36 14E4:4311:1365:103C.5.conf
-rw-r--r-- 1 root root    905 2009-02-24 21:36 14E4:4311:1374:103C.5.conf
-rw-r--r-- 1 root root    905 2009-02-24 21:36 14E4:4311:1375:103C.5.conf
-rw-r--r-- 1 root root    905 2009-02-24 21:36 14E4:4311:1376:103C.5.conf
-rw-r--r-- 1 root root    905 2009-02-24 21:36 14E4:4311:1377:103C.5.conf
lrwxrwxrwx 1 root root     26 2009-02-24 21:36 14E4:4311.5.conf -> 14E4:4311:1363:103C.5.conf
-rw-r--r-- 1 root root    961 2009-02-24 21:36 14E4:4312:135F:103C.5.conf
-rw-r--r-- 1 root root    961 2009-02-24 21:36 14E4:4312:1360:103C.5.conf
-rw-r--r-- 1 root root    961 2009-02-24 21:36 14E4:4312:1361:103C.5.conf
-rw-r--r-- 1 root root    961 2009-02-24 21:36 14E4:4312:1362:103C.5.conf
-rw-r--r-- 1 root root    961 2009-02-24 21:36 14E4:4312:1370:103C.5.conf
-rw-r--r-- 1 root root    961 2009-02-24 21:36 14E4:4312:1371:103C.5.conf
-rw-r--r-- 1 root root    961 2009-02-24 21:36 14E4:4312:1372:103C.5.conf
-rw-r--r-- 1 root root    961 2009-02-24 21:36 14E4:4312:1373:103C.5.conf
lrwxrwxrwx 1 root root     26 2009-02-24 21:36 14E4:4312.5.conf -> 14E4:4312:135F:103C.5.conf
-rw-r--r-- 1 root root    901 2009-02-24 21:36 14E4:4318:1355:103C.5.conf
-rw-r--r-- 1 root root    901 2009-02-24 21:36 14E4:4318:1356:103C.5.conf
-rw-r--r-- 1 root root    901 2009-02-24 21:36 14E4:4318:1357:103C.5.conf
lrwxrwxrwx 1 root root     26 2009-02-24 21:36 14E4:4318.5.conf -> 14E4:4318:1355:103C.5.conf
-rw-r--r-- 1 root root    957 2009-02-24 21:36 14E4:4319:1358:103C.5.conf
-rw-r--r-- 1 root root    957 2009-02-24 21:36 14E4:4319:1359:103C.5.conf
-rw-r--r-- 1 root root    957 2009-02-24 21:36 14E4:4319:135A:103C.5.conf
lrwxrwxrwx 1 root root     26 2009-02-24 21:36 14E4:4319.5.conf -> 14E4:4319:1358:103C.5.conf
-rw-r--r-- 1 root root    901 2009-02-24 21:36 14E4:4320:00E7:0E11.5.conf
-rw-r--r-- 1 root root    924 2009-02-24 21:36 14E4:4320:12F4:103C.5.conf
-rw-r--r-- 1 root root    901 2009-02-24 21:36 14E4:4320:12F8:103C.5.conf
-rw-r--r-- 1 root root    901 2009-02-24 21:36 14E4:4320:12FA:103C.5.conf
-rw-r--r-- 1 root root    901 2009-02-24 21:36 14E4:4320:12FB:103C.5.conf
lrwxrwxrwx 1 root root     26 2009-02-24 21:36 14E4:4320.5.conf -> 14E4:4320:00E7:0E11.5.conf
-rw-r--r-- 1 root root    957 2009-02-24 21:36 14E4:4324:12F9:103C.5.conf
-rw-r--r-- 1 root root    957 2009-02-24 21:36 14E4:4324:12FC:103C.5.conf
lrwxrwxrwx 1 root root     26 2009-02-24 21:36 14E4:4324.5.conf -> 14E4:4324:12F9:103C.5.conf
-rw-r--r-- 1 root root    961 2009-02-24 21:36 14E4:4328:1366:103C.5.conf
-rw-r--r-- 1 root root    961 2009-02-24 21:36 14E4:4328:1367:103C.5.conf
-rw-r--r-- 1 root root    961 2009-02-24 21:36 14E4:4328:1368:103C.5.conf
-rw-r--r-- 1 root root    961 2009-02-24 21:36 14E4:4328:1369:103C.5.conf
lrwxrwxrwx 1 root root     26 2009-02-24 21:36 14E4:4328.5.conf -> 14E4:4328:1366:103C.5.conf
-rw-r--r-- 1 root root 811278 2009-02-24 21:36 bcmwl5.inf
-rw-r--r-- 1 root root 604928 2009-02-24 21:36 bcmwl5.sys


Any help is very much appreciated..
Thanks in advance

ps: java_flex has no relation with me whatsoever, sorry was in a rush to register on this forum only to realise this nick came about subconciously from yours.

---

### Post by mattchess on 2009-03-16
Thanks - worked for my M1210 :D

---

### Post by yvedpathak on 2009-03-17
Thank you very much. It works!

---

### Post by Thumbtack on 2009-03-24
Thank-You Sweet Jesus it finally works.  New to linux, command line, everything... Glad my wireless now works though.  This really helped after trying 20 different ways to get online.  I got a feeling I am headed for a LONG walk trying to figure this stuff out.

---

### Post by Dirty TR on 2009-03-29
Ok, so I'm very new and I'm followin the step-by step on the first page.  When I get to Step 5, I get the following error:

# sudo gedit /etc/init.d/wirelessfix.sh

(gedit:10807): Gtk-WARNING **: cannot open display: 


Any ideas?

---

### Post by rzh on 2009-04-12
New user here. I'm running Intrepid on an Dell Inspiron 9300 with a Broadcom 4306 (rev 03) and wanted to say that, after trying several other suggestions scattered around these forums, I finally found total success with the method listed in the original post. Thank you!

---

### Post by Mangulit_Lang on 2009-04-24
My Gosh!!!  :lolflag:

**You hit the nail right on the Head.** 

Im a noob but a technical support person and trying my hand on Ubuntu.

Patience is virtue... and believe me in my work its a requirement.

But with this wireless issue im stumped.  If its a microsoft OS i would have fixed it in 10-15mins or less but since this is Linux i dont know a thing about it. I've tried OpenSuse, no good and had to switch to Ubuntu but it still took me weeks finding solutions.	](*,)

**However, because of you, im posting this reply using my NEW ubuntu wireless capability. YEHEY!!! ** \\:D/

If you were here i would have drop by your house and hug and kiss you to death or treat you to a dinner. ***IM NOT KIDDING.*** ;D

I can always fly to SG for a visit or have a friend there to reward you by kissing and hugging you then treat you to dinner. HOWS THAT?

Just tell me when and where.


[SIZE="1"]BTW... did i mention that the friend who will be doing the DEED is a guy? [/SIZE]	:biggrin:

---

### Post by dmies73 on 2009-04-27
I hae been fighting this all night about 6 hours at least
 and i still can not get it work
 
wlan0     IEEE 802.11g  ESSID:"GOESH"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
 
anyone have anything?
i am new to this and not happy right now,,

---

### Post by azmike on 2009-05-15
this was the ticket.......... thank you hours of fumbling and solved in just a few simple steps    this worked great:KS:popcorn:):P

---

### Post by Mr.Ice Cold on 2009-05-17
Bump!

---

### Post by seanohoulihan on 2009-06-03
Awesome!!!  Thanks so much.  I am a total n00b at this and was fairly certain that I did something wrong somewhere, but when I re-booted my system... I could see my wireless networks!!  Many Thanks.  It's nice when something actually works.

---

### Post by Lacho on 2009-06-04
Hi,

I am a Ubuntu newbie, with almost 19 years of experience dealing with MS Windows frustrations, so please bear with me.

I have everything working fine in my laptop, with Ubuntu as the only OS, no more Vista for me, but I have a question that my inner obsessive compulsive geek cannot postpone any longer: After installing the drivers for my wifi card (bcm43xx), several files are kept in my home folder, horacio, do I have to leave them there, or are these leftover from the installation and can be safely deleted?

My candidates for deletion are: bcm43xx, Driver, bcm43xx.cat, bcmwl5.inf, bcmwl5.sys, Driver3100640.zip.

Or take a look at the screenshot:

---

### Post by jtmedin on 2009-06-04
FYI I had trouble with the broadcom wireless & finally gave up because the xmission rate was so poor & unreliable. Moved to 9.04 & problem solved. Did nothing but install & setup the security. Thanks boys/girls of 9.04.

---

### Post by Ayuthia on 2009-06-05
> **Lacho said:**
> Hi,

I am a Ubuntu newbie, with almost 19 years of experience dealing with MS Windows frustrations, so please bear with me.

I have everything working fine in my laptop, with Ubuntu as the only OS, no more Vista for me, but I have a question that my inner obsessive compulsive geek cannot postpone any longer: After installing the drivers for my wifi card (bcm43xx), several files are kept in my home folder, horacio, do I have to leave them there, or are these leftover from the installation and can be safely deleted?

My candidates for deletion are: bcm43xx, Driver, bcm43xx.cat, bcmwl5.inf, bcmwl5.sys, Driver3100640.zip.

Or take a look at the screenshot:

The two files that ndiswrapper uses are bcmwl5.inf and bcmwl5.sys.  If you used ndiswrapper, it would be best to keep those two files in case you ever need to install them again.  However, if I recall correctly, those two files are probably in /etc/ndiswrapper/bcmwl5 also.

---

### Post by SpaCeTraNce on 2009-06-16
After two days of frustration. This worked for my broadcoam 4318 card(using the correct drivers from another post). Needless to say this has been a huge learning experience. I have been a pc technician for years and I'm moving over to network administration so I moved to Ubuntu to start studying a linux system. Getting my wireless card up and going has gotten me slighlty familure and comfortable with the command prompt (it will take a while to loose the dos language :) ). 

Anyways thanks for a good post... now I just have to fix my WPA/DHCP issue.... I can connect to open networks... but not one with security turned on....

:D

---

### Post by JoeLaX75 on 2009-07-18
You deserve an award, my friend. Thank you much!

---

### Post by pvnbg on 2009-07-19
Ubuntu 9.04 & Broadcom 4318 & your guide... It works. 10x :popcorn:

---

### Post by jmarpu33 on 2009-10-11
It works also in karmic koala, 9.10! Thanks.

---

### Post by pilot26 on 2009-10-12
Thank YOU!!
you are my hero
I am using ubuntu 9.04 W/ broadcom 4311 V1
and after working when i first installed then not working for the past TWO mo. and endless questions and answers that did not solve the problem, this did.
Matt

---

### Post by Herukam on 2009-10-22
There should be some kind of popular working solutions sector in this forum. :P

I tried this yesterday and IT WORKED. Was a bit surprised since all the other eight or ten solutions I tried had not worked. Thanks Alex. :)

I have HP Pavilion ZE2000 with that mean Broadcom 4318 which everybody is worrying about. Ubuntu version is 9.04.

---

### Post by mariou on 2009-10-22
Thank you so much! I tried other approaches posted, but this one saved the day....now if I could just get WAP to work :-(

---

### Post by wstock69 on 2009-10-25
Post 1 in this process worked for me first try and 100% on my BCM4318 Wireless.

THANKS!!!

---

### Post by damien82 on 2009-11-01
<-- another happy mofo, thanks ALOT for this, nothing else worked :D

---

### Post by mbr78 on 2009-11-01
How do I get this to work if my only source of the internet is wireless? I can download files in XP and access them in Ubuntu 9.10 but I can't use the get commands and stuff in Ubuntu untill my wireless adapter works in Ubuntu.

---

### Post by howcanireachthesekids on 2009-11-02
Is there any way to get my [B]_*B*roadcom Wireless BCM4312 (rev 01)_ 
[/B]to work on Ubuntu 9.10 ?
I have no access to internet, hence i cant wget or update....

Thanks in advance !
It will HELP me a lot, i am having headache with this problem:(

---

### Post by howcanireachthesekids on 2009-11-03
bump for good

---

### Post by howcanireachthesekids on 2009-11-03
I can not download ```
ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
```
Can anyone upload the exact tool somewhere else ? Possibly, rapidshare.com

Thanks

---

### Post by dudekaz1 on 2009-11-03
man! right when i find this on the forms im at work....without linux

---

### Post by CaKiwi on 2009-11-09
When I enter

sudo apt-get install ndiswrapper-utils-1.9

I get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.9

Any thoughts?

---

### Post by dt_matthews on 2009-11-09
well I have nearly done it succesfully! wifi is now enabled with WPA support but my router (with WPA/WPA2 security) is disabled, the other unsecured networks being enabled. can anyone advise why this might be?

TIA,
dan

---

### Post by Ayuthia on 2009-11-10
> **CaKiwi said:**
> When I enter

sudo apt-get install ndiswrapper-utils-1.9

I get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.9

Any thoughts?

If you have a working internet connection, you might try the following:
```
sudo apt-get update
sudo apt-get intsall ndiswrapper-utils-1.9
```
If you don't, it might be on the LiveCD so you will need to add it:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```When you enter the apt-cdrom command, it will ask you for the LiveCD.  Press enter once the CD is loaded and then proceed with the next two commands.

Hope that helps.

---

### Post by CaKiwi on 2009-11-14
Thanks Ayuthia, that did work but i ended up using post #1 in 

[http://ubuntuforums.org/showthread.php?t=1305906](http://ubuntuforums.org/showthread.php?t=1305906)

to fix my problem

---

### Post by kiruri on 2009-11-26
Hi, all and sorry if I am wrong with the forum thread of this post. 

**Summary first:** **[updating]("http://ubuntuforums.org/archive/index.php/t-1305906.html")** newer wireless drivers from compat-wireless solves the wireless problem in Ubuntu 9.10 for Lenovo IdeaPad s12 with Via Nano processor.

How I managed to get broadcom card to work:

**Story:**
New, freshly installed Ubuntu 9.10 on Lenovo IdeaPad s12 (Via Nano processor).

I have done all the instructions, step by step from this (current) thread - no result.
I have done the instruction from the previous post of this thread (fully update and upgrade Ubuntu, then activate new proprietary hardware driver for Broadcom) - no result.
**[This tutoria]("http://ubuntuforums.org/showthread.php?t=25683")l** unfotunatelly gave me no results too (I have done it step by step).

By 'no result' I mean that I could see my wireless card, but I couldn't connect to my hidden wireless network - it was not in the available networks list and it was not possible to connect to it by defining its ESSID manually.

I have an Ubuntu 8.04 desktop and Nokia smartphone that work perfectly with this particular wireless network (IPcop is used, and I manually define all allowed MAC addresses).

Though, the result of all guides was that I could see one available wireless network in the list (probably my neighbour's), but not mine.
[B]
lspci:[/B]
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

**iwconfig:**
eth1     IEEE 802.11    Nickname:""
            Access point: Not-Associated

And then I followed [this]("http://ubuntuforums.org/showthread.php?t=1266620") tutorial, and I saw 2 drivers (b43 and STA) in Administration>Hardware drivers.
Undo blacklisting of b43 (fw-cutter) and it began to work. I suppose that was because the b43 has been updated.

**(lspci** showed a new interface: wlan1)

Thank you all authors of all mentioned guides!

P.S. As I am a newbie in Linux (not a newbie, but not a specialist too :)), I think that more experienced members of this forum could re-edit my story to make a good step-by-step guide specially for Lenovo IdeaPad s12 (via nano) owners. These owners willl be thankful I think :)

keywords for the s12 owners: ubuntu 9.10 enable wireless lenovo ideapad s12 via nano

---

### Post by meuzak on 2009-12-26
> **alex_kent_18 said:**
> I used the following steps to enable my _*Broadcom Wireless BCM4312 (rev 02)*_.

**Step 1 (run in terminal)**

[COLOR=Blue]echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx[/COLOR]

[COLOR=Red]**For Step 2, You can check your Broadcom wireless version with this command in terminal : [B][COLOR=Red]"_*lspci | grep Broadcom\ Corporation*_"[/COLOR]**,if your wireless device is different from BCM4312 (rev 02), please refer to the following link for this step and you can continue again with step 3 onwards:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)[/B][/COLOR]


**Step 2 (run in terminal)**

[COLOR=Blue]sudo apt-get install cabextract
wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
cabextract sp34152.exe[/COLOR]

**Step 3 (run in terminal)**

[COLOR=Blue]sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant[/COLOR]

**Step 4  (run in terminal)**

[COLOR=Blue]sudo aptitude remove b43-fwcutter[/COLOR]

**Step 5  (run in terminal)**

[COLOR=Blue]sudo gedit /etc/init.d/wirelessfix.sh[/COLOR]

**Step 6**

Paste the followings in the opened file(wirelessfix.sh)and **make sure you save it before continuing Step 7**

[COLOR=Blue]#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
[/COLOR]
**Step 7  (run in terminal)**

Run this :

[COLOR=Blue]cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh[/COLOR]

**Step 8  (run in terminal)**

finally run this:

[COLOR=Blue]sudo update-rc.d wirelessfix.sh defaults [/COLOR]

**Step 9**

[COLOR=Blue]Restart your machine[/COLOR] and enjoy the freedom from those wires....



Thank you so very much....I got a bcm4306 and 4318 both laptop's working with that....I can't thank you enough. My wife thanks you too.....:P

---

### Post by alanpmurphy on 2009-12-26
FYI for all interested. I have successfully used the Broadcomm released LINUX driver for their chipset. Follow the instructions and you should have no problem. My machine is Dell Inspiron 6400 with B44 version chipset. If anyone has a difficulty, let me know and I'll try and help.

---

### Post by nanimo on 2009-12-28
I am trying to use these steps to get my broadcom bcm4328 card working in Ubuntu 9.10.  lspci gives me this: 
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)
Does this mean that a driver is working for the card? 
ndiswrapper gives me this feedback:
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4328) present (alternate driver: ssb)
iwconfig gives me this:
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

I am not sure how to determine if my driver is functioning or what I should try next.  Sorry to ask for such basic help, but I have been trying to use a lot of the forums and have been met with little success.  
Thanks

---

### Post by trixter76 on 2010-01-05
I just wanted to thank you for posting these steps.  They were very helpful in getting my wireless to work and I appreciate you taking the time out to write them.  

I also want to thank all of the people on the forum that posted any advice.  I'm pretty sure I read through everything available and was able to get mine working.  

Thanks all!

---

### Post by jesjep on 2010-01-27
Hi,

I have been spending the last few days trying to get my broadcom 4318 wireless working in 8.04 and I was unable to do it with this guide. I can't get even the light to turn on. The card works ok in windows. I'm tired. I'm going to bed. Help. Please. Thanks.

uname -a

Linux laptop 2.6.24-26-generic #1 SMP Tue Dec 1 18:37:31 UTC 2009 i686 GNU/Linux

lshw -C network

WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth1
       version: 02
       serial: 00:14:a4:5d:43:71
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:e0:56:eb
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.254.2 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes

ndiswrapper -l

bcmwl5 : driver installed
    device (14E4:4318) present (alternate driver: ssb)

ndiswrapper -v

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-26-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-26-generic SMP mod_unload 586 

lspci -nn|grep Network

06:05.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod|grep -i -e bcm43xx -e b43 -e ssb -e b44 -e ndiswrapper -e wl

ndiswrapper           192920  0 
usbcore               146412  4 ndiswrapper,ehci_hcd,ohci_hcd


cat /etc/modules|grep -i -e b43 -e b44 -e ssb -e ndiswrapper

install/manage Windows drivers for ndiswrapper
usage: ndiswrapper OPTION
ndiswrapper

lspci -nm

00:00.0 "0600" "1002" "5950" -r01 "1025" "0080"
00:02.0 "0604" "1002" "5a34" "" ""
00:06.0 "0604" "1002" "5a38" "" ""
00:07.0 "0604" "1002" "5a39" "" ""
00:13.0 "0c03" "1002" "4374" -p10 "1025" "0080"
00:13.1 "0c03" "1002" "4375" -p10 "1025" "0080"
00:13.2 "0c03" "1002" "4373" -p20 "1025" "0080"
00:14.0 "0c05" "1002" "4372" -r11 "1025" "0080"
00:14.1 "0101" "1002" "4376" -p8a "1025" "0080"
00:14.3 "0601" "1002" "4377" "1025" "0080"
00:14.4 "0604" "1002" "4371" -p01 "" ""
00:14.5 "0401" "1002" "4370" -r02 "1025" "0079"
00:14.6 "0703" "1002" "4378" -r02 "1025" "0080"
00:18.0 "0600" "1022" "1100" "" ""
00:18.1 "0600" "1022" "1101" "" ""
00:18.2 "0600" "1022" "1102" "" ""
00:18.3 "0600" "1022" "1103" "" ""
01:00.0 "0300" "1002" "3150" "1025" "0080"
06:05.0 "0280" "14e4" "4318" -r02 "1468" "0311"
06:06.0 "0607" "104c" "8031" "1025" "0080"
06:06.2 "0c00" "104c" "8032" -p10 "1025" "0080"
06:06.3 "0180" "104c" "8033" "1025" "0080"
06:06.4 "0805" "104c" "8034" "1025" "0080"
06:07.0 "0200" "10ec" "8169" -r10 "1025" "0079"

ls -l /etc/ndiswrapper/bcmwl5*

total 1524
-rw-r--r-- 1 root root    905 2010-01-20 16:18 14E4:4311:1363:103C.5.conf
-rw-r--r-- 1 root root    905 2010-01-20 16:18 14E4:4311:1364:103C.5.conf
-rw-r--r-- 1 root root    905 2010-01-20 16:18 14E4:4311:1365:103C.5.conf
-rw-r--r-- 1 root root    905 2010-01-20 16:18 14E4:4311:1374:103C.5.conf
-rw-r--r-- 1 root root    905 2010-01-20 16:18 14E4:4311:1375:103C.5.conf
-rw-r--r-- 1 root root    905 2010-01-20 16:18 14E4:4311:1376:103C.5.conf
-rw-r--r-- 1 root root    905 2010-01-20 16:18 14E4:4311:1377:103C.5.conf
lrwxrwxrwx 1 root root     26 2010-01-20 16:18 14E4:4311.5.conf -> 14E4:4311:1363:103C.5.conf
-rw-r--r-- 1 root root    961 2010-01-20 16:18 14E4:4312:135F:103C.5.conf
-rw-r--r-- 1 root root    961 2010-01-20 16:18 14E4:4312:1360:103C.5.conf
-rw-r--r-- 1 root root    961 2010-01-20 16:18 14E4:4312:1361:103C.5.conf
-rw-r--r-- 1 root root    961 2010-01-20 16:18 14E4:4312:1362:103C.5.conf
-rw-r--r-- 1 root root    961 2010-01-20 16:18 14E4:4312:1370:103C.5.conf
-rw-r--r-- 1 root root    961 2010-01-20 16:18 14E4:4312:1371:103C.5.conf
-rw-r--r-- 1 root root    961 2010-01-20 16:18 14E4:4312:1372:103C.5.conf
-rw-r--r-- 1 root root    961 2010-01-20 16:18 14E4:4312:1373:103C.5.conf
lrwxrwxrwx 1 root root     26 2010-01-20 16:18 14E4:4312.5.conf -> 14E4:4312:135F:103C.5.conf
-rw-r--r-- 1 root root    901 2010-01-20 16:18 14E4:4318:1355:103C.5.conf
-rw-r--r-- 1 root root    901 2010-01-20 16:18 14E4:4318:1356:103C.5.conf
-rw-r--r-- 1 root root    901 2010-01-20 16:18 14E4:4318:1357:103C.5.conf
lrwxrwxrwx 1 root root     26 2010-01-20 16:18 14E4:4318.5.conf -> 14E4:4318:1355:103C.5.conf
-rw-r--r-- 1 root root    957 2010-01-20 16:18 14E4:4319:1358:103C.5.conf
-rw-r--r-- 1 root root    957 2010-01-20 16:18 14E4:4319:1359:103C.5.conf
-rw-r--r-- 1 root root    957 2010-01-20 16:18 14E4:4319:135A:103C.5.conf
lrwxrwxrwx 1 root root     26 2010-01-20 16:18 14E4:4319.5.conf -> 14E4:4319:1358:103C.5.conf
-rw-r--r-- 1 root root    901 2010-01-20 16:18 14E4:4320:00E7:0E11.5.conf
-rw-r--r-- 1 root root    924 2010-01-20 16:18 14E4:4320:12F4:103C.5.conf
-rw-r--r-- 1 root root    901 2010-01-20 16:18 14E4:4320:12F8:103C.5.conf
-rw-r--r-- 1 root root    901 2010-01-20 16:18 14E4:4320:12FA:103C.5.conf
-rw-r--r-- 1 root root    901 2010-01-20 16:18 14E4:4320:12FB:103C.5.conf
lrwxrwxrwx 1 root root     26 2010-01-20 16:18 14E4:4320.5.conf -> 14E4:4320:00E7:0E11.5.conf
-rw-r--r-- 1 root root    957 2010-01-20 16:18 14E4:4324:12F9:103C.5.conf
-rw-r--r-- 1 root root    957 2010-01-20 16:18 14E4:4324:12FC:103C.5.conf
lrwxrwxrwx 1 root root     26 2010-01-20 16:18 14E4:4324.5.conf -> 14E4:4324:12F9:103C.5.conf
-rw-r--r-- 1 root root    961 2010-01-20 16:18 14E4:4328:1366:103C.5.conf
-rw-r--r-- 1 root root    961 2010-01-20 16:18 14E4:4328:1367:103C.5.conf
-rw-r--r-- 1 root root    961 2010-01-20 16:18 14E4:4328:1368:103C.5.conf
-rw-r--r-- 1 root root    961 2010-01-20 16:18 14E4:4328:1369:103C.5.conf
lrwxrwxrwx 1 root root     26 2010-01-20 16:18 14E4:4328.5.conf -> 14E4:4328:1366:103C.5.conf
-rw-r--r-- 1 root root 811278 2010-01-20 16:18 bcmwl5.inf
-rw-r--r-- 1 root root 604928 2010-01-20 16:18 bcmwl5.sys

---

### Post by northd_tech on 2010-02-20
Hi jesjep.

This guide is really old (as is Hardy Heron).  The newer versions of Ubuntu have better support for Broadcom wireless.  There are proprietary hardware drivers that work with many of the Broadcom chips.  Can you go into System > Administration > Hardware Drivers and see anything related to "Broadcom"?

As I recall, the 4318 probably needs the "b43" driver, but I'm not 100% certain on that.

---

### Post by Prakash B H on 2010-04-02
Thanks a lot..
It helped me in getting my wireless connection., for which i was struggling from days.
Thanks again..

---

### Post by peeterparker on 2010-04-17
I am still unable to configure wireless on my laptop.

I am very new to ubuntu, used Win7 earlier.
I followed your steps but unable to see the network getting connected.


I don't see any driver for Broadcomm under System> Admin > Hardware Drivers
Any pointers please!!!!
Please help!!!

---

### Post by Ayuthia on 2010-04-19
> **peeterparker said:**
> I am still unable to configure wireless on my laptop.

I am very new to ubuntu, used Win7 earlier.
I followed your steps but unable to see the network getting connected.


I don't see any driver for Broadcomm under System> Admin > Hardware Drivers
Any pointers please!!!!
Please help!!!

You might try installing b43-fwcutter (open source) or bcmwl-kernel-source (proprietary).  It should work the same as Hardware Drivers.

---

### Post by peeterparker on 2010-04-19
I am so sorry to ask a n00b question.

Where is the link as when I browse [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) webpage... I couldn't find a link where I could save the driver onto my desktop.

---

### Post by Ayuthia on 2010-04-20
> **peeterparker said:**
> I am so sorry to ask a n00b question.

Where is the link as when I browse [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) webpage... I couldn't find a link where I could save the driver onto my desktop.

You might be better off trying to install the b43-fwcutter application from Synaptic first.  The link that you are looking at contains the most recent source code for various wireless drivers.  However the link that you are wanting is located in the "Directly downloading the tarball" section about less than halfway down on the page.  If you click on it, it should download to your Downloads folder.

If you do want to install b43-fwcutter from the Terminal:
```
sudo apt-get update
sudo apt-get install b43-fwcutter

```

---

### Post by Rhemat on 2010-04-20
I enabled the restricted drivers for my Broadcom in Xubuntu 8.10.  The deal was that the restricted drivers are blacklisted right from a fresh install, but still visible in the "Restricted Drivers Repository."  I'm still wondering why they were blacklisted, because they work just fine.
Hopefully they fixed that in the newer versions so no one has to deal with the Windows drivers any more.

---

### Post by doodude on 2010-05-23
Thank you so much! after hours of trying to get the adapter working, your process did it.

---

### Post by tester321 on 2010-05-29
To the thread author THANK YOU, this worked perfectly on a brand new emachines 250-1162 Netbook.

(Why install Hardy and not Intrepid this late in the game?  Because I want to run VMware Server 1.x ... and though Intrepid recognizes all its hardware upon install, it is MUCH more difficult getting VMware 1.x running on Hardy than going this route.  Why VMware 1.x and not 2.x? Should be self explanatory, LOL).

Now have the best of all worlds (for me) for a tiny road warrior setup:
small form factor Netbook w/ 2GB RAM
250GB HD
LUKS Encryption 
Ubuntu
VMware 1.x
Windoze as a guest VM
 
Cheers!!
:guitar:

---

### Post by fslezak on 2010-06-07
Not working for me and my Broadcom B4306 Revision 3.

Any Suggestions?

---

### Post by sirhc1004 on 2010-09-23
I LOVE YOU!
I have been trying to get a wifi connection for WEEKS!
I got wifi on my: (using "lspci" command in terminal)
"01:06.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)"

The physical PCI card says that it is a BCM4301, but this worked. 

THANKS AGAIN!!

---

### Post by chewcudda on 2010-10-03
ok i need help. been banging my head again the wall on this one for about 5 hours now. 

using broadcom bcm9431bmpg in a compaq presario v5000

ok not really mine helping out a neighbor but I digress....

I ran the live cd and it gave me the you are using proprietary drivers message. I said great i can now install knowing that wireless will work. 

I install....now when I got to the driver window it lists nothing and I still cannot get a wireless connection. everything I see on the forums is about hardy with this issue but I have karmic to install. 

I ram the commands in the orginal post and every thing looks good it just does not seem to see the proprietary drivers if I boot from the HDD.

and suggestions and or help is greatly appreciated

chewy

---

### Post by tinfoilhat on 2011-04-24
hellz yeah...worked like a charm.  That's a brutal slog to get up and running with no network connections and a Windoze box to work from, but had no issues once i collected the pieces.
 
Thanks!
 
:guitar:

---

### Post by drguitar on 2011-05-09
This is very nicely done.  Even a Linux newbie like myself was able follow the directions and get my wireless up and running.  The confusing thing was that the wireless hardware in my notebook (Broadcom BCM4306 rev. 2) is supposed to work with the b43 legacy drivers... but it does not.  The best those drivers did was allow my computer to see that there was a wireless nearby... it just would not connect.  

After a week of trying to set it up, I found this post and was up and running in a half an hour.  Much Thanks!!!  :P:P:P

---

### Post by medusa569 on 2011-05-30
Many many thanks for finally getting my card recognized  !  After so many pages of useless frustrating info.  One problem...first my wireless is acknowledged on wlan1 and no wlan0....this may have something to do with why I can't connect??
I have my key WEP key right..so why does the attempted connection just keep trying with no success??  My router is about 4 feet to my right so the signal should come through..and to my knowledge there is no security program in ubuntu blocking it.

Any thoughts??  thanks in advance.

ps why does my wireless connection always start in network manager as disabled?

---

### Post by Seventh Sev on 2011-06-13
Edit:

Not sure what happened, just started it up, and there was the wireless settings, it worked!!! Thank you!

Original:

Hi, I didn't realize this thread was so long, and I ended up following the initial steps, which resulted in the wireless option disappearing altogether... has anyone else had this experience, or know how to fix it?

---

### Post by medusa569 on 2011-06-30
I really liked your step by step but despite following your way and other posters I can't get a connection. 
I see only one wireless network (no other in the area) an it acts like its trying to connect but doesn't. I have no antivirus and I'm totally frustrated now.  Any help would be appreciated.

medusa

---

### Post by vjola on 2011-10-25
> **alex_kent_18 said:**
> I used the following steps to enable my _*Broadcom Wireless BCM4312 (rev 02)*_.

**Step 1 (run in terminal)**

[COLOR=Blue]echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx[/COLOR]

[COLOR=Red]**For Step 2, You can check your Broadcom wireless version with this command in terminal : [B][COLOR=Red]"_*lspci | grep Broadcom\ Corporation*_"[/COLOR]**,if your wireless device is different from BCM4312 (rev 02), please refer to the following link for this step and you can continue again with step 3 onwards:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)[/B][/COLOR]


**Step 2 (run in terminal)**

[COLOR=Blue]sudo apt-get install cabextract
wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
cabextract sp34152.exe[/COLOR]

**Step 3 (run in terminal)**

[COLOR=Blue]sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant[/COLOR]

**Step 4  (run in terminal)**

[COLOR=Blue]sudo aptitude remove b43-fwcutter[/COLOR]

**Step 5  (run in terminal)**

[COLOR=Blue]sudo gedit /etc/init.d/wirelessfix.sh[/COLOR]

**Step 6**

Paste the followings in the opened file(wirelessfix.sh)and **make sure you save it before continuing Step 7**

[COLOR=Blue]#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
[/COLOR]
**Step 7  (run in terminal)**

Run this :

[COLOR=Blue]cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh[/COLOR]

**Step 8  (run in terminal)**

finally run this:

[COLOR=Blue]sudo update-rc.d wirelessfix.sh defaults [/COLOR]

**Step 9**

[COLOR=Blue]Restart your machine[/COLOR] and enjoy the freedom from those wires....





i am sorry, but i do all these thing, it gives me problems like : 
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Reading extended state information       
Initializing package states... Fatto
Couldn't find any package whose name or description matched "b43-fwcutter"
Couldn't find any package whose name or description matched "b43-fwcutter"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Reading extended state information       
Initializing package states... Fatto
viola@viola-laptop:~$ sudo aptitude remove b44-fwcutter
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Reading extended state information       
Initializing package states... Fatto
Couldn't find any package whose name or description matched "b44-fwcutter"
Couldn't find any package whose name or description matched "b44-fwcutter"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Reading extended state information       
Initializing package states... Fatto
viola@viola-laptop:~$ sudo aptitude remove b45-fwcutter
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Reading extended state information       
Initializing package states... Fatto
Couldn't find any package whose name or description matched "b45-fwcutter"
Couldn't find any package whose name or description matched "b45-fwcutter"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Reading extended state information       
Initializing package states... Fatto
viola@viola-laptop:~$ sudo gedit /etc/init.d/wirelessfix.sh
viola@viola-laptop:~$ cd /etc/init.d/&& sudo chmod 755 wirelessfix.sh
viola@viola-laptop:/etc/init.d$ sudo update-rc.d wirelessfix.sh defaults
update-rc.d: warning: /etc/init.d/wirelessfix.sh missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/wirelessfix.sh already exist.
viola@viola-laptop:/etc/init.d$viola@viola-laptop:~$ sudo iwconfig wlan0
[sudo] password for viola: 
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
viola@viola-laptop:~$ echo 'blacklist bcm43xx'| sudo tee -a /etc/modprobe.d/blcalist sudo apt-get install ndiswrapper-
utils-1.9 mkdir /bcm43xx; cd /bcm43xx
blacklist bcm43xx
bash: cd: /bcm43xx: Not a directory
viola@viola-laptop:~$ sudo apt-get install cabextract wget [ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe)
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
E: Impossibile trovare il pacchetto cabextract
viola@viola-laptop:~$ sudo ndiswrapper -i bcmwl5.inf ndiswrapper -l sudo depmond -a sudo modprobe nidswrapper 
sudo cp /etc/network/interfaces /etc/network/interfaces.orig echo -e 'auto lo\niface lo inet loopback\n'| sudo tee 
/etc/network/interfaces sudo ndiswrapper -m echo 'nidswrapper'| sudo tee -a/etc/modules echo 'ENABLED=0'| sudo tee 
-a/etc/default/wpasupplicant
sudo: ndiswrapper: command not found
[sudo] password for viola: [sudo] password for viola: tee: invalid option -- '/'
Try `tee --help' for more information.
Sorry, try again.
[sudo] password for viola: 
tee: invalid option -- '/'
Try `tee --help' for more information.
Sorry, try again.
[sudo] password for viola: 
tee: invalid option -- 'm'
Try `tee --help' for more information.
viola@viola-laptop:~$ sudo ndiswrapper -i bcmwl5.inf ndiswrapper -l sudo depmond -a sudo modprobe nidswrapper 
sudo cp /etc/network/interfaces /etc/network/interfaces.orig echo -e 'auto lo/niface lo inet loopback/n'| sudo tee 
/etc/network/interfaces sudo ndiswrapper -m echo 'nidswrapper'| sudo tee -a/etc/modules echo 'ENABLED=0'| sudo tee 
-a/etc/default/wpasupplicant
sudo: ndiswrapper: command not found
tee: invalid option -- '/'
Try `tee --help' for more information.
tee: invalid option -- 'm'
Try `tee --help' for more information.
tee: invalid option -- '/'
Try `tee --help' for more information.
viola@viola-laptop:~$ sudo ndiswrapper -i bcmwl5.inf ndiswrapper -l sudo depmond -a sudo modprobe nidswrapper 
sudo cp /etc/network/interfaces /etc/network/interfaces.orig echo -e 'auto lo\niface lo inet loopback\n'| sudo tee 
/etc/network/interfaces sudo ndiswrapper -m echo 'nidswrapper'| sudo tee -a/etc/modules echo 'ENABLED=0'| sudo tee 
-a/etc/default/wpasupplicant
sudo: ndiswrapper: command not found
tee: invalid option -- '/'
Try `tee --help' for more information.
tee: invalid option -- 'm'
tee: invalid option -- '/'
Try `tee --help' for more information.
Try `tee --help' for more information.
viola@viola-laptop:~$ sudo aptitude remove b43-fwcutter
Lettura elenco dei pacchetti... Fatto




help me please!!!!!

---

### Post by brad1138 on 2012-05-20
After spending ~10 hours, reading a LOT of the how to's on fixing wireless on Compaq V5000. I found the (an) answer, which is a combo of this thread and a few other fixes, I thought I would wrap it all up. This worked on Ubuntu 12.04, I will be testing it on some other current releases soon (debian, Mint, Xubuntu)


Step #1 Make sure the wireless driver in "additional drivers" is **not** activated.

Step #2 Install ndiswrapper from Synaptic Package Manager. Type "ndis" in the search bar and install all 5 packages that start "ndis" (excluding ndisc6 - in my case anyway). Installing ndiswrapper-dkms solves a bug (discussed [**here**]("https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/986064?comments=all"))

Step #3 Run "lspci | grep Broadcom\ Corporation" in terminal to determin your wireless adapted model #. Then find appropriate .exe [**here**]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851"). Look for "Step 2: Download and Extract Drivers", about 3/4 of way down page. Create a new folder in your home directory (name it whatever you want), download and extract into that. Extract by double-clicking file and selecting extract.

Step #4 Type "sudo apt-get install firmware-b43-installer b43-fwcutter" in terminal. This fixes another bug where firmware doesn't get installed (discussed [**here**]("http://askubuntu.com/questions/88854/firmware-missing-for-broadcom-802-11b-g-adapter")).

Step #5 Run ndiswrapper from launcher (labeled "Windows wireless drivers" on my system) and click "install new driver" - select the .inf file from the extracted .exe you created in step #3

Step #6 Reboot (not sure if this is needed but can't hurt)

That should do it. I actually did steps 4 & 5 in reverse order, as soon as I finished step 4, I had wireless, no reboot needed. I think the steps as I listed above are the better way to do it though. So if there is anyone still using a V5000 laptop, I hope this helps. 

Brad

P.S. I know these instructions are usually given completely with terminal commands. I like using the GUI when I can and that is how it worked for me.

---

### Post by Bucky Ball on 2012-05-20
```
sudo apt-get install firmware-b43-installer b43-fwcutter
```... should be all that is required in 12.04 LTS. It is all that is required in 10.04 LTS. ndiswrapper is  superseded for most Broadcom cards.

@Brad: From your link:

> But as soon as **loading a windows *.inf driver** file in the ndisgtk program it show the following popup messageIf you are using a Broadcom card and the B43 drivers/firmware you wouldn't be 'loading a windows *.inf driver' so ... ndiswrapper is intended for that purpose and this is what was required three or four years ago before the B43 setup arrived. I would try without step #2 and frankly, I would also activate B43 via 'Additional Drivers' if available there (might need to connect with a cable and do an update before it is). ;)

---

### Post by chili555 on 2012-05-20
> Step #2 Install ndiswrapper from Synaptic Package Manager. Type "ndis" in the search bar and install all 5 packages that start "ndis" (excluding ndisc6 - in my case anyway). Installing ndiswrapper-dkms solves a bug (discussed here)

Step #3 Run "lspci | grep Broadcom\ Corporation" in terminal to determin your wireless adapted model #. Then find appropriate .exe here. Look for "Step 2: Download and Extract Drivers", about 3/4 of way down page. Create a new folder in your home directory (name it whatever you want), download and extract into that. Extract by double-clicking file and selecting extract.

Step #4 Type "sudo apt-get install firmware-b43-installer b43-fwcutter" in terminal. This fixes another bug where firmware doesn't get installed (discussed here).
There is no need for ndiswrapper for almost any Broadcom card.

---

### Post by brad1138 on 2012-05-20
> **Bucky Ball said:**
> ```
sudo apt-get install firmware-b43-installer b43-fwcutter
```... should be all that is required in 12.04 LTS. It is all that is required in 10.04 LTS. ndiswrapper is  superseded for most Broadcom cards.

@Brad: From your link:



If you are using the B43 drivers/firmware you wouldn't be 'loading a windows *.inf driver' so ...

OK, I'll test that also. I only found that as a fix for the problem my link pointed to. But if you are correct, I wasted a lot of time... :(

---

### Post by brad1138 on 2012-05-20
> **brad1138 said:**
> OK, I'll test that also. I only found that as a fix for the problem my link pointed to. But if you are correct, I wasted a lot of time... :(

Well, when I removed the driver through ndiswrapper and rebooted I lost wireless. I ran "sudo apt-get install firmware-b43-installer b43-fwcutter" again and still nothing. When I re-installed the .inf through ndiswrapper my wireless came back instantly. It seems I need both installed. I know that you shouldn't (or can't) have 2 drivers installed, but apparently I do. I didn't think "firmware" was the same as a "driver".

---

### Post by jpeddicord on 2012-05-20
Hi all,

This thread is very old. As the wireless driver situation is constantly changing, following the advice on this thread in more recent versions of Ubuntu may only lead to frustration. I'm going to close this thread; if you have your own wireless issues feel free to create a new thread.

If you feel this was closed in error, please post in Forum Feedback & Help.

Thanks!
Jacob

---

