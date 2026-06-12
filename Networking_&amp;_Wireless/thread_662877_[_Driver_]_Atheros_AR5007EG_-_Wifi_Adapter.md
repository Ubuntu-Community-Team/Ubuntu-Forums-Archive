---
title: "[ Driver ] Atheros AR5007EG - Wifi Adapter"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by tistaharahap on 2008-01-09
I've been having problems with my Acer 4315 laptop's wifi card. The chipset is Atheros AR5007EG. Ubuntu seems to recognise the card as AR5006EG.

So I dug through Google and Ubuntu Forums with ndiswrapper as the solution. For me ndiswrapper didn't solved anything. My wifi's on/off button doesn't work in Ubuntu even though the card is detected properly.

For Hardy Heron users please do this first:
> 
1. Go to System -> Administration -> Hardware Drivers
2. UNCHECK **Atheros Hardware Abstraction Layer (HAL)**
3. Leave **Support for Atheros 802.11 wireless LAN cards.** CHECKED


For 64bits systems please follow the link below:
> 
[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)


I found this great link:
> [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

Go to the bottom of the page and you'll find a link containing an already patched madwifi to support AR5007EG. 

Here's the download link:
> [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

The following are simple steps to compile and install the driver:
> 1. Remove any ath_pci driver from the RESTRICTED DRIVERS MANAGER
2. Make sure that you have **build-essential** package installed, if not, fire up a terminal and type in **sudo apt-get install build-essential**
3. Navigate your way in Terminal to the directory where you downloaded the archive for the driver
4. Type these to decompress the archive **tar xfz madwifi-ng-r2756+ar5007.tar.gz** and **cd madwifi-ng-r2756+ar5007**
5. Type **make** to compile
6. Type **sudo make install** to install the driver
7. Type **sudo modprobe ath_pci** to insert the driver as a kernel module
8. Restart by typing **sudo reboot**
9. If all goes well, after you restarted, you will find wireless networks in your Network Manager

Good luck ;)

---

### Post by K.Mandla on 2008-01-09
Moved to Networking and Wireless.

---

### Post by fissionmailed on 2008-01-09
I have a Toshiba with that same card I've been trying to get to work but nothing seems to work. :\  I'm loading Vista on it now to see if the thing even works.

---

### Post by raiwo on 2008-01-10
these instructions work like a charm, thanks man! 

Only thing I have noticed is wireless signal is not as strong as with ndiswrapper, it's about 20% lower (according wicd) so hopefully this will be fixed in future releases

---

### Post by doubleij on 2008-01-10
Hey, I think I am experiencing exactly the same issue with my Acer 4315. My Atheros also shows as a 5006 (but perhaps it's actually a 5007?), and I tried ndiswrapper with the 5006 driver but no luck. I couldn't even see my wan card under ifconfig.

I will try the solution you mentioned at the top tonight or tomorrow. I was really giving up hope on this until I did a random search for "Acer 4315" and found your post. Hopefully problem solved...

---

### Post by tistaharahap on 2008-01-10
One thing I noted about the driver, it's dependent on my laptop's wifi on/off button actually. If I disable wifi in xp, the card won't function in Ubuntu although still detected properly. When I enable the card by pushing the wifi button in Ubuntu, it won't work but if I go back to windows to enable it, it works.

Looking from madwifi's ticket responses, I think it's unlikely for them to update the codes. The current solution for AR5007EG breaks compatibility due to AR5007EG's different HAL approach. But let's be positive and hope that it'll be updated.

---

### Post by dca on 2008-01-11
Oddly enough, this worked for me versus using 'ndiswrapper' and the Windows driver (which also works)...

---

### Post by doubleij on 2008-01-12
Update: Got wireless to work thx to this thread. One note. The fix listed here allowed me to see my router--but not to connect to it! I had to edit the network/interfaces file to do that. I added this code at the bottom and got it to work. 

iface wifi0 inet dhcp
wireless-key XXXXXX
wireless-keymode open
wireless-essid <name of network>

auto wifi0 

...where wifi0 is the logical name of my card.

This fix is cancelled/undone if the backports-modules is applied in Synaptic. I tried to do this in order to get  my audio out and mic in ports to work. The backports crashed my soundcard and undid hours of work on my wireless card. So don't get backports-modules! Hopefully support for my sound card will be added in Hardy...

---

### Post by jvijayv on 2008-01-13
Thanks a lot!!! This perfectly worked for me. I have a Compaq Presario F750US Notebook PC and by default the network manager wasn't showing me my wireless connection. Once I used this method, I was able to reboot and instantly see wireless networks that I can connect to.

Very Helpful! Thanks for the great support!
:KS:KS:KS:KS:KS
-Vijay

---

### Post by SonicsDemon on 2008-01-14
Alright, I would sincerely appreciate it If someone could help me. I have the exact acer and  wifi as described in the how to. I followed it, and it worked... The problem is that I can't keep this working. It woks fine- so long as I don't shutdown. Once I shutdown, I have to redo the "how to" in order to get it to work. It works just fine, I was practically jumping with joy. But then I shutdown and goodbye.:confused::confused::confused::confused:

---

### Post by SonicsDemon on 2008-01-14
the last command:  " sudo modprobe ath_pci " doesn't seem to do anything. I don't know, is the problem or what because my laptop's wifi button doesn't come on.

---

### Post by dlowerre on 2008-01-15
Fantastic!  I installed Gutsy on a Satellite P205D-S7802 for a friend of mine who just bought one (I MUST save him from Vista!) and the steps detailed here for compiling and installing madwifi got it working with very little Sturm and Drang!

What a great community!

---

### Post by doubleij on 2008-01-15
Hi sonics demon,

Sorry the fix didn't work as well for you. I'm quite new, so I can't give much advice. However, I would check a couple of things if I were you:

1. Are you logged in as root to make these changes? I find sometimes that I have to redo preferences between root and a regular user. This probably isn't the problem, but it doesn't hurt to check.

2. Is your wireless button disabled or setting itself to off somehow every time you boot up? I'm running straight Linux (not dual-boot) and the wireless button is apparently disabled (which is my preference anyways). 

3. Is your wireless router still recognized after you restart? Does it still show a little signal bar when you click on the network manager applet? If so, the problem might be related to your password if its a WPA or WEP network. It would be strange if its not recognized, since the driver will be in modprobe permanently once inserted and should always recognize the card and enable it to see your router (unless, I suppose, you have essid hidden).

4. Did you install anything else before rebooting? That could possibly have undone your hard work on the wireless (see my note on backports in previous post).

In answer to your other question, yes, the the modprobe command is important. As far as I understand, it's what inserts the driver into the kernel so that it works. 

Anyways, I'm still very new, but maybe this can point you in the right direction. Perhaps someone with more experience can comment/correct here.

---

### Post by doubleij on 2008-01-29
I figured out the conflict between the Alsa fix for my sound card and the madwifi fix for my Atheros. The trick is to install the sound fix first and then the wireless. If wireless is installed first than the Alsa driver cancels out the wireless fix and you have to reinstall. I run 7.10 on Acer 4315.
More details here.
[http://ubuntuforums.org/showthread.php?p=4229511#post4229511](http://ubuntuforums.org/showthread.php?p=4229511#post4229511)

---

### Post by mikerman55 on 2008-01-29
it would be lovely if someone posted a script that did not assume that we knew what we were doing. you know for we newbies in the group who have crippled Acer Aspire 5315-2077 units. something that is simple, complete and would be a basic tutorial with explinations of what is going on.  a criptic "load madwifi" is as helpful as, well as helpful as nothing for those of us who are stumbling through the tall grass after spending thirty years fighting windows.
thanks
Mike

---

### Post by nutz on 2008-03-01
I also have this NIC in my laptop which runs Ubuntu 64 bit and after many days of searching and tweaking and trying various things I have come to the conclusion that it just isn't going to work on 64 bit platforms until madwifi updates the HAL. Some users of 32 bit platforms have gotten it to work but even then it's performance and reliability is still rather poor.

So untill madwifi has full support for this on 64 bit platforms the only other option is to swap out the NIC for one that does work with Ubuntu 64 bit. A quick search online shows that a mini pci-express wireless nic is only about $30 so that is the route I am going to take for now. But I will be keeping an eye on this thread as well as other AR5007EG related threads so please post any updates you come across guys!

---

### Post by ijf8090 on 2008-03-04
"2. Is your wireless button disabled or setting itself to off somehow every time you boot up? I'm running straight Linux (not dual-boot) and the wireless button is apparently disabled (which is my preference anyways). "

My wireless button is disabled (Compaq Presario F700) dual-boot Vista - cannot enable it. I think Vista is turning it off as part of its shut-down process. 
I tried 
"To Fix this issue, I went to Vista/Control Panel / System / Device manger. Under network adaptors I selected the wireless card, right clicked and selected properties. Under the &#8220;Power Management&#8221; you can unselect &#8220;Allow the computer to turn off this device to save power.&#8221;
 but the wireless button still does not work. It goes from backlit Blue enabled to Orange disable on shut-down and stays that color when Ubuntu boots.

I looked for a  BIOS setting - but there does not seem to be one. Just about ready to buy a USB wireless adapter, but want to give it one last shot. 

BTW - I bought this laptop to learn about Linux. What I've learned - don't install Linux on a Compaq  laptop<s>..

Any suggestions gratefully appreciated....

---

### Post by pavan.ngs on 2008-03-06
thanks a lot.................this is the perfect solution.................once again thank u very very much:):):):):)

