---
title: "i5 Integrated GMA HD Laptop!"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by darkerlink on 2010-02-09
I just bought a Dell Inspiron laptop. This is currently being used as a desktop replacement. The CPU is the intel i5 quad core with a GMA HD integrated graphic. I've been searching my hair out and can't find anything related to this specific card and ubuntu. I've installed Karmic and it displays 1600 by 900 fine. The problem Im having is that video played on movie player is extremely choppy. Youtube video is a bit better but not great. I did a system update and my xorg has a -intel prefix. 

From time to time, my computer locks up when I perform certain tasks. For eample, glxgears will not display and lock up my computer. Compiz does not work. Im getting extremely frustrated. A brand new computer having trouble with ubuntu?

I've checked System>Administration>Hardware Drivers but there is nothing listed.

Please help!

---

### Post by phidia on 2010-02-09
Probably start a flame war here but-integrated cards and specifically the intels are not seen as very good in performance terms-if compiz doesn't work though perhaps xorg isn't set up correctly? You can look at the Ubuntu community video info [here]("https://help.ubuntu.com/community/Video") or you may want to look at [this guide]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.10-karmic-koala-p2") to be sure your media dependent apps are set up right.

---

### Post by darkerlink on 2010-02-09
I have to disagree because it came with windows 7 out of the box and video ran perfectly on it. Sorry but that link you sent me had no info on the intel GMA HD. I think I have the wrong xorg installed but I'm not sure how to change that. If anyone has experience with this chipset/laptop, please chime in. I've gone off windows for over a year and I dont want to go back!

---

### Post by Seq on 2010-02-09
> **phidia said:**
> Probably start a flame war here but-integrated cards and specifically the intels are not seen as very good in performance terms-if compiz doesn't work though perhaps xorg isn't set up correctly? You can look at the Ubuntu community video info [here]("https://help.ubuntu.com/community/Video") or you may want to look at [this guide]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.10-karmic-koala-p2") to be sure your media dependent apps are set up right.

The intel cards are awesome. Sure you can't run certain high-end games on them, but they run OpenGL, Compiz, and other effects perfectly fine (I'm using compiz on an 865 at work, and have used on a 950 and x3100 at home).

---

### Post by darkerlink on 2010-02-09
> **Seq said:**
> The intel cards are awesome. Sure you can't run certain high-end games on them, but they run OpenGL, Compiz, and other effects perfectly fine (I'm using compiz on an 865 at work, and have used on a 950 and x3100 at home).

How did you get it to work?

---

### Post by Seq on 2010-02-09
> **darkerlink said:**
> I just bought a Dell Inspiron laptop. This is currently being used as a desktop replacement. The CPU is the intel i5 quad core with a GMA HD integrated graphic. I've been searching my hair out and can't find anything related to this specific card and ubuntu. I've installed Karmic and it displays 1600 by 900 fine. The problem Im having is that video played on movie player is extremely choppy. Youtube video is a bit better but not great. I did a system update and my xorg has a -intel prefix.The new i5 CPUs actually have the integrated graphics core on the CPU itself, which should help with performance (since the memory controller is also on the CPU). Heat-dissipation should be improved too, which I'm jealous about as I've got an nVidia furnace in my current laptop.

Intel actually started adding support for these new graphics chips long before they were released to makret, so there should be basic support already. But as you noticed, it is buggy. Considering the driver 9.10 uses was released in September and the chips themselves only recently, it is not that surprising.

There are some PPAs that contain updated drivers. There is the xorg-edgers [drivers-only]("https://launchpad.net/~xorg-edgers/+archive/drivers-only") PPA, which should be fairly stable. It has -intel 2.9.1 from October, so a bit more recent.

There is an [x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") ppa, but it doesn't seem to have anything that will help you. (for 9.10, just a mesa update for 32-bit GL on 64-bit systems).

There is also a [main xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") ppa, but it probably WILL break something (that is somewhat the point of this PPA) so I don't really recommend using it.

> **darkerlink said:**
> From time to time, my computer locks up when I perform certain tasks. For eample, glxgears will not display and lock up my computer. Compiz does not work. Im getting extremely frustrated. A brand new computer having trouble with ubuntu?

Phoronix ran an article called [Intel Clarkdale Linux Graphics Performance]("http://www.phoronix.com/scan.php?page=article&item=intel_clarkdale_gpu&num=1") where they benchmarked a desktop-version of the i5. They had a few crashes as well with a few games, but had success with compiz. They were running a test release of Ubuntu 10.04 (not recommended) with a manually-installed kernel and intel driver (doubly-so).

I can't really recommend much other than trying the drivers-only PPA, and hoping that by 10.04 the support for this card is improved.

> **darkerlink said:**
> I've checked System>Administration>Hardware Drivers but there is nothing listed.This is typically only for closed-source drivers and firmware (nvidia, broadcom, etc) since Open-Source drivers are enabled out of the box.

---

### Post by Seq on 2010-02-09
> **darkerlink said:**
> How did you get it to work?

It just does. Older cards have the advantage of being better tested. Your card was released after 9.10 was released, so support is not quite as good. Intel is trying to get driver updates out before the cards, but considering there are bugs with cards that have been out for years, you can imagine issues with supporting unreleased hardware.

---

### Post by blur xc on 2010-02-09
I've always understood that with Linux the latest hardware isn't always the best.  If you stay a generation or two behind though, it should run pretty well.  If you have to have the latest and greatest- then in some cases it's probably the best bet to stick w/ Windows.

BM

---

### Post by Seq on 2010-02-09
> **Seq said:**
> I can't really recommend much other than trying the drivers-only PPA, and hoping that by 10.04 the support for this card is improved.

Actually, looks like 2.9.1 didn't add anything that will help you: [wiki]("http://wiki.x.org/wiki/Intel29Branch"), [announcement]("http://lists.freedesktop.org/archives/xorg/2009-October/047859.html").

---

### Post by darkerlink on 2010-02-09
> **Seq said:**
> It just does. Older cards have the advantage of being better tested. Your card was released after 9.10 was released, so support is not quite as good. Intel is trying to get driver updates out before the cards, but considering there are bugs with cards that have been out for years, you can imagine issues with supporting unreleased hardware.

I added that PPA to my sources and upgraded xserver-xorg-video-intel . Tried to apply desktop effects and it still locks up. I suppose I will just have to wait for Lucid and HOPE it is supported? Sorry for the newbish, when is lucid coming out and do you think intel will have x running by then?

---

### Post by darkerlink on 2010-02-09
> **Seq said:**
> Actually, looks like 2.9.1 didn't add anything that will help you: [wiki]("http://wiki.x.org/wiki/Intel29Branch"), [announcement]("http://lists.freedesktop.org/archives/xorg/2009-October/047859.html").



@ seq and blur hc, That is such a bummer to hear. :(

---

### Post by Seq on 2010-02-09
> **blur xc said:**
> I've always understood that with Linux the latest hardware isn't always the best.  If you stay a generation or two behind though, it should run pretty well.

It depends. Some things hit Linux first. USB3 support, for example. Regular users still have to wait until Distros pick these improvements up (USB3 arrived in Ubuntu 9.10 it looks like -- not that I have hardware to test with).

> **blur xc said:**
> If you have to have the latest and greatest- then in some cases it's probably the best bet to stick w/ Windows.

There is never a reason to go back to Windows. I'd rather be unsupported in a familiar usable environment than supported in an unfamiliar unusable one. ;)

I'd go back to -vesa or over to Fedora, but I can't see spending an additional few hundred dollars on Windows to get a piece of hardware working a little faster, then suffering for several months on trying to actually use the hardware. I've put up with unsupported keyboards (Never again buy new apple hardware on launch day -- at least I learned how to write kernel patches), crashy graphics (I've repressed memories of 9.04) and unsupported display backlight interfaces (my current nvidia laptop).

---

### Post by Seq on 2010-02-09
> **darkerlink said:**
> I added that PPA to my sources and upgraded xserver-xorg-video-intel . Tried to apply desktop effects and it still locks up. I suppose I will just have to wait for Lucid and HOPE it is supported? Sorry for the newbish, when is lucid coming out and do you think intel will have x running by then?

Ubuntu releases every April and October. The version numbers reflect this. Karmic was 9.10, for 2009.October. Lucid is 10.04 for 2010.April. If we survive the end of the alphabet we'll have a number issue in 2100.

According to that article on Phoronix I linked to a few posts ago, it seems to be working with upstream sources, but still has some minor stability in a few choice games. Hopefully those get fixed. ubuntu will apparently be backporting the -nouveau driver, hopefully they have an up-to-date -intel too. I haven't been following too closely though.

---

### Post by blur xc on 2010-02-09
> **Seq said:**
> It depends. Some things hit Linux first. USB3 support, for example. Regular users still have to wait until Distros pick these improvements up (USB3 arrived in Ubuntu 9.10 it looks like -- not that I have hardware to test with).



There is never a reason to go back to Windows. I'd rather be unsupported in a familiar usable environment than supported in an unfamiliar unusable one. ;)

I'd go back to -vesa or over to Fedora, but I can't see spending an additional few hundred dollars on Windows to get a piece of hardware working a little faster, then suffering for several months on trying to actually use the hardware. I've put up with unsupported keyboards (Never again buy new apple hardware on launch day -- at least I learned how to write kernel patches), crashy graphics (I've repressed memories of 9.04) and unsupported display backlight interfaces (my current nvidia laptop).

I guess that the "some cases" part of my statement is subjective to the individual.  Broken graphics and video playback, imo, would be a deal breaker, until suitable drivers come along.  But I am one to tolerate some degree of difficulties, for the other obvious benefits of running Linux.

I spec'd my desktop with several generations old hardware, and it kicks butt w/ Ubuntu. 

BM

---

### Post by phidia on 2010-02-09
> **Seq said:**
> The intel cards are awesome. Sure you can't run certain high-end games on them, but they run OpenGL, Compiz, and other effects perfectly fine (I'm using compiz on an 865 at work, and have used on a 950 and x3100 at home).

