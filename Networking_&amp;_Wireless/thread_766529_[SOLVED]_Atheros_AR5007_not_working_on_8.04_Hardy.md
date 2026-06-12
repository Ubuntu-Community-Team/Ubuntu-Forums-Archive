---
title: "[SOLVED] Atheros AR5007 not working on 8.04 Hardy"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by jdv1800 on 2008-04-25
I have an Atheros AR5007 wireless network adapter that isn't turning on with Hardy 8.04. There is one of those unsupported drivers that shows up in system. Any ideas?

---

### Post by ToM-X on 2008-04-25
I'm working on Atheros AR5007EG, I'l get back to you if I get anywhere.

Same situation I bet.

---

### Post by Farivan on 2008-04-25
I'm having the same problem, and as an absolute new-comer to ubuntu I'd appreciate any advice anyone could offer...

---

### Post by ophion on 2008-04-25
I have the same problem on an Asus F3KA-A1 notebook (AR5007EG).

---

### Post by ophion on 2008-04-25
There is a lot of information on the problem at the URL below.  Things do not look promising for those running 64-bit systems.

[http://madwifi.org/ticket/1679]("http://madwifi.org/ticket/1679")

---

### Post by IndyGunFreak on 2008-04-25
I just setup my AR5007EG... Here's how I got it working in Gutsy, and it worked just fine in Hardy also, with some minor modifications... 

[http://ubuntuforums.org/showthread.php?t=680209](http://ubuntuforums.org/showthread.php?t=680209)


For what its worth, my device is a AR5007EG, but it is misdetected as 

```
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
``` 


I went to Hardware drivers, and disabled HAL, but left "Support for Atheros 802.11 wireless Lan cards" enabled.  This option was never there in Gutsy.  Then I restarted and used the instructions and patch for the madwifi driver in the link above, and plugged in my network settings.  Works fine w/ WPA, etc.

Edit:  As mentioned, Not sure how this will work on 64bit, it worked fine on 32bit.  Laptop is a Acer Aspire 5315-2153

IGF

---

### Post by ToM-X on 2008-04-25
Right, I'm back now like I promised.

**Atheros AR5007EG for hardy.**

First of all go to "System/Administration/Hardware Drivers" and disable by un-ticking the box.:

```
Atheros Hardware Access Layor (Hal) 
```

Then Reboot

Then open the terminal "Applications/Accessories/Terminal" and copy the following:

```
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz 
```

```
sudo apt-get install build-essential
```

```
tar xfz madwifi-ng-r2756+ar5007.tar.gz
```

```
cd madwifi-ng-r2756+ar5007
```

```
make
```

```
sudo make install
```

```
sudo modprobe ath_pci
```

```
sudo reboot
```

Then thats it :D Enjoy!

---

### Post by raiwo on 2008-04-25
my atheros 5007 card worked fine with above instructions in gutsy but now its recognized in hardy as AR242x card!?!

04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

And yes, it really is a atheros 5007, not atheros 5006 as gutsy thought or AR242X card as hardy thinks... now I am using ndiswrapper to get wireless as madwifi patch refuses to compile.
:confused:

:(

---

### Post by ToM-X on 2008-04-25
> **raiwo said:**
> my atheros 5007 card worked fine with above instructions in gutsy but now its recognized in hardy as AR242x card!?!

04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

And yes, it really is a atheros 5007, not atheros 5006 as gutsy thought or AR242X card as hardy thinks... now I am using ndiswrapper to get wireless as madwifi patch refuses to compile.
:confused:

:(


What error did you get when trying to compile? and did you disable HAL?

---

### Post by ophion on 2008-04-25
ToM-X, does your procedure work for 64-bit systems?

---

### Post by Pinoy915 on 2008-04-25
This procedure did not work for me. I am running Ubuntu 8.04 AMD64.

---

### Post by IndyGunFreak on 2008-04-25
> **Pinoy915 said:**
> I am running Ubuntu 8.04 AMD64.

Thats probably why.  Read the rest of the thread, I believe someone posted a link that details the issues this device has w/ 64bit.

IGF

---

### Post by major_rocks on 2008-04-25
just curious if tomx is running 64bit hardware and 32bit ubuntu or, 64bit ubuntu on (obviously) 64bit hardware.

Let us know...Please

---

### Post by Pinoy915 on 2008-04-25
Success!!! I have my wireless card working! I am using ndiswrapper with 64 bit drivers. Here is the thread I used to get mine working. [http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

Here are the only steps I used. I did not disable anything in the restricted drivers menu.

Go to System/Administration/Hardware Drivers. Disable the default drivers by unchecking "Atheros Hardware Access Layer(HAL)" and "Support for Atheros 802.11 Wireless LAN cards." Reboot if necessary.

Blacklist the default driver:

```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

Get the 64 bit driver:
```
wget http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz
```

Extract driver:
```
tar xvf ar5007eg-*.tar.gz
tar xvf ndiswrapper-newest.tar.gz
```

Ensure you have your kernel headers and the build essential package.
```
sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential
```

Install ndisgtk:

```
sudo apt-get install ndisgtk
```

Either use ndisgtk to install the driver or:

```
sudo ndiswrapper -i net5211.inf
```

Load up ndiswrapper every time Linux is loaded:
```
sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules
```

Restart:
```
sudo reboot
```

My card was detected and shows available networks but if it does not, try ```
sudo iwlist scan
```

My laptop is a Compaq C751NR. lspci gives me:
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

I am running Ubuntu AMD64 8.04. Oh and by the way, the button for my wireless network is orange(off) and will not turn blue(on) but it is indeed working. It just will not change colors. The actual button works though.

---

### Post by ToM-X on 2008-04-25
Nice, we have the card working in 32bit and 64bit.Just out of curiosity Pinoy915, does the WIFI card find networks after reboot. That was the problem with 32bit.

Either way, Nice work. Good to see the card working so everyone has wifi :) 

See you later.

---

### Post by CPImmanuel on 2008-04-25
I get stuck on the build:
paul@paul-laptop:~$ cd madwifi-ng-r2756+ar5007
paul@paul-laptop:~/madwifi-ng-r2756+ar5007$ make
cd: 1: can't cd to /lib/modules/2.6.24-16-386/build
Makefile.inc:66: *** /lib/modules/2.6.24-16-386/build is missing, please set KERNELPATH.  Stop.
paul@paul-laptop:~/madwifi-ng-r2756+ar5007$ 

any ideas? What do I set KERNALPATH to?

I assume that somewhow I need to add a string to indicate where the build code is...

Paul

---

### Post by ToM-X on 2008-04-25
> **CPImmanuel said:**
> I get stuck on the build:
paul@paul-laptop:~$ cd madwifi-ng-r2756+ar5007
paul@paul-laptop:~/madwifi-ng-r2756+ar5007$ make
cd: 1: can't cd to /lib/modules/2.6.24-16-386/build
Makefile.inc:66: *** /lib/modules/2.6.24-16-386/build is missing, please set KERNELPATH.  Stop.
paul@paul-laptop:~/madwifi-ng-r2756+ar5007$ 

any ideas? What do I set KERNALPATH to?

I assume that somewhow I need to add a string to indicate where the build code is...

Paul


Try:

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by Pinoy915 on 2008-04-26
Yes, it auto connects me to my wifi after reboot.

---

### Post by major_rocks on 2008-04-26
nice job pinoy...  I followed those same intructions for Gutsy, however it seems as though they dont quite work for me in Hardy...... i followed your abbreviated instructions, and the card see's my wireless network as well as others but it will not connect.

Did you by chance blacklist "ath_pci" ?

what you have posted should work for me, for some reason something small is different from Gutsy to Hardy.

---

### Post by Pinoy915 on 2008-04-26
> **major_rocks said:**
> nice job pinoy...  I followed those same intructions for Gutsy, however it seems as though they dont quite work for me in Hardy...... i followed your abbreviated instructions, and the card see's my wireless network as well as others but it will not connect.

Did you by chance blacklist "ath_pci" ?

what you have posted should work for me, for some reason something small is different from Gutsy to Hardy.

Oh man, sorry for that. I forgot to add that. Yes, I did blacklist it so the driver that came with Ubuntu did not load and uses ndiswrapper instead.

---

### Post by major_rocks on 2008-04-26
right on !! 

wireless is working for me now after following your instructions, just need to add the blacklist of "ath_pci",

```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

however i also had to disable support for "atheros wireless lan" & "hal" in the restricted drivers: System > Administration > Hardware Drivers.

Gonna reboot now and see if it atomatically reconnects.

Thanks Dude !

---

### Post by _godbout_ on 2008-04-26
Everything was working fine with the beta of Hardy. Then, I crashed the system and install the fresh new release, but cannot make the wireless work anymore! As a long time ago, I've compiled and installed ndiwrapper, the 64bit driver, wicd, get the led working and so on, but no connection.

Maybe I'll give a shot to madwifi?
Let you know.

---

### Post by sanctified-x on 2008-04-26
Thanks for all the help guys. I can't wait to try this out. :D

---

### Post by major_rocks on 2008-04-26
> Gonna reboot now and see if it atomatically reconnects.

ok, it got a bit late last night........anyways. After a reboot i ran into issues of network manager seeing wireless networks but again not being able to connect. This morning i made the switch from Network-Manager to Wicd, and BADA-BING! no more problems.

Just thought i'd post that for anyone else having the same issues .=)

---

### Post by Pinoy915 on 2008-04-26
The led color problem can be solved with newer drivers I presume. When I was on Gutsy, I do not remember which driver I used but I had the network working with a driver and had the led problem. I switched to a different driver and the led problem was fixed. I am afraid to touch my setup at the moment to get the led working. The madwifi fix may work with Hardy 32 bit. I am running x64 so x64 drivers are needed.

---

### Post by gnicko on 2008-04-26
[QUOTE=ToM-X;4791500]Right, I'm back now like I promised.

**Atheros AR5007EG for hardy.**

First of all go to "System/Administration/Hardware Drivers" and disable by un-ticking the box.:

```
Atheros Hardware Access Layor (Hal) 
```

Thanks!!

Wanted to point out that I had to disable "Support for Atheros 802.11 Wireless Cards" in order for this to work (Actually in order to get my system to even boot the new kernel)

I'm running an Acer Extensa 5420 w/AR5007EG...

Once I did that, everything was good!!

---

### Post by lanruisen on 2008-04-26
ToM-X, Thank You! Your post (#7) got my wireless back up.

---

### Post by _godbout_ on 2008-04-28
Ok, I've played with ndiswrapper, madwifi and Hardy 32 and 64bits. I was previously running on Hardy beta with ndiswrapper and everything worked, even the led and the option of controlling how the led was blinking! 
This time, I couldn't get ndiswrapper works correctly, so I decided to try the madwifi. Under the 64bits, impossible to make it work, so I went back to the 32bits version. Madwifi is working great, and I can even now monitor my wireless card how I want. Pretty cool, just missing the led :p

---

### Post by kevdog on 2008-04-28
Just want to clarify that the patched madwifi driver for the ar5007 chipset does not work on 64 bit systems.  I think its pretty clear by the responses in the thread it does not work on 64 bit systems, however this knowledge has also been officially published on the madwifi website.  Hopefully a patched 64 bit driver will be available soon, but as of right now -- there is no 64 bit patched driver available.

---

### Post by rellai on 2008-04-28
HI ALL
I have bought a loptop and disided to install Ubuntu
I installed drivers on wifi (Atheros 5007) modem. I installed them following to all the instructions in the post &#8470;7. Everything was ok but it was impossible to turn into waiting mode and hybernation: it threw out into the console and it doesn't work. 
In  pm-suspend.log the following is written:

Sat Apr 26 13:34:35 MSD 2008: running suspend hooks. 
===== Sat Apr 26 13:34:35 MSD 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear ===== 
===== Sat Apr 26 13:34:35 MSD 2008: running hook: /usr/lib/pm-utils/sleep.d/05led ===== 
===== Sat Apr 26 13:34:36 MSD 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager ===== 
===== Sat Apr 26 13:34:36 MSD 2008: running hook: /usr/lib/pm-utils/sleep.d/20video ===== 
kernel.acpi_video_flags = 0 
===== Sat Apr 26 13:34:36 MSD 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth ===== 
===== Sat Apr 26 13:34:36 MSD 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules ===== 
/usr/lib/pm-utils/functions: line 200: 6681 Segmentation fault modprobe -r $1 
# could not unload 'ath_pci', usage count was 0 

If you turn off the modem drivers everything is ok
Is it possible to solve this problem?
Thank you for your help

---

### Post by logrusmage on 2008-04-28
> **Pinoy915 said:**
> *-snip-*

Thank you. I've been trying for at least 5 days to get this thing to work and this finally did it!

Now I can actually see wireless networks and click on em!

Unfortunately, they won't connect. It SAYS they have full strength, but it can't connect to them. Just attempts to for awhile before stopping, whence the tiny symbol changes into its "You have an errorlol" form.

Anyone have any ideas why this could be happening?

Here's what I get when I try to connect via the terminal:

> beowolf@beowolf-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1f:3a:8e:f4:d2
Sending on   LPF/wlan0/00:1f:3a:8e:f4:d2
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


So... what gives?

---

### Post by Pinoy915 on 2008-04-28
Mine stopped connecting a few days ago. I added to the instructions to disable the default drivers by going to System/Administration/Hardware Drivers and unchecking both the Atheros drivers. For some strange reason, it would connect me again now. Also, do not forget to blacklist the default drivers.

---

### Post by danstever on 2008-04-28
Thanks ToM-X! This worked perfectly verbatim. For reference, I am using a Sony VAIO VGN-NR110E/S.

Props!

---

### Post by dwinstonm on 2008-04-28
Thanks Tom-X for posting that solution, it seems to work just fine.

---

### Post by nicedude on 2008-04-28
To anyone with AR5007EG Atheros wifi, If you use ndiswrapper + XP drivers you won't be able to put your wireless chip set into the neat modes like monitor or promiscuous mode. I am using gutsy 32bit with a 2.6.24 kernel which I pulled from the hardy repository together with patched MadWifi version "madwifi-nr-r3366+ar5007.tar.gz" drivers. Madwifi drivers blow the other solutions out of the water. If all you want to do is surf the web then you might be just fine, But I wouldn't trade my "monitor mode" for anything :-) Well if anyone here still has ar5007eg problems then drop me a PM and I will try to help ya.

---

### Post by abhilashkumar on 2008-04-29
> **nicedude said:**
> r.gz" drivers. Madwifi drivers blow the other solutions out of the water. If all you want to do is surf the web then you might be just fine, But I wouldn't trade my "monitor mode" for anything :-) Well if anyone here still has ar5007eg problems then drop me a PM and I will try to help ya.

I sorta agree.
Ndiswrapper was always a little buggy on my laptop. Requiring a recompile quite a few times. 
Now I use the madwifi drivers and WICD. WICD is really easy to use and configuring your wifi network to connect is also really easy through it.

---

### Post by FredB on 2008-04-29
Well, as I am using this horrible chipset under Hardy 64 bits, I had no other choice but to use windows XP 64 bits driver and ndiswrapper.

It worked without a lot of trouble. Sometimes, I have to remove / reload by hard ndiswrapper kernel module to go online with my wifi connection.

Besides this, no problem with that hardware. Gutsy was harder to set up with that wifi hardware.

---

### Post by Pinoy915 on 2008-04-29
> **FredB said:**
> Well, as I am using this horrible chipset under Hardy 64 bits, I had no other choice but to use windows XP 64 bits driver and ndiswrapper.

It worked without a lot of trouble. Sometimes, I have to remove / reload by hard ndiswrapper kernel module to go online with my wifi connection.

Besides this, no problem with that hardware. Gutsy was harder to set up with that wifi hardware.

I, too, will have to this sometimes. It will show the networks but will not connect. I just had to reload the driver. Madwifi patch is for the 32-bit version, correct? I will not go back to 32-bit and I will stick with 64-bit regardless of little things here and there with the wifi.

---

### Post by Anabolic_OMEN on 2008-04-29
i had an acer 5315 with this exact wireless card.
i was unable to get it to work with the instructions in this post - so i post what did work for me :)

[information from bassetss or something like that on #ubuntu-uk, laptoptestingteam]

```
gksudo gedit /etc/default/linux-restricted-modules-common
```

Add ath_hal to the DISABLED_MODULES="" section so the file looks like this

```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.
 
DISABLED_MODULES="ath_hal"
```

Now we need to install build-essential, download and extract the madwifi snapshot and patch, patch the snapshot and then install the patched driver

```
sudo apt-get install build-essential
wget 'http://madwifi.org/attachment/ticket/1679/madwifi-ng-0933.ar2425.20071130.i386.patch?format=raw'
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz
tar zxvf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007
patch -p0 < ../madwifi-ng-0933.ar2425.20071130.i386.patch\?format\=raw
make clean
make
sudo make install
sudo reboot
```

*note : [http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz](http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz) - link was down so i used
**note : patch has already been applied to the snapshot - but i have patch over it.


ubuntu 7.10 with all updates installed, should work with hardy since i was having problems with hardy and decided to use 7.10 but ran into the same problem. this time i had it fixed.

monitor mode works
adapter works as ath0 with wifi0 - no ndis wrapper, no mess.

---

### Post by louisiana84 on 2008-04-29
I know nothing about Linux, but I'm anti-windows. So, I bought a Toshiba a215-s5829 specifically for the purpose of having a decent Ubuntu laptop. Well, this whole atheros 5007 deal has soured me completely. If I have to go into terminal to fix this and start typing this 'code' in, well, screw it! That's ridiculous for someone with as little computing experience as me. I love Ubuntu. Had it on my previous Toshiba, but... All I want is the freakin' wireless to work. Otherwise, all I have is another desktop machine.

---

### Post by Anabolic_OMEN on 2008-04-29
Well, these commands can be made into a script, so you could double click and it does it all for you.
I think nobody will bother to write a script for this.

Also doing this isnt too difficult and its a great way to learn.

Too many people are brought up in this gui sanbox, scared of text, manuals and the terminal :).

---

### Post by Pinoy915 on 2008-04-29
The command line is pretty powerful. Also, this "code" is just basically copying and pasting into the terminal. We have to do what we have to do to get it working and keep Windows off our laptops...lol.

---

### Post by ToM-X on 2008-04-29
louisiana84

Sorry, this topic is for getting the Atheros AR5007 chipset working. We have the card working with simple commands. If you are not capable of doing such things then linux is not for you.

Stop complaining, this topic is not the place.

I will look into making a script but it will not be on my first priority due to coursework and the simplicity of the current commands to have the chip working.

---

### Post by ophion on 2008-04-29
> **ToM-X said:**
> louisiana84

Sorry, this topic is for getting the Atheros AR5007 chipset working. We have the card working with simple commands. If you are not capable of doing such things then linux is not for you.

Stop complaining, this topic is not the place.

I will look into making a script but it will not be on my first priority due to coursework and the simplicity of the current commands to have the chip working.

This is why GNU/Linux fails, year after year.  The onus of hardware support forever falls upon the vendor, never upon the user.

---

### Post by lemming465 on 2008-04-29
> **louisiana84 said:**
> I know nothing about Linux, but I'm anti-windows. ... this whole atheros 5007 deal has soured me completely. If I have to go into terminal to fix this and start typing this 'code' in, 

Unfortunately, not all vendors reflexively ship high quality open source drivers yet, and Atheros is among the worst, though that may be changing.  In the interim, there only 3 solutions:

1. Buy hardware certified to work with Linux, e.g. from Dell.
2. Learn to be comfortable with the command line.
3. Wait 6-12 months for support to mature.  I'm pretty sure the '5007s will be supported OK in ubuntu 8.10 this fall.

If you already bought a Toshiba satellite (I just got one recently too), #1 is out.  You're rejecting #2; that only leaves #3.

It could be worse; you could be trying to get 64-bit windows support for devices.  Now there is a *real* nightmare ...

---

### Post by logrusmage on 2008-04-29
I've ran XP 64. Horrible support and no way around it.

Anyway, still can't ******* connect. It seems to be working, I can see multiple nets, I just can't connect.

---

### Post by louisiana84 on 2008-04-29
Okay, I fired up a terminal got in there, posted the code and VOILA! 

It works. I feel like a moron for whining. THis was a piece of cake and the damn thing worked like a charm. Thank you so much!!!

---

### Post by suoko on 2008-04-29
this howto worked perfectly for an acer 5715Z

Thanks man

---

### Post by Spartacus84 on 2008-04-30
I have no Linux experience, and I have a Copmaq Presario f756nr with an AMD 64 processor and an Atheros AR5007 that can't connect to the internet. I've been following Post #14 exactly trying to get it to work, but I keep getting an error at the part where I extract ndiswrapper (tar xvf ndiswrapper-newest.tar.gz) and when I try to install the driver with ndiswrapper (sudo ndiswrapper -i net5211.inf). Anybody know what I'm doing wrong?

---

### Post by ToM-X on 2008-04-30
> **Spartacus84 said:**
> I have no Linux experience, and I have a Copmaq Presario f756nr with an AMD 64 processor and an Atheros AR5007 that can't connect to the internet. I've been following Post #14 exactly trying to get it to work, but I keep getting an error at the part where I extract ndiswrapper (tar xvf ndiswrapper-newest.tar.gz) and when I try to install the driver with ndiswrapper (sudo ndiswrapper -i net5211.inf). Anybody know what I'm doing wrong?

Ok,Lets try:

```
wget http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz
```

```
tar xvf ar5007eg-64-0.2.tar.gz
```

```
sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential
```

```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

```
sudo apt-get install ndiswrapper
```

```
pushd ar5007eg-64-0.2/ar5007eg/
```  this bit may be wrong, I'm on windows so I can't test. If it is wrong then you just need to point it to your extracted folder directory.

```
sudo ndiswrapper -i net5211.inf
```

```
popd
```

```
sudo modprobe ndiswrapper
```

```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

```
sudo reboot
```

---

### Post by Spartacus84 on 2008-04-30
When I get to the part where I enter "sudo apt-get install ndiswrapper", I get the following error: "E: Couldn't find package ndiswrapper". What do I do now?

---

### Post by ToM-X on 2008-04-30
Ok try this...

download ndiswrapper and save to your **Home** folder.

```
http://wifix.sourceforge.net/software.php?title=ndiswrapper
```

Then open the terminal:

```
tar xvf ndiswrapper-1.51.tar.gz
```

```
pushd ndiswrapper-1.51
```

```
sudo make uninstall
```

```
make
```

```
sudo make install
```

```
popd
```

Then Ndiswrapper should be installed.

---

### Post by Spartacus84 on 2008-04-30
I did that, and everything worked! I installed wicd, and can see the networks and configure them, but I cannot connect. Any idea what's wrong?

---

### Post by Tuxseak on 2008-04-30
Can someone explain to me why  get this error? I have an Atheros AR5007EG  with Hardy 8.04
i'm running an i386 copy instead of 64 bit (my laptop has an AMD 64 Athlon X2) because 64 bit wont install - does it have an impact?
-Please I'd appreciate a response as I'm getting very frustrated over this wifi business.
- Is it better if I get an USB wifi card that is known to work? can you recommend one? 
Sorry this is so long - Thank you all in advance]


serge@Tuxseak-laptop:~/madwifi-ng-r2756+ar5007$ make 
Checking requirements... ok. 
Checking kernel configuration... ok. 
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/serge/madwifi-ng-r2756+ar5007 modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic' 
  CC [M]  /home/serge/madwifi-ng-r2756+ar5007/ath/if_ath.o 
  CC [M]  /home/serge/madwifi-ng-r2756+ar5007/ath/if_ath_pci.o 
  LD [M]  /home/serge/madwifi-ng-r2756+ar5007/ath/ath_pci.o 
  CC [M]  /home/serge/madwifi-ng-r2756+ar5007/ath_hal/ah_os.o 
  HOSTCC  /home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: In function 'uudecode_usage': 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: At top level: 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:40: error: expected ')' before '*' token 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:70: error: expected ')' before '*' token 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: In function 'main': 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: for each function it appears in.) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function) 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu' 
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose' 
make[3]: *** [/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode] Error 1 
make[2]: *** [/home/serge/madwifi-ng-r2756+ar5007/ath_hal] Error 2 
make[1]: *** [_module_/home/serge/madwifi-ng-r2756+ar5007] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic' 
make: *** [modules] Error 2

---

### Post by Spartacus84 on 2008-04-30
When I attemt to connect to the internet on wicd, it says I am "Connected to none at 0 (IP: 192.168.X.X), and my internet doesn't work. Am I doing the static IP adress wrong? I just put in my regular IP adress. What should I do?

---

### Post by Spartacus84 on 2008-04-30
Hmm... when I try it without a static IP, it goes between saying "<SSID>: Obtaining IP adress..." and "None: Obtaining IP adress...", and it ends up with "Not connected". Any ideas?

---

### Post by Spartacus84 on 2008-04-30
Below the "Auotmatically connect to this network" box is the following: "90%  Secured WEP  00:18:01:F3:E1:27  Managed  Channel 6".

In preferences, my WPA supplicant driver is set to ndiswrapper, my wireless interface is wlan0, and my wired interface is eth0.

What do I have to do to get it to connect?

---

### Post by troach on 2008-04-30
These instructions are useless to me. Why? I don't have any network access. Just a wireless card.

Any idea how I can download on another machine and load everything on my Ubuntu?

You'd think Ubuntu would have had most of this worked out by now.

---

### Post by major_rocks on 2008-05-01
> **Spartacus84 said:**
> Below the "Auotmatically connect to this network" box is the following: "90%  Secured WEP  00:18:01:F3:E1:27  Managed  Channel 6".

In preferences, my WPA supplicant driver is set to ndiswrapper, my wireless interface is wlan0, and my wired interface is eth0.

What do I have to do to get it to connect?

try setting the wpa supplicant driver to "wext" instead, you may need to reboot as well.

---

### Post by zeba on 2008-05-01
I tried to install those things I was told at ubuntu forums, mad wifi, the wrapper, cant remmeber it&#347; exact name, and a windowsdriver i dl from acer, but also should be availeble at atheros site. I did nt get it to work and no wireless connection in my list of connection options. 

Then I installed the package in synaptic called hostapd and suddenly I could see the wireless networks. I don t really know how I did but maybe u can get some help out of it?
this is the program I installed last and suddenly everything worked..

but I dl both my driver in windows version, madwifi, wrapper and Im not sure what is the key for it all..I dont dare to test it either ...what if I cant get it right again..lol...

The current version includes support for other drivers, an integrated
EAP authenticator (i.e., allow full authentication without requiring
an external RADIUS authentication server), and RADIUS authentication
server for EAP authentication.

hostapd works with the following drivers:

 * Host AP driver for Prism2/2.5/3,
 * Prism54 driver for Intersil/Conexant Prism GT/Duette/Indigo,
 * madwifi driver for cards based on Atheros chip set (ar521x),
 * Any wired Ethernet driver for wired IEEE 802.1X authentication.

---

### Post by Spartacus84 on 2008-05-01
Now it says "Connected to <SSID> at 90 (IP: 192.168.X.X)", but I still am not connected!

Am I doing the DNS right? I didn't know what to do so I just put my normal IP adress.

---

### Post by major_rocks on 2008-05-01
> **Spartacus84 said:**
> Now it says "Connected to <SSID> at 90 (IP: 192.168.X.X)", but I still am not connected!

Am I doing the DNS right? I didn't know what to do so I just put my normal IP adress.

hmm typically if it is showing how strong the signal(90) is, it usually means you are connected.

is your wirless network "hidden"? 

dns is not the same as your internet ip or your local ip, dns is the ip addresses that are used to connect to your isp. Usually you can find those in your router setup/information: for example i have a linksys router, when i go to 192.168.1.1 it brings me to the router configuration. Under "status" it shows my dns servers that my isp provides. Typically it's two ip addys that are similar.

The only reason you should need your dns server ip's are if your assigning a static ip to your machine, otherwise those setting should be blank, meaning you are letting the router assign the ip to the machine via DHCP.

hope this bit of info helps.

---

### Post by Rotarychainsaw on 2008-05-01
It's so weird, the first 2 days of 8.04 I had ndiswrapper going fine, on reboots I would connect to my AP no problem. Now on reboot I have to rmmod and modprobe ndiswrapper to jumpstart my wireless. It's a real bummer. Does this happen for others? Abit airpace amd 64.

---

### Post by Spartacus84 on 2008-05-01
How would I find out a working DNS? Also, what are these "Global DNS Servers" in preferences? Could I use those?

---

### Post by Rotarychainsaw on 2008-05-01
[http://ubuntuforums.org/showpost.php?p=4829624&postcount=345]("http://ubuntuforums.org/showpost.php?p=4829624&postcount=345")

I think this fixed my problems.... /knock on wood/

edit- the realtime kernel seems to make things worse as well, so if you're running ubuntu-studio, good luck... It was constantly resetting wlan0.

---

### Post by _godbout_ on 2008-05-02
> **Rotarychainsaw said:**
> It's so weird, the first 2 days of 8.04 I had ndiswrapper going fine, on reboots I would connect to my AP no problem. Now on reboot I have to rmmod and modprobe ndiswrapper to jumpstart my wireless. It's a real bummer. Does this happen for others? Abit airpace amd 64.
I got the same problem with ndiswrapper and the amd64 version. Sometimes I could connect without any problem, but pretty rare. Usually I had to modprobe -r ndiswrapper and modprobe again. I've never found any valable reason for that :/

---

### Post by Tuxseak on 2008-05-02
> **ToM-X said:**
> Ok,Lets try:

```
wget http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz
```

```
tar xvf ar5007eg-64-0.2.tar.gz
```

```
sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential
```

```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

```
sudo apt-get install ndiswrapper
```

```
pushd ar5007eg-64-0.2/ar5007eg/
```  this bit may be wrong, I'm on windows so I can't test. If it is wrong then you just need to point it to your extracted folder directory.

```
sudo ndiswrapper -i net5211.inf
```

```
popd
```

```
sudo modprobe ndiswrapper
```

```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

```
sudo reboot
```

I followed these instructions until the part when it came to installing the driver then I followed the instruction on the following page:

[http://www.ginad.org.uk/NDISwrapper.html](http://www.ginad.org.uk/NDISwrapper.html)

And now my wireless works! Thanks TomX and every good person that has posted a reply.
Thanks to Ubuntu I'm tasting 64bit computing-- my windows version of course is running a 32bit on a 64 bit machine.:confused:
UBUNTU Rocks!:guitar:

---

### Post by prylux on 2008-05-02
After following all the instructions here I got the wireless up and running
I could even get online using Wicd. But it kept dropping the connection around 5 to 10 seconds. It would also disconnect if I closed the Wicd Manager window. 
So I tried connecting using other Wifi connection managers. They all recognize the wireless and see all the local access points, some even said I was connected.
But every time I tried to use firefox I could not access a webpage.
I reinstalled Network Manager and that didn't help.
Went back to Wicd and now it says I'm "Connected to None at 0dBm (192.168.0.194)" I'm sitting right beside the router.
I can connect with the wired connection but it sometimes drops the connection now. ](*,)

---

### Post by burunji on 2008-05-02
ToM-X
thank you so much...you are a life saver i followed you instructions now i can see for the first time in ubuntu my wireless connection.
all i have to do now is to set it up.
Thank you so much 
:):):)