---

### Post by nutz on 2008-03-06
> **pavan.ngs said:**
> thanks a lot.................this is the perfect solution.................once again thank u very very much:):):):):)

And what solution would that be?

---

### Post by az_human on 2008-03-26
Thank you SO MUCH for this!  I tried all sorts of other instructions but none of them worked for me.  This one did!

If anybody else has a Toshiba Satellite P205D-S7802, give this one a try!

---

### Post by SandmanXC on 2008-03-28
Thanks very much, mate!!

Worked for an **ASUS X51RL** notebook.

---

### Post by Xalabam on 2008-03-28
Muchas gracias :)
 It worked as stated on the initial post/guide.

For reference, i am using [COLOR="DarkRed"]Acer TravelMate 5510[/COLOR]

thx again .

---

### Post by Triv1um on 2008-03-31
Im using AMD64, any luck for me? 

Do I *have* to re-install?

---

### Post by Giacecco on 2008-03-31
I think you can find this information somewhere in the forums: someone managed to compile the patch for the AMD64 platform but the resulting drivers were unstable and underpeforming. 

I reinstalled and I am relatively happy now. My only open problem is getting the network to work after suspending or hibernating the laptop.

Giacecco

---

### Post by tscook on 2008-04-14
This worked really well for me until I tried to hibernate my laptop. As part of the process it unloads  wireless modules but when it tries to unload ath_pci it segfaults and brings the entire process to a halt. Same with modprobe -r ath_pci, except it crashes just short of a kernel oops. Does this happen to anyone else? Is it the patch that even allows madwifi to be used for ar5007eg that is causing this?

