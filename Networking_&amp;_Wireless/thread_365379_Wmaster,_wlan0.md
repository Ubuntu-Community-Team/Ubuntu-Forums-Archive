---
title: "Wmaster, wlan0?"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by TFrog on 2007-02-19
I just re-installed Feisty again after a ndiswrapper fiasco.  They still haven't gotten ndiswrapper working with Kubuntu 7.04 :(  Yes, I tried both 1.9 and 1.1 versions of ndiswrapper.  No go.  I even tried to compile ndiswrapper 1.37 from source.  Multiple errors from that compilation and no install :(  Actually I wouldn't say the ndiswrapper 1.9 or 1.1 fail to work.  It's they fail to connect :(  So now I did a fresh install of Feisty.  I'd read where the Broadcom 43xx cards would work out of the box on 7.04.  Well, I'm on Edgy writting this with a question about Herd 4 to get my networking working.  When I pull up System Settings/Network Settings, I see two devices in there besides my "wired" lan.  I see a Wmaster and a wlan0.  WTF?  So I set both to DHCP and rebooted to see if it would work.  No wireless.  Can someone help?  Though not new to Kubuntu, I'm lost on this one.  Any help would be greatly appreciated.

---

### Post by Tichondrius on 2007-02-19
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

I have feisty (64 bit) and got ndiswrapper working for my Dell 1390 wireless card.
I haven't tried using ndiswrapper from the repository. I just compiled from source. Compiling from source is simple, you just need the kernel headers and build tools.

After installing it you need to prevent the broadcom module from loading by adding it to the blacklist file. Also you need to load ndiswrapper module. At that point you should be able to scan for wireless networks (using iwlist command) and connect with the appropriate settings (mode/essid/wep key).

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

---

### Post by TFrog on 2007-02-20
> **Tichondrius said:**
> [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

I have feisty (64 bit) and got ndiswrapper working for my Dell 1390 wireless card.
I haven't tried using ndiswrapper from the repository. I just compiled from source. Compiling from source is simple, you just need the kernel headers and build tools.

After installing it you need to prevent the broadcom module from loading by adding it to the blacklist file. Also you need to load ndiswrapper module. At that point you should be able to scan for wireless networks (using iwlist command) and connect with the appropriate settings (mode/essid/wep key).

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

This may have worked for you but, on my Compaq R4125US all versions of ndiswrapper fail.  The versions on the install disc (1.1 and 1.9) load and unload the drivers fine.  They just fail to connect.  Had errors compiling source code for ndiswrapper project version 1.37 and failed to load.  Assistance was asked for at lauchpad and was informed to report this as a bug.  This fails not only in Feisty Fawn but also with Edgy Eft all kernels.  Besides, that wasn't the intended point of this thread to begin with.  I'm curious as to why I show two wireless devices in a fresh install of Feisty.  One labeled Wmaster0 and one Wlan0.

---

### Post by spd106 on 2007-02-20
They've tried to pull the new Devicescape stack into Feisty's kernel, that's where it came from. It's a bit too soon for it though, so it'll probably be removed before release.

As you've seen it's a bit broken at the moment.

Let's try to keep these discussions to the Feisty forum until it's released.

---

### Post by TFrog on 2007-02-20
> **spd106 said:**
> They've tried to pull the new Devicescape stack into Feisty's kernel, that's where it came from. It's a bit too soon for it though, so it'll probably be removed before release.

As you've seen it's a bit broken at the moment.

Let's try to keep these discussions to the Feisty forum until it's released.

Here here!  I'm all for moving my own thread to the Feisty Forum as I just noted it on the main forum page.  As to too soon for the Devicescape stack, I quite frankly would like to see a distro pull it off.  Ubuntu would be a perfect candidate since it's one of the most popular distro's.  Only problem there is would be manufacturer support for the Devicescape stack.

Again, if a moderator wishes, I'm all for this being moved to the Feisty Forum.

---

### Post by Tichondrius on 2007-02-21
> **TFrog said:**
> This may have worked for you but, on my Compaq R4125US all versions of ndiswrapper fail.  The versions on the install disc (1.1 and 1.9) load and unload the drivers fine.  They just fail to connect.  Had errors compiling source code for ndiswrapper project version 1.37 and failed to load.  Assistance was asked for at lauchpad and was informed to report this as a bug.  This fails not only in Feisty Fawn but also with Edgy Eft all kernels.  Besides, that wasn't the intended point of this thread to begin with.  I'm curious as to why I show two wireless devices in a fresh install of Feisty.  One labeled Wmaster0 and one Wlan0.

So let me understand, ndiswrapper is working correctly for you ("ndiswrapper -l" shows driver loaded etc) ?

If so, do you get a list of wireless networks with iwlist command ?

---

### Post by TFrog on 2007-02-22
> **Tichondrius said:**
> So let me understand, ndiswrapper is working correctly for you ("ndiswrapper -l" shows driver loaded etc) ?

If so, do you get a list of wireless networks with iwlist command ?

Yes, ndiswrapper is working for me and not the one on the installation disc.  I had to submit a bug report via launchpad.  The developers contacted me once they recompiled the 1.9 ndiswrapper using source code version 1.30.  I'm happily writing this to you from Feisty.  Now I'm on to other issues to find fixes for in Feisty.

---

### Post by kosson on 2007-02-23
Please, share with us !
Thanks for hope...

---

### Post by TFrog on 2007-02-24
For all of those that haven't gotten their Broadcom 4318 to work with ndiswrapper and Fiesty you can get the latest ndiswrapper here if you can't connect through Fiesty.  At least you can download it off a Winbloze machine and copy it over to the Linux partition that way unless of course you got Fiesty to read/write NTFS.  The site for the download is:

[https://bugs.launchpad.net/ubuntu/feisty/i386/ndiswrapper-utils-1.9/1.30-1ubuntu1](https://bugs.launchpad.net/ubuntu/feisty/i386/ndiswrapper-utils-1.9/1.30-1ubuntu1)

**MAKE SURE YOU ALSO HAVE NDISWRAPPER-COMMON INSTALLED OR THIS WON'T WORK!**

---