---

### Post by major_rocks on 2008-05-02
> **Spartacus84 said:**
> How would I find out a working DNS? Also, what are these "Global DNS Servers" in preferences? Could I use those?

Spartacus....are you using a router?

---

### Post by Spartacus84 on 2008-05-02
> **major_rocks said:**
> Spartacus....are you using a router?

Yes.

---

### Post by major_rocks on 2008-05-02
ok, you should see your dns server ips if you go to:

  **main menu > system > administration > network**

click the "DNS" tab and that should show the dns ips, again you only need those if you are going to assign a static ip to your machine.

Global DNS settings in Wicd tells Wicd to use the DNS ips' for the wireless, and wired connections.

---

### Post by prylux on 2008-05-03
Okay... I feel silly... The reason I was getting those problems was this:

 System>Administration>Network
In network settings make sure ONLY Wireless or Wired networks are checked.
When both were checked they were both trying to connect and throwing the other off.

That's why I could see wireless connection points but was connected to "Connected to None at 0dBm (192.168.0.***)"

Set locations up for Wired and Wireless now it works fine.\\:D/

---

### Post by burunji on 2008-05-03
Hi I installed my drive following this instructions but i can see my connections and other connections,

I also installed wicd, but I can't get it to connect.

When I try it without a static IP address, I get the message "Connected to <SSID> at 0 (IP: 192.168.X.X)".

