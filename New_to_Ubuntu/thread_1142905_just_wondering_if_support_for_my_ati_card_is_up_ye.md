---
title: "just wondering if support for my ati card is up yet for jaunty"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by libihero on 2009-04-29
here is what happens when i put in "lspci"
```

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
```
I had a real bad experience with jaunty, since i had no drivers for my graphics card, a lot of the compiz ran extremely slow.  so i was just wondering if a stable open source driver has come out yet, or where/how i can check if it has.

---

### Post by LowSky on 2009-04-29
use the live CD, its the best test

I do know that AMD/ATi said they are only going to support newer cards, but I don't remebr what that cutoff was.. As for the open source driver, I hear its gotten better, but you said it didn't work well with Jaunty so I don't know. 

Personally I think too many people say the "need" compiz. Even for my own personal use Compiz is only on my desktop, as I dont find much use for it. I guess I'm a simple guy. On my netbook, my other backup laptop, and my soon to be media PC I dont even use desktop effect, they just get in the way or take up too much resources for me to want them.

---

### Post by Didius Falco on 2009-04-29
Not yet. If you keep on eye on the forums, believe me, you'll know. Besides, it will come through the Update Manager automatically.

---

### Post by libihero on 2009-04-29
would it show on my 8.10 update manager even tho i have the fglrx driver already?  ya i kno some people use the compiz just for wiggly windows, but the tabbing windows together, different types of window selectors, and assigning corners made it so that using a computer without it for me is unbearable haha

---

### Post by markbuntu on 2009-04-29
No proprietary driver for you in Jaunty and your x1200 and there never will be. The open source ati driver has full 2D acceleration and 3D support for that card so you don't need fglrx.

Be sure to remove fglrx before upgrading or you will have difficulties.

---

### Post by dmaxel on 2009-04-29
Is there any open source drivers for the ATI Radeon HD 2600 XT? I am getting sick of problems with Google Earth when I use the proprietary drivers. The screen keeps flickering at a high pace, and if I turn the drivers off, then it's better, but REALLY slow.

---

### Post by Duskao on 2009-04-29
Yeah, sorry for the bad news, but Ati has dropped support for your graphics processor. Either stick with 8.10 or use the open source drivers with 9.04 or if you want (like me) pick up a new video card that is supported. It's a shame that your video card like mine (radeon x1950 pro) was dropped and put into the legacy bin, but it helps free up resources for new drivers with new video cards. So it is a bit of a catch 22 at this point because with the new 9.04 you can't even use the 9.3 drivers from Ati because Ubuntu 9.04 doesn't support them and you can't use 9.4 drivers because Ati dropped support for your card. If you want to be able to use your graphics processor for gaming in more then an extremely basic 3d way or 2d way then you will have to stick with an older ubuntu or upgrade the graphics processor. 

On the up side, prices for new video cards are pretty decent for good cards. If you don't know much about video cards and want the best for your money just ask. As for the battle between Ati and Nvidia... Well to sum it up. 
Short term = Nvidia
Long term = Ati (because they are going to be releasing their drivers to the open source community)

---

