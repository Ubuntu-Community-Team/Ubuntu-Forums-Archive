---
title: "HOWTO: RaLink rt61 chipset install in Gutsy"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by RebounD11 on 2007-11-28
Easier than it was done here [http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980). It worked for me, I hope it does so for you.

First you need to download this archive: rt61-cvs-daily.tar.gz, from [here]("http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz").

After you've done that you need to untar the archive somewhere and cd to the newly created directory. 

Then do this:
```

make all
sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/.
sudo depmod -a
sudo modprobe rt61

```

And after you reboot, to check if your wireless driver was loaded:

```

iwconfig

```

As you can see the steps don't differ from the howto I've mentioned above, only that some are skipped. The rest of the configuration can be done the same as there. It worked for me, let me know if it works for you too.

EDIT: Thanx to Mr. Arne for pointing out the fact that after you cd to the newly created directory (at the beginning of the tutorial) you have to also cd to the Module sub-directory.
EDIT2: Also would like to add that if it doesn't after reboot, you should blacklist the rt61pci module first. You can do that like this:

```

sudo gedit /etc/modprobe.d/blacklist

```

and add this:

```

blacklist rt61pci

```

at the end of the file.

then repeat:

```

sudo depmod -a
sudo modprobe rt61

```

and reboot. And now it should work, at least it did for me.

---

### Post by wieman01 on 2007-11-29
Looks like a promosing guide. Does that driver support WPA as well? How about Network Manager? Would be great if you let me know, so I can include the link in my own tutorial if you don't mind.

---

### Post by Mr_Arne on 2007-12-01
Hi, I tried this guide tonight. Easy install, just note that you have to cd to subfolder /Module in the newly created folder before "make all".
And it works great with static IP, manually configured. The roaming state is not working, it seems that WPA and WPA2 is possible (haven't tried yet, must reconfigure the router in that case, maybe tomorrow (sigh)), but WEP is running good.

/ola

---

### Post by RebounD11 on 2007-12-02
> **Mr_Arne said:**
> Hi, I tried this guide tonight. Easy install, just note that you have to cd to subfolder /Module in the newly created folder before "make all".
And it works great with static IP, manually configured. The roaming state is not working, it seems that WPA and WPA2 is possible (haven't tried yet, must reconfigure the router in that case, maybe tomorrow (sigh)), but WEP is running good.

/ola

Thanks for pointing that out I'll edit as soon as I get the chance :D

> 
Looks like a promosing guide. Does that driver support WPA as well? How about Network Manager? Would be great if you let me know, so I can include the link in my own tutorial if you don't mind.

I don't mind :D. And I haven't yet tried WPA but I will as soon as I can. As for the network manager - I've never used it for wireless. Right after installation, the network manager saw all wireless networks as having 60% signal strength, and I could get my wireless card into monitor mode, more it said that the driver and the chipset are unknown. After compiling and loading the new kernel module, network manager saw a few more networks only everyone of them showed 0 % signal strength. however I succeeded in getting my wireless card into monitor mode, and I could connect to my router this time as well... I used WEP encryption, and now the I gave the router to my parents (my mom got a new laptop - with wireless and she is now sharing the internet connection with my dad, I'm on campus so I only need a switch to share my internet connection with my girlfriend) so I can't try WPA right away, but maybe Mr. Arne can do that faster if he would be so kind :D.

---

### Post by Mr_Arne on 2007-12-02
...and how kind could a man be...? As me of course, my humbleness is almost without limits :mrgreen:

All my attempts with WPA is so far negative; WPA Personal tested with TKIP and later AES. WPA2 personal with TKIP+AES, no one is working. Is the encryption managed by the driver itself or is it the package named wpasupplicant who is doing the (poor) job? Maybe one should try the package named xsupplicant instead? Anyone who has already?
And I guess the difference between say WICD and Gnome network manager has quite little to do with it...

From a kind one ;)

/ola

---

### Post by RebounD11 on 2007-12-02
> **Mr_Arne said:**
> From a kind one ;)

:lolflag:

---

