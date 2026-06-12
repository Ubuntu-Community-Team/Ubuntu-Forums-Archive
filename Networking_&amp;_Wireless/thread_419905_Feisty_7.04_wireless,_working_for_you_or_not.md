---
title: "Feisty 7.04 wireless, working for you or not ?"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by alanmzifa on 2007-04-23
Having recently tried to update from 6.06 through 6.10 to 7.04 and encountering wireless difficulties I've been spending a lot of time on this forum and some threads in particular seeing if others were encountering problems and/or finding fixes.

In the end I decided to do a clean 6.06 install and was able to reconfigure wireless with a little tinkering, leaving 7.04 for another day.

**I'm curious to see how much of a problem wireless really is however for all others and as you don't normally hear from those who aren't having problems thought the best way to quantify it would be through a poll.**

---

### Post by alanmzifa on 2007-04-23
I've just realised that anwering the poll questions doesn't bring the post back to the top of the first page so unless it's made sticky or voters make a "bump" post the thread will be off the page in about 40 minutes.

Please therefore bump when you vote.

---

### Post by qrprat77 on 2007-04-23
My problem is with the Linksys WUSB54Gv4.
worked well with Eft, now I'm just left.  I guess the Fawn got a little too feisty or something!

---

### Post by Melcar on 2007-04-23
Running a Compaq laptop with a Broadcom 4318 chip.  Wireless worked flawlessly under Dapper and Edgy using ndiswrapper.  Now with Feisty the only way I can get a stable wireless connection is using the native firmware support, which is not that good of a solution since it caps my speed to 11Mbps.
When using ndiswrapper I can get the chip to "work" (the wireless button on the laptop turns on meaning that the module loads successfully) and I can scan for networks; it just refuses to connect to any network for some reason.

---

### Post by JerseyShoreComputer on 2007-04-23
Wireless worked in Edgy, but I had to use WiFi Radar in order to get it to work. Now with Fiesty, I just plug in the wireless card (Linksys) and it runs and connects to my home 128bit WEP network. I turned Roam mode off and used manual config... So far so good. We'll see what happens when I bring it to the office and try to connect to the WPA-PSK network here... I couldn't do that in Edgy.... Wish me luck!

---

### Post by kpjoyce on 2007-04-23
I'd imagine that you'll find that many of the people visting the forum for duscussing wireless and networking issues are having more issues with wireless and/or networking than the general user population.

But I guess those that have it figured out are here as well ... which is good for those of us who, like me, are out of ideas.

---

### Post by RomeReactor on 2007-04-23
Hi. I've had wireless since Dapper, with a Marvell w8300 card using NdisWrapper; back then it would auto-connect at boot. Then did a fresh Edgy install and for the first 3 months it refused to connect unless i ran **sudo dhclient wlan0 -g 192.168.1.66**, so I made an executable file called **.wireless** on my home folder

```
#!/bin/bash
dhclient wlan0 -g 192.168.1.66
```

and made a launcher for it in "Applications-->System Tools" (the command section reads **gksudo home/sho/.wireless**). Then, in the last month, after installing and removing just about every wireless management tool to be found in Synaptic and fiddling with /etc/network/interfaces, it started to connect on its own (I have no idea how that came to be); now I am on Feisty (also a fresh install) and I'm back at having to manually launch wireless (even though I *am* using exactly the same settings as before). Also, I had to remove network-manager.

---

### Post by maxol on 2007-04-23
I got round the Network Manager problem but now have very slow download speeds. More [here]("http://ubuntuforums.org/showthread.php?p=2517165&posted=1&")

---

### Post by jpatton on 2007-04-23
My experience is that depending on what driver your wireless is using a kernel upgrade may or may not break it...lol...and what might work for one may not work for another. That said, I have an Acer Travelmate 250, that was upgraded from 6.10 to 7.04. The laptop has a built-in wavelan wireless adapter that is based on the prism 2.5 chipset, at least from what I gather by reading the various posts. ANYway, the card actually uses the orinoco driver and in order to get mine to work i had to add the following entries to my blacklist file:

blacklist prism2
blacklist prism2_pci
blacklist hostap_pci
blacklist hostap

Your mileage may vary, good luck!

---

### Post by alex77 on 2007-04-23
bump

---

### Post by Ichijin on 2007-04-23
i have a cisco mpi350 and wireless didn't work straight out of the box.  I have tried wifi radar and wicd, that helped a little in that i can now connect to unsecure APs but still can't connect to secure ones

---

### Post by Catiline on 2007-04-23
I've had mixed fortunes.  On my Thinkpad T41, with its Atheros chipset, wireless worked on install.  However, compared to XP (dual boot machine) the signal strength was way way down.  Under Edgy it had been on a par.

On my desktop no dice whatsoever.  An RT61 chipset so I guess I was asking for it.  On the other hand I'm completely new to Linux and the card works like a trooper with XP.  Being a noob I just don't have the background to fix it.  The Terminal is way beyond the tinkering I've done with the XP command prompt and registry.  The workrounds to get the RT61 working, though well meaning, are way beyond my current level of understanding.

I'll keep tinkering because in all other respects I've been really impressed with Ubuntu.  Unfortunately it looks like I'll have to stick with XP in the medium term for my secure home network.

---

### Post by A*p on 2007-04-23
It works but is broken, It looses connection and reconnects randomly + SWScanner bails on me whenever I start a scan.  I am prob going to loose the avahi stuff and see if that helps if I cannot get it working as it should.  It was working great in dapper and edgy after some initial WPA tinkering.

Intel PRO/Wireless 2100  on a hpcompaq nx7010

---

### Post by Lokithor on 2007-04-23
I'm using a Linksys WUSB54G v4 and it worked out of the box.

Left it plugged in when I installed Feisty and then went to the Network Wireless Connection and changed the Properties to reflect my SSID and encryption key.

Very slick!   :)

---

### Post by cmat on 2007-04-23
A lot of stuff didn't work after I installed 7.04. Wireless on my desktop seemed to work flawlessly with NDISWrapper in 6.10 but failed to work in 7.04. I got it working on my desktop but my laptop is a total loss with it's atheros card, ndiswrapper didn't even work with my USB wireless that worked great with ubuntu on my desktop. I can't even get updates for my system to fix the problem without the internet.

---

### Post by msak007 on 2007-04-23
I had a few wireless problems on both my laptop and desktop.

Desktop:
Upgraded from Edgy --> Feisty, using a Linksys WMP54GS (Broadcom) w/ ndiswrapper. The card wasn't detected at all after a reboot (not even in the interfaces file). I tried uninstalling the driver, reinstalling it, removing the module, re-inserting it, etc., but nothing worked. I added the CD as a repo and then installed ndiswrapper-utils-1.9 (was running 1.8 in Edgy). Not sure why that wasn't listed as an update or an upgrade to 1.8 during my upgraded to Feisty, but it seems you can have all the different versions of the ndiswrapper utils installed at the same time. Once I installed the 1.9 version of the utils and removed / reinserted the module, it was picked up in both the interfaces file and in NetworkManager. 

Laptop:
Clean install of Feisty on an old Dell C610 with no built-in wireless, using an old WPC11 card which I believe is using the Prism I chipset. lspci doesn't pick it up, just shows the 2 PCMCIA slots (it used to in Edgy). "pccardctl info" does though:

```
lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420
02:01.1 CardBus bridge: Texas Instruments PCI1420
``````
pccardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1="The Linksys Group, Inc."
PRODID_2="Instant Wireless Network PC Card"
PRODID_3="ISL37300P"
PRODID_4="RevA"
MANFID=0274,1613
FUNCID=6
```In all previous versions I used to use the hostap driver. hostap, orinoco, and hermes are all loaded at the same time, so I would blacklist orinoco and hermes. When running Feisty beta and using hostap, the laptop would freeze if the card was in at bootup, but worked fine if inserted after bootup. After a clean install, the freezing problem persisted but the card no longer worked with NM. Blacklisting orinoco and hermes didn't do anything and they continued to load. I ended up blacklisting hostap (and hostap_cs) instead and now everything works fine.

---

### Post by Staudie on 2007-04-23
I'm in the same boat as some of you... It works but not completely. I'm using a Netgear WG111T (Wireless USB) connecting to a WGT624 with Ndiswrapper and WEP. It works great with the exception of bootup. I have to manually initialize the connection after boot. which causes other boot issues like NTP, but its been like this since beta.

***** UPDATE...  I tried to setup a second machine using the WG111T and it wont work. Drivers install but its not listed in iwconfig. After some checking I notice that the machine with the working doggle is listed at 2.6.20-14 but the new one is 2.6.20.15 ** The orininal machine was a fresh beta install but hasnt been updated in a couple weeks. The second is a fresh install from the lastest 15APR07 iso. After running an update on the beta machine Im stuck in the same boat. Now either machine works... arrrgg!

-Staudie

---

### Post by Ichijin on 2007-04-23
bump

---

### Post by Ek0nomik on 2007-04-23
I got mine to work, but only after some "tinkering".

I use Windows drivers and ndiswrapper.

---

### Post by jonocorp on 2007-04-23
It works on maybe 1 out of 100 tries.  I've been using the ndiswrapper and Network Manager since Dapper, and I'm able to connect easily.  I have the dreaded Broadcom 4318 chipset.

Now that I'm on Feisty, my connection strength is way lower than it should be.  The router is in the next room and my laptop shows a signal of 30%.

I can see the various networks, but something won't let me connect to them.  Network Manager keeps spinning and spinning.

Right now, I was finally able to connect after many tries.

I want to upgrade the ndiswrapper to the new 1.42, but I'm never successful in compiling the source.  I just want to get wireless to work after every upgrade.  It seems like wireless support craps out after every version.

---

### Post by ggratto on 2007-04-23
Dell 610 no built-in wireless,   heve a cisco aironet 350 working in the open...  have a linksys wpc11 which is not working at all .. the wpc11 not even seen by network manager...

---

### Post by JackF on 2007-04-23
My Compaq V2010LA laptop (internal Intel PRO/2200BG) with Linux Mint Bianca worked perfectly. Now after a clean install of Ubuntu Feisty is NOT working, even after several tweaks and using WiFi Radar. It does recognize all available networks but locks completly!

Any ideas of how to solve this?

---

### Post by luckebstrd on 2007-04-23
Had wireless working on Edgy, upgraded and all went fine except the wireless will no longer connect to my AP.  

Running a DLink DWA-142 (Marvel chipset I think) throught ndiswrapper, network manager using WPA2. The device shows up, just won't connect and nothing has worked yet to fix the problem.

---

### Post by msak007 on 2007-04-23
> **jonocorp said:**
> Now that I'm on Feisty, my connection strength is way lower than it should be.  The router is in the next room and my laptop shows a signal of 30%.
You know I didn't pay attention to it earlier, but I see the same thing now. My router is in the next room and the card in this comp has always had 100% signal. Now in Feisty it's @ ~46%!!! WTH happened?

---

### Post by mainely_linux on 2007-04-23
I went from 6.10 to 7.04 via upgrade.  My ipw3945 10/100 Intel Wireless device worked out of the box on my laptop.  The same cant be said of my dialup modem.

---

### Post by jonocorp on 2007-04-24
This is complete insanity now.  I just tried out an usb wifi adapter, and it works perfectly.  The insane part is when I click on the Network Manager and see that the usb adapter gets a better signal strength than my laptop.  No hassles there.  WTF???

My laptop says my signal is 30%, but the usb adapter says 90%.

---

### Post by cliff01 on 2007-04-24
I had to use Linuxant to get my wireless to work in Edgy, now that won't even help me with Fiesty. This is a major PIA!

---

### Post by gwhitener on 2007-04-24
bump

---

### Post by chili555 on 2007-04-24
Works perfectly on an ancient Thinkpad T23 and an equally ancient no-name Prism II card. The key-ring bugs me a bit, but I haven't yet decided to disable it.

---

### Post by zedfrugnug on 2007-04-24
bump

---

### Post by adampyre on 2007-04-24
I got my PCMCIA wireless card working with my old Dell C610 Laptop after finding the windows drivers and ndiswrapping them, but trying the same situation on my desktop with a WMP54GS with the recommended drivers doesn't work. It accepts the driver and iwconfig appears to be the same as on my laptop, but no go.... :(

---

### Post by JackF on 2007-04-24
Sorry but I will go back to Linux Mint 2.2 (Bianca) even having to do a fresh install again over my Ubuntu Fiesty installation!
I need my wireless connection too much!

Good luck to all of you!

---

### Post by NobleSavage on 2007-04-24
No luck for me.  I have IPW2200 and my network uses WPA2.   Network manager says I'm conected, but I can't ping any external IPs.   Wired network works fine. I have no idea what to try - I've read everying I can find and asked for help several times - no one seems to know.  :(

---

### Post by Smokersroom on 2007-04-25
Nada, Zip , Nothing.

I really want to use ubuntu, but this is a n00bs nightmare!

---

### Post by AirRaven on 2007-04-25
Installed 7.04 over a fully working 6.10 build. 

RT2500 Chipset-based WLAN PCI card. It appears in network-manager, but it can't seem to connect to the network I specify. 

I enter the SSID, Static IP, Gateway IP and Subnet Mask etc, but I can't connect to the internet in any application. I've tried multiple DNS servers- it's not a DNS entry error.

---

### Post by mrsticks on 2007-04-25
I have an Averatec 5500 laptop.  The builtin wireless uses the RT2500 chipset.  Dapper and Edgy ran the wireless just fine.  Feisty's network manager recognized my wireless router, but did not detect the signal.  The router is 20 feet away, and I usually get 95% signal from downstairs.  I got it working now.

I disabled roaming mode from the network monitor
I manually set my SSID with iwconfig
I did dhclient ra0 ( my wifi connection )

It now works everytime on reboot.

I havent read enough of the problem to know what's wrong, I just hope they fix it.  Id like to be able to easily connect to other wifi hotspots as before.

-peter

---

### Post by Scheater5 on 2007-04-25
Did a clean install of Kubuntu 7.04, wireless worked out of the box.  Wireless worked out of the box on a Dell Inspiron 9300 with an internal Intel wireless card.  I don't like KNetworkManager as much as WiFi-Radar, so I may install that later, but even with KNetworkManager I got connection working straightaway.

---

### Post by cliff01 on 2007-04-25
Clean install, no more wireless! This sucks, I don't have time to pull cat-V to my desk. And where is the ndisdriver??

---

### Post by Lord Illidan on 2007-04-25
I didn't really install it (no time to waste with exams) but I did try out the live cd on my dad's sony vaio with an intel wifi chipset.

Our wifi system is WPA2 with AES, and while network manager detected the network, it refused to connect with it. So I installed an edgy version of wicd, and it worked fine.

---

### Post by Ameeya on 2007-04-25
bump....wpa not working for me...not available as an option in network manager.

---

### Post by Melcar on 2007-04-25
To anyone having problems, you should try compiling ndiswrapper from source (if you are using ndiswrapper to get your wireless going).  That worked for me.

---

### Post by ruletrak on 2007-04-25
I'm a newbie and trying to get it to work on either a desktop with wusb54g adapter or preferably on a laptop with wpc54g card.  I must use wpa security.  Sometimes I can see the card and wireless networks--sometimes I can't.  When I am able to see networks---can't connect with wpa---only shows wep options which aren't acceptable.  Glad I don't have to use this for my regular use.  I'm learning way more than I want to about the guts of Ubuntu and hope as time goes by that this stuff will be more plug and play.  I was pleased to see the wired network and other things work right away--but this wireless thing has been awful.

Have a great day,
Rusty:confused:

---

### Post by jpatton on 2007-04-25
> **ruletrak said:**
> I'm a newbie and trying to get it to work on either a desktop with wusb54g adapter or preferably on a laptop with wpc54g card.  I must use wpa security.  Sometimes I can see the card and wireless networks--sometimes I can't.  When I am able to see networks---can't connect with wpa---only shows wep options which aren't acceptable.  Glad I don't have to use this for my regular use.  I'm learning way more than I want to about the guts of Ubuntu and hope as time goes by that this stuff will be more plug and play.  I was pleased to see the wired network and other things work right away--but this wireless thing has been awful.

Have a great day,
Rusty:confused:

Plug and Pray is certainly nice, but does anyone harken for the days when you had to scour the net for an S3 video driver just to get X to work? Most likely why I try to run Linux on such ancient machines...I miss the thrill! 

Although I must say the wi-fi garbage is fun...if you're in to that sort of thing ;)

---

### Post by haloedrain on 2007-04-25
I updated from Edgy on my Inspiron B130 (with the Broadcom airforce one wireless chipset that everyone seems to have trouble with).  The wireless has never worked properly before but it's much better now without any tinkering at all--finally I can see signal strength!

---

### Post by Razzl on 2007-04-25
I wasn't able to get wireless working with edgy and I've done a clean install of Feisty on the old partitions and still can't get it working.  I'm trying to go through the instructions on various postings and in Keir Thomases' new edition of his Begiinning Ubuntu book, but as a non-programmer I'm not making progress.

And I have no idea what "bump" means.  Failure to understand the beginner enough to explain the not-obvious is a real sin of Linux culture, apparently...:confused:

---

### Post by haloedrain on 2007-04-25
"bump" is forum-speak for posting a comment so the thread gets "bumped" up to the top of the forum so it doesn't get pushed to the next page because there aren't any new replies :)

---

### Post by ruletrak on 2007-04-25
> **jpatton said:**
> Plug and Pray is certainly nice, but does anyone harken for the days when you had to scour the net for an S3 video driver just to get X to work? Most likely why I try to run Linux on such ancient machines...I miss the thrill! 

Although I must say the wi-fi garbage is fun...if you're in to that sort of thing ;)

I must admit I enjoy a good puzzle and that's why I'm here in part.  I would love to be able to offer a viable alternative to my windows clients.  I wouldn't mind searching for the driver to offer the alterrnative--but unfortunately this type of work is a bit much for the average computer user.

Hope someone here can help us with this problem!!  On the flip side as I said before--this newest version is getting so much closer to being user friendly for the masses.  Hope the good work continues and accelerates.

Til then,
Rusty

---

### Post by genecaldwell on 2007-04-25
> **Ameeya said:**
> bump....wpa not working for me...not available as an option in network manager.same here, the card was detected, hell, it was even showing me the AP's around including my own as well as the signal strength, but I could not get it to connect at all. oh well, so much for the perfect score Ubuntu, you did well with this release, but I can't give you the gold star until I can install on a computer and have networking work out of the box. so I guess I have to stay with windoz till you get it working for people who don't want to hassle with black hole puzzles and millions of commands. give me a GUI wizard to get all my hardware working please.

---

### Post by TRinQtown on 2007-04-25
My wireless card worked out of the (Fiesty) box, but the lack of WPA-TKIP in the network manager applet is beyond my very limited Linux skills. I know wpasupplicant can fix this but it makes my brain hurt. Forgive me, but Windows XP is much better in this area.

---

### Post by Talon2 on 2007-04-25
> **alanmzifa said:**
> 
**I'm curious to see how much of a problem wireless really is.**

I didn't vote in the poll.  I usually don't come by this forum much.  I do use wireless extensively.  I've never had a problem with a wireless driver...in any operating system.

How is this you say?

I don't use wireless devices that require pci or usb drivers.  For those that are unaware, it is entirely possible to operate wirelessly without devices that need drivers (other than for the NIC).  Here are some that I use:

DWL-2100AP in client mode - in use with a desktop system running Ubuntu.
[http://www.dlink.com/products/?pid=292](http://www.dlink.com/products/?pid=292)

DWL-G820 - in use with a desktop system running Ubuntu.
[http://www.dlink.com/products/?pid=333](http://www.dlink.com/products/?pid=333)

DWL-G730AP in client mode - In use with a laptop system running Ubuntu.
[http://www.dlink.com/products/?pid=346](http://www.dlink.com/products/?pid=346)

Configuration is accomplished via Firefox.  This method might be something some folks would want to consider in the future.  For me, doing wireless this way Just Works (tm).

FWIW:  This isn't a Dlink ad.  Other makers of wireless equipment make similar devices.  I just happen to use Dlink devices.  The DWL-2100AP is a really super little device to use to for wireless support for a desktop setup.

---

### Post by jpatton on 2007-04-25
> **genecaldwell said:**
> same here, the card was detected, hell, it was even showing me the AP's around including my own as well as the signal strength, but I could not get it to connect at all. oh well, so much for the perfect score Ubuntu, you did well with this release, but I can't give you the gold star until I can install on a computer and have networking work out of the box. so I guess I have to stay with windoz till you get it working for people who don't want to hassle with black hole puzzles and millions of commands. give me a GUI wizard to get all my hardware working please.
Not sure if Ubuntu is really the culprit of the lack of broad wireless support. I think wireless is still new enough to be very quirky, and with the dominance of Windows in the market, if you can't get brand x wireless to work with Ubuntu, nobody really cares. There was a report out the other day that Windows owns 90% of the market and Linux only 4%....take that however you want

---

### Post by medad on 2007-04-25
I am using a Wg111v2 USB stick on a etower 466ix.  I selected "Connect to other wireless network" and set up WEP128 bit passphrase.  Which then set me up with a keyring.  I have to log into the keyring every time I get on the computer, but at least it worked.  This computer worked on the initial installation of the beta Feisty, but started to give me problems after I ran update manager.  I did some tweaks (of which I can't seem to recall) and it is now running okay.  I had to change the channel on my router.  That seemed to help with me connection problem.  If I even attempt to use Manual Configuration, my system will not recognize my wireless stick.  But once I restore it back to its default setting, the system is trying to connect again.  I actually wanted to install xubuntu, but I couldn't get it to connect to anything.

---

### Post by ruletrak on 2007-04-25
> **jpatton said:**
> Not sure if Ubuntu is really the culprit of the lack of broad wireless support. I think wireless is still new enough to be very quirky, and with the dominance of Windows in the market, if you can't get brand x wireless to work with Ubuntu, nobody really cares. There was a report out the other day that Windows owns 90% of the market and Linux only 4%....take that however you want

Wireless is definitely used extensively throughout the traditional business world and should be supported for any OS.  I'm a computer tech by trade and I'm sure that better than 50% of the businesses out there use some kind of wireless.  Either for laptops that travel or just in the standard offices.  It has nothing to do with windows dominance--it has everything to do with convenience to access the internet and work over local networks.  I went to the eye doctor yesterday and the office had every computer in the building running on wireless.  If Ubuntu or any other Linux wants to compete and gain market share---they'll need to be more wireless friendly for the general public who aren't as savvy as the folks on this forum.  They want to plug it in and have it work without having to do a bunch of command work.

---

### Post by Lord Illidan on 2007-04-26
For WPA, I find that Wicd works very well..

---

### Post by BillUK on 2007-04-26
> **ruletrak said:**
> Wireless is definitely used extensively throughout the traditional business world and should be supported for any OS.  I'm a computer tech by trade and I'm sure that better than 50% of the businesses out there use some kind of wireless.  Either for laptops that travel or just in the standard offices.  It has nothing to do with windows dominance--it has everything to do with convenience to access the internet and work over local networks.  I went to the eye doctor yesterday and the office had every computer in the building running on wireless.  If Ubuntu or any other Linux wants to compete and gain market share---they'll need to be more wireless friendly for the general public who aren't as savvy as the folks on this forum.  They want to plug it in and have it work without having to do a bunch of command work.

I TOTALLY AGREE.  

The alarm bells should be ringing loud and clear for Ubuntu 7.04 as a new final release should not have reached this stage if the beta tests were completed correctly on a typical user basis. This will discourage potential new users in a big way.

I have upgraded from a very reliable 6.10 to 7.04 with a Belkin F5D6000 v1000 wireless card to find that I simply cannot connect to the internet even after trying many suggestions from this forum. From the outset I could apparently connect to the router using manual settings (per wifi radar and wicd)  but in reality it is  not a working connection. DHCP does not work at all.

One curious feature is that an additional "unknown device" has appeared called 'wmaster0' associated with the wireless card but appears to be totally ineffective. This is not present under 6.10.  

I will probably be following the route taken by the guy who started this thread and moving back to a fresh install of 6.10 until a reliable upgrade is available.

---

### Post by B0b on 2007-04-26
I agree, the lack of wireless support does not help with the push for Linux to gain wider use. In order to gain wider acceptance amongst the everyday user (which I`m guessing is at least part of the plan) things need to work properly.

---

### Post by diepruis on 2007-04-26
I run two systems: one has an rt61 chipset wireless adapter, the other uses rt73. I have to install custom drivers and purge network-manager for Feisty to associate with the AP.

---

### Post by Yoeri on 2007-04-26
Zydas 1211 not working on my machine ... thinking of switching back to Edgy (needed recompile in Edgy but it worked). A bit disappointed in a much awaited release ...

---

### Post by palmerthegeek on 2007-04-26
During the beta I recongized the change in how wireless was going, trying to provide a better manager.  It is better, but sometimes it is slow to respond to the OS. I've noticed switching from manual mode, to roaming mode can sometimes take up to a minute or more.  
My "work around" is that I logout after I've made a wireless change.   
This seems to be working for me.
Still happy with Feisty!

---

### Post by peterbakker on 2007-04-26
No, Yes,
I use the Ralink PCI wifi card with the rt2500 chip. The card works out of the box from since 6.06. Since feisty, the renewed network manager just doesn't connect with my network. Network manager does see my (and other) wifi networks. Thus, i tried System>Administration>Network  and configured my network manually, like i was used to do in 6.06 & 6.10. This worked for me finally (after rebooting just too much because my desktop was connected, bet actually wasn't (...It felt like i was using M$) Then, i tried to use WICD network manager. Tried several versions (first stable, then latest) but also WICD didn't connect. It keeps hanging at "getting IP adress" or something for ages... As for me, wifi works, but after a lots of:confused: :( :mad:
(use 128 bits ASCII not hidden network)

---

### Post by jpatton on 2007-04-26
> **ruletrak said:**
> Wireless is definitely used extensively throughout the traditional business world and should be supported for any OS.  I'm a computer tech by trade and I'm sure that better than 50% of the businesses out there use some kind of wireless.  Either for laptops that travel or just in the standard offices.  It has nothing to do with windows dominance--it has everything to do with convenience to access the internet and work over local networks.  I went to the eye doctor yesterday and the office had every computer in the building running on wireless.  If Ubuntu or any other Linux wants to compete and gain market share---they'll need to be more wireless friendly for the general public who aren't as savvy as the folks on this forum.  They want to plug it in and have it work without having to do a bunch of command work.

i didn't mean that windows dominates the wireless market, i meant it seems from reading these threads that many people are using ndiswrapper, which allows a windows driver to work in linux, which means the vendors aren't as concnerned with building wifi drivers for linux as they are for windows.

---

### Post by jpatton on 2007-04-26
> **BillUK said:**
> I TOTALLY AGREE.  

The alarm bells should be ringing loud and clear for Ubuntu 7.04 as a new final release should not have reached this stage if the beta tests were completed correctly on a typical user basis. This will discourage potential new users in a big way.

...

I will probably be following the route taken by the guy who started this thread and moving back to a fresh install of 6.10 until a reliable upgrade is available.

it's amazing to me nearly 50% of people are unable to get wireless to work and this version of the os is the latest? makes me wonder if perhaps the beta download should be pushed more heavily to get more valid usability testing. would be interested in knowing if there is an accurate count of the number of folks that ran the beta and were using wifi equipment the average person would get at say best buy or walmart.

and again, it may not be the folks at ubuntu as much as the kernel development stuff. from what i have read on other posts is the kernel update in 6.10 broke many wireless nic's and you had to blacklist those drivers, which is what i had to do for both 6.10 after the kernel upgrade, AND 7.04 after the upgrade.

---

### Post by p110011 on 2007-04-26
Not very well. My first try at Ubuntu 6.10 was with a Dell usb adapter D1450ou and never was able to get it going. So I went out and got a Linksys WUSB54GC, still didn't work. Found a thread here on how to install the RT73 Ralink driver and all was well. Did a fresh install of Feisty and now I'm unable to get the Linksys to work, but the Dell works, kind of. Feisty picked it up right out of the box but it doesn't have a good signal and drops now and then, mostly now.

Gill

---

### Post by raymac46 on 2007-04-26
It works the same for me as it did with Edgy.
I use a D-Link DWL-G520 wifi adapter with WPA. The adapter has the well supported Atheros chipset which uses the madwifi driver in Linux.
With Edgy I followed the howto on a manual configuration of /etc/network/interfaces and /etc/wpa_supplicant.conf. When I clean installed Feisty, the Network Manager applet showed no network although it did offer to configure the Atheros card with WEP.
I repeated the steps to manually install WPA support, and it works fine. The Network Manager applet now says "Manual Configuration".
So the wireless support in Feisty for my case is no different-no GUI support and strictly a manual WPA setup.
I might add that two other distros  -PCLOS 2007 and Mepis 6.5 - offered me a GUI and direct configuration with WPA straight out of the box. They are KDE based so that might be a factor.

---

### Post by ruletrak on 2007-04-26
Based on the comments here---it sure looks like there's a problem with wireless in the new release.  I'm new to this whole thing and have some questions:

1) Who recognizes officially that it needs help and starts the process to get a fix in place??
2) Has the problem been recognized and identified by Ubuntu?
3) How do we know something is in the works to repair and how long will it take??

Just Curious--realize that much of this is done by volunteers but there must be some process to make it work and get improved on a timely basis......

Have a great day.....

---

### Post by cricalixwood on 2007-04-26
I'm using a CNet USB wireless stick, using the Ralink RT73 driver. Worked like a charm under 6.06 and 6.10. 
Upgraded to feisty a couple of days ago, and rebuilt the driver. Bulit and installed with no errors. 

But when I try to use it (on my Dell Inspiron 1000 laptop), the Caps Lock and Num lock ligts come on, and blink slowly, and the machine is completely hung.

To fix it, I have reverted to running the 2.6.27 kernel under Feisty, and not the 2.6.20 kernel. That works just fine.

Roger

---

### Post by jpatton on 2007-04-26
> **ruletrak said:**
> Based on the comments here---it sure looks like there's a problem with wireless in the new release.  I'm new to this whole thing and have some questions:

1) Who recognizes officially that it needs help and starts the process to get a fix in place??
2) Has the problem been recognized and identified by Ubuntu?
3) How do we know something is in the works to repair and how long will it take??

Just Curious--realize that much of this is done by volunteers but there must be some process to make it work and get improved on a timely basis......

Have a great day.....

I would second that

---

### Post by p110011 on 2007-04-26
> **cricalixwood said:**
> 
But when I try to use it (on my Dell Inspiron 1000 laptop), the Caps Lock and Num lock ligts come on, and blink slowly, and the machine is completely hung.
Roger

That's exactly what my clone desktop did, flashing keyboard lights and needed hard reboot.
Out of the box my wusb54gc would see wireless nets around me, but could not get it to connect. I tried manual settings, WEP, Broadcast essid, just would not connect. So I tried the thread for the RT73 Ralink  serialmonkey and as soon as I did comand to bring the device UP my system froze.

Part of that thread was to purge the networkmanager so now I have to manually restart the Dell constantly because it's a piece of don't.

But the rest of Feisty is great for me.:guitar:

---

### Post by shelleycat on 2007-04-26
Not working
ASUS A9rp laptop, card is a built in USB WL159g.

It used to work on 6.10 using the zd1211b driver, with modified usb id.  I cannot get that driver
to compile under 7.04.  No wireless devices have been found.  Doing a modprobe of zd1211rw puts the module in, but nothing else happens.  

I'm not sure how to re-compile the zd1211rw module yet.

---

### Post by shelleycat on 2007-04-26
> **Yoeri said:**
> Zydas 1211 not working on my machine ... thinking of switching back to Edgy (needed recompile in Edgy but it worked). A bit disappointed in a much awaited release ...
Have you managed to compile the zd1211 module (in 7.04), and if so how?

---

### Post by mpaget on 2007-04-26
[SOLVED]
I have an Averatec 5100 that has a centrino wireless card (ipw2100).  The radio is controlled by a software switch and the av5100 kernel module I used to turn on the radio was working in edgy, but after the upgrade the wireless card would not turn on.

Previously in /etc/network/interfaces I would turn on the radio at startup with: 
Lines from /etc/network/interfaces
```
auto eth1
iface eth1 inet dhcp
pre-up modprobe av5100 radio=1
wireless-essid yourESSID
wireless-key yourkey
```

but I would get the error in dmesg```

av5100: failed at request_region()

```

After some tinkering I changed the kernel module to the other rfswitch module and it worked!
Lines from /etc/network/interfaces 
```
auto eth1
iface eth1 inet dhcp
pre-up modprobe pbe5 radio=1
wireless-essid yourESSID
wireless-key yourkey
```

I hope this helps other Averatec users with the same problem.

---

### Post by Sensei_V on 2007-04-26
I wish I could change my vote, I got wireless to work in Feisty.  I explained it all in [gory detail]("http://ubuntuforums.org/showthread.php?t=424262") in another thread. :)

---

### Post by the_maassk on 2007-04-27
Took me almost everything....and finally WiCD got it working for me. I came across the bcmxx updated firmware on some thread after that ...but did not have the guts to mess with it. Too much trouble already.

Am happy with WiCD for now.

---

### Post by RomeReactor on 2007-04-27
Wow. After finally finding the [WICD page]("http://compwiz18.ig3.net/wicd/wb/"), I decided to give it a try and.... It worked! Now I'm happy with it; it even has a tray icon. Perhaps it should be included in Gutsy, instead of Network Manager, seeing as it's [released under the GPL]("http://compwiz18.ig3.net/wicd/wb/pages/about.php").

---

### Post by dkaddict on 2007-04-27
I did an upgrade to Feisty around 6 or 7 weeks ago and have had no problems. With regards to the wireless issue, I didn't even know my laptop had a 802.11g card built in. I subscribed to BT Total Broadband and as part of the deal was given a 'BT Home Hub' (I think it is a customized Thompson router). I found out that I had a wireless card in my notebook, turned it on, and used 'Wireless Assistant' to detect and connect to my BT Home Hub. All I needed to do in order to link my wireless card to my Home Hub was to start 'Wireless Assistant' select the relevant connection and enter the WEP key (found on the back of the BT HHub) at the prompt invoked by WiAsst. APT and my internet connection both worked as well as they had with a cable connection with no probs.

This may be of use, however.

In order to have USB devices detected in Ubuntu I had to add options to Grub by way of modifying my '/boot/grub/menu.lst'. 
Before wireless I simply had to add 'noapic' to the end of the lines beginning with 'kernel' in the above file.
This option, alas, renders my wireless card as being unuseable so instead of 'noapic', I added 'irqpoll' to the end of the said lines in '/boot/grub/menu.lst'

eg, so it looks like (Added option is red!)>>>

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash [COLOR="Red"]irqpoll[/COLOR]
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault




This is where I found out how to change grub options

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

and

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Google has loads of stuff on irqpoll.

Hope this may be of some help to someone.

PEACE

dkaddict

---

### Post by msak007 on 2007-04-27
> **dkaddict said:**
> Before wireless I simply had to add 'noapic' to the end of the lines beginning with 'kernel' in the above file.
This option, alas, renders my wireless card as being unuseable so instead of 'noapic', I added 'irqpoll' to the end of the said lines in '/boot/grub/menu.lst'

eg, so it looks like (Added option is red!)>>>

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash [COLOR=Red]irqpoll[/COLOR]
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
Interesting. Not to go off topic, but I had "noapictimer" at the end of my kernel entry, and it rendered the Feisty kernel (2.6.20-15) unbootable (all previous Edgy kernels and the recovery Feisty kernel booted fine). I kept getting errors at the initial bootup about invalid IRQs, then kept getting timeout errors accessing the hard drives, then i'd be dumped to a shell environment (not bash) with the prompt "initramfs>" and the system wouldn't boot. Removing that option fixed it and I can now boot, I'll have to look into irqpoll.

Back on topic. Regarding WiCD, I tried it once and couldn't get it to work. Besides that, I'm on Kubuntu and it doesn't integrate very well into KDE (no system tray icon or applet, for example, like you have in Gnome). Even though my wireless is working, I think something is seriously wrong because my signal is half what I used to have in Edgy. Bug in kernel, NM, ndiswrapper?

---

### Post by Neeks on 2007-04-27
I installed Feisty from alternate cd, and couldne get my wireless working even though it worked on 6.06. Tried uninstalling network manager and installing wicd instead as some ppl have suggested. Works great now!! But for some reason it says my signal strength is zero..... but its working great. I dont know why its not displaying my signal strength correctly? Any ideas??

---

### Post by SwaroopKunduru on 2007-04-27
> **Ek0nomik said:**
> I got mine to work, but only after some "tinkering".

I use Windows drivers and ndiswrapper.

I did the same but do not work. Could you please let me know what all the steps you followed? I am having dell laptop. I was useing ndiswrapper and windows drivers on 6.04 and I can't even see wireless icon in Network manager applet.

Requested to please help.

Thanks and regards,

Swaroop Kunduru.

---

### Post by cricalixwood on 2007-04-27
My previous message was that my laptop hung solid: I now think that that MAY have been an error on my part. I assigned a static IP; but also tried to run DHclient for the interface.  I now think that it was that that hung the machine.

Anyway, it is now working, with a static IP. I have not yet been brave enough to reboot and see what happens!

Roger

---

### Post by DarkN00b on 2007-04-27
Linksys wpc54g v3 PCMCIA card with Broadcom 4318 chipset. I installed the firmware and connected right away.

---

### Post by thomasca on 2007-04-27
I was able to get the wireless to connect on the first try at home, but when I try to connect to the wireless at my campus, Nm-applet will connect but won't retrieve a IP address, and network-admin will connect and retrieve an IP address, but drop it after 15 seconds.

I have to do sudo dhclient wlan0 to get it to retrieve an IP address and keep it. Otherwise, it won't get it from DHCP or will, but drop it after a while.

Also, ifconfig refuses to recognize it with ifup. Why that is, I don't know.

---

### Post by belekas on 2007-04-27
broadcom 4318 airforceone 54g rev2 wifi card on fujitsu-amilo 1650 doesnt work, because on windows when i press the button it turns the wifi on and the light comes red, on ubuntu/linux mint that never happens. tried native/ndiswrapper whatever, nothing worked. anyone has found a cure? would be lovely.

---

### Post by phansiizwe on 2007-04-27
I had to remove network-manager, use ndiswrapper instead of the official "beta" drivers, but then everything worked together with wpa supplicant for WPA2.

*** I have a AVM Fritz!WLAN USB Stick ***

---

### Post by Handssolow on 2007-04-27
> **ruletrak said:**
> Based on the comments here---it sure looks like there's a problem with wireless in the new release.  I'm new to this whole thing and have some questions:

1) Who recognizes officially that it needs help and starts the process to get a fix in place??
2) Has the problem been recognized and identified by Ubuntu?
3) How do we know something is in the works to repair and how long will it take??

Just Curious--realize that much of this is done by volunteers but there must be some process to make it work and get improved on a timely basis......

Have a great day.....

I agree. Taking the problem of the RT2500 chipset wireless cards working under Feisty, where in the Forum do you find any acknowledgement  and progress reports? Is it a Launchpad thing? I'm wondering how long it will be before I can switch on my PC and not have to go into the Terminal to ifconfig down my card to enter my essid and WEP key. Yes I want to move over to WPA but looks like I'll have to wait for a new driver.

Finally to those posting with a report telling us of their success, please identify the wireless card you are using with your report.

---

### Post by dcraigp2002 on 2007-04-27
I have two laptops. I did a fresh install from disk. On my HP the install went fine but I have a Belkin wireless card. The Belkin has the Broadcom chipset. It was a pain in the butt but I finally got it going. The other laptop is a Toshiba Tecra. The Toshiba seems to be made for Ubuntu. I had zero problems with the install or the wireless.

---

### Post by RodneyLee on 2007-04-27
Not for me, tryed near everthing, system just got worse, did reinstall and it got even worse, trying from 6.04 now

---

### Post by dworourke on 2007-04-28
My Broadcom 43xx would not work after Feisty upgrade.
Copied all bcm* files from /lib/firmware/'old kernel name" to new kernel directory. Rebooted; now all is well.

---

### Post by jasonbrisbane on 2007-04-28
> **alanmzifa said:**
> Having recently tried to update from 6.06 through 6.10 to 7.04 and encountering wireless difficulties I've been spending a lot of time on this forum and some threads in particular seeing if others were encountering problems and/or finding fixes.

In the end I decided to do a clean 6.06 install and was able to reconfigure wireless with a little tinkering, leaving 7.04 for another day.

**I'm curious to see how much of a problem wireless really is however for all others and as you don't normally hear from those who aren't having problems thought the best way to quantify it would be through a poll.**

Hi,

Just wanted to thank all of the people who posted on the forums.

I now am sending this through my encrypted WPA connection on my Compaq Presario M2000 Laptop with inbuilt Broadcom 4306 (rev 03) wireless adaptor.

Here is how I go this to work:

1) Firstly, Back up All your data. You DO have backup's right? Including Favourites, Databases, files, etc?
2) Download the ISO of Ubuntu 7.04 and burn a New CD for it.
3) Reboot and run the CD. 

3a) Now, As you watch the install start to run, you will see something strange. "bcm43xx_microcodeX.fw not found" errors. What is this? The program is looking for FW files? What is an FW? Well it is a 'cut' firmware file that the 'cutter' program creates... Ooh looks like Ubuntu 7.04 is actually looking for the firmware by default. But of course it wont find it since the firmware is copyright (or not Open, at least).

4) Install the Ubuntu 7.04 cd. Connect up a WIRED network!!! When connected, you should be able to connect and start the Synaptic Package Manager. Search for bcm43xx-cutter and download it.
5) When prompted, select YES to search for the Firmware. (ooh. Aahh)
6) When downloads/installs will finish.
7) Unplug the wired network, reboot the laptop.


And watch the downloads fly.
After  DAYS of playing around with the upgraded version of Ubuntu (6.10 to 7.04) this worked for my in less than 4 hours. And that includes creating the backups to my ipod's 4GB disk and burning the CD.

The Network Manager icon on the toolbar automatically recognised that I had a wired and wireless connection. The SCAN automatically found the wireless essid and when I clicked on it, it prompted for the WPA password (with the option to select from the other connection types, but it knew that it was WPA, not WPA2, WEP, etc). Type the WPA passphrase and it asks again for the passphrase for the Keyring manager to assign to "default" (there was another topic about this...somewhere on this forum). There were a few messages warning about the bcm43xx-cutter not being an unsupported program or some such but just click past these with OK, or whatever.

Now it connects just fine and works like a treat!

Rock on Ubuntu!!
:guitar: :guitar: :guitar: 

Ubuntu creators' - Never will I doubt again!
:lolflag:
__________________
Regards,

Jason Brisbane
Ubuntu 7.04 Convert

---

### Post by sanderella on 2007-04-28
My wireless card Dell 1370WLAN has never worked on any Ubuntu version. Ongoing problems. :(

---

### Post by shabri on 2007-04-28
> **maxol said:**
> I got round the Network Manager problem but now have very slow download speeds. More [here]("http://ubuntuforums.org/showthread.php?p=2517165&posted=1&")

ditto

---

### Post by xadder on 2007-04-28
IBM T43 - worked straight away with clean install of fiesty. Also had worked flawlessly with edgy and dapper, no tweaking.

---

### Post by Tom Fury on 2007-04-28
I have an IBM T42p.  Atheros ar5212 chipset.  I tried all the fixes I could find in the forums.  No luck.  I re-installed 6.10, installed the restricted modules and network manager and my wireless worked straight up; WPA on a Linksys wireless router.  There are definitely some issues in Feisty.

---

### Post by ajlewis2 on 2007-04-28
Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

How do I compile madwifi-old which works when the madwifi-ng doesn't?

Actually it didn't work with the upgrade to Edgy either, but I was able to compile madwifi-old and that worked.   

My complaint with Feisty is that I cannot compile the madwifi-old. Here is how I did it with Edgy:

1. install the sharutils and the build-essential packages
2. uninstall the restricted-modules package
3. Get old madwifi [http://snapshots.madwifi.org/madwifi-old-current.tar.gz](http://snapshots.madwifi.org/madwifi-old-current.tar.gz)
4. untar, make, sudo make install
5. Check to make sure old modules are not loaded and remove if they are.
6. sudo modprobe ath_pci
7. sudo dhclient ath0

Feisty does not have 'sharutils' and I have a feeling that something else is used in its place.  I tried downloading sharutils from Debian and installing that, but the compiling still didn't work.  I will try it again and give more information if anyone is interested.

I have got the card working with ndiswrapper, but I'd rather use madwifi.  I can access a router farther away than the one in my building, but it is not a good connection and cuts out. The router in my building is not available to me to check out. I am using it with permission, but it is not mine.  

There is some reason why madwifi-old connects and madwifi-ng doesn't.

And the really sad story is that I just bought another card which I was sure was Ralink and it turns out to be the same chipset as my old one.  :( 

Anita

---

### Post by mah817 on 2007-04-28
I have a Sony laptop with an Atheros mini-pci wireless adapter. Everything was fine under 6.10 but when I did an upgrade to 7.04 the wireless card is not found under the network administration tool. It sees my wired ethernet adapter and my built in mini-pci modem. I am new to Linux and don't have a clue as to how to get the OS to find the wireless adapter. As a side note, Beryl quit working as well after the upgrade. HELP!

---

### Post by ajlewis2 on 2007-04-28
> **mah817 said:**
> I have a Sony laptop with an Atheros mini-pci wireless adapter. Everything was fine under 6.10 but when I did an upgrade to 7.04 the wireless card is not found under the network administration tool. It sees my wired ethernet adapter and my built in mini-pci modem. I am new to Linux and don't have a clue as to how to get the OS to find the wireless adapter.

You probably just need to install the restricted drivers. Put the install cd in your drive and then open up synaptic.  Do a search on 'restricted' and install the linux-restricted-modules that go with your kernel, probably 2.6.20-15 I think.

Probably the easiest thing after that would be to take out the cdrom and reboot.  If you still don't get anything, what do you get with these commands:

lspci  (just the info on your Atheros card)

lsmod |grep ath

I'm curious to see if this is the same chipset as I have.  

Thanks, Anita

---

### Post by mah817 on 2007-04-28
Actually, I did the upgrade with the Update Manager although I did download the 7.10 iso earlier. I will have to burn the cd and then try your suggestion. Thanks!

---

### Post by ajlewis2 on 2007-04-28
> **mah817 said:**
> Actually, I did the upgrade with the Update Manager although I did download the 7.10 iso earlier. I will have to burn the cd and then try your suggestion. Thanks!

In that case, check first in synaptic to see if the restricted drivers for the new kernel are installed. It could be that it did not upgrade them, but no sense burning the cd if the correct package is already installed. I guess since you don't have Internet on the new system, you will have to burn that cd.  That is the bummer with this--it's hard to fix when it is your Internet connection that is broken.  

If the restricted modules for your kernel (check with 'uname -r') are already installed, then look at 
'lsmod |grep ath' to see if the module is loaded.  If not, try 'sudo modprobe ath_pci'.

Anita

---

### Post by rustybronco on 2007-04-28
wpc54g v2 also was working on edgy.

---

### Post by mah817 on 2007-04-28
> **ajlewis2 said:**
> In that case, check first in synaptic to see if the restricted drivers for the new kernel are installed. It could be that it did not upgrade them, but no sense burning the cd if the correct package is already installed. I guess since you don't have Internet on the new system, you will have to burn that cd.  That is the bummer with this--it's hard to fix when it is your Internet connection that is broken.  

If the restricted modules for your kernel (check with 'uname -r') are already installed, then look at 
'lsmod |grep ath' to see if the module is loaded.  If not, try 'sudo modprobe ath_pci'.

Anita

I should have waited for your reply, burned CD restricted drivers were loaded, I unloaded and could not reload from CD. Brought out the long Cat5 cable and then reloaded from the other repositories and rebooted and the Atheros driver was loaded this time.

In answer to your earlier request lspci returned 00:07.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
lsmod |grep ath returned ath_rate_sample        13184  1 
ath_pci                95392  0 
wlan                  203076  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               191696  3 ath_rate_sample,ath_pci

Thanks for pointing me in the right direction. I am new to Linux but not to computers. Now I don't have to go back to being a XP geek.

---

### Post by firesyde424 on 2007-04-28
I have an inspiron 9300 with an Intel 2200 B/G internal wireless card.  It worked right out of the box after a clean 7.04 install.  However, the "wifi" light to the left of the power button didn't.  The 9300 requires that you press the "Fn" + "F2" keys together to toggle the power to the wifi card.  If the wifi light does not toggle, you really have no way of knowing whether or not the card is actually on.  In an attempt to get it fixed, I followed the install instructions located at [http://ipw2200.sourceforge.net/INSTALL](http://ipw2200.sourceforge.net/INSTALL) to get the best drivers I could.  The install went according to plan, and my wireless card began to function as it had before.  However, the wifi light still does not work, (yes it works in windows) so I am still left guessing as to whether or not my wireless card is powered or not.  (No the "wifi" light didn't work in 6.10 either)

---

### Post by foureight84 on 2007-04-28
latitude x1 with 2200BG not working with fiesty final. sd and cf slot won't read either.

---

### Post by jyabe on 2007-04-30
Okay I'm a linux-noob but I was able to get my netgearWG311v3 Wireless PCI adapter to work on Ubuntu Feisty 7.04 using ndiswrapper.  I found a good site with easy instructions and I thought I'd share it with you all:

[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/44780-getting-wireless-lan-card-work-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/44780-getting-wireless-lan-card-work-linux.html)  

The examples weren't exactly for the Ubuntu distro but most of the directions are applicable 'as is'.

I haven't read all the threads in this forum so the link might be a repeat.  I hope this helps!

---

### Post by sohaibma on 2007-04-30
My BCM4318 [AirForce One 54g] 802.11g  wireless card did not work out of the box on feisty, but I was able to set it up in barely 2 minutes using bcm43xx-fwcutter. This is a great improvement from edgy where I could not get it to work for hours sometimes.

This is how I did it:
[http://ubuntuforums.org/showthread.php?t=424994]("http://ubuntuforums.org/showthread.php?t=424994")

---

### Post by msak007 on 2007-04-30
> **sohaibma said:**
> My BCM4318 [AirForce One 54g] 802.11g  wireless card did not work out of the box on feisty, but I was able to set it up in barely 2 minutes using bcm43xx-fwcutter. This is a great improvement from edgy where I could not get it to work for hours sometimes.
That's great that it worked for you and I would use bcm43xx in a heartbeat over ndiswrapper, but I won't until it supports the full speed of 54g. 11 is fine for the internet, but it's just too slow when you're doing a lot of file transfers over the network.

---

### Post by jubilee33 on 2007-04-30
I wish I could vote twice.  I have two laptops.  One is a Dell Inspiron 600m with an ipw2100B (rev 04) mini pci card.  The wireless card worked out of the box for Dapper, Edgy and now Feisty.  In fact, the connection is the fastest ever, much better than in Windows XP.

However, on the other laptop, it's a sob story.  In Dapper, the ATI Xpress 200m graphic card (wide-screen too) and Intel soundcard both failed me relentlessly but I used bcm43xx-fwcutter for the bcm4311 uart (rev 01) wireless network card to work within 5 minutes.  In Edgy, the graphic card and wireless network card worked easily but sadly still a mute system from the very beginning.  I even filed a bug report.  Now finally I waited until Feisty was released.  When I first heard the login sound, I was so excited.  However, bcm43xx-fwcutter stopped working.  I seem to have connected but I cannot access the Internet.  It almost seems like the connection is too slow for any web page to load.  No obvious error.  I then tried ndiswrapper which ended up wiping out my network card's existence completely.  So now I went back to fwcutter and already uninstalled the useless network manager.  /etc/network/interfaces finally wasn't modified every time I reboot but still I am waiting for the wireless connection to REALLY work.

---

### Post by alharris on 2007-04-30
:confused: Dell and Acer Notebooks PCMCIA and USB wireless - updated from Edgy - neither worked on Wireless anymore but OK out of box on Edgy.  Desktop PC - Clean install of feisty and no wireless on PCI card nor USB.

Not too impressed with it all - fruitless Saturday - so went back to Edgy and all is well.

---

### Post by thomasca on 2007-04-30
Gah, lost my temper at my Desktop when I disconnected wireless, and lo and behold, it would reconnect but never get anything back from DHCP or assign the essid to the nickname, and thus wouldn't connect to anything.

This is on an Atheros card too. Had similiar problems on a Broadcom chipset.

I'm thinking that something just doesn't work well with upgrading dists and wireless drivers, as this has been a theme for me for dist upgrades in ubuntu. I would suggest that dist upgrades be discouraged for those who have their wireless working, as it causes more problems then it solves.

I'm going to try uninstalling the drivers I got from aptitude and reinstall them from the source packages. If that doesn't work, I'll try a clean install of 7.04, and if that doesn't work, I'll go right back to edgy.

---

### Post by jputman01 on 2007-04-30
my wireless did not work out of the box, but it worked with minimal effort, i actually used the same steps as i did with 6.10 but used an updated version of ndiswrapper. I could not get it to work by upgrading but did a clean install of 7.04 and all is well.

bcm4311 + ndiswrapper + network manager

---

### Post by micdhack on 2007-04-30
at first a managed to make it work with the native drivers but speed was 11mbits.
After some trials and error i managed to make it work with bcm4311 + ndiswrapper 1.43 + network manager. Signal is pretty weak (51% and im at the next room from the server) but i have 54mbits connection.
For updating the ndiswrapper i first used "sudo rmmod ndiswrapper" then "sudo make install" on the new ndiswrapper...But still this didnt updated the new version.
I had to copy ndiswrapper.ko file from the tar to  /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/.
After i did that i rebooted and i had wireless working. I also checked "ndiswrapper -v" and version is 1.43.

---

### Post by Carandol on 2007-04-30
I'm using an Edimax EW-7108PCg wifi PCMCIA card (RA2500 chip) in my IBM Thinkpad. It's worked well previously (in fact I bought it because it was advertised as compatible with Ubuntu!), but Network Manager won't work with it. I got it working in manual mode, but I can no longer connect to my university's MS VPN network -- I've been using pptpconfig, but that now refuses to connect, and I can't find anything else that will either.

---

### Post by scribbles on 2007-04-30
HP dv2315nr laptop, bcm4321 wlan. WLAN not working out of the box. Trying fwcutter

---

### Post by AmyRose on 2007-04-30
Wireless on my laptop is flawlessly supported, and I could always get onto the Internet at my college (WPA-PEAP MSCHAPv2 and all that stuff). It has an Atheros MiniPCI card in it.

My other computer, however, had perfectly working wireless in Edgy OUT OF THE BOX but with Feisty, it's horribly broken! ARGH! It has a Ralink RT2570 chipset in it and is a USB card. But I'm not downgrading to Edgy because the S3 video driver works in Feisty but not Edgy. GAAAH! I can never win!!! ](*,)

EDIT: I got it to work! [http://ubuntuforums.org/showpost.php?p=2570962&postcount=3](http://ubuntuforums.org/showpost.php?p=2570962&postcount=3)

> **firesyde424 said:**
> I have an inspiron 9300 with an Intel 2200 B/G internal wireless card.  It worked right out of the box after a clean 7.04 install.  However, the "wifi" light to the left of the power button didn't.  The 9300 requires that you press the "Fn" + "F2" keys together to toggle the power to the wifi card.  If the wifi light does not toggle, you really have no way of knowing whether or not the card is actually on.  In an attempt to get it fixed, I followed the install instructions located at [http://ipw2200.sourceforge.net/INSTALL](http://ipw2200.sourceforge.net/INSTALL) to get the best drivers I could.  The install went according to plan, and my wireless card began to function as it had before.  However, the wifi light still does not work, (yes it works in windows) so I am still left guessing as to whether or not my wireless card is powered or not.  (No the "wifi" light didn't work in 6.10 either)
The wifi light on Dell laptops is controlled by special Dell software on Windows, if I remember correctly.

---

### Post by perstromgren on 2007-05-01
Is there an overview of the problem somewhere, which gives the background to why this is a problem in the first place? It seems to me that whatever what re-written could be un-done, but that is only my naive view of it.

What exactly happened to many WLAN drivers between 6.10 and 7.04?

Per.

PS. I have a Compaq Presario 2100 that does not work with anything later than the 2.6.17-10-generic kernel.

---

### Post by jonnywombat on 2007-05-01
My belkin usb stick  f5d 7050 v4 works fine with wpa encryption, although only in b mode not in g mode, but thats ok. I also have a f5d 7050 v3 which works but does not support wpa when the v4 does.

Jonny

---

### Post by c600g on 2007-05-01
I have had Dapper on an old Dell Inspiron 1100 laptop with a DLink DWL-650+ PCMCIA wireless card, and it worked flawlessly "out of the CD".

 I skipped Edgy but decided to try out Feisty, so downloaded and burned a live CD image. When I boot up the live CD, it detects the wireless adapter, and even displays my local wireless network as available with a connection strength somewhere around 50%.

 However, when I try to connect to it (using WEP), no connection is made.

 The DWL-650+ uses the acx100r11 chipset.

 Ideas?

---

### Post by gwilki5691 on 2007-05-01
Hi all,
I have an ASUS laptop with built in Broadcom wireless chipset. I managed to get it working great in Dapper using ndiswrapper, but since my update to feisty have not managed to get it working :(
I'll post an update if I have any breakthru's.
TTFN

---

### Post by BillUK on 2007-05-01
> **perstromgren said:**
> Is there an overview of the problem somewhere, which gives the background to why this is a problem in the first place? It seems to me that whatever what re-written could be un-done, but that is only my naive view of it.

What exactly happened to many WLAN drivers between 6.10 and 7.04?

Per.

PS. I have a Compaq Presario 2100 that does not work with anything later than the 2.6.17-10-generic kernel.

I agree completely with your logic.

I have just reverted to a fresh install of 6.06 and it is so refreshing to find everything works first time with no mysterious fixes required.

When 6.10 was first released I had a similar problem with wireless connection for a week or two until a fix emerged. My Belkin 6001 V1000 card (identified as adm8211) developed a second ghost "Wmaster" identity as well as its original nomenclature and simply would not connect.  I could get the system working by moving back to an earlier kernel but eventually there was an upgrade and the problem went away.

I draw a parallel since the strange "wmaster" feature was also evident from the outset with 7.04 and so I conclude that there is a basic problem with the core package.

---

### Post by Bastien on 2007-05-01
Hi,
My wireless with the famous RT61 Chipset did not work on the previous versions.
I updated then made a clean install and it still did not work.
However I managed to have an uncrytpted wireless connection with wicd. Bur still isn't working with WEP nor WPA.

When I configure with network-manager my WEP key then try to connect the systm just freezes straight away.

Another problem, but I may post it on another section is that my Audio card does not work.
I worked on the previous versions, although the card was unknown.
Now Ubuntu 7.04 know it and gives it a name, but does not work with it... too bad...

If anyone has the key to knowlege and happiness I'd be happy to borrow it.

---

### Post by Churnd on 2007-05-01
Clean install on my Inspiron 8200.  Worked out of the box, but no WPA2 :(.  I'm bumming off my neighbor until I can get that bug worked out.  I saw the howto concerning manual config, but I want to keep using the network manager if possible.

---

### Post by scrooge_74 on 2007-05-01
I have a Compaq nx6110, had some issues using Edgy when trying to connect via Wireless, upgraded to Fiesty and now wireless conectiviy has improve.

The card is a Broadcom BCM4306

---

### Post by m0u53m4t on 2007-05-01
I think I'll downgrade back to 6.10. Wireless worked on that...

---

### Post by maxol on 2007-05-01
I have downgraded to 6.10 after much troubleshooting, Feisty seems to be a step backward in regard to networking.

---

### Post by tact on 2007-05-01
I had problems with wifi and 6.10 on my Dell D410 laptop.  Networkmanager was a separate install under edgy but it solved my problems.

When I upgraded to Fiesty (7.04) I chose to do a clean install (root is on a separate partition so all my configs were preserved) - Fiesty comes with networkmanager already installed and configured and it just worked out of the box.  No hassles at all.

Sorry for those who have a less happy experience.

(I also find that evolution and open office work much better and faster under fiesty.  I use evolution heavily, linked to 2 POP accounts and an essential Exchange server connection/account, and used to be pretty frustrated with unreliability under Edgy.  Its good under fiesty.)

---

### Post by ruletrak on 2007-05-01
> **ruletrak said:**
> Based on the comments here---it sure looks like there's a problem with wireless in the new release.  I'm new to this whole thing and have some questions:

1) Who recognizes officially that it needs help and starts the process to get a fix in place??
2) Has the problem been recognized and identified by Ubuntu?
3) How do we know something is in the works to repair and how long will it take??

Just Curious--realize that much of this is done by volunteers but there must be some process to make it work and get improved on a timely basis......

Have a great day.....

I don't see that these questions have been answered.  Can anyone help with them??  Seems there's a problem that needs to be addressed in the code and I'd like to know that someone is working on it.  Or is there another place we need to get this information so that someone at Ubuntu is addessing the issue???

---

### Post by helmut_hed on 2007-05-01
I still have the same problem I observed back in Dapper (my first Ubuntu release) - two incompatible drivers for the same prism2 device get loaded.  As many of you know they are hostap_pci and prism2_pci.  I prefer hostap_pci because it supports WPA, but it wouldn't be completely crazy to just do prism2_pci.  What certainly doesn't make sense, and has been the status quo for over a year, is to load both, preventing me from having any wireless access at all until I fix it.  Looks like there's a bug filed in Launchpad, high importance: [63989]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63989")
Jeff

---

### Post by Jerminator on 2007-05-01
Ubuntu had better get working on this. Wireless issues are going to turn a huge bloc of users off. I know that I haven't installed it simply because I need the wireless. I have been testing it on the LiveCD, but that's only so good.

---

### Post by mhallowes on 2007-05-01
I uninstalled Network Manager, and installed wicd.  Worked like a charm.  Thanks to whoever suggested that earlier in this thread!

---

### Post by IsaacJ on 2007-05-01
I can get wireless working but only without security. Unfortunately, that won't work for me. I need WPA. WICD made no difference with my WUBS54G v4.

I thought I would try Ndiswrapper instead of the native driver since others seem to have had some luck with that. No luck for me, though. I can't get it working at all in Feisty, though I once got it going in Edgy. I have only tinkered with Ubuntu now and then since I can't get security working, so I'm not a pro. Until I can get wireless working the way I want (even if it takes some tinkering) I'm afraid I'll never do much more than play with Ubuntu on occasion.

If only this problem could be resolved, I would start switching to Linux/Ubuntu as my primary OS and wean myself off of XP. I'm not interested in Vista. Man, Feisty is just so close I can almost taste it. I hope someone can improve wireless security soon, especially with regard to USB adapters. I don't have any room in my machine for an internal adapter so USB is it. 

Ever hopeful, I will keep checking back. Just in case something changes.



IsaacJ

---

### Post by ziadoz on 2007-05-01
Didn't work for me until I compiled a new kernel. Its been acknowledged as a kernel issue on Launchpad now.

---

### Post by montgoej on 2007-05-01
I still can't get wifi to work on my new laptop, I'm gonna get some rest and try again after school tomorrow. Atheros AR5005G 802.11abg
~Jordan Montgomery

---

### Post by Mr.Ham on 2007-05-01
Was able to install it, but still having difficulty getting it to work.



_________________
Tammy
[Far Circuits](http://www.who-sells-it.com/cy/far-circuits-623/far-circuits-173.html)  -  Download The Far Circuits Catalog

---

### Post by takakia on 2007-05-01
My wifi card is intel2200, it works well in my University.  I got an **[COLOR="Red"]Asus  WL-520g [/COLOR]**wireless router at home.  

I had initial problem with it in Kubuntu Fiesty Fawn 7.04.  After going through several forum posts (and spending several hours) and installing ieee80211-source package, and using Wireless Assistant, I got it working with 128-bit encryption.  Knetwork manager couldn't get connected.  I am using knetworkmanager too, to show my wired networks.

---

### Post by earobinson on 2007-05-02
no BCM4311

---

### Post by dschaller on 2007-05-02
My rt2500 chipset had been working out of the box with my Armada M700 since Breezy Badger. Did a clean install of 7.04 and spent two days at it with no joy. Finally went back to Edgy and it's working again. Right now, I plan to run Edgy to end-of-life. Maybe longer.

---

### Post by Chonnawonga on 2007-05-02
I'm using a Netgear WG511v1, Prism54 chipset. Worked fine on Edgy. After a clean install of Feisty, it can recognize networks, but won't connect. Uninstalling NM and replacing it with Wicd made no difference: it still gets stuck on "Obtaining IP address".

I'm very disappointed, but I may have to downgrade to Edgy, as I have a big research trip coming up, and I need everything working. I really hate to say this, but having to downgrade feels like M$ all over again. I know Ubuntu doesn't owe me anything, but still, I feel very let down.

---

### Post by kjj on 2007-05-02
On my Compaq Evo N410c it worked fine from install other than the signal strength being reported about half what it should be.

Currently 12 feet from AP with no obstructions and getting around 40%.  Same at home and all other makes of AP tried.

This problem was the same in Edgy, but was fine in dapper.

The laptop is an excellent cheap 2nd user unit off ebay and works with Ubuntu really well.  The Wireless is an atheros card installed in the internal expansion slot.

---

### Post by wakeme on 2007-05-03
Not working for me. My Cisco Aironet 350 detects the wireless lan, seems to give accurate signal strength, but it just won't connect! I'm loath to downgrade but it might be the easiest option in the short term.

---

### Post by phorus on 2007-05-03
I recently installed Xubuntu 6.10 from scratch, on a Latitude CPx with a Dlink G650 atheros A5212-based CardBus wireless card.  The card was detected by madwifi during install but did not work once the install was completed.  A forum post suggested updating restricted modules, which sorted out the problem.

Last night, when I tried a clean install of 7.04 on another Latitude, the Netgear WG511T v1 card, which uses the same A5212 chipset, was not detected during install, so there has clearly been a step back!

Tonight I'll drop in a wired card and load restricted modules to see if that resolves the problem - I'll report back in due course.

However, as madwifi seems potentially to offer the most seamless route to effective wireless support, and as I am sure many linux users will have specifically bought atheros-based hardware because of this, it is surprising that its invocation seems to have been dropped from the install process.  Rather, one would have expected the previous 6.10 shortcoming - effective detection of atheros cards but ineffective installation of the madwifi module - to have been corrected.

---

### Post by Outrunner on 2007-05-03
On a clean Feisty install it works straight away(TEW-443PI -AR5212 chipset)

---

### Post by phorus on 2007-05-03
Interesting.   Perhaps I should add that I used the Xubuntu Alternate install, so I could control the location of Grub.  Could it be that the Alternate install is in some way missing atheros chipset detection?

---

### Post by Dale Clarke on 2007-05-03
Running an Advent laptop with Marvell Libertas, even though I have got it to recognise the driver, nothing else happens unable to turn it on,even tried holding the Wifi button down...

Gone back to windows as like a lot here I need WIFI...

Dale

---

### Post by phorus on 2007-05-03
Re atheros support - booted last night's 7.04 installation again this afternoon in preparation to do battle with the wireless problem and as if by magic a message popped up about restricted drivers.  It seems the system has now spontaneously found the atheros wireless card!  It now shows in System > Network - previously it wasn't there - and I have been able to configure it without further problems.  :)

---

### Post by Paul_UK on 2007-05-04
Tried the live CD on my Dell Inspiron 640m with Intel 4965AGN wireless.  Wireless card does not show up anywhere - only the 10/100 ethernet port is available.

After problems with previous versions, I'm not going to bother trying to install this.  With each new release of Ubuntu and the promises that things like wireless will be sorted, I optimistically try it and end up disappointed.  I am looking for ease of use, and having to fiddle around in terminal to fix things that really should work is not acceptable.

Time to give SUSE a try on this new PC now.  If that doesn't work it'll be Windows for the next few months or until whenever one of the main Linux distros gets their act together with wireless.

---

### Post by scalvin on 2007-05-04
Man, this Linux stuff is just not ready for prime time when it comes to wireless. Ironically, it seems to get worse with every release. I have a laptop with AMD 64bit, and  Broadcom wireless chip, which apparently doesn't play well with Linux. I've been through this with Mac Powerbooks, now PC...How hard can it be to write a friggin driver for these things. If you are a PC manufacturer, please stop using Broadcom chipsets. Sheesh.:mad:

---

### Post by Corey on 2007-05-04
So strange that cards that use to work now don't :( I'm using a linksys card with the rt2500 chipset

---

### Post by Paul_UK on 2007-05-04
> **Corey said:**
> So strange that cards that use to work now don't :(

That seems to be the pattern with Ubuntu generally since 6.06.  It seems that if it's an LTS release there will be effort made to make it as stable as possible, but for any other release we just get it as it is at the release date, warts and all....

---

### Post by Electraglider on 2007-05-04
This is my first post and since my wireless seems to be working I shall try to at least convey what I have.

First off, I have a Gateway MT6452 laptop. The processor is an AMD64 X2 dual processor. My wireless adapter is a Realtek RTL8187. After getting it home and making sure everything worked with Windoze Vista I loaded up Ubuntu 6.10 x86 version. Everything worked with the exception of wireless, of course. I then used the upgrade feature to go to 7.04 and wireless still didn't work. I finally decided that, since I had the 64 bit processor, to try 7.04 AMD64. Lo and behold, that worked. I am now connected wirelessly and have had few problems. The only times I have had any problems is when I screw around with the settings to try different things. I have tried to use wifi-radar and have had no luck with that. I have tried to strengthen my encryption and I am only able to get it to work with WEP 40 bit Hexadecimal encryption. 

I have yet to try and take it out to connect up to a wireless  hotspot but since at this time that is not a high priority for me, I' m not too concerned about it. I will try it sometime just to see if I can get it to work.

Unfortunately I am not very good at documenting my efforts to get things working. I generally try the easy obvious things first. If that doesn't work I go to the forums and poke around looking to see if anyone is having the same issues as I am with the same hardware. If I can't find the same issues with the same hardware I try to find the same issues with different hardware. 

Suffice to say, I have a working connection at home and I am generally satisfied with it for the most part.

One thing however, in searching for an easy way to upgrade my encryption I discovered software readily available through Synaptic package manager that will, what did it say? crack WEP, WPA1 and WPA2 with up to 512k encryption after a few packets of data are intercepted. I mean really, what is the point of going through all the trouble of locking down your network when some pimply faced little kid with a computer can come along with some software and and break the encryption code? Go figure..

I noticed that I have a neighbor with an encrypted network that I can see on my computer and I'm sure he can see mine. I wonder if I should try one of those encryption cracking programs to see if they work.:confused:

---

### Post by alanh on 2007-05-04
Here's my experience:

Ever since I installed Feisty my D-Link DWL-650+ card will not connect to my wireless network. _However, I also have a Retail Plus USB wireless adapter that works perfectly._ The D-Link card recognises the wireless network and attempts to connect. The NetworkManager Applet 0.6.4 indicates 1 green light and prompts me for a password, which I enter. The device then tries to connect again but then fails.

Previously posted here:

[http://ubuntuforums.org/showthread.php?t=432618](http://ubuntuforums.org/showthread.php?t=432618)

---

### Post by rick1210 on 2007-05-04
I did a clean install and it works after some tinkering. I have a D-Link card with Atheros chipset. I had tried extensively to get it to work with Breezy, but never did. I suppose I may have succeeded eventually with more patience. I skipped Dapper and Edgy. The only issue I had with Feisty was that I finally found out that I needed to enable SSID broadcast. Some Googling seemed to indicate that this is a bug in Feisty.

---

### Post by syruppie on 2007-05-04
I did a clean install of Ubuntu 7.0.4.  My Dlink DWL-G650 (Atheros AR5212)  does not work.  It cannot establish a connection using wpa2.  Everything was working perfectly on 6.10.  

I can see a bunch of wireless networks / ssids but I can't connect to any of them.

---

### Post by ph8ze8 on 2007-05-05
I don't have my own laptop just a company one which is tied down. So i have been using the LIVE 6.10 ubuntu to get round that and use the internet with a usb ...... it is newish HP laptop and with 6.10 it wireless works with the built in card  like a dream...the only thing was mp3s,mpeg etc due to the licensing stuff. I have tried the live 7.04 and the wireless doesn't work, i have even tried two diffferent PCMCIA wireless cards with no luck.

Any ideas?

---

### Post by jamesmm on 2007-05-08
I tried following all the instructions on different threads. Clean install of feisty, wireless still doesnt work :(

---

### Post by frail on 2007-05-08
No wireless for me either with a clean install of 7.04.  Using an IBM Thinkpad T41p with Atheros wifi. My wifi card is recognized using a restricted driver but it won't connect to my router (Linksys WRT54G) using WPA2 TKIP+AES. WPA with TKIP or AES doesn't work either. And I won't use WEP or leave it unsecured. So that's that. With this release I was ready to ditch Windows for good but not having wifi is a showstopper (in fact, the *_only_* thing stopping me from switching). I'll try again in October with the release of 7.10.

---

### Post by gerrymoth on 2007-05-08
I originally had Network manager working fine on my Acer 2428 laptop until last week when I had the common problem of it looking like its connected okay, but no internet connection. After a few days trying to sort the problem while away from home I gave up and used Wifi Radar and manually entered my IP address, DNS address, etc..

Only on returning home I tried Network manager again, still had the same problem with Network Manager connecting but no internet connection, that is until I had a brainwave and connected to my router via the cable (noticed wired was via ETH1), then while still connected via the cable searched for wifi connections. At this point it asked for the keyring password (something I hadn't seen for a week or so).

Disconnected the cable and it automatically switched to wifi (on ETH1). Internet still worked.

Restarted the laptop and it asked for the keyring password and connected to the internet (Noticed wired was ETH0 and wifi ETH1).

I've power up/down about 20 times since then and its still keeping the wifi connection.

I'm not to clued up on all this so I think for some reason its losing or getting confused with ETH0 and ETH1.

---

### Post by ageilers on 2007-05-09
I had good luck with 7.04 live CD and my wife's IBM x31. Wireless worked fine. Not the same for the IBM T23. Wireless did not work with the CD, so I knew it would take a little work to make it work once I installed. I had to use a D-Link DWL-G650 (Atheros AR5212) to connect initially. No issues there, just popped the card in and configured WEP.
I had to blacklist following as someone in this thread suggested to get the onboard wireless to work:

blacklist prism2
blacklist prism2_pci
blacklist hostap_pci
blacklist hostap

Once I did that, the onboard wireless connected with a very strong signal everywhere.
Just for testing purposes, I tried my old Netgear MA521 (Rtl8180l). No go there. Device is seen by the Device Manager, but no network goin' on. A little searching tells me it is not worth the bother trying to get that to work.

---

### Post by diskinetic49 on 2007-05-09
buh-ump

---

### Post by jimrz on 2007-05-13
2 different systems, both with atheros 5212 chipsets, worked OTB. 

1 little glitch - network-manager could not "see" my router which was not broadcasting it's essid, although it could and did connect to others within range. this was not true of previous versions (bug?). setting the router to broadcast the essid solved the problem and all is working nicely.

---

### Post by Ashrael on 2007-05-14
Hi, I've got the netgear ma521 wirelesscard, it use to work, not so now....searched around for a sollution, but found none that worked,  Tried : [http://rtl8180-sa2400.sourceforge.net](http://rtl8180-sa2400.sourceforge.net) ..
Ran into this: 

:~/rtl8180-0.21$ make
make -C /lib/modules/2.6.20-15-386/build SUBDIRS=/home/adaptr/rtl8180-0.21 MODVERDIR=/home/adaptr/rtl8180-0.21 modules
make[1]: Entering directory `/lib/modules/2.6.20-15-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.20-15-386/build'
make: *** [2.6] Error 2

Anybody? hints, tips etc...

if not i'm reverting to edgy  ;(

---

### Post by davecambs on 2007-05-14
I had awful problems installing INPROCOM 2220 by reading these (and other forums). 

In the end I uninstalled my manually configured NDISWRAPPER and driver. 

I used add/remove package GUI. selected all. searched and installed ndiswrapper-utils. 

Then I ran the utils (I think it's ndiswrapper 1.8) - added my card driver file, configured my WEP settings, re-booted and it worked. 

The only strange thing is that the gui network tool shows no hardware, there is no driver in the restricted drivers manager either. Network performance seems ok though.

---

### Post by mmdski on 2007-05-14
I just bought a Dell Inspiron E1405 and it came with the ipw3945.  I installed 7.04, and wireless is working but is shakey -  duplicate packates and very slow.

*BUMP*

Edit:
Disregard the above statement.  My router was crap, I got a new one and now I'm flying.

---

### Post by Ashrael on 2007-05-14
Also i'm trying not to go the ndiswrapper way, why should i? it used to work before, so it is possible....

---

### Post by Chuckels550 on 2007-05-14
I got Network Manager with WPA to work using Feisty - Dlink DWL-650 wireless Atheros chipset- out of the box.  However every one or two days, I have to reboot the system in order to connect to my wireless access point.  I did a clean install of Feisty.  I never had this problem with Ubuntu 6.10.  I understood that in Edgy, the same problem existed with the KNetwork Manager, but not with Gnome's.   Does the problem go away with wifi-radar?

Issue resolved - Network Manager doesn't work for wireless.  However, the manual set up of the /etc/networking file along with generating the passphrase for WPA_Supplicant works according to the instructions in the community documentation works just fine for the Atheros chipset and madwifi drivers.

---

### Post by erichnewell on 2007-05-14
I have a Dell M65 with the Intel internal wireless (3945). I can connect to open WiFi no problem, and can setup WEP.

I cannot get WPA/WPA2 connections to work, and have not yet looked into the cause.

Additionally, kismet no longer works with either the internal card or my Orinoco Gold card...I cannot get any wireless device into a proper monitor mode, regardless of the driver or chipset.

:confused:

---

### Post by Ashrael on 2007-05-14
Well i've solved my probs...hope i can relay... 

installed ndiswrapper with synaptic.
also installed ndisgtk.
downloaded this inf file : [http://wejump.ifac.cnr.it/pages/pub/sw/drivers/network/Netgear%20MA521/NETMA521.inf](http://wejump.ifac.cnr.it/pages/pub/sw/drivers/network/Netgear%20MA521/NETMA521.inf)
started up a terminal and entered: sudo ndisgtk
pointed to the inf file....lol it works....

---

### Post by mistamcgoo on 2007-05-14
Wireless in feisty is going so bad for me that i decided to go back to windows 2000. 
i have been using ubuntu since breezy, had to do days of messing around to get at least 1 of my 3 different usb wifi sticks working in each new version .
now  I tried the same procedure i used in dapper and edgy to get my zd1211 chipset working, it's hopeless. same results with my atheros chipset usb stick. 


sorry but i've had it. The only os that ever worked really good for me is win2k, i'm going back to it.

---

### Post by Undertwotimes on 2007-05-14
So I'm 1/1.  On my laptop the upgrade went without a hitch, wireless is working fine,  with no issues what so ever (Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)). 

So yesterday I thought it would be cool to upgrade my girlfriends lap top right before she moved out of town for the summer...  She was in a big hurry so I didn't have a chance to test the wireless, but it booted up fine, so she left.  Today I find out that I'm in big f***ing trouble, as the wireless is no longer working (Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI).  I have no idea how to fix it.  Basically it looks like the driver is working, she can scan for other networks even, but the signal strength is 0 for everything, and it won't connect or get a dhcp request.  It seems others are having this problem as well.  I'm and idiot for upgrading with no time to test... arg.  I hate phone tech support.

---

### Post by sean on 2007-05-14
Dell D620 (Core 2 Duo, BCM4310 wireless).  Ndiswrapper does not work with NetworkManager at all.  I have to remove NetworkManager.  If I am connected with Ndiswrapper, my laptop locks up when I try to shut it down.  None of these problems existed with Edgy.

---

### Post by ctsdownloads on 2007-05-14
I think the message is pretty obvious - it's back to musical wifi cards for everyone! yippie! :guitar: 

[http://ubuntuforums.org/showthread.php?t=444006](http://ubuntuforums.org/showthread.php?t=444006)

---

### Post by earobinson on 2007-05-14
Works for me now :)

---

### Post by syruppie on 2007-05-15
> **Chuckels550 said:**
> I got Network Manager with WPA to work using Feisty - Dlink DWL-650 wireless Atheros chipset- out of the box.  However every one or two days, I have to reboot the system in order to connect to my wireless access point.  I did a clean install of Feisty.  I never had this problem with Ubuntu 6.10.  I understood that in Edgy, the same problem existed with the KNetwork Manager, but not with Gnome's.   Does the problem go away with wifi-radar?

i've tried this twice now! reinstalled ubuntu, dlink DWL-G650 detects wireless networks but cannot connect using WPA2-TKIP/AES.  BTW, my G650 is rev B4 which rev is yours? I don't know if it even matters.

And what is even funnier is my DWL-G520 (rev B1. 5213 chipset) pci card also has the same problem.  Sees the networks but cannot connect.  

BTW, my SSID is hidden, is that the reason?  6.10 worked flawlessly hidden or not.

---

### Post by joe.turion64x2 on 2007-05-15
My Atheros chip works like a charm!

Joe.

---

### Post by ctsdownloads on 2007-05-15
Hopefully the next upgrade keeps it this way, I sincerely am happy it is working for you.

---

### Post by joe.turion64x2 on 2007-05-15
> **ctsdownloads said:**
> Hopefully the next upgrade keeps it this way, I sincerely am happy it is working for you.
Thanks, I think it will keep working fine, it always has in all the Linux distributions I have installed. Besides there are plenty of good references of Atheros cards above Intel cards for example.

Joe.

---

### Post by DarthImpala on 2007-05-15
Finally got my Broadcom 4306 in my comcrap ... compaq presario 2100 working w/ the bcm43xx driver via a tutorial on this forum that used the firmware from the 4306 with the 43xx driver. However could not get it to work with WPA-PSK. I had to go to ndiswrapper and could not get the one from the packagemanager to work (modprobeing ndis kept failing). So I had to make from source and it was starting up from boot, but has recently stopped eventhough it is set in the config files (ndiswrapper -m). I can't get it to auto connect to non broadcasted ESSID's and have to enter in the key each time..... also I get less signal strength and less coverage with NDIS.... 

So I give it a working, but an WTF as well.

---

### Post by b_chris on 2007-05-15
I cannot get it to work, it is recognised... but...............

*-network
description: Wireless interface
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@03:00.0
logical name: eth1
version: 02
serial: 00:13:02:1f:f2:66
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list logical wireless
configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=no multicast=yes wireless=unassociated
resources: iomemory:edf00000-edf00fff irq:21

---

### Post by Ashrael on 2007-05-15
well, it seems that i was wrong... it worked last night (with ndiswrapper), but this morning it didn't...so i booted 6.10 from cd and it works...so did: lsmod and saw that it used module r818x....rebooted 7.04 and modprobed for r818x....it recognizes the netgear MA521 now...but i can't connect to anything..uninstalled all ndiswrapper packages...also i found out that wlassistant is no longer installed so did that....wlassistant says it sees my network...try to connect...nothing.. in the terminal window it keeps saying :  

Trying to get gateway address...
...from 'route'
Gateway address: 192.168.123.254
etc.etc.

but no connection...

suggestions? please..

---

### Post by Ashrael on 2007-05-15
ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:08:5A:1C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:3 overruns:0 frame:0
          TX packets:2306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1086 (1.0 KiB)  TX bytes:96832 (94.5 KiB)
          Interrupt:11 Memory:d8b7e000-d8b7e100 

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b  ESSID:"WhateverNe"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:F6:0D:08:39   
          Bit Rate=11 Mb/s   Sensitivity=80/85  
          Retry: on   Fragment thr: off
          Power Management: off
          Link Quality=1/100  Signal level=-81 dBm  Noise level=-157 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

so what's going on here?

---

### Post by Ashrael on 2007-05-15
wlassistant:

==>stderr: Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Operation not supported.
iwconfig_ap: /sbin/iwconfig wlan0 ap 00:0C:F6:0D:08:39
ifconfig_dhcp: /sbin/dhclient -q wlan0
==>stderr: There is already a pid file /var/run/dhclient.pid with pid 134993416
Trying to get gateway address...
...from 'route'
No default gateway.
OggS-SEEK: at 0 want 60408 got 51136 (diff-requested 60408)
OggS-SEEK: at 60352 want 520 got 0 (diff-requested -59832)

might this be the problem?

---

### Post by Ashrael on 2007-05-15
ah f*ck it i'm reverting to 6.10 again, cost me less time, and i KNOW it will work...
i'll just wait for a better version or a patch.. or i might try PCLinuxOS on this machine..the hardware recognition works much better there!

---

### Post by Ashrael on 2007-05-15
reverted, wlan works like a charm....no more feistyness for me... ;)

---

### Post by bmartin on 2007-05-15
I have one of those evil built-in Broadcom chipsets with the hardware switch. It has been a nightmare in the past, but it worked quite well after using [the method described here]("http://ubuntuforums.org/showthread.php?t=405990"). Even the hardware switch works. I had to use **ifdown** and **ifup** after setting my wireless properties; I have to repeat the ifdown/ifup steps when coming out of hibernation.

I'm not surprised to see so many people disgruntled. I used a 3rd party module to get my Belkin USB stick working when I had that; this is the first time I've had my Broadcom 4318 chipset working. HP printer support is pretty good; wireless is now the most painful aspect of the Ubuntu experience. The new Sabayon live DVD was able to recognize my chipset right away. Since the method above involves proprietary crap, perhaps it could be part of the restricted drivers group. I'd like to see a utility dedicated to the process of helping people install and configure their wireless drivers after installation, regardless of the open/proprietary status.

---

### Post by jml on 2007-05-15
My wireless still worked after the Edgy to Feisty upgrade.  I have a System 76 Darter and followed the instructions posted on the System 76 sub-forum.  Total upgrade took a bit over an hour, but everything still works.  (keeping fingers crossed.)

Joe

---

### Post by jonfenton on 2007-05-15
My main PC is a wired desktop and my experience with this has been great. I also have a laptop which I like to use with a wireless adapter but it has been a real struggle. It has been especially annoying to get my adapter working only for a new kernel to wipe out the effort.

I recently used my laptop to show Ubuntu to a friend. He seemed keen but I had to be honest and say that since wireless was important to him not to bother. Getting a connection painlessly to the internet is just one of those things that has to happen.

---

### Post by joe.turion64x2 on 2007-05-15
This is why at home I have a wired network (so I don't have to bother setting up security & Linux to recognize it) and can easily connect to open networks out there to get free internet when necessary.

---

### Post by cbrehm on 2007-05-17
I have an RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

and I cannot get wireless working on Feisty or anything.

It worked great in Edgy which I have installed now.

Has there been any progress on this?

---

### Post by bmartin on 2007-05-17
Try [these instructions]("http://ubuntuforums.org/showthread.php?t=241565&highlight=RT2500"). They assume you're using WPA. If you want other instructions, do a search for RT2500 on the forums; there are a lot of posts out there.

---

### Post by El Viejo Lobo on 2007-05-17
for Broadcom bcm4318  on Feisty  it works !!!

[http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb](http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb)

:guitar:

---

### Post by V. Wayne on 2007-05-17
I have a  Gateway MX6442 laptop (amd64) with Ubuntu 7.04 (x86_64) installed and the wireless connection works very well with the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02).  I enabled the roaming mode and presto!

Check out nickm's post on... Ubuntu Forums > The Ubuntu Forum Community  > Other Community Discussions  > Tutorials & Tips > How to: Broadcom Wireless cards... follow the instructions and you should have your wireless connection working.

---

### Post by Domie on 2007-05-18
> **c600g said:**
> I have had Dapper on an old Dell Inspiron 1100 laptop with a DLink DWL-650+ PCMCIA wireless card, and it worked flawlessly "out of the CD".

 I skipped Edgy but decided to try out Feisty, so downloaded and burned a live CD image. When I boot up the live CD, it detects the wireless adapter, and even displays my local wireless network as available with a connection strength somewhere around 50%.

 However, when I try to connect to it (using WEP), no connection is made.

 The DWL-650+ uses the acx100r11 chipset.

 Ideas?

Same problem, but with a "normal" PCI card

---

### Post by vgrisham on 2007-05-19
My Atheros 5212 based nic worked great in Dapper with no tweaking needed. It won't work at all in Feisty (and never would in Edgy either). I filed a bug report, and it seems to be languishing under the label of moderate importance. So, I bought a [Buffalo Ethernet Converter]("http://www.buffalotech.com/products/wireless/wireless-g-mimo-performance/wireless-g-mimo-performance-ethernet-converter/") which basically acts as a wireless server and allows me to plug the converted signal into my router's internet port. That has worked very well and has allowed me to avoid Ubuntu's Achilles' heel. It is frustrating that what works in one version of Ubuntu craps out in subsequent versions. I like Feisty very much, but one would think that a major aspect of today's computing, wireless, wouldn't be so blatantly neglected. I know, I know, blame the hardware manufacturers for not making Linux drivers. That mantra gets old, and is as pointless as whining to the refs in a lopsided basketball game. I wonder how many potential Windows converts have balked because of this issue? How many people are going to spend money in order to get buy hardware to get around an Ubuntu shortcoming? I'm sticking with Ubuntu regardless, but I'd sure like to see a day when hardware regression in new releases is deemed unacceptable.

---

### Post by statue on 2007-05-20
can't connect, i hope next release they focus on improving wireless support

---

### Post by gtfourdreams on 2007-05-20
[http://ubuntuforums.org/showthread.php?p=2692103](http://ubuntuforums.org/showthread.php?p=2692103)

if this would help anyone. this is how my setup was done.

---

### Post by KMW on 2007-05-21
Not working! After a week of playing with this there is still no network connection. Network help tool says my DWL 520+ should work out of the box in fact it states "just plan works", well it doesn't. Card is seen and can send but won't receive a thing.

Have posted twice in the network forum and as of yet not a single reply. And from all the reveiws and reccommendations that Ububtu was the easiest to use and set up, if this was the case then I'd hate to see the other distros!

---

### Post by doanut on 2007-05-21
Upgraded my laptop (ASUS f3jc) and wireless worked out of the box.

---

### Post by ChangBeer on 2007-05-21
I did a clean install and got my Linksys WPC11 v3 working after some tinkering:

When I booted from the live CD, networking worked fine. :)

After installing, system hangs up while booting if the wireless card is in.:(

Investigation showed installed version using hostap driver, while live CD used orinoco.:o

After blacklisting hostap_cs, wireless works using orinoco.:cool:

NOTE:  from what I have read, orinoco is not the correct driver for this card, should be hostap! WTF?:confused:

SECOND NOTE: The LInksys WPC11 v3 has been well supported in linux for several years now, Feisty is the first distro that I installed that had a problem with it.  Other than wireless, Feisty has been great though.;)

---

### Post by hoodwink on 2007-05-22
The poll numbers say it all. Very few users are having a good wireless experience with Feisty.

---

### Post by smdeep on 2007-05-22
Wireless worked on my Toshiba A80 laptop without problems. Can't say the same when I tried a Live cd on a desktop with a Netgear PCI card.

---

### Post by hodad on 2007-05-22
I have a six year old Dell laptop, and bought a D-Link Air 650  wireless card a few weeks ago.  Knowing that I'd have hardware problems as I always seem to when trying something new, I tried to research what would work.  There seemed to be good results from people using D-Link cards in general, so I got one.  As I expected, it wasn't recognized. Admin-Network on the desktop showed a modem connection, but not a network connection.  At the advice of a friend who uses Ubuntu, I upgraded to Feisty, but the wireless card still didn't work. I then found the Wireless section under Documentation, and got into that for a while, but the suggestions there didn't work either.  Looked into what cards worked with NDISWRAPPER, and several D-Link 650 cards were listed, but none of them was the "revision" I have.  Every time I try to follow someone's instructions, as well meaning as they are, it inevitably leads to a dead end, because the instructions given only work for a particular configuration, and/or have some aspect that isn't fully explained. Anyway, I'm giving it up for a while and just staying standalone.

I have never hooked up any piece of hardware without running into weeks of tribulation. I've found that If it doesn't work when I do a fresh install of Ubuntu, it simply won't work, and no amount of messing with the myriad drivers, etc, that are needed will make any difference.  I realize that this is a problem with me, more than with Ubuntu.  I really think that this is a great movement, and I wish it the best, but it's just to hard for me.  My next computer will have to be a Windows box or an Apple, because I need the computer to work for me rather than vice/versa.

Best of luck to you all!

---

### Post by wavz on 2007-05-22
Did a fresh install of Fiesty and blamo the wireless didnt work. Where as in Edgy it worked right away. Found through these forums that the drivers for my wireless card (Linksys WPC11 v4) had been blacklisted. So after unblacklisting the driver it recognized my card and with a few more tinkers it started to work, but it didnt work well. It would drop the signal every few seconds or so. So back to Edgy I went till there is a fix.

                                                                                                          Wavz

---

### Post by joylay83 on 2007-05-22
computer 1 = intel chipset wireless = worked flawlessly and fast

computer 2 = Ralink RT2500 :
don't know what i did last time, got it to work after hours of meddling. reinstalled 7.04 and didn't work again. will update when i manage to get it working.

---

### Post by thunderkyss on 2007-05-22
I voted that the wireless worked straight-away after a clean install. Truth is, I did have to do some thinkering to get it to work, but not on the Ubuntu end. I had MAC filtering enabled, and forgot about it.

Not only that, but I spent a few days trying to get DVDs & Mp3s to play( off topic I know) but after I figured out the wireless card thing, I reformatted, did a clean install(for other reasons) and DVDs & Mp3s worked almost automatically. I popped in a DVD, and Ubuntu told me it didn't have the codecs to make it work. Asked If I wanted to search for the right software, I said yes, and Ubuntu did the rest automatically. Same thing with Mp3s.

Internet, DVDs, & Mp3s..... that's about all I need. 

Now I can start doing something productive, like tweaking my desktop.

---

### Post by Enverex on 2007-05-22
> **alex77 said:**
> bump

Works fine on my Centrino (Intel) A/B/G Mini-PCIe card in my new laptop and the Seano (Atheros) A/B/G PCMCIA card in my old laptop.

---

### Post by JSThePatriot on 2007-05-22
Below are the links to a couple of solutions I found useful when installing the wireless on my machines.

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

I hope this helps someone,
JS

---

### Post by bmartin on 2007-05-22
(removed, wrong thread)

---

### Post by Pyrogenesis on 2007-05-22
Did a clean install, wifi not working, unable to make it work, giving up on Ubuntu. RaLink RT2500. There are several threads in this forum with people having problems with this card.

---

### Post by akobus on 2007-05-22
Using Intel 3945 card. Clean install - no problems.

---

### Post by JSThePatriot on 2007-05-22
> **bmartin said:**
> Dear JSThePatriot,

I hope you don't get an arrogant PM from the "owner" of this thread like I did; he whined about me "spamming links". If you do, here's the [link for ignoring]("http://ubuntuforums.org/profile.php?do=editlist") people like him.

I appreciate that, but the "owner" has failed to contact me.

Thanks again,
JS

---

### Post by alanmzifa on 2007-05-22
> **bmartin said:**
> Dear JSThePatriot,

I hope you don't get an arrogant PM from the "owner" of this thread like I did; he whined about me "spamming links". If you do, here's the [link for ignoring]("http://ubuntuforums.org/profile.php?do=editlist") people like him.


**bmartin**, I'm the instigator or "owner" of this thread. I haven't PM'd anyone on this thread, whining, arrogantly  or otherwise.

Please explain why you incorrectly said that I did. Perhaps you should also edit your erroneous/malicious post.

---

### Post by bmartin on 2007-05-22
Wrong thread. Sorry. I'm subscribed to a bunch of threads like this one.

---

### Post by misfitpierce on 2007-05-22
Anyone with broadcom wireless 4318 on 7.04 just hook ethernet cord in type this:
sudo apt-get update
sudo apt-get install bcm43xx-fwcutter and say yes when it asks if you want it to auto get firmware...

Afterwards you can go to /usr/lib/firmware or /lib/firmware/ and see the bcm files copy them all and save to disc and when you install ubuntu again ever just paste those there and itll work instant... Hope this helps some

---

### Post by dustigroove on 2007-05-22
[FONT=Arial][SIZE=2][COLOR=Black]7.04 on ThinkPad T60 with the Atheros based WLAN card.  Did not work straight out of the box with Feisty and enabling the restricted drivers through the RDM.  Ended up going with ndiswrapper and the Windows drivers provided by Lenovo.


This is my bump, and I'm sticking to it.

Cheers,

[/COLOR][/SIZE][/FONT]

---

### Post by jazzdaughter on 2007-05-22
After much searching of the web and elsewhere, I now have my wireless working, thanks very much to [this]("http://ubuntuforums.org/showthread.php?p=2703722#post2703722") how to.  It's magical!

---

### Post by vampyrebytes on 2007-05-23
Using an HP Pavilion zv5000 series (custom) with a Linksys WPC11 v4 PCMCIA card.
I don't recall exactly whether in Dapper and Edgy it was eth0 or ath0 or wlan0 but I have had it working "out of the box" since Dapper came out. I remember having to tweak an earlier installation (Breezy) heavily to get a lot of stuff working. Including something baout the PCMCIA slot.

Dapper and Edgy were both clean installs and the card worked without any tweaks.
Feisty doesn't see it at all... But I'm a "n00b" and don't know how to go behind the scenes and figure crap out for myself. I am technologically capable, if I could find a walk through.. but no one seems to know exactly what the problem is.

---

### Post by KMW on 2007-05-23
Only took 2 weeks but I finally got mine working. With a D-Link 520+ card. What a PITA!

Took the whole network apart, including Windows. Reset the router and the cable modem and removed Network Manager then reset in Network Tools.

Now I love Feisty!

---

### Post by oskarloko on 2007-05-23
I see that numbers are clear: wifi is a terrible hemorrhage on Ubuntu ( and Linux in general ).

That question isn't fair for Linux and Ubuntu in general, because wireless system is well developed ( kernel wireless, daemons, network manager ) and driver support is a enormeous effort ( developing free drivers offered, inversed reingeenirng, ndiswrapper ) covering any imaginable way  - except aiming a gun into hardware creator's CEOs. ;-)

But, world isn't fair - even for Linux - and we must deal with consequences of closed and locked soft/hard - figthing against them.

---

### Post by cdiem on 2007-05-23
I installed Ubuntu Feisty several minutes after it came out (considering the time to burn the disk). I still do not have a working wireless with ipw3945, and I'm still searching a solution for it. But, for the rest of the system, I'm in love with Ubuntu Feisty (especially the desktop effects, the power management - a long list going here), and I prefer it to any other system.

---

### Post by Enverex on 2007-05-23
> **cdiem said:**
> I installed Ubuntu Feisty several minutes after it came out (considering the time to burn the disk). I still do not have a working wireless with ipw3945, and I'm still searching a solution for it. But, for the rest of the system, I'm in love with Ubuntu Feisty (especially the desktop effects, the power management - a long list going here), and I prefer it to any other system.

IPW3945 works perfectly out of the box. What exactly is not working with it?

---

### Post by cdiem on 2007-05-23
Sorry if the post is too long, I'm not good at formatting posts.

In the network manager, I can see no wireless connection. I checked /sbin and /lib/firmware, the ipw3945 modules are there, 

lspci says: 
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

dmesg | grep -C 2 ipw says:
[ 4933.152000] ieee80211: 802.11 data/management/control stack, 1.2.17
[ 4933.152000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[ 4933.200000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[ 4933.200000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[ 4933.204000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[ 4933.204000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[ 4933.204000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[ 4935.144000] ipw3945: Radio Frequency Kill Switch is On:
[ 4935.144000] Kill switch must be turned off for wireless networking to work.

When checking my disk for mistakes (after it has been mounted N times), comes the following (which may be of use):
udevd[2626] PHYSDEVX values are deprecated and will be removed from a future kernel, please fix it in /etc/udev/rules.d/85-linux-wlan-ng.rules:1    (and also 2,3,4)

lsmod | grep ipw says:
ipw3945               118816  1 
ieee80211              50412  1 ipw3945

and lshw -C network says:
*-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@04:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:d4000000-d4000fff irq:16

Hope this is of use.

edited: I'm using an Fujitsu Siemens Amilo Pro v3505. In the BIOS I do not find a way to turn the radio frequency kill switch off; Fn+F2 doesn't do it either; Fn+F10(which seems to be the key for my wireless) doesn't do anything. I guess turning the radio frequency kill switch off would fix the problem, but I don't know how to do this. Any suggestions?

---

### Post by cdiem on 2007-05-23
I beg for your pardon for using this thread for solving my own problem; however, turning the rf_kill off seemed impossible. After trying 
sudo echo 0 > /sys/bus/pci/drivers/ipw3945/0000:04:00.0/rf_kill 
to turn it off, the terminal claimed, that I have no access: 
bash: /sys/bus/pci/drivers/ipw3945/0000:04:00.0/rf_kill: Permission denied
which sounded strange to me, since I access it via sudo (but, on the other hand, I'm pretty much a newbie, and there may be something I don't know about this).
So, after trying to turn the kill switch off via the big button for turning the wireless off at my Amilo Pro v3505, and then making the command: 
 dmesg | grep -C 2 ipw
it gave the following output:
[   19.016000] sky2 eth0: enabling interface
[   19.020000] sky2 eth0: ram buffer 0K
[   19.032000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   19.032000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   19.032000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   19.032000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   19.036000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   19.220000] NET: Registered protocol family 10
[   19.220000] lo: Disabled Privacy Extensions
--
[   20.688000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   20.688000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.064000] ipw3945: Radio Frequency Kill Switch is On:
[   21.064000] Kill switch must be turned off for wireless networking to work.
[   21.768000] NET: Registered protocol family 17
--
[ 1532.928000] atkbd.c: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0).
[ 1532.928000] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
[ 1796.796000] ipw3945: Error sending STATISTICS_CMD: time out after 500ms.
[ 1797.468000] ipw3945: Error sending STATISTICS_CMD: time out after 500ms.
[ 1819.612000] ipw3945: Error sending STATISTICS_CMD: time out after 500ms.
[ 1827.948000] atkbd.c: Unknown key released (translated set 2, code 0xe0 on isa0060/serio0).
[ 1827.948000] atkbd.c: Use 'setkeycodes e060 <keycode>' to make it known.
--
[ 3254.056000] atkbd.c: Unknown key released (translated set 2, code 0xe0 on isa0060/serio0).
[ 3254.056000] atkbd.c: Use 'setkeycodes e060 <keycode>' to make it known.
[ 3372.728000] ipw3945: Error sending STATISTICS_CMD: time out after 500ms.
[ 3373.396000] ipw3945: Error sending STATISTICS_CMD: time out after 500ms.
[ 3485.636000] atkbd.c: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0).
[ 3485.636000] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.

I guess, it just cannot recognize the button for the wireless. I guess, it has to be set via the 'setkeycodes' command. The problem is, I have no idea how. Does somebody know?

---

### Post by hessiess on 2007-05-23
it just will not work, [thred]("http://ubuntuforums.org/showthread.php?t=434944&highlight=bt+voyager")

---

### Post by chiarchiaru on 2007-05-23
Completely new Linux user. I hope my linux experience will not only last one week, the time I have spent so far to make my Cisco Aironet 350 card working with my T23 laptop under ubuntu 7.04. Still no way to let it work with WEP. It is working without encription though.

---

### Post by raul_ on 2007-05-23
I already gave up. Ralink's are a no-go, and they're the cheap ones

---

### Post by tonab on 2007-05-23
just installed feisty 7.04  , my pcmcia card is having all sorts of wireless issues
the same card worked out of the box on ubuntu 5.10 with minor network manager adjustments that is.

---

### Post by veebis on 2007-05-23
Nope. 
Worked perfectly in 6.10, vanished in 7.04.

Thinkpad T22, Linksys WPC11... Old school primitive, but fun when it worked.
Had to comment out the blacklist just to get Ubuntu to see the dang card.
Net Mgr asks all the right questions (WEP, etc.) but then ingnores the answers (apparently)... 

Any suggestions would be awesome!
-Vb

---

### Post by stchman on 2007-05-23
My Atheros card worked out of the box.  No problems.  Edgy I had to make the madwifi drivers.

---

### Post by cblanquer on 2007-05-23
I installed U7.04 on 4 PC with 4 different Wifi accesses:
[LIST]
[*]PCI ralink - OK after activating manually
[*]PCMCIA atheros - OK after activating manually, works with proprietary drivers
[*]USB ralink Conceptronic - KO, cannot get it working (i did in U6.10 installing serialmonkey RT73 driver)
[*]USB ralink D-Link DWL-G122 C1 - KO, cannot get it working (currently fighting!)
[/LIST]
=> in order to expand Linux use all this should be transparent ! Too much effort.
None of my relatives feels like installing and maintaining a Linux PC when base functionality requires such effort. 
Maybe when well known, public lists expose which are the WiFi cards working out of the box some of the companies issuing them will provide drivers or open access to their technical info. "ralink" is a key player.

---

### Post by veebis on 2007-05-23
Just got done posting/whining about my TP T22's inability to use Linksys WPC11 card for wireless with Feisty (worked great in Dapper)...

I'd already found a suggestion about commenting out a coupla blacklisted items ( /etc/modprobe.d/blacklist) for Feisty to even see the card:

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
[B]# blacklist r818x
# blacklist r8187[/B]

...That worked, but then Network Manager didn't seem to work.

Then I read someone's post suggesting **adding an "x" to the name of your wifi host, in Network Manager settings... i.e., "linksysx"**

...AND IT WORKED! I'm happy now, posting this from active WEP wireless connection.
Yay! Thanks, two handy guys...

For other lost souls using Search (like I did) on the forums, here's the data: 
Thinkpad T22  Linksys PCMCIA wireless card, model # WPC11  Feisty  7.04  Ubuntu

---

### Post by euchrid on 2007-05-24
I upgraded from 6.10, where my card worked fine. Now in 7.04, it doesn't even show up in Network Manager. I have a Realtek RTL-8185 pci card, which worked 'out of the box' in Edgy - and that is all the information I can find. This is appalling. Ubuntu has been so great, but I can't believe something as important as an internet connection can be killed in an upgrade! It's only because I am lucky enough to have another computer that I can even post this. 

Somewhere out there, there MUST be a solution by now - mustn't there? This has gone on too long!

---

### Post by euchrid on 2007-05-24
OK, for anyone else with a Realtek network card (RTL 8185 or 8187 particularly), I managed to get this to work by commenting out the line referring to 'rtl818x' in /etc/modprobe.d/blacklist, then rebooting (this allowed Network Manager to find the card); then, in Network Manager, I added an 'x' to the ESSID, and it worked! Bizarre, but at least I can get back on the internet and network.

[This post]("http://ubuntuforums.org/showthread.php?p=2711528"), which included [this link]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255") helped me out.

Maybe someone who can provide a more general solution should start a post where we can all post SOLUTIONS instead of problems - that's what many of us are here for! (Or should I just start one anyway? Are there no general solutions?)

---

### Post by zorog on 2007-05-24
RT 2500

6.0.6 :)
7.0.4 :(

nuff said.

---

### Post by ittiam on 2007-05-24
I was using Edgy then made a clean install of feisty. But I had to tinker more in feisty than in edgy. bcm4xx had to be blacklisted, also my AP uses WPA...i was able to connect to the AP but did not get any DHCP offers...if i switch to a network which doesnt require a network key...the AP automatically switches me to the secured network. But after fixing things in /etc/network/interfaces and recompiling ndiswrapper...i got it working.

---

### Post by pmenefee on 2007-05-24
This is really a disaster for Ubuntu.  Now granted, that's probably an overstatement, but with the number of users having serious problems and leaving the platform, I would call this serious.
It's a pretty interface, but I can't connect by wireless, so for the most part it's useless.  Using 7.04, and tried WICD to maybe help, but no luck.  I get connected once in a while after I change settings, and for no apparent reason.  Then it drops out.  Then won't work again with the same settings.
I have a dual boot system, and more and more I just boot up with XP and go.  I can get open office for Windows, and the thing works.  I'll sort of hang  around in the shadows till the next upgrade, but for the most part I'm very disappointed.  I was really excited to try the OS, but I'm not here as a hobbyist, or a cheerleader, I just want it to work.

---

### Post by Pyrogenesis on 2007-05-24
I find it especially ironic that the supported wireless faq starts with an explicit recommendation of Ralink 2500 cards. I suppose that was for v6. This is a major blunder - to fail to make a very popular and recommended card work in Feisty - and not just fail to make it work out of the box, but mess it up so bad that people are giving up trying to fix it.

---

### Post by Josh Kurtz on 2007-05-24
My atheros card was detected during install.  I had to enter in my WEP key and it configured properly with dhcp.  Once it loaded, I was online.  Every so often, when it wakes up, it's not connected to my LAN and I've got to manually disable then enable it to get it back to my access point.  I also can't seem to connect on other open systems.  I'm guessing that's because it's trying to use my WEP key.

Regardless, it works at home.  Plus, my little blue wireless light on my nc6000 comes on.  This didn't work on any previous release.

---

### Post by pmenefee on 2007-05-24
To give the OP an answer, as if there wasn't one already, as of right now there are 1146 pages of threads on the Networking and Wireless section of the Ubuntu forum.  Each one of those threads has one or two posts and some have many many more.  I doubt many of them say all is working well and thanks.  This must be an extremely difficult problem for Linux and/or Ubuntu.

---

### Post by DaveNZ on 2007-05-24
Dell Inspiron 1300. Problems with WPA.

Problem is actually Keyring Manager that keeps changing WPA password (default) no matter how many times you change it back. Obviously with the wrong password wireless stops working!

Solution, delete default keyring, activate your WPA networking (by using "connect to other wireless network") put in your WPA password and when Keyring Manager asks if it is OK for Network Manager to access Keyring Manager, say "deny".

Ever since wireless networking has worked perfectly! And no nagging by Keyring Manager every time you log on!

---

### Post by sk545 on 2007-05-24
didn't work with rt61.

---

### Post by jahrel on 2007-05-24
If wireless used to work with you in a previous version of Ubuntu, try booting with the kernel for this version. I solved my wireless problems for both of my computers (Feisty) booting the last kernel from Edgy.

---

### Post by itsjustarumour on 2007-05-25
Its a terrible thing to have to say, but I dual boot with Feisty and XP and I'm finding that more and more I'm having to boot into XP just to get things done, and Ubuntu/Feisty is becoming more of a side-show.  I've really wanted to make a success of Ubuntu, but I think this whole wireless thing has become the last straw.  It worked - for a while - in Edgy, and - for a while - in Feisty Beta4  (but at "b" not "g" speeds, and still only if I switched all encryption off). But now nothing. This is a real deal-breaker for me and so many others.  

I personally feel that the Ubuntu team have been much too slow to address these issues. Check out the [Ubuntu critical bugs list]("https://bugs.launchpad.net/ubuntu/+bugs?search=Search&field.importance=Critical&field.status=Unconfirmed&field.status=Confirmed&field.status=In+Progress&field.status=Needs+Info&field.status=Fix+Committed") and (not counting Bug #1 Microsoft has a majority market share) there are 26 critical bugs on there, only 4 of which show as "in progress " or "fix committed".  Two of those 26 bugs relate to wireless, and theres been no movement since Fiesty was released.  I assume the lack of progress is due to shortages in developer time/resources/money, and maybe I don't understand how their system works, but to a non-programmer like me that looks very poor.

So back to Ubuntu/XP - I've got a lot of positive things out of Ubuntu.  Its taught me a lot of useful things about *NIX-based OS's, its been a fantastic techology demonstrator, and I've generally had a lot of fun with it.  But would I use Ubuntu as my primary OS and trust my 15 years of data to it? Or put it on my laptop?  Not a cats chance in hell I'm afraid.

Oh dear - I started this post to make a comment about Feisty wireless, and realise that its turned into one of those dreadful "why I'm leaving Ubuntu" posts.  Apologies to all!  But I've put in a lot of effort over the last 8 months to file bugs reports, test software, email hardware manufacturers to provide Linux drivers etc etc all in the name of  "furthering the cause" of GNU/Linux/OSS, and I guess I'm just feeling a little let down by the Ubuntu team.

Well - PCLinuxOS has just relased their new version and I'll be giving that a try this afternoon to see if I get any more joy than I did with Feisty.  And if that doesn't work, I'll be putting Linux aside until the release of openSUSE 10.3 at the end of October.  I will of course be keeping a close eye on Ubuntu developments from the wings, but only as an interested observer.  I can't help wondering how many others are in the same position.  I suppose if the worst comes to the worst, I can at least console myself that all my favourite programs - Firefox, Thunderbird, Pidgin, OpenOffice and Abiword are all available for Windows...

---

### Post by CrispyFried on 2007-05-25
took a while (linux noob here) but with ndiswrapper and the stock windows driver I got my Compaq M2010 notebook with built in Broadcom BCM4306 to work on a Fiesty 7.04 clean install (dual boot with XP).

---

### Post by videodrome on 2007-05-25
I *specifically* purchased an RT2500 card because it worked perfectly out of the box with Edgy.

Now the same card no longer works. Way to go Ubuntu!

---

### Post by Old *ix Geek on 2007-05-25
I have to change my vote.  Initially, I did a clean install of Feisty on a new HP laptop (that, of course, came with 'doze preinstalled on it), and could not get wireless working at all.  After a couple days of trying I gave up and put Edgy on it.  Then I had wireless, but it was very slow.  After much poking around the forums I was directed to instructions for ndiswrapper that I hadn't seen before and, upon following them, had a blazingly fast connection.  A few days later I decided I would now re-try Feisty and see if I could make it work--and I did!  So although my vote was tallied as 'never got it working,' I now *DO* have wireless working on Feisty and it's nice. :p

---

### Post by madmetal on 2007-05-25
I did a clean 7.04 install, wireless worked straight away

i have a compaq armada e500 with a linksys WPC54G pcmcia card..
just installed the linux chipset driver and it works!
with WEP and WPA  ;)

---

### Post by ppietryga on 2007-05-25
I did a clean install of 7.04 and I checked 2 answers:
**_[COLOR="Lime"]My wireless works out of the box with some networks[/COLOR]_**
and
[B][U][COLOR="Red"]I can't get it to work with other networks.
[/COLOR][/U][/B]
After some research I have found, that if there is a "wireless isolation" turned on on Access Point, then my card works until it receives an IP.
I use kubuntu, and when I connect to "wireless isolation enabled" network, the progress bar stops at 29%. There is no access to network.
I have:
```

02:03.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

```
I didn't spend a lot of time trying to resolve the problem, but that's the second thing, that makes me keep my Windows XP on HDD.

---

### Post by Kourosism on 2007-05-26
I can't get WiFi to work on Feisty LiveCD on a Advent 7113. I've posted this a few times elsewhere, but I'm not spamming - just trying to find a solution. I've had a read around, and cannot seem to find a workable solution - I'd like to get the connection working on the LiveCD before installing, as I can then be certain it will work, without spending too much time on it - is this even possible?

My original post:-


I've been playing around with Ubuntu for a year or so, and I finally got around to purchasing a laptop to install it onto. I loaded the LiveCD first, as I wanted to make sure everything appeared to work, and on the whole it did, except I am having the following issue.

Ubuntu can see my wireless LAN - but it refuses to connect to it. It simply sits there attempting to connect, but does not. I have tried it without security, and with 64bit WEP, but still no joy. Any hints? I don't really want to go "whole hog" if I can't get Wifi to work - the main reason for having a lappy these days.

The laptop is an Advent 7113. I believe it uses an inbuilt MSI 6877 WLAN card.

---

### Post by ajlewis2 on 2007-05-26
> **Kourosism said:**
> 
The laptop is an Advent 7113. I believe it uses an inbuilt MSI 6877 WLAN card.

While in the LiveCD open a terminal.  Run 

lspci

Identify the line about your wireless card.  This is exactly what the chip is.  From there it can be found if this chip is supported either by a kernel module, a restricted module, or ndiswrapper.

Anita

---

### Post by Enverex on 2007-05-26
> **ppietryga said:**
> I did a clean install of 7.04 and I checked 2 answers:
**_[COLOR="Lime"]My wireless works out of the box with some networks[/COLOR]_**
and
[B][U][COLOR="Red"]I can't get it to work with other networks.
[/COLOR][/U][/B]
After some research I have found, that if there is a "wireless isolation" turned on on Access Point, then my card works until it receives an IP.
I use kubuntu, and when I connect to "wireless isolation enabled" network, the progress bar stops at 29%. There is no access to network.
I have:
```

02:03.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

```
I didn't spend a lot of time trying to resolve the problem, but that's the second thing, that makes me keep my Windows XP on HDD.

I have that same machine in my desktop now and lsmod shows that there isn't even a driver loaded for it... that's not a good start :(

---

### Post by Kourosism on 2007-05-26
> **ajlewis2 said:**
> While in the LiveCD open a terminal.  Run 

lspci

Identify the line about your wireless card.  This is exactly what the chip is.  From there it can be found if this chip is supported either by a kernel module, a restricted module, or ndiswrapper.

Anita

Hi Anita,

The only network device that seems to show is

```
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd RTL-8139/8139C/8139C+ (rev 10)
```

Maybe I'm just being a dumdum, I dunno. While Ubuntu can see wireless networks, and their strength, when connected it only gets 0%.

---

### Post by Enverex on 2007-05-26
> **Kourosism said:**
> Hi Anita,

The only network device that seems to show is

```
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd RTL-8139/8139C/8139C+ (rev 10)
```

Maybe I'm just being a dumdum, I dunno. While Ubuntu can see wireless networks, and their strength, when connected it only gets 0%.

That's not Wireless, that's the wired network adapter.

---

### Post by Kourosism on 2007-05-26
> **Enverex said:**
> That's not Wireless, that's the wired network adapter.

Sorry, yes I know that - I should have made my last post clearer, and left that out entirely. This is the only network device which shows - no wireless shows at all, which is particularly odd as Ubuntu can see the local networks - it simply will not connect to them (or gets 0% strength).

---

### Post by ppietryga on 2007-05-26
> **Me]
I use kubuntu, and when I connect to "wireless isolation enabled" network, the progress bar stops at 29%. There is no access to network.
I have:
```

lspci
...
02:03.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

```
[QUOTE=Enverex said:**
> I have that same machine in my desktop now and lsmod shows that there isn't even a driver loaded for it... that's not a good start :(
[/QUOTE]

Well, on my side, the module is loaded. The problem is not about the hardware, becouse it works in nearly all circumstances. Ii doesn't work when Wireless/AP isolation is enabled on Access Point. It does however when running windows.
```

lsmod |grep rt2500
rt2500                179044  1

```

What I know about this wireless isolation is that it creates a vlan (virtual lan) for every client, so the wireless clients can't connect to each other directly.
Unfortunately in my University the APs are wireless isolation enabled, and I can't access the network using Ubuntu.

---

### Post by kwame on 2007-05-26
Using a Satellite A135 S2266. Tried as I could, was never able to get wireless working under Dapper or Edgy.  Did a clean install of Feisty and everything's just breezing along.

---

### Post by Enverex on 2007-05-26
> **ppietryga said:**
> Well, on my side, the module is loaded. The problem is not about the hardware, becouse it works in nearly all circumstances. Ii doesn't work when Wireless/AP isolation is enabled on Access Point. It does however when running windows.
```

lsmod |grep rt2500
rt2500                179044  1

```

What I know about this wireless isolation is that it creates a vlan (virtual lan) for every client, so the wireless clients can't connect to each other directly.
Unfortunately in my University the APs are wireless isolation enabled, and I can't access the network using Ubuntu.

root@Xenith:/# lsmod | grep 2500
root@Xenith:/# modprobe rt2500
FATAL: Module rt2500 not found.

---

### Post by newhope16 on 2007-05-26
i useing wmp54g linksys to no avail..

---

### Post by AndyCinDallas on 2007-05-26
Acer Travelmate 2500 with a CardBus D-Link Airplus DWL-G650. Worked out of the box with 7.04 Feisty.

---

### Post by msak007 on 2007-05-26
> **newhope16 said:**
> i useing wmp54g linksys to no avail..
I've got a WMP54GS and it's always worked in the past with ndiswrapper. As of Feisty, it connects but the signal strength is cut in half.

---

### Post by ppietryga on 2007-05-26
@Enverex:
I don't know why the module isn't loading.
I've been using this RaLink rt2500 since Breezy Badger and the problem appeared when the University changed old Access Points to new ones with AP isolation enabled.
I can't help You.
Did you try these steps?
```

sudo aptitude install rt2500 rt2500-source
sudo module-assistant auto-install rt2500-source
modprobe rt2500

```
I didn't need them, so I didn't try them, but I found these steps on Polish UbuntuForum.

---

### Post by Enverex on 2007-05-26
Fails to build, probably why it wasn't in the kernel by default *sighs*

```
touch config.mk \
                && /usr/bin/make clean
make[1]: Entering directory `/usr/src/modules/rt2500'
make[1]: Leaving directory `/usr/src/modules/rt2500'
dh_clean
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/rt2500'
touch config.mk \
                && /usr/bin/make clean
make[2]: Entering directory `/usr/src/modules/rt2500'
make[2]: Leaving directory `/usr/src/modules/rt2500'
dh_clean
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.22-5-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.22-5-generic/g ;s/#KVERS#/2.6.22-5-generic/g ; s/_KVERS_/2.6.22-5-generic/g ; s/##KDREV##/2.6.22-5.11/g ; s/#KDREV#/2.6.22-5.11/$
  done
# Install module
dh_installdirs lib/modules/2.6.22-5-generic/kernel/drivers/net/wireless
# Build modules
/usr/bin/make KERNDIR=/usr/src/linux PATCHLEVEL=6
make[2]: Entering directory `/usr/src/modules/rt2500'
make[3]: Entering directory `/usr/src/linux-headers-2.6.22-5-generic'
  CC [M]  /usr/src/modules/rt2500/rtmp_main.o
In file included from /usr/src/modules/rt2500/rtmp_main.c:50:
/usr/src/modules/rt2500/rt_config.h:58:40: error: linux/config.h: No such file or directory
/usr/src/modules/rt2500/rtmp_main.c: In function &#8216;RT2500_open&#8217;:
/usr/src/modules/rt2500/rtmp_main.c:272: warning: &#8216;deprecated_irq_flag&#8217; is deprecated (declared at include/linux/interrupt.h:66)
/usr/src/modules/rt2500/rtmp_main.c:272: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/usr/src/modules/rt2500/rtmp_main.c: In function &#8216;rt2500_init_module&#8217;:
/usr/src/modules/rt2500/rtmp_main.c:940: warning: implicit declaration of function &#8216;pci_module_init&#8217;
make[4]: *** [/usr/src/modules/rt2500/rtmp_main.o] Error 1
make[3]: *** [_module_/usr/src/modules/rt2500] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.22-5-generic'
rt2500.ko failed to build!
make[2]: *** [module] Error 1
make[2]: Leaving directory `/usr/src/modules/rt2500'
make[1]: *** [binary_modules] Error 2
make[1]: Leaving directory `/usr/src/modules/rt2500'
make: *** [kdist_build] Error 2
```

---

### Post by Jo0Lz on 2007-05-27
Grrr. This restricted wireless thing is really bugging me out!

I've tried several solutions on these forums, but no go. I can 't even see the card to change it's options.
The card is however installed with the restricted drivers...

I have a new Amilo Pro V8210 Notebook, Suse 10.2 and Windows both supported the Wifi out of the box, altough it was buggy on Suse.

Now, on Ubuntu (7.04) the video didn't work, until I did some tinkering, the wifi isn't working at all, and i had to hack some files by hand to get sound to work.

Can someone enlighten me with some magic link that has the solution? :')

I've got the Intel Wireless 3945 Pro driver, but it's "restricted". It's in use though, but doesn't show in the networking tools.

HELP PLEASE?!

---

### Post by Go99an on 2007-05-27
Like Jo0lz, I also tried SuSE10.2 before (K)ubuntu and WiFi worked OK, but it trashed itself when I tried to install Beryl!!

Was recommended to try Kubuntu and now can't connect with Wifi

I desperately want to kick M$ into touch on the other two laptops in our household, but until I can get a reliable functional system I can only experiment on one. I have'nt even started with the other Linux Gotcha...... Printers!!!

I have the intel/Pro Wireless 2100 3B on a Dell Latitude D600.

If anyone can guide me to fix this, I would be most grateful, till then I will keep reading the help forums,

Regards,
Go99an.

---

### Post by Jo0Lz on 2007-05-27
> **Go99an said:**
> Like Jo0lz, I also tried SuSE10.2 before (K)ubuntu and WiFi worked OK, but it trashed itself when I tried to install Beryl!!

Was recommended to try Kubuntu and now can't connect with Wifi

I desperately want to kick M$ into touch on the other two laptops in our household, but until I can get a reliable functional system I can only experiment on one. I have'nt even started with the other Linux Gotcha...... Printers!!!

I have the intel/Pro Wireless 2100 3B on a Dell Latitude D600.

If anyone can guide me to fix this, I would be most grateful, till then I will keep reading the help forums,

Regards,
Go99an.

I've read several guides on how to fix the problem with the wireless, but I can't get it to work.
Hell, I can't even make the thing show up as active, so I can try to connect, let alone configure it.

someone must have the same laptop or card and got it to work right?

---

### Post by Jo0Lz on 2007-05-27
> **Jo0Lz said:**
> I've read several guides on how to fix the problem with the wireless, but I can't get it to work.
Hell, I can't even make the thing show up as active, so I can try to connect, let alone configure it.

someone must have the same laptop or card and got it to work right?
Oke, I just found out the card was installed, but not enabled. No way for me to enable it in ubuntu, so I rebooted into windows and turned it on, that was all I needed, I'm posting this on my laptop, wireless.

The strange thing is, that the bios setup of the laptop had the option to turn it on by default, so I don't get why it did not do that.

Works like a charm now, I think everything does :D.

---

### Post by didobuntu on 2007-05-27
Hello, 

I did a fresh install on my laptop (Feisty 7.04). Wired internet works, but wireless do not work (it worked fine under Edgy 6.10).

I have a Netgear WG511 v2 card. I installed the windows 2000 drived via the ndiswrapper 1.9 from repos.

The more problematic is when I try to get a wifi connection ... my ubuntu freezes ... :(

I need another fresh install .. but without solution for the netgear wg511 v2 card, I will have the same problem.

---

### Post by jmcwb on 2007-05-27
I have a netgear wg511v1 card and could never get it to work using the prism54 driver or the ndiswrapper under Feisty 7.04.  It worked fine with the previous 6.10 version.  So, for now I installed PCLinuxOS 2007 and it works just fine with the ndiswrapper and the windows inf file.  From the looks of it, I'll try 7.10 when it comes out and see if the card works then.  I prefer ubuntu to any other distribution since I've used it the longest.

:o

---

### Post by sanbysan on 2007-05-27
Toshiba M55 S331 working fine :)

---

### Post by ppietryga on 2007-05-27
> **Enverex said:**
> Fails to build, probably why it wasn't in the kernel by default *sighs*


Tried for myself and it doesn't build either. Will ask the one who wrote those on Polish Forum.

---

### Post by ugm6hr on 2007-05-27
Got my Acer Aspire 5050/5051 laptop wireless to work from the second minute of installing.  Just ticked a box that popped up on installing to enable the Atheros Restricted Driver for my Atheros5005G card, and I was connected.  Only problem is Network Manager and the Atheros driver seem to cause intermittent dropped connections with WPA.

---

### Post by valkyrie on 2007-05-28
RaLink 2500 chipset is supposed to work with Linux and it did in 6.06... now suddenly in 7.04, nothin'!

---

### Post by Enverex on 2007-05-28
> **valkyrie said:**
> RaLink 2500 chipset is supposed to work with Linux and it did in 6.06... now suddenly in 7.04, nothin'!

It doesn't seem to compile against kernels .21 and up which is also not going to help matters.

---

### Post by epee on 2007-05-28
GRRRR!!!!

Ran the auto-update got some kernel updates and now my USB/Wifi isn't recognised at all!

Someone must have broken the wireless networking again!

I'm just about ready to sell out to Microsoft - I've had Ubuntu about 4 weeks or so but Ihave yet to have a month unfettered use - it took me 2 weeks of endless try-and-error to get the wireless working as it was!

I'm so p*ssed off!!!

---

### Post by Kourosism on 2007-05-28
Still having no joy, Ran lshw, and get the following:-

```
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:08:12:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

However, iwconfig brings up the following:-

```
lo        no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

I'm frankly feeling like I'm beating my head against a brick wall here. I've dug around on the 'net, and anything I have tried to follow is still failing to succeed. Can I provide anymore info, even if it just means that someone can tell me why it isn't working... that would suffice now! I'd love to actually get it to work, but if it can't, it can't. But at least I should know whether to stop trying!

---

### Post by Collywobbles on 2007-05-29
Hi all,

I've just discovered Ubuntu (v7.04). I've installed various flavours of Linux before but always ended up removing them as I can't get stuff to work. The Ubuntu...It Just Works...has tempted me back.

Unfortunately, I cannot get my wireless connection to work. I have D-Link DWL-G650+ wireless PMCIA card in my Dell Latitude laptop. I'm trying to connect to a D-Link DSL-G604T wireless router. It didn't work at all out of the box, but then I followed some guides and managed to get it to detect the G650+ card. Ubuntu can even see the G604T router now as it appears in the Wireless Networks listing. However, it still refuses to connect. I have no idea what else to try.

I may install Ubuntu (v6.06) before giving up on Linux again :(

Collywobbles

---

### Post by itsjustarumour on 2007-05-29
> **epee said:**
> GRRRR!!!!

Ran the auto-update got some kernel updates and now my USB/Wifi isn't recognised at all!

Someone must have broken the wireless networking again!

I'm just about ready to sell out to Microsoft - I've had Ubuntu about 4 weeks or so but Ihave yet to have a month unfettered use - it took me 2 weeks of endless try-and-error to get the wireless working as it was!

I'm so p*ssed off!!!

My wireless wasn't working at all, but at least Feisty had detected my Broadcom 4318-based  USR5417 MAXg card. Now since yesterdays kernel updates - absolutely nothing!!!!!! ](*,)

---

### Post by ivesjd on 2007-05-29
Wireless worked on my 1st gen macbook out of the box. But on my dekstop (stupid college only has wireless) Ive still got nothing.

---

### Post by useResa on 2007-05-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/117580](https://bugs.launchpad.net/ubuntu/+bug/117580) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				> **itsjustarumour said:**
> Now since yesterdays kernel updates - absolutely nothing!!!!!! ](*,)I encountered the same issue.
It could be worthwhile to report your issue in the above mentioned bug I found.

---

### Post by regebro on 2007-05-29
I tried with a D-Link DWL-G510 Rev C2. This is supposed to work out of the box, but didn't. It looked like it works OK, except that the link quality typically shows up as 0 except for one network, but I couldn't connect, with or without security. No amount of trobleshooting, configuration, alternative drivers and recompilation of things made any kind of difference.

One of the big problems is D-Links habit of issuing completely different and incompatible cards with only revision numbers differing. C1 and C2 doesn't use the same chipsets and should have different drivers. The net abounds with people asking for help and getting it, and rarely do you know exactly what card they have, and never ever is the solution the same. It seems that pretty much everbody that tries D-link cards have problems, and they are never the same problem or the same resolution, Conclusion: Stay away from D-link cards for dear life!

Today I gave up (after two days of trying) and bought a Netgear WPN311. Worked directly straight out of the box. Plug'n play!

One step closer to having mu Ubuntu Multimedia Home Theater PC! :popcorn:
(You can follow the exploits on my blog [http://regebro.wordpress.com/](http://regebro.wordpress.com/) )

---

### Post by vv88 on 2007-05-29
Hey, just thought I'd add my 2 cents...

WPC11 V.4 was working with Feisty and Ndiswrapper, however, the connection was pretty bad so I purchased a DI-624 and DWL-G650.  A definite upgrade considering I wanted to stream video and the router/new card provided the boost/connection I needed.

About the DI-624 and DWL-G650

After scouring this site for quite awhile, I found success with [wicd]("http://wicd.sourceforge.net/").  WPA and MAC filtering work fine.  BUT, I still cannot get the card to pick up my hidden SSID (when enabled).

EDIT: Sorry about the model # errors ;)

---

### Post by bgissal on 2007-05-29
I have been able to configure my wireless internet with Feisty to the point where Network Manager sees the wireless network, but it cannot connect upon startup. 

I have to grab a terminal and type the command everytime I want to connect to the wireless router:
sudo iwconfig wlan0 essid asdf 

Is there any way to get this command to go through automatically at startup????

---

### Post by elehayyme on 2007-05-29
> **itsjustarumour said:**
> My wireless wasn't working at all, but at least Feisty had detected my Broadcom 4318-based  USR5417 MAXg card. Now since yesterdays kernel updates - absolutely nothing!!!!!! ](*,)

I'm feeling your pain.  Earlier I was able to connect to the 'net, etc upon booting up.  Since the kernel update, I can't connect at all. It seems like it recognizes my card (adapter).  We thought of rebuilding things but since we can't connect to the 'net, that's really difficult. ](*,)

My laptop is fine but my main system seems to be pooched and I'm about to give up on Ubuntu.

---

### Post by deadowl on 2007-05-29
1. Wireless worked after some tinkering.
2. Can't get wireless to work after kernel update.

---

### Post by topikal on 2007-05-30
> **bgissal said:**
> I have been able to configure my wireless internet with Feisty to the point where Network Manager sees the wireless network, but it cannot connect upon startup. 

I have to grab a terminal and type the command everytime I want to connect to the wireless router:
sudo iwconfig wlan0 essid asdf 

Is there any way to get this command to go through automatically at startup????

Go to System > Preferences > Sessions.

Then just add an entry with that command line. It will automatically perform the terminal command upon startup without popping anything up.

---

### Post by aldomontoya on 2007-05-30
I used this guide:

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

takes 2 minutes and worked perfectly, the only thing that got WPA to work proerly for me. Feisty 7.04 btw.

---

### Post by unisol on 2007-05-30
i tried your method and it locks up my screen. any clues why? i have rt61 wireless pci cards.

---

### Post by Handssolow on 2007-05-30
Returning from holiday I'd hoped on my return that more progress would had been made so as to enable  my PC running FF with a RT2500 PCI card to connect automatically without me having to manually input my essid and WEP key every time I switch on. No chance. Earlier I came to the conclusion that the FF developers assumed everybody would be using WPA so this left the WEP folk floundering (and swearing at ...??). Faith in Ubuntu has undoubtedly been shaken.

What do I do with my wife's PC that's still on EE but working without a hitch?  Why upgrade her to FF?

My current view is that If I moved over to WPA then things might be better but that involves a certain trust of the unknown, lots of work and my time working on three PCs and four OS at this house which use our WLAN.

Shouldn't they have told us that if you have a  RT2500 card FF works well  but only if you use WPA not WEP?

Anyone out there using RT2500 and WEP without a hitch please reply.

---

### Post by lerch527 on 2007-05-30
> **itsjustarumour said:**
> My wireless wasn't working at all, but at least Feisty had detected my Broadcom 4318-based  USR5417 MAXg card. Now since yesterdays kernel updates - absolutely nothing!!!!!! ](*,)

try this( showthread.php?t=197102&highlight=4318)in ubuntuforums. i'm fairy new myself but i've used this several time on new install of last couple versons of ubuntu the 43xx and wrapper methods both work for fiesty. all i do is fresh install pluss complete updates +wifi-radar then use instrutons on thread good luck

---

### Post by form51 on 2007-05-30
I just bought a Lenovo V100 laptop.  Installed 6.10 from a DVD and wireless was not working.  I didn't even fool around with trying to fix it.  I upgraded to 7.04 via synaptic and Feisty recognized and was using a restricted intel driver right away... works flawlessly (for once).

---

### Post by usernamed on 2007-05-30
Thought I'd be brave and just make the switch from XP back to Ubuntu.  I'm already remembering why I went back to XP from Edgy.  I'm typing this from my hp nx6125 where I currently have wireless, but in 10 minutes I probably won't (despite being 10 foot from the wireless router)

I keep losing connection and not getting it back without rebooting followed by a disable/enable of the interface then a /etc/init.d/networking restart.  The hardware's fine.  It was working at full strength with WinXP.

I got ths far after I waded through enough documentation to figure out wpa_supplicant and how to get the broadcom 43xx driver working.   My PDA can do WPA without any hassle, but Ubuntu can't integrate WPA into its network manager?

My desire to use Ubuntu doesn't come from some love of technology for technology's sake, I just don't want to keep feeding the monster that is Microsoft.  This stuff needs to work out of the box.  With all the heavyweights behind Linux (HP, IBM etc) why can't pressure be put on companies like Broadcom to modify their licensing so their customers aren't penalised for choosing non-Microsoft?

Ubuntu is as far away from being an out of the box solution now as it was two years ago from my perspective as an end user, and the problems now seem to be legal/political (availability of drivers/firmware licensing for example) as much as technical.  I'm disappointed, I was expecting real progress.

---

### Post by moron on 2007-05-30
> **Handssolow said:**
> Earlier I came to the conclusion that the FF developers assumed everybody would be using WPA so this left the WEP folk floundering (and swearing at ...??). Faith in Ubuntu has undoubtedly been shaken.

Handssolow, WEP is pretty much equivalent to using no encryption at all.  As in crackable in 45 to 30 seconds (or less with a newer computer).  It is dangerous for you to use it.  Do you use encrypted POP connections when checking email?  How about encrypted HTTPS connections to every single website you log into?  Do you re-use passwords at all?  Do you share files at all locally on your LAN?  Do you want to share your net connection with any random person who feels like using it?  How secure is your router - is the password easily guessable (since they will be able to log and try a bruteforce attack in under a minute)?  Etc., etc. 

WEP is deader than dead, don't use it.

Also, keep in mind that Ubuntu is a distribution, the vast majority of code in Ubuntu is not written by anyone to do with Ubuntu.  The only stuff that is going to be purely Ubuntu are setup scripts and then some custom applications.  

I feel your wireless pain, I have my own issues with the madwifi drivers at the moment but your faith in Ubuntu should be based on the fact that you have good community support and an overall distro that works pretty well not on whether a specific hardware driver (which for wireless cards vendors have in general proven to be obnoxiously hard to get decent docs from) works flawlessly for you.  Also note that the vast majority of the code driving your system has been written by selfless volunteers.  

Hardwired ethernet cards tend to be a million times more reliable so perhaps your solution is to go with a wireless bridge?

Cheers

---

### Post by DougB1958 on 2007-05-30
Well, I upgraded from 6.10 and took some tinkering to get wireless working, but it does finally work.

I have a LinkSys WMP54G wireless card with an RaLink RT61 chip set, talking to a LinkSys router with WPA. The key to making this work under 7.04 for me was the discussion at [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=21546&sid=c5e02ed97dde07681fb564639e9f50c5]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=21546&sid=c5e02ed97dde07681fb564639e9f50c5"). This page talks about making RT61 drivers work for a different Linux distribution (Fedora Core 6), but it provides a series of "iwpriv" and "iwconfig" commands that work just fine to make Ubuntu's RT61 driver talk WPA to my router.

Once I'd verified that the commands do the trick, I put them in a shell script and made it run as a "pre-up" command for my wireless interface in "/etc/network/interfaces" (I threw out network-manager), and now the wireless interface connects automatically whenever I start my computer.

---

### Post by joe.turion64x2 on 2007-05-30
My wireless worked out of the box with Ubuntu 7.04 (only needed to accept the restricted drivers), however today I noticed that it works better in Fedora Core 6: a little more range and it can connect to more wireless networks.

---

### Post by sugoihito on 2007-05-31
I'm running a bcm4318 on a Compaq under feisty.
I tried soo much... no luck.

---

### Post by mikledet on 2007-05-31
I don't know if anyone noticed this before, but to me this poll seems a little misleading (or mistitled), since it is posted in a forum where around 90%-95% of the people here are here since they have a problem with their network...  :rolleyes:
While keeping that in mind, the poll is still interesting.

---

### Post by obavjestenja on 2007-05-31
my wireless work on xp,vista but on feisty no luck.
can you help guys but on simply it ubuntu language:)
[[IMG]http://img363.imageshack.us/img363/8633/screenshot3zv0.th.png[/IMG]](http://img363.imageshack.us/my.php?image=screenshot3zv0.png)

---

### Post by xtriqiq on 2007-05-31
I'm using Kubuntu.
After upgrading from 6.10 to 7.04, my wireless didn't work that well. My PC was just turned on and off after a few minutes. So I had to reboot it several times a day just to ensure that I could connect to Internet. :( .

But a week ago I decided to remove WifiRadar and Wireless Assistant and replace it with KWifiManager which is available but not by default. Since that then my wireless connection becomes better. The bad thing is that I can't even open KWifiManager since it will disconnect my working connection. But that would be Ok for me since I don't need it at all. Maybe you guys can try it out. you will lose nothing anyway...

---

### Post by cdiem on 2007-05-31
Although I voted that the wireless doesn't work, and I stated this opinion here, after tweaking (you can find it in the thread [http://ubuntuforums.org/showthread.php?p=2753972#post2753972](http://ubuntuforums.org/showthread.php?p=2753972#post2753972) ), I managed to turn the kill switch   OFF on my Amilo pro v3505. So, if i had the chance to vote again, I would vote, that after a bit of tweaking, the wireless would work (I still cannot believe, that with 2 simple commands I have empowered mine, thanks to "goranpop", after searching for some time how to do this).

---

### Post by Handssolow on 2007-05-31
> **moron said:**
> Handssolow, WEP is pretty much equivalent to using no encryption at all.  As in crackable in 45 to 30 seconds (or less with a newer computer).  It is dangerous for you to use it.  Do you use encrypted POP connections when checking email?  How about encrypted HTTPS connections to every single website you log into?  Do you re-use passwords at all?  Do you share files at all locally on your LAN?  Do you want to share your net connection with any random person who feels like using it?  How secure is your router - is the password easily guessable (since they will be able to log and try a bruteforce attack in under a minute)?  Etc., etc. 

WEP is deader than dead, don't use it.

Also, keep in mind that Ubuntu is a distribution, the vast majority of code in Ubuntu is not written by anyone to do with Ubuntu.  The only stuff that is going to be purely Ubuntu are setup scripts and then some custom applications.  

I feel your wireless pain, I have my own issues with the madwifi drivers at the moment but your faith in Ubuntu should be based on the fact that you have good community support and an overall distro that works pretty well not on whether a specific hardware driver (which for wireless cards vendors have in general proven to be obnoxiously hard to get decent docs from) works flawlessly for you.  Also note that the vast majority of the code driving your system has been written by selfless volunteers.  

Hardwired ethernet cards tend to be a million times more reliable so perhaps your solution is to go with a wireless bridge?

Cheers

Thanks moron for your comments. I know that I need to ditch our use of WEP but for the moment I've sited our wireless router low down on the ground floor. Fortunately we haven't got close neighbours and WiFi Radar currently only shows our WLAN though it has detected a new neighbour's recently.

Perhaps I should install a wired connection to my router from at least one of our PCs where it would be easy.

---

### Post by unisol on 2007-05-31
i have feisty with a rt61(linksys WMP54G with rangebooster) when i login to the desktop and go to NetworkManager, i try yo select my home network and my desktop freezes. my card is recognised, and winxp has no problem working with  the wireless network.

---

### Post by LazerTag on 2007-05-31
*bump*

I updated from 6.10, can't get wireless to work


Was working just fine before upgrading.

Dell 4100 laptop using a Netgear MA510 PCMCIA card.

---

### Post by steeleyuk on 2007-05-31
Netgear WG311v2 works as long as Network Manager is not installed.

Worked fine in Edgy as well.

---

### Post by stoian on 2007-05-31
wifi worked for me and others in Dapper and Feisty until a few days ago: please bump these:

[http://digg.com/linux_unix/Ubuntu_devs_for_God_s_sake_please_fix_the_wireless_problem](http://digg.com/linux_unix/Ubuntu_devs_for_God_s_sake_please_fix_the_wireless_problem)
[http://ubuntuforums.org/showthread.php?t=459665](http://ubuntuforums.org/showthread.php?t=459665)

i hope somebody will fix this mess in ubuntu...

---

### Post by ppietryga on 2007-06-01
> **Enverex said:**
> It doesn't seem to compile against kernels .21 and up which is also not going to help matters.
Hi,
had been away for some time.
I can't compile it either, and didn't receive any help with it.
But are You sure your card is ok? Maybe it's broken?

I've have had some experience with rt2500 on another computers and it has always worked like a charm (I had more trouble with it under Windows then with linux).
It always worked even from LiveCD. :o

And if Any of You have a problem with a wireless not working, the issue may be with an AP (or wireless) isolation enabled on Access Point. To resolve this I did just this :D:
```
sudo modprobe 8021q
```
And sometimes **this** can help You :)
```

sudo vconfig add ra0 <vlan #>

```
before setting the interface up.

PS. By the way: does anyone know, how Windows XP know which vlan_id it needs? I use my computer in many different networks and I need to run the vconfig command very often. Under windows I don't need to. Well I don't even know how could I set it up manually. :confused:

PS2. There's only one more thing, that keeps my Windows on HDD. I need to buy a good laser printer 'cause my Canon i250 does not get a good support under linux. :D

---

### Post by EL1984 on 2007-06-01
My wlan isn't working too... can see here: 
[http://ubuntuforums.org/showthread.php?t=459084]("http://ubuntuforums.org/showthread.php?t=459084")

in any case i preferred 6.06, at least wlan worked on it :/

---

### Post by Enverex on 2007-06-01
> **ppietryga said:**
> Hi,
had been away for some time.
I can't compile it either, and didn't receive any help with it.
But are You sure your card is ok? Maybe it's broken?

I've have had some experience with rt2500 on another computers and it has always worked like a charm (I had more trouble with it under Windows then with linux).
It always worked even from LiveCD. :o

And if Any of You have a problem with a wireless not working, the issue may be with an AP (or wireless) isolation enabled on Access Point. To resolve this I did just this :D:
```
sudo modprobe 8021q
```
And sometimes **this** can help You :)
```

sudo vconfig add ra0 <vlan #>

```
before setting the interface up.

PS. By the way: does anyone know, how Windows XP know which vlan_id it needs? I use my computer in many different networks and I need to run the vconfig command very often. Under windows I don't need to. Well I don't even know how could I set it up manually. :confused:

PS2. There's only one more thing, that keeps my Windows on HDD. I need to buy a good laser printer 'cause my Canon i250 does not get a good support under linux. :D

The card is fine, it works under Windows. As I pointed out it doesn't work under Linux because I'm on kernel .22 and it doesn't compile against >= .21

---

### Post by cptcrunch on 2007-06-01
The latest updates broke my wireless on my laptop. Now I am using the old cat5 cable. 1 step forward 2 steps back ubuntu, lol


Cheers

---

### Post by ihristov on 2007-06-02
It worked pretty much straight away with the native bcm43xx driver.
The only thing I had to do was to install the firmware.

I noticed that it was there was an error loading the firmware
```
$ dmesg | tail
[  783.782769] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
```

So I installed fwcutter:
```
$ sudo apt-get install bcm43xx-fwcutter
```

This prompted me to download the firmware. It detected the card, extracted the correct firmware and after reloading the module all worked perfectly fine.
```
$ sudo modprobe -r bcm43xx
$ sudo modprobe bcm43xx
```


My laptop is an HP dv2000

```
$ lspci | grep -i broadcom
01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
```

```
$ lspci -n | grep 01:00.0
01:00.0 0280: 14e4:4312 (rev 01)
```

---

### Post by msak007 on 2007-06-02
> **ihristov said:**
> It worked pretty much straight away with the native bcm43xx driver.
The only thing I had to do was to install the firmware.
If only bcm43xx supported 54g speeds, I'd use it. Until then it's ndiswrapper for me.

---

### Post by bcollignon on 2007-06-05
Realtek 8100 wireless card not recognized post upgrading from 6.10 to 7.04.  I understand it is a driver recognition issue.  Re-installed 6.10 as my fix, but lost lots of settings and files.  Not overly impressed thusfar, but I understand two things:  you get what you pay for and Windows is only getting more difficult to deal with.

---

### Post by ukripper on 2007-06-07
My BCM4318 worked fine with some tinkering in Edgy using Acer Aspire. But yesterday I installed Feisty on my other laptop Sony Vaio with Atheros chipset which shows up in restricted module and also detects access point and essid however it doesn't accept WEP key and also Bitrate is only 1MB/s(strange). Today I will go and probably install atheros drivers myself and then try again.

---

### Post by diesel1 on 2007-06-07
bump!

---

### Post by guitodd on 2007-06-07
This appears to be a big problem.. I have one wired machine.. all is good.  I have a machine running a Dlink wireless.. No Worky.  And a laptop that ocasionally won't boot with the Cnet cardbus card in it's slot.  Still have some tinkering to do.

---

### Post by SkyScrap on 2007-06-08
Maybe it's a good idea to update the wiki with working hardware on Feisty. 

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

I'm currently looking for which hardware I should get that works best, but information is really scattered. My current tries to collect all data is documented here:
[http://ubuntuforums.org/showthread.php?t=467786](http://ubuntuforums.org/showthread.php?t=467786)

---

### Post by ukripper on 2007-06-08
Feisty worked out of the box on my Sony Vaio with Ati restricted drivers preinstalled with atheros Wlan i have just installed wlassistant and configured within 1 min and I am up and running with updates and dist upgrade now I am running all my edgy stuff on my new feisty on vaio.
Also confugured my samba as wins server for home network.
I am very happy feisty&Edgy user.;)

---

### Post by derekwp on 2007-06-08
I'll add to the wireless frustrated clan out there.

Most likely my ability to solve the wireless issue within a timely manner is directly linked to my knowledge of Linux, which is to say elementary.  However, after seeing and reading about Ubuntu I was intrigued.  Install went well, after a bit of confusion with the partitioning.  Then came the wireless issue...

WMP54G is the card I have.  For reasons this is my only way to connect to the router at the current time so a land line was not an option.  Then my story follows the same tune as many in here have said: hours tinkering with X Y Z files, settings, debs, tars etc...  What a mess.

To be honest, If I were to do a fresh install again I would "be afraid, be very afraid."  Although I can safely assume it was: uninstall gui network progs, install ralink/wpa supplicant from thier website, install serialmonkey drivers in coordination with editing from a wiki on RT61 drivers.  /shudder

Since getting it to work a few days ago, I have had a good time with this new OS.  Playing with Beryl and different docks is an experience a VIsta user can only dream about.

Derek

---

### Post by james957 on 2007-06-08
I've got a Broadcom 1390, and had all kinds of trouble with Dapper.  But I did a clean Feisty install, and with the help of this:
[https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%28WifiDocs%2FDriver%29)

wireless is working perfectly now!

This is the best experience that I've had with ubuntu by far.

James

---

### Post by myo on 2007-06-09
It works fairly well on my 12" G4 Powerbook, although sometimes it won't pick up new networks. 

Completely null on my Athlon desktop though... = \

---

### Post by SkyScrap on 2007-06-09
I swapped my USB WLAN Stick against a PCI card yesterday, and now it works immediatly! Thanks to the reports in this thread, they were a very helpful resource to check which cards work well with Feisty.

My network card is now a D-LINK DWL-G520 (Rev. B4):
 ```

andreas@andreas-desktop:~$ lspci | grep Ethernet
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
04:09.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

I plugged it in, when I logged in, I was greeted with a symbol that new restricted drivers have been loaded. I choose my network from network manager, it asked me for my WPA key --> it just works. :biggrin:

---

### Post by ukripper on 2007-06-09
> **SkyScrap said:**
> I swapped my USB WLAN Stick against a PCI card yesterday, and now it works immediatly! Thanks to the reports in this thread, they were a very helpful resource to check which cards work well with Feisty.

My network card is now a D-LINK DWL-G520 (Rev. B4):
 ```

andreas@andreas-desktop:~$ lspci | grep Ethernet
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
04:09.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

I plugged it in, when I logged in, I was greeted with a symbol that new restricted drivers have been loaded. I choose my network from network manager, it asked me for my WPA key --> it just works. :biggrin:

I have the same atheros chipset in my vaio laptop. It is great to see it working out of the box unlike edgy or dapper.

---

### Post by Kubunteando on 2007-06-09
Wireless is working in Feisty but not in a very stable way.
I use the bcm43xx kernel driver for a wireless Dell Broadcom 4311.
Some times when connecting to the WIFI network I get in the kernel log "IRQ_READY TIMEOUT" and then the only solution to get the wireless working is to reboot the computer.

I have noticed it is important the firmware you load to the card with fw-cutter.

So I cannot trust the wireless and I use a wired Ethernet.
It is a pity the HW support goes so slow...

---

### Post by truico on 2007-06-09
:oops::confused:
This is driving me up the wall.
Intel Corp. PRO/Wireless 3945ABG Network worked fine after 7.04 install on my Ahtec laptop.
Until yesterday.
Interface info. just disappeare: Hardware adress: not available; multicast: not av.; MTU: not av.; Connection Speed: not av.; Status: not av. 
What can have happened? Or better: HOW can I make the machine recognise the wireless card again???

---

### Post by Bartikky on 2007-06-09
My wireless worked for a while, only because it was using the neighbours unprotected wireless rather than mine, I haven't voted in the poll yet because I am still doing a bit of tinkering to try and get it to work for my wireless router.

---

### Post by Cowboy22 on 2007-06-09
I am really disappointed I cannot update my laptop to 7.04 because of the wireless issue.
Works fine with 6.10.

I really cannot understand why very knowledgeable and gifted people will spend months developing a complex program that is nothing more than eye candy for kiddies and let a very important issue like wireless connectivity slide!

In this day and time a laptop that cannot connect wireless is nothing more than a very expensive doorstop.

How can any linux distro ever expect to become mainstream until this issue is fixed?

End of rant.

---

### Post by percyt on 2007-06-09
I am lucky to have 2 laptops - one my own (Dell Latitude D600) and a works one HP (Compaq) nc6000

I started out booting 7.04 Fiesty on the Dell and could not get it to see the wireless at all.
I tried with 6.10 and still nothing.

Tried booting the HP with Fiesty and it worked out of the box!!

Seems i'm going to have to find another Linux distro until Ubuntu is fixed for the Dell wireless card.

I'm downloading Suse 10.2 so i'll see what that says.

---

### Post by mahasmb on 2007-06-09
For some reason ... I don't see how I can post a new thread. Anywho, here's my issue:

I initially installed 6.06 LTS a few months ago, but wireless wasn't working because I have the BCM43XX card. After a lot of tinkering and looking around I got it fixed. So wireless was working beautifully.

Just the other day I decided to upgrade to Feisty Fawn. So I upgraded to 6.10 and am now in the middle of upgrading to 7.04. (Wireless didn't seem to be working with 6.10... but I've decided to leave that problem for when I'm finished upgrading to Feisty ) But I've been asked this and I don't know which to pick:


======================================
Replace the customized configuration file '/etc/modprobe.d/blacklist' ?

--- /etc/modprobe.d/blacklist	2007-05-02 20:24:08.000000000 -0400
+++ /etc/modprobe.d/blacklist.dpkg-new	2007-04-03 10:03:42.000000000 -0400
@@ -24,5 +24,7 @@
 
 # causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
 blacklist i2c_i801
-#module below does not work with Broadcom 4318 wireless cards
-blacklist bcm43xx
+
+# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
+blacklist r818x
+blacklist r8187

=======================================

So basically it's asking me if I want to keep my old customized file or upgrade to the new one. I don't wanna mess this up.

And oh, I'm pretty new to Ubuntu. I'm trying to see if I can replace Windows with it.

---

### Post by Drifter on 2007-06-09
It just doesn't work does it.

---

### Post by detroit/zero on 2007-06-10
I did a fresh install of Feisty on a new Toshiba laptop that I'm dual-booting with Vista. Wireless worked with no problems and no issues at all.

---

### Post by ajlewis2 on 2007-06-10
> **mahasmb said:**
> For some reason ... I don't see how I can post a new thread. 
<snip>
But I've been asked this and I don't know which to pick:
======================================
Replace the customized configuration file '/etc/modprobe.d/blacklist' ?

--- /etc/modprobe.d/blacklist	2007-05-02 20:24:08.000000000 -0400
+++ /etc/modprobe.d/blacklist.dpkg-new	2007-04-03 10:03:42.000000000 -0400
@@ -24,5 +24,7 @@
 
 # causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
 blacklist i2c_i801
-#module below does not work with Broadcom 4318 wireless cards
-blacklist bcm43xx
+
+# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
+blacklist r818x
+blacklist r8187

=======================================

So basically it's asking me if I want to keep my old customized file or upgrade to the new one. I don't wanna mess this up.


For a new post, go to the top left and click on "Networking and Wireless" to move up out of this thread. Then near the top left you will see the link for new post.

This new file is going to delete the blacklist bcm43xx which you may or may not need with Feisty.  It is going to add a couple.  I would suggest that you keep your old file, because the other two that it is adding are wireless modules and you obviously do not have those since you are using broadcom most likely.  You may no longer need the blacklisting of the bcm43xx, but it shouldn't hurt to leave it if your card is using a different module.  bcm43xx is blacklisted because it was loading when it shouldn't have been.  If that is removed from the file, the wireless will not work unless this is something they have fixed.  I imagine that you added it when you fixed your wireless problem. 

Tell the installer to leave the file.

Anita

---

### Post by ukripper on 2007-06-11
> **percyt said:**
> I am lucky to have 2 laptops - one my own (Dell Latitude D600) and a works one HP (Compaq) nc6000

I started out booting 7.04 Fiesty on the Dell and could not get it to see the wireless at all.
I tried with 6.10 and still nothing.

Tried booting the HP with Fiesty and it worked out of the box!!

Seems i'm going to have to find another Linux distro until Ubuntu is fixed for the Dell wireless card.

I'm downloading Suse 10.2 so i'll see what that says.

Goodluck!

---

### Post by ajlewis2 on 2007-06-11
> **percyt said:**
> I am lucky to have 2 laptops - one my own (Dell Latitude D600) and a works one HP (Compaq) nc6000

I started out booting 7.04 Fiesty on the Dell and could not get it to see the wireless at all.
I tried with 6.10 and still nothing.


The Dell is supposed to have Intel PRO/Wireless 2100,  The module for that card is contained with the kernel image along with the firmware.  I don't have the card; so I've never used it, but the module is ipw2100.  

Try these things to see what the card is and if the driver is loaded. In a terminal:

Look for the card with:
```
lspci 
```

Look for the module:
```
lsmod |grep ipw
```

If you don't see the module:
```
sudo modprobe iwp2100
```

It would be odd if that is the card and the module did not get loaded, but these are the first things I would look at.  This card does work in Feisty according to some posts in this forum.

Anita

---

### Post by alex_anthony on 2007-06-13
third ndiswrapper bcm43xx install - getting easier all the time (although this may be me getting better)

---

### Post by ukripper on 2007-06-14
> **alex_anthony said:**
> third ndiswrapper bcm43xx install - getting easier all the time (although this may be me getting better)

I am using Ndiswrapper for bcm4318 chipset, worked first time within 2mins of fiddling around in edgy.
ndiswrapper has come a long way with Edgy towards Feisty andis  in very strong position.
Follow the correct guide for your particular chipset and you wont be dissapointed.

---

### Post by Circus-Killer on 2007-06-14
currently running HP Pavilion DV6000 laptop with a broadcom wireless card.

the wireless did not work out of the box, but i was able to get it working using the ndiswrapper.

i followed these instructions to do so: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

---

### Post by absol_of_doom on 2007-06-14
For everyone with a Linksys WUSB54G v4, try unpluging it and repluging it in before you set it up.  I spent three days trying to make mine work only to find that I just needed to unplug it first! I really felt stupid. :p

---

### Post by thecure on 2007-06-15
On one of my laptops, which was a recent clean install of feisty, it was adding extra "auto eth0, auto eth1, auto etc." to the end of the configuration file when ever I changed adapters or chaged settings. Once I figured this out a deleted the extra's "auto whatevers" and  it worked. On this one particular laptop is the only one I had to enter the wep key manually; and then later the wpa key when I went to that in the config file. The others work like a charm whenevr I change settings without messing with the config file.

---

### Post by ajlewis2 on 2007-06-16
> **Kourosism said:**
> I can't get WiFi to work on Feisty LiveCD on a Advent 7113. I've posted this a few times elsewhere, but I'm not spamming - just trying to find a solution. I've had a read around, and cannot seem to find a workable solution - I'd like to get the connection working on the LiveCD before installing, as I can then be certain it will work, without spending too much time on it - is this even possible?

My original post:-


I've been playing around with Ubuntu for a year or so, and I finally got around to purchasing a laptop to install it onto. I loaded the LiveCD first, as I wanted to make sure everything appeared to work, and on the whole it did, except I am having the following issue.

Ubuntu can see my wireless LAN - but it refuses to connect to it. It simply sits there attempting to connect, but does not. I have tried it without security, and with 64bit WEP, but still no joy. Any hints? I don't really want to go "whole hog" if I can't get Wifi to work - the main reason for having a lappy these days.

The laptop is an Advent 7113. I believe it uses an inbuilt MSI 6877 WLAN card.

Here is someone who went through what you have.  In fact, this may be you!  I did not read it through entirely, but maybe it will help.

I don't know why the card is not showing up in lspci. Perhaps it is usb?  lsusb would show that.  The only reason I suggest that it might be usb is that in the article the guy states that Feisty mistakenly loads rt73usb for the driver.

[http://www.andrewcocker.co.uk/wep-wpa-on-linux-advent-7113-ubuntu-7.04-feisty-fawn.html](http://www.andrewcocker.co.uk/wep-wpa-on-linux-advent-7113-ubuntu-7.04-feisty-fawn.html)

Anita

---

### Post by slyboots on 2007-06-16
Yes but the package bcm43xx-firmware that have my nx6110 get to work with my Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller,[COLOR="Red"]** is listening to all connected devices to same access point.**[/COLOR] So for example: gkrellm or other iftop is showing all connections from other pcs. I wold like use gkrellm for monitoring my transfered sizes of data, but with this function is it no possible. I have maked downgrade, but without efect.

Previously i have used ndiswrapper with windows direvers, but they havent maked this issue previously. I useing newest feisty with newest updates, withou special changes.

Any idea how to turn this "feature" off?

---

### Post by RocketRanger on 2007-06-17
I use a zyxel zyair g-302v3 card. It was plug and play in Dapper and has shown only a fleeting glimpse of life in Feisty.

---

### Post by jrtpaul on 2007-06-17
Sort of. i tried for days to get the card going (BCM4311) and now i cant find my home network, only neighbors.......

If anyone could gimme some help that would be great. The thread is [**[COLOR="Red"]here.[/COLOR]**]("http://ubuntuforums.org/showthread.php?p=2859997")

---

### Post by thecrazyguitargod on 2007-06-17
Hi,
 well first of all i'd like to thank all you developers out there for the wonderfull ubuntu 7.04. I purchased a IBM tp40, wiped of windooz, installed feisty, and everything except for wireless worked out-of-the-box! The machine is a second hand one and the guy i bought it from, exchanged the IntelPRO mini-pci card for a Broadcom 4318 based one. I swa this only when i had the machine. Searching for a native driver, i found bcm43xx, but the developer say its unstable. It also didn't work for me. So here's what i did:

1) I got the newest version of  [Ndiswrapper (1.46) here]("http://sourceforge.net/project/showfiles.php?group_id=93482")
together with the [widows drivers here]("http://ubuntuforums.org/attachment.php?attachmentid=30908&d=1177587401")

2) Then i compiled, installed Ndiswrapper (You need the build-essentials package from the ubuntu repositories!) with
```
make
sudo make install
```

3) Next i unpacked the windows driver archive and went into the newly created folder,which contains bcmwl5a.inf and bcmwl5.sys, then i ran: 
```
ndiswrapper -i ./bcmwl5a.inf
```. This causes Ndiswrapper to load the windows driver. Running ```
ndiswrapper -l
``` you should see something like
```
computer:~$ ndiswrapper -l
bcmwl5a : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)

```

4) The next step was to delete everything in /etc/network/interfaces, except
```
auto lo
iface lo inet loopback
```
This has to do with the network manager, which controls every network interface, which isn't manually configured in /etc/network/interfaces (see the [wiki for Network Manager here]("https://help.ubuntu.com/community/WifiDocs/NetworkManager") )

5) I then reloaded Ndiswrapper:
```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```
and restarted the network:
```
/etc/init.d/networking restart
```
If it doesn't work, just reboot.

6) Now the network manager applet (the 2 black monitors in the upper right corner), shows on mouse click, a list of availible wired/wireless networks and their strengths (for the wireless ones).

I hope this saves some people headaches! Buy the way, you might ask why i didn't manually configure Ndiswrapper in /etc/network/interfaces. 

One reason is: it just didn't work. The driver was loaded, ifconfig showed an interface eth1, as did iwconfig. The problem was, i wasn't able to set the essid with iwconfig.

Second, the network manager works flawlessly, and like i said, i get a nice list of networks, from which i can choose one.

Cheers thecrazyguitargod

---

### Post by superuser on 2007-06-17
Hi,

I have a BCM4318 WLAN card in my network that used to work perfectly with Edgy Eft and the network-manager gnome applet, having installed ndiswrapper. Since I upgraded, however, I experience that it takes ages to get a WLAN connection going, and in many cases doesn't work for 6-7 tries. Once it manages to establish a connection, everything works quite as it should.

I also noticed that the wrong network connection is monitored (eth0 which is the ethernet card really. Of course I can easily change to eth1.) and that, even though working with ndiswrapper, the connection quality can now be display. I also seem to see an insane amount of networks, some of which must be very far away, as even in Windows I cannot see them.

BTW: Where can I delete my current network-manager configuration?

Thanks
superuser

---

### Post by ukripper on 2007-06-17
> **superuser said:**
> Hi,

I have a BCM4318 WLAN card in my network that used to work perfectly with Edgy Eft and the network-manager gnome applet, having installed ndiswrapper. Since I upgraded, however, I experience that it takes ages to get a WLAN connection going, and in many cases doesn't work for 6-7 tries. Once it manages to establish a connection, everything works quite as it should.

I also noticed that the wrong network connection is monitored (eth0 which is the ethernet card really. Of course I can easily change to eth1.) and that, even though working with ndiswrapper, the connection quality can now be display. I also seem to see an insane amount of networks, some of which must be very far away, as even in Windows I cannot see them.

BTW: Where can I delete my current network-manager configuration?

Thanks
superuser


try wlassistant, it a KDE app but you can run by issuing sudo wlassitant in terminal once installed. it is very easy to configure and works great with bcm4318 chipset , I have found no problem so far.

```
sudo apt-get install wlassistant
```

---

### Post by superuser on 2007-06-17
ukripper,

thanks for your tip. I will try that asap.

In the meantime, **I got lucky by replacing the ndiswrapper* debs with the hand-built ndiswrapper source fresh from source forge.** Essentially summing thecrazyguitargod's post (big thanks), then: **If you use ndiswrapper, and if your wifi card worked ways better in prior ubuntu versions, then try and get a newer ndiswrapper drvier version from the source(tm). ** My WLAN connection attempts (even to encrypted networks, that is) are now dealt with within seconds!

---

### Post by thecrazyguitargod on 2007-06-18
Hi, @ukripper: isn't this what opensource is all about? By the way, deactivating the wireless card in /etc/network/interfaces is important, otherwise the network manager blocks ndiswrapper from working. One can also deinstall nm with loss of the fancy applet.

@everyone: I would like to configure the network manager so that i can easily switch between 2 wired networks with STATIC adresses, via nm-applet. If i let nm take over eth0 (wired), then it attempts to aquire an ip via DHCP, but i want it to manage eth0 with 2 static ip's.
Can s.o. help?
Cheers thecrazyguitargod

---

### Post by bobz086 on 2007-06-18
clean install, Linksys wireless.
worked fine.

---

### Post by timcredible on 2007-06-18
my wireless works easily, but it's broadband wireless, so i'm really using the ppp dialer, so maybe that's not a fair vote for having wireless working.

---

### Post by pandorazboxx on 2007-06-18
first off i just started using linux and have no idea what i'm doing. but i know a little bit of unix so some of this makes sense. 

I just installed 7.04, and i have a usr 5417 PCI card. I tried to install using NDIS wrapper. In the install instructions it tells you to check and make sure one of the directories has a .config file. when i checked it there was no .config. has anyone done this and where can i get the .config file. it says i should update the kernel but i just downloaded this fiesty fawn and i would think it has the latest kernel with the right files...

someone please help me :) thanks

---

### Post by thecrazyguitargod on 2007-06-18
Hi

There's no .config file. What you need to do is just run ```
make
```
in the directory of ndiswrapper, then ```
sudo make install
```. For this you need the build-essentials package from the ubuntu repositories:
```
sudo apt-get -i build-essentials
```

---

### Post by bobbyshafter on 2007-06-18
My first laptop ,Acer Aspire 5570Z which comes with unsuported wifi adapter.

Using a D-Link WUA-2340 usb stick.No native linux support,had to use xp driver with ndiswrapper.
imes
Very unstable work great sometimes,lockup sometimes,had to unistall the driver and reinstall.

Edit my etc/modules to include ndis module to run at boot ,could this be causing the unstable condition?

---

### Post by majesticturkey on 2007-06-18
I have to tinker each time I want to use it.

Clean 7.04 install here, although with the same hardware in earlier versions, I had no problem using ndiswrapper...which doesn't work with 7.04.

---

### Post by kevdog on 2007-06-18
Is there any point to this thread?? People who say they cant get their wireless working just havent spent enough time reading the forums or looking elsewhere.  Is getting wireless working in Feisty a pain -- YES, was it a pain in Edgy -- YES.  But come on, be more diligent in trying to find solutions to the problem, and when posting questions to the forum, it sure would be a lot more helpful to actually post some configurations about their wireless card and system, rather than the proverbial "It Doesnt Work!!"

---

### Post by jingba on 2007-06-18
Well, I'm not going to say, "It doesn't work!"  No, I'm going to say, "It works!" (kind of).  I got my D-Link DWL-G122 B1 to pull up!  :D

But, it won't do the WPA thing.  I am reading through threads to see what can be done.  I've followed a couple of recommendations in other threads (that WPA sticky is a little over my head and, thus, daunting), but I've not had success...  yet.

---

### Post by a2mech on 2007-06-19
Used Feisty 7.04Live CD on a Dell Latitude D600 with Intel Pro 2100 Mini A wireless adapter. The wireless works along with WPA, though I have to run Network manager twice for some reason. No other configuration was needed.

---

### Post by brimu on 2007-06-19
I think this might interest a few people having problems connecting to an access point.

When I first started up Ubuntu (Feisty) I wasn't able to connect to my Netgear router WGR614 v4 SSID: "müll netz". I tried everything from a manual configuration to roaming on but without luck.

Then I thought that the "ü" in the SSID is messing stuff up and in fact it was. I then changed the SSID of the router through the web interface to "ubvis" and after telling Ubuntu to connect to another wirelessnetwork: "ubvis" it connected without problems.

And for those of you wondering, spaces in the SSID didn't provide any problems either.

So to sum up, _**make sure that your SSID does not use any special characters...otherwise change it to chars from a to z.**_

greetz

edit: I'm running an Acer Extensa 4101WLMi with an Intel 2200BG wireless adapter.

---

### Post by ukripper on 2007-06-19
> **thecrazyguitargod said:**
> Hi, @ukripper: isn't this what opensource is all about? By the way, deactivating the wireless card in /etc/network/interfaces is important, otherwise the network manager blocks ndiswrapper from working. One can also deinstall nm with loss of the fancy applet.




What context you referring to? What is open source all about? I am lost mate. Till where I rember in my posts I didn't mention anything to prove what open source is about? Please enlighten me?

---

### Post by friendly2004 on 2007-06-19
mine is working fine now.

after having had some trouble my wifi is working properly. i use the network-selector-applet to choose between the ethernet-card and the wifi-module.

i like feisty. i used open-suse10.2 before. this OS now is quite enough for me as i only want to use it for internet ...

but i think i'll delet windumb xp to have only linux installed.

---

### Post by pi3832 on 2007-06-19
Mostly a bump, but I'll detail my problems:

I'm trying to run Xubuntu 7 on a refurbiushed T30 ThinkPad.  I gave up on the Cisco card that came with it, and bought a replacement.  I checked around and the Intel 2200BG is listed all over the place as working "out of the box" with Linux, even with WPA encryption.

I bought and installed an Intel 2200BG, and it doesn't work.    I did a clean re-install of 7.04, and then updated everything that synaptic wanted to update.  The hardware is detected, the correct module is loaded, the firmware is the latest release.  The card still doesn't work.

And, to add insult to injury: it works fine under XP.:roll:

I suspect it's something simple, but even finding simple things seems to be difficult sometimes with (X)Ubuntu. (Yes, I'm a n00b.)

---

### Post by tnmarktx on 2007-06-19
Got my Dell 1501 to work with Feisty under ndiswrapper.  Works with no problems.

---

### Post by thecrazyguitargod on 2007-06-22
> **ukripper said:**
> What context you referring to? What is open source all about? I am lost mate. Till where I rember in my posts I didn't mention anything to prove what open source is about? Please enlighten me?

I was referring to your '(Big Thanks!)' in your reply my prior post, nothing else. By this i mean that in the open source community everyone should help those in need.

---

### Post by ukripper on 2007-06-22
> **thecrazyguitargod said:**
> I was referring to your '(Big Thanks!)' in your reply my prior post, nothing else. By this i mean that in the open source community everyone should help those in need.

That is the whole concept of Ubuntu. - Linux for Human beings :p

---

### Post by Drittponken on 2007-06-27
In Ubuntu Feisty i just couldn't get my wireless RaLink card to work :S It found some networks but with 0% link strenght.

After some hourns i just couldn't stand it and tried a cd with Kubuntu 6.06 i had laying around and it worked direktly -.-

So now i'm gonna try Ubuntu 6.06, i dont like kde. :(

---

### Post by ukripper on 2007-06-27
> **Drittponken said:**
> In Ubuntu Feisty i just couldn't get my wireless RaLink card to work :S It found some networks but with 0% link strenght.

After some hourns i just couldn't stand it and tried a cd with Kubuntu 6.06 i had laying around and it worked direktly -.-

So now i'm gonna try Ubuntu 6.06, i dont like kde. :(

Just install gnome-desktop within kubuntu it will become ubuntu

---

### Post by Paul_Joseph on 2007-06-29
Had a bit of problem, but it was related to the boot options I was using not Feisty.  I have a HP Pavilion dv6000 (6054nr) with Dell 1390 (Broadcom 4311) wifi card.  I am running Feisty 7.04 Xubuntu AMD64.  I am using ndiswrapper.

My trials:  [http://ubuntuforums.org/showthread.php?t=487198]("http://ubuntuforums.org/showthread.php?t=487198")

---

### Post by graphicw on 2007-06-29
I am among those that cannot get wireless to work with 7.04.  I can see the network SSID and encryption type show in the network manager, but it does not connect with the key and will work even if I disable all encryption.

---

### Post by chetter72 on 2007-06-30
My fun time is I finally got my card working but I cant connect at all, network reads my card, card reads my network, but system wont let them play together.  still no wireless to speak of, Kevdog is helping me I hope he has a trick up his sleeve! thanks Kevdog for all your hard work!

---

### Post by dudenamedsteve on 2007-06-30
Worked after some fighting, IBM T-23 with a USR MAXg 5411.  Used the [AutoNDISWrapper script]("http://ubuntuforums.org/showthread.php?t=457371") with the windows drivers and BAM, surfing from my recliner at 54Mb/s drinking a beer.

---

### Post by bruzer on 2007-06-30
I haven't given up on wireless yet!!! Soon, I will rule the world!

Oh, bump.

---

### Post by ajlewis2 on 2007-06-30
> **pi3832 said:**
> Mostly a bump, but I'll detail my problems:

I'm trying to run Xubuntu 7 on a refurbiushed T30 ThinkPad.  I gave up on the Cisco card that came with it, and bought a replacement.  I checked around and the Intel 2200BG is listed all over the place as working "out of the box" with Linux, even with WPA encryption.

I bought and installed an Intel 2200BG, and it doesn't work.    I did a clean re-install of 7.04, and then updated everything that synaptic wanted to update.  The hardware is detected, the correct module is loaded, the firmware is the latest release.  The card still doesn't work.

And, to add insult to injury: it works fine under XP.:roll:

I suspect it's something simple, but even finding simple things seems to be difficult sometimes with (X)Ubuntu. (Yes, I'm a n00b.)

Does it show up in the Menu/System/Network?  Is Wireless showing there and is it checked? 

Anita

---

### Post by obryant on 2007-07-03
I have the Prism 2.5 Wavelan chipset. During installation with the Feisty Alternate CD, there was no difficulty. After installation from the Live CD, however, it wanted to use the prism_pci driver. I added
   blacklist prism2
   blacklist prism2_pci
to the end of /etc/modprobe.d/blacklist, and now it is working with the orinoco_pci driver.

---

### Post by odiseo77 on 2007-07-04
I voted for options 4 and 5; I'll try to explain myself why: I'm using an Edimax EW-7128g wireless card (rt2500 chipset) whcih works out of the box on Ubuntu. By the time of installation I was using a WEP encryption to connect to my router, and it was as easy as opening The Gnome network manager tool, entering my WEP key, and I was done. But later, I decided to change to WPA and the Gnome networking tool doesn't allow you to set a WPA connection, so I had to search a bit on google on how to set up a WPA connection on Ubuntu, but after two hours of editing my /etc/network/interfaces file, stopping and starting the network and looking on google I had it working like a charm. To be precise, all I needed to read was [this document]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500") in order to edit the 'interfaces' file properly, and [this other doc]("http://doc.gwos.org/index.php/WirelessSec") (which overall didn't work, but taught me how to generate the hex key from my ASCII key).

---

### Post by dennis_the_bug on 2007-07-04
Ubuntu 7.04 Sucks. Wifi does not work. Printer does not work. Nothing works. It forced me to rollback to 6.10. I don't know how Canonical Ltd. is selling it as a Desktop Software, Red Hat is much better. At least we get source that compiles easily on red hat distribution.

---

### Post by ukripper on 2007-07-06
> **dennis_the_bug said:**
> Ubuntu 7.04 Sucks. Wifi does not work. Printer does not work. Nothing works. It forced me to rollback to 6.10. I don't know how Canonical Ltd. is selling it as a Desktop Software, Red Hat is much better. At least we get source that compiles easily on red hat distribution.

Then Why  even use  6.10,  carry on with RedHat!

---

### Post by atarianer on 2007-07-17
So after reading this, among other postings i assume 6.10 would be the best choice for my Gericom X5 Force with prism 2.5 chipset ?
I was thinking about installing OpenSuse 10.2 but i will give 6.10 a try ...

---

### Post by outlaw686 on 2007-07-24
bump. i'm somewhat new to ubuntu and getting these wireless drivers to work on my thinkpad r52 is driving me nuts.

---

### Post by nick.inspiron6400 on 2007-07-25
I had a lot of problems with the Intel PRO Wireless 2200 in Ubuntu, and in Linux as a whole! I then got a new computer and the wireless has been a little luckier.

Still though Linux does not have the hardware-detection and sometimes one-click install, like Windows has. Linux needs to become more user friendly. 

Why are there so many new distros? But at the end of the day they are still bases on the same problem? Isn't that what Microsoft does? Just build on from problems?

When I switched the most confusing thing was KDE and Gnome.

---

### Post by Simon-v on 2007-07-25
I made wireless to work (same old Broadcom card which is known to make issues) on Edgy. When i upgraded to Fiesty it worked straight away - probably because the update just replaced the executables without touching the settings or the extracted firmware.
I must be one of the lucky people.

---

### Post by junknstuff on 2007-07-27
im using ubuntu 7.04, fresh install, and im suprised to read that every person who has the intel pro wireless 3945 chipset has had zero problems, but mine just dont connect with feisty fawn :(

i have a dv2000t CTO and everything else seems to work fine BUT the wireless. even after manually configuring i wasnt able to get it go work. i await a fix..


*edit* didnt know i had to uninstall the network manager, but after that WICD works great! thanks for the help!

---

### Post by spitfirenut on 2007-07-31
Couldn't make it work reliably at first, then found a link to Wicd (wicd.sourceforge.net) and it was working within 5 minutes.  The only problem I have is a glitch on hibernate.  When it comes back up it loses my wireless card and I have to reboot.  I don't know if it's a card problem, a expresscard slot problem on the bus, of a Feisty problem, but it's pretty low priority.  I installed a week ago fresh from Dapper.  Hardware is Dell B120 with 1390 Wlan express card for wireless.  I highly recommend Wicd, with the 1390 just use the default Wext driver.
Don

---

### Post by misfitpierce on 2007-07-31
Wireless works fine in feisty for me with firmware cutter it auto set everything up on broadcom.

---

### Post by vampyrebytes on 2007-08-14
> **vampyrebytes said:**
> Using an HP Pavilion zv5000 series (custom) with a Linksys WPC11 v4 PCMCIA card.
I don't recall exactly whether in Dapper and Edgy it was eth0 or ath0 or wlan0 but I have had it working "out of the box" since Dapper came out. I remember having to tweak an earlier installation (Breezy) heavily to get a lot of stuff working. Including something baout the PCMCIA slot.

Dapper and Edgy were both clean installs and the card worked without any tweaks.
Feisty doesn't see it at all... But I'm a "n00b" and don't know how to go behind the scenes and figure crap out for myself. I am technologically capable, if I could find a walk through.. but no one seems to know exactly what the problem is.

IN the end, I found the solution.
Due to some problems some users had experienced with the drivers for this particular card set, they made it to the blacklisted file.

```
sudo nano /etc/modprobe.d/blacklist
```
I just commented out these two lines: 
```
#blacklist r818x
#blacklist r8187
```

I also need to add a dummy character to the end of the SSID for some reason. But my wireless is working "just fine" now.

---

### Post by paintandswim09 on 2007-08-14
Yeah... I would say that this is not entirely reflecting the population of Ubuntu users. I found this poll while searching for how to install ndiswrapper, because my DLink WUA-1340 usb adapter is not working. Does anybody know of a really good link for either of those topics?

---

### Post by netron on 2007-08-20
> **vampyrebytes said:**
> IN the end, I found the solution.
Due to some problems some users had experienced with the drivers for this particular card set, they made it to the blacklisted file.

```
sudo nano /etc/modprobe.d/blacklist
```
I just commented out these two lines: 
```
#blacklist r818x
#blacklist r8187
```

I also need to add a dummy character to the end of the SSID for some reason. But my wireless is working "just fine" now.

that didnt work for me.

Gateway laptop with Realtek RTL-8185 chipset 

when i do "dmesg" i see lots of :

"rtl8180: WW: No more TX desc, returning 30 of 30"

fresh feisty install + all the latest updates via apt-get upgrade

---

### Post by eeefresh on 2007-08-20
I have an old P3 notebook and a Netopia wifi card that a friend gave me.  (RT2500 chipset, I think)  I have been using it since Ubuntu 5.10 and never had to configure anything.  I considered myself very lucky.

However, when I upgraded to Feisty, the card no longer worked.  Knowing very little about setting up wireless networks in Linux, I decided just go back and do a fresh install of 6.10.  Wireless *still* didn't work.  6.06 didn't work either.  Why in the world wouldn't my card work with older versions one day, and not the next?

So, basically, Feisty screwed me.  The card woks fine when I boot into Windows (dual boot setup.)  I have no experience with network manager or NDIS wrapper, but I would appreciate a link to any troubleshooting guides!

---

### Post by dwc-ubu on 2007-08-20
Worked at home after 6.10 upgrade, then won't work on an open network?  dhcp not found?

I upgraded from Edgy a couple of days ago and wireless worked via network manager flawlessly at home. However when I tried an open network (with unbroadcasted  ESSID that I knew), it would connect but now no ip (or maybe dhcp, DNS, etc.)

I have a toshiba satellite A135-2286 with atheros wifi chipset

iwconfig showed only weak signal, and showed lots of of other area networks ok (which I have no password for)

seemed to connect but never an ip.

I tried disabling ipv6 as per ubuntu wiki, no dice, so I reenabled it

It seemed to insert my home systems DNS address into the slots in networks 

I got confused by the interaction between network manager and system:administration:network.

Finally I deleted all locations in networks and got back into roaming mode, still no dice

Then I rebooted and Network selector worked (i had left it in from 6.10) and i got an IP.

:confused: network manage does not play well with other things.  this reminds me of memory locks on old apple OS.

Maybe it will work at home now! 8-[

If I have time I'll try to reproduce this and post outputs somewhere, but i don't trust network manager.

---

### Post by cubdukat on 2007-08-21
I have had no problems with my wireless in Feisty, or any other version for that matter, and I expected to have the most problems of any user. For one, my laptop is a Compaq Armada M700--not exactly the bleeding edge in hardware. Second, the card is a refurbished D-Link wireless PC card with an Atheros chipset. I guess Atheros was widely supported in Linux, but not so much these days.

At any rate, even with a clean install, it worked right off the bat, except when I did the occasional kernel update, but even then I was eventually able to get it up after some tinkering in the previous kernel to switch things over to the new one. 

The one thing that concerns me though is one of the laptops that I'm seriously considering--the HP Pavilion dv6408--appears to be one of the hardest to get the wireless working on. The other one I'm considering--the Lenovo 3000 N100 that's on sale at Office Depot--is a little more expensive, but according to the Ubuntu Wiki appears to be more compatible, not to mention Lenovo's excellent reputation where Linux is concerned. Hopefully I'll have good luck with either one; if I can't get the wireless working in Ubuntu on either one, it's more or less a lost cause for any other distro, right?

---

### Post by chrisch on 2007-08-22
This is what saved my but on my Dell Inspiriion B120 with a Dell Internal wireless 1370 (Broadcom BCM43xx)  It took about 3 days of reading posts and pulling my hair out.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I had to manually configure the network though, it wouldn't let me leave it in roaming.

CC

---

### Post by UI-Freak on 2007-08-22
I had to manually configure my wireless network. It was hell. I fear that upgrading to Gutsy will break it. I really don't want to go through it again.

---

### Post by mimsmall on 2007-08-22
(other than for the NIC)? 
DWL-G730AP Please post more info on making this card work.

---

### Post by R_U_Q_R_U on 2007-08-23
I installed the Cisco Aironet CB21AG-A-K9 cardbus wireless card on a Dell D600. Wireless worked without any issues. I am using WPA security and Fiesty asked for me to select the SSID of my network and my router WPA password. Connected immediately.

---

### Post by caricc on 2007-08-23
I have a broadcom 4306 on my laptop as wireless. After some playing around and a lot of searching, I found wicd for my manager. I have teh windows wireless drivers for this card, using ndiswrapper, etc, etc,  
This link helped me setup wicd. I have had no wireless connection problems since using this setup. 
[http://ubuntuforums.org/showthread.php?t=527159]("http://ubuntuforums.org/showthread.php?t=527159")

Actually, I even use it from connecting my laptop to a wired network at work. I may have to manually connect to my wireless at home and wired at work. but i can live with this. 

Enjoy.

---

### Post by ntom-taylor on 2007-08-23
bump

---

### Post by Scanner on 2007-08-27
bump

---

### Post by pi3832 on 2007-08-28
> **pi3832 said:**
> Mostly a bump, but I'll detail my problems:

I'm trying to run Xubuntu 7 on a refurbiushed T30 ThinkPad.  I gave up on the Cisco card that came with it, and bought a replacement.  I checked around and the Intel 2200BG is listed all over the place as working "out of the box" with Linux, even with WPA encryption.

I bought and installed an Intel 2200BG, and it doesn't work.    I did a clean re-install of 7.04, and then updated everything that synaptic wanted to update.  The hardware is detected, the correct module is loaded, the firmware is the latest release.  The card still doesn't work.

And, to add insult to injury: it works fine under XP.:roll:

I suspect it's something simple, but even finding simple things seems to be difficult sometimes with (X)Ubuntu. (Yes, I'm a n00b.)

A follow up:

I got the wireless to work using [wicd]("http://wicd.sourceforge.net/wiki/doku.php?id=faq").  It was basically painless.  If you're having trouble, I highly recommend trying wicd.

---

### Post by Tom W on 2007-08-28
It's an awefull job to get the wireless working. Iv'e been trying for 4 days now. No results.

---

### Post by KCPokes on 2007-08-28
Mine worked immediately after the install, somewhat.  My wireless connection works for basic surfing, but anything requiring copying large files or heavy traffic will cause my connection to drop.  The biggest issue is that I cannot reconnect back to my wireless without rebooting (well I'm sure there are other options, but a reboot is typically just the easiest at the time).  Seems to be a common issue with the Realtek chips (my card is Realtek 8187, i think), one that drives me nuts.

---

### Post by Teedyo on 2007-08-28
Ok, I stretched the truth just a hair by saying I can't get wireless to work on K 7.04.  I can get it to work using iwconfig and friends; just not using knetworkmanager.  On my home router; I use all 4 WEP key slots and rotate between them.  knetworkmanager appears to only support one key slot.  I would change to WPA but my knetworkmanager doesn't even give the option.  I've seen screenshots of knetworkmanager with WPA options but the version I have doesn't.  It does have an "Advanced" button but it is greyed out and unusable.  Perhaps I should do an apt-get reinstall of networkmanager??  When I manually connect using iwconfig and friends; networkmanager still doesn't show a wireless connection.  Normal??

---

### Post by HeavyAl on 2007-08-30
On my thinkpad t40 my wireless was through a pcmcia linksys card - feisty picked it up just fine during a clean install but I had to do some tinkering to get it to actually connect to my network - it didnt want to keep the wep key for some reason.

On my new Dell Inspiron 1721 WiFi worked straight away with a clean install. But then, when I had them build it I made sure they put in the Intel wireless card rather than the crappy built in Dell wireless. 

I love Ubuntu!

---

### Post by ZShakespeare on 2007-08-30
Voted works after tinkering. It actually worked out of the box for about 2 weeks, but now at least once a day at different times knetworkmanager will disconnect from my wireless, and get stuck at 28% - configuring device and won't reconnect after a soft boot, hard boot, or even if I completely power the laptop down, unplug it and remove the battery. I have to boot from my Ubuntu, or PCLinuxOS 2007 livecd, use it to connect to the network, and then reboot into kubuntu, after which the wireless works fine.

curiously this issue didn't begin until I installed uswsusp, and started using s2disk. The computer's suspend issues are another thing altogether. The odd thing is that the problem doesn't occur after resuming from disk, it seems to be at random, so I would tend to think the timing is coincidental.

for reference, my machine is an IBM Thinkpad T41 2373-1FU

---

### Post by simplysimple on 2007-08-31
I have a Belkin F5D7010 ver.5000 it has the atheros chipset. Everything works perfect but the card doesn't light up. Who knows? I suppose I'm saving battery without the lights and as long as my connection works I don't mind. **[SIZE="3"]My suggestion to anyone struggling with linux and wifi[/SIZE]** is to do research on what cards work well and then purchase that card. I did lots of research and decided on this one. I even spent time at several different stores in order to find the right version since Belkin has changed chipsets several times. My card will also do packet injection which is useful when testing the integrity of a network I've setup. Cheers! :)

---

### Post by mandeep kaur on 2007-08-31
Hi,

I had installed ubuntu feisty 7.04 on my edge laptop. I have a problem getting wireless connection in it. It has ipw2100 card. Please let me know if anybody know procedure of getting it into wireless

Thanks & Regards 
Mandeep Kaur

---

### Post by hadeshorn on 2007-09-02
I am running a DWL-G122 Vb USB. I plugged it in and it worked.

I am just trying to get WPA to work. Looking up a guide!

---

### Post by argie on 2007-09-02
Intel Wireless PRO 3945ABG. Out of the box with 7.04.

---

### Post by casa adelfa on 2007-09-13
Loaded Ubuntu 7.04 this week, having tried Susi 9.1, Xubuntu and an earlier Ubuntu. Using D-Link DWL-G520+  card. No luck on any distro, but Feisty is the closest I've got to a working wireless setup.
My network seems to be recognised, but every URL returns 'Server not found'. Bereft of ideas.
Computing should be fun.

---

### Post by DouglasAWh on 2007-09-13
my wireless was working, but now it's not.  It was working this morning, in fact.  Anybody know what could have broken it?

---

### Post by tomski on 2007-09-15
tried to compile the zd1211 driver and it errors all the time :(
if i am using a generic kernel image why is there not a generic module for the zd1211????

---

### Post by alanmzifa on 2007-09-19
[I][B]Thanks to all who placed a vote in the poll, viewed it or posted a reply.

Below is a reply I made today to another thread [located here]("http://ubuntuforums.org/showthread.php?t=554210") by someone else concerning wireless in Gutsy which is due out in a matter of weeks.
You might want to voice your own opinion there after reading my reply which I've pasted below.[/B][/I]



The OP stated that there was a poll somewhere on wireless.
I was responsible for starting that poll as I too got frustrated over wireless or lack of.
You'll find it here.

Every time I posted about my frustration somewhere I got the usual "yeah, but this way you can learn about the OS" answer. Fact is, I want to have to learn as little as possible. I'm neither stupid or uninterested but I have a 3 yr old and a (very) full time job.

I've wasted money buying wireless devices which were supposedly compatible only to find they either didn't work, worked erratically or worked at the time but subsequent versions of Ubuntu broke them. Both my partner and my 3 yr old are not computer buffs so I need something that will work without open heart surgery. I want Ubuntu/Open Source to be a hobby of choice not one of necessity.

In my circle of friends I am the most competent person I know around computers and I can't get a Ralink 2500 device to work with anything beyond 6.06 (which until a week ago I had installed on a laptop used by my partner and daughter).

I have 3 wireless devices that many, many hours of scouring threads here couldn't get working reliably on my desktop. I've therefore decided that wireless is just much too flawed on Ubuntu to be relied upon, who's fault that is doesn't matter.

I've wanted to support Open Source OS development but I was wasting too much time on trying to get this or that working adequately. My 6.06 on the laptop broke a couple of weeks ago. Couldn't find a reason as to why, it seemed to break after an automatic kernel update but the problem left me unable to boot anything.... so an old OEM XP install disc (which authenticated itself first time dialling into Microsoft - thanks Bill) found itself replacing Ubuntu after a year and a half's trails and tribulations.
Yes, it's slower, boot time in terms of weeks rather than seconds but works pretty much flawlessly - the clincher being I know the wireless won't fall over for those who use the laptop when I'm away on business or out working.

On my 64 bit desktop I currently have a 2 HDD dual boot system with XP and Ubuntu 7.04. XP is set to auto boot by default. The only reason Ubuntu is on there at all now is because I went and bought a pair of Solwise Homeplug powerline ethernet adapters which uses the mains electrical wiring in the house to distribute the signal instead of CAT 5 or wireless.

The fact is, and this is the reason I started the poll, for the majority of folks like me, even with above average computer knowledge, wireless is a non-starter. The poll was set up from a combination of frustration and curiosity to see how many others were in the same predicament.
Unfortunately when anyone criticizes the support for wireless a developer or someone else always dismisses it (either politely or not).

The results of the poll tells me that there are many, many disaffected people (who's views are NOT being taken on board) with an average knowledge of computers (the masses) who like me want to support Open Source OS development but can't find a way to. In fact I was genuinely surprised that the poll results were so one sided despite the fact that 4 out of 6 of the possible answers concerned wireless working in Ubuntu rather than not.

Because of this, and the fact that the thread is the 6th most viewed thread in the wireless/networking forum (c. 43,000) and the 2nd most replied to (402) I feel it has some real validity.

When the developers of all things wireless in Open Source (both Ubuntu and the drivers) decide to take these people seriously in terms of re-prioritising the resources devoted to addressing this only then will Open Source be available to the masses. Until that time it will be the preserve of the geek or enthusiastic hobbiest (I consider myself the latter).

As we stand it will be a very long time before Ubuntu (Gutsy or otherwise) finds it's way back on to any wireless machine of mine.

---

### Post by eger on 2007-09-22
> **jpatton said:**
> ANYway, the card actually uses the orinoco driver and in order to get mine to work i had to add the following entries to my blacklist file:

blacklist prism2
blacklist prism2_pci
blacklist hostap_pci
blacklist hostap

Your mileage may vary, good luck!

Just wanted to post that this worked for me on a Sager 8887 with a Gemtek wireless card. lscpi lists it using a Prism 2.5 chipset. So this is probably needed to force the Prism 2.5 to use the orinoco one.

---

### Post by uputer on 2007-09-23
Alan, the problem is that people post 'X works' without exactly explaining what that means.   This is a major problem with computer forums especially when it comes to technical discussions.

People post 'X works' which really means ABSOLUTELY NOTHING.   The person might have had whatever working for 1 minute.   Maybe 2.   Then it stops working but they don't ever come back to report it.   You don't know.

I got a Belkin USB adapter and tried to get wireless working in Kubuntu Feisty.   It did but it worked erratically and I couldn't sync it with a static IP setup.   Also, there were two different network config tools or methods (as far as GUI goes) and one only would allow it to be set up via WEP.   But, I wanted WPA.   KNetwork Manager allowed WPA but Network Interfaces only allowed WEP and I could use a static IP but can only configure wireless in WEP mode using that method.   It would take a while to activate and consequently would lose the connection eventually.   I could not go to my router settings either but perhaps, that could be solved by figuring out the problem.

My point is that this is another example in which Linux has major hurdles before it's a workable desktop option.

---

### Post by Jadephyre on 2007-09-23
BCM43xx works with the Native Firmware Mode, but just with 11MBit, no WPA2 and no hidden SSID... hope it gets better with Gutsy 7.10

---

### Post by holihue on 2007-09-27
> **mainely_linux said:**
> I went from 6.10 to 7.04 via upgrade.  My ipw3945 10/100 Intel Wireless device worked out of the box on my laptop.  The same cant be said of my dialup modem.

I have a ipw 3945 and it works almoust out of the box.
I have a screenshot of a test...

The speed has been like this after the upgrade to Feisty.
pleas help me with that:(:(:(

my friend was right next to me, and he got about 5000kbit in download and upload with wireless.
he have a broadcom 4318, and running ndiswrapper.

---

### Post by Jimby on 2007-10-01
I was finally able to get my wireless working through several hours of tinkering.  Im using a Dell C610 laptop with an Orinoco Proxim card 8480-fc.  Using the network manager was pretty much useless to me, wouldnt even alow me to chose wpa.  Anyhoo, I ended up editing etc/network/interfaces as follows to get it to work.  Though Im a little dissapointed in the range.  Having a hard time getting it to work downstairs.  When windows xp was on the laptop, it did not have any troubles.
Any suggestions is appreciated.

 BTW, Im using a WRT54G with DD-WRT firmware as my router.


auto ath0
iface ath0 inet static
address 192.168.1.99
gateway 192.168.1.1
dns-nameservers 192.168.1.1
netmask 255.255.255.0
wpa-driver Atheros
wpa-ssid My SSID
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk My WPA Key

---

### Post by Yiftos on 2007-10-02
I too am havining problems with Network manager. I have a fresh install of Fiesty 7.04 and a Xterasys  wireless card that contains the Realtek RTL8180 chips set. I removed the native driver from the modprobe.d/ blacklist file and seems to load just fine. It sees all the networks around me including my home router but it will not connect to any of them. I turned off my WPA and left my router wide open. I still could not connect. Network manager just jumps back to the wired. This card works just fine in a windows laptop so it is not the card bus.

It should not be this difficult to connect especially when the driver is shown to running.

---

### Post by Rob500 on 2007-10-02
Wireless works fine, just the button that disables/enables it that doesn't work.

I would hate it if I upgrade in 3 weeks time and I lose wireless completely :(

---

### Post by brazdf on 2007-12-08
I have a clean install of Xubuntu 7.04, using Realtek 8180. Couldn't make the wifi working at all. After a while I found teh driver but it would not connect. Next step was discovering I cannot setup the encyption parameters. The command (iwconfig) runs with no error message, but the card wouldn't accept the encrypton. When I disable the encryption on the router, the card works. Now I am trying to find a solution that would allow me to use encryption on my wifi.

---

