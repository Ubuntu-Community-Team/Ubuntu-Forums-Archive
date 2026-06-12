---
title: "82865G Integrated Graphics Controller"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by super kim on 2009-07-30
well thats the on board card, but i dont think i have the right drivers installed since there is nvidia x server settings listed in my administration tab.

my graphics is very slow (2d only, i'm not playing games on my pc) and when i try to open a vido the player just closes itself?!?

where do i go from here i would like to check that i have the right driver installed but i couldnt find out from my scroogle search.

---

### Post by overdrank on 2009-07-30
> **super kim said:**
> well thats the on board card, but i dont think i have the right drivers installed since there is nvidia x server settings listed in my administration tab.

my graphics is very slow (2d only, i'm not playing games on my pc) and when i try to open a vido the player just closes itself?!?

where do i go from here i would like to check that i have the right driver installed but i couldnt find out from my scroogle search.

You may use the command lspci in the terminal located under applications, accessories. This will identify your hardware.
Look for VGA. It is possible to have a additional graphics card along with the integrated graphics chipset.
if you have intel graphics only you may look at the link in my signature.

---

### Post by komputes on 2009-07-30
If it's an Intel card, there will be no nvidia settings utility or binary driver (it could be there if you installed it - but it will not make a difference if you have an intel card). If you are not able to get the performance you expect, feel free to open a bug against the Intel Driver:

[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-intel](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-intel)

---

### Post by super kim on 2009-08-02
$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by super kim on 2009-08-02
i know the card is an intel i wanted to know how i can find out which driver is in use? and the nvidia stuff is on here because my friend thought he needed it for compiz to work. please dont start i know!! i wasnt there in fact this wasnt my computer till i broke mine and got this one as a donation, it is slow and old but i know the graphics card works better than it currently is.
the problem is... i cant view any movies, flash mpgs avis anything. they really should work i know there is nvidia drivers on the computer i can see them in the synaptic package manager.
i want to know a, how to purge the all nvidia drivers and ALL related stuff using my terminal, b how i can set up ubuntu to play videos. 
and by the way i dont want compiz, i love the epo wall and its usefull but this machine can't handle too much at once. i just want basic functions, like videos lol

---

### Post by super kim on 2009-08-02
OK this seem simple enough.
first i'll use the synaptic package manager to remove/purge:
nvidia-settings
nvidida-96-kernel-source
nvidia-common
nvidia-71-modaliases
nvidia-173-modaliases
nvidia-180-modaliases
nvidia-96-modaliases
xserver-xorg-video-nv
smartdimmer
nvidia-glx-96

then after i reboot, my computer wont work lol


no it still works, well the videos wont work but it still boots.
i read through this thread [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
but the warning at the start has scared me a little as this is my third computer in 7six days and the i dont want to  break it.
is there a fool proof method of fixing the bug mentioned in the above link?

---

### Post by HotShotDJ on 2009-08-02
If -- **and ONLY IF** -- you are using Jaunty (Ubuntu 9.04), please see the [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582")

---

### Post by super kim on 2009-08-02
yea that thread has a warning at the start for people like me lol which steps should i follow?
yes i am using jaunty 9.04, yes i have an intel graphics card, and no it doesnt work yet. see the word yet, that shows optimism and determination ha ha

this is the relevant bit from my xorg:


Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

---

### Post by HotShotDJ on 2009-08-02
> **super kim said:**
> is there a fool proof method of fixing the bug mentioned in the above link?If for any reason you do not want to follow the instructions for fixing the Intel video problems in Jaunty -- and it is true that this fix is not for the "faint of heart" :D -- your best bet is to reinstall Ubuntu using Hardy (Ubuntu 8.04 LTS).  The LTS versions (Long-Term Support) are quite stable and less likely to introduce regressions like the current problems with Intel graphics in Jaunty.

Another option is to revert to the older driver version 2.4, which I can personally confirm works rather well... and is a less scary fix than the method I referenced earlier.  See: [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

EDIT: You know... the more I think about it, the more I think reverting to 2.4 is the better option for you.  If, for any reason, it doesn't work as expected, it is very easy to remove the changes.  But I think it will work and shouldn't cause you any undue fear and trepidation. ;)

---

### Post by super kim on 2009-08-02
what is this mtrr bug? do i have to fix that? i wont reinstall ubuntu for many reasons the biggest is i dont have a cd drive at the moment. i will be brave and try the instructions and carefully too, i just hope it works

and please can somebody tell me how i determin which drivers i am using, that would be really great there must surely be a terminal code to do this if not why not?!?

---

### Post by cwsnyder on 2009-08-02
Whether you use 8.04 (Hardy Heron) or 9.04 (Jaunty Jackalope), you need to go into Synaptic and make sure you have added the 'ubuntu-restricted-extras' package for your version of ubuntu/kubuntu/edubuntu/etc. added to allow you to view videos other than ogg-theora videos.

---

### Post by super kim on 2009-08-02
is it true that theres a magical koala that can help with this?

from what i've been reading the latest ubuntu release karmic koala, has no issues with the intel graphics. if this is the case i will get a cd drive from downstairs and plug in a fresh hdd and install on that, although the iso i downloaded says its an alpha, does that mean it wont work easily?

what the hell i'm tring it. i will use a different hdd so i can always just format the disk if it dosnt work. hopefully i wont need to follow instructions i dont fully understand and the new kernel will have the intel support i deserve lol

:popcorn:

---

### Post by HotShotDJ on 2009-08-02
> **super kim said:**
> what is this mtrr bug? do i have to fix that?Don't worry about that for now.  The bug has pretty much been worked out in the newest drivers and kernels (which you won't have unless you use the "scary" Intel performance guide).  If you revert to the older driver as outlined in the second link I gave you, you won't have to deal with the mttr problem at all.
> **super kim said:**
> and please can somebody tell me how i determin which drivers i am using, that would be really great there must surely be a terminal code to do this if not why not?!?Undoubtedly, you are using the default xorg drivers that come with Jaunty. You can use Synaptic (System --> Administration --> Synaptic Package Manager) and run a search for xserver-xorg-video-intel to determine the exact version you are running

---

### Post by HotShotDJ on 2009-08-02
> **super kim said:**
> what the hell i'm tring it. i will use a different hdd so i can always just format the disk if it dosnt work. hopefully i wont need to follow instructions i dont fully understand and the new kernel will have the intel support i deserve lol==Using Karmic will fix the Intel problem, but it will also introduce you to the world of pre-release software.  Karmic is NOT a stable distribution yet, and I foresee much yelling and gnashing of teeth in your future if you go that route. If the Jaunty Intel Performance Guide scared you, then a complete pre-release operating system is definitely NOT a good idea. I strongly recommend against it.  But, as always, "Your Computer, Your Choice."

---

### Post by super kim on 2009-08-02
when i installed the jaunty jackalope the first time it was pre-release and yes i had a few teething problems but the koalas beta release date is the 10th no? i could wait i suppose lol probably wont tho i'm not an expert by any means buuuut and stop me if i'm wrong but the changes made in the koala should make my computer work better, since jaunty doesn't work so well with intel graphics chips and the karmic does... i don't know all the changes but are they not mostly relating to netwoks and therefore not too relevant for me? i don't know i will have a crack at it al the same.
cwsnyder, i did not have the ubuntu-restricted-extras, i have now added the package, but the player still just closes up as soon as the video plays. humpf

---

### Post by super kim on 2009-08-02
OK i will go and get microwave pizza and then i'll follow the so called scary instructions btw i dont think they are scary looking in fact they are pretty well written i am just being cautious since my sleep button adventure a few days ago.  i will in fact be so cautius that i will post here a log of what i am doing so if/when anything goes wrong hopefully some one will see where i've mucked up :)  but first the food, its never good to work on an empty belly:popcorn:

---

### Post by HotShotDJ on 2009-08-02
There is no way to predict what kind of problems you may run into when using pre-release software (alpha or beta).  You may be going along nicely, and then the next set up upgrades will come out and *bang* your system is crashing all over the place.  If you don't mind breakage and trouble-shooting, then, by all means, use Koala -- after all, the developers will only be able to fix things if there are people out there using the software and discovering the bugs.

But, my general impression of you (and I may be wrong) is that you have a relatively low tolerance for breakage and bug testing/fixing.  That is why I recommend strongly against your using Koala.  Maybe you'll be lucky and not run into trouble.  But, in my opinion, that would be a sucker's bet.

Is there any reason that you are resistant to reverting to the 2.4 driver as outlined at [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) ??  It may very well correct your problem simply and cleanly with having to mess around with kernel upgrades or pre-released operating systems.

---

### Post by HotShotDJ on 2009-08-02
> **super kim said:**
> OK i will go and get microwave pizza and then i'll follow the so called scary instructions Mmmmmmmm... Pizza! :)

I agree, the instructions are really not that scary and are very well written.  I just called them that so I wouldn't have to keep typing "Jaunty Intel Video Performance Guide."

Perhaps you should consider a "stepped" approach... that is, starting with the simplest, least intrusive method, and then moving to the next method only if the previous step does not produce satisfactory results.. so here are my recommendations -- of course, you can do whatever you want :)

1) [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
2) [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) (starting with the safe method, and working your way up as needed)
3) Karmic Koala (very last resort, although if the first two steps don't work, I doubt Karmic will help).

Good Luck and let us know how it works out.

---

### Post by super kim on 2009-08-02
> **HotShotDJ said:**
> 
Perhaps you should consider a "stepped" approach... that is, starting with the simplest, least intrusive method, and then moving to the next method only if the previous step does not produce satisfactory results...

what does this do?... does it just revert the intel kernel or does it have effect on the whole thing? if it's just the intel stuff then i would try that now as it seems, as you say the simplest and least intrusive method, although i will try the koala tomorrow to see how that works but as i said earlier i would do it on a spare hard drive.

---

### Post by HotShotDJ on 2009-08-02
> **super kim said:**
> what does this do?... does it just revert the intel kernel or does it have effect on the whole thing?It does exactly what the instructions tell you its doing.  It removes the current, buggy, version of xserver-xorg-video-intel and replaces it with the older (2.4) version of xserver-xorg-video-intel.  It doesn't touch the kernel.

---

### Post by super kim on 2009-08-02
how can i enable the dri ? i have changed the buggy xserver-video-intel and replaced it with a newer version that does not freeze with dri enabled
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by super kim on 2009-08-02
> **super kim said:**
> how can i enable the dri ? i have changed the buggy xserver-video-intel and replaced it with a newer version that does not freeze with dri enabled
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
  

this is how i understand it...

when the new jaunty was released the dri would freeze with some intel chips, my chip is one thats a problem, so at some point there was an update that disabled the dri for all the i865 chips since stability was more important than performance for jauntys develpers.
if i were to revert to an older xserver-video-intel this would fix the problem-ish but the new driver has also been reported as a fix for bug #317457 however simply updating the drivers is not enough, i need to remove the patch that by default disables the dri for all the i865 graphics cards. for once i have read up and not just clicked OK, i hope this works for me, but a bit of help with the dri patch removal would be much appreciated :D

---

### Post by HotShotDJ on 2009-08-02
> **super kim said:**
> how can i enable the dri ? i have changed the buggy xserver-video-intel and replaced it with a newer version that does not freeze with dri enabled
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
Hi, Super Kim.  I really can't help you any further.  There are several methods for correcting your problem out there that are known to work and for which I've provided you links.  For whatever reason, you have chosen not to follow them but are instead making scatter-shot changes to your system.  That is certainly your prerogative.

Once again... [THIS]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") will probably fix you problem. If not, then try [THIS]("http://ubuntuforums.org/showthread.php?t=1130582").  You do not, of course, have to follow either one of those known fixes.  You are free to do everything under the sun except one of those known fixes, if that is what you fancy.  I have given you all the knowledge I have on this issue.  Accept it or reject it as you wish.

---

### Post by super kim on 2009-08-02
> **HotShotDJ said:**
> There is no way to predict what kind of problems you may run into when using pre-release software (alpha or beta).  You may be going along nicely, and then the next set up upgrades will come out and *bang* your system is crashing all over the place.  If you don't mind breakage and trouble-shooting, then, by all means, use Koala -- after all, the developers will only be able to fix things if there are people out there using the software and discovering the bugs.

But, my general impression of you (and I may be wrong) is that you have a relatively low tolerance for breakage and bug testing/fixing.  That is why I recommend strongly against your using Koala.  Maybe you'll be lucky and not run into trouble.  But, in my opinion, that would be a sucker's bet.

Is there any reason that you are resistant to reverting to the 2.4 driver as outlined at [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) ??  It may very well correct your problem simply and cleanly with having to mess around with kernel upgrades or pre-released operating systems.
 
i found this on [https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance) thats what swayed me into trying the newer driver as oppsed to the older driver.
**Problem: EXA performance has regressed since Intrepid.  Why not stick with the old driver?**

 A common question that comes up is, if the performance has regressed since Intrepid, why not just stick with the old driver? 
There are two problems with this. 
First, one of the main reasons for upgrading drivers is to gain support for newer hardware. We would lose this support were we to revert. Upgraded drivers also include numerous bug fixes incorporated since the last release but not backported to the previous stable tree. We would lose those as well. 
There are many people who do *not* have performance troubles, who would thus suffer much more significant regressions (crashes, freezes, failure to boot, etc.) were we to do this. 
Second, reverting the -intel driver probably would not solve the issue. -intel just provides 2d support, but many of the performance problems are in 3d code... which means that you would need to revert xorg-server, mesa, libdrm, and probably more. 
One of the main differences between Jaunty and Intrepid is that we are using the GEM memory manager, both for UXA and EXA. At least one person has reported good results when disabling GEM via the patch at [http://paste.ubuntu.com/142337/](http://paste.ubuntu.com/142337/).  This hasn't been widely tested though, so we're not shipping it in Jaunty at this time.

---

### Post by thiebaude on 2009-08-03
This is what I had to do to fix my X freezing on the i815 Intel .

sudo gedit /etc/X11/xorg.conf

this is what i added to the Device section

Option "DRI" "off"

and save

Ever since i've had no problems at all.

---

### Post by super kim on 2009-08-03
no no, i do not suffer from my X freezing since the dri is set to default as standard for all i865 graphics cards. i want to enable the dri, hopefully i can reverse engineer your method of switching your dri off and turn mine on. and even more hopefully my X wont freeze, and even more hopefully i can watch videos again yay :)


would this work?

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
    Option        "DRI"            "on"
EndSection


or should it be...
    Option        "DRI"            "true"

---

### Post by super kim on 2009-08-03
i've changed my xorg.conf to:

Section "Device"
    Identifier    "Configured Video Device"
    Option        "AccelMethod"            "uxa"
    Option        "EXAOptimizeMigration"        "true"
    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "true"
EndSection


and done this:

**Use preview of 2.8 driver**

 If you're using Ubuntu 9.04, add the following line to synaptic software source or in /etc/apt/sources.list 
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty mainAdd PPA's key to your system: 
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 165d673674a995b3e64bf0cf4f191a5a8844c542Then update the system and reboot: 
sudo apt-get update
sudo apt-get upgradeall

i have to do now is reboot, and pray lol (why is there no smiley for 'fingers crossed')

---

### Post by super kim on 2009-08-03
nope if your reading this, dont try my method at all. didnt work. i would try the methods suggested by hotshotdj, and i will, just as soon as i get my x to stop crashing!


OK now i'm back to how it was... i will go for that staggered approach that the thehotshotbj suggested but i'm pretty sure the problems are to do with the tiling option being true in my xorg.conf but i'm too tired now to try things out so i'll just follow the instructions without really understanding them fully so i can watch family guy once again.

---

### Post by mox386 on 2009-08-04
> **HotShotDJ said:**
> 

1) [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
2) [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) (starting with the safe method, and working your way up as needed)
3) Karmic Koala (very last resort, although if the first two steps don't work, I doubt Karmic will help).


I tried #1 and it didn't work.


I take that back after reviewing it I was able to get it to allow me to enable effects on the desktop!

---

### Post by mox386 on 2009-08-04
Tried number two, and it stopped my X from working correctly.... undid it and now I'm back. 



fyi I have the 82865G Integrated Graphics Controller, and I'm trying to make an always on eye candy/weather station.

---

### Post by super kim on 2009-08-05
yes both the first method did not work and the second froze my x. what can i say, the intel card is crap for a start but i cant be bothered spending any more time trying to get it to work. 
i got a new computer instead, thats number 4 now, but the last ones not broken so that shouldn't count. i just cant get the graphics card to work with ubuntu.

new computer but i kept my old hard drive so i don't know if its all set it's self up automatically but it plays movies so i judt dont care right now :D
hang on how do i get the sounds to work???

by the way i had been using the karmic off the live cd all day today and it works perfectly, better in fact. any way on to my sounds....

---