When I try it with a static IP address, I still get the message "Connected to <SSID> at 0 (IP: 192.168.X.X)".

Please help:confused:

---

### Post by liquerLOVER on 2008-05-04
im doing dual boot winXP & ubuntu since my ubuntu cannot connect to internet during my wireless problem. im using Acer Aspire 4520 which is really famous & cheap. the wireless driver is atheros AR5007EG. ok... this all start when the first time using linux & ubuntu 8 hardy was my 1st linux. i had been settle this problem for 2 times but stuck for d 3rd time until now.

my first trial, im able to settle network problem by follow all the threads that i coppied from ubuntu forums. however, sudenlly, my ubuntu having problem with sound just after i settle withmy network. maybe after 1/2 o more then that. so, i decide 2 re-install ubuntu for the 2nd time to make sure that i have a PERFECT ubuntu because im thinking off get rid winXP.

after that, i try to set up the wireless, AGAIN with steps that given in the threads that i coppied from ubuntu forums. i follow & read all the process step by step carefully. & once again, im able to settle my network for the 2nd time. and after that, im online using ubuntu since i want to update & install movie & audio codec from internet. after settle with codec & few things, i feel relief so i finally decide to decrease the size of my winXP.

so, i resize the partition from winXP using partition magic 8 which i had installed before i resize my partition & install ubuntu. after that, there is a warning that saying error in resizing partition so i quit.

so...i decide to give a check on my beloved ubuntu & U know what??? GRUB LOADING ERROR!!! so, i set WinXP as an active partition so that i can get in my winXP.

after that, i decide to install ubuntu for the 3rd time. this is where i stuck & everything turn to ****.no matter what i use, madwifi-ng-r2756+ar5007 or madwifi-nr-r3366+ar5007 even ndiswrapper, all i got is fail. below is one of error that i got from madwifi-ng-r2756+ar5007. 


rj@blackTOP:~/madwifi-ng-r2756+ar5007$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/rj/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
CC [M] /home/rj/madwifi-ng-r2756+ar5007/ath/if_ath.o
CC [M] /home/rj/madwifi-ng-r2756+ar5007/ath/if_ath_pci.o
LD [M] /home/rj/madwifi-ng-r2756+ar5007/ath/ath_pci.o
CC [M] /home/rj/madwifi-ng-r2756+ar5007/ath_hal/ah_os.o
HOSTCC /home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/serge/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/rje/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: At top level:
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: In function 'main':
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/rj/madwifi-ng-r2756+ar5007/ath_hal/uudecode] Error 1
make[2]: *** [/home/rj/madwifi-ng-r2756+ar5007/ath_hal] Error 2
make[1]: *** [_module_/home/rj/madwifi-ng-r2756+ar5007] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2

i follow all the steps given but still the terminal reply my command like above. i dont know whether i miss a steps or spelling error. it's impossible to make a mistake cos after few times i found failure, i just copy & paste because tired & want to ensure that i follow the steps.

what i want to say here is, HELP me all ubuntu experienced user. i really want to use linux as my no 1 OS. maybe you all can help me by reply me with a full complete step because im very new to linux & this my 1st time to linux. to be frank, i dont know wat does the command mean. im very attract to ubuntu since i heard wat does ubuntu mean. so, im one of human being that want to learn ubuntu. help me...

p/s:sorry for being a loser in this forum. i really hope ubuntu community can help me. thank you.

---

### Post by Spartacus84 on 2008-05-04
I actually got it to connect and I could go on the internet (connecting without a static IP address), however, after I rebooted my computer, it no longer works. Anybody know what could be causing this?

---

### Post by prylux on 2008-05-05
I kept running into a new problem. Like some of you here, I had problems where I was able to see networks, and it would look like I was connected to them, even showed the signal strength I was connected at. But I couldn't connect to anything else like browsers or updates. Other times everything would work.
I was using Wicd and while it was not this program that was giving me problems **wlan0:avahi** was giving me sporadic connection problems
I found it when I added the "Network Monitor" to my panel. When I opened it one of the selections was **wlan0:avahi**
It was competing for resources with **wlan0** is my bet and so I removed it
I fixed this problem by doing the following in this order:

Open Synaptic Package manager
Select to completely remove Wicd
Install Network Manager
Reboot

Open a terminal and input
sudo ip link set wlan0:avahi down

Open network settings
Set static IP address

Check /etc/network/interfaces
should look like this
---------------------------------
auto lo
iface lo inet loopback





iface wlan0 inet static
address 192.168.0.139
netmask 255.255.255.0
gateway 192.168.0.1
wireless-key 1234567891 
wireless-essid linksys
---------------------------------
or whatever you setup

This worked for me on my C751NR laptop
I have not gone anywhere else and tried to setup another connection but it works for me at home.

---

### Post by _godbout_ on 2008-05-06
Hi again there,

Previously in the topic, I wrote that I could use the madwifi drivers given with Ubuntu Hardy. That's true, partially. Actually, I can't connect any protected network, WEP or WPA :D
I'm using a non-protected network now, but I would like to protect it. Is there something that I've missed somewhere? Anything to install?

---

### Post by FastZ on 2008-05-06
You can't protect a non-protected network via your laptop.  The WAP has to be configured for WEP or WPA/WPA2 for the network to be protected.  If you want to make all your surfing annonymous, you can read up on the [Tor project]("http://www.torproject.org/").

---

### Post by logrusmage on 2008-05-06
> **logrusmage said:**
> Thank you. I've been trying for at least 5 days to get this thing to work and this finally did it!

Now I can actually see wireless networks and click on em!

Unfortunately, they won't connect. It SAYS they have full strength, but it can't connect to them. Just attempts to for awhile before stopping, whence the tiny symbol changes into its "You have an errorlol" form.

Anyone have any ideas why this could be happening?

Here's what I get when I try to connect via the terminal:



So... what gives?

Bump.

