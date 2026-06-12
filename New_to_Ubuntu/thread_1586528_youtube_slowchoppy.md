---
title: "youtube slow/choppy"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by Blenta on 2010-10-02
Hello to everyone, just recently I installed ubuntu 10.4 32bit and have been experiencing some problems watching you tube videos and videos posted on other sites. What happens is that it tends to chop in fullscreen especially when the navigation bar comes up. It gets worse when I play more than 2 clips at a time, please help its annoying! The wierdest thing that happend was this:  [http://yfrog.com/1467113436p](http://yfrog.com/1467113436p)
Thanks upfront

I use firefox 3.6.10

nvidia gforce9600GT 512MB(tried 173, 180 drivers), intel genuine dualcore2,66Ghz, 1,5GB DDR2 533mhz

---

### Post by dcsoldschool53 on 2010-10-02
> **Blenta said:**
> Hello to everyone, just recently I installed ubuntu 10.4 32bit and have been experiencing some problems watching you tube videos and videos posted on other sites. What happens is that it tends to chop in fullscreen especially when the navigation bar comes up. It gets worse when I play more than 2 clips at a time, please help its annoying! The wierdest thing that happend was this:  [http://yfrog.com/1467113436p](http://yfrog.com/1467113436p)
Thanks upfront

I use firefox 3.6.10

nvidia gforce9600GT 512MB(tried 173, 180 drivers), intel genuine dualcore2,66Ghz, 1,5GB DDR2 533mhz
Question did you install the latest version of adobe flash? Also, when playing you tube videos, click the pause button to let it load up fully first then, play it.

---

### Post by gandaran on 2010-10-02
> **Blenta said:**
> Hello to everyone, just recently I installed ubuntu 10.4 32bit and have been experiencing some problems watching you tube videos and videos posted on other sites. What happens is that it tends to chop in fullscreen especially when the navigation bar comes up. It gets worse when I play more than 2 clips at a time, please help its annoying! The wierdest thing that happend was this:  [http://yfrog.com/1467113436p](http://yfrog.com/1467113436p)
Thanks upfront

I use firefox 3.6.10

nvidia gforce9600GT 512MB(tried 173, 180 drivers), intel genuine dualcore2,66Ghz, 1,5GB DDR2 533mhz
hi,
it's not only you that have this problem, I have it in both my desktop and netbook and a lot of ubuntu users too!
and flash used to work very well before on this desktop, the issue only came up after installing ubuntu 10.04, I hope the next ubuntu 10.10 will be free from this.

---

### Post by Blenta on 2010-10-02
Yes, I have the latest flash and no, its not a connection problem...

---

### Post by Blenta on 2010-10-02
> **gandaran said:**
> hi,
it's not only you that have this problem, I have it in both my desktop and netbook and a lot of ubuntu users too!
and flash used to work very well before on this desktop, the issue only came up after installing ubuntu 10.04, I hope the next ubuntu 10.10 will be free from this.


Thanks for the reply... So, there is really nothing I can do about it? 
I downloaded some new drivers but, as I read somewhere it needs nvidia installer or something like that to apply...
And considering the fact that I installed ubuntu 2 days ago, should I even bother trying this?
Once again, Thank you!

---

### Post by jonick on 2010-10-02
Hi Guys,

Being brutally honest, Flash is totally underpants in Linux period.

It's not a Ubuntu thing, its just Flash is so resourse hungry, its been an issue forever, and all Linux distro's suffer from the problem to a greater or lesser extent.

---

### Post by lovinglinux on 2010-10-02
> **gandaran said:**
> hi,
it's not only you that have this problem, I have it in both my desktop and netbook and a lot of ubuntu users too!
and flash used to work very well before on this desktop, the issue only came up after installing ubuntu 10.04, I hope the next ubuntu 10.10 will be free from this.

> **Blenta said:**
> Thanks for the reply... So, there is really nothing I can do about it? 
I downloaded some new drivers but, as I read somewhere it needs nvidia installer or something like that to apply...
And considering the fact that I installed ubuntu 2 days ago, should I even bother trying this?
Once again, Thank you!

There are some things you can do.

First make sure you have the latest driver for you video card and try the third item on [this list]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html").

If YouTube is your main concern, then use my [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/161869/") extension.

Also please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by Lacrymology on 2010-10-03
I have the same issue, I ran the settings the firefox site recommended, to no avail. Also deactivated compiz, and that didn't work either, so I'm posting my datum here, I hope this doesn't bother anyone.

Thanks

**Shockwave Flash**

 File:  /var/lib/flashplugin-installer/npwrapper.libflashplayer.soVersion:   Shockwave Flash 10.1 r85
[B]Mozilla Firefox
[/B]

 Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.10) Gecko/20100915 Ubuntu/10.04 (lucid) Firefox/3.6.10

and I attach my firefox-report.txt

---

### Post by lovinglinux on 2010-10-03
> **Lacrymology said:**
> I have the same issue, I ran the settings the firefox site recommended, to no avail. Also deactivated compiz, and that didn't work either, so I'm posting my datum here, I hope this doesn't bother anyone.

Thanks

**Shockwave Flash**

 File:  /var/lib/flashplugin-installer/npwrapper.libflashplayer.soVersion:   Shockwave Flash 10.1 r85
[B]Mozilla Firefox
[/B]

 Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.10) Gecko/20100915 Ubuntu/10.04 (lucid) Firefox/3.6.10

and I attach my firefox-report.txt


Get version 1.0.14 of FLASH-AID and install the 64bit flash plugin when prompted.

[http://github.com/lovinglinux/flash-aid/downloads](http://github.com/lovinglinux/flash-aid/downloads)
[https://addons.mozilla.org/en-US/firefox/addon/161939/versions/](https://addons.mozilla.org/en-US/firefox/addon/161939/versions/)

---

### Post by Lacrymology on 2010-10-03
@lovinglinux thanks, but no, not good =/ with or without compiz running

---

### Post by lovinglinux on 2010-10-04
> **Lacrymology said:**
> @lovinglinux thanks, but no, not good =/ with or without compiz running

If you are using nvidia, then could try the latest driver from xswat ppa.

[http://ubuntuforums.org/showpost.php?p=9876094&postcount=6](http://ubuntuforums.org/showpost.php?p=9876094&postcount=6)

BTW, what is your computer specs?

---

### Post by Lacrymology on 2010-10-06
Athlon 64 3500+ 2.2GHz, 2GB 667MHz RAM, GeForce 9400GT

---

### Post by lovinglinux on 2010-10-06
> **Lacrymology said:**
> Athlon 64 3500+ 2.2GHz, 2GB 667MHz RAM, GeForce 9400GT

That is a single core CPU right? I guess that could be the problem. I use a Core2 Duo, but before that I had a P4 3.06 GHz single core and I had similar issues with flash. The P4 is particularly problematic due to high temps, so after playing flash videos for a while it would lag a lot. It was almost unwatchable.

Upgrading you nVidia driver might help tho.

---

### Post by sticky_icky on 2010-10-28
**I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  **I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  

      I wish to christ i could have found this years ago...  i have the  same  problem, main monitor is 1440x900, running an xfx geforce 7600gt,  and  everything but youtube works.  flash/youtube/ubuntu=HUGE #$^@##@   headaches for years.  i tried litterally hundreds of workarounds or   fixes, HOURS of time trying to get the stupid flash fixed for more than 2   minutes, and not one single thing worked, ever, until now.t

      ubuntu forums had been completely useless to me, in those  endeavors,  wasted much time for nothing, though, in fairness to the  buntu, i fully  acknowledge the fruitful efforts of the ubuntu team, the  linux world has  made HUGE strides forward since i started with  slackware7.   with  ubuntu, the reality is that aside from arbitrary  reference, i haven't  needed the forums, everything but flash, some  really obscure software,  works like a charm, since the nvidia driver  issues have been  sorted.(btw, for me, the only way to install properly  working nvidia  drivers/nvidia settings/flashplugin is with apt from  terminal after  stopping gnome...**not with synaptic from the desktop**)

     since nothing's ever worked for me, i didn't bother reading the  thread, i'd be shocked if it was mentioned... anyway, after a routine  cleaning/reinstallation of firefox i happened across this:[ http://www.addonfox.com/]("http://www.addonfox.com/"),   which icludes some really good addons for firefox....also some bs, the   converter, swifclick, and windowshopper addons pissed me off...

the real gem of that collection, which i had never found before is:

**[flashvideoreplacer 1.0.5]("https://addons.mozilla.org/en-US/firefox/addon/161869/")**

      it "replaces embedded flash videos with quicktime or windows media   player compatible videos."   WHAT THAT MEANS IS IT COMPLETELY REPLACES   THE WHOLE, STUPID, YOUTUBE/GOOGLEVIDEO GUI AND **EMBEDS IN ITS PLACE MPLAYER**.
(in the preferences,the selection for plugin/mimeType, is "windows media player (application/x-mplayer2)

hall-o-fu#%ing-luja!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

     _**this is the only thing that has ever worked for me**_,   and it seems to be a really solid addon, so far as i can tell, not   buggy, video looks great-not choppy, options exist to automatically   choose the quality of youtube videos, choose cache size(default is   2megs), enable post processing, all the gnome mplayer interface   settings, etc.  _it doesn't seem to change anything on any video sites except youtube/googlevideos, and optionally vimeo and blip.tv etc._  only problem is i haven't been able to get the youtube playlist to autoplay the next vid.

if  you are frustrated wit yt/google, try this.  i can confir, it works   with gnome mplayer on 10.04.1 LTS.  i have every video and audio   application i could find, though, not sure of the impact other packages   have on mplayer/vice-versa.
[B]
hope this works for you, NO need to thank me if it does, but--

         PLEASE[/B] **PLEASE PLEASE help others when you have solutions.**

god bless.

---

### Post by lovinglinux on 2010-10-29
> **sticky_icky said:**
> **I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  **I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  

      I wish to christ i could have found this years ago...  i have the  same  problem, main monitor is 1440x900, running an xfx geforce 7600gt,  and  everything but youtube works.  flash/youtube/ubuntu=HUGE #$^@##@   headaches for years.  i tried litterally hundreds of workarounds or   fixes, HOURS of time trying to get the stupid flash fixed for more than 2   minutes, and not one single thing worked, ever, until now.t

      ubuntu forums had been completely useless to me, in those  endeavors,  wasted much time for nothing, though, in fairness to the  buntu, i fully  acknowledge the fruitful efforts of the ubuntu team, the  linux world has  made HUGE strides forward since i started with  slackware7.   with  ubuntu, the reality is that aside from arbitrary  reference, i haven't  needed the forums, everything but flash, some  really obscure software,  works like a charm, since the nvidia driver  issues have been  sorted.(btw, for me, the only way to install properly  working nvidia  drivers/nvidia settings/flashplugin is with apt from  terminal after  stopping gnome...**not with synaptic from the desktop**)

     since nothing's ever worked for me, i didn't bother reading the  thread, i'd be shocked if it was mentioned... anyway, after a routine  cleaning/reinstallation of firefox i happened across this:[ http://www.addonfox.com/]("http://www.addonfox.com/"),   which icludes some really good addons for firefox....also some bs, the   converter, swifclick, and windowshopper addons pissed me off...

the real gem of that collection, which i had never found before is:

**[flashvideoreplacer 1.0.5]("https://addons.mozilla.org/en-US/firefox/addon/161869/")**

      it "replaces embedded flash videos with quicktime or windows media   player compatible videos."   WHAT THAT MEANS IS IT COMPLETELY REPLACES   THE WHOLE, STUPID, YOUTUBE/GOOGLEVIDEO GUI AND **EMBEDS IN ITS PLACE MPLAYER**.
(in the preferences,the selection for plugin/mimeType, is "windows media player (application/x-mplayer2)

hall-o-fu#%ing-luja!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

     _**this is the only thing that has ever worked for me**_,   and it seems to be a really solid addon, so far as i can tell, not   buggy, video looks great-not choppy, options exist to automatically   choose the quality of youtube videos, choose cache size(default is   2megs), enable post processing, all the gnome mplayer interface   settings, etc.  _it doesn't seem to change anything on any video sites except youtube/googlevideos, and optionally vimeo and blip.tv etc._  only problem is i haven't been able to get the youtube playlist to autoplay the next vid.

if  you are frustrated wit yt/google, try this.  i can confir, it works   with gnome mplayer on 10.04.1 LTS.  i have every video and audio   application i could find, though, not sure of the impact other packages   have on mplayer/vice-versa.
[B]
hope this works for you, NO need to thank me if it does, but--

         PLEASE[/B] **PLEASE PLEASE help others when you have solutions.**

god bless.

Thanks for the comments about FlashVideoReplacer.

---

### Post by andus on 2013-01-27
Update on this issue.  I had the same problem, and tried to download flashvideoreplacer, but it was no longer available.  Instead, I installed the Flash-Aid add-on for Firefox and now my problem is solved.

Flash-Aid uninstalled gnash and adobe-flashplugin because they were conflicting.  Youtube runs fine now.

Edit: I'm running 12.04 (precise) and have Ubuntu Studio installed on top of the regular desktop distro.  Flash-Aid installed the beta adobe-flashplugin after removing the stable version, it seems the stable version had the problem.  I re-installed gnash, and everything is still fine.

---

### Post by oldos2er on 2013-01-28
Old thread closed.

---

