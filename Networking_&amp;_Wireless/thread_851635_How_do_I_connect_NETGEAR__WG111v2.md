---
title: "How do I connect NETGEAR  WG111v2?"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by Gman035t on 2008-07-06
I use a netgear adapter to connect to my router. The adapter requires drivers to be installed. How would I go about making this work with Ubuntu? Thanks in advanced!

---

### Post by pytheas22 on 2008-07-06
My WG111v2 definitely "just works" on Ubuntu 8.04, using the p54 driver, with WPA.  You should not need to do anything besides plug it in and click connect in Network Manager (note however that for some reason the light doesn't come on, but it still works fine).  Does that not work?  If so, please provide this information:
```

lsusb
```

and which version of Ubuntu are you using?

You can always use ndiswrapper (a utility allowing you to drive your card via Windows drivers) if necessary.

---

### Post by aimwin on 2008-07-07
> **pytheas22 said:**
> My WG111v2 definitely "just works" on Ubuntu 8.04, using the p54 driver, with WPA.  You should not need to do anything besides plug it in and click connect in Network Manager (note however that for some reason the light doesn't come on, but it still works fine).  Does that not work?  If so, please provide this information:
```

lsusb
```

and which version of Ubuntu are you using?

You can always use ndiswrapper (a utility allowing you to drive your card via Windows drivers) if necessary.

Hi pytheas22

Could you please give us more details of how do you install wg111v2 with p54 driver. It will be good if you do tutorial thread, since many of us are trying to work out this problem.

Thanks

---

### Post by Mr_FixIT on 2008-07-07
Gman035t, check out what I went through.
[http://ubuntuforums.org/showthread.php?t=838291](http://ubuntuforums.org/showthread.php?t=838291)
Need to install WG111v2 driver from CD or internet with Ndiswrapper.  There are threads out there on this site on how to do this (I've looked at so many, I've lost track or exactly which ones, sorry).
You will need to do this using the "terminal", which can be found under Applications>Accessories>Terminal
A comman-line window will open up and allow you to input various commands.
I tried the WinXP driver first (that is what the instrucitons for Ndiswrapper said to do), did not work.  Eventually used the Win98 version and it worked for an "open", no security system.  In my search, I have learned that the Win98 driver may not work with security (WPA, WEP, etc.), but have not tried yet.
Good luck,
Mr_FixIT

---

### Post by pytheas22 on 2008-07-07
> Could you please give us more details of how do you install wg111v2 with p54 driver. It will be good if you do tutorial thread, since many of us are trying to work out this problem.


There are really no details...you just install Ubuntu, plug the WG111v2 in and it works.  No driver installation of any kind is necessary.  The blue light on the stick only comes on for a second and then goes off, but don't let this bother you; the device will still work fine even with the light off.  This worked for me on two different computers running Ubuntu 8.04.

It's possible that there are different versions of WG111v2 out there that use different chipsets, meaning that what works with mine may not work with yours.  But they should all be the exact same device.  To find out, use the lsusb command.  If you see a line that looks like:
```

ID 0846:4240 NetGear, Inc. WG111 WiFi (v2)
```

then you have the exact same wireless card as me, and you should not need to do anything besides plug it in and click connect.  I know this doesn't make sense if you're coming from Windows, but there is no need to install anything before this device will work.

You can use ndiswrapper to drive this card if you want, but that shouldn't be necessary (maybe it was in earlier versions of Ubuntu).  You should only use ndiswrapper when no native Linux driver exists.  This is not the case with the WG111v2.

---

### Post by pytheas22 on 2008-07-10
Did anyone get a chance to try the WG111v2 without ndiswrapper?  I'm curious to know whether yours work or not, because as I said, I'm absolutely sure that on multiple machines with Hardy installed, all I had to do was plug mine in and it worked right away.  If others are not having the same experience, I'd like to get to the bottom of it.

---

### Post by jvin248 on 2008-07-28
I have the "other" netgear WG111v2 (lsusb = 0846:6a00) and it's definitely _not_ plug and play under 8.04.1

I'm trying the ndiswrapper route but so far unsuccessful.

I need WPA-TKIP.

I had another WG111v2 working under 6.06, but lost the notes there and am not sure it was advanced WPA capable.


J

---

### Post by pytheas22 on 2008-07-29
> I have the "other" netgear WG111v2 (lsusb = 0846:6a00) and it's definitely _not_ plug and play under 8.04.1

Alright, that explains a lot; I guess there are two different releases of the WG111v2.

[Here]("http://ubuntuforums.org/showthread.php?t=590942#6") they say that it's possible to get your version working, at least in Gutsy, so it should be possible.  If you provide the output of these commands, maybe we can figure out how to make yours work, too:
```

cat /etc/modprobe.d/blacklist
ndiswrapper -l
lshw -C Network
dmesg
```

(dmesg output will be very long, but please post it all, and make sure you've plugged in your wireless adapter before running dmesg)

Also, how far have you gotten?  Does the system recognize the wireless interface at all?  Can you scan for networks?

And are you using a 32-bit or 64-bit kernel?

---

### Post by mcgarry83 on 2008-08-08
I've been struggling with this since April. My WG111v2 worked out of the box with Hardy, just plug-n-play. The problem is that it only works for a little while, then for no apparent reason, I have no connection. Network manager however, still shows that I am connected even displays signal strength in real time. The only way to regain a true connection is to unplug the adapter and plug it back in. This however only works for a few minutes, then the never ending cycle repeats. I'm not using Ndiswrapper, I did try but had a lot of problems getting it to work properly. I never had this problem in Gutsy. Now I'm trying to find a new wifi card that works, but I would still like to get the WG11v2 problem solved. I think it has something to do with the RTL8187 driver. Im looking into it.

---

### Post by pytheas22 on 2008-08-08
> I've been struggling with this since April. My WG111v2 worked out of the box with Hardy, just plug-n-play. The problem is that it only works for a little while, then for no apparent reason, I have no connection. Network manager however, still shows that I am connected even displays signal strength in real time. The only way to regain a true connection is to unplug the adapter and plug it back in. This however only works for a few minutes, then the never ending cycle repeats. I'm not using Ndiswrapper, I did try but had a lot of problems getting it to work properly. I never had this problem in Gutsy. Now I'm trying to find a new wifi card that works, but I would still like to get the WG11v2 problem solved. I think it has something to do with the RTL8187 driver. Im looking into it.

I think all versions of the WG111v2 have prism chipsets (not Realtek/RTL8187) and use driver modules named "p54usb" and "p54common" (there's also p54pci which I assume is used for PCI cards.

If you want to try troubleshooting the card, the next time it crashes, please immediately open a terminal and type:
```

dmesg
```

and post the output here.  That will hopefully provide some clue about why it's crashing.

---

### Post by pytheas22 on 2008-08-19
I've just gotten done trying to troubleshoot crashes on my WG111v2 as well.  I blacklisted the prism drivers (p54usb, p54common) and installed the Windows driver from [here]("http://kbserver.netgear.com/release_notes/D102534.asp").  Yes, that driver is for the WG111, but it seems that Netgear did a really poor job documenting what's actually inside of the various products sold as WG111/WG111v2, and even though my card was sold as a WG111v2, it needs the WG111 Windows driver.  If you have the same card as me, the command:
```

lsusb | grep -i netgear
```

would give:
```

[...] ID 0846:4240 NetGear, Inc. WG111 WiFi (v2)
```

It seems that there are other versions of the WG111v2 floating around out there, though (apparently at least one of them uses a Realtek chipset), so if your device doesn't match mine, you need a different Windows driver to make it work in ndiswrapper.  Google your "lsusb" output to figure out which one.

With the Windows driver that I linked to above, this card seems to work reliably under ndiswrapper.

---

### Post by Bikerbob on 2008-09-08
> **pytheas22 said:**
> I've just gotten done trying to troubleshoot crashes on my WG111v2 as well.  I blacklisted the prism drivers (p54usb, p54common) and installed the Windows driver from [here]("http://kbserver.netgear.com/release_notes/D102534.asp").

pytheas22,


I thought you have the prism drivers running fine? what happened that you decided to go to ndiswrapper?


I am using a Dlink G122 A1 which is also a prismGT usb stick. I have been having my issues, and 8.0.4 does not detect mine and just run on boot either.

Just wondering.

James

---

### Post by pytheas22 on 2008-09-08
> 
I thought you have the prism drivers running fine? what happened that you decided to go to ndiswrapper

It did seem to be working fine, but it was crashing frequently (visiting certain sites seemed to trigger it).  Originally I thought that the problem was simply that my computer was far away from the router (it was), but after moving it closer, the issue continued.  When the device crashed, the only way to get it to work again was to unplug the adapter and plug it back in, or reinsert the p54 module.  Under ndiswrapper with the Windows driver linked to in my last post, I haven't had this problem so far.

An interesting thing to note is that a few years ago, when I was using this same card on Mandriva under ndiswrapper (at that time there was no native driver available), I also had weird crashing symptoms very similar to what I experienced in Ubuntu under the p54 driver.  But, again, the card does seem to work fine in Ubuntu using ndiswrapper.

If you want to try switching to ndiswrapper and need help installing, please post the output of 'lsusb' so that we can look up where to get a good Windows driver for your card.

---

### Post by Bikerbob on 2008-09-08
Well so far I have tried to get this dongle to work in linux on 2 machines with 2 different linux distros.

puppy linux and Ubuntu 8.0.4

on a C800 Dell laptop and a AMD 3000+ NF7-S computer  - The Ubuntu on the desktop as the laptop really does not have the reasources for Ubuntu.

I have yet to get it working on either.

On the laptop I can get it visable with the p54usb driver.. on the desktop it is even crashing because of IRQ conflicts.. weird.


BTW - xp on either machine and the dongle work no questions.

James

---

### Post by pytheas22 on 2008-09-08
What's the output of the command 'lsusb' when the device is plugged in?

---

### Post by Skutor on 2008-09-08
And what about a WG311v3 Card?

I've just installed Ubuntu Ultimate Edishion and do not know how i can live without internet! :-)

I maybe could install the windows drivers with wine, but without internet I CAN'T INSTALL WINE !!! ](*,)

I only can use internet in windows...

Please help me!

---

### Post by pytheas22 on 2008-09-08
> And what about a WG311v3 Card?

I've just installed Ubuntu Ultimate Edishion and do not know how i can live without internet!

I maybe could install the windows drivers with wine, but without internet I CAN'T INSTALL WINE !!!

I only can use internet in windows...

Please help me!

You can't use wine to install device drivers, as wine provides only an application compatibility layer for running Windows applications.  Driver stuff is handled at a lower level and wine doesn't support that.

If you plug your card in and post the output of:
```

lsusb
```

I'll try to help you find instructions on getting the card working.

---

### Post by Skutor on 2008-09-10
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 099a:7202 Zippy Technology Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 041e:3040 Creative Technology, Ltd 
Bus 001 Device 001: ID 0000:0000  

(I've got a Creative sound card)

---

### Post by pytheas22 on 2008-09-10
Was your wireless card plugged into the computer when you ran the 'lsusb' command?  It wasn't detected, which is a major problem and may indicate a problem with the hardware.  Does the card work in Windows?

Please unplug the card, plug it back in and then immediately post the output of:
```

dmesg | tail
lsusb
```

---

### Post by Skutor on 2008-09-10
You know, the card is build in the computer:
[IMG]http://firmware.netgear-forum.com/ntgfirm/img/produit/WG311v3_1.jpg[/IMG]
But in Windows it works.

Do I really have to extract it? (theoretically it's possible :) )

---

### Post by pytheas22 on 2008-09-10
> You know, the card is build in the computer:

Sorry, my apologies; I thought it was a USB device (because my Netgear WG111v2 is, I assumed that the v3 would be as well).  Since you have a PCI device, please post the output of this command:
```

lspci -nn
```

---

### Post by Bikerbob on 2008-09-11
Two things Skutor, if your squimish about pulling a card out of your computer, then maybe linux is not for you, 2nd this is a pci card not a usb card, so you need to do a lspci and see if we find it, but that being said.. 

IF you boot the computer up in windows and it works.. then in windows go to the properties of the device and find the driver that it is using.

You need the inf and sys that windows is using.. 


Look here.. this is the chipset you have and it should help you ..

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

---

### Post by Bikerbob on 2008-09-13
Well I got my G122 A1 working in Puppy with ndiswrapper.

Now I went back to a Kernel that did not have the p54usb modules in it.. so I did not have to blacklist anything.

So I think I should have no issues getting this working as long as I blacklist out the drivers.

I am disappointed though.. as I really like to see Linux grow, and since the p54usb has it listed right in the code that it supports this device its sad that I cant get it to work.

One interesting thing is that I noticed puppy linux looks for a different firmware when using the p54usb driver than Ubuntu does... I can get it to work somewhat in puppy .. it loads the firmware and says successful, where in ubuntu the firmware it tries to load I get a - cannot read eeprom error.

I have no idea how to tell ubuntu to load a different firmware or even if you can.

James

---

### Post by tomjennings on 2008-09-15
So it appears that there are TWO! of these miserable things... via lsusb:

GOOD ONE: ID 0846:4240 NetGear, Inc. WG111 WiFi (v2)
BAD ONE:  ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

The 4240 unit 'just works' it seems, from reports here. The 6a00 unit comes up for me, but fails when I move data through it. I am using shell wireless-tools commands to bring up the connection, so it's not network-manager issues.

If I simply ping through it, it seems to stay up "for a long time". If I attempt to move large-ish amounts of data through it, eg. apt-get upgrade that wants to fetch a kernel, it fails, repeatably, within a few minutes.

After it has failed, I can again bring it up again manually. Works the same very time.

I have Hardy Heron, netgear WG111v2 with 0846:6a00.

module rtl8187 is loaded, not p54 anything.


Here's most of my dmesg:

```

lan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 2134.943481] wlan0: deauthenticated
[ 2136.004790] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 2136.006100] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 2136.006118] wlan0: authenticated
[ 2136.006129] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 2136.204763] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 2136.206230] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 2136.206247] wlan0: deauthenticated

{lost some dmesg here}

[ 3120.074940] wlan0: authenticated
[ 3120.074951] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3120.077434] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=79)
[ 3120.077451] wlan0: associated
[ 3120.077462] printk: 1 messages suppressed.
[ 3120.077474] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 2498.316884] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 2498.316899] wlan0: deauthenticated
[ 3123.935984] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3123.938056] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3123.938073] wlan0: authenticated
[ 3123.938084] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3123.941297] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=80)
[ 3123.941312] wlan0: associated
[ 3123.941322] printk: 1 messages suppressed.
[ 3123.941334] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3124.059346] wlan0: deauthenticate(reason=3)
[ 3128.952724] wlan0: Initial auth_alg=0
[ 3128.952746] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3128.955833] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3128.955853] wlan0: authenticated
[ 3128.955864] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3128.958903] wlan0: RX AssocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=81)
[ 3128.958922] wlan0: associated
[ 3128.960014] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2518.540974] wlan0: no IPv6 routers present
[ 3158.409813] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3158.409829] wlan0: deauthenticated
[ 3159.406938] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3159.408829] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3159.408844] wlan0: authenticated
[ 3159.408855] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3159.411324] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=82)
[ 3159.411339] wlan0: associated
[ 3159.411349] printk: 3 messages suppressed.
[ 3159.411361] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3159.411374] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3160.099463] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 3162.170774] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3162.170791] wlan0: deauthenticated
[ 3163.194163] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3163.197612] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3163.197629] wlan0: authenticated
[ 3163.197639] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3163.200264] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=83)
[ 3163.200279] wlan0: associated
[ 3163.200293] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3165.957833] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3165.957850] wlan0: deauthenticated
[ 3166.955408] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3166.957000] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3166.957017] wlan0: authenticated
[ 3166.957028] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3166.959616] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=84)
[ 3166.959634] wlan0: associated
[ 3166.959650] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3169.719401] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3169.719417] wlan0: deauthenticated
[ 3170.716651] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3170.718313] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3170.718330] wlan0: authenticated
[ 3170.718341] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3170.720710] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=85)
[ 3170.720728] wlan0: associated
[ 3170.720747] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3173.496474] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3173.496490] wlan0: deauthenticated
[ 3174.493870] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3174.495492] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3174.495508] wlan0: authenticated
[ 3174.495518] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3174.497993] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=86)
[ 3174.498009] wlan0: associated
[ 3174.498024] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3177.257559] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3177.257576] wlan0: deauthenticated
[ 3178.255107] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3178.256567] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3178.256583] wlan0: authenticated
[ 3178.256594] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3178.258682] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=87)
[ 3178.258696] wlan0: associated
[ 3178.258711] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3181.019010] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3181.019027] wlan0: deauthenticated
[ 3182.016372] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3182.018019] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3182.018035] wlan0: authenticated
[ 3182.018045] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3182.020646] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=88)
[ 3182.020662] wlan0: associated
[ 3182.020678] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3184.788472] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3184.788488] wlan0: deauthenticated
[ 3185.785603] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3185.787236] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3185.787253] wlan0: authenticated
[ 3185.787264] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3185.789627] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=89)
[ 3185.789644] wlan0: associated
[ 3185.789663] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3188.577396] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3188.577413] wlan0: deauthenticated
[ 3189.574837] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3189.576660] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3189.576677] wlan0: authenticated
[ 3189.576687] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3189.579531] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=90)
[ 3189.579546] wlan0: associated
[ 3189.579560] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3192.346855] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3192.346872] wlan0: deauthenticated
[ 3193.344078] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3193.345867] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3193.345884] wlan0: authenticated
[ 3193.345895] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3193.348234] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=91)
[ 3193.348249] wlan0: associated
[ 3193.348263] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3196.108039] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3196.108056] wlan0: deauthenticated
[ 3197.105309] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3197.106936] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3197.106952] wlan0: authenticated
[ 3197.106963] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3197.109428] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=92)
[ 3197.109443] wlan0: associated
[ 3197.109457] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3199.893244] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3199.893261] wlan0: deauthenticated
[ 3200.890563] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3200.892133] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3200.892148] wlan0: authenticated
[ 3200.892159] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3200.894634] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=93)
[ 3200.894650] wlan0: associated
[ 3200.894664] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3203.662319] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3203.662335] wlan0: deauthenticated
[ 3204.659805] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3204.661709] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3204.661724] wlan0: authenticated
[ 3204.661735] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3204.664078] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=94)
[ 3204.664093] wlan0: associated
[ 3204.664107] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3207.435651] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3207.435668] wlan0: deauthenticated
[ 3208.433043] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3208.434784] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3208.434800] wlan0: authenticated
[ 3208.434811] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3208.437282] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=95)
[ 3208.437297] wlan0: associated
[ 3208.437312] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3211.196717] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3211.196734] wlan0: deauthenticated
[ 3212.194470] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3212.196244] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3212.196261] wlan0: authenticated
[ 3212.196271] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3212.198358] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=96)
[ 3212.198373] wlan0: associated
[ 3212.198387] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3214.962039] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3214.962055] wlan0: deauthenticated
[ 3215.959542] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3215.961075] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3215.961092] wlan0: authenticated
[ 3215.961103] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3215.963319] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=97)
[ 3215.963335] wlan0: associated
[ 3215.963346] printk: 1 messages suppressed.
[ 3215.963358] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3218.739362] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3218.739379] wlan0: deauthenticated
[ 3219.736770] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3219.738248] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3219.738262] wlan0: authenticated
[ 3219.738273] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3219.740863] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=98)
[ 3219.740877] wlan0: associated
[ 3222.504437] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3222.504453] wlan0: deauthenticated
[ 3223.502087] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3223.503956] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3223.503972] wlan0: authenticated
[ 3223.503982] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3223.506697] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=99)
[ 3223.506712] wlan0: associated
[ 3223.506722] printk: 3 messages suppressed.
[ 3223.506733] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3226.290803] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3226.290819] wlan0: deauthenticated
[ 3227.287249] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3227.288534] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3227.288551] wlan0: authenticated
[ 3227.288562] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3227.290652] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=100)
[ 3227.290667] wlan0: associated
[ 3227.290677] printk: 1 messages suppressed.
[ 3227.290689] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3230.047214] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3230.047230] wlan0: deauthenticated
[ 3231.044502] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3231.046245] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3231.046262] wlan0: authenticated
[ 3231.046272] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3231.048365] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=101)
[ 3231.048382] wlan0: associated
[ 3231.048394] printk: 1 messages suppressed.
[ 3231.048406] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3233.816415] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3233.816431] wlan0: deauthenticated
[ 3234.813740] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3234.815464] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3234.815482] wlan0: authenticated
[ 3234.815497] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3234.817464] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=102)
[ 3234.817482] wlan0: associated
[ 3237.645776] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3237.645793] wlan0: deauthenticated
[ 3238.643140] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3238.644794] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3238.644810] wlan0: authenticated
[ 3238.644820] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3238.647035] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=103)
[ 3238.647050] wlan0: associated
[ 3238.647060] printk: 1 messages suppressed.
[ 3238.647071] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3241.431862] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3241.431879] wlan0: deauthenticated
[ 3242.428364] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3242.429868] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3242.429885] wlan0: authenticated
[ 3242.429895] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3242.432358] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=104)
[ 3242.432372] wlan0: associated
[ 3242.432382] printk: 1 messages suppressed.
[ 3242.432394] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3245.192170] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3245.192186] wlan0: deauthenticated
[ 3246.189601] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3246.192184] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3246.192200] wlan0: authenticated
[ 3246.192210] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3246.194930] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=105)
[ 3246.194944] wlan0: associated
[ 3246.194954] printk: 1 messages suppressed.
[ 3246.194966] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3248.973256] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3248.973272] wlan0: deauthenticated
[ 3249.970878] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3249.972263] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3249.972280] wlan0: authenticated
[ 3249.972291] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3249.974756] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=106)
[ 3249.974771] wlan0: associated
[ 3252.762696] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3252.762713] wlan0: deauthenticated
[ 3253.760093] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3253.761456] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3253.761472] wlan0: authenticated
[ 3253.761483] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3253.763695] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=107)
[ 3253.763710] wlan0: associated
[ 3253.763719] printk: 3 messages suppressed.
[ 3253.763731] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3256.524157] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3256.524174] wlan0: deauthenticated
[ 3257.521341] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3257.522667] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3257.522684] wlan0: authenticated
[ 3257.522695] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3257.524653] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=108)
[ 3257.524669] wlan0: associated
[ 3257.524679] printk: 1 messages suppressed.
[ 3257.524691] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3260.281216] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3260.281233] wlan0: deauthenticated
[ 3261.278569] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3261.280353] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3261.280369] wlan0: authenticated
[ 3261.280380] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3261.282340] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=109)
[ 3261.282354] wlan0: associated
[ 3261.282369] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3264.083280] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3264.083296] wlan0: deauthenticated
[ 3265.080796] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3265.082044] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3265.082060] wlan0: authenticated
[ 3265.082070] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3265.084536] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=110)
[ 3265.084550] wlan0: associated
[ 3267.852355] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3267.852372] wlan0: deauthenticated
[ 3268.850038] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3268.851369] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3268.851385] wlan0: authenticated
[ 3268.851396] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3268.855364] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=111)
[ 3268.855379] wlan0: associated
[ 3268.855388] printk: 1 messages suppressed.
[ 3268.855400] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3271.613551] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3271.613567] wlan0: deauthenticated
[ 3272.611301] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3272.612955] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3272.612971] wlan0: authenticated
[ 3272.612982] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3272.615578] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=112)
[ 3272.615595] wlan0: associated
[ 3272.615610] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3275.379263] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3275.379280] wlan0: deauthenticated
[ 3276.376523] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3276.378397] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3276.378413] wlan0: authenticated
[ 3276.378423] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3276.380638] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=113)
[ 3276.380652] wlan0: associated
[ 3276.380666] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3279.140453] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3279.140469] wlan0: deauthenticated
[ 3280.137764] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3280.139594] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3280.139609] wlan0: authenticated
[ 3280.139620] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3280.141962] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=114)
[ 3280.141976] wlan0: associated
[ 3282.909659] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3282.909676] wlan0: deauthenticated
[ 3283.906990] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3283.908665] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3283.908681] wlan0: authenticated
[ 3283.908692] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3283.911162] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=115)
[ 3283.911177] wlan0: associated
[ 3283.911186] printk: 1 messages suppressed.
[ 3283.911198] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3286.714854] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3286.714871] wlan0: deauthenticated
[ 3287.712248] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3287.713878] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3287.713894] wlan0: authenticated
[ 3287.713905] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3287.716122] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=116)
[ 3287.716138] wlan0: associated
[ 3287.716152] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3290.476304] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3290.476320] wlan0: deauthenticated
[ 3291.473507] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3291.475709] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3291.475726] wlan0: authenticated
[ 3291.475736] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3291.477828] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=117)
[ 3291.477845] wlan0: associated
[ 3291.477861] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 2635.740346] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 2635.740361] wlan0: deauthenticated
[ 2636.737524] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 2636.739047] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 2636.739063] wlan0: authenticated
[ 2636.739071] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 2636.741284] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=118)
[ 2636.741297] wlan0: associated
[ 3299.111509] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3299.111526] wlan0: deauthenticated
[ 3300.109201] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3300.111024] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3300.111040] wlan0: authenticated
[ 3300.111051] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3300.114296] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=119)
[ 3300.114314] wlan0: associated
[ 3300.114326] printk: 2 messages suppressed.
[ 3300.114337] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3302.878136] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3302.878156] wlan0: deauthenticated
[ 3303.878458] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3303.879853] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3303.879869] wlan0: authenticated
[ 3303.879880] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3303.881969] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=120)
[ 3303.881986] wlan0: associated
[ 3303.881996] printk: 1 messages suppressed.
[ 3303.882008] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3306.697899] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3306.697915] wlan0: deauthenticated
[ 3307.696922] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3307.699085] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3307.699103] wlan0: authenticated
[ 3307.699113] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3307.701784] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=121)
[ 3307.701803] wlan0: associated
[ 3307.701814] printk: 1 messages suppressed.
[ 3307.701826] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3310.559347] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3310.559363] wlan0: deauthenticated
[ 3311.556922] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3311.558240] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3311.558256] wlan0: authenticated
[ 3311.558267] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3311.560602] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=122)
[ 3311.560616] wlan0: associated
[ 3314.316546] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3314.316563] wlan0: deauthenticated
[ 3315.314144] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3315.315939] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3315.315955] wlan0: authenticated
[ 3315.315966] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3315.318171] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=123)
[ 3315.318185] wlan0: associated
[ 3315.318194] printk: 3 messages suppressed.
[ 3315.318206] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3318.082252] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3318.082269] wlan0: deauthenticated
[ 3319.079384] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3319.081137] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3319.081152] wlan0: authenticated
[ 3319.081163] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3319.083380] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=124)
[ 3319.083395] wlan0: associated
[ 3319.083404] printk: 1 messages suppressed.
[ 3319.083416] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3321.855078] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3321.855095] wlan0: deauthenticated
[ 3322.852645] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3322.854350] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3322.854368] wlan0: authenticated
[ 3322.854379] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3322.856473] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=125)
[ 3322.856490] wlan0: associated
[ 3322.856501] printk: 1 messages suppressed.
[ 3322.856513] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3325.616895] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3325.616911] wlan0: deauthenticated
[ 3326.613860] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3326.615783] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3326.615799] wlan0: authenticated
[ 3326.615810] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3326.618280] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=126)
[ 3326.618295] wlan0: associated
[ 3329.428733] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3329.428749] wlan0: deauthenticated
[ 3330.426146] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3330.427406] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3330.427423] wlan0: authenticated
[ 3330.427434] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3330.429784] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=127)
[ 3330.429801] wlan0: associated
[ 3330.429813] printk: 3 messages suppressed.
[ 3330.429828] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3333.245945] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3333.245962] wlan0: deauthenticated
[ 3334.243385] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3334.244697] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3334.244713] wlan0: authenticated
[ 3334.244724] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3334.246684] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=128)
[ 3334.246699] wlan0: associated
[ 3334.246709] printk: 2 messages suppressed.
[ 3334.246721] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3337.003372] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3337.003389] wlan0: deauthenticated
[ 3338.000606] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3338.002015] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3338.002030] wlan0: authenticated
[ 3338.002040] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3338.004131] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=129)
[ 3338.004145] wlan0: associated
[ 3338.004159] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3340.772598] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3340.772615] wlan0: deauthenticated
[ 3341.769868] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3341.771602] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3341.771619] wlan0: authenticated
[ 3341.771630] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3341.774100] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=130)
[ 3341.774117] wlan0: associated
[ 3344.577648] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3344.577664] wlan0: deauthenticated
[ 3345.575115] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3345.576936] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3345.576954] wlan0: authenticated
[ 3345.576965] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3345.578944] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=131)
[ 3345.578961] wlan0: associated
[ 3345.578972] printk: 1 messages suppressed.
[ 3345.578987] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3348.338847] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3348.338864] wlan0: deauthenticated
[ 3349.336339] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3349.337993] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3349.338010] wlan0: authenticated
[ 3349.338020] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3349.340105] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=132)
[ 3349.340120] wlan0: associated
[ 3349.340134] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3352.104307] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3352.104323] wlan0: deauthenticated
[ 3353.121587] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3353.123327] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3353.123345] wlan0: authenticated
[ 3353.123355] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3353.125443] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=133)
[ 3353.125460] wlan0: associated
[ 3353.125477] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3356.013478] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3356.013495] wlan0: deauthenticated
[ 2685.673425] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 2685.675220] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 2685.675235] wlan0: authenticated
[ 2685.675243] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 2685.677757] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=134)
[ 2685.677772] wlan0: associated
[ 3360.153101] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3360.153118] wlan0: deauthenticated
[ 3361.150784] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3361.152647] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3361.152665] wlan0: authenticated
[ 3361.152675] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3361.155006] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=135)
[ 3361.155023] wlan0: associated
[ 3361.155034] printk: 1 messages suppressed.
[ 3361.155046] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 2691.460980] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 2691.460995] wlan0: deauthenticated
[ 2692.458557] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 2692.460102] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 2692.460116] wlan0: authenticated
[ 2692.460125] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 2692.462220] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=136)
[ 2692.462234] wlan0: associated
[ 2692.462248] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3368.551222] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3368.551239] wlan0: deauthenticated
[ 3369.548477] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3369.550253] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3369.550271] wlan0: authenticated
[ 3369.550282] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3369.552602] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=137)
[ 3369.552619] wlan0: associated
[ 3369.552634] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3372.368414] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3372.368431] wlan0: deauthenticated
[ 3373.386155] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3373.387882] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3373.387898] wlan0: authenticated
[ 3373.387909] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3373.390007] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=138)
[ 3373.390022] wlan0: associated
[ 3373.390037] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3376.185813] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3376.185829] wlan0: deauthenticated
[ 3377.183397] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3377.184953] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3377.184968] wlan0: authenticated
[ 3377.184979] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3377.187571] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=139)
[ 3377.187585] wlan0: associated
[ 3379.982639] printk: 1 messages suppressed.
[ 3379.982660] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3379.984900] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3379.984915] wlan0: deauthenticated
[ 3381.004651] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3381.005907] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3381.005923] wlan0: authenticated
[ 3381.005934] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3381.008271] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=140)
[ 3381.008284] wlan0: associated
[ 3383.772335] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3383.772352] wlan0: deauthenticated
[ 3384.769890] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3384.772099] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3384.772115] wlan0: authenticated
[ 3384.772125] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3384.774743] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=141)
[ 3384.774760] wlan0: associated
[ 3384.774771] printk: 2 messages suppressed.
[ 3384.774783] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3387.541410] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3387.541427] wlan0: deauthenticated
[ 3388.556126] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3388.557807] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3388.557823] wlan0: authenticated
[ 3388.557833] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3388.560427] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=142)
[ 3388.560441] wlan0: associated
[ 3388.560451] printk: 1 messages suppressed.
[ 3388.560463] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3391.375613] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3391.375630] wlan0: deauthenticated
[ 3392.417309] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3392.419164] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3392.419178] wlan0: authenticated
[ 3392.419189] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3392.421657] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=143)
[ 3392.421669] wlan0: associated
[ 3395.252742] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3395.252758] wlan0: deauthenticated
[ 3396.250567] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3396.252274] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3396.252292] wlan0: authenticated
[ 3396.252303] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3396.254385] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=144)
[ 3396.254402] wlan0: associated
[ 3396.254414] printk: 3 messages suppressed.
[ 3396.254425] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3399.058550] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3399.058566] wlan0: deauthenticated
[ 3400.055790] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3400.057564] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3400.057579] wlan0: authenticated
[ 3400.057590] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3400.060810] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=145)
[ 3400.060824] wlan0: associated
[ 3400.060834] printk: 1 messages suppressed.
[ 3400.060845] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3402.827503] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3402.827519] wlan0: deauthenticated
[ 3403.825035] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3403.826500] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3403.826514] wlan0: authenticated
[ 3403.826525] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3403.829123] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=146)
[ 3403.829137] wlan0: associated
[ 3403.829147] printk: 1 messages suppressed.
[ 3403.829158] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3406.588947] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3406.588963] wlan0: deauthenticated
[ 3407.586266] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3407.587976] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3407.587992] wlan0: authenticated
[ 3407.588003] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3407.590970] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=147)
[ 3407.590985] wlan0: associated
[ 3410.402155] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3410.402171] wlan0: deauthenticated
[ 3411.399544] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3411.401559] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3411.401577] wlan0: authenticated
[ 3411.401588] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3411.404703] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=148)
[ 3411.404721] wlan0: associated
[ 3411.404737] printk: 3 messages suppressed.
[ 3411.404749] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3414.179495] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3414.179512] wlan0: deauthenticated
[ 3415.196757] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3415.198118] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3415.198135] wlan0: authenticated
[ 3415.198145] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3415.200612] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=149)
[ 3415.200628] wlan0: associated
[ 3415.200639] printk: 1 messages suppressed.
[ 3415.200651] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3417.961052] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3417.961068] wlan0: deauthenticated
[ 3418.957987] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3418.959817] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3418.959834] wlan0: authenticated
[ 3418.959845] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3418.962313] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=150)
[ 3418.962330] wlan0: associated
[ 3418.962341] printk: 1 messages suppressed.
[ 3418.962353] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3421.733747] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3421.733764] wlan0: deauthenticated
[ 3422.731242] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3422.733651] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3422.733669] wlan0: authenticated
[ 3422.733680] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3422.736641] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=151)
[ 3422.736658] wlan0: associated
[ 3425.588215] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3425.588231] wlan0: deauthenticated
[ 3426.588492] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3426.590083] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3426.590099] wlan0: authenticated
[ 3426.590109] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3426.592451] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=152)
[ 3426.592483] wlan0: associated
[ 3426.592493] printk: 1 messages suppressed.
[ 3426.592505] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3429.356016] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3429.356033] wlan0: deauthenticated
[ 3430.390728] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3430.392537] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3430.392553] wlan0: authenticated
[ 3430.392563] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3430.395407] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=153)
[ 3430.395423] wlan0: associated
[ 3430.395437] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3433.154575] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3433.154591] wlan0: deauthenticated
[ 3434.151979] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3434.153230] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3434.153246] wlan0: authenticated
[ 3434.153256] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3434.155839] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=154)
[ 3434.155853] wlan0: associated
[ 3434.155867] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3436.919675] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3436.919692] wlan0: deauthenticated
[ 3437.917220] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3437.918947] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3437.918965] wlan0: authenticated
[ 3437.918975] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3437.923583] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=155)
[ 3437.923601] wlan0: associated
[ 3440.744850] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3440.744866] wlan0: deauthenticated
[ 3441.767420] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3441.768984] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3441.769000] wlan0: authenticated
[ 3441.769011] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3441.771852] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=156)
[ 3441.771867] wlan0: associated
[ 3441.771877] printk: 1 messages suppressed.
[ 3441.771889] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3444.541310] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3444.541327] wlan0: deauthenticated
[ 3445.540678] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3445.542443] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3445.542460] wlan0: authenticated
[ 3445.542470] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3445.544680] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=157)
[ 3445.544695] wlan0: associated
[ 3445.544709] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3448.304368] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3448.304385] wlan0: deauthenticated
[ 3449.301910] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3449.303365] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3449.303379] wlan0: authenticated
[ 3449.303389] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3449.305735] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=158)
[ 3449.305748] wlan0: associated
[ 3449.305757] printk: 1 messages suppressed.
[ 3449.305769] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3452.065564] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3452.065580] wlan0: deauthenticated
[ 3453.063137] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3453.064687] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3453.064701] wlan0: authenticated
[ 3453.064711] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3453.067683] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=159)
[ 3453.067696] wlan0: associated
[ 3455.826775] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3455.826792] wlan0: deauthenticated
[ 3456.824395] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3456.826298] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3456.826315] wlan0: authenticated
[ 3456.826326] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3456.829048] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=160)
[ 3456.829065] wlan0: associated
[ 3456.829077] printk: 3 messages suppressed.
[ 3456.829089] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3459.607843] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3459.607859] wlan0: deauthenticated
[ 3460.605620] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3460.607236] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3460.607252] wlan0: authenticated
[ 3460.607263] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3460.609852] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=161)
[ 3460.609867] wlan0: associated
[ 3460.609877] printk: 1 messages suppressed.
[ 3460.609888] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3463.401247] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3463.401264] wlan0: deauthenticated
[ 3464.398698] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3464.400403] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3464.400420] wlan0: authenticated
[ 3464.400431] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3464.402502] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=162)
[ 3464.402519] wlan0: associated
[ 3464.402530] printk: 1 messages suppressed.
[ 3464.402542] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3467.208423] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3467.208439] wlan0: deauthenticated
[ 3468.205920] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3468.207185] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3468.207200] wlan0: authenticated
[ 3468.207211] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3468.209674] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=163)
[ 3468.209689] wlan0: associated
[ 3470.994361] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3470.994378] wlan0: deauthenticated
[ 3471.992156] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3471.993878] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3471.993894] wlan0: authenticated
[ 3471.993904] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3471.995866] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=164)
[ 3471.995880] wlan0: associated
[ 3471.995890] printk: 3 messages suppressed.
[ 3471.995902] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3474.775690] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3474.775706] wlan0: deauthenticated
[ 3475.793394] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3475.794835] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3475.794852] wlan0: authenticated
[ 3475.794863] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3475.797819] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=165)
[ 3475.797834] wlan0: associated
[ 3475.797848] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3478.561384] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3478.561400] wlan0: deauthenticated
[ 3479.558644] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3479.560408] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3479.560424] wlan0: authenticated
[ 3479.560435] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3479.563279] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=166)
[ 3479.563296] wlan0: associated
[ 3479.563311] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3482.354697] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3482.354714] wlan0: deauthenticated
[ 3483.351868] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3483.353718] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3483.353734] wlan0: authenticated
[ 3483.353745] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3483.356225] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=167)
[ 3483.356241] wlan0: associated
[ 3486.115776] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3486.115792] wlan0: deauthenticated
[ 3487.113102] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3487.115042] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3487.115058] wlan0: authenticated
[ 3487.115068] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3487.119413] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=168)
[ 3487.119427] wlan0: associated
[ 3487.119437] printk: 1 messages suppressed.
[ 3487.119449] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 2791.949305] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 2791.949319] wlan0: deauthenticated
[ 3490.982554] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3490.984057] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3490.984074] wlan0: authenticated
[ 3490.984085] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3490.987060] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=169)
[ 3490.987077] wlan0: associated
[ 3490.987093] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3493.913301] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3493.913317] wlan0: deauthenticated
[ 3494.910862] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3494.912323] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3494.912341] wlan0: authenticated
[ 3494.912352] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3494.915179] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=170)
[ 3494.915193] wlan0: associated
[ 3494.915202] printk: 1 messages suppressed.
[ 3494.915214] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3497.724601] wlan0: RX deauthentication from 00:0f:24:f1:7e:20 (reason=2)
[ 3497.724617] wlan0: deauthenticated
[ 3498.722084] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3498.723628] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3498.723644] wlan0: authenticated
[ 3498.723655] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3498.726248] wlan0: RX ReassocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=171)
[ 3498.726262] wlan0: associated
[ 3499.601029] wlan0: deauthenticate(reason=3)
[ 3506.220716] wlan0: No ProbeResp from current AP 00:0f:24:f1:7e:20 - assume out of range
[ 3506.398232] wlan0: Initial auth_alg=0
[ 3506.398253] wlan0: authenticate with AP 00:0f:24:f1:7e:20
[ 3506.400447] wlan0: RX authentication from 00:0f:24:f1:7e:20 (alg=0 transaction=2 status=0)
[ 3506.400465] wlan0: authenticated
[ 3506.400476] wlan0: associate with AP 00:0f:24:f1:7e:20
[ 3506.403212] wlan0: RX AssocResp from 00:0f:24:f1:7e:20 (capab=0x421 status=0 aid=172)
[ 3506.403230] wlan0: associated
[ 3506.403241] printk: 3 messages suppressed.
[ 3506.403253] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3506.403266] wlan0: switched to short barker preamble (BSSID=00:0f:24:f1:7e:20)
[ 3506.404107] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3525.904344] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 2823.022606] wlan0: no IPv6 routers present
[ 3557.888266] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3578.225207] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 3593.558698] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3613.688985] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 3638.538978] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 2927.246307] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 2965.918166] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3037.585889] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 3797.211664] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 3087.580526] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 4035.163535] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 4055.137977] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 4083.785828] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 4140.150044] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 4150.424820] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 4188.259189] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 4271.466228] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 4322.987207] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 4328.282419] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 4352.566217] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 4373.530784] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 4450.385995] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 4456.549268] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 4476.891392] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 4486.266271] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 4537.320181] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 4595.676295] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 4624.045429] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 3802.928176] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 4773.214682] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 4833.184024] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 4853.175068] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 4858.052616] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 4888.899379] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 4899.357922] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 4974.502403] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 4993.098472] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 5043.237116] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 5072.072010] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)
[ 5092.548023] wlan0: CTS protection disabled (BSSID=00:0f:24:f1:7e:20)
[ 5097.785976] wlan0: CTS protection enabled (BSSID=00:0f:24:f1:7e:20)


```

---

### Post by pytheas22 on 2008-09-15
tomjennings,

Thanks for finally clearing up that there are two distinct versions of this device, and giving the PCI IDs of each.  Mine is the "Good" one (although it also has its share of problems), but I did look into the problems you have with yours as well.

This [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182473") deals with issues that may be related to yours on the rtl8187 driver.  Unfortunately there's no real solution there that I found, although I didn't read the whole thing, and people are still reporting the problem under the Intrepid alpha release.

Have you tried using ndiswrapper instead of rtl8187 to drive your card?  I suspect that it would work better.

---

### Post by sennep on 2008-09-19
Some people still report getting the "bad" 0846:6a00 working though.

In [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225851") bugreport Willem says that using Wicd or a PPA of network manager solved his problem.

Also, Thomazian reports [here]("http://ubuntuforums.org/showthread.php?t=892270&highlight=wg111v2#5") that using iwconfig to reduce the speed to 11M auto worked for him.

---