For the love of god please help me! (OK, I'm being dramatic)

auto lo
iface lo inet loopback

Is the only thing in my etc/network/interfaces file/ Is this a problem?

Help

---

### Post by _godbout_ on 2008-05-06
Oh oh oh, sorry, there is a misunderstanding here. What I meant is that I want to re-configure my router to enable the WPA protection. I have to disable it now if I want to connect to my router.
Actually, after several tests yesterday and a bit of work, I succeeded to connect it, but not always, I don't know the reason.

---

### Post by TheWhatkin on 2008-05-07
Aargh. Help, please?

I had my Aspire 3680 working with Madwifi on 7.10 prior to upgrading to 8.04.

I've tried the instructions in post #7, but my computer then refuses to reboot cleanly.

---

### Post by ameseisch on 2008-05-07
I am using a 32-bit install, so i used post #7 and the wireless card is working. A good step! I can see all the networks available and I can even connect to unsecured ones, but I cannot connect to secure networks. it just trys for a while and then keeps asking for the passphrase. and I am as sure as I can be that I have the passphrase correct. any ideas?

---

### Post by shootermk on 2008-05-08
> **prylux said:**
> Okay... I feel silly... The reason I was getting those problems was this:

 System>Administration>Network
In network settings make sure ONLY Wireless or Wired networks are checked.
When both were checked they were both trying to connect and throwing the other off.

That's why I could see wireless connection points but was connected to "Connected to None at 0dBm (192.168.0.***)"

Set locations up for Wired and Wireless now it works fine.\\:D/

I have my wireless card installed, but can't manage to uncheck the wired connection. Everytime I access the network manager both connections are checked. Any help please!?!

---

### Post by ameseisch on 2008-05-08
Same problem of not being able to connect to secure netoworks with Wicd. Help please!!! its been almost 2 weeks that I have been at this wireless issue, and I am so close I can almost taste it...

---

### Post by shootermk on 2008-05-08
OK, I somehow managed to get connected. For those who still have problems with connecting..

1. Check your DNS Servers.
2. Check your host name.
3. Make separate locations for wired and wireless connections and make sure in every location you have just one connection type checked.
4. Good Luck to you all, I worked 2 days on getting connected.

And forgot to say, I didn't try WPA encryption, managed to connect through WEP.

---

### Post by Pinoy915 on 2008-05-08
What is wicd? Is it for 32-bit versions? I cannot seem to find it on x64 and I never used it to make my card work.

---

### Post by abhilashkumar on 2008-05-08
> **Pinoy915 said:**
> What is wicd? Is it for 32-bit versions? I cannot seem to find it on x64 and I never used it to make my card work.



Wicd is an open source wired and wireless network manager for Linux. If your original network manager is not detecting the wireless network, maybe WICD will be better.

---

### Post by HitRefresh on 2008-05-08
Thanks Tom-X! Your short how-to post (#7) worked, and have wireless working now on HP DV6704nr laptop. 

Just one question for anyone whom also followed the post, I disabled "HAL" from the restricted drivers but I have enabled "Support for Atheros 802.11 Wireless LAN Cards." Is that correct configuration ? I was not sure.

---

### Post by drlisacuddy on 2008-05-09
Hey, guys! I followed post 7, and my wireless now works, the only thing is that the computer used to hibernate and suspend properly, but now with the wireless the computer refuses to hibernate or suspend. Any ideas as to why?

---

### Post by Darkendes on 2008-05-09
I was successful in configuring this wireless adapter with ndiswrapper. I had to get rid of madwifi and the old ndiswrapper before mine would work.

I'm using ndiswrapper 1.52, and used 64-bit XP drivers for it (I'm running Hardy 64-bit). It installed fine and was able to see access points, but not connect to them at first.

I then went into the console and typed:

```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether xxxxxxxx <replace x's with your MAC address>
```

And viola, I was able to acquire an IP address from the router.

After that, I installed wifi-radar, and set it up to use those ifconfig commands before it auto-connects to the access point, and now I'm automatically connected to my home network at bootup.

I'll leave it to you to find instructions and XP drivers for ndiswrapper, since from the looks of it, even though it's the same wireless card, people are having different kinds of luck with different drivers, depending on the laptop model. I'm using a Toshiba Satellite A215-S5837.

If you want to try the method I used anyway, here's the link: [http://ubuntuforums.org/showthread.php?t=527619](http://ubuntuforums.org/showthread.php?t=527619) Go to post #2 and start from there. You'll have to find XP driver yourself, but one that worked for me: [ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/Wireless_Atheros_V5.3.0.67_XP_XB63_XB62(WHQL).zip](ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/Wireless_Atheros_V5.3.0.67_XP_XB63_XB62(WHQL).zip) (use 32-bit if you're running 32-bit Linux, 64-bit for 64-bit).

He used ndiswrapper 1.47, but mine worked with 1.52 with no problems at all.

The ifconfig stuff is on page 4, I believe. Post #38, if you'd like to see it for yourself.

Good luck!

---

### Post by cubastreet on 2008-05-10
Wireless card working now thanks :)
However, cannot switch it off, probably not great for battery life.

---

### Post by longboneslinger on 2008-05-10
> **ameseisch said:**
> I am using a 32-bit install, so i used post #7 and the wireless card is working. A good step! I can see all the networks available and I can even connect to unsecured ones, but I cannot connect to secure networks. it just trys for a while and then keeps asking for the passphrase. and I am as sure as I can be that I have the passphrase correct. any ideas?

Try this: Go to the set-up for your router. If its a linksys, just type 198.168.1.1 into your browser. Look for the WPA shared key. It's under Wireless-->Wireless Security. Copy down the key and put it in as the passphrase. 
I hope this helps someone.
Later taters and God bless,
bone

---

### Post by pcaulder on 2008-05-10
The original post worked perfect for me.  Acer 3680-2682 with the atheros 5700 chipset in 8.04

---

### Post by longboneslinger on 2008-05-10
Boy oh boy. I'm trying to get madwifi to work on an Acer Aspire 5315 with the afore mentioned AR5007EG on a clean install of 8.04 (32 bit). It just wont work. 
When I run ```
/etc/init.d/networking restart
``` it gives the following:
>  * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:1b:38:63:36:f8
Sending on   LPF/eth0/00:1b:38:63:36:f8
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:1b:38:63:36:f8
Sending on   LPF/eth0/00:1b:38:63:36:f8
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.1.103 from 192.168.1.1
DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.103 from 192.168.1.1
bound to 192.168.1.103 -- renewal in 38214 seconds.


Notice the > widi0: unknown hardware address type 801
I checked /etc/network/interfaces and changed 'wext' to 'madwifi' but it made no difference. I tried changing ath0 to wifi0 in /interfaces but no joy.
I just checked /interfaces again and most the add-ins are gone including the wext line. My pid is gone to. this is nuts. I put it in like it was in 7.10. I went back into NM and added the PID there and it's back in /interfaces. I had to reboot since I lost my eth0 connection. This is insane.
Sigh. I hope someone can make sense of this. I really want to use madwifi. I really don't want any Winblows junk on my lappy. So TIA to all who try to help.
bone

---

### Post by longboneslinger on 2008-05-11
Small update. I dumped Network Manager for wicd. It says "No wireless networks found." I played in preferences and changed wpa supplicant driver from wext to madwifi with no results. I also tried wifi-radar and it saw the network and by giving it a static IP I was able to get it to claim it was connected. It wasn't. ```
ping google.com -c 3
``` just timed out with unknown host.
I'll even add a copy of /etc/network/interfaces just for the fun of it:

>   GNU nano 2.0.7         File: /etc/network/interfaces                          

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp

wpa-pairwise TKIP
wpa-group TKIP
wpa-psk XXXXXX
wpa-driver madwifi
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid bOnEs_YaRd
wireless-keymode open

I'm still on TKIP cuz on 7.10 AES wouldn't connect but TKIP would. Go figure. Now on a fresh install my wireless is connectionless no matter what I try.
Here's to hoping someone can figure this out. TIA for your time all.
bone

---

### Post by Alfred_McGee on 2008-05-12
When WICD says "No wireless networks found" it has always meant, to me, that the external switch for my wifi card needed to be flipped back on, but that doesn't sound like the problem you're having.

Anybody know a good way to manage wifi connections for an AR5007EG card running under Atheros? I believe it's running because I used the fix posted at the beginning of this thread and because sudo iwlist scanning gives lots of good info from my wifi card (ath0). Iwlist scanning unfortunately also gives info from some other interfaces that don't exist. Is WICD still the way to go, even though I seem to have partially kicked the ndiswrapper habit?

EDIT: Yes, WICD rules! I set the WPA supplicant to wext, by the way, Bone. Iwlist scanning still tells me I have another wireless interface -wifi0- but if it ain't broke, don't fix it, right?

---

### Post by wernotalone on 2008-05-12
Hi, I'm new to ubuntu and I am having trouble with the terminal.

I was following the directions from the second page of this thread, and I got an error with the code


Code:

wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

Error parsing proxy URL [http://:8080:](http://:8080:) Invalid Host name.

Any help would be greatly appreciated.

> **Pinoy915 said:**
> Success!!! I have my wireless card working! I am using ndiswrapper with 64 bit drivers. Here is the thread I used to get mine working. [http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

Here are the only steps I used. I did not disable anything in the restricted drivers menu.

Go to System/Administration/Hardware Drivers. Disable the default drivers by unchecking "Atheros Hardware Access Layer(HAL)" and "Support for Atheros 802.11 Wireless LAN cards." Reboot if necessary.

Blacklist the default driver:

```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

Get the 64 bit driver:
```
wget http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz
```

Extract driver:
```
tar xvf ar5007eg-*.tar.gz
tar xvf ndiswrapper-newest.tar.gz
```

Ensure you have your kernel headers and the build essential package.
```
sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential
```

Install ndisgtk:

```
sudo apt-get install ndisgtk
```

Either use ndisgtk to install the driver or:

```
sudo ndiswrapper -i net5211.inf
```

Load up ndiswrapper every time Linux is loaded:
```
sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules
```

Restart:
```
sudo reboot
```

My card was detected and shows available networks but if it does not, try ```
sudo iwlist scan
```

My laptop is a Compaq C751NR. lspci gives me:
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

I am running Ubuntu AMD64 8.04. Oh and by the way, the button for my wireless network is orange(off) and will not turn blue(on) but it is indeed working. It just will not change colors. The actual button works though.

---

### Post by HitRefresh on 2008-05-12
> **drlisacuddy said:**
> Hey, guys! I followed post 7, and my wireless now works, the only thing is that the computer used to hibernate and suspend properly, but now with the wireless the computer refuses to hibernate or suspend. Any ideas as to why?


I have the same problem as well. When trying to suspend or hibernate it just sort of hangs, and then a bunch of error messages scroll by and the laptop shuts down. 

That is weird, what does the wireless configuration have to do with suspend/hibernate functions ? 

Anyone have any fixes/suggestions to try for this ?

---

### Post by williamson389 on 2008-05-12
i also have a Atheros AR242x and cannot conect to wireless internet.  i tired tom-X's code but nothing changes.  At both of these lines:tar xfz madwifi-ng-r2756+ar5007.tar.gz and sudo modprobe ath_pci the terminal didnot respond or change.  i tried pinoy's instructions and got throught the ccode fine but after reboot i was still unable to connect to the internet.  On a side note are madwifi and ndiswrapper applications, because i cannot find them to open them.

---

### Post by balagosa on 2008-05-12
> **ToM-X said:**
> Right, I'm back now like I promised.

**Atheros AR5007EG for hardy.**

First of all go to "System/Administration/Hardware Drivers" and disable by un-ticking the box.:

```
Atheros Hardware Access Layor (Hal) 
```

Then Reboot

Then open the terminal "Applications/Accessories/Terminal" and copy the following:

```
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz 
```

```
sudo apt-get install build-essential
```

```
tar xfz madwifi-ng-r2756+ar5007.tar.gz
```

```
cd madwifi-ng-r2756+ar5007
```

```
make
```

```
sudo make install
```

```
sudo modprobe ath_pci
```

```
sudo reboot
```

Then thats it :D Enjoy!


dude...this crashed my Hardy on reboot. i can not log in anymore.

the situatuion....booting on non-recovery mode


Loading Kernel Modules
Loading Manual Drivers.... then after 30mins of wait, still nothing.

i tried booting into recovery mode and this is what i got...
*Reading files needed to boot
lp: driver loaded but no devices found
ndiswrapper version 1.52 loaded (smp=yes, preempt = no)

and this is where it doesnt do anything

using Xubuntu 8.04, kernel 2.6.24-16-generic. i am using NDiswrapper though...not madwifi. so i think when i "modprobe", this caused my problem?

---

### Post by balagosa on 2008-05-13
uhm...bump

---

### Post by ToM-X on 2008-05-13
Try booting on to recovery and removing Ndiswrapper..

```
sudo apt-get remove ndiswrapper
```
```
sudo reboot
```

: /

Also can I please note to the thread. Atheros are NOT offically supporting for linux. We will get errors,problems and glitches. Its a *trial and error* situation. Do NOT expect perfection.

If the driver works then be thankfull, if it doesn't then it's not my fault.

---

### Post by balagosa on 2008-05-13
i wasnt blaming you :KS, i am blaming myself for trying something knowing that it could mess up my kernel by a slight chance of 50%. **Always remember people, BACKUP your files every once in a while.** This sure hit me in the head, because now i am regretting that i didnt backup my files.

hmmm....my CURRENT situation is so long. maybe you can just go to this link and refer to the latest post.

[Current Situation]("http://ubuntuforums.org/showthread.php?t=789824&page=2")

but your idea of removing ndiswrapper is good though. i will try it.

---

### Post by logrusmage on 2008-05-13
This is it. One more night of no wireless and I'm going back to Winblows -_-

> beowolf@beowolf-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6218
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1f:3a:8e:f4:d4
Sending on   LPF/wlan0/00:1f:3a:8e:f4:d4
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


It says the driver is working. When I scan using the terminal, I can see multiple networks. I cannot see any networks in Network-manager. Both wired and wireless are in roaming mode in network-manager.

WTF should I do?

EDIT: NEVERMIND. Got it working, sorta forgot to do the mode Managed command. However, Network manager is still being a douche. How can I fix? Reinstall or use WCID (I cannot find WCID in synaptic -_-)

---

### Post by lescarlin on 2008-05-15
> **ToM-X said:**
> Right, I'm back now like I promised.

A big thank you.  I've followed various threads in the N & W forum without much success.  It seems i too was a victim of the AR5007 mislabelling, but your solution worked fine.

FYI, i'm running a Fujitsu-Siemens laptop, Intel Dual CPU 1.6GHz.  In my case i have a single partition with ubuntu 8.04 OS

Good to be connected at last. :biggrin:
Talking

---

### Post by Snappo on 2008-05-15
would this work with the ar5005g?

---

### Post by Alfred_McGee on 2008-05-15
How can I fix? Reinstall or use WCID (I cannot find WCID in synaptic -_-)[/QUOTE]

Logrusmage:

It's WICD, not WCID. I highly recommend WICD. WICD has its own website with install instructions.

---

### Post by balagosa on 2008-05-16
> **Snappo said:**
> would this work with the ar5005g?

i dont think it will work for 5005g.

well 5007 and 5006 can live with the same drivers.

---

### Post by danwood76 on 2008-05-17
Isnt the 5005g supported under the default madwifi?
The patch in this thread is just for the x86 7007EG.

---

### Post by BETELGEUSE58 on 2008-05-18
I have ACER 5315 with atheros 5007eg  and this guide worked perfect for me. 

I also tried to get aircrack to work amongst other similar ones which require updates, patches etc which caused my w/card to stop working. I then redone these steps and it works again as it did when I first did it. Cant get aircrack etc to work without messing up my system but thats another topic. 

Great post, works fine.

---

### Post by Alfred_McGee on 2008-05-19
Hey Betelgeuse58, some USB dongles will do everything you need without any patches. The AR5007 card running under Wicd will give a nice overview of things while your dongle is working. But thanks for posting on this important topic. Many new possibilities are sure to emerge now that there is finally native Linux support for the AR5007 card.

---

### Post by Israphel on 2008-05-22
I just followed your steps for the Atheros wireless card, but it doesn't find any network.

```

lspci
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```

And I'm next to the Router, completely open.

---

### Post by eks on 2008-05-23
Confirmed that [solution on post #7 ]("http://ubuntuforums.org/showpost.php?p=4791500&postcount=7")worked for me, on a HP Pavillion dv6705 under a new installation of Hardy 8.04. BUT!!! I had some major problems.

It installed but it wouldn't connect to any network. I could see them but I wouldn't get an IP, no matter what configuration I used, DHPC, zero conf, etc. I tried these two things at once, so don't really know which worked, but they are:
[SIZE="3"]
. also remove the drivers provided with Ubuntu over the restricted drivers (System/Administration/Hardware Drivers)

. install [wicd]("http://wicd.sourceforge.net/download.php").[/SIZE]

Either way, I strongly recommend **wicd**, it's way more feature full and way more **EASY** to understand than the current Network Manager


Cheers and good luck!
eks

---

### Post by HitRefresh on 2008-05-23
eks: 

Do you have any problems with suspend or hibernate now ? 

I also tried the same post on a HP dv6704, and can connect to wireless networks, but now cannot suspend or hibernate the laptop. I have not tried installing wicd, though.

---

### Post by Alfred_McGee on 2008-05-27
This solution worked for me, but appeared to prevent suspend and hibernate functions. The screen would go black and fill with code that said stuff like ath_pci_remove. The only way out was to hold down the power button and then restart. Later, after reinstalling Ubuntu, I was able to get this fix to work:

[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

It uses a different tarball from Madwifi and has some other differences. But, most importantly, suspend now works!:)

---

### Post by nicedude on 2008-05-27
The install guide Alfred McGee has posted a link to above is my guide on how to install the AR5007 within 32BIT Hardy. While it isn't the only way and also is not the easiest ( as I remove the restricted modules and restricted manager completely ). I think its the best way ( personal preference and opinion ) but anyone who uses my way please read it fully and follow it step by step as otherwise it will not work.

Also know you will have to manage whatever other drivers the restricted manager is currently managing for you automatically. The only ones should be any Nvidia or ATI graphics drivers and I like to use the newest ones from the Nvidia site anyway as they work the best and are the most up to date with fixes for my 8400M Nvidia chipsets power management. So please just read my guide before you decide to try it and make sure you understand what you will be required to do if you have a graphics driver that is being currently managed by Jockey (the restricted driver manager) since using my way that will be removed. I have a text file attachment at that link with instructions on how to install the Nvidia Linux driver package from their website ( I can't help with an ATI one as I don't have any ATI graphics cards to test with ) but be advised it is written for after using my Atheros install guide and removing all the restricted modules and manager and as such IT WILL NOT WORK as a guide for installing the Nvidia driver package on a system that still has those components in place. Just felt I should warn all to be careful and study what you do before you attempt it to save problems later. Good luck to all however you choose to install your AR5007. :-)

PS To anyone trying to install madwifi aircrack patched drivers you need the driver version 3366 as the earlier one wouldn't work when I tried it. The driver you need can be found at madwifi.org site support ticket #1679 

Link to the support ticket
[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

Link to the driver you need
[http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)

That driver is needed if you ever want to be able to use aircrack and kismet wifi security and hacking tools.

Hope the info and links help everyone out.

nicedude

---

### Post by RobHK on 2008-06-04
> **ToM-X said:**
> Right, I'm back now like I promised.

**Atheros AR5007EG for hardy.**

First of all go to "System/Administration/Hardware Drivers" and disable by un-ticking the box.:

```
Atheros Hardware Access Layor (Hal) 
```

Then Reboot

Then open the terminal "Applications/Accessories/Terminal" and copy the following:

```
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz 
```

```
sudo apt-get install build-essential
```

```
tar xfz madwifi-ng-r2756+ar5007.tar.gz
```

```
cd madwifi-ng-r2756+ar5007
```

```
make
```

```
sudo make install
```

```
sudo modprobe ath_pci
```

```
sudo reboot
```

Then thats it :D Enjoy!

I've done this successfully on a previous installation but I didn't keep the madwifi file. Today it's gone from the site, though there is one with 2756 replaced by 3366. I thought I'd give it a try but the installation failed at "sudo modprobe ath_pci".

I don't really understand any of this, I'm just following Tom's instructions. So 2 points:

Should the new file work?
Could someone upload the old 2756 file to an FTP service, please?

---

### Post by braveerudite on 2008-06-04
I follow your steps in the same order you post them and I got this error.  What am I doing wrong?

> rambo@Ubuntu64-8:~$ echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
[sudo] password for rambo: 
blacklist ath_pci
rambo@Ubuntu64-8:~$ wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)
--12:36:42--  [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)
           => `ar5007eg-64-0.2.tar.gz'
Resolving blakecmartin.googlepages.com... 209.85.141.118
Connecting to blakecmartin.googlepages.com|209.85.141.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 369,404 (361K) [application/octet-stream]

100%[====================================>] 369,404       30.59K/s    ETA 00:00

12:37:02 (43.07 KB/s) - `ar5007eg-64-0.2.tar.gz' saved [369404/369404]

rambo@Ubuntu64-8:~$ tar xvf ar5007eg-*.tar.gz
ar5007eg-64-0.2/
ar5007eg-64-0.2/ar5007eg/
ar5007eg-64-0.2/ar5007eg/net5211.inf
ar5007eg-64-0.2/ar5007eg/net5211.cat
ar5007eg-64-0.2/ar5007eg/ar5211.sys
ar5007eg-64-0.2/README
rambo@Ubuntu64-8:~$ tar xvf ndiswrapper-newest.tar.gz
tar: ndiswrapper-newest.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
rambo@Ubuntu64-8:~$ 

---

### Post by eks on 2008-06-05
> **Alfred_McGee said:**
> [http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

It uses a different tarball from Madwifi and has some other differences. But, most importantly, suspend now works!:)

Could you post exactly what you did that made the driver work with hibernate/suspend? :)

