---
title: "Gutsy vs. Feisty, does your wireless work?"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by bmartin on 2007-10-19
[COLOR="Red"]If you wireless works out-of-the-box, that's great. Please post only if you had to do something in particular to get it working; telling everyone that your wireless worked with no effort doesn't make it easier for the people who need help.[/COLOR]

Someone ran a poll regarding wireless functionality in Feisty Fawn, so I think it's only fair that we keep a running tally to see if wireless support in Ubuntu is getting better or not. If your wireless worked after some tinkering, please share the name of the device (or the chipset, if you know what it is) and the steps you took to get it working.

Personally, I've never had out-of-the-box functionality in Ubuntu, since the Broadcom firmware isn't installed by default. It doesn't support my device well, anyways. I always use NDISwrapper and the bcmwl5 driver to get my device to work. However, when I upgraded, my wireless stopped working. It suddenly and mysteriously started working after several reboots.

---

### Post by Zer0Nin3r on 2007-10-20
I rely on a wifi connection that I share (yes I pay) with my neighbor.  I upgraded the laptop first and had to boot to my windows partition to snag two files that were part of the restricted drivers Ubuntu was asking for.  One was the .deb file for the firmware cutter for Broadcom WiFi Cards (BCM 43xx) and the other was the "firmware" file that the cutter extracts from.  After these two steps the card is working flawlessly.  No need for Ndiswrapper either!

>  [http://us.archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb)

[http://xeve.de/down/wl_apsta.o](http://xeve.de/down/wl_apsta.o)

***EDIT***
> **bmartin said:**
> However, when I upgraded, my wireless stopped working. It suddenly and mysteriously started working after several reboots.

Funny you mention that.  I have  a desktop that runs the RTL8187 driver and when I did the upgrade I had wifi initially.  I then did an update install and rebooted, now it's broken.  Have yet to try to troubleshoot it.  I know I used to run ndiswrapper in Feisty, I'm guessing I'll have to do the same.  (need to research a little bit to see if anyone else is having the same problems)

---

### Post by Gina on 2007-10-20
I have been testing the pre-release of Gutsy for a while and now installed the full release version.  I was unable to get wireless working  with this so have a wired connection to router.  I decided to leave having a concerted effort at getting wireless to work until the full release.  Trying now and no luck.

I have a Belkin F5D7000UK PCI card that has the Ralink RT2500 chipset.  lspci entry is :-
00:0d.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

This was working fine in Feisty except that I had to down the interface, set essid and then up the interface to get it to work.  Now in Gutsy this doesn't work.  I just want a wireless connection that works and not mess with ndiswrapper or network manager etc.  I can't find anything about using the supplied driver - I expected the known bug of downing the interface to be cured in Gutsy.  I'm sure I'm missing something.  Can anyone suggest an answer, please?

This is a copy of my terminal window when I try this in Gutsy (iwconfig shows AP as Not-Associated - iwlist scan shows the correct router MAC but empty ESSID) :-

```
gina@old-desktop:~$ sudo iwconfig
[sudo] password for gina:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gina@old-desktop:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
gina@old-desktop:~$ sudo iwconfig wlan0 essid mystery mode managed channel 11
gina@old-desktop:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
gina@old-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"mystery"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gina@old-desktop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:A8:DA:2A
                    ESSID:""
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Signal level=-52 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000003756a04181

gina@old-desktop:~$ 

```

---

### Post by Trueno22 on 2007-10-20
The network managr for me wasn't enabling me to connect to my wireless network unless i had it in roaming mode.  So I instaled Wicd and have had no problems at all ever since.

---

### Post by bmartin on 2007-10-20
> **Zer0Nin3r said:**
> I rely on a wifi connection that I share (yes I pay) with my neighbor.  I upgraded the laptop first and had to boot to my windows partition to snag two files that were part of the restricted drivers Ubuntu was asking for.  One was the .deb file for the firmware cutter for Broadcom WiFi Cards (BCM 43xx) and the other was the "firmware" file that the cutter extracts from.  After these two steps the card is working flawlessly.  No need for Ndiswrapper either!
I also have a Broadcom BCM43xx chipset, but I use NDISwrapper. The connection's less flaky (a general consensus arrived at; see the comments in the Broadcom thread at the top of the wireless forum) and you get 54Mbps w/ ndiswrapper. However, if the firmware works fine, I'd keep using it. If connecting is kind of slow or the connection is flaky, try NDISwrapper.

---

### Post by #Reistlehr- on 2007-10-20
i have a broadcom 4310 on my laptop. In feisty it took me three months to find the right drivers from HP to get to work with ndiswrapper. That is HP's fault for listing the wrong drivers. I wish that Gutsy, and Feisty had built in support for my Broadcom chipset. (It can't use the 43xx drivers or the 4318 drivers).

---

### Post by PBK on 2007-10-20
I have built-in RTL8185 and had some problems with Feisty, but got it to work with WEP encryption. Gutsy hard locks (capslock indicator just flashes ?) unless there is no encryption used. At least I haven't figured it out or read a post on it, yet.

PK

---

### Post by k3lt01 on 2007-10-20
I did a clean install and Gutsy doesn't even accept ndiswrapper trying to do the driver work. It says it has installed the driver but the folder is empty. It took me 3 days with Feisty so I will keep trying

> **Trueno22 said:**
> The network managr for me wasn't enabling me to connect to my wireless network unless i had it in roaming mode.  So I instaled Wicd and have had no problems at all ever since. I had that problem with Feisty but she stayed in Roaming, now I know about Wicd I'll try that if I have the same thing in Gutsy.

---

### Post by Pete051 on 2007-10-20
I found it impossible to connect with the rt61pci driver from the 2.6.22 kernel, luckily the rt61 driver from the 2.6.20 kernel worked fine.
This is the wireless-G pci card

---

### Post by bmartin on 2007-10-20
> **#Reistlehr- said:**
> That is HP's fault for listing the wrong drivers. I wish that Gutsy, and Feisty had built in support for my Broadcom chipset. (It can't use the 43xx drivers or the 4318 drivers).
I blame Broadcom. I've contacted them; they simply refuse to release any information pertaining to their chipsets (for IP reasons) and won't produce a bcm43xx driver. If it's not related to running a server, Broadcom doesn't care.

---

### Post by rustybronco on 2007-10-20
acx-111 chipset and atheros chipsets, It makes the difference, both work in 7.04 and 7.10 
and that is the reason I choose them.

---

### Post by kevdog on 2007-10-20
Ive got two wireless cards

bcm4306 - ndiswrapper + bcmwl5
atheros - madwifi (restricted_package)

Both work no problem

If only I could get the fonts problem figured out with firefox!

---

### Post by ricardisimo on 2007-10-20
It's pretty bad. I've just now gotten my connection up and running via ndiswrapper [Linksys Wireless G - RaLink RT2500 chipset]. Before now I had to connect by way of the Feisty Live CD, in order to download the driver, etc.

Here's what I don't understand: How can the wireless support be getting so markedly worse from one upgrade to the next, and so consistently? I don't recall having any issues at all on Dapper; Edgy, required a bit of tweaking; on Feisty I had to do some rather extensive experimentation before I finally figured out how to manually set everything up; and now Gutsy has become a nightmare.

So, I've installed the Windows wireless drivers for my card via ndiswrapper, and I have a connection, but it's barely there - maybe single-digit kbps, 10s and 20s tops. Mind you, if I were to go back on the Feisty Live CD right this very moment, without touching anything, moving the antenna or the computer, I would find a very fast connection. Guaranteed. What's up with that? Total frustration.

---

### Post by corncob on 2007-10-20
I had no problem in Feisty.  However, now that I've installed Gutsey I'm not connected when I boot up.  I have to go into System > Administration > Network and fiddle around.  I disconnect Wireless, check roaming mode, check wired connection, and then do the opposite.  When I finally get back to where I was with the Wireless connection checked and roaming mode unchecked, a window opens saying "Changing Interface Configuration" and then I'm connected.  I have to do this every time I start the computer.  I'm here looking for a way to fix this.