---

### Post by sigmabetatooth on 2008-04-15
Thanks a ton.  I have a new COMPAQ C700 and limited ubuntu experience.  The [Ubuntu  Wifi Document ]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a14b8a20c3973fe959032bd1566ad35dceb30132") wasn't able to help :( but the Ubuntu community was :)

Only other problem is this pesky orange wifi button.  Has anyone  had any sucess with getting it working?  Would much appreciate a little more help from the legendary ubuntu community.

---

### Post by Mahyar on 2008-04-23
I can confirm that this works with the Hardy Heron on an Acer Aspire 4315.

Thanks

---

### Post by Giacecco on 2008-04-25
Did anybody try if Hardy Heron supports the AR5007EG out of the box? Mahyar, what does exactly "work" on your Acer? Thanks,

Giacecco

---

### Post by uku on 2008-04-25
No, unfortunately Hardy doesn't support Atheros 5007 EG out of the box, at least not in the case of my Samsung R25+. But this guide did it. Many thanks, tistaharahap :D
Now there's only to wait for madwifi "stock release" improvements.

---

### Post by taliz on 2008-04-26
I sometimes hit the wlan button by accident, which disables the wlan.
At first I didn't actually know what caused it to stop functioning, or what that button was for.
Later I noticed that dmesg says this when its hit:
[  663.815641] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
[  663.895979] atkbd.c: Unknown key pressed (translated set 2, code 0xd5 on isa0060/serio0).
[  663.895984] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
[  663.896644] atkbd.c: Unknown key released (translated set 2, code 0xd5 on isa

e056 and e055 is the same key, just hit twice. Apparently e055 means wlan is turned on and e056 means its turned off.

also you can check it via:
root@lap:~# cat /proc/acpi/acer/wireless 
1

...and hence enable/disable it via echo 1(or 0) to that file.

You can also map the key to do whatever you want(it'll still enable/disable the wlan via hw though) via setkeycodes which I guess is best done via /usr/share/hotkey-setup/acer.hk.

You can see examples here, which should work with slight modifications:
[http://gentoo-wiki.com/HARDWARE_Acer_Aspire_5024_WLMi#Startup_Settings_7](http://gentoo-wiki.com/HARDWARE_Acer_Aspire_5024_WLMi#Startup_Settings_7)

In my opinion it should be mapped by default to something telling the user that the wlan is disabled/enabled, I have 10 years of Linux experience and yet it took me a while to figure out what was happening.
[https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/57849](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/57849) I guess that applies for most(all?) of Acers laptops.

PS. the wlan doesnt work in hardy on Acer 4315 by default. Need do use the patched madwifi.

---

### Post by sigmabetatooth on 2008-04-27
> **sigmabetatooth said:**
> Thanks a ton.  I have a new COMPAQ C700 and limited ubuntu experience.  The [Ubuntu  Wifi Document ]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a14b8a20c3973fe959032bd1566ad35dceb30132") wasn't able to help :( but the Ubuntu community was :)

Only other problem is this pesky orange wifi button.  Has anyone  had any success with getting it working?  Would much appreciate a little more help from the legendary ubuntu community.

Follow up...

It was working until I installed fluxbox.  Considering fluxbox is just a windows manager I highly doubt that it is the cause of my problems.  Probably what happened was the reboot killed it :(.  But now, after installing gOS and then hardy heron over that, i'm still without wireless.  When heron installed it didn't recognize my atheros card and installed the private drivers.  I'm thinking the card may be off, the button is orange.  Anyone know how to check the wifi button on a compaq c700?  Any other advice is appreciated.  Precise idiots guide to ubuntu style instructions are the best.

I guess i'll try madwifi again until then...

---

### Post by grantbuntu on 2008-04-28
Thanks heaps - worked with my Acer 4315. \\:D/ I now have a fresh install of Hardy and it is excellent.

---

### Post by Mahyar on 2008-04-28
Giacecco,

Sorry for the late reply.

What exactly works?  Wireless works fine, as it did by default with the OEM install (Gutsy), but not with Hardy.

Do you mean generally though?  If so, the only things that don't work are the wireless button, which does work with Keytouch though, and the dial-up modem.  That could probably be configured if it mattered.

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


os: ubuntu 7.10 with all updates installed.
adapter works as ath0 with wifi0 - no ndis wrapper no mess

---

### Post by ironjon on 2008-04-29
I have too this card on a Packard Bell MX52-B-073 with dual boot Vista-Ubuntu 7.10 and I cannot connect with any lan.
Today I have to do this solution

---

### Post by tistaharahap on 2008-04-29
Edited the guide to add compatibility with Hardy Heron and 64bits systems.

---

### Post by k66473 on 2008-04-30
Sometime, my system hangs and I need to cycle the power.
After hard reset the system, this mad driver gone and the system does not recognize the wireless network any more. I must to re install the driver for wireless. (make and make install)
This happen two times with me.

---

### Post by SpinningAround on 2008-05-04
Working great except one small problem, the diod that show if the WLAN is on or off don't work, atm it show that wlan is off but it's clearly on.

---

### Post by Serdgent on 2008-05-05
Hello everyone

I am just a newbie and try desperately to get my wifi to work on this config :

Acer 5520G (amd 64) + Hardy + Atheros 5007 card + Network Manager

I followed a bunch of tutorials included the ones on this thread, but still nothing... I don't even see a wlan0 when hitting iwconfig. 

ndiswrapper - l spits : 
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci

and I have blacklisted ath_pci , and tried playing with the wifi on/off key a couple of times, but ... nothing ](*,)

I read that some people have managed to get the wifi with a similar configuration

Can anyone help please

Thx

Serdgent

---

### Post by tistaharahap on 2008-05-06
> **Serdgent said:**
> Hello everyone

I am just a newbie and try desperately to get my wifi to work on this config :

Acer 5520G (amd 64) + Hardy + Atheros 5007 card + Network Manager

I followed a bunch of tutorials included the ones on this thread, but still nothing... I don't even see a wlan0 when hitting iwconfig. 

ndiswrapper - l spits : 
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci

and I have blacklisted ath_pci , and tried playing with the wifi on/off key a couple of times, but ... nothing ](*,)

I read that some people have managed to get the wifi with a similar configuration

Can anyone help please

Thx

Serdgent

have you uninstalled the ndiswrapper driver prior to following instructions in this thread?

---

### Post by Serdgent on 2008-05-06
Hello

no, does it not erase automatically the previous driver ?

---

### Post by Hknuckles on 2008-06-14
Hey

I'm have trouble downloading the madwifi driver, it seems that madwifi.org is down.  Could someone e-mail me the driver?

Thanks

aaron dot chr at gmail dot com

---

### Post by nukemelamers on 2008-06-15
i am a super newbie, and completely n00bs

what do u mean by "3. Navigate your way in Terminal to the directory where you downloaded the archive for the driver"
i downloaded it and put on desktop

---

### Post by Pinger05 on 2008-06-15
> **tistaharahap said:**
> I've been having problems with my Acer 4315 laptop's wifi card. The chipset is Atheros AR5007EG. Ubuntu seems to recognise the card as AR5006EG.

So I dug through Google and Ubuntu Forums with ndiswrapper as the solution. For me ndiswrapper didn't solved anything. My wifi's on/off button doesn't work in Ubuntu even though the card is detected properly.

For Hardy Heron users please do this first:


For 64bits systems please follow the link below:


I found this great link:


Go to the bottom of the page and you'll find a link containing an already patched madwifi to support AR5007EG. 

Here's the download link:


The following are simple steps to compile and install the driver:


Good luck ;)

This worked for me with one caveat.  That being at the end add another step to check your WEP key.  Yes I use WEP.  Dont laugh at me.

---

### Post by abuzakour on 2008-06-21
it worked also for Aspire 4720z .. thanks a million :D

---

### Post by Ray190e on 2008-06-25
You are the MASTER JEDI the force is strong with you.

Thanks mate the post was most help full my wifi is working like a charm.
:popcorn:

---