It's basically the same guide but with a link to the patched driver. (Btw, great work nicedude!).

But yes, HitRefresh, the hibernate/suspend does not work... I don't get any errors, it just disconects and I THINK I cannot reconnect again unless I restart. But I haven't debuged it much and I don't have the laptop currently with me.


eks

---

### Post by eks on 2008-06-05
You are just missing the ndiswrapper-newest.tar.gz. From the rest of the code it doesn't seem that you have downloaded it.

> **braveerudite said:**
> I follow your steps in the same order you post them and I got this error.  What am I doing wrong?
```

rambo@Ubuntu64-8:~$ tar xvf ndiswrapper-newest.tar.gz
tar: ndiswrapper-newest.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
rambo@Ubuntu64-8:~$

```

---

### Post by mikey.duhhh on 2008-06-05
**[SIZE="4"]When the Kernel updates[/SIZE]**

There is one thing you should mention.  When the kernel updates you will lose your wifi again. To fix this you will 
need to tick and then untick the Atheros Hardware Access Layer (HAL), 

Reboot.

Open the terminal and  

```
cd madwifi-ng-r2756+ar5007
```

```
sudo make install
```

```
sudo modprobe ath_pci
``` 

```
sudo reboot
```

There is no need to make it again since you have done this already, but
you will need to make install and modprobe ath_pci to set the changes needed to run the wifi in the newer kernel.

Also save this to Tomboy or a file so you won't forget what to do when 
the kernel ...18 becomes ...19 becomes ...20 ...21, etc.



> **ToM-X said:**
> Right, I'm back now like I promised.

**Atheros AR5007EG for hardy.**

First of all go to "System/Administration/Hardware Drivers" and disable by un-ticking the box.:

```
Atheros Hardware Access Layor (Hal) 
```

Then Reboot

Then open the terminal "Applications/Accessories/Terminal" and copy the following:


```
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz 
```

```
sudo apt-get install build-essential
```

```
tar xfz madwifi-ng-r2756+ar5007.tar.gz
```

```
cd madwifi-ng-r2756+ar5007
```

```
make
```

```
sudo make install
```

```
sudo modprobe ath_pci
```

```
sudo reboot
```

Then thats it :D Enjoy!

---

### Post by braveerudite on 2008-06-07
I did both steps... In fact I did those two steps before I read your post.  I'm having trouble connecting too :( and other suggestions?

---

### Post by lorgonjortle on 2008-06-07
> **ToM-X said:**
> I'm working on Atheros AR5007EG, I'l get back to you if I get anywhere.

Same situation I bet.

I have the same one, please PM me if you find an answer.

---

### Post by daRealScanMan on 2008-06-07
> **lorgonjortle said:**
> I have the same one, please PM me if you find an answer.
Did you read Tom's post #7?  However, the 2756 driver isn't available anymore, you'll have to use the 3366.

[http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)

---

### Post by braveerudite on 2008-06-08
Here is the answer to all your prayers.  Finally!!! a super simple method that will works 100% with Ubuntu 8.04 “Hardy Heron” 64bit and Atheros AR2425 (AR5007EG) chipset. No more the need ndiswrapper or even Wi-Fi Radar and WICD to get secure (WPA2,WEP) connection working.  You can just keep the default Ubuntu wired and wireless network manager because now it just works with no problem. 

Make sure you go to System ->Administration ->Hardware Drivers and disable Atheros (HAL) & Atheros support and reboot before you follow the steps on the guide.  At the end of the guide you'll see that it will ask you to re-enable them again and reboot.

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

Thank the guy that posted the guide last night by clicking on his Gold star with a blue ribbon on the right.

---

### Post by DapperMe17 on 2008-06-10
Hello,


Any way someone can upload blakemartin's 64-bit driver for the AR5007???

Also, is "build-essentials" on the LiveCD, and how would I extract it from the CD???


Unfortunately, I dont have a current internet connection to this machine...


Thanks for any help!

---

### Post by rjkola on 2008-06-10
I tried ToM-X's fix posted on April 25'2008. Followed his directions and all but ( sudo modprobe ath_pci ) worked. Now using the AR5007 card. It's in a HP dv6704nr cheepy laptop running Ubuntu 8.04 AMD64 under wubi. I tried most all of the other posted fixes, was getting bleary eyed and miss typed a lot...suffered through and BINGO! Thanks for a great fix.:
:)

---

### Post by julianna on 2008-06-10
Thanks Tom - I'm totally a newbie at this system, and your steps worked just fine for my Compaq F762NR.  A dozen yellow roses to you, friend.  Thanks again.

---

### Post by logrusmage on 2008-06-10
Alright, again, I can see networks but cannot connect to them.

What the hell man...

---

### Post by coltcannon on 2008-06-12
Just sitting here today I lost wifi, which had been working previously in the day. I tried to reinstall with no success. Anyone got an idea on getting the wireless setup back to a fresh install type state?

---

### Post by coltcannon on 2008-06-12
Interesting, I restarted and the wifi was working for about an hour. Now it just stopped again.

---

### Post by wwusnobrdr on 2008-06-12
I believe the upgrade to hal may have killed my wireless.  I re-compiled the 3366 snapshot and installed it.  When I did modprobe ath_pci, this is what I got 
> 
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-19-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
> 
[  302.072923] ath_pci: disagrees about version of symbol _ath_hal_attach
[  302.072942] ath_pci: Unknown symbol _ath_hal_attach
[  302.073105] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[  302.073109] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  302.073356] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[  302.073360] ath_pci: Unknown symbol ath_hal_computetxtime
[  302.073627] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[  302.073631] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  302.073909] ath_pci: Unknown symbol _ath_hal_detach
[  302.075239] ath_pci: disagrees about version of symbol ath_hal_init_channels
[  302.075244] ath_pci: Unknown symbol ath_hal_init_channels
[  302.075467] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[  302.075471] ath_pci: Unknown symbol ath_hal_getwirelessmodes


---

### Post by daRealScanMan on 2008-06-12
> **wwusnobrdr said:**
> I believe the upgrade to hal may have killed my wireless.  I re-compiled the 3366 snapshot and installed it.  When I did modprobe ath_pci, this is what I got
Did you first uninstall the older kernel module?  Something like:
```
cd /path/to/madwifi
sudo make uninstall
sudo make clean
sudo make
sudo make install
sudo modprobe ath_pci

```

---