At the risk of escalating this "awesome" at what and what does that even mean in quantifiable terms? Integrated cards always perform at much slower fps rates than dedicated cards and if you look at the raw numbers at places like [this]("http://www.notebookcheck.net/Mobile-Graphics-Cards-Benchmark-List.844.0.html") it will be hard call those cards anything but mediocre.
It's not too surprising that the card performs better using win7 and the driver the laptop and video card man specified for it.

---

### Post by Seq on 2010-02-09
> **phidia said:**
> At the risk of escalating this "awesome" at what and what does that even mean in quantifiable terms? Integrated cards always perform at much slower fps rates than dedicated cards and if you look at the raw numbers at places like [this]("http://www.notebookcheck.net/Mobile-Graphics-Cards-Benchmark-List.844.0.html") it will be hard call those cards anything but mediocre.
It's not too surprising that the card performs better using win7 and the driver the laptop and video card man specified for it.

(Sorry for knocking the thread off-course.)

I noted you can't run high-end games on them. So benchmark bragging and gaming aside, what is the benefit of a dedicated gpu with discrete memory?

The intel cards have a few things going for them: Low power use, open drivers, proper integration with the system, out-of-the-box support (except if your hardware is newer than your OS release -- but hey, same issue with nvidia and fglrx in Ubuntu), and low cost as they are integrated into existing components. When was the last time you cared about the FPS of Firefox? Or gnome-panel? Your flat panel probably only updates at 60Hz anyway, and intel can easily push kwin and compiz that fast. The only desktop-targeted feature they currently lack which I would enjoy is hardware video decoding.

My current laptop has an nvidia 9600m that takes 30+ seconds to re-init the screen on resume, doesn't work with xrandr, the nvidia-settings utility requires a GUI so it can't be scripted or bound to a key, it occasionally doesn't detect external monitors, sometimes corrupts itself when activating an external monitor (if it does detect it). Basically it uses more power to provide a sub-par user experience. So yeah, Intel was pretty awesome for me.

Granted, it's not awesome when it doesn't work, such as the new i5 GPU on 9.10.. And again, sorry for hijacking the thread with my earlier comment (and this reply).

---

### Post by skymera on 2010-02-09
> **darkerlink said:**
> The CPU is the intel i5 quad core 

FYI that CPU is a hyper-threaded dual core. Not quad.

Some i5 desktop CPUs are quad core.

---

### Post by msrinath80 on 2010-02-09
> **Seq said:**
> (Sorry for knocking the thread off-course.)

I noted you can't run high-end games on them. So benchmark bragging and gaming aside, what is the benefit of a dedicated gpu with discrete memory?

The intel cards have a few things going for them: Low power use, open drivers, proper integration with the system, out-of-the-box support (except if your hardware is newer than your OS release -- but hey, same issue with nvidia and fglrx in Ubuntu), and low cost as they are integrated into existing components. When was the last time you cared about the FPS of Firefox? Or gnome-panel? Your flat panel probably only updates at 60Hz anyway, and intel can easily push kwin and compiz that fast. The only desktop-targeted feature they currently lack which I would enjoy is hardware video decoding.

My current laptop has an nvidia 9600m that takes 30+ seconds to re-init the screen on resume, doesn't work with xrandr, the nvidia-settings utility requires a GUI so it can't be scripted or bound to a key, it occasionally doesn't detect external monitors, sometimes corrupts itself when activating an external monitor (if it does detect it). Basically it uses more power to provide a sub-par user experience. So yeah, Intel was pretty awesome for me.

Granted, it's not awesome when it doesn't work, such as the new i5 GPU on 9.10.. And again, sorry for hijacking the thread with my earlier comment (and this reply).

I totally second your thoughts. Integrated graphics may not give the best FPS, but they do have a lot more going for them. Nvidia/ATI were never originally designed for the mobile platform. The consumer laptop market demand forced these companies to try and build chips that could be squeezed into a laptop. In trying to keep the performance at par with the desktop cousins, they ended up creating little "furnaces" in the laptop as someone described earlier.

Intel on the other hand started experimenting with integrated graphics way back around the time the first i810 was released. Up until then, Via, SiS and S3 were the major players in the integrated graphics market. They have obviously had a great amount of time to sit down and perfect this technology.

FWIW, I game on my laptop too. But I'm old school... I play OpenArena or better still  Unreal Tournament GOTY at times. My GMA950 seems to give me 60+ FPS on average which is more than I need for such games. It can do Compiz too, but I find it more of a distraction, so I don't use it. But, at the end of the day, in exchange for the high-end performance I've gained:

1. Low power consumption => More battery life and Low heat
2. Free software (GPL) drivers for the GPU. So if at a later date, something needs to be fixed, it can still be done.

---

### Post by darkerlink on 2010-02-09
> **skymera said:**
> FYI that CPU is a hyper-threaded dual core. Not quad.

Some i5 desktop CPUs are quad core.


Really? On win7 it shows 4 cores running in task manager and it also shows 4 cores in Ubuntu system monitor.

I'm not doubting you. My brother told me the technical specs. Something about thread simulating cores but I was(and still am) somewhat confused.

@ seq and blur, hi-jacking the thread is fine! As long as it adds to the thread and from what I've read so far, I've learned some stuff I didn't know.

In all honesty, i agree with you here.

[quote=seq]There is never a reason to go back to Windows. I'd rather be unsupported in a familiar usable environment than supported in an unfamiliar unusable one.[/quote]

The main reason I am running ubuntu is because I am familiar with it. It took me about a year to get Ubuntu down as a casual user. It took me nearly half a decade to get windows XP down and I wasn't going to bother with another windows product. If the main issue with my CPU is lack of support, then I can wait until Lucid. Although it would be nice to unleash the power of this brand new laptop :) I havent had a new computer in a very long time so having this slowdown and no compiz is really disappointing. Pardon me, I'm just very anxious! I expect more people will be posting about this problem. At least until Lucid is out.

