---
title: "Problem with ATI Drivers"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by dcheifer on 2010-04-07
I'm working on switching over to Ubuntu (9.10 64 bit) as my primary OS, but I've run into a bit of a problem that I haven't been able to solve.  My laptop has an ATI Mobility 5870 graphics card, and I can't seem to get it to work quite right.  I understand that this is probably a driver problem.  

-The open source driver gives the wrong aspect ratio (can't be corrected with display settings) and text does not look sharp.  

-ATI's drivers installed by either envy or Ubuntu's hardware driver manager give me the correct resolution (1600x900), but there is a watermark in the lower right corner of my screen.  Text looks sharper, but some images seem to be unusually low quality (especially noticeable with the background image while Ubuntu is booting up).

-I've also tried manual installation of the Catalyst 10.3 drivers from ATI's website following procedures found here:  [http://ubuntuforums.org/showthread.php?p=7792744#post7792744](http://ubuntuforums.org/showthread.php?p=7792744#post7792744) as well as in ATI's official installation instructions. usually ends with my computer not recognizing an applicable device when I try to run aticonfig.  Incidentally, this process goes wrong in the same place for me as it did in post #16 of the above link.

I've gotten other weird results, like my computer telling me while booting up that it can only run in low quality graphics mode.  Unfortunately I can't recollect how I did this or reproduce it, but it has happened at least twice.  

I appreciate any help anyone might be able to offer.  I'd really like to make this work!

---

### Post by dcheifer on 2010-04-07
Sorry, but does anyone have any ideas?  Or should I be posting this in a different spot?

---

### Post by J V on 2010-04-07
Open source ATI drivers: Sucks
Closed source ATI drivers through hardware manager (Isn't that what envy is?): Watermark
Closed source ATI drivers manually installed from ATI website: Works fine, but a bitch to get working properly.

ATI hates linux, I advise you to never buy from them again... ever... just because they are like this now, nvm 10 years from now... EVER... Ok, now that that is over :)

The instructions on ATI's site are also impossible to find, if it were a simple executable it would be easy, but its a pos and you will need to google ways to get it to work properly...

(Use nvidia myself, but the ATI site is all but user friendly and helping someone through im yielded such results)

---

### Post by jaycee23 on 2010-04-07
I have ATI card on my desktop - see my signature!

Using the ATI Catalyst 10.3 driver from their website. 

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

The instructions are clear even for a relative newbie like myself and I have got to say it works like a dream. I was a bit concerned seeing all the anti-ATI stuff on the forum but the new driver released last month is great. You will need to check if your card is supported but I think it will be.

Post back if you have any issues.

---

### Post by Mark Phelps on 2010-04-07
Suggest you check over at the Phoronix forums.  

They do a LOT of work with ATI drivers -- closed-source and open-source.  

They may have a patch for the watermark problem.

---

### Post by phidia on 2010-04-07
I had looked at a laptop with this card in it but after doing a lot of searches I decided that the 58 series is unsupported in linux-not saying someone somewhere doesn't claim it works but there is nothing out there as a guide for that card on linux. There is another poster at the forums [here]("http://ubuntuforums.org/showthread.php?t=1422592") asking the same thing with even fewer replies.

---

### Post by dcheifer on 2010-04-07
Huh.  It looks as though they support the 5870 is listed as supported for the regular Radeon, but not the Mobility Radeon.  I'll have to check in the Phoronix forums and see if they have any ideas.  

I sure hope I can get this to work.  I bought this computer hoping to switch from Mac OS to Linux.  I'd really hate to have to switch to Windows.  Maybe I'll luck out and ATI will add support for this card in their next monthly driver update...

Thanks for the tips!

---

### Post by quadproc on 2010-04-07
> **dcheifer said:**
> I'm working on switching over to Ubuntu (9.10 64 bit) as my primary OS, but I've run into a bit of a problem that I haven't been able to solve.  My laptop has an ATI Mobility 5870 graphics card, and I can't seem to get it to work quite right.I am running HD4870x2 and I am presently getting satisfactory results.
> 
-ATI's drivers installed by either envy or Ubuntu's hardware driver manager give me the correct resolution (1600x900), but there is a watermark in the lower right corner of my screen.I find that the Hardware Drivers utility does not report correctly on the status of my system.  In particular, it says that the fglrx driver is not in use when it is in use and is working correctly.  Consequently, I prefer to run the ATI driver installation manually from ATI's .run file.  This also lets me specify the --keep option so that I can look in the files it used for the installation.

quadproc

---

### Post by dcheifer on 2010-04-12
Thanks for your comment.  I'm glad it works for you.  I've tried that method too.  The documentation for the drivers looks like it supports the 4870, but not the 5870 yet.  I've kind of resigned myself to hoping that the drivers will be updated soon to support my card.

---

### Post by egalvan on 2010-04-12
The new Lucid 10.04 LTS may have better ATI support.

I am testing the Beta2 on an IBM Thinkpad with ATI graphics,
and they run fine (totally default install)
That machine had video issues before Lucid.

Sorry I don't have the chip name to hand.

As soon as Lucid goes stable, I will upgrade a ThinkPad 60P from Hardy.
It also has ATI graphics.
It also had issues with previous Linux.

---

### Post by QIII on 2010-04-13
A word on whether AMD/ATI hates Linux or not:  No.

ATI (before it was AMD/ATI) was definitely snobbishly Windows-centric.  AMD/ATI is no longer so.

When ATI was bought by AMD, one of the first things that happened was a change in that culture.  It took them some time to turn it around.  By 2008, they were on the right track, albiet with some issues.  By 2009, they were spot on.

In fact, for the last few versions of Ubuntu (Ubuntu specifically, other Linux distros have to wait a bit), AMD/ATI has worked very hard to make sure that new drivers are available in the Ubuntu repos by the final release date.  This time, for Lucid, they made sure it worked with the lastest Xserver by the time Alpha 1 came out.  That's well before the final release date.

The misconception persists, however.  It is, by now, FUD.  I say again:  The AMD/ATI drivers and the Catalyst Control Center are in the Ubuntu repos.  The Ubuntu repos.  Need I say that again?  Point, click, install.

I have used the AMD/ATI drivers and Catalyst since Jaunty with absolutely no problems.  I encountered some frustration prior to that.  I am running Lucid Alpha 1 right now with multiple monitors, Compiz, independent desktops, independent rotating cubes, etc, without any problems at all.

Use the appropriate AMD/ATI driver and Catalyst for your version of Ubuntu.

As for "legacy" ATI cards, you will be left with the open source drivers.  AMD/ATI no longer maintains drivers for them, and offers only legacy drivers.  You may disabuse yourself of any thought that nVidia has not done the same with its "legacy" cards.

---

### Post by dcheifer on 2010-04-13
Yup, I noticed that a little while ago myself!  There's some talk about it here:  [http://www.phoronix.com/scan.php?page=news_item&px=ODA4MA](http://www.phoronix.com/scan.php?page=news_item&px=ODA4MA)

According to that page, it's possible to pull the 10.4 drivers out of Lucid and install them on earlier versions, but exactly how to do so is beyond me at this point.  I'm working on upgrading to Lucid right now to see if this is going to fix the problem.  If it does, I'll have to decide whether I want to just stick with the beta or figure out how to pull those drivers out and install them in 9.10.  I'll post the results here, just in case there's interest.

---

### Post by dcheifer on 2010-04-13
It certainly seems like an exaggeration that ATI "hates" Linux, but the 10.3 drivers released a couple of weeks ago definitely did not support Mobility 5xxx graphics cards.  They are not mentioned in ATI's documentation as being supported, and when installed (by pretty much any method), they did not recognize the card.

However, I have just installed the new beta of 10.04, and it works like a charm.  Even the open source drivers recognized the proper resolution for my display, and the Catalyst 10.4 drivers available through the proprietary driver manager works even better.  If anyone else out there is having problems with a Mobility 5xxx graphics card, download the new Ubuntu beta, figure out how to get the Catalyst 10.4 drivers from the Lucid Repository, or wait for ATI to post the new driver to their site.

---

### Post by Mark Phelps on 2010-04-13
QIII:

While you make some valid points in your post, I would like to point out that AMD/ATI has only abandoned the Linux community in terms of legacy driver updates, not the MS Windows community.

I am using the same legacy card in Ubuntu 9.10 as I am in Win7, and in the latter, the ATI Catalyst version available for the legacy drivers is now up to Catalyst v10.2 -- only a couple of minor releases behind the current 10.4 beta.

In contrast, not only is the Linux legacy version still back at Catalyst 9.3, I can't even use that in Ubuntu 9.10.

---

### Post by QIII on 2010-04-13
I can appreciate that.  But it must be remembered that in the Windows community, OEMs don't have to contend with the substantial Xserver changes that have happened as of late.

nVidia has "legacied" cards in terms of Linux support as well.

I had one Win XP machine (which recently died) that was running an ancient Matrox card...

---

### Post by Mark Phelps on 2010-04-14
Thanks for the info:

> **QIII said:**
> nVidia has "legacied" cards in terms of Linux support as well.

I feel better now about not being singled out because of my ATI legacy card :)

---