---

### Post by bmartin on 2007-10-20
> **rustybronco said:**
> acx-111 chipset and atheros chipsets, It makes the difference, both work in 7.04 and 7.10 
and that is the reason I choose them.
If anyone is unfortunate enough to come across an Atheros AR5007EG, they **don't** work with MadWiFi; [here are the NDISwrapper instructions]("http://ubuntuforums.org/showthread.php?t=512828").

---

### Post by hessiess on 2007-10-20
workes on live cd, dus not work once installed

---

### Post by Gina on 2007-10-20
Yes - I think it's reasonable to expect things to improve from one release to the next!  How things can actually get worse I really don't know.  Wireless is something that needs sorting out before Ubuntu can really compete with Windows for the average user IMO.  In most other respects Ubuntu is progressing in leaps and bounds :)

---

### Post by Kappity on 2007-10-20
Working with a Belkin USB wireless adapter.  I had configured this under Feisty; it would see available wireless connections, but couldn't connect to them.  With Gutsy, suddenly it's working, with no additional configuration by me.

I hope it keeps working.

---

### Post by taliosfalcon on 2007-10-20
My wireless worked flawlessly in feisty off a fresh install, it looks like i'm going to have to ndiswrapper it to get it working in gutsy

---

### Post by gluutbuntu on 2007-10-20
Hi all,

I'm using a WMP54G recognized by lspci as: RaLink RT2561/RT61 802.11g PCi
Doesn't work in ubuntu feisty nor in gutsy (also tried with opensuse 10.3) none of them work out of the box, nor with fiddling around. Ndiswrapper no solution (even with the windows drivers from the linksys CD), SerialMonkey RT2x00 driver no solution. And the RT61PCI driver from the distribution doesn't work either.

After fiddling around for a week, reading every distro forum there is about the subject, I'm returning to windows, very frustrating indeed, because I really want to give linux a go for my desktop, this however isn't working out.

Kind regards,
Gluutbuntu

---

### Post by mishaco on 2007-10-20
wireless was my one problem and gutsy fixed it !

unfortunately the price of my wireless connection was my dual head nvidia 6600 gt and dell 1907fp monitors . after alot of tinkering theyre finally the same resolution , but slow as molasses and with out compiz or anything clever . this is not the upgrade i had envisioned .

---

### Post by gluutbuntu on 2007-10-20
> **gluutbuntu said:**
> Hi all,

I'm using a WMP54G recognized by lspci as: RaLink RT2561/RT61 802.11g PCi
Doesn't work in ubuntu feisty nor in gutsy (also tried with opensuse 10.3) none of them work out of the box, nor with fiddling around. Ndiswrapper no solution (even with the windows drivers from the linksys CD), SerialMonkey RT2x00 driver no solution. And the RT61PCI driver from the distribution doesn't work either.

After fiddling around for a week, reading every distro forum there is about the subject, I'm returning to windows, very frustrating indeed, because I really want to give linux a go for my desktop, this however isn't working out.

Kind regards,
Gluutbuntu

After my last post I got mad and redo the configurations with ndiswrapper again and now it works (I'm posting this message from my ubuntu installation). Still a lot of hassle to get a common wireless card working, but okay it finally works

---

### Post by Het Irv on 2007-10-20
I need to change my Vote.  I put that I upgraded and that it doesn't work.  Well after fiddleing with it a bit (downloading the bcm43xx stuff from an earliyer post in this thread and then restarting, lo and behold IT WORKS.  

My wirless card?? WMP54GS

---

### Post by theak on 2007-10-21
Worked great in Feisty, but in Gutsy it doesn't connect at boot-up and I have to manually restart networking each time I start up my system.

I'm using RT2500 802.11g.

---

### Post by simongreen.net on 2007-10-21
My problem is slightly different. I have a boradcom 4312 chip, and use ndiswrapper to get it working.. lspci reports:
30:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

In Fesity, when I went between home and work (without shutting down the computer), the gnome network manager automatically updated the list of wireless networks available. However under gutsy, the list does not update, and I have to shutdown the computer to pick up the new network. Any ideas on how to fix this? Or should I fill a ubuntu bug for this?

I've emailed our lug mailing list, but no one was able to help.

---

### Post by UbuntuniX on 2007-10-21
Worked with both. :)

---

### Post by zekica on 2007-10-21
Works out-of-the box with TL-WN551G with Atheros AR2413 chipset, and on my laptop, it works with ndiswrapper - Broadcom BCM4318. It can scan for networks with bcm43xx but cannot connect.

---

### Post by sefs on 2007-10-21
Cnet or Dlink that previously wored in all up to feisty with some tinkering now totally fubared in Gutsy.  Inserting USB adapter now produces a hard lock when serialmonkey drivers are used, that needs a hard reboot.  Will have to try to see if I can get some ndiswrapper love later today.

PS: for those who from distr to distr get it working out of the box which wireless dongle are you using and which driver.  Thanks.

PSS: NDISwrapper with rt73 windows driver also produces hardlock and hard reset with caps lock and scroll lock blinking.

---

### Post by Kappity on 2007-10-21
> **Kappity said:**
> Working with a Belkin USB wireless adapter.  I had configured this under Feisty; it would see available wireless connections, but couldn't connect to them.  With Gutsy, suddenly it's working, with no additional configuration by me.

I hope it keeps working.

Should add that, under Feisty, I had used ndiswrapper to install the Belkin driver, and Gutsy apparently picked that up and ran with it.

The model I'm using is a "Belkin Wireless G USB Network Adapter".  The fine print on the back seems to show the model number as F5D7050.  One lesson in these discussions, though, seems to be that the same thing does *not* work for everybody.

Found that after leaving the computer in suspend overnight, it had unmounted all USB devices, including the wireless, but that's minor.

I own a Netgear wireless PCMIA card, but neither Feisty nor Gutsy can even detect that it's there.  I gather that there might be a (for me) rather complicated fix for that, which I'll look into when I have time.  This computer has a single USB port, so I have to use an external hub, or just use it for one thing at a time. 

I'm really pleased, though.  Gutsy is the first linux distribution I've tried where I was able to get *any* wireless working.  Shame that it's not working for everybody.

---