---

### Post by skymera on 2010-02-11
> **darkerlink said:**
> Really? On win7 it shows 4 cores running in task manager and it also shows 4 cores in Ubuntu system monitor.

I'm not doubting you. My brother told me the technical specs. Something about thread simulating cores but I was(and still am) somewhat confused.


The some i3's, i5's and i7's have HyperThreading.
This allows each CPU core to take two data threads simultaneously.
Thus showing each core as 2 :)

This is why some of the Pentium4's showed up as 2 CPUs back in the day. The performance increase is somewhere between 10-30%

---

### Post by PSIRockin on 2010-02-12
I'm feeling your pain, darkerlink. I bought an HP dv4-2170us, which I think has the same graphics chip set. I think I'm going to install 10.4 and keep up with updates until, hopefully, there's support.

---

### Post by darkerlink on 2010-02-13
Not just bumping for no reason.

After a few days keeping things the way they were, I noticed a few strange things.

1. Youtube and flash freezes. When I am playing a YT video, it will play fine for a few seconds and all of a sudden, it will freeze. It will "resume" when I move the mouse. This is really frustrating. The same thing happens with anything that has a progress bar. Like if I am copying a file and it says 15 seconds left. It will stay that way until i move the mouse. It's almost if the screen does not refresh unless the mouse is moved. Really strange, and annoying.

2. The second thing I am noticing is my eyes hurt after a few hours looking at the screen. I've looked at other screens for hours and not have any eye strains but for some reason, this screen hurts my eyes. At first I thought it was my hardware but i remembered it looking crisp on win7. Not arguing for a reason to go back to win7, just an observation. At first I thought it was the screen resolution but this was not the case. @ 1600 by 900, some pictures look blurry. By pictures i mean graphics. For instance, I am a webmaster and when I log into my Wordpress blog, the top left logo has jaggy. At first, I thought it was lack of ant-aliasing but then i thought, "this is firefox, that can't be the case". Other graphics look "off" also. I concluded that the screen outputs at 1600 by 900 but my x server is not rendering the graphics correctly.

3. last thing i noticed was the difficulty scrolling. It would render so slow as if the cpu was lagging behind but i know that's not the case since its a brand new computer! Remember the old days when your would scroll and your screen would lock up taking a second to respond. This is the case here. Sometimes it is "fast" but other times, it is "slow" and by slow i mean it would take a split second to scroll. It feels unresponsive. 


Thanks PSIRockin, glad to know I am not alone. Anyone else with this chipset/problem please feel free to chime in and add your story. I've done all the searching and this is the only thread concerning this problem (last time i checked).

---

### Post by cariboo on 2010-02-13
You never really said what chipset your laptop has, I have an atom 320 powered media pc, with a 945 chipset, it does full screen video on my 32" HD LCD with no problems, but full screen hd flash brings it to its knees. It's more due to shared memory and a low powered cpu than a graphics problem. 

I just got a Compaq 1100 netbook with the same graphics chip and an Atom 270 cpu, I will do YouTube HD at full screen, but there is a slight bit of flickering depending on the video, some work fine and others don't. Both systems use the Intel i915 driver, which is installed by default.

---

### Post by darkerlink on 2010-02-14
from my gui version of lshw, my chipset is:

Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz

Taking a wild shot since I'm not too technically inclined, is my chipset better than the intel atom you have?

From what I reckon, there's no reason from the slowdown and choppiness. At least not from the cpu I have. Rephrasing it, my cpu is more than capable right?

---

### Post by Seq on 2010-02-15
> **cariboo907 said:**
> You never really said what chipset your laptop has, I have an atom 320 powered media pc, with a 945 chipset, it does full screen video on my 32" HD LCD with no problems, but full screen hd flash brings it to its knees. It's more due to shared memory and a low powered cpu than a graphics problem.

The core i5 has the graphics core on-die with the CPU. This allows faster access to shared memory since the memory controller on the i-series processors is also on-die. The new motherboards that support this have video output (DVI, etc) but no actual graphics processor integrated, requiring support from a CPU. If you were to drop in another processor (eg. i7) the graphics ports would be dead.

---

### Post by PSIRockin on 2010-02-23
Just a follow-up, I did manage to get accelerated graphics by installing Lucid and then getting the latest xserver-xorg-video-intel from the xorg edgers repository and switching "vesa" to "intel" in my xorg.conf. I'm left with other hardware related problems though. It's still progress!

---

### Post by makaki on 2010-02-25
I just bought a Dell Inspiron 1564 that has Core i3 and Intel integrated graphic card. I have the same issue with the graphics :(

My screen is 15.6" and the current resolution is 1024x768 :(
I spoke with Dell and they said that the resolution should be 1200x720. So there are a lot of issues to deal with.

I haven't tried the solutions here yet. I hope they work.

---

### Post by ajslay on 2010-02-25
why dont you install 10.04 alpha?? and see if it works? thats what i would do if i were in your situation.

---

### Post by makaki on 2010-02-26
I added the xorg-edgers PPA and when I searched for the package: xserver-xorg-video-intel I found that it was already installed!!

---

### Post by makaki on 2010-02-26
Does anybody have the resolution problem? :(

---

### Post by Garibaldi3489 on 2010-02-26
I have a Lenovo with a i5 and the same problem. I added xorg-edgers and upgraded xserver-xorg-intel and all of the other drivers in that repository. Moreover, I installed the 2.6.32 kernel. Some reading on the Gentoo Wiki said I should use the following my xorg.conf:
```
Section "Device"
       Identifier      "Configured Video Device"
       Driver          "intel"
#      Driver          "vesa"
       Option "AccelMethod" "UXA"
       Option "Tiling" "False"
EndSection
```

As well as set the i915 modeset to 1, which I did following [these instructions](http://ubuntuforums.org/archive/index.php/t-1189111.html).

After all of that and several variations of testing - the result is the same - GDM comes up fine but when I login and the desktop starts to load, everything freezes. I cannot even tty to a terminal so I'm forced to CTRL+ALT+REI which kills X and gets me to a terminal where I can edit xorg.conf back to vesa and reboot.

If anyone else has any other ideas, I'll try them and let you know.

---

### Post by makaki on 2010-02-27
Guys I installed Ubuntu 10.04 Alpha 3 and everything worked out of the box :D

So be patient guys, only one month is left ;)


[COLOR=Red]UPDATE: Even though the graphics work fine, but Ubuntu is highly unstable :S[/COLOR]

---

### Post by andyvr4 on 2010-03-01
> **makaki said:**
> Guys I installed Ubuntu 10.04 Alpha 3 and everything worked out of the box :D

So be patient guys, only one month is left ;)

Is this with compiz enabled and all the fancy graphics stuff running?

I'm looking at getting a new laptop very shortly with the i3 and would really like to get the integrated graphics for the power savings because I've got my desktop for gaming.  All that I use my laptop for is browsing the internet and open office!

I've just been worried about how well these new intel integrated graphics are going to work with linux, I've always stuck with nvidia because I know they're supported really well, I just don't like the idea of the power hungry nivida graphics in a laptop that has no need for a performance graphics card!

Thanks

---

### Post by Garibaldi3489 on 2010-03-03
I can confirm that lucid alpha 3 has compiz enabled out of the box. I looked and the kernel is also 2.6.32 so that is not the problem. It seems that the xserver-xorg-video-intel (2.10.x) and related packages from xorg edgers are broken and that's why it works for a couple seconds on my system and freezes. The lucid package version is 2.9.1 - if we could somehow get ahold of these versions of the drivers from xorg edgers or another source I think we could get this working. Does anyone know where we could find these packages?

---

### Post by darkerlink on 2010-03-05
> **makaki said:**
> Guys I installed Ubuntu 10.04 Alpha 3 and everything worked out of the box :D

So be patient guys, only one month is left ;)