### Post by dolphin_oracle on 2007-12-02
I've been using an RT61 for a while now.  The driver from ralink manages wpa security itself.  You can specify settings in a file called RT61STA as specified in the readme that comes with the driver.  You can also use iwpriv commands to set parameters directly in the interfaces file.  I'm on the wrong computer at the moment, so I can't paste the information in here.

By the by, wpa and RT61 will not work together through network manager.  You also don't need WPAsupplicant for the reasons above.

If you find the howto for edgy, it works exactly the same in Gutsy.  only feisty and dapper were different.

---

### Post by RebounD11 on 2007-12-03
> **dolphin_oracle said:**
> I've been using an RT61 for a while now.  The driver from ralink manages wpa security itself.  You can specify settings in a file called RT61STA as specified in the readme that comes with the driver.  You can also use iwpriv commands to set parameters directly in the interfaces file.  I'm on the wrong computer at the moment, so I can't paste the information in here.

By the by, wpa and RT61 will not work together through network manager.  You also don't need WPAsupplicant for the reasons above.

If you find the howto for edgy, it works exactly the same in Gutsy.  only feisty and dapper were different.

The driver you speak of not only it didn't work for me, but it also had the side-effect that Ubuntu didn't even see my wireless card as part of the system, if I was holding it in my hand would have been the same thing as having it in my computer. The default drivers, the ones that come when you install Ubuntu at least recognized my card, I couldn't connect to anything, but the card was present within Ubuntu, not only inside the computer case.

---

### Post by dolphin_oracle on 2007-12-03
> The driver you speak of not only it didn't work for me, but it also had the side-effect that Ubuntu didn't even see my wireless card as part of the system, if I was holding it in my hand would have been the same thing as having it in my computer. The default drivers, the ones that come when you install Ubuntu at least recognized my card, I couldn't connect to anything, but the card was present within Ubuntu, not only inside the computer case.

Did you copy the firmware files (*.bin) to /etc/Wireless/RT61STA ?

I actually didn't notice you guys are trying at the serial monkey drivers.  Since they are enchanced Ralink drivers, they actually configure via iwpriv the same way as the ralink ones.  WPA is handled by the driver, and its actually stated as incompatible with WPA Supplicant in the driver readme file included in the tarball.

Out of curiosity, do your rt61 show up as wlan0 or ra0?

---

### Post by RebounD11 on 2007-12-03
Yes I did copy the firmware files I did everything in the Readme and when that didn't work I tried variations. Still didn't work for me.

As for your second question, my rt61 is shown as wlan0.

---

### Post by Mr_Arne on 2007-12-03
Hi,
My rt61 is also shown as wlan0, in opposition to the long gone times when I struggled with Efty, and followed this howto:
[http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)
At that state, I didn't care about WPA (was pleased with WEP), and I got it to work at 1st attempt, and the card showed up as ra0 in that configuration. I can do some firmware copying in accordance to the readme file and see if works for me some evening in the week (silly question maybe, but where do I find the firmware files to copy...?). One thing about this that I don't like is that we are now going towards the common text mode methods usable when nothing else works in Linux, and I always try to benchmark the graphic tools to see whether if Linux truly can compete with Windows (for the vast majority of plug and players...). I think it's such a pity that some of these fundamental demands not yet is possible to fulfill. But we strive and we strive, huh...? :)

To be continued

/ola

---

### Post by dolphin_oracle on 2007-12-03
> **Mr_Arne said:**
> Hi,
My rt61 is also shown as wlan0, in opposition to the long gone times when I struggled with Efty, and followed this howto:
[http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)
At that state, I didn't care about WPA (was pleased with WEP), and I got it to work at 1st attempt, and the card showed up as ra0 in that configuration. I can do some firmware copying in accordance to the readme file and see if works for me some evening in the week (silly question maybe, but where do I find the firmware files to copy...?). One thing about this that I don't like is that we are now going towards the common text mode methods usable when nothing else works in Linux, and I always try to benchmark the graphic tools to see whether if Linux truly can compete with Windows (for the vast majority of plug and players...). I think it's such a pity that some of these fundamental demands not yet is possible to fulfill. But we strive and we strive, huh...? :)

