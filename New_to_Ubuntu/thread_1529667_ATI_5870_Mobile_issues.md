---
title: "ATI 5870 Mobile issues"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by michealdbrown on 2010-07-12
I just recently bought a new laptop, and am trying to make a move towards open source, so I installed ubuntu, however in addition to the builtin 17 inch display, when i'm at home I usually have a 24 inch LCD hooked up as well, however in ubuntu, when i have said monitor activated, after a few minutes it fritzes out the display and goes to all bars, making it unusable, I like Ubuntu, and want to stay with it, but I also want to be able to use my secondary display.  I realize it's new hardware and driver support may be an issue, i was just wondering if anyone has had similar issues, and if anyone has found a solution or work around.  Would finding drivers for the monitor help maybe? (it's a BenQ 24 HD 1920x1080 monitor, not sure if BenQ ships or makes linux based drivers)

Mike

---

### Post by vandorjw on 2010-07-14
Finding drivers for your monitor is not the issue.
If you think that drivers might be the issue, go to ATI support site and download the linux ATI drivers for your Graphics Card.

Just a couple questions
- Does it do it for all resolutions?
- Does it do this for all the available ports?
Example: Have you tried using a VGA cable, HDMI cable, etc...

Since it does this only after a few minutes, what I would try and do is, turn off the power saving feature...Most monitors go into standby mode if they thinks they are not being used to save electrical bill. Turn that off and let me know if it continues to do this.

Cheers - CC7

---

### Post by alphacrucis2 on 2010-07-14
> **michealdbrown said:**
> I just recently bought a new laptop, and am trying to make a move towards open source, so I installed ubuntu, however in addition to the builtin 17 inch display, when i'm at home I usually have a 24 inch LCD hooked up as well, however in ubuntu, when i have said monitor activated, after a few minutes it fritzes out the display and goes to all bars, making it unusable, I like Ubuntu, and want to stay with it, but I also want to be able to use my secondary display.  I realize it's new hardware and driver support may be an issue, i was just wondering if anyone has had similar issues, and if anyone has found a solution or work around.  Would finding drivers for the monitor help maybe? (it's a BenQ 24 HD 1920x1080 monitor, not sure if BenQ ships or makes linux based drivers)

Mike

Have you activated the Catalyst driver via System - Administration - Hardware Drivers ? That should get you Catalyst 10.5 which is the latest one in the repos. AMD have released 10.6 and 10.7 will be out sometime over the next couple of weeks. 10.6 has major improvements over 10.5 so it is worth downloading it. The install using the AMD/ATI installer is a bit trickier than installing via the Hardware Drivers menu. It would pay to read this:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by mavicus on 2010-07-20
I too have the freeze to "all bars" issue. Here is what I have observed:

I have an ASUS G73JH Notebook.

It does it under both 32 bit and 64 bit versions of Ubuntu.
It does it under both Ubuntu 9.10 and 10.04 (32 and 64)
It does it with an actual OS install AND with the "try ubuntu" mode.
It usually only does it when I play a game with 3D acceleration, but not necessarily.
It will [COLOR="SeaGreen"]not[/COLOR] do it after I disable the ATI drivers.
I haven't noticed it doing it *before* I enable them the first time.
It does it with both the version that comes available from within Ubuntu and also with the latest driver download from AMD/ATI.
With the newer driver version from ATI, it *can* sometimes "almost" freeze for a split second, sometimes going to the bars and back in an instant, but will eventually freeze.
Browsing the internet and using local videos and music do not seem to trigger it per se.
The only way to recover seems to be a manual power-off.
Brand new $1500 laptop and no Ubuntu. *CRY!* :frown:

Help please?

---

### Post by mavicus on 2010-07-22
I was able to make my laptop temporarily usable by running ubuntu 9.10 and replacing my driver with xorg-driver-fglrx from synaptic.

Performance is sub-par but I can play a few simple 3d accelerated games like "zaz" with no crashes. I now have a watermark that states unsupported hardware.

I know this does not solve the original poster's problem, because with this setup I don't have the catalyst control center available and cannot activate my external monitor as a second monitor, but for anyone else that finds this post with the vertical bars freeze, it might help.

I have submitted this to ATI, along with the original poster's problem.
After doing some more reading, I am inclined to believe it is due to a lack of demand for use with the mobile version of their video cards in linux.

---

### Post by kezeb on 2011-02-17
install the latest prop. drivers [http://www2.ati.com/drivers/linux/ati-driver-installer-11-2-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-2-x86.x86_64.run) and you can get rid of the tearing by running aticonfig --set-pcs-u32=DDX,EnableTearFreeDesktop,1 once you've installed the drivers, check my thread if you want to get a couple of other things to work right :
[http://ubuntuforums.org/showthread.php?t=1689936](http://ubuntuforums.org/showthread.php?t=1689936)

---