### Post by libihero on 2009-04-29
lol well i dont use my laptop for gaming, so i wouldnt wanna buy a new one.  where can i get instructions for downloading the open source driver?  and is it free from most bugs?
what sucks the most is i just got this laptop this summer :(

---

### Post by markbuntu on 2009-04-30
The open source driver is included in the upgrade and will automatically install and configure itself so don't worry about that.

Both the ati and radeon open source drivers are vastly improved over the ones available in Hardy and Intrepid and should work without any problems for all RV200-RV500 series cards including accelerated 2D and full 3D support. This meand that any card before the HD3xxx series should work OOB in Jaunty with no need for a driver from ati.

Don't feel so bad, ati dropped support for those cards from their windows drivers too and there is no open source driver available at all for windows. According to ATI any operating system from Feb 2009 on will not get new drivers for these cards. I wonder if that includes windows 7?

---

### Post by Niniel on 2009-04-30
Could be.
I have an X800 XT card (R430 I believe) and I'm currently running Catalyst 9.2 in Windows XP SP3. 9.3 gave me big problems, so I had to get rid of it and install 9.2 instead.
For my card, the ati (free) driver works very well in Ubuntu. The upgrade process also managed to get rid of the fglrx driver completely. I found a guide here in the forums to remove it, and it turned out it was all gone already.

---

### Post by Mortus Pryde on 2009-04-30
I found savear 3D performance issues with the open sourse drivers for my Radeon Mobility 9600 in Jaunty, so I went back to Intrepid and used the AMD driver.

---

### Post by Niniel on 2009-04-30
Funny, on my laptop with a Radeon Mobility 9600 card, it works very well.

---

### Post by kernel_script on 2009-04-30
I have a ATI Radeon 9600PRO, it's true that ATI dropped support for it? :(

[COLOR="Red"]EDIT[/COLOR]
Yes [it's true]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English") :(

---

### Post by libihero on 2009-05-19
just checkin up again.... i dunno how to tell if the open source drivers are ready, or if they're any good for that matter

---

### Post by Mark Phelps on 2009-05-20
> **libihero said:**
> just checkin up again.... i dunno how to tell if the open source drivers are ready, or if they're any good for that matter

If you have any video at all, you're either running the open source drivers or you installed the restricted drivers.  Since there are no restricted drivers in 9.04 for your video card, you're running the open source.

As to the comment about Catalyst versions, there is no version that will run on 9.04 that supports your card.  The latest that DOES work with your card is either 9.2 or 9.3, and neither work with the Xorg version in 9.04.  Only version 9.4 and newer work -- and they don't support your card.

---

### Post by libihero on 2009-05-20
O i havent upgraded to jaunty yet, i'm still running 8.10.  i didnt want to upgrade until the open source drivers were running well.

---

### Post by Mark Phelps on 2009-05-20
> **libihero said:**
> O i havent upgraded to jaunty yet, i'm still running 8.10.  i didnt want to upgrade until the open source drivers were running well.
Don't know exactly what you mean by "running well", but I'm using open source with an ATI X1600 (for the first time since 7.04), and for 2D graphics, videos and DVDs, the performance is fine -- no lag, no stutter, no tearing. 

But, don't use Wine and don't do any 3D gaming, so don't know about performance there.

---

### Post by MrWES on 2009-05-20
> **markbuntu said:**
> The open source driver is included in the upgrade and will automatically install and configure itself so don't worry about that.

Both the ati and radeon open source drivers are vastly improved over the ones available in Hardy and Intrepid and should work without any problems for all RV200-RV500 series cards including accelerated 2D and full 3D support. This meand that any card before the HD3xxx series should work OOB in Jaunty with no need for a driver from ati.

Don't feel so bad, ati dropped support for those cards from their windows drivers too and there is no open source driver available at all for windows. According to ATI any operating system from Feb 2009 on will not get new drivers for these cards. I wonder if that includes windows 7?

True enough; I have an older ATI video card in my Dell D600 laptop:
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)

```
It works very well with Jaunty, and I even got visual effects to enable, but I needed to change the acceleration from the default EFX to XAA in xorg.conf
```
Section "Device"
	Identifier	"Configured Video Device"
	Option          "AccelMethod"   "XAA"

```

Bill

---

### Post by libihero on 2009-05-20
would that work with Radeon X1200?
i tried jaunty RC and it ran MUCH slower on my compiz

---

### Post by dazman19 on 2009-05-20
yea i had to blow jaunty off my notebook. I just use it for windows apps now. I got Jaunty on my desktop now, thats got an nVidia card. I must say Compiz/Fusion is vnice to have.

Answer to your question is no support yet from ATI. I would keep my eye out for an open source option, or go back to version 8. 

Even if the open source version pops up, it may not work as well as a manufacturer specified driver. ATI wont ever release this now that they have dropped support, and its recession year, i am assuming thats why we have lost support on the x1XXX cards already.

---

### Post by markbuntu on 2009-05-20
I think a lot of people do not understand what ati is up to. ATI is moving towards full open source drivers. The proprietary drivers will be only for the most recent cards that do not have full open source driver support. As the open source drivers fully support cards, they will be dropped from the proprietary driver.

ATI has released all the information it can about its cards to support open source drivers. It has full time employees working on the open source drivers and supports others in their open source driver efforts with information, support, and money.

This is actually a good thing. Open source means open code and more people fixing bugs and providing improvements in a faster moving environment. Over the past year or so we have been in a transition period for RV200-500 cards as accelerated 2D and 3D were introduced in the ati and radeon drivers. 

Many distributions including Ubuntu do not provide regular updates for these drivers so new versions only become available with distribution upgrades. So much progress has been made with the ati and radeon drivers over the past year that they work better for many cards than the fglrx driver ever did, particularly the x1200-x1600 series.

So, if you have and RV200-500 card, do not automatically think that you need a proprietary driver, you don't. And don't think you are getting screwed because you can't use the 9.4 driver, be glad you don't have to deal with all its problems, and they are a lot.

Performance of the open source drivers is already very good and is rapidly improving. RV600-700 3D should be out in a few months. I am waiting for this for my HD3650 card. fglrx has been a PITA for me and I will be glad to be rid of it.

---

### Post by libihero on 2009-05-20
are the open source drivers automatically downloaded when upgrading to 9.04?  i tried upgrading it and the compiz was horribly slow.  did i not download the drivers?

---

### Post by MrWES on 2009-05-21
> **libihero said:**
> would that work with Radeon X1200?
i tried jaunty RC and it ran MUCH slower on my compiz

Worth a try, no? It's a simple change, so putting it back the way it was wouldn't be too difficult.

~Bill

---

### Post by libihero on 2009-05-21
lol isnt it almost impossible to downgrade?  i tried 9.04 and i had to redownload 8.10.  i dont wanna upgrade to 9.04 unless i kno for sure the open source drivers are good enough to handle compiz at least, i dont need gaming.

---

### Post by Didius Falco on 2009-05-21
If you have a spare 10-15 gigs of space on your hard drive (you could get away with less, but I like a little breathing room), just install 9.04 by itself, without touching your 8.04 setup.

That way you can test the 9.04 and still have your 8.10 setup as a fall-back position.

Another option would be to download ReMasterSys (there is a link in my signature) and use it to make a complete, installable backup of your 8.10 setup to CD/DVD before you upgrade to 9.04.

In your case, I think I'd recommend the dual install, though ReMasterSys is now a permanent addition to my toolkit for backup and tinkering with my own Live CD Recovery Kit CD.

Regards,

Didius

---

### Post by libihero on 2009-05-22
ok i made a seperate partition with 9.04.... so how do i get the open source drivers?

---

### Post by markbuntu on 2009-05-22
The open source drivers are part of the install and are automatically loaded and configured for you in Jaunty. You can check the /var/log/Xorg.0.log to see what driver is loaded and what options it is using.

---

### Post by Didius Falco on 2009-05-22
> **libihero said:**
> ok i made a seperate partition with 9.04.... so how do i get the open source drivers?

The Open Source driver would already be installed, as part of the normal installation.

If you go into Synaptic Package Manager and search for "ati" you'll see the "xserver-xorg-video-ati" package installed, along with whatever package it determined you'd need for your particular card - ATI Mach64, Rage128, Radeon and FireGL series cards.

As long as you keep using that driver, any updates to it will be automatically sent to you as part of the regular Update Manager updates.

Believe me, you'll know when 3d support hits the Open Source driver. There'll be plenty of threads about it, and more than likely, an official announcement about it.

Meanwhile, you get the best of both worlds - 8.10 with 3D and a chance to play around with 9.04. ;)

Regards,

Didius

---

### Post by markbuntu on 2009-05-22
3D support is already implemented in the open source ati, radeon, and radeonhd drivers for RV200-RV500 cards, which is anything before the HD3xxx cards which are RV600 series. Accelerated 2D is already implemented and full 3D support is coming soon for RV600 and a short time later for RV700 cards. Expect rapid improvements in 3D for all cards over the next few months.

Generally, the drivers in a distribution will not be updated but improved drivers will be integrated into the next distribution release. Patience is in order. People are aware of many issues and are working hard to resolve them but a severe lack of  bug reports from users is impeding progress, 

You can provide tremendous help for yourself and everyone else by filing bug reports. There is a how to bug report sticky at the head of the Absolute Beginners forum. Use it.

The developers have neither the time nor inclination to follow the forums so do not expect your specifically weird hardware problem to be solved by posting here or that the developers will take notice or do something about it. The developers only have so much time and only so many machines and only so much hardware and are unable to test every conceivable configuration and so they depend on you, the user, to help them and the only way you can do that is through bug reporting.

If you want Koala to work better with your hardware....

Please, report all bugs.

Thank you for your attention,

mark

---

### Post by hawthornso23 on 2009-07-02
> **markbuntu said:**
> Don't feel so bad, ati dropped support for those cards from their windows drivers too and there is no open source driver available at all for windows. According to ATI any operating system from Feb 2009 on will not get new drivers for these cards. I wonder if that includes windows 7?

I've just installed Jaunty on the box I'd previously been using to play with windows 7 beta, which has this chipset (onboard graphics). I can confirm no driver for windows 7. The XP driver did work with full 3D - but was probably also responsible for frequent spontaneous reboots, lockups and blue screens of death.

The open source driver with Jaunty works fine for me so long as you steer clear of anything 3D. I'm now looking to invest in a video card. Recommendations?

---