[COLOR=Red]UPDATE: Even though the graphics work fine, but Ubuntu is highly unstable :S[/COLOR]


OMG! this thread is still alive! Glad to see I was not alone. So lucid looks like its going to fix this? YES!!!!!! This is awesome news. I could kiss you right now! I can't wait to have my laptop running buttery smooth with compiz. Mind keeping us updated with the alphas and betas of Lucid and this thread? I am reluctant to install the alpha only because im in the process of downloading some huge files that can, literally, take weeks.

Much thanks again guys! Keep us posted!:popcorn:


addendum: Just to clarify, as far as my research goes, this problem only affects the new GMA HD laptops and maybe the GMA HD desktop chipsets. The is currently the newest generation of intel GMA chipsets.

[http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)

From that wiki page, it seems that all intel GMA HD chipsets ranging from the i3 to the i7 are affected.

---

### Post by makaki on 2010-03-22
Any new news? I wonder if it works now with 9.10. Anybody found a solution yet for 9.10? Lucid isn't stable at all yet.

---

### Post by Garibaldi3489 on 2010-03-25
I'm running the lucid beta now and it works great! It has been quite stable for me

---

### Post by Orographic on 2010-03-27
Good to hear, I'm thinking of getting the Core i5 6xx or Core i3 because of the power savings and less heat. I don't play games at all so frame rates are not important to me. 

I've been testing Lucid Beta 1 on my Core E4300 and it is looking good. Better graphics in YouTube and iView as of the latest updates yesterday.

---

### Post by carlsiu on 2010-04-04
Hi all, I'm using i3 and GMA HD facing the same problem! Ubuntu just randomly hangs. I originally think that it is the hardware problem since it is a new computer with the hard disk taking from the old one.

Anyway, I want to ask if the problem can be relieved by setting Visual Effects to None? Thanks!

---

### Post by Funnnny on 2010-04-28
I also have the randomly hangs problem. My laptop also have Win7 installed but it runs fine and stable (except the fact that I hate Windows).
But really, I have to switch to Windows when I'm working

---

### Post by -curly- on 2010-05-03
I have this same problem.  This is on an Acer 5740-6491 with an i5 and Intel GMA HD.

In one week of using Ubuntu 10.04 it has frozen about ten times.  I've enabled CTRL-ALT-BACKSPACE, which does not work when the display freezes.

This is really disappointing.

---

### Post by darkerlink on 2010-05-03
Ohh man, i was just about to install 10.04 on my i5 laptop. So this problem still exists? Thats funny because I have the beta and it works fine.

---

### Post by -curly- on 2010-05-04
Yes, this problem still exists.

---

### Post by darkerlink on 2010-05-04
> **-curly- said:**
> Yes, this problem still exists.

Curly, I did a fresh install of the AMD 64 bit 10.04 .iso and everthing runs extremely smooth. Did you do a fresh install?

Immediately after the install, I followed Untitled_No4's post at #9 on this thread.

