---
title: "Atheros AR2413 wifi help"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by scraghty604 on 2008-04-07
welcome to club..i been trying to get the wireless to work for that past 9 hours

Moderater Edit: This thread was in response to this: [http://ubuntuforums.org/showthread.php?p=4672837](http://ubuntuforums.org/showthread.php?p=4672837)
Separated due to 2 different wifi issues.

---

### Post by scraghty604 on 2008-04-07
i wish i could use that but i havent got a clue what that means

---

### Post by scraghty604 on 2008-04-07
in reading that link..it said vista drivers are not compatable that is what was on here befor?

---

### Post by scraghty604 on 2008-04-07
there is a password and what not on the router...but as for that other stuff i did not set it  up, its a public router that my landlord inputs the password, i do not know the password
she just types it in the comp when i need it 
and im online with it right now wired (said i needed to dl some secret stuff for work :P)


scotty@scotty-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:fc:92:34
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=192.168.1.65 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10

---

### Post by ugm6hr on 2008-04-07
> **scraghty604 said:**
>        product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
      

This should work with little difficulty.

First - follow the advice in the "Enable Repos" link below.

Go to the Restricted Driver Manager (System->Administration)

It should offer you some options - install them.

It should then work (in theory).

Have you connected to the network with another OS before?  If so - how?  That will tell what encryption etc (describe the exact procedure).

---

### Post by scraghty604 on 2008-04-07
i made sure the 4 boxs were checked and then went to the rescricted driver manager, there were no options other then help and cancal  i did see this tho

atheros acces hardware layer(HAL)

said it was enabled and in use i have the option to un enable it thats it

---

### Post by ugm6hr on 2008-04-07
> **scraghty604 said:**
> i made sure the 4 boxs were checked and then went to the rescricted driver manager, there were no options other then help and cancal  i did see this tho

atheros acces hardware layer(HAL)

said it was enabled and in use i have the option to un enable it thats it

OK - looks like it already enabled.

Try this again:
```
lshw -C network
```
Under the Atheros entry, you should see something like this now:
```
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 4
       bus info: pci@0000:08:04.0
       logical name: wifi0
       version: 01
       serial: 00:19:7d:33:e4:13
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes **driver=ath_pci** ip=192.168.1.3 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

I've attached a picture of the restricted driver page - yours should look similar (although perhaps without the ATI entry).

---

### Post by scraghty604 on 2008-04-07
this is what i got back

scotty@scotty-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:fc:92:34
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=192.168.1.65 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10

---

### Post by ugm6hr on 2008-04-07
> **scraghty604 said:**
> this is what i got back

Hmmm.... Just confirm the exact card with this command:
```
lspci | grep Atheros
```

It should come back with:
```
08:04.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
```

PS: Are you using 32 or 64-bit Ubuntu?

---

### Post by scraghty604 on 2008-04-07
this is what came back the same except for the begign part

scotty@scotty-laptop:~$ lspci | grep Atheros
0a:03.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
scotty@scotty-laptop:~$ 

it should be 32 7.10 how do i find out

---

### Post by ugm6hr on 2008-04-07
> **scraghty604 said:**
> this is what came back the same except for the begign part

scotty@scotty-laptop:~$ lspci | grep Atheros
0a:03.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
scotty@scotty-laptop:~$ 

it should be 32 7.10 how do i find out

OK - you have the same card as me.  So this will work.  Just need to work out why things have gone awry for you.

What How-to's have you tried already?

Have you tried to use ndiswrapper?

The version of Ubuntu is displayed by:
```
uname -a
```

And post the text displayed following this:
```
gedit /etc/modprobe.d/blacklist
```

---

### Post by scraghty604 on 2008-04-07
i have tried diffrent tings befor when i tried opensuse but that did not work  i have a FRESH install of  ubuntu now i didnt  do any that stuff yet..i tried befro tho  but anyways fresh instal

hey thanxs so much for your help man really thanxsful..i been workgin on this for 12 hours now haha thanxs!!!!

scotty@scotty-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"
scotty@scotty-laptop:~$ 

scotty@scotty-laptop:~$ uname -a
Linux scotty-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
scotty@scotty-laptop:~$

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

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

---

### Post by ugm6hr on 2008-04-07
If this is genuinely a fresh install - it should work without any effort.

My wifi worked out-of-the-box, as your should.

I'm going to have to give this some thought for a few hours to try and work out why yours doesn't work.

Only other thing is to try a reboot.  Shouldn't make a difference... but can't hurt!

Did wifi work from the LiveCD?

---

### Post by scraghty604 on 2008-04-07
I had orginlly DL opensuse10.3 it didnt seem wanna work so i said forget then dl and installed ubuntu..neith of them ever show any sign of wireless(to me anywas i am VERY fresh with this linux stuff) the only  thing i noticed is that the wifi light  on the comp it self is lite  always on

I did reboot

i was gonna try that wrapper thing but i havent got a clue what to do i have the windows driver dl to the desktop just need to do somethign with it.

But your way seems so much eaiser

---

### Post by scraghty604 on 2008-04-07
being a nube i didnt try form a live cd befor i erased windows lol  when unbuntu installed  there was liek a desktop thign befor it actuly installed it was not workign then either

---

### Post by ugm6hr on 2008-04-07
> **scraghty604 said:**
> I had orginlly DL opensuse10.3 it didnt seem wanna work so i said forget then dl and installed ubuntu..neith of them ever show any sign of wireless(to me anywas i am VERY fresh with this linux stuff) the only  thing i noticed is that the wifi light  on the comp it self is lite  always on

I did reboot

i was gonna try that wrapper thing but i havent got a clue what to do i have the windows driver dl to the desktop just need to do somethign with it.

But your way seems so much eaiser

So presumably the hardware switch for wifi is ON?

You don't have to press a button (or keyboard shortcut) to enable wifi?

When Ubuntu first installed, did it warn you about the Restricted Driver thing?  It should have told you that it was necessary to use the driver for functionality, but that is is proprietary (unsupported).

I can't think why Ubuntu would auto-enable Atheros HAL (restricted driver), but not load the ath_pci driver with the wifi card.  Bizarre :confused:

---

### Post by scraghty604 on 2008-04-07
yes it would apprear to be on 

i have seen so much today i cant say if i have seen that or not i THINK so...

if i were to start from scrath and reinstall everythign what should i do...musta been somethign i did mabey

---

### Post by ugm6hr on 2008-04-07
From a fresh install, it should tell you that Restricted Drivers are installed.

Then just check the lshw output for evidence that a driver has been installed.

If so - it should just work (by clicking on the networking icon top-right)..

---

### Post by scraghty604 on 2008-04-07
> **ugm6hr said:**
> From a fresh install, it should tell you that Restricted Drivers are installed.

Then just check the lshw output for evidence that a driver has been installed.

If so - it should just work (by clicking on the networking icon top-right)..



Ok so cd in
reboot
wanna delet al partions so on and so on 
it will say  resrcied driver are instaled  accpet that ?
 

when do i check lshw  on first boot up ?

what will it say how do i know it is installed

i will try after i hear a reply  thanxs 

and go from there i guess

At least windows works for 5 min befro crashing :P i havent got a single thign to work either 

OH also i had to screw around with thw aound ( adjusting surround) as noted in a diffretn post is that somethign i can fix  when i reinstall...

---

### Post by ugm6hr on 2008-04-07
You can just try from the "LiveCD" environment.

CD in.
Reboot.
Select "Start or Install"
Wait (for a while) until the brown screen (desktop) appears - this is the LiveCD environment.
Open a Terminal here.
lshw -C network
Look for the response that I posted earlier (from my computer) - it should be like that, not like yours at present.
Click on the networking icon (top-right somewhere)
It should give a drop-down list of networks that it can see.
Click on your landlords network.

---

### Post by scraghty604 on 2008-04-07
i am in live as we speak here is what came up  and inthe coronr is the same as befor 

wired connection and modem

ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:fc:92:34
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=192.168.1.65 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10

---

### Post by scraghty604 on 2008-04-07
ther is other networks in the area but  like there isnt even a wireless option...i just no from when i had windows and it wokred fine

---

### Post by scraghty604 on 2008-04-07
well i am gonna tweak lol...i screwed around in live and what i did was dl a NDIS wrapper but  some front end thing like a programe then i dl the driver off of acer extracted.

When i ran the NDIS it said to input a .inf file...so i inputed the only .inf there was that dl with the  driver and volia it worked

so i was like ok...i finshed the installing of ubuntu  and WTF would u know it it was working when it installed so i dont know whats going on why does it work now...haha and now im afraid to do the updates becase i seen on a diffretn post guy did updates and screwed eerythign up.

any thoughts?!?

---

### Post by kevdog on 2008-04-07
ndiswrapper is a kernel module -- when you upgrade distro's -- like gusty to hardy, the kernel number changes to a more recent version, so hence the module needs to be recompiled against the newest kernel's headers and then reinserted.  Routine maintainance numbers should not interfere in any way with ndiswrapper because the kernel version does not change.

---

### Post by ugm6hr on 2008-04-08
> **scraghty604 said:**
> well i am gonna tweak lol...i screwed around in live and what i did was dl a NDIS wrapper but  some front end thing like a programe then i dl the driver off of acer extracted.

When i ran the NDIS it said to input a .inf file...so i inputed the only .inf there was that dl with the  driver and volia it worked

so i was like ok...i finshed the installing of ubuntu  and WTF would u know it it was working when it installed so i dont know whats going on why does it work now...haha and now im afraid to do the updates becase i seen on a diffretn post guy did updates and screwed eerythign up.

any thoughts?!?

Glad you got it installed with ndiswrapper - and without any further help!

The only explanantion I can think of is that the Linux kernel recognises your Atheros wifi card as the same as mine, but it is actually a different chipset.  This has happened before with the AR5007 (which has a madwifi patch).  Is your wifi very new?

I wonder whether a new madwifi patch is available for yours? Obviously, this point is now mute, since yours is working.  There are only 2 chipsets recognised as working with this: [AR5005G]("http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5005G") and [AR5BMB5]("http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5BMB5").

Anyway,  updates for Gutsy generally won't interfere with your wifi.  Who said it messed things up for them?  The only way it would ruin things is if the madwifi driver has been updated to work with your chipset, so an update of the Restricted Driver interferes with ndiswrapper.

If that is the case, then the solution we were searching for was an update!

However - to ensure your wifi stays as it is (working with ndiswrapper), you should disable the Atheros HAL in Restricted Drivers, and add *ath_pci* to the blacklist file.

---

### Post by scraghty604 on 2008-04-08
thanxs for you help never woulda got ther without it... but i dont understand tho is i got  it to work in "live" mode  then i installed clean boyaa all gone...andi t worked ?  but y not the first 3 times i instaled ? and im pleaed to point out that my signal has not droped once yet so far (knock on wood)  which it would do every five min in windows...im starting to like this linux thing  why it gotta be so damn complicated

---

### Post by ugm6hr on 2008-04-08
> **scraghty604 said:**
> thanxs for you help never woulda got ther without it... but i dont understand tho is i got  it to work in "live" mode  then i installed clean boyaa all gone...andi t worked ?  but y not the first 3 times i instaled ? and im pleaed to point out that my signal has not droped once yet so far (knock on wood)  which it would do every five min in windows...im starting to like this linux thing  why it gotta be so damn complicated

So did you need ndiswrapper in the end or not?

---

### Post by scraghty604 on 2008-04-08
nope when i did the fresh instal the thrid time it was there aleady???

---

### Post by chilskater on 2008-04-10
hello there,
want to ask u...i got my ndiswrapper working for my SENAO USB Antenna with atheros chip (net5523.inf)..but i would like to use madwifi for cracking WEP purpose...so shud i stick to ndiswrapper??i am 1 week ubuntu noobie

---

### Post by ugm6hr on 2008-04-10
> **chilskater said:**
> hello there,
want to ask u...i got my ndiswrapper working for my SENAO USB Antenna with atheros chip (net5523.inf)..but i would like to use madwifi for cracking WEP purpose...so shud i stick to ndiswrapper??i am 1 week ubuntu noobie

I'm no expert, but from my reading, this is my understanding:

I don't know if madwifi works on USB chipsets - I don't think it does.

ndiswrapper doesn't work with aircrack type tools.

So - unless you know otherwise. it won't be possible to do this.

---

### Post by w4lgh on 2008-05-03
> **scraghty604 said:**
> well i am gonna tweak lol...i screwed around in live and what i did was dl a NDIS wrapper but  some front end thing like a programe then i dl the driver off of acer extracted.

When i ran the NDIS it said to input a .inf file...so i inputed the only .inf there was that dl with the  driver and volia it worked

so i was like ok...i finshed the installing of ubuntu  and WTF would u know it it was working when it installed so i dont know whats going on why does it work now...haha and now im afraid to do the updates becase i seen on a diffretn post guy did updates and screwed eerythign up.

any thoughts?!?

Where did you find this driver...what you had is xactly my problem and I need to get my wireless back up and running....

HELP!!!!

---

### Post by saipu on 2008-05-03
You may try this drivers [http://www.atheros.cz/](http://www.atheros.cz/). Select according to your chipset. Works fine with me! :)

---

### Post by clap.your.hands on 2008-05-29
I have Atheros AR2413 and I have no wireless at all. It isn´t even an option under network manager. And I am completely new to Linux/Ubuntu and all things terminal and codes. I have made futile attempts at various solutions floating around but errors keep poping up. So I have no idea.. any help?

---

### Post by ZinkAlkon on 2008-05-30
As the person before me in this post, I'm also trying to get my Wifi to work, I've been coming back and forth for a week now with this.... new status:

Hardware light is now OFF (Acer Aspire 5043WLMi with those orange lights in the front)

this is my terminal today:

zink@Zink-Book:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:0b:05:2a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,01/10/2004,4.0.0.14001 latency=128 maxlatency=28 mingnt=10 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:46:21:36
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=10.0.0.5 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
zink@Zink-Book:~$ lspci | grep Atheros
06:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
zink@Zink-Book:~$ 

Any ideas? I have Ubuntu 8.04 HArdy 64 bits version....

I travel a lot, so Wifi is a MUST for me! 

Thxs in advance

---

### Post by kelbizzle on 2008-06-04
It's doesn't work for me either. One time with the hal driver in 7.10 it connected to my wireless network. It never worked after that. Suddenly the interface disappeared. It appears the wireless card isn't connected. lspci shows the card exist. But iwconfig shows no card. I then installed 8.04 I could see networks but not connect to my unprotected network. I've tried madwifi same result..I could see networks but not connect.

---

### Post by quanumphaze on 2008-06-10
I find that the problem is often fixed by flicking the wireless switch/button/Fn+* on the laptop before the OS actually starts (at GRUB time).

Mine worked perfectly until 3 days ago when it refuses to load up the drivers and configure the ath0 interface. It takes up to 2 reboots until it works. Keep playing with the wireless button until it gets picked up.

Rebooting is not the Ubuntu way of solving this. If anyone knows how to set up network interfaces (ath0 and wifi0) which don't get created at boot we would like to hear from you. The kernel modules usually can be loaded manually so the road block is getting the ath0 interface to use the module.

EDIT: oh and this script for those who want to compile MadWifi from source [http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)

---