### Post by neilq101 on 2007-10-21
Lucky for you there Kappity, I just tried the Gutsy live cd and my Belkin usb adapter, which I'm pretty sure is the same as yours, is completely incapable of connecting to a WEP network.  Under Feisty, it works straight away... Admittedly under Feisty I was using WPA, (we now use WEP for my house-mates' DS) but I can see no excuse for it not to connect to WEP out of the box.  As for my Broadcom wireless card, I have never been able to use NDISwrapper in any version of Ubuntu, and now the BCM43xx driver won't even download for some reason, says it can't connect to the server (when I'm using ethernet ofc).

Back to Windows then.

---

### Post by Kappity on 2007-10-21
> **neilq101 said:**
> Lucky for you there Kappity, I just tried the Gutsy live cd and my Belkin usb adapter, which I'm pretty sure is the same as yours, is completely incapable of connecting to a WEP network.  Under Feisty, it works straight away... Admittedly under Feisty I was using WPA, (we now use WEP for my house-mates' DS) but I can see no excuse for it not to connect to WEP out of the box.  As for my Broadcom wireless card, I have never been able to use NDISwrapper in any version of Ubuntu, and now the BCM43xx driver won't even download for some reason, says it can't connect to the server (when I'm using ethernet ofc).

Back to Windows then.

I guess that's the frustrating thing with wireless on these systems.  One person says he did something that got it working, you try it, and it won't work for you.  In this case I was just lucky, didn't figure anything out.  I wish I could offer expert advice, but I'm not an expert.:?

It's only a guess that ndiswrapper had anything to do with it.  Used it to install the driver under Feisty, and suddenly the device worked with Gutsy, so I don't have a better explanation, unless Gutsy just ignored the driver and did things its own way.  Is that possible?

---

### Post by bmpv666 on 2007-10-22
> **Pete051 said:**
> I found it impossible to connect with the rt61pci driver from the 2.6.22 kernel, luckily the rt61 driver from the 2.6.20 kernel worked fine.
This is the wireless-G pci card

may i ask you how did you manage to install the driver from the 2.6.20 kernel? 
i have a card with the the rt61 chipset, it works out of the box on Feisty. but I had no luck with Gutsy... 
I tried to follow [this]("http://www.lockergnome.com/nexus/linux/2007/10/18/ubuntu-gutsy-wireless-help") tutorial, and i got it working for a while. then for some reason, the connection would drop, and dmesg wouldn't provide many answers to what may have been the reason...only a reboot would make it work for a while more..

so i'm back to Feisty for now, until i find a feasible solution to this problem.

the irony is that i bought this card because of this chipset, and Ralink provides open source drivers for it. i thought that by making this choice i was preventing future problems in this camp...oh boy if i was wrong...:(

---

### Post by easytiger on 2007-10-22
When i upgraded from feisty to gutsy the wireless via the gnome applet for roaming worked perfectly. My wireless was WPA personal with TKIP. However since the first day it worked the applet that let me connect has now gone missing. It doesn't run and the manual connection box from System->network doesn't let me authenticate. 

Anyone know the name of the applet or how to get it back? my understanding is it should appear when i enable network roaming for an interface.

Also.. why doesn't the manual configuration dialog offer the same authentication options as the roaming one? Surely this is a serious bug?

---

### Post by ushills on 2007-10-22
I had to uninstall network-manager and network-mamanger-gnome, then use Prefs>Network to set up a manual connection to my router with a RT61 card.

Works with WPA encryption to my router.

Doing the same with a RT61 vB card in Xubuntu does not work at all despite following the same steps.

---

### Post by acl123 on 2007-10-22
I have a Netgear WG311 v3. It didn't work when I started it up (and I almost cried).
However I got it to work by using the same instructions that I originally followed to get it working in Feisty - [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

In the end, all I needed to do was run this command:
sudo modprobe ndiswrapper

By the way, the one problem I had with those instructions was that I couldn't install the newest version of ndiswrapper, I had to install the older version.

I ran Envy again to install my graphics card and now I've just skimmed through all my apps and everything seems to be working. Cool.

---

### Post by stevoo on 2007-10-23
well it was easy to make it work ..... the haard part is to make it stay up and running ! 

There seems to be a lot of issues with the wirelles of 7.10 ! 

I guess something is not right

---

### Post by mschraier on 2007-10-23
I had a Wubi install of Fiesty, and once I inputed my SSID & WEP it worked perfectly.  I am try ing Gutsy on LiveCD (have Freespire installed at the moment), it finds my SSID, I input the WEP and choose DCHP.  The Wifi light goes on but I cannot connect to the network though.   I have a Dell E1505 with Intel Pro WIreless 3945 ABG.  HELP !!!!

---

### Post by dnel on 2007-10-23
I have an Edimax PCI MIMO card which worked flawlessly under Feisty. I initially upgraded to Gutsy but the machine became unusable by hanging within a minute of loading up which may have been the wireless at fault or possibly my mouse which bathed in hot Tea during the install. :s

I did a full reinstall after this and the wireless didn't work at all initially and hung after a few minutes of getting it to work using iwconfig, dmesg showed CTS errors in  so I switched my network to pure 802.11g which fixed that but now the computer hangs after any significant amount of upstream traffic which is how it remains.

It's sad to see wireless support took a stride backwards with this release.

---

### Post by Zipster90 on 2007-10-23
> **hessiess said:**
> workes on live cd, dus not work once installed

This is exactly what's happening to me. I gave an Intel 4965AGN that worked beautifully on the live CD. But once I installed Gutsy on the hard drive, I can't even detect networks. It appears that my wireless card is detected, but it isn't doing diddly squat. It worked perfectly in Suse 10.3, and perfectly on the Gutsy live CD, but now it's crap! Help! :confused:

---

### Post by DonParker on 2007-10-23
After a clean install my wireless card sort of works. It sees my router and SSID but after I enter the 128 bit WEP key my system hangs. And I mean hangs!  I can't even move the mouse.   Any ideas about next steps would be welcome.:confused:

---

### Post by neilq101 on 2007-10-23
Turns out my problem was simply that i hadn't connected to a WEP network before, and didn't realise Network Manager needed me to select ASCII before i put my key in.  The restricted drivers manager also installs the broadcom firmware perfectly now.  This is still a bad thing though; I didn't have to tell Windows what type of wireless key it was, so why should I have to tell Ubuntu? And even if there is a reason, how is a newbie supposed to figure that out? Plus I'm sure when I first tried and failed to get my Broadcom to work, I did exactly the same thing as I did this time, but I guess I may be wrong.  Still, happy to find that everything works great now and I don't have to go back to Windows.

---

### Post by sefs on 2007-10-23
Serialmonkey rt2500 legacy driver still works.  I manage to get my hand on a cnet pci card that is a rt2500 based card. After compiling and installing it (the rt2500 driver)  works but sadly it does not support WPA2.

---

### Post by modmidget on 2007-10-23
I "upgraded" from Feisty to Gusty three days ago.  After the upgrade I could not get a wireless connection.  After tinkering around for about 5 minutes I discovered the upgrade had lost my user name and wep encryption key from the configuration file.  I entered both pieces of info and that was the end of my problem.  Everything works great now.  My wireless card is a Zyxel Zyair G300 PCI card.  It's advertised to work with Linux right out of the box and it has worked well for me in SuSE, Mandrake, and Ubuntu.

---

### Post by boozker on 2007-10-23
It just amazes me that this many people have this problem. I have had it and tried everything and even worse Ubuntu must see this and won't offer a way to to go back to Feisty wireless setup. It obviously worked better but they had to change it. 

[http://ubuntuforums.org/showthread.php?t=587800](http://ubuntuforums.org/showthread.php?t=587800)

That is my post and look how many thing DIDN'T work

---

### Post by kaufman on 2007-10-23
Mine didn't work at all with feisty or gutsy...both clean installs. I remenber reading about known issues with ubuntu wireless on IBMx60.
No help from the forum. I'm back to xp again.

---

### Post by boozker on 2007-10-23
I know what you mean about switching to XP. I hate XP and have a Mac OS X and Ubuntu, but each day I can't get on the internet when it worked fine on the previous versions of Ubuntu makes me want to switch to the stealing, bloated, Windows XP or Vista. IF this doesn't somehow get fixed soon I will, but man do I not want to.

---

### Post by a2c39a on 2007-10-23
Hi Folks,

I Upgraded from Feisty to Gutsy about 3 days ago. Wireless did not work at all.
I have the RaLink RT61 mini PCI card which I followed a thread, back in Edgy days, to get working. An Edgy Kernel upgrade killed it quickly afterwards but that was soon fixed.
I had no problems with the Feisty upgrade nor any Kernel upgrades until Gutsy.

However if I boot the 2.6.20...... Kernel instead of the new 2.6.22....... then the RT61 works fine (that's how I'm posting this message!).

If I try to install the rt61.ko in the 2.6.22.... system it tells me 'incorrect driver type' or something similar. 
With the 2.6.22..... Kernel booted, clicking the wireless icon brings up a message box indicating that the hardware was not found.

Will try to find some time to look properly at what is going on!

With best wishes, John.

---

### Post by rustybronco on 2007-10-23
> **bmartin said:**
> If anyone is unfortunate enough to come across an Atheros AR5007EG, they **don't** work with MadWiFi; [here are the NDISwrapper instructions]("http://ubuntuforums.org/showthread.php?t=512828"). Yes, that was too broad of a statement, but for the most part true.

---

### Post by AFPilot on 2007-10-23
Feisty worked out of the box, Gutsy recognizes the device (listed correctly in lspci) but the OS won't recognize it. Both were fresh installs. Been searching forums and Google since last Thursday when the distro was released and haven't found anything helpful but have found others with the same problem.

---

### Post by starlily on 2007-10-24
I have a generic PCcard wifi adaptor that uses the rt2500 driver. I had it working fine with ndiswrapper on Feisty. Upgrading to Gutsy broke it; I can see wireless networks in roaming mode, but I cannot connect to them, nor can I connect with a manual config. It acts like its not negotiating with the AP at all. Naturally, nothing I do fixes it, because something NEW has been introduced without anyone telling us (the users) about it, and there is ZERO documentation about it. Nothing in the million and a half posts here covers the changes. 

It is pretty frightening that so many people have the exact same issue, that its apparent there have been some major changes in the wireless stack, yet NOTHING AT ALL has been said or offered as a solution by ANYONE in the Ubuntu dev chain.

---

### Post by bmartin on 2007-10-24
starlily, have you tried PCLinuxOS? It's was above Ubuntu in the distrowatch.com ratings. If you use NDISwrapper normally, you'll have the option to set your wireless up when you first start the distro (it has NDISwrapper functionality built-in). It makes everything much easier. As long as you nail wireless at the beginning, it stays with you for a long time.

Seemingly, the more people mess with their wireless, the harder it is to fix.

P.S. Have you tried the serialmonkey driver? The RT2500 driver that comes w/ Ubuntu is pretty much always broken.

---

### Post by frbe0101 on 2007-10-24
My wireless is kind of working, I don't know if its a problem between KDE and Gnome or if it's because of the upgrade, [http://ubuntuforums.org/showthread.php?t=589852](http://ubuntuforums.org/showthread.php?t=589852)
In hindsight I really should not have installed both right after each other!

---

### Post by starlily on 2007-10-24
> **bmartin said:**
> starlily, have you tried PCLinuxOS? It's was above Ubuntu in the distrowatch.com ratings. If you use NDISwrapper normally, you'll have the option to set your wireless up when you first start the distro (it has NDISwrapper functionality built-in). It makes everything much easier. As long as you nail wireless at the beginning, it stays with you for a long time.

Seemingly, the more people mess with their wireless, the harder it is to fix.

P.S. Have you tried the serialmonkey driver? The RT2500 driver that comes w/ Ubuntu is pretty much always broken.

Tried serialmonkey, same issue - can see the AP, cant connect. I have this feeling that no matter what I try, itll be the same - because *something fundamental changed* and no one has pointed it out yet. Makes me think it wont just be Ubuntu or Debian, either (think video and USB junk), but that could be my perception. 

The fact that all of us have to dig around and hunt for the change and figure out ourselves how to work with it is un-f'cking-bearable. Where are the devs, the people that made the changes, why arent they here to say "hi, we changed some stuff, for the better in the long run, but heres where things will break and heres how you might fix"? Hmm? Where? Locked in a basement eating Doritos and laughing in a chat channel somehwere? Sure feels like it. 

And the GUI tools completely piss me off. They are fine, IF the stuff they are controlling works flawlessly, which obviously its not. The second I start troubleshooting, I want a guide that tells me what to do in a terminal, with actual commands. Point And Click repair is for Windows, and you are not paying me nearly enough for that. 

So, the score is; rt2500 fails to connect to an AP using distrib, ndis and serialmonkey drivers, at least for me. Succeeded in wasting a very frustrating 24 hours for me so far, given that it took about 15 minutes to set up initially.

---

### Post by defconoii on 2007-10-24
belkin F5D7050-4 ver: 3002 does not work out of the box with gutsy gibbon

---

### Post by unisol on 2007-10-24
fiesty never worked on my system. the rt61 drivers caused the system to  freeze up. with gutsy it works most of the time, depending on weather conditions.

---

### Post by rustybronco on 2007-10-24
> **starlily said:**
> I have a generic PCcard wifi adaptor that uses the rt2500 driver. I had it working fine with ndiswrapper on Feisty. Upgrading to Gutsy broke it; I can see wireless networks in roaming mode, but I cannot connect to them, nor can I connect with a manual config. It acts like its not negotiating with the AP at all. Naturally, nothing I do fixes it, because something NEW has been introduced without anyone telling us (the users) about it, and there is ZERO documentation about it. Nothing in the million and a half posts here covers the changes. 

It is pretty frightening that so many people have the exact same issue, that its apparent there have been some major changes in the wireless stack, yet NOTHING AT ALL has been said or offered as a solution by ANYONE in the Ubuntu dev chain. 

Nice ******  support, Cannonical. I should have known there would be problems when the upgrade broke on the EXACT SAME timezone data bug that slaughtered upgrades six months ago. If you cant fix a simple link problem in six months, you damn sure arent going to help us fix the bigger stuff you break on upgrades, like wireless. Nice to know, now. 

Bitches. See if I ever tell anyone to use Ubuntu again.
WOW, pretty rough comments there...
How about...  
[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)
or [http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)

what model wireless device do you have?

---

### Post by Duffy on 2007-10-24
It seems to recognize that there is a wireless card present. Every time I enter the SSID and password it needs, then Kubuntu tries to restart the card with the new settings and the entire system locks up. You cannot do a thing. All keys and mouse actions are ignored. YOu have to use the power button or reset to restart the system. The wireless card worked perfect and was detected by 6.10, 7.04 required driver to be loaded with ndiswrapper, now this is a clean install, and while 7.10 recognizes the card, trying to activate it is locking up the system.  :(

---

### Post by starlily on 2007-10-24
> **starlily] 
I have a generic PCcard wifi adaptor that uses the rt2500 driver. I had it working fine with ndiswrapper on Feisty. ...
[/quote]
[quote=starlily]
...
So, the score is said:**
> 

[QUOTE=rustybronco;3621982]WOW, pretty rough comments there...
How about...  
[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)
or [http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)

what model wireless device do you have?

Sorry the abrasiveness distracted you from actually reading what I wrote. Nice try with the RTFM link though.

---

### Post by rustybronco on 2007-10-24
> **starlily said:**
> Sorry the abrasiveness distracted you from actually reading what I wrote. Nice try with the RTFM link though.I never get distracted by talking, just by ranting, you can try them or rant, one will possibly make things work, one wont. 

[https://launchpad.net/](https://launchpad.net/)   post your problems.

still did you try the links?

---

### Post by Duffy on 2007-10-24
> **Duffy said:**
> It seems to recognize that there is a wireless card present. Every time I enter the SSID and password it needs, then Kubuntu tries to restart the card with the new settings and the entire system locks up. You cannot do a thing. All keys and mouse actions are ignored. YOu have to use the power button or reset to restart the system. The wireless card worked perfect and was detected by 6.10, 7.04 required driver to be loaded with ndiswrapper, now this is a clean install, and while 7.10 recognizes the card, trying to activate it is locking up the system.  :(

I have now installed the driver using ndiswrapper.  The system locks up again. Restart and now I get a kernel panic. Same issue I had with 7.10 after upgrading from 7.04.  Only that time I was able to revert to an older kernel to get it running. Since I have now done a clean install of 7.10, no old kernel to revert to.  I guess I am back to again loading the OS for the fourth time trying to get this to work.  What a P.I.T.A.!!!!

---

### Post by toni2 on 2007-10-24
intel 3945 wireless:
  · ubuntu 7.04 running from cd, works perfectly
  · ubuntu 7.10 running from cd or upgraded from 7.04 doesn't work. It shows wifi's but when i try to connect, it can't.
  · kubuntu 7.10 running from cd, doesn't work.

---

### Post by bmartin on 2007-10-24
> **starlily said:**
> And the GUI tools completely piss me off. They are fine, IF the stuff they are controlling works flawlessly, which obviously its not. The second I start troubleshooting, I want a guide that tells me what to do in a terminal, with actual commands. Point And Click repair is for Windows, and you are not paying me nearly enough for that.
I had a similar disturbing problem. Have you ever had to edit your xorg.conf file? Usually, if you have a graphics problem, you can edit that file to fix it. It helps to have a log file handy to debug those sorts of problems.

The new failproof X server wrote logs ONLY of the failproof xorg.conf file. So I had to figure out how to make it so it wouldn't load the failproof settings. Then, once it wouldn't load anymore, I could read the log... and it was still a hassle to fix the problems.

---

### Post by starlily on 2007-10-24
I FIXED MINE. 

Wanna know what it was? Sure you do. 

Recap: I have a RT2500 pcmcia card (some offbrand thing). It worked perfectly with ndiswrapper on 7.04. It broke in the upgrade to 7.10. I could see APs, but not connect to them. All my ndis stuff was fine, everything loaded great, no worries anywhere, wtf?? :(

My blacklist had:
rt2500

I had to ADD:
rt2500pci

Pretty simple, really. Too bad it took a full day of frustration, reading, installing and uninstalling, reading, thinking, etc. to figure it out. 

I wish someone would have simply said "oh yes, we've added a new driver with a similar name", and it would have been dreamy if someone else at Ubuntu would have said "thanks, we'll watch for that in our update process". Too bad its a dream. 

Now see if your blacklist is up to date. 

Peace, 
Lily

---

### Post by Les Oeufs on 2007-10-24
Feisty definitely wins this round. Never tried wifi in Feisty before. Installed gusty on this computer, couldnt get wifi working after anything I did. 
Decided to see if feisty can do any better. Installed that, was connected in about 5 minutes

---

### Post by Yiftos on 2007-10-24
If you are using network manager, sudo gedit /etc/interfaces and remark out all except lo:  
Now in /etc/wpasupplicant create a file sudo gedit wpasupplicant.conf and the context within should be ENABLE=0
once saved then enter sudo touch wpasupplicant.conf

Reboot, then you should be able to use network manager with WEP or personal WPA passphrase.

---

### Post by Yiftos on 2007-10-24
Forgot to mention, use network manager to find the AP and just select it. It should prompt you to create a password for a KeyRing to lock the passphrase/wep key you entered.

---

### Post by GWoitena on 2007-10-24
Upgraded to Gutsy and the whole thing was seamless as far as my wireless connection was concerned until....

I don't know if this is a Gutsy problem or a Broadcom chipset problem or a router problem.  I upgraded to Gutsy with the RC.  No problem.  Everything worked perfectly.  Yesterday I buy a new D-Link DIR-615 802.11n router. My previous router was an older Netgear 802.11b.  I cannot connect to the new router using connection manager and WEP.   My current laptop wireless network card is a Motorolla 802.11g with the Broadcom chipset.  I can connect with WEP disabled but not using connection manager and WEP enabled.  I'm leaning toward the problem being the router and 802.11n because I stuck an old 802.11b wireless card into this laptop and still couldn't connect.  I ended up having to manually configure a connection to my SSID using WEP and dynamic DHCP.  

I guess this is OK as a workaround but I have to reconfigure each time I go somewhere and use a different network.

Any ideas as to the problem would be appreciated.  But I'm starting to figure that this is part of the cost of trying to be MS free until Ubuntu and Linux in general move further along.

---

### Post by gr8birdie on 2007-10-24
I upgraded to 7.10 and my linksys WPC54G card did not work until I follow the following instructions from 2 posts:
Echo ‘blacklist bcm43xx’ | sudo tee –a /etc/modprobe.d/blacklist
Sudo rmmod bcm43xx
Sudo rmmod ndiswrapper
Sudo apt-get remove ndiswrapper-utils
Sudo rm –r /etc/ndiswrapper/
Sudo rm –r /etc/modprobe.d/ndiswrapper
Sudo apt-get install ndiswrapper-utils
Sudo ndiswrapper –I /home/mike/Linksys/Linksys.inf
Sudo ndiswrapper –m
Sed –e ‘s/radiostate|1/radiostate|0/’ /etc/ndiswrapper/Linksys/*.conf
Sudo modprobe ndiswrapper
Once I did that it worked, but when I rebooted I had to do modprobe again.  With a little researce and a great how to by ubunturules I added the following in the terminal :

echo 'ndiswrapper' |sudo tee -a /etc/modules

Once I did that I have been fine.

Good luck

---

### Post by quoob on 2007-10-24
Encountering the ever-popular problem of not getting an IP address upon moving to Gutsy and after trying the various solutions mentioned in this forum -- from moving from the bcm43xx driver to replacing NetworkManager with Wicd -- it finally dawned on me that if we're not getting an IP address, maybe, just maybe, we're having trouble finding the DNS.  Well, after checking my DNS settings, I found that my static DNS addresses were gone so we were trying to use the flaky DNS in my wireless router.  Putting in my ISP's DNS addresses fixed my problems.  (At least until something else goes wrong such as perhaps a packet is lost somewhere or something equally devastating.)

UPDATE: <brain cramp> I see I horribly mixed up two issues I was engrossed in.  Not finding the DNS was the symptom seen in the browser , not the cause.  The cause, of course, is not communicating with DHCP to set up the network in the first place.  In my mucking around, I not only set a static DNS but alsoa  static IP address.  I did the static DNS because it had seemed more stable back in the Feisty days.  Both the DNS and DHCP on my router seem to be flaky, hence the mixup in my befuddled post.

---

### Post by chili555 on 2007-10-24
Upgraded my Thinkpad T60; my ipw3945 worked perfectly before and after. I did a fresh install on my Thinkpad T23. My no-name Prism II card needed a bit of fiddling to get working.

Gutsy wireless works just fine here.

---

### Post by misterbeetz on 2007-10-25
I can connect to my WPA network if I am in roaming mode however manual mode isn't working as it should.  Once I set manual configuration for network manager it connects fine until I reboot. After that it does not work again until I go back into network manager's manual config and re-enter my network settings.  Obviously the settings are already there but somehow re-entering everything allows me to connect again.  I have no experience with wireless in Feisty for comparison.

I'm using a TRENDnet TEW-443PI pci wireless adapter. (Atheros chipset)

- misterbeetz

---

### Post by bd@cb8be8510 on 2007-10-25
I'm working with a ASUS WL-167G USB-adapter, which was working fine under Feisty. After upgrading
to Gutsy, I could no longer connect to my network. When I start Gutsy with kernel Linux 2.6.20.16,
I can use my network as before. When starting Gutsy with kernel 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux I can't get the network operating. So the problem is related to the
kernel?

Listing the hardware gives the following results:

Kernel 2.6.20-16 :

*-network
       description: Wireless interface
       physical id: 1
       logical name: rausb0
       serial: 00:11:d8:8e:79:2d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RT2500USBSTA driverversion=1.0.0 - BETA2 multicast=yes wireless=RT2500USB WLAN

Kernel 2.6.22-14 :

*-network
       description: Wireless interface
       physical id: 1
       logical name: rausb0
       serial: 00:11:d8:8e:79:2d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

I wonder why the RT2500-drivers have not been associated to this device, although the have
been installed properly:

modprobe -vl *2500*
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2500pci.ko

When starting Gutsy with  2.6.22-14 one can see a short activity on the wlan @ booting the system. It looks as if the DNS-server has been found (DHCP-release?), because when I shut down the driver, I get the
following data:
sudo ifdown rausb0
There is already a pid file /var/run/dhclient.rausb0.pid with pid 5423
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/rausb0/00:11:d8:8e:79:2d
Sending on   LPF/rausb0/00:11:d8:8e:79:2d
Sending on   Socket/fallback
DHCPRELEASE on rausb0 to 192.168.1.1 port 67

However I can't ping the DNS-server. As all is working fine with kernel 2.6.20-16, how can I make that
the new kernel uses the drivers as used by the kernel before? --> rt2500usb.ko.

I tried a live-cd on a Dell Inspiron 5150 equipped with another ASUS WL-167G USB-adapter as well. When starting up, one can see 2 networks (my proper network and that of my neighboor). However
it is not possible to connect to my proper network (although it's an unprotected wireless network - only mac-address-blocking is used). Is there a major problem with kernel 2.2.22-14 regarding usb-wireless-networks? 

Please, give me some advice!  Thx in advance

---

### Post by tommcd on 2007-10-25
For me, the Ralink rt61 driver was broken in fiesty and caused my laptop to lockup solid on boot up. In gutsy the rt61 driver just works out of the box.  So this issue, at least, has been fixed.
As always, I did a clean install of gutsy, not an upgrade.

---

### Post by rustybronco on 2007-10-25
> **starlily said:**
> I have a generic PCcard wifi adaptor that uses the rt2500 driver.... If you cant fix a simple link problem in six months, you damn sure arent going to help us fix the bigger stuff you break on upgrades, like wireless. Nice to know, now. 



[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152027](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152027)

>  Tim Gardner wrote on 2007-10-24: (permalink) 
Can you guys try this for me:

wget [http://people.ubuntu.com/~rtg/linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.40UNRELEASED_i386.deb](http://people.ubuntu.com/~rtg/linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.40UNRELEASED_i386.deb)
sudo dpkg -i linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.40UNRELEASED_i386.deb
sudo reboot looks like something going on.

---

### Post by dbushong on 2007-10-27
> **chili555 said:**
> Upgraded my Thinkpad T60; my ipw3945 worked perfectly before and after. I did a fresh install on my Thinkpad T23. My no-name Prism II card needed a bit of fiddling to get working.

Gutsy wireless works just fine here.

My T23 worked great in Feisty (with blacklist prism2_pci), but no joy in Gutsy: it sees the APs but dhclient never finds anything.  What was the "bit of fiddling" you did?

---

### Post by gusmao on 2007-10-27
> **corncob said:**
> I had no problem in Feisty.  However, now that I've installed Gutsey I'm not connected when I boot up.  I have to go into System > Administration > Network and fiddle around.  I disconnect Wireless, check roaming mode, check wired connection, and then do the opposite.  When I finally get back to where I was with the Wireless connection checked and roaming mode unchecked, a window opens saying "Changing Interface Configuration" and then I'm connected.  I have to do this every time I start the computer.  I'm here looking for a way to fix this.

Corncob, did you manage to get it working? I'm having the same problem...

---

### Post by Zer0Nin3r on 2007-10-27
> **#Reistlehr- said:**
> i have a broadcom 4310 on my laptop. In feisty it took me three months to find the right drivers from HP to get to work with ndiswrapper. That is HP's fault for listing the wrong drivers. I wish that Gutsy, and Feisty had built in support for my Broadcom chipset. (It can't use the 43xx drivers or the 4318 drivers).

As consumers we can give our voice and support for open source to the manufacturers in hopes of creating change.

---

### Post by zyg0t3 on 2007-10-27
Personally trying to get my wifi to work was the biggest difficulty in using Gutsy. First i installed 64bit gutsy. The broadcom firmware didn't work. So i tried to get up and running with ndiswrapper. But for the life of me, i couldn't find the proper drivers to go with my wifi card. After 3 days and numerous downloads and tests i said screw it and wiped the partition. I then proceeded to install 32bit Gutsy. After install it took all but 5 minutes to get ndiswrapper and have wifi working.

IMHO this is one of the biggest problems in gutsy.

---

### Post by welshlion on 2007-10-29
When I first installed Feisty, I had to use ndiswrapper 1.9 to activate my TP-Link USB adapter and when I upgraded to Gutsy I had to do it all over again. 
What I like about Gutsy though is that it now opens my Windows shares without any further messing about... alas I never could open them under Feisty,even after trying various Samba share set-ups which I found on these forums.

Now can someone please help?..I've had a go at this [https://help.ubuntu.com/community/SimplyStunningLinuxDesktop](https://help.ubuntu.com/community/SimplyStunningLinuxDesktop) and I can't find the System tools, he refers to, under main menu/system/preferences.

Problem solved, found the answer in a thread about missing "Beryl"

---

### Post by dr_agon on 2007-11-04
It almost made me nuts, but finally I managed to get it going.
My wireless PCI card worked out-of-the-box on Feisty. A week ago I made a fresh installation of Gutsy, and the connection was lost. I have a rt2400 chipset on my wifi card and Gutsy AMD64 installed.

Here is a line from lspci:
04:07.0 Network controller: RaLink Wireless PCI Adapter RT2400 / RT2460

I was getting mad trying to figure out what the hell is wmaster0 interface for, and why iwconfig and ifconfig say everything is OK and I still have no connection. ](*,)
And the solution was so simple: 
[COLOR="DarkGreen"]
get rid of the enclosed rt2400pci drivers and install one from serialmonkey.[/COLOR] 

The rest was straightforward. The tutorials how to do it can be found on this forum.
The small inconvenience is that *iwlist scan* doesn't work with this driver. But now I don't need it.

---

### Post by roachk71 on 2007-11-10
My computer has an rt73 wireless USB NIC.

Actually, it does for a while using the included rt2x00 and rt73 drivers, then quits after a few hours. As for the CVS rt73 driver, it won't work at all (even after building and running RutilT, which simply crashes when a profile is applied.)

Now, I simply use a wired interface.

---

### Post by yvesg on 2007-11-11
I upgraded from Feisty to Gutsy on a Sony Vaio VGN-SZ5MN/B laptop, using the update manager. After reboot, the network icon showed a message about an SIOCGIFFLAGS error. No wifi peripheral had been detected.The peripheral was shown by the command "[FONT="Courier New"]lshw -C network[/FONT]" as  UNCLAIMED. The hardware is Pro/Wireless 3945ABG. Of course the commands "[FONT="Courier New"]ifconfig[/FONT]" and "[FONT="Courier New"] iwconfig[/FONT]" showed no wifi  connection.

The problem came from the kernel: version 2.6.22-14-i386 appeared first in [FONT="Courier New"]/boot/grub/menu.lst[/FONT]. I commented out the lines concerning this version, so that the fist choice became 2.6.22-14-generic. And after reboot, the wifi worked correctly.

---

### Post by rolex42 on 2007-11-11
YES it works!

I have an old laptop that I have used with Win XP for some time.
The laptop is old, I know, but still it works and it's a shame to
throw it away only because Windows is too demanding. So, after 
installing xubuntu 7.10 I needed my old WLAN adapter to work.

My equipment:

Dell Latitude C600, 256 MB RAM, 20 GB disk
XUbuntu 7.10 (2.6.22-14-generic)

NetGear MA111 (ver 1)

Zyxel P-335WT router
 IP Address: 	192.168.1.1
 IP Subnet Mask:255.255.255.0
 Channel 4 2427 MHz
 Security mode:         Static WEP
 WEP Encryption:        128-bit WEP
 Authentication method: Shared key

Now, with my solution at hand I can say that I started this setup wrong.
Reading a number of forums and help pages indicated that some hands on
was needed. But that was for older versions of Ubuntu, not 7.10:
Ex.
[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111)

What best describes how to correct setup the Netgear MA111 is chapter
5.6. Ubuntu 7.10 (Gutsy) at page [https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb).
It says: 
**"The prism2_usb driver works out of the box, also with NetworkManager."**

Unfortunately I didn't read that the first thing.
Instead I tried to follow descriptions for older versions and
* edited /etc/modprobe.d/aliases & /etc/network/interfaces
* installed linux-wlan-ng
* Got lots of error messages (see below)

In the beginning Network setting -> Wireless Properties did show Wireless settings.
But after restoring files to (I beleive) original setting there was only Connection settings.
I'm not certain exactly how I managed to get the Wireless settings to appear again
but after some editing, restart, disconnecting/connecting WLAN USB adapter etc it
came back.

My Zyxel router was configured for Shared key. I did find a very nice site describing
Shared key and Open system in WEP. Guess where. Microsoft Technet!
[http://technet.microsoft.com/sv-se/library/bb727047.aspx](http://technet.microsoft.com/sv-se/library/bb727047.aspx)
chapter  Do Not Use Shared Key Authentication

After reading the technet article i changed the router to 
Authentication method: Open system
I beleive the Shared key setting was a major reason to my earlier problems.

OK. This is probably the point where I should have started **without** editing files
and executing unix commands.

The solution is:
1/ Don't use Shared key in your WLAN router.
2/ Configure your Linux in Network Setting -> Wireless Properties 
	Wireless settings
	 Disable Roaming mode.
	 Network name (ESSID)  select your WLAN (In my case: Nygren)
	 Password type  (in my case WEP key)
	 Network password ...
	Connection settings.
	 Configuration: Automatic configuration (DHCP)
3/ Remove and insert the WLAN adapter if needed.
   Restart the computer if needed.

4/ Use full command to check
$ lsmod |grep prism
$ ifconfig
$ iwconfig

5/ Final working settings, /etc/network/interfaces:
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-key ef8e6e22ee040681e7907fdc98
wireless-essid Nygren

auto wlan0

___________________________________________________________________________

_**Some error messages**_

$ sudo ifup wlan0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.


Restore the above files to original and configure only in Network settings
$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:09:5b:41:ad:87
Sending on   LPF/wlan0/00:09:5b:41:ad:87
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


After restart
$ ifconfig
...
wlan0     Link encap:Ethernet  HWaddr 00:09:5B:41:AD:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

$ iwconfig
...
wlan0     no wireless extensions.

$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

---

### Post by drinkmocha on 2007-11-11
I have the Dell 1500 Wireless-N minicard in my Vostro with Broadcom chipset. It doesn't work for my Ubuntu Gutsy install. I tried several times to follow instructions from this forum but to no avail. The Broadcom 1390 unfortunately doesn't work for me. Good thing, I dual-boot to the lameass XP.

I am thinking of getting a USB wireless adapter instead, I think I might get the LINKSYS WUSB54GSC. Any other suggestion on what USB adapter I should get instead that would surely work in Gutsy?

---

### Post by Grafster on 2007-11-11
> **Pete051 said:**
> I found it impossible to connect with the rt61pci driver from the 2.6.22 kernel, luckily the rt61 driver from the 2.6.20 kernel worked fine.
This is the wireless-G pci card

This is the fundamental problem for everyone with this card.
The old driver worked perfectly... for no particular reason anyone can explain someone just updated to a "new" driver that doesn't work. (the only explanation I've heard is that apparently someone had some sort of problem using the older driver... so they decided to move back to having everyone on the same page and it not working at all? didn't really follow the logic).

I have the same problem, but haven't figured out out to get back to the good driver yet.

---

### Post by nnull on 2007-11-13
Wireless works, but then messes up and ends up locking up my computer.
Using the ipw3945ABG wireless card on my T61p, lots of bug reports about this card sadly :/ It has been a few months and still no real fix other than not using gnome network manager.

---

### Post by Merk42 on 2007-11-13
> **drinkmocha said:**
> I have the Dell 1500 Wireless-N minicard in my Vostro with Broadcom chipset. It doesn't work for my Ubuntu Gutsy install. I tried several times to follow instructions from this forum but to no avail. The Broadcom 1390 unfortunately doesn't work for me. Good thing, I dual-boot to the lameass XP.

I am thinking of getting a USB wireless adapter instead, I think I might get the LINKSYS WUSB54GSC. Any other suggestion on what USB adapter I should get instead that would surely work in Gutsy?

Do you know something I don't? I just got that exact model and it does NOT work 'out of the box'.  I dual boot, so I haven't fully looked into fixing it in Ubuntu yet.

---

### Post by lukipuki on 2007-11-15
Hello everybody,
I didn't read the whole thread (didn't have time). But this is my story: I am using Gentoo on almost every computer, so I am not a normal Ubuntu user. I have Ubuntu on one router. I upgraded feisty to gutsy and the wifi worked very bad. These are the stats of the router: [www.lukipuki.sk/ubuntu-wifi.png](www.lukipuki.sk/ubuntu-wifi.png). I upgraded on November 06 and solved the problem on November 15.

So I decided to downgrade the kernel. I added this line to /etc/apt/sources.list
```
deb [http://sk.archive.ubuntu.com/ubuntu/](http://sk.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse universe
```

And then
```
apt-get update
apt-get install linux-image-2.6.20-15-generic
reboot
```

Everything seems to work now.

---

### Post by bazzer on 2007-11-15
To be quite honest I'm getting sick of the crap support in Ubuntu for wireless devices. I've had to scratch about for "firmware this and modprobe that" to get networking going the last 4 releases of Ubuntu and it's wearing thin now. I really DON'T care whose fault it is, manufacturers, developers, whatever. It's not worth me wasting my time over.

I'm going back to XP for my home system.

---

### Post by JustLikeJsh on 2007-11-19
> **Zer0Nin3r said:**
> I rely on a wifi connection that I share (yes I pay) with my neighbor.  I upgraded the laptop first and had to boot to my windows partition to snag two files that were part of the restricted drivers Ubuntu was asking for.  One was the .deb file for the firmware cutter for Broadcom WiFi Cards (BCM 43xx) and the other was the "firmware" file that the cutter extracts from.  After these two steps the card is working flawlessly.  No need for Ndiswrapper either!



***EDIT***


Funny you mention that.  I have  a desktop that runs the RTL8187 driver and when I did the upgrade I had wifi initially.  I then did an update install and rebooted, now it's broken.  Have yet to try to troubleshoot it.  I know I used to run ndiswrapper in Feisty, I'm guessing I'll have to do the same.  (need to research a little bit to see if anyone else is having the same problems)

can someone pleasee tell me how to download those two files and install on ubuntu?  i have to get them from windows cuz no internet through ubuntu 7.10. Thanks.

---

### Post by Makcum on 2007-11-20
Yes it does but only with this trick
[http://ubuntuforums.org/showthread.php?t=617457&highlight=AR5007EG](http://ubuntuforums.org/showthread.php?t=617457&highlight=AR5007EG)

Acer Aspire 5052
My wireless card is  AR5007EG 
Ubuntu 7.10 x64

---

### Post by meastp on 2007-11-20
My wireless (intel ipw3945) does work, but it crashes at random, especially when using bittorrent.

Bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/109887](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/109887)

---

### Post by poobslag on 2007-11-21
I got Wireless working in Feisty after a lot of effort. However, it broke after upgrading to Gutsy.

Gutsy's "Restricted Drivers" manager found my drivers, but I can't see any networks. My card is reported as a "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller". It sounds like this particular card worked "out of the box" for some users in Gutsy, so I guess it's just my bad luck.

---

### Post by neilford on 2007-11-24
I have a home brew AMD 2400 based system with a Gigabyte motherboard. It has a Belkin FSD7000 with an RT61 chipset in it. I have been, successfully, running Feisty, "out of the box ", for some time on it. I upgraded to Gutsy and my wireless became sporadic. It will work for a few minutes after booting up, then I lose the connection. It only comes back with a reboot. I have tried using wicd and had limited success with it, The longest I have sustained a connection is about a half hour of continuous use. 
This has been sum of my experience with Ubuntu and wireless:

Dapper -  wireless worked immediately
Edgy - wireless did not work
Feisty - wireless worked flawlessly
Gutsy - wireless worked poorly to not at all

See a pattern, here?

neilford

---

### Post by TimeDragon on 2007-11-28
I have a belkin card with rt2500 drivers. i installed the driver with ndiswrapper and sometimes it works perfectly but most times it can't connect.
If i keep on rebooting then it starts but at times it need 6 reboot and a loss of half an hour....
does anybody knows how to resolve this?

---

### Post by Don Cox on 2007-11-29
[http://us.archive.ubuntu.com/ubuntu/...006-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/...006-3_i386.deb)

[http://xeve.de/down/wl_apsta.o](http://xeve.de/down/wl_apsta.o)


I updated to 7.10. Wireless worked but was slower to connect, ran at a lower percentage strength and occasionally dropped. Feisty was and is again perfect after giving up on Gutsy for the time being and reverting to Feisty using Acronis True Image.

The two files alluded to above are easy enought to download and save to the desktop. If I tried Gutsy again, in which directory or directories should each of the files be installed (or doesn't it matter)? 

Don Cox

---

### Post by dialgo on 2007-11-29
NETGEAR ROUTER

NETGEAR USB DONGLE

Both work after 2 days of messing lol but work they do.

NETWG11T
Or indeed the whole WG111 family do work, but certainly not out of the box, if you want to get them to work check out my post in the Networkign & Wireless section:

[http://ubuntuforums.org/showthread.php?t=626499]("http://ubuntuforums.org/showthread.php?t=626499")

---

### Post by cmp1988 on 2007-12-01
Ok here it goes...


Netgear WG311 v2 (TI ACX100 or ACX111 based chip, did not use Ndiswrapper)
DWL-G132 HW Ver. A2 (haven't tried yet, but will soon)

Dapper: Worked out of the box
Edgy: Worked out of the box
Feisty: Worked out of the box
Gutsy Alpha: Worked out of the box
Gutsy FINAL:  FROZE MY COMPUTER WHEN IT ATTEMPTED TO CONNECT TO NETWORK

I was shocked.  This card worked in many different versions of Ubuntu and several other distros, but with Gutsy Final.  My computer froze upon attempting to connect to a network, and my CAPS LOCK, and SCROLL LOCK lights were flashing at me. I remember this happening on my D-Link DWL-G132 USB wireless card in Feisty and the Knoppix LiveDVD.  This computer relies upon wireless connectivity because the Router is on a different floor.:(


Seems lately, Ubuntu is becoming less and less compatible with my computer.  First the whole GRUB mess, now a card that works in other versions of Ubunty, including Feisty, freezes my computer.

---

### Post by cmp1988 on 2007-12-01
Back,  I just tried out the DWL-G132 in Gutsy and...







IT WORKED! OMG!

This card didn't even work in Edgy, Feisty, and the Knoppix DVD.  As a matter of fact, it even froze the system entirely before.  Now it decides to work flawlessly in Gutsy.  I just had to Ndiswrapper the bad boy and I'm on my way.

---

### Post by Grafster on 2007-12-01
> **cmp1988 said:**
> 
This card didn't even work in Edgy, Feisty, and the Knoppix DVD.  As a matter of fact, it even froze the system entirely before.  Now it decides to work flawlessly in Gutsy.  I just had to Ndiswrapper the bad boy and I'm on my way.

Congrats! Yeah there's no ryme or reason to why wireless is working or not. Nobody really seems to have ownership of the issue. Things just sort of get changes and will work or won't work for no particular reason.

Good that you've got one that works though! Hope they don't change that particular bit of code in Hardy.

---

### Post by cmp1988 on 2007-12-02
> **Grafster said:**
> Congrats! Yeah there's no ryme or reason to why wireless is working or not. Nobody really seems to have ownership of the issue. Things just sort of get changes and will work or won't work for no particular reason.

Good that you've got one that works though! Hope they don't change that particular bit of code in Hardy.

Yea, same here.  I hope they do fix that bit of code that would get my other card that's always worked, to start working again.  I do have a problem with the DWL-G132 starting at boot time though, even though I've done the whole "ndiswrapper -m" command.

---

### Post by LinuxLuver29 on 2007-12-03
After a bit of tinkering in Gusty, I got my wireless working in appox. 10 min.  I am using Dell Wireless Card which contains a BroadCom chipset.  If anyone needs help, PM me.

---

### Post by erothoff on 2007-12-09
My wireless generally works with Gutsy right out of the box. I have had it disconnect and require a reboot to reconnect, which is a bit annoying, but generally only after a long idle time. Things ARE improving...

---

### Post by MSchenker on 2007-12-09
Thanks for posting this poll.

My wireless connection is not working.  I'm running a Kubuntu desktop, and a Kubuntu laptop.  It's very frustrating.

---

### Post by sanctified-x on 2007-12-10
For the life of me I am STILL trying to get my Atheros card to work in Gutsy.
Will Hardy be the fix I am looking for? 
Lol...

---

### Post by Achetar on 2007-12-10
The only thing I had to do to get it work again was to type the following:

```
sudo modprobe ndiswrapper
```. And then log off with Save Session enabled! W00T! When I upgraded to Feisty at first only my WiFi worked, then when I did it again 4 months later, everything else worked. I am pleased that this time EVERYTHING WORKED!!! (Aside from being unable to enable PRISM2_DOWNLOAD_SUPPORT no matter how many times I rebuild the kernel) Thank you Canonical!

---

### Post by d^v3 on 2007-12-10
i had some problems initially.  when i had first install fiesty,  i had dual booted with xp.  the major problem there was the braodcom card.  i had an old atheros card laying around at work and poped it in, did a fresh full install and was doing just fine.  after i upgrade to gutsy i didnt really have to do much save for re-adding a wpa key

---

### Post by MSchenker on 2007-12-10
I'm confused how there could be such different experiences with wireless.  Mine simply doesn't work, while other people seem to get it working with no problems at all.

What accounts for the difference?

Is it configuration?

Here's what I'm running:
Desktop is a Compaq Presario with Kubuntu 7.10.
Printer is an HP Photosmart 8250
Wireless router is a D-Link 802.11/b/g/a

Laptop is a Sony Vaio with Kubuntu 7.10
Wireless card is an Intel Pro Wireless 2200

Can someone tell me if there is something about the equipment I just named that might be causing my problem, because I'm getting totally frustrated with wireless issues.

---

### Post by sanctified-x on 2007-12-10
@ MSchenker

I got it up and running I think maybe at try #9 with [this]("http://ubuntuforums.org/showthread.php?t=512828") guide. Ever since then It has not worked. Well if I had it running, why is it not running now, you might ask. I made a mistake in my partitioning and gave Ubuntu 4BG instead of the 10 I had planned to originally. After something like 2 hours it was telling me it had no more space left. Stupid me uninstalled and reinstalled and it has not worked since. I've tried just about every guide I can find on here. My plan is just to attack it over Christmas break and not stop until I get it working fully.

---

### Post by MSchenker on 2007-12-11
sanctified-x,
Unfortunately, again, that guide won't help me.

If you look at the poll results, about 53% of people here cannot get wireless to work at all.  Another 25% could get it to work only with some tinkering.  That means that only 25% can get it working easily.

I'm really curious to know -- those of you who got wireless to work, what configuration do you have on your desktop/laptop?  What makes wireless work so well with some people and not work at all for others?  How can there be such huge differences if we are all running the same operating system?

Someone please explain!

---

### Post by Scotty Bones on 2007-12-11
Card: Linksys WMP54GS

I was never able to get it to work completely in Feisty.  I did get to the point where I could see my network, just couldn't connect to it.  With Gutsy the card showed up in the Restricted drivers manager.  All I had to do was point it to the driver (bcmwl5a.sys) I had extracted from the windows setup program.  I haven't tried security like WEP or WPA as I live in the middle of no where.  I do filter MAC's though.

---

### Post by Deep fried ice-cream on 2008-02-07
How do you get network-manager to read a 256 bit wep?

---