### Post by coltcannon on 2008-06-12
> **daRealScanMan said:**
> Did you first uninstall the older kernel module?

I tried this and still cant connect. I can see the networks but cant connect.

---

### Post by coltcannon on 2008-06-13
Hmm I can connect to my FON router but only through the non-secure SSID. Isnt there a file that contains the wifi security info? Could it be corrupt?

---

### Post by williamson389 on 2008-06-14
i had my wireless working after scouring thru the forums and finding a website on google--([http://blog.linuxoss.com/2008/05/08/ubuntu-804-enabling-atheros-ar5007-based-wireless/](http://blog.linuxoss.com/2008/05/08/ubuntu-804-enabling-atheros-ar5007-based-wireless/))

I held off on the updates because i had a feeling they would screw m over. then last night i updated and behold, my wireless was out again.  now i find that the madwifi patch is no longer availible?  i have the tar file still on my computer but am unsure of how to install again.  i tried some of the ideas in similar posts and none have worked. im running 32  bit.

Any ideas?  

also does anyone know for sure what happened to the madwifi.org site?  and will it be fixed?

---

### Post by lunatik90 on 2008-06-14
williamson389, look in this topic: [http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)

fixed my problem using the ubuntu for EEE PC installation

---

### Post by abhilashkumar on 2008-06-15
> **williamson389 said:**
> i had my wireless working after scouring thru the forums and finding a website on google--([http://blog.linuxoss.com/2008/05/08/ubuntu-804-enabling-atheros-ar5007-based-wireless/](http://blog.linuxoss.com/2008/05/08/ubuntu-804-enabling-atheros-ar5007-based-wireless/))

I held off on the updates because i had a feeling they would screw m over. then last night i updated and behold, my wireless was out again.  now i find that the madwifi patch is no longer availible?  i have the tar file still on my computer but am unsure of how to install again.  i tried some of the ideas in similar posts and none have worked. im running 32  bit.

Any ideas?  

also does anyone know for sure what happened to the madwifi.org site?  and will it be fixed?

@williamson
Madwifi does break every time the system undergoes a kernel update.
However, I have always been able to get it working again by recompiling the madwifi drivers for the new kernel

If you still have the extracted madwifi drivers from last time, just go there again and recompile.

How I do it is:

1. Go into the folder (extracted madwifi)

2. Cleanup previous compile.
```
sudo make uninstall
```
```
sudo make clean
```

3. Recompile madwifi for the current kernel
```
sudo make
```
```
sudo make install
```

4. Bring up the card to connect
```
sudo modprobe ath_pci
```

This works for me everytime.

Let me know if it works!

Cheers!

---

### Post by williamson389 on 2008-06-15
aaaaaaaaa!! this is very frustrating i have tried multiple steps to get my wireless back since i updated and none have worked.
@abhilashkumar thank you.. it looked like it was working.  i only had a problem at the command sudo make.   it replied ther is command to make. or something like that.  i continued with it and the other steps apperaed to be working but no dice.  wireless networks dont even show up in Wicd.  i dont know if it is the type of madwifi file i am usig. based on other threads if i am using the wrong one then nothing will take effect.  i used the 3366 one idk if that is right.

the original patch i used was r2756-5007...this was before the update knocked out my wireless.

---

### Post by abhilashkumar on 2008-06-15
> **williamson389 said:**
> aaaaaaaaa!! this is very frustrating i have tried multiple steps to get my wireless back since i updated and none have worked.
@abhilashkumar thank you.. it looked like it was working.  i only had a problem at the command sudo make.   it replied ther is command to make. or something like that.  i continued with it and the other steps apperaed to be working but no dice.  wireless networks dont even show up in Wicd.  i dont know if it is the type of madwifi file i am usig. based on other threads if i am using the wrong one then nothing will take effect.  i used the 3366 one idk if that is right.

the original patch i used was r2756-5007...this was before the update knocked out my wireless.

the madwifi version that I am using is > madwifi-ng-r2756+ar5007
This has been working for me right through Gutsy and now Hardy. I have been using this for the lat 4-5 months.

Which one are you using?

---

### Post by williamson389 on 2008-06-15
i solved my problem finally. i used nicedudes walkthrough. it didnt work for me before so i didnt bother trying it until now. here's the link: [http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

i have a feeling it worked this time because i unistall all of linux-restricted-modules in synaptic

Good Luck

---

### Post by cynicall on 2008-07-01
Hello, 

I have followed the steps in the post but it does not seem to work for me. I have a 32 bit and when I run make it gives me an error: 


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential
hasan@hasan-laptop:~/Masaüstü$ 


MAKE in /madwifi-ng-r2756+ar5007 D&#304;RECTORY

Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  HOSTCC  /home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: At top level:
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: In function 'main':
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal/uudecode] Error 1
make[2]: *** [/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007/ath_hal] Error 2
make[1]: *** [_module_/home/hasan/Masaüstü/madwifi-ng-r2756+ar5007] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2

I have disabled HAL and rebooted and it did not work. Thanks in advance.

---

### Post by abhilashkumar on 2008-07-01
You need to install build essential

"sudo apt-get install build-essential" to compile stuff..

Then try the make commands!

---

### Post by abhilashkumar on 2008-07-01
> **williamson389 said:**
> i solved my problem finally. i used nicedudes walkthrough. it didnt work for me before so i didnt bother trying it until now. here's the link: [http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

i have a feeling it worked this time because i unistall all of linux-restricted-modules in synaptic

Good Luck

Are you saying WICD worked for you?
It was one on the options I had gone through when I was setting up. I was using WICD with ndiswrapper. The whole thing broke on upgrade to newer kernel.

Till date madwifi is the only thing giving me the goods with minimum interference. (the only thing is the recompile after kernel upgrade)

---

### Post by Johnytxtc on 2008-07-04
This line never works for me in 64bit it just wont happen:

computer@computer-laptop:~$ tar xvf ndiswrapper-newest.tar.gz
tar: ndiswrapper-newest.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

If i just miss this out later i get stuck here:

sudo ndiswrapper -i net5211.inf
couldn't open net5211.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.


whats wrong with it why cant i just get a simple thing like wireless to work on this thing :(

---

### Post by coltcannon on 2008-07-04
I had been having trouble with my wifi going out randomly and not connecting to a network it had just been connected to. I was using the madwifi 3366, I started using the 2756 and have had a much much more reliable connection.

---

### Post by hkbruvold on 2008-07-07
> **ToM-X said:**
> Right, I'm back now like I promised.

**Atheros AR5007EG for hardy.**

First of all go to "System/Administration/Hardware Drivers" and disable by un-ticking the box.:

```
Atheros Hardware Access Layor (Hal) 
```

Then Reboot

Then open the terminal "Applications/Accessories/Terminal" and copy the following:

```
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz 
```

```
sudo apt-get install build-essential
```

```
tar xfz madwifi-ng-r2756+ar5007.tar.gz
```

```
cd madwifi-ng-r2756+ar5007
```

```
make
```

```
sudo make install
```

```
sudo modprobe ath_pci
```

```
sudo reboot
```

Then thats it :D Enjoy!

THANKS, that really works!!! :):)

---

### Post by johndoe32102002 on 2008-07-12
The instructions did not work to fix the Atheros wireless drivers on a 64-bit Compaq F756NR.

I hope that Ubuntu fixes this error in the future.

---

### Post by williamson389 on 2008-07-13
@Abhilashkumar, 
yes my wicd works.  i am not using network manager or ndiswrapper.  my problem was that wicd would not recognize an wireless signal even though my computer had recognized the card.
does anyone know if this bug will be fixed soon b/c i am anxious to update again as i feel i am missing out. :)

---

### Post by Mindcrime13 on 2008-07-22
hello guys,

i currently bought a sont vaio VGN-NR220E for my GF it borught windows vista on it, wich it sucks, it was sluggish and horrible, anyway i remove i and intall ubuntu, wich is great and fast, the computer has a atheros242x card with a on off switch in the outside case, 

i have tried this with no luck, i have very little experience with terminal :

> **Pinoy915 said:**
> Success!!! I have my wireless card working! I am using ndiswrapper with 64 bit drivers. Here is the thread I used to get mine working. [http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

Here are the only steps I used. I did not disable anything in the restricted drivers menu.

Go to System/Administration/Hardware Drivers. Disable the default drivers by unchecking "Atheros Hardware Access Layer(HAL)" and "Support for Atheros 802.11 Wireless LAN cards." Reboot if necessary.

Blacklist the default driver:

```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

Get the 64 bit driver:
```
wget http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz
```

Extract driver:
```
tar xvf ar5007eg-*.tar.gz
tar xvf ndiswrapper-newest.tar.gz
```

Ensure you have your kernel headers and the build essential package.
```
sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential
```

Install ndisgtk:

```
sudo apt-get install ndisgtk
```

Either use ndisgtk to install the driver or:

```
sudo ndiswrapper -i net5211.inf
```

Load up ndiswrapper every time Linux is loaded:
```
sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules
```

Restart:
```
sudo reboot
```

My card was detected and shows available networks but if it does not, try ```
sudo iwlist scan
```

My laptop is a Compaq C751NR. lspci gives me:
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

I am running Ubuntu AMD64 8.04. Oh and by the way, the button for my wireless network is orange(off) and will not turn blue(on) but it is indeed working. It just will not change colors. The actual button works though.



what else can i do to get the wireless working?

thanks for your help

---

### Post by Mindcrime13 on 2008-07-24
thanks for this thread

---

### Post by chudux on 2008-07-24
Would EasyBCD for dual booting cause an issue with the process required to make the Athros work?
[http://ubuntuforums.org/showthread.php?t=868589]("http://ubuntuforums.org/showthread.php?t=868589")

---

### Post by Jeztastic on 2008-07-27
This info is out of date, readme in the tarball states:> You most likely downloaded this tarball since you are looking for a version
of MadWifi which supports the AR5007 chipset family, which is for example
used in the EeePC.

However, since you've downloaded this tarball, you've followed outdated
instructions. The code that this tarball once contained is now obsolete.
Please follow these instructions to enable your AR5007-based WLAN device:
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

If you have any questions about it, please contact our regular support
channels:
[http://madwifi.org/wiki/Support](http://madwifi.org/wiki/Support)

Thanks.

---

### Post by eks on 2008-07-29
So Atheros is releasing a free official driver with the support from the community:

[http://madwifi.org/wiki/news/20080725/ath9k-atheros-unveils-free-linux-driver-for](http://madwifi.org/wiki/news/20080725/ath9k-atheros-unveils-free-linux-driver-for)

Anyone knows when this might hit the repos?

And I supose I should just enable the driver on the (Restricted) Hardware Drivers? But how do I know that's the latest official one?


eks

PS: I'm really interested in this because the madwifi one kept broking on each kernel update, and my wife needs to take de laptop for a long trip soon and doesn't know how to compile from source...

---

### Post by Pinoy915 on 2008-07-29
I have been using 32-bit but decided to go back to 64-bit. This howto is much easier than what I have done before for those who have Atheros and running 64-bit Hardy Heron.

[http://ubuntuforums.org/showthread.php?t=816780&highlight=atheros+amd64]("http://ubuntuforums.org/showthread.php?t=816780&highlight=atheros+amd64")

---

### Post by avinash_destiny on 2008-09-22
Everything worked fine but the ndiswrapper is showing as invalid driver(net5211)

hardy 8.04 64 bit

lspci:

01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

aspire4520

---

### Post by XMaverickX on 2008-09-29
> **braveerudite said:**
> Here is the answer to all your prayers.  Finally!!! a super simple method that will works 100% with Ubuntu 8.04 “Hardy Heron” 64bit and Atheros AR2425 (AR5007EG) chipset. No more the need ndiswrapper or even Wi-Fi Radar and WICD to get secure (WPA2,WEP) connection working.  You can just keep the default Ubuntu wired and wireless network manager because now it just works with no problem. 

Make sure you go to System ->Administration ->Hardware Drivers and disable Atheros (HAL) & Atheros support and reboot before you follow the steps on the guide.  At the end of the guide you'll see that it will ask you to re-enable them again and reboot.

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

Thank the guy that posted the guide last night by clicking on his Gold star with a blue ribbon on the right.

Ricght you are ^^^ It just worked perfect, just remember to accept the web address when you have to download the file with a "t" I didnt the first time and it didnt work lol

---

### Post by datanalytics.com on 2008-09-29
I have this card on a AMD64 platform. I followed the instructions and the ndiswrapper plugin is up and working.

However, sometimes I was unable to get a MAC address for a given ESSID, as reported by the iwconfig command. I could scan and see the networks, but sometimes, the connection would just be impossible.

Finally I found a workaround. After a reboot, if I cannot get the MAC address of a network, I reload ndiswrapper:

sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

After that, the card works like a charm.

---

### Post by edyeeh on 2008-10-10
New Note 9

> **major_rocks said:**
> ok, it got a bit late last night........anyways. After a reboot i ran into issues of network manager seeing wireless networks but again not being able to connect. This morning i made the switch from Network-Manager to Wicd, and BADA-BING! no more problems.

Just thought i'd post that for anyone else having the same issues .=)

thnx to major_rocks for the tip! its functioning now. Not only that  WICD has has a better interface (better panel) and has more options. I just wonder if its because it can flush the route table that it works unlike network manager.


> **datanalytics.com said:**
> I have this card on a AMD64 platform. I followed the instructions and the ndiswrapper plugin is up and working.

However, sometimes I was unable to get a MAC address for a given ESSID, as reported by the iwconfig command. I could scan and see the networks, but sometimes, the connection would just be impossible.

Finally I found a workaround. After a reboot, if I cannot get the MAC address of a network, I reload ndiswrapper:

sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

After that, the card works like a charm.

I also do this every time I want to connect. I'm still finding a script to do this at boot since i don't know how to write one :D. try installing WICD, it solved my problem.

---

### Post by schase02 on 2008-10-12
The source files were updated.
Download latest here.

[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/)

move it to home directory

follow ToM-X's steps here
[http://ubuntuforums.org/showpost.php?p=4791500&postcount=7](http://ubuntuforums.org/showpost.php?p=4791500&postcount=7)

skip the wget (since you downloaded it) and replace the hal name above for the madwifi-ng-r2756+ar5007.tar.gz bit that ToM-X notes.

Worky worky 
:popcorn:

---

### Post by Jenga-kun on 2008-10-12
> **ToM-X said:**
> Right, I'm back now like I promised.

**Atheros AR5007EG for hardy.**

First of all go to "System/Administration/Hardware Drivers" and disable by un-ticking the box.:

```
Atheros Hardware Access Layor (Hal) 
```

Then Reboot

Then open the terminal "Applications/Accessories/Terminal" and copy the following:

```
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz 
```

```
sudo apt-get install build-essential
```

```
tar xfz madwifi-ng-r2756+ar5007.tar.gz
```

```
cd madwifi-ng-r2756+ar5007
```

```
make
```

```
sudo make install
```

```
sudo modprobe ath_pci
```

```
sudo reboot
```

Then thats it :D Enjoy!

Nothing happens when I enter 

```
tar xfz madwifi-ng-r2756+ar5007.tar.gz
```

into terminal.

---

### Post by donaldshelton on 2008-10-12
everything was great until I entered "make" into the terminal 

make: *** No targets specified and no makefile found.  Stop

Now What?

---

### Post by schase02 on 2008-10-12
donald
read two posts above yours

---

### Post by nomind111 on 2008-10-18
Hello all, I followed the above instructions and this is what i got when i typed "make." the success ended there...

vichara@sage:~$ Atheros Hardware Access Layor (Hal)
bash: syntax error near unexpected token `('
vichara@sage:~$ wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
--10:29:39--  [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
           => `madwifi-ng-r2756+ar5007.tar.gz.1'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 485 [application/x-gzip]

100%[=============================================================================================>] 485           --.--K/s             

10:29:40 (29.12 MB/s) - `madwifi-ng-r2756+ar5007.tar.gz.1' saved [485/485]

vichara@sage:~$ sudo apt-get install build-essential
[sudo] password for vichara: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
vichara@sage:~$ tar xfz madwifi-ng-r2756+ar5007.tar.gz
vichara@sage:~$ cd madwifi-ng-r2756+ar5007
vichara@sage:~/madwifi-ng-r2756+ar5007$ make
make: *** No targets specified and no makefile found.  Stop.
vichara@sage:~/madwifi-ng-r2756+ar5007$ 

any help or advice is greatly appreciated.  i dont have 64bit installed

---

### Post by gsimpson on 2008-10-19
Worked  great thanks. Had to put SUDO in front of MAKE for it to work.

ACER laptop Aspire 4315

---

### Post by smooth3006 on 2008-10-19
> **schase02 said:**
> The source files were updated.
Download latest here.

[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/)

move it to home directory

follow ToM-X's steps here
[http://ubuntuforums.org/showpost.php?p=4791500&postcount=7](http://ubuntuforums.org/showpost.php?p=4791500&postcount=7)

skip the wget (since you downloaded it) and replace the hal name above for the madwifi-ng-r2756+ar5007.tar.gz bit that ToM-X notes.

Worky worky 
:popcorn:

i downloaded the current version and you cannot use madwifi-ng-r2756+ar5007, you have to use the current version name. unless im doing something wrong ? when you install a new version of the madwifi don't you have to delete the old version first ? how can this be done ? 

has anybody had any luck getting their wireless kill switch and led to work on laptops ?

---

### Post by feelinggood on 2008-10-20
Can someone show me the code to use for the updated file.  I have been trying to replace the old version with the hal version but it is not working.  Thanks, Steve

---

### Post by smooth3006 on 2008-10-20
> **feelinggood said:**
> Can someone show me the code to use for the updated file.  I have been trying to replace the old version with the hal version but it is not working.  Thanks, Steve

use this guide, it worked for me. 

[http://it.dennyhalim.com/2008/08/atheros-5007-wifi-ar2425-chips-linux.html]("http://it.dennyhalim.com/2008/08/atheros-5007-wifi-ar2425-chips-linux.html")


:KS

---

### Post by feelinggood on 2008-10-20
Finally got the wireless up and running.  Used this from another thread and it worked perfectly.  Still have orange light but wireless works.  Any way to get blue light on would be great.  Steve

Re: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01
Quote:
Originally Posted by reasoner View Post
Thanks so much to those above for figuring this out for me. Let me spell out the installation in a little more detail to save those after me some time.

I did this on a fresh Ubuntu 8.04 install on a Compaq Presario C770US Laptop with an ethernet cable plugged into my router.

The device string displayed by lspci -v was as follows:

Code:

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 91300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

First under System/Administration/HarwareDrivers disable both the Atheros HAL and the Atheros wireless thing and then reboot.

The kernel headers and the compiler are needed to build this driver so I started by installing build-essential. In a terminal window (Applications/Accessories/Terminal) enter:

Code:

sudo apt-get install build-essential

The driver code will be downloaded with the subversion source code manager so I installed subversion:

Code:

sudo apt-get install subversion

I needed a place to put the driver source without mixing it up with other stuff so I changed directory to my home directory:

Code:

cd ~

Created a directory:

Code:

mkdir madwifi

And changed to the new dirctory:

Code:

cd madwifi

Use subversion to download (checkout) a copy of the code:

Code:

svn co [https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6](https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6)

The above command failed for me at first because subversion couldn't find svn.madwifi.org
Madwifi will probably have their DNS problems worked out by the time you read this. But if not then see the section at the bottom of this post titled "Cant find svn.madwifi.org" for a solution before continuing.

After the driver code is downloaded by subversion, change to the directory, which should be madwifi-hal-0.10.5.6

Code:

cd madwifi-hal-0.10.5.6

Run the make script to have the compiler build the driver:

Code:

make

Install the driver

Code:

sudo make install

Add the Atheros kernel module to the list of modules to be automatically loaded at boot by adding "ath_pci" (without the quotes) to the end of the /etc/modules file. I used the vi editor which I won't describe here. Gedit is probably easy to use so try:

Code:

sudo gedit /etc/modules

Now you can reboot and it should work. To get it working without a reboot you need to load the module manually:

Code:

sudo modprobe ath_pci

That should do it. The little wireless button seems to always stay lit orange. When I press it it seems to disable the wireless but it still stays lit orange. WPA works for me. I assume WEP will also. I haven't tried WPA2



CANT FIND svn.madwifi.org

If subversion has a hard time finding svn.madwifi.org then add it's IP address to your hosts file. I found this page [http://madwifi.org/ticket/1982](http://madwifi.org/ticket/1982) at madwifi.org that gives the IP address 217.24.1.142 of svn.madwifi.org in one of the last messages. I tried just giving subversion the command to connect to the IP address instead of the domain name, but it failed before finishing the checkout. Edit the file /etc/hosts and add "217.24.1.142 svn.madwifi.org" (without the quotes). I added it just after the 127.0.1.1 line

Code:

sudo gedit /etc/hosts

Now you can continue with the subversion checkout. You should probably remove this line from your hosts file when you're done with this so that if you want to go back there some day and they've moved it then DNS will give the most recent IP address.

---

### Post by smooth3006 on 2008-10-21
> **feelinggood said:**
> Finally got the wireless up and running.  Used this from another thread and it worked perfectly.  Still have orange light but wireless works.  Any way to get blue light on would be great.  Steve

Re: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01
Quote:
Originally Posted by reasoner View Post
Thanks so much to those above for figuring this out for me. Let me spell out the installation in a little more detail to save those after me some time.

I did this on a fresh Ubuntu 8.04 install on a Compaq Presario C770US Laptop with an ethernet cable plugged into my router.

The device string displayed by lspci -v was as follows:

Code:

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 91300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

First under System/Administration/HarwareDrivers disable both the Atheros HAL and the Atheros wireless thing and then reboot.

The kernel headers and the compiler are needed to build this driver so I started by installing build-essential. In a terminal window (Applications/Accessories/Terminal) enter:

Code:

sudo apt-get install build-essential

The driver code will be downloaded with the subversion source code manager so I installed subversion:

Code:

sudo apt-get install subversion

I needed a place to put the driver source without mixing it up with other stuff so I changed directory to my home directory:

Code:

cd ~

Created a directory:

Code:

mkdir madwifi

And changed to the new dirctory:

Code:

cd madwifi

Use subversion to download (checkout) a copy of the code:

Code:

svn co [https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6](https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6)

The above command failed for me at first because subversion couldn't find svn.madwifi.org
Madwifi will probably have their DNS problems worked out by the time you read this. But if not then see the section at the bottom of this post titled "Cant find svn.madwifi.org" for a solution before continuing.

After the driver code is downloaded by subversion, change to the directory, which should be madwifi-hal-0.10.5.6

Code:

cd madwifi-hal-0.10.5.6

Run the make script to have the compiler build the driver:

Code:

make

Install the driver

Code:

sudo make install

Add the Atheros kernel module to the list of modules to be automatically loaded at boot by adding "ath_pci" (without the quotes) to the end of the /etc/modules file. I used the vi editor which I won't describe here. Gedit is probably easy to use so try:

Code:

sudo gedit /etc/modules

Now you can reboot and it should work. To get it working without a reboot you need to load the module manually:

Code:

sudo modprobe ath_pci

That should do it. The little wireless button seems to always stay lit orange. When I press it it seems to disable the wireless but it still stays lit orange. WPA works for me. I assume WEP will also. I haven't tried WPA2



CANT FIND svn.madwifi.org

If subversion has a hard time finding svn.madwifi.org then add it's IP address to your hosts file. I found this page [http://madwifi.org/ticket/1982](http://madwifi.org/ticket/1982) at madwifi.org that gives the IP address 217.24.1.142 of svn.madwifi.org in one of the last messages. I tried just giving subversion the command to connect to the IP address instead of the domain name, but it failed before finishing the checkout. Edit the file /etc/hosts and add "217.24.1.142 svn.madwifi.org" (without the quotes). I added it just after the 127.0.1.1 line

Code:

sudo gedit /etc/hosts

Now you can continue with the subversion checkout. You should probably remove this line from your hosts file when you're done with this so that if you want to go back there some day and they've moved it then DNS will give the most recent IP address.

im having the same issue with wireless working but no blue led and the kill switch does not work.

---

### Post by nomind111 on 2008-10-21
hello, i am confused with the instructions when you say "move it to your home directory". i dont know how to do that, and can you give the example when you say replace such and such with the above.  i think i know what you mean but it still wasnt clear. thanks SCHASE.

I DOWNLOADED THE most recent snapshot, sept 07 i believe from the link at the top that schase gave.  i saved it to my desktop. do i extract it? im guessing no since that was never mentioned.  then i go to terminal and skip the wget like schase said and tried to replace the filename so i typed this...

tar xfz madwifi-hal-0.10.5.6/

is that what you mean??

i also tried using this guide which was said to work and got a little further but not much...

[http://it.dennyhalim.com/2008/08/atheros-5007-wifi-ar2425-chips-linux.html](http://it.dennyhalim.com/2008/08/atheros-5007-wifi-ar2425-chips-linux.html)

it worked for other ppl, maybe itll work for you.

---

### Post by wadams on 2008-10-21
Tom-X's instructions do not work for me!!!!!!!!!

---

### Post by nomind111 on 2008-10-23
use this it worked for me, and is the most easy to understand and simple for new users.  read the comment at the bottom of the link if you are gettin error. it fixed my problem.:)

[http://it.dennyhalim.com/2008/08/atheros-5007-wifi-ar2425-chips-linux.html]("http://it.dennyhalim.com/2008/08/atheros-5007-wifi-ar2425-chips-linux.html")

wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
tar zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-current/scripts 
sudo ./madwifi-unload
sudo ./find-madwifi-modules.sh $(uname -r)
cd ..
make
sudo make install

if cd madwifi-hal-0.10.5.6-current/scripts is not working for you (it didn't for me), cd madwifi-hal-[tab]/scripts worked for me.  this is what the guy told me to do.  DONT type tab, but hit the tab button after cd madwifi-hal- and it should work.

---

### Post by arunvir on 2008-10-23
I have posted on how to do this in my blog. Here are the links:-

[http://technoemperor.blogspot.com/2008/10/getting-wireless-to-work-in.html](http://technoemperor.blogspot.com/2008/10/getting-wireless-to-work-in.html)
[http://technoemperor.blogspot.com/2008/10/getting-wireless-to-work-in_05.html](http://technoemperor.blogspot.com/2008/10/getting-wireless-to-work-in_05.html)
[http://technoemperor.blogspot.com/2008/10/getting-wireless-to-work-in_4015.html](http://technoemperor.blogspot.com/2008/10/getting-wireless-to-work-in_4015.html)

Check these links. Has for both madwifi and ndiswrapper installations. and how to get the Led working with ndiswrapper.

All the Best!!!!!!!

< posting like this can be considered self publicizing>:lolflag::lolflag::lolflag:

---

### Post by indian_gamer2003 on 2008-10-28
FYI the file specified on the first page is a outdated madwifi version, use the latest version from here instead 
> [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/)

---

### Post by schase02 on 2008-10-31
Works in Intrepid too.

btw, I used these same directions (with the update I had posted earlier) and it worked okay.

The only difference was on Hardware Drivers I needed to leave "Support for Atheros 802.11 wireless LAN cards" enabled.

---

### Post by pasencorelui on 2008-11-02
The link is brocken, the site madwifi.org is unavailable. Is there a way to get madwifi-hal-0.10.5.6 somewhere else or is someone can share it??


Thank you

---

### Post by pasencorelui on 2008-11-02
madwifi.org is unreachable. is there another way to get madwifi-hal-0.10.5.6 ? Is someone can share or indicate a mirror to get it?

Thank's

---

### Post by The Judderman on 2008-11-05
Yep! The link is still broken! Any ideas?

Thanks

---

### Post by The Judderman on 2008-11-05
Here is the link to the tar file:


[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)

I hope this works!

---

### Post by RealG187 on 2008-12-30
I type make on the tar and get this

> mpg@MIKED6:~/Desktop/Atheros AR5007/madwifi-hal-0.10.5.6-r3875-20081105$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/mpg/Desktop/Atheros AR5007/madwifi-hal-0.10.5.6-r3875-20081105 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** No rule to make target `AR5007/madwifi-hal-0.10.5.6-r3875-20081105'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
mpg@MIKED6:~/Desktop/Atheros AR5007/madwifi-hal-0.10.5.6-r3875-20081105$ 


Sh*t ain't working. Please help me

---

### Post by kevdog on 2008-12-30
I dont mean to intrude on your guys progress, but I've read that the new ath9k module now supports the ar5007 chipset.  This is an alternative to the closed source madwifi solution with the modified build as is currently being discussed.  Note it is an alternative and not a replacement.

I know this ath9k driver is included in the Ibex kernel by default, but I don't believe it was in Hardy's kernel.  To make a .deb file of the ath9k driver that you can then install for kernel's older than Intrepid's:
sudo dpkg -i <package_name>
This post describes the process:[http://ubuntuforums.org/showpost.php?p=5535562&postcount=3](http://ubuntuforums.org/showpost.php?p=5535562&postcount=3)

Once the driver is installed, you can use the driver by typing:
sudo modprobe ath9k
To have the driver loaded at boot time:
echo ath9k | sudo tee -a /etc/modules

Just an alternative suggestion to what is being suggested here.

---

### Post by RealG187 on 2008-12-30
Now it's working I don't know what I did.

I moved the folder from my desktop right to my home folder (originall to avoid having to type cd Desktop/Atheros .../madwifi....

I then type make and make install and it worked. I got an error at "modprobe ath_pci
" but restarted and it worked....

UPDATE: I [installed 8.10](http://ubuntuforums.org/showthread.php?p=6480892#post6480892), will this work?

---

### Post by BinaryHex on 2009-01-10
> **RealG187 said:**
> 
UPDATE: I [installed 8.10](http://ubuntuforums.org/showthread.php?p=6480892#post6480892), will this work?

8.10 (64-bit) works for me, after installing linux-backports-modules-intrepid-generic

---

### Post by RealG187 on 2009-01-10
> **Pinoy915 said:**
> I did not disable anything in the restricted drivers menu.

Go to System/Administration/Hardware Drivers. Disable the default drivers by unchecking "Atheros Hardware Access Layer(HAL)" and "Support for Atheros 802.11 Wireless LAN cards."

The restricted drivers option is under System/Administration/Hardware Drivers now, so you did disable it.

---

### Post by RealG187 on 2009-01-10
> **BinaryHex said:**
> 8.10 (64-bit) works for me, after installing linux-backports-modules-intrepid-generic

Did you do the madwifi method or the NDISWRAPPER method?
I got it working on Ubuntu 8.10 x86 ..

---

### Post by BinaryHex on 2009-01-19
> **RealG187 said:**
> Did you do the madwifi method or the NDISWRAPPER method?
I got it working on Ubuntu 8.10 x86 ..

After installing the backports package and rebooting, it worked without any additional configuration.  Just keyed the password into network manager and it was all done.

---

### Post by Ketara on 2009-01-26
I had this issue a while back in Hardy, fixed it through the madwifi method, was pretty easy.

Upgraded to Intrepid and tried the backports solution since it sound simpler, and installing the backports package seems to have fubar'd my graphics card. Intrepid will only run in "low graphics mode" now, even after removing the package.

Edit: Apparently I did not properly remove the packages, removing them did in fact fix it.

---

### Post by Ketara on 2009-01-26
Hmm.

Going the madwifi route in Intrepid did not seem to fix it.

I didn't get any errors, but still cannot see wireless.

---

### Post by RealG187 on 2009-05-20
Does this device work on 9.04?

---

### Post by RobHK on 2009-05-21
> **RealG187 said:**
> Does this device work on 9.04?

Yes. Out of the box! (And my SiS graphics as well!)

---

### Post by RealG187 on 2009-05-21
So they fixed whatever caused it not to work on 8.04? That's good, that's one of the things that's a significant factor in my decision to upgrade. I think a cool feature is that I have autorun.inf files on my flash drives that have custom icons in windows. In 8.10 I don't see the custom icons but in 9.04 I do! I didn't think that would happen since autorun.inf is for windows...

---

### Post by KiNiMa on 2009-06-09
> **jdv1800 said:**
> I have an Atheros AR5007 wireless network adapter that isn't turning on with Hardy 8.04. There is one of those unsupported drivers that shows up in system. Any ideas?

[https://help.ubuntu.com/community/WifiDocs/Device/AR5007](https://help.ubuntu.com/community/WifiDocs/Device/AR5007)

without command line: 
cd ..

---

### Post by KiNiMa on 2009-06-09
> **Farivan said:**
> I'm having the same problem, and as an absolute new-comer to ubuntu I'd appreciate any advice anyone could offer...


[https://help.ubuntu.com/community/WifiDocs/Device/AR5007](https://help.ubuntu.com/community/WifiDocs/Device/AR5007)

without command line: 
cd ..

---

### Post by RobHK on 2009-06-09
> **KiNiMa said:**
> [https://help.ubuntu.com/community/WifiDocs/Device/AR5007](https://help.ubuntu.com/community/WifiDocs/Device/AR5007)

without command line: 
cd ..

9.04 works out of the box

---

### Post by Soglad on 2009-07-12
> **RobHK said:**
> 9.04 works out of the box

Sadly it doesn't. I recently installed 8.04 and it did not work, then I upgraded to 9.04 and still nothing.

I've tried everything, but most of the code lines in this thread do no work for me which is extremely frustrating! They always come back reading errors. I don't know what to do.

I have an Atheros 5007 802.11b/g WiFi Adaptor

Thanks

---

### Post by RealG187 on 2009-07-13
It doesn't work in 9.04 for you? Nor does the madwifi driver?

---

### Post by Soglad on 2009-07-14
I've tried both, the madwifi driver commands don't work and give me errors and no installation of Ubuntu ever worked, I'm on 9.04 at moment!

Please let me know if you've any ideas! Everything works bar the bloody wifi :(

---

### Post by naomibrown on 2009-07-14
I'm on 9.04 and it didn't just work.

I just completed [https://help.ubuntu.com/community/WifiDocs/Device/AR5007]("https://help.ubuntu.com/community/WifiDocs/Device/AR5007") successfully. 

I tried clicking on the network manager applet, but it only has the option for lo (loopback?) not my wireless network. So I can't connect to it :(

I haven't done anything apart from exactly what is in that document (well actually I had to change the filename to be what had downloaded), so maybe I'm making a stupid mistake?

Thanks!
Naomi

---

### Post by Soglad on 2009-07-14
OK guys, on this link: [https://help.ubuntu.com/community/WifiDocs/Device/AR5007](https://help.ubuntu.com/community/WifiDocs/Device/AR5007)

I can only get as far as **"cd madwifi-hal-0.10.5.6-r4016-20090429/scripts/"** because it gives me an error saying **"bash: cd: madwifi-hal-0.10.5.6-r4016-20090429/scripts/: No such file or directory"**.....so annoying, anyone know what to do?

---

### Post by Soglad on 2009-07-14
I changed the filename and now it's at least regocnizing my wifi connection, but it still is not turned on or able to connect which is bizare!

It has my connection detected, but the button on my laptop for wifi is off and when I try to connect to the wifi it just freezes and returns asking for a password over minite or so (yes, the password is right)

Any ideas?

---

### Post by RealG187 on 2009-07-14
> **Soglad said:**
> I've tried both, the madwifi driver commands don't work and give me errors and no installation of Ubuntu ever worked, I'm on 9.04 at moment!

Please let me know if you've any ideas! Everything works bar the bloody wifi :(

Did you run "make install" as root (sudo make install)

---

### Post by Soglad on 2009-07-14
> **RealG187 said:**
> Did you run "make install" as root (sudo make install)

Hi there :)

I have gotten past that point now and my connection is being recognized but it cannot connect to it and I still can't turn my wifi button on, very weird...

---

### Post by RealG187 on 2009-07-14
> **Soglad said:**
> I changed the filename and now it's at least regocnizing my wifi connection, but it still is not turned on or able to connect which is bizare!

It has my connection detected, but the button on my laptop for wifi is off and when I try to connect to the wifi it just freezes and returns asking for a password over minite or so (yes, the password is right)

Any ideas?

What computer are you using? I have a HP G50 notebook and in Vista when wifi is off the light on the button is orange and when it's on it's blue.

In Ubuntu the light is orange but wifi is working, as I am sending this the light is orange...

---

### Post by Soglad on 2009-07-14
> **RealG187 said:**
> What computer are you using? I have a HP G50 notebook and in Vista when wifi is off the light on the button is orange and when it's on it's blue.

In Ubuntu the light is orange but wifi is working, as I am sending this the light is orange...

I have a Compaq Presario CQ60 but the light is same for yours as is mine. I will continue to try and connect to the wifi then, everything should be in order :S

Thanks mate

---

### Post by Soglad on 2009-07-14
Yeah I definitely am not getting anything. All I get is the two little bubbles at the top right with the blue beam rotating but it never connects, keeps asking for passwords. I won't connect :(

I have my password here in front of me, don't know

---

### Post by Soglad on 2009-07-14
Nevermind! A quick reboot and everything is fine!

Thank you!

---

### Post by naomibrown on 2009-07-15
> **Soglad said:**
>  All I get is the two little bubbles at the top right with the blue beam rotating but it never connects, keeps asking for passwords. I won't connect :(


I don't have any little bubbles :(

When I restart nothing has changed....

I'm on a toshiba satellite pro if that helps!

---

### Post by RealG187 on 2009-07-15
> **Soglad said:**
> Yeah I definitely am not getting anything. All I get is the two little bubbles at the top right with the blue beam rotating but it never connects, keeps asking for passwords. I won't connect :(

I have my password here in front of me, don't knowIf the thing is rotating and it asks you for a password then that means the device is working. Some times I asks me for a password when signal is weak.

There used to also be a bug when you suspended or hibernated and when you resumed it would keep asking for a password. That must mean a problem with Ubuntu accessing Wifi on a software level... Because when you would suspend/hibernate it would turn off the wifi software...

---

### Post by naomibrown on 2009-07-17
I still can't get this to work - I've followed the instructions and it doesn't look like anything has changed and the only option I have to connect to is lo 

:(

---

### Post by RealG187 on 2009-07-17
I really don't know. For me in 9.04 it just works. What instructions did you file?

---

### Post by naomibrown on 2009-07-18
> **RealG187 said:**
> What instructions did you file?

[https://help.ubuntu.com/community/WifiDocs/Device/AR5007]("https://help.ubuntu.com/community/WifiDocs/Device/AR5007")

If it works automatically, do I need to undo those changes in some way? Or reinstall 9.04?

Thanks

Naomi

---

### Post by naomibrown on 2009-07-19
does anyone know why this isn't working for me?

:(

---

### Post by kudzugarden on 2009-08-01
> **naomibrown said:**
> does anyone know why this isn't working for me?

:(

it could be because the madwifi driver changes version numbers frequently, so for instance, where the wifidocs tutorials says:
```
cd madwifi-hal-0.10.5.6-r4016-20090429/scripts/

```
you would have to change the number to reflect whatever the current version of madwifi-hal-0.10.5.6-current.tar.gz is. 

so, with the most recent update, the correct command would be:
```
cd madwifi-hal-0.10.5.6-r4068-20090705/scripts/
```

and of course this will change again soon enough, but you can find the correct number in the output from the previous command from the wifidocs tutorial.

hope this helps.

---

### Post by RealG187 on 2009-08-02
> **kudzugarden said:**
> it could be because the madwifi driver changes version numbers frequently, so for instance, where the wifidocs tutorials says:
```
cd madwifi-hal-0.10.5.6-r4016-20090429/scripts/

```
you would have to change the number to reflect whatever the current version of madwifi-hal-0.10.5.6-current.tar.gz is. 

so, with the most recent update, the correct command would be:
```
cd madwifi-hal-0.10.5.6-r4068-20090705/scripts/
```

and of course this will change again soon enough, but you can find the correct number in the output from the previous command from the wifidocs tutorial.

hope this helps.I just used tab completion.

---