[http://ubuntuforums.org/showthread.php?t=1468743](http://ubuntuforums.org/showthread.php?t=1468743)

Everything now works fine. Flash has no hiccups so far. Compiz worked out of the box. I am happy with Lucid so far.

---

### Post by -curly- on 2010-05-04
It's a clean install, 64 bit flash, etc.

---

### Post by icepop on 2010-05-05
my computer:
 * Ubuntu 10.04 LTS
 * LENOVO, 4313CTO, ThinkPad T510
* Intel(R) Core(TM) i5 CPU M 540 @ 2.53GHz
* Integrated Graphics Chipset: Intel(R) Arrandale

X seems to have hung last night at 21:57:12 NZST, as that time is still frozen on the screen.

Alt-SysRq-s (sync) makes the disk activity LED flash, so that tells me the keyboard is working. also, i can use the keyboard to adjust the brightness and it *does* update the value in [FONT=Fixedsys]/proc/acpi/video/VID/LCD0/brightness[/FONT], and i can use the keyboard to turn the thinklight(tm) on and off and its state is reflected in "[FONT=Fixedsys]/sys/devices/platform/thinkpad_acpi/leds/tpacpi::thinklight/brightness[/FONT]". there's also keyboard buttons for volume, but i can't find where that would be read from CLI. i can run mplayer via ssh and play music from the hung laptop, which is amusing.

i am ssh'd into the box, but i can't escape from the GUI to a console. Alt-SysRq-k should work, but i haven't yet tried it.

interesting info in /var/log/messages about i915 and Xorg, starting a couple of minutes after the GUI froze:
```

May  5 21:59:32 cz101 kernel: [627199.346843] i915          D 0000000000000000     0   765      2 0x00000000
May  5 21:59:32 cz101 kernel: [627199.346853]  ffff88010abb9d40 0000000000000046 0000000000015bc0 0000000000015bc0
May  5 21:59:32 cz101 kernel: [627199.346862]  ffff8801306e5f80 ffff88010abb9fd8 0000000000015bc0 ffff8801306e5bc0
May  5 21:59:32 cz101 kernel: [627199.346871]  0000000000015bc0 ffff88010abb9fd8 0000000000015bc0 ffff8801306e5f80
May  5 21:59:32 cz101 kernel: [627199.346879] Call Trace:
May  5 21:59:32 cz101 kernel: [627199.346898]  [<ffffffff8153f867>] __mutex_lock_slowpath+0xe7/0x170
May  5 21:59:32 cz101 kernel: [627199.346911]  [<ffffffff81058620>] ? finish_task_switch+0x50/0xe0
May  5 21:59:32 cz101 kernel: [627199.346918]  [<ffffffff8153f75b>] mutex_lock+0x2b/0x50
May  5 21:59:32 cz101 kernel: [627199.346953]  [<ffffffffa022c37d>] i915_gem_retire_work_handler+0x3d/0xa0 [i915]
May  5 21:59:32 cz101 kernel: [627199.346975]  [<ffffffffa022c340>] ? i915_gem_retire_work_handler+0x0/0xa0 [i915]
May  5 21:59:32 cz101 kernel: [627199.346986]  [<ffffffff81080777>] run_workqueue+0xc7/0x1a0
May  5 21:59:32 cz101 kernel: [627199.346995]  [<ffffffff810808f3>] worker_thread+0xa3/0x110
May  5 21:59:32 cz101 kernel: [627199.347001]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
May  5 21:59:32 cz101 kernel: [627199.347007]  [<ffffffff81080850>] ? worker_thread+0x0/0x110
May  5 21:59:32 cz101 kernel: [627199.347012]  [<ffffffff81084fa6>] kthread+0x96/0xa0
May  5 21:59:32 cz101 kernel: [627199.347018]  [<ffffffff810141ea>] child_rip+0xa/0x20
May  5 21:59:32 cz101 kernel: [627199.347024]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
May  5 21:59:32 cz101 kernel: [627199.347028]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
May  5 21:59:32 cz101 kernel: [627199.347049] Xorg          D 0000000000000000     0   995    916 0x00400004
May  5 21:59:32 cz101 kernel: [627199.347055]  ffff880107721cb8 0000000000000086 0000000000015bc0 0000000000015bc0
May  5 21:59:32 cz101 kernel: [627199.347061]  ffff880106e55f80 ffff880107721fd8 0000000000015bc0 ffff880106e55bc0
May  5 21:59:32 cz101 kernel: [627199.347067]  0000000000015bc0 ffff880107721fd8 0000000000015bc0 ffff880106e55f80
May  5 21:59:32 cz101 kernel: [627199.347076] Call Trace:
May  5 21:59:32 cz101 kernel: [627199.347084]  [<ffffffff8153f867>] __mutex_lock_slowpath+0xe7/0x170
May  5 21:59:32 cz101 kernel: [627199.347093]  [<ffffffff8105b1d5>] ? wake_up_process+0x15/0x20
May  5 21:59:32 cz101 kernel: [627199.347101]  [<ffffffff8153f75b>] mutex_lock+0x2b/0x50
May  5 21:59:32 cz101 kernel: [627199.347121]  [<ffffffffa022be36>] i915_gem_busy_ioctl+0x46/0xd0 [i915]
May  5 21:59:32 cz101 kernel: [627199.347149]  [<ffffffffa01b6e2a>] drm_ioctl+0x27a/0x480 [drm]
May  5 21:59:32 cz101 kernel: [627199.347170]  [<ffffffffa022bdf0>] ? i915_gem_busy_ioctl+0x0/0xd0 [i915]
May  5 21:59:32 cz101 kernel: [627199.347179]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
May  5 21:59:32 cz101 kernel: [627199.347190]  [<ffffffff81152a92>] vfs_ioctl+0x22/0xa0
May  5 21:59:32 cz101 kernel: [627199.347197]  [<ffffffff81152d41>] do_vfs_ioctl+0x81/0x380
May  5 21:59:32 cz101 kernel: [627199.347202]  [<ffffffff811431df>] ? vfs_read+0x12f/0x1a0
May  5 21:59:32 cz101 kernel: [627199.347207]  [<ffffffff811530c1>] sys_ioctl+0x81/0xa0
May  5 21:59:32 cz101 kernel: [627199.347216]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
May  5 22:01:14 cz101 kernel: [627301.239569] usb 1-1.1.4: USB disconnect, address 12
May  5 22:01:22 cz101 kernel: [627308.957934] usb 1-1.1.3: new high speed USB device using ehci_hcd and address 13
May  5 22:01:22 cz101 kernel: [627309.081627] usb 1-1.1.3: configuration #1 chosen from 1 choice
May  5 22:01:22 cz101 kernel: [627309.082033] scsi15 : SCSI emulation for USB Mass Storage devices
May  5 22:01:27 cz101 kernel: [627314.076807] scsi 15:0:0:0: Direct-Access     TOSHIBA  TransMemory      PMAP PQ: 0 ANSI: 0 CCS
May  5 22:01:27 cz101 kernel: [627314.077609] sd 15:0:0:0: Attached scsi generic sg2 type 0
May  5 22:01:30 cz101 kernel: [627316.648461] sd 15:0:0:0: [sdb] 15874048 512-byte logical blocks: (8.12 GB/7.56 GiB)
May  5 22:01:30 cz101 kernel: [627316.649072] sd 15:0:0:0: [sdb] Write Protect is off
May  5 22:01:30 cz101 kernel: [627316.651517]  sdb: sdb1
May  5 22:01:30 cz101 kernel: [627316.699524] sd 15:0:0:0: [sdb] Attached SCSI removable disk
May  5 22:01:32 cz101 kernel: [627319.293876] i915          D 0000000000000000     0   765      2 0x00000000
May  5 22:01:32 cz101 kernel: [627319.293883]  ffff88010abb9d40 0000000000000046 0000000000015bc0 0000000000015bc0
May  5 22:01:32 cz101 kernel: [627319.293890]  ffff8801306e5f80 ffff88010abb9fd8 0000000000015bc0 ffff8801306e5bc0
May  5 22:01:32 cz101 kernel: [627319.293896]  0000000000015bc0 ffff88010abb9fd8 0000000000015bc0 ffff8801306e5f80
May  5 22:01:32 cz101 kernel: [627319.293902] Call Trace:
May  5 22:01:32 cz101 kernel: [627319.293916]  [<ffffffff8153f867>] __mutex_lock_slowpath+0xe7/0x170
May  5 22:01:32 cz101 kernel: [627319.293925]  [<ffffffff81058620>] ? finish_task_switch+0x50/0xe0
May  5 22:01:32 cz101 kernel: [627319.293931]  [<ffffffff8153f75b>] mutex_lock+0x2b/0x50
May  5 22:01:32 cz101 kernel: [627319.293957]  [<ffffffffa022c37d>] i915_gem_retire_work_handler+0x3d/0xa0 [i915]
May  5 22:01:32 cz101 kernel: [627319.293974]  [<ffffffffa022c340>] ? i915_gem_retire_work_handler+0x0/0xa0 [i915]
May  5 22:01:32 cz101 kernel: [627319.293981]  [<ffffffff81080777>] run_workqueue+0xc7/0x1a0
May  5 22:01:32 cz101 kernel: [627319.293987]  [<ffffffff810808f3>] worker_thread+0xa3/0x110
May  5 22:01:32 cz101 kernel: [627319.293993]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
May  5 22:01:32 cz101 kernel: [627319.293998]  [<ffffffff81080850>] ? worker_thread+0x0/0x110
May  5 22:01:32 cz101 kernel: [627319.294003]  [<ffffffff81084fa6>] kthread+0x96/0xa0
May  5 22:01:32 cz101 kernel: [627319.294009]  [<ffffffff810141ea>] child_rip+0xa/0x20
May  5 22:01:32 cz101 kernel: [627319.294014]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
May  5 22:01:32 cz101 kernel: [627319.294019]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
May  5 22:01:32 cz101 kernel: [627319.294038] Xorg          D 0000000000000000     0   995    916 0x00400004
May  5 22:01:32 cz101 kernel: [627319.294044]  ffff880107721cb8 0000000000000086 0000000000015bc0 0000000000015bc0
May  5 22:01:32 cz101 kernel: [627319.294050]  ffff880106e55f80 ffff880107721fd8 0000000000015bc0 ffff880106e55bc0
May  5 22:01:32 cz101 kernel: [627319.294056]  0000000000015bc0 ffff880107721fd8 0000000000015bc0 ffff880106e55f80
May  5 22:01:32 cz101 kernel: [627319.294071] Call Trace:
May  5 22:01:32 cz101 kernel: [627319.294078]  [<ffffffff8153f867>] __mutex_lock_slowpath+0xe7/0x170
May  5 22:01:32 cz101 kernel: [627319.294084]  [<ffffffff8105b1d5>] ? wake_up_process+0x15/0x20
May  5 22:01:32 cz101 kernel: [627319.294089]  [<ffffffff8153f75b>] mutex_lock+0x2b/0x50
May  5 22:01:32 cz101 kernel: [627319.294104]  [<ffffffffa022be36>] i915_gem_busy_ioctl+0x46/0xd0 [i915]
May  5 22:01:32 cz101 kernel: [627319.294125]  [<ffffffffa01b6e2a>] drm_ioctl+0x27a/0x480 [drm]
May  5 22:01:32 cz101 kernel: [627319.294144]  [<ffffffffa022bdf0>] ? i915_gem_busy_ioctl+0x0/0xd0 [i915]
May  5 22:01:32 cz101 kernel: [627319.294154]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
May  5 22:01:32 cz101 kernel: [627319.294166]  [<ffffffff81152a92>] vfs_ioctl+0x22/0xa0
May  5 22:01:32 cz101 kernel: [627319.294174]  [<ffffffff81152d41>] do_vfs_ioctl+0x81/0x380
May  5 22:01:32 cz101 kernel: [627319.294183]  [<ffffffff811431df>] ? vfs_read+0x12f/0x1a0
May  5 22:01:32 cz101 kernel: [627319.294191]  [<ffffffff811530c1>] sys_ioctl+0x81/0xa0
May  5 22:01:32 cz101 kernel: [627319.294201]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
May  5 22:03:32 cz101 kernel: [627439.240238] i915          D 0000000000000000     0   765      2 0x00000000
May  5 22:03:32 cz101 kernel: [627439.240245]  ffff88010abb9d40 0000000000000046 0000000000015bc0 0000000000015bc0
May  5 22:03:32 cz101 kernel: [627439.240252]  ffff8801306e5f80 ffff88010abb9fd8 0000000000015bc0 ffff8801306e5bc0
May  5 22:03:32 cz101 kernel: [627439.240258]  0000000000015bc0 ffff88010abb9fd8 0000000000015bc0 ffff8801306e5f80
May  5 22:03:32 cz101 kernel: [627439.240264] Call Trace:
May  5 22:03:32 cz101 kernel: [627439.240279]  [<ffffffff8153f867>] __mutex_lock_slowpath+0xe7/0x170
May  5 22:03:32 cz101 kernel: [627439.240289]  [<ffffffff81058620>] ? finish_task_switch+0x50/0xe0
May  5 22:03:32 cz101 kernel: [627439.240294]  [<ffffffff8153f75b>] mutex_lock+0x2b/0x50
May  5 22:03:32 cz101 kernel: [627439.240321]  [<ffffffffa022c37d>] i915_gem_retire_work_handler+0x3d/0xa0 [i915]
May  5 22:03:32 cz101 kernel: [627439.240339]  [<ffffffffa022c340>] ? i915_gem_retire_work_handler+0x0/0xa0 [i915]
May  5 22:03:32 cz101 kernel: [627439.240348]  [<ffffffff81080777>] run_workqueue+0xc7/0x1a0
May  5 22:03:32 cz101 kernel: [627439.240354]  [<ffffffff810808f3>] worker_thread+0xa3/0x110
May  5 22:03:32 cz101 kernel: [627439.240360]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
May  5 22:03:32 cz101 kernel: [627439.240366]  [<ffffffff81080850>] ? worker_thread+0x0/0x110
May  5 22:03:32 cz101 kernel: [627439.240371]  [<ffffffff81084fa6>] kthread+0x96/0xa0
May  5 22:03:32 cz101 kernel: [627439.240377]  [<ffffffff810141ea>] child_rip+0xa/0x20
May  5 22:03:32 cz101 kernel: [627439.240382]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
May  5 22:03:32 cz101 kernel: [627439.240386]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
May  5 22:03:32 cz101 kernel: [627439.240407] Xorg          D 0000000000000000     0   995    916 0x00400004
May  5 22:03:32 cz101 kernel: [627439.240413]  ffff880107721cb8 0000000000000086 0000000000015bc0 0000000000015bc0
May  5 22:03:32 cz101 kernel: [627439.240418]  ffff880106e55f80 ffff880107721fd8 0000000000015bc0 ffff880106e55bc0
May  5 22:03:32 cz101 kernel: [627439.240424]  0000000000015bc0 ffff880107721fd8 0000000000015bc0 ffff880106e55f80
May  5 22:03:32 cz101 kernel: [627439.240430] Call Trace:
May  5 22:03:32 cz101 kernel: [627439.240436]  [<ffffffff8153f867>] __mutex_lock_slowpath+0xe7/0x170
May  5 22:03:32 cz101 kernel: [627439.240443]  [<ffffffff8105b1d5>] ? wake_up_process+0x15/0x20
May  5 22:03:32 cz101 kernel: [627439.240448]  [<ffffffff8153f75b>] mutex_lock+0x2b/0x50
May  5 22:03:32 cz101 kernel: [627439.240463]  [<ffffffffa022be36>] i915_gem_busy_ioctl+0x46/0xd0 [i915]
May  5 22:03:32 cz101 kernel: [627439.240481]  [<ffffffffa01b6e2a>] drm_ioctl+0x27a/0x480 [drm]
May  5 22:03:32 cz101 kernel: [627439.240496]  [<ffffffffa022bdf0>] ? i915_gem_busy_ioctl+0x0/0xd0 [i915]
May  5 22:03:32 cz101 kernel: [627439.240503]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
May  5 22:03:32 cz101 kernel: [627439.240510]  [<ffffffff81152a92>] vfs_ioctl+0x22/0xa0
May  5 22:03:32 cz101 kernel: [627439.240515]  [<ffffffff81152d41>] do_vfs_ioctl+0x81/0x380
May  5 22:03:32 cz101 kernel: [627439.240521]  [<ffffffff811431df>] ? vfs_read+0x12f/0x1a0
May  5 22:03:32 cz101 kernel: [627439.240526]  [<ffffffff811530c1>] sys_ioctl+0x81/0xa0
May  5 22:03:32 cz101 kernel: [627439.240532]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
May  5 22:05:32 cz101 kernel: [627559.185048] i915          D 0000000000000000     0   765      2 0x00000000
May  5 22:05:32 cz101 kernel: [627559.185056]  ffff88010abb9d40 0000000000000046 0000000000015bc0 0000000000015bc0
May  5 22:05:32 cz101 kernel: [627559.185063]  ffff8801306e5f80 ffff88010abb9fd8 0000000000015bc0 ffff8801306e5bc0
May  5 22:05:32 cz101 kernel: [627559.185068]  0000000000015bc0 ffff88010abb9fd8 0000000000015bc0 ffff8801306e5f80
May  5 22:05:32 cz101 kernel: [627559.185074] Call Trace:
May  5 22:05:32 cz101 kernel: [627559.185089]  [<ffffffff8153f867>] __mutex_lock_slowpath+0xe7/0x170
May  5 22:05:32 cz101 kernel: [627559.185099]  [<ffffffff81058620>] ? finish_task_switch+0x50/0xe0
May  5 22:05:32 cz101 kernel: [627559.185104]  [<ffffffff8153f75b>] mutex_lock+0x2b/0x50
May  5 22:05:32 cz101 kernel: [627559.185131]  [<ffffffffa022c37d>] i915_gem_retire_work_handler+0x3d/0xa0 [i915]
May  5 22:05:32 cz101 kernel: [627559.185149]  [<ffffffffa022c340>] ? i915_gem_retire_work_handler+0x0/0xa0 [i915]
May  5 22:05:32 cz101 kernel: [627559.185156]  [<ffffffff81080777>] run_workqueue+0xc7/0x1a0
May  5 22:05:32 cz101 kernel: [627559.185162]  [<ffffffff810808f3>] worker_thread+0xa3/0x110
May  5 22:05:32 cz101 kernel: [627559.185169]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
May  5 22:05:32 cz101 kernel: [627559.185175]  [<ffffffff81080850>] ? worker_thread+0x0/0x110
May  5 22:05:32 cz101 kernel: [627559.185179]  [<ffffffff81084fa6>] kthread+0x96/0xa0
May  5 22:05:32 cz101 kernel: [627559.185186]  [<ffffffff810141ea>] child_rip+0xa/0x20
May  5 22:05:32 cz101 kernel: [627559.185191]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
May  5 22:05:32 cz101 kernel: [627559.185195]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
May  5 22:05:32 cz101 kernel: [627559.185215] Xorg          D 0000000000000000     0   995    916 0x00400004
May  5 22:05:32 cz101 kernel: [627559.185221]  ffff880107721cb8 0000000000000086 0000000000015bc0 0000000000015bc0
May  5 22:05:32 cz101 kernel: [627559.185227]  ffff880106e55f80 ffff880107721fd8 0000000000015bc0 ffff880106e55bc0
May  5 22:05:32 cz101 kernel: [627559.185232]  0000000000015bc0 ffff880107721fd8 0000000000015bc0 ffff880106e55f80
May  5 22:05:32 cz101 kernel: [627559.185238] Call Trace:
May  5 22:05:32 cz101 kernel: [627559.185244]  [<ffffffff8153f867>] __mutex_lock_slowpath+0xe7/0x170
May  5 22:05:32 cz101 kernel: [627559.185251]  [<ffffffff8105b1d5>] ? wake_up_process+0x15/0x20
May  5 22:05:32 cz101 kernel: [627559.185256]  [<ffffffff8153f75b>] mutex_lock+0x2b/0x50
May  5 22:05:32 cz101 kernel: [627559.185272]  [<ffffffffa022be36>] i915_gem_busy_ioctl+0x46/0xd0 [i915]
May  5 22:05:32 cz101 kernel: [627559.185289]  [<ffffffffa01b6e2a>] drm_ioctl+0x27a/0x480 [drm]
May  5 22:05:32 cz101 kernel: [627559.185304]  [<ffffffffa022bdf0>] ? i915_gem_busy_ioctl+0x0/0xd0 [i915]
May  5 22:05:32 cz101 kernel: [627559.185310]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
May  5 22:05:32 cz101 kernel: [627559.185318]  [<ffffffff81152a92>] vfs_ioctl+0x22/0xa0
May  5 22:05:32 cz101 kernel: [627559.185323]  [<ffffffff81152d41>] do_vfs_ioctl+0x81/0x380
May  5 22:05:32 cz101 kernel: [627559.185329]  [<ffffffff811431df>] ? vfs_read+0x12f/0x1a0
May  5 22:05:32 cz101 kernel: [627559.185334]  [<ffffffff811530c1>] sys_ioctl+0x81/0xa0
May  5 22:05:32 cz101 kernel: [627559.185340]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
May  5 22:07:32 cz101 kernel: [627679.132282] i915          D 0000000000000000     0   765      2 0x00000000
May  5 22:07:32 cz101 kernel: [627679.132289]  ffff88010abb9d40 0000000000000046 0000000000015bc0 0000000000015bc0
May  5 22:07:32 cz101 kernel: [627679.132296]  ffff8801306e5f80 ffff88010abb9fd8 0000000000015bc0 ffff8801306e5bc0
May  5 22:07:32 cz101 kernel: [627679.132302]  0000000000015bc0 ffff88010abb9fd8 0000000000015bc0 ffff8801306e5f80
May  5 22:07:32 cz101 kernel: [627679.132308] Call Trace:
May  5 22:07:32 cz101 kernel: [627679.132322]  [<ffffffff8153f867>] __mutex_lock_slowpath+0xe7/0x170
May  5 22:07:32 cz101 kernel: [627679.132331]  [<ffffffff81058620>] ? finish_task_switch+0x50/0xe0
May  5 22:07:32 cz101 kernel: [627679.132336]  [<ffffffff8153f75b>] mutex_lock+0x2b/0x50
May  5 22:07:32 cz101 kernel: [627679.132363]  [<ffffffffa022c37d>] i915_gem_retire_work_handler+0x3d/0xa0 [i915]
May  5 22:07:32 cz101 kernel: [627679.132379]  [<ffffffffa022c340>] ? i915_gem_retire_work_handler+0x0/0xa0 [i915]
May  5 22:07:32 cz101 kernel: [627679.132388]  [<ffffffff81080777>] run_workqueue+0xc7/0x1a0
May  5 22:07:32 cz101 kernel: [627679.132394]  [<ffffffff810808f3>] worker_thread+0xa3/0x110
May  5 22:07:32 cz101 kernel: [627679.132400]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
May  5 22:07:32 cz101 kernel: [627679.132406]  [<ffffffff81080850>] ? worker_thread+0x0/0x110
May  5 22:07:32 cz101 kernel: [627679.132410]  [<ffffffff81084fa6>] kthread+0x96/0xa0
May  5 22:07:32 cz101 kernel: [627679.132417]  [<ffffffff810141ea>] child_rip+0xa/0x20
May  5 22:07:32 cz101 kernel: [627679.132422]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
May  5 22:07:32 cz101 kernel: [627679.132426]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
May  5 22:07:32 cz101 kernel: [627679.132446] Xorg          D 0000000000000000     0   995    916 0x00400004
May  5 22:07:32 cz101 kernel: [627679.132452]  ffff880107721cb8 0000000000000086 0000000000015bc0 0000000000015bc0
May  5 22:07:32 cz101 kernel: [627679.132458]  ffff880106e55f80 ffff880107721fd8 0000000000015bc0 ffff880106e55bc0
May  5 22:07:32 cz101 kernel: [627679.132464]  0000000000015bc0 ffff880107721fd8 0000000000015bc0 ffff880106e55f80
May  5 22:07:32 cz101 kernel: [627679.132469] Call Trace:
May  5 22:07:32 cz101 kernel: [627679.132475]  [<ffffffff8153f867>] __mutex_lock_slowpath+0xe7/0x170
May  5 22:07:32 cz101 kernel: [627679.132482]  [<ffffffff8105b1d5>] ? wake_up_process+0x15/0x20
May  5 22:07:32 cz101 kernel: [627679.132487]  [<ffffffff8153f75b>] mutex_lock+0x2b/0x50
May  5 22:07:32 cz101 kernel: [627679.132501]  [<ffffffffa022be36>] i915_gem_busy_ioctl+0x46/0xd0 [i915]
May  5 22:07:32 cz101 kernel: [627679.132520]  [<ffffffffa01b6e2a>] drm_ioctl+0x27a/0x480 [drm]
May  5 22:07:32 cz101 kernel: [627679.132535]  [<ffffffffa022bdf0>] ? i915_gem_busy_ioctl+0x0/0xd0 [i915]
May  5 22:07:32 cz101 kernel: [627679.132541]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
May  5 22:07:32 cz101 kernel: [627679.132550]  [<ffffffff81152a92>] vfs_ioctl+0x22/0xa0
May  5 22:07:32 cz101 kernel: [627679.132555]  [<ffffffff81152d41>] do_vfs_ioctl+0x81/0x380
May  5 22:07:32 cz101 kernel: [627679.132561]  [<ffffffff811431df>] ? vfs_read+0x12f/0x1a0
May  5 22:07:32 cz101 kernel: [627679.132566]  [<ffffffff811530c1>] sys_ioctl+0x81/0xa0
May  5 22:07:32 cz101 kernel: [627679.132574]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b

```if anyone has any ideas, or if anyone can suggest a better place to post the data from messages...

thanks to everyone on nzlug for getting me this far!

---

### Post by icepop on 2010-05-06
here's a big fat clue that i didn't notice last night... X is in uninterruptible sleep.

```

# ps auwx | egrep X
root       995  2.0  1.2 163248 49804 tty7     Ds+  Apr28 217:01 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-q8m9Et/database -nolisten tcp vt7

```i tried to kill it with alt-sysReq-k and it didn't work. then via ssh i tried killing it (with SIGTERM implied) then with SIGKILL. nothing. then i noticed that it's in uninterruptible sleep. then i scrolled back in my terminal windows (on the freebsd box that i'm ssh-ing from) and found that it's been that way since last night.

trying to kill the parent process (gdm-simple-slave) isn't getting far, and now "ps" hangs. even rebooting from CLI isn't doing anything useful. the whole damn thing is hung. just before poking it in the eye i nmap'd it nmap says it's down.

---

### Post by barinov2000 on 2010-05-11
Integrated GMA HD on Acer Aspire 5740 - same problem.

To get out of frozen GUI do this:

Holding down Alt and SysRq (which is the Print Screen key) while slowly  typing REISUB will get you safely restarted. REISUO will do a shutdown rather than a restart.

source: [http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

On another note: the most recent updates seem to have made the problem go away. though, I haven't done any real stress test. Last times it happened during starting a screen-saver and changing a desktop background.

Good luck!

---

### Post by -curly- on 2010-05-13
> **barinov2000 said:**
> Integrated GMA HD on Acer Aspire 5740 - same problem.

To get out of frozen GUI do this:

Holding down Alt and SysRq (which is the Print Screen key) while slowly  typing REISUB will get you safely restarted. REISUO will do a shutdown rather than a restart.

source: [http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

On another note: the most recent updates seem to have made the problem go away. though, I haven't done any real stress test. Last times it happened during starting a screen-saver and changing a desktop background.

Good luck!
Wow, that actually worked, thanks!

The updates have done nothing for me.  My system has frozen twice today.  I am nearing the point of giving up and installing a different OS.

This is on an Acer 5740 with Intel GMA HD.

---

### Post by TNT07 on 2010-05-24
I have an Acer Aspire 7740 with i5 and integrated GMA HD. I am running Lucid with the latest stable drivers and updates.
I have had a ton of random freezing. Mostly during VirtualBox sessions, when screensaver is running  or when I resize a window.
Only Alt Sys REISUB works. It seems I don't get them anymore when I inactivate Compiz (it's been several days so far and no freezing with Metacity). I miss the compiz effects.
I hope somebody will find a solution to this problem.

---

### Post by fishbulb1022 on 2010-06-01
Hello, there is a large thread on laptops freezing with 10.04 here [http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)
seems to be a big problem. My suggestion is to go here [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) and look at updating to the mainline kernel...I did it yesterday and have had no freezes since then. I'm on an Acer Aspire 7740-6656. Good Luck!

---

### Post by Saghaulor on 2010-06-01
I had stability issues. I turned off Compiz and my system has been stable ever since.

I have a different problem. My brightness hotkeys trigger the brightness meter to move up and down, however, the actual brightness is unaffected.

I've upgraded to upstream kernel 2.6.34, and updated xorg from the edgers ppa,  so I'm running xserver-xorg-video-intel v 2.2.11, and that did not fix the issue.

Is anyone else having this brightness issue? Any suggestions?

---

### Post by Saghaulor on 2010-06-03
> **Saghaulor said:**
> I had stability issues. I turned off Compiz and my system has been stable ever since.

I have a different problem. My brightness hotkeys trigger the brightness meter to move up and down, however, the actual brightness is unaffected.

I've upgraded to upstream kernel 2.6.34, and updated xorg from the edgers ppa,  so I'm running xserver-xorg-video-intel v 2.2.11, and that did not fix the issue.

Is anyone else having this brightness issue? Any suggestions?

No on is having issues with the lcd brightness toggle not actually toggling the brightness level?

---

### Post by fishbulb1022 on 2010-06-04
I'm having brightness the same issue, where the brightness function keys bring up the notification, but do not actually effect brightness.

---

### Post by Saghaulor on 2010-06-09
This thread offers some suggestions, however, none of them seemed to help me.

[http://ubuntuforums.org/showthread.php?t=1492275]("http://ubuntuforums.org/showthread.php?t=1492275")

Any other suggestions?

---

### Post by Saghaulor on 2010-06-14
bump

---

### Post by Saghaulor on 2010-06-14
This bug report is worth noting. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573984]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573984")

---

### Post by fondle-em on 2010-06-15
> **Saghaulor said:**
> This thread offers some suggestions, however, none of them seemed to help me.

[http://ubuntuforums.org/showthread.php?t=1492275]("http://ubuntuforums.org/showthread.php?t=1492275")

Any other suggestions?

Your mileage may vary *greatly* - however, in a Thinkpad T510 with a Core i5 and integrated Intel Arrandale graphics, installing the 2.6.32-23.37 kernel from lucid-proposed and the [X-Updates PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") containing newer Intel Graphics drivers seems to have cleared things up.  It's been stable for three days with Compiz running.  Previously you wouldn't have gotten it to last 3 hours running Compiz.

---

### Post by Saghaulor on 2010-06-16
> **fondle-em said:**
> Your mileage may vary *greatly* - however, in a Thinkpad T510 with a Core i5 and integrated Intel Arrandale graphics, installing the 2.6.32-23.37 kernel from lucid-proposed and the [X-Updates PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") containing newer Intel Graphics drivers seems to have cleared things up.  It's been stable for three days with Compiz running.  Previously you wouldn't have gotten it to last 3 hours running Compiz.

I'm actually running the newest upstream kernel and upstream xorg.

See below:
> uname -a
Linux stephenaghaulor-laptop 2.6.34-020634-generic #020634 SMP Mon May 17 19:27:49 UTC 2010 x86_64 GNU/Linux
stephenaghaulor@stephenaghaulor-laptop:~$ aptitude show xserver-xorg-core
Package: xserver-xorg-core
State: installed
Automatically installed: no
Version: 2:1.7.6-2ubuntu7.1
Priority: optional
Section: x11
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Uncompressed Size: 4,989k
Depends: xserver-common (>= 2:1.7.6-2ubuntu7.1), xserver-xorg, udev (>= 149),
         libc6 (>= 2.7), libdrm2 (>= 2.3.1), libgcrypt11 (>= 1.4.2),
         libpciaccess0 (>= 0.10.7), libpixman-1-0 (>= 0.15.16), libudev0 (>=
         147), libxau6, libxdmcp6, libxfont1 (>= 1:1.2.9)
Recommends: libgl1-mesa-dri (>= 7.1~rc1)
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Conflicts: xserver-common (< 7), xserver-xfree86 (< 1:7.0.0), xserver-xorg (<
           6.8.2-38), xserver-xorg-input, xserver-xorg-input-2,
           xserver-xorg-input-2.1, xserver-xorg-input-4,
           xserver-xorg-input-wacom (< 0.7.8), xserver-xorg-video,
           xserver-xorg-video-1.0, xserver-xorg-video-1.9, xserver-xorg-video-2,
           xserver-xorg-video-4, xserver-xorg-video-5
Replaces: xserver-common (< 7), xserver-xfree86 (< 1:7.0.0), xserver-xorg (<
          6.8.2-38)
Provides: xserver
Description: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers. 
 
 The Xorg server supports most modern graphics hardware from most vendors, and
 supersedes all XFree86 X servers. 
 
 More information about X.Org can be found at: <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg> 
 
 This package is built from the X.org xserver module.


stephenaghaulor@stephenaghaulor-laptop:~$ aptitude show xserver-xorg-video-intelPackage: xserver-xorg-video-intel
State: installed
Automatically installed: no
Version: 2:2.11.0-1ubuntu1~xup
Priority: optional
Section: x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,253k
Depends: libc6 (>= 2.4), libdrm-intel1 (>= 2.4.13), libdrm2 (>= 2.4.17),
libpciaccess0 (>= 0.8.0+git20071002), libx11-6 (>= 0), libx11-xcb1,
libxcb-aux0 (>= 0.3.6), libxcb-dri2-0 (>= 0), libxcb1 (>= 0), libxext6,
libxfixes3 (>= 1:4.0.1), libxv1, libxvmc1, xserver-xorg-core (>=
2:1.6.99.900)
Conflicts: 915resolution, xserver-xorg-driver-i810, xserver-xorg-video-i810 (<
2:1.9.91-1), xserver-xorg-video-i810-modesetting,
xserver-xorg-video-intel-modesetting
Replaces: xserver-xorg (< 6.8.2-35), xserver-xorg-driver-i810,
xserver-xorg-video-i810 (< 2:1.9.91-1),
xserver-xorg-video-i810-modesetting,
xserver-xorg-video-intel-modesetting
Provides: xserver-xorg-video-6
Description: X.Org X server -- Intel i8xx, i9xx display driver
This package provides the driver for the Intel i8xx and i9xx family of
chipsets, including i810, i815, i830, i845, i855, i865, i915, i945 and i965
series chips. 

This package also provides XvMC (XVideo Motion Compensation) drivers for
i810/i815 and i9xx and newer chipsets. 

More information about X.Org can be found at: <URL:http://www.X.org>
<URL:http://xorg.freedesktop.org>
<URL:http://lists.freedesktop.org/mailman/listinfo/xorg> 

This package is built from the X.org xf86-video-intel driver module.

stephenaghaulor@stephenaghaulor-laptop:~$

$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


---

### Post by Saghaulor on 2010-06-23
Now I'm getting somewhere.

There seems to be an issue with permissions on /proc/acpi/video/GFX0/DD02/brightness

After ```
sudo su
``` and then ```
echo 50 > /proc/acpi/video/GFX0/DD02/brightness
``` my brightness level changed.

See my post here.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573984/comments/27](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573984/comments/27)

---

### Post by -samuel- on 2010-07-16
apparently our integrated graphics (i have a i350M proccesor) are officialy unsopported yet my friend. just configure the repositories of xorg for the xorg to have the last updates and wait.
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) lucid main
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) lucid main
now work!
install the repositories, upgrade all your drivers (apt-get upgrade) and install kernell 2.6.35
all work fine!

---

### Post by luckyknight on 2010-08-18
I want to build a HTPC running a Core i3 530 and Linux (running XBMC). Does anyone know if xf86-video-intel supports 23.976Hz? (for true 24fps playback)

---