To be continued

/ola

Mr_Arne, you are quite eloquent.  I too have been with an RT61 since edgy.

I wish you good luck in finding graphical tools that will play with RT61s.  I have not as most assume WPA_supplicant for wpa duties and RT61's handle WPA themselves (even serial monkeys').  My current Feisty setup is the first one where I haven't needed to use a configuration file, I'm using the iwpriv commands.

As for firmware files, they should be in the Module directory where the Makefile information is stored.  

**edit** I just checked the tarball, and the *.bin files are in there (3 I think).

---

### Post by Mr_Arne on 2007-12-03
> Mr_Arne, you are quite eloquent.
...My humble thanks :redface:

I hope that time and devoted developers will work for rt61 compa- and usability, so with a little patience maybe we get what we're longing for - if rt61 isn't a dead end of course...! I think I'll try to learn a bit more about the iwpriv commands. Is it maybe a good idea to disable wpasupplicant to avoid possible conflicts?

Coming back some day will

/ola

---

### Post by dolphin_oracle on 2007-12-03
As promised, my /etc/network/interfaces file (edited of course)

auto ra0
iface ra0 inet dhcp
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid myessid
pre-up iwpriv ra0 set WPAPSK=myphrase

---

### Post by brodiepearce on 2007-12-04
RT61 is working out of the box with Gutsy for me, WPA2PSK is even working with network manager.  However, it has a tendency to spontaneously drop out if several things are using the connection.  (E.g. uTorrent + IRC/SSH).  It's odd that it's working for some but not for others, I think there are also one of two people on these forums that have RT61 with WPA and Network Manager working with no problems/drop-outs whatsoever.  :(

---

### Post by wieman01 on 2007-12-04
> **brodiepearce said:**
> RT61 is working out of the box with Gutsy for me, WPA2PSK is even working with network manager.  However, it has a tendency to spontaneously drop out if several things are using the connection.  (E.g. uTorrent + IRC/SSH).  It's odd that it's working for some but not for others, I think there are also one of two people on these forums that have RT61 with WPA and Network Manager working with no problems/drop-outs whatsoever.  :(
Well, I have heard from others that it works for them as well. But these are the ones who installed Gutsy recently, so apparently there has been a change. But they also confirm the driver isn't very stable and they face dropping connections a lot.

---

### Post by brodiepearce on 2007-12-04
> **wieman01 said:**
> Well, I have heard from others that it works for them as well. But these are the ones who installed Gutsy recently, so apparently there has been a change. But they also confirm the driver isn't very stable and they face dropping connections a lot.

I installed Wicd last night (and consequently uninstalled Network-manager), will try it out for the next few days (holding off on torrents till the average quota catches up with me :P) and see how it goes.  I believe it uses WPA_Supplicant (wext driver is selected) instead of directly using the serialmonkey driver as the Network-manager does.

---

### Post by RebounD11 on 2007-12-04
With Gutsy's defaults I couldn't do anything with my wireless, just see the other wireless devices in my area. With serial-monkey's drivers I can use aircrack and "crack" those networks... I can't see the signal strength in network selector, but I can see it with iwconfig, and I can configure the connection the same way... and it works 24/7 no glitches. 

PS: this wireless card didn't work at all with Vista and with XP it works for half an hour when you have to restart (disable/re-enable) it (my dad has an identical one - that's how I know). The tutorial I posted here was the only way I could get my wireless to do sth other than list available networks and show their (inaccurate) signal strength.

PPS: My card is Ovislink Airlive WT2000PCI... the Windows XP driversare made of a setup.exe which installs a malfunctioning wireless manager (under XP) along with the actual drivers, so using ndiswrapper is not an option. If anybody knows of another way to get full functionality out of it or at least a GUI way to connect to a wireless network, and not just see if I'm connected or not.

---

### Post by wieman01 on 2007-12-05
> **brodiepearce said:**
> I installed Wicd last night (and consequently uninstalled Network-manager), will try it out for the next few days (holding off on torrents till the average quota catches up with me :P) and see how it goes.  I believe it uses WPA_Supplicant (wext driver is selected) instead of directly using the serialmonkey driver as the Network-manager does.
As Ralink drivers do not support 'wext' and hence the use of "wpa-supplicant", WICD does not having an option. So I believe they have implemented a second interfaces that supports Ralink (or plan to do so).

---

### Post by ZenX on 2008-01-24
Hmmh, doesn't work with my D-Link DWL G-630 card.. Everything installs well, i can see the card in Network Manager, and when I try to open up Firefox and go to any site, it just pops open the " Page cannot be displayed" -error.

lspci says: 03:00.0 Network controller : RaLink RT2561/RT61 rev B 802.11g

:(

---

### Post by wieman01 on 2008-01-24
What about:
> ping [www.google.com](www.google.com)
Do you get a response?

---

### Post by ZenX on 2008-01-26
Nope, it says : unknown host google.com

Even when I try to ping the router / wlan box, it always says that Destination Host Unreachable. I have tried installing the RaLink drivers too, but with little success. Although when I started up my laptop, it popped open a window saying "New Restricted drivers in use.". So it appears that the installation was at least somewhat succesful.

---

### Post by dolphin_oracle on 2008-01-26
zenx,

did you copy the firmware (*.bin) files to the default firmware directory (/lib/firmware, it think.)  
without the firmware files, the module will still load, but it won't drive the card.

---

### Post by ZenX on 2008-01-27
I got the card working now, but found out that the reason it wasn't working was that my father had changed our ESSID, and so the card didn't work :D :lolflag:  Thanks everyone for trying to help:-\"

---

### Post by sunseeker888 on 2008-02-12
> **RebounD11 said:**
> Easier than it was done here [http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980). It worked for me, I hope it does so for you.

First you need to download this archive: rt61-cvs-daily.tar.gz, from [here]("http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz").

After you've done that you need to untar the archive somewhere and cd to the newly created directory. 

Then do this:
```

make all
sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/.
sudo depmod -a
sudo modprobe rt61

```

And after you reboot, to check if your wireless driver was loaded:

```

iwconfig

```

As you can see the steps don't differ from the howto I've mentioned above, only that some are skipped. The rest of the configuration can be done the same as there. It worked for me, let me know if it works for you too.

EDIT: Thanx to Mr. Arne for pointing out the fact that after you cd to the newly created directory (at the beginning of the tutorial) you have to also cd to the Module sub-directory.
EDIT2: Also would like to add that if it doesn't after reboot, you should blacklist the rt61pci module first. You can do that like this:

```

sudo gedit /etc/modprobe.d/blacklist

```

and add this:

```

blacklist rt61pci

```

at the end of the file.

then repeat:

```

sudo depmod -a
sudo modprobe rt61

```

and reboot. And now it should work, at least it did for me.





HI I am a newbie, I have followed your steps, download the tar files,  untar the files etc

cd modules

make all, ok
sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/.           (ok)

make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
*** Module rt61.ko built successfully






when I do 
sudo depmod -a


I get this 

WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.22-14-generic/kernel/drivers/net/rt61.ko



Please help


:confused:

---

### Post by sunseeker888 on 2008-02-12
lspci

03:05.0 Network controller: RaLink RT2561/RT61 802.11g PCI




But the green light is no longer on. :(

---

### Post by thamane on 2008-02-24
Thank you !

I did a fresh install of Gutsy today. My card was recognized, but the built-in driver did not work. I had uninstalled network-manager manually and had configured the card in the /etc/network/interfaces before following your tutorial.

My wireless card seems to work fine now. I got a warning in the make all process that the module created was too big, but I went ahead anyway and this doesn't seem to be a problem.

I think it might be of help to explain the 'uname -r', just in case ...

My system :
Athlon64 X2 4200+
ASUS M2N-E
D-Link AirPlus G DWL-G510  Rev C2 (Firmware Version 5.00) 
Chipset RT61 rev. B

Our network uses WEP and a hidden ESSID.
The card shows up as wlan0.
I have a wmaster showing up that should be hidden I read somewhere else.
I did have to blacklist the rt61pci driver and reboot before it would work.

Thanks again, and greetings from Paris,
thamane

---

