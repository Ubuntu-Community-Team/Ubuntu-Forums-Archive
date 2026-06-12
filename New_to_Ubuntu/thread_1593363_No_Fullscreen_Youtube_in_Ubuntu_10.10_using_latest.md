---
title: "No Fullscreen Youtube in Ubuntu 10.10 using latest Google Chrome Stable"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by Dyegov on 2010-10-11
Well as the title says, I have pretty smooth playback on youtube videos, no problems with flash whatsoever, but when I try to go full screen the sound goes on but the image is frozen. If I go back to normal image moves again. How could I solve this?

I'm using Ubuntu 10.10 Final release 32 bits.

---

### Post by cariboo on 2010-10-11
Which graphics driver are you using?

---

### Post by Dyegov on 2010-10-11
I didn't install any, ubuntu just worked out of the box and never offered me proprietary drivers. It's an integrated graphics card on my Laptop (Dell Inspiron 1545)

---

### Post by Dyegov on 2010-10-11
Can someone help me please?

---

### Post by Ckytep on 2010-10-11
I've got the same problem here. Using the graphic driver that Ubuntu installed automatically. Video adapter is Intel GMA950 in my HP nx7300 laptop.
It worked like a charm in 10.04 :-/

---

### Post by jiykauu on 2010-10-12
> **Dyegov said:**
>  try to go full screen the sound goes on but the image is frozen. If I go back to normal image moves again. How could I solve this?

I'm using Ubuntu 10.10 Final release 32 bits.


Same problem, didn't have it on 10.04, on Asus laptop, with Intel graphic.

---

### Post by renkinjutsu on 2010-10-12
It might be this issue here.. 
[http://code.google.com/p/chromium/issues/detail?id=55954]("http://code.google.com/p/chromium/issues/detail?id=55954")
They have a fix, but it hasn't been merged yet.

---

### Post by Dyegov on 2010-10-12
I don't know if I read right but that doesn't seem to have anything to do with my problem :s

---

### Post by khopek on 2010-10-12
I can confirm this problem. Once I upgraded to the new release of Ubuntu, flash no longer works in Fullscreen. The only trick I have found to some sites is to PAUSE the video, then fullscreen it, then unpause the video.

Very annoying though. Also, annoying that the ESC keep does not work to exit out of fullscreen anylonger. One has to use the mouse to click the screen first, then Esc will work.

---

### Post by Dyegov on 2010-10-12
> **khopek said:**
> I can confirm this problem. Once I upgraded to the new release of Ubuntu, flash no longer works in Fullscreen. The only trick I have found to some sites is to PAUSE the video, then fullscreen it, then unpause the video.

Very annoying though. Also, annoying that the ESC keep does not work to exit out of fullscreen anylonger. One has to use the mouse to click the screen first, then Esc will work.
We don't seem to have the same problem, since mine doesn't work full screen even if I pause it before going full screen, and my ESC key always works to exit the full screen (which doesn't work properly).

---

### Post by rs31337 on 2010-10-12
I think we have the same problem. I'm running Ubuntu 10.10 on a Dell Inspiron e1405 aka m640.

My Graphics Card:

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

It has to be something with chrome (I'm using the version straight from google's website)... because it works fine with Firefox.

---

### Post by SpockVulcan on 2010-10-12
I have the same issue I have found that going in and out of full screen a few times will solve it

---

### Post by seismicmike on 2010-10-12
```

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```

I have the same problem as OP, but in both Chrome AND Firefox. Found it interesting that this doesn't seem to be a problem with the flash player itself. Check out these results from around the internets. Does the following play in Fullscreen for me?

```

Site            Firefox       Chrome
Youtube         No            No
Daily Motion    No            Yes
Vimeo           No            No
ESPN            Yes           Yes
NFL.com         Yes           Yes
MLB.com         Yes           No
Hulu            Yes           Yes

```


I did also notice that sometimes I could not get it to work in fullscreen at all, while at other times, going back and forth a couple times will eventually get it to work. the No's on here are ones where I couldn't get it to work at all.

I'd be very interested in finding out what the cause of this is and if there's a fix. I have a hard time believing it's flash because some sites work while others don't. I also have a hard time believing it's my browser since it's both FF and Chrome. I also have a hard time believing that it's my drivers, b/c it was working fine until I upgraded from 10.04 to 10.10 using APT the other day.

Thanks.

---

### Post by Dileepa Rajapaksha on 2010-10-12
same problem .... some time works but some times not...both in fir fox and chrome...

---

### Post by seismicmike on 2010-10-12
Here's a thought. While I did my research and typed out my explanation of my problem, I had a youtube video buffering in firefox. After I finished typing this out, I went back to that video and the buffer was full. I thought, just for the heck of it I'd try it fullscreen, *and it worked*! Perhaps it's an issue with trying to switch before the buffer fills up. So try letting the buffer fill before going to full screen and see if that fixes the problem.

---

### Post by Netnai on 2010-10-13
> **seismicmike said:**
> ...So try letting the buffer fill before going to full screen and see if that fixes the problem.

I have the same problem with Chromium and Firefox.
Fill the buffer doesn't solve the issue.
And i have also a Dell, Latitude D510.

Any clue?

---

### Post by jiykauu on 2010-10-13
Does any one ask Ubuntu debugers or staff or whatever about it?

---

### Post by 3dgard on 2010-10-14
Hey guys! I had the same problem, and I found the solution!

```
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
```

The solution was posted on the following website:

[http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10](http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10)

---

### Post by Dileepa Rajapaksha on 2010-10-14
> **3dgard said:**
> Hey guys! I had the same problem, and I found the solution!

```
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
```The solution was posted on the following website:

[http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10](http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10)

Thanks man.... Itz work...:P

---

### Post by fordp on 2010-10-14
> **3dgard said:**
> Hey guys! I had the same problem, and I found the solution!

```
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
```The solution was posted on the following website:

[http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10](http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10)

Worked for me too. Thanks.

---

### Post by 3dgard on 2010-10-14
No problem!! Glad it worked! :popcorn:

---

### Post by Netnai on 2010-10-14
Here works too. 3dgard, you rules! :D

---

### Post by zeating on 2010-10-14
When you click fullscreen do you see a black box? if so try to minimize

---

### Post by clay005 on 2010-10-15
Hello guys.

I do have this kind of problem but a little different. When i go to full screen everything seems fine, but later my pc hangs-up completely.

please help me..

---

### Post by enantiomer2000 on 2010-10-16
I can confirm the exact same issue.  No proprietary driver have an asus p5q-em motheboard with integrated intel graphics chip.  I can watch HD video just fine but as soon as switch to fullscreen, the video freezes but the sound still plays.  No problem in 10.04 but when I upgraded to 10.10 it doesn't work.  I think I have actually seen it work a few times but the vast majority of time it doesn't work.  Have tested it on Firefox and Chromium.

---

### Post by enantiomer2000 on 2010-10-16
Ok I can confirm that this fixed it but does that mean after doing that fix, there is no hardware acceleration anymore?  I can still play 1080p video, so I suppose its ok...

---

### Post by hamidoo on 2010-10-16
> **3dgard said:**
> Hey guys! I had the same problem, and I found the solution!

```
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
```

The solution was posted on the following website:

[http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10](http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10)

Works perfectly!
thx bro 
cheers

---

### Post by chilloutmo on 2010-10-21
I have exact the same issue but the solutions did not work for me. it still hangs up on full screen. can anyone please help ?
here are some details: 
the mkdir solution doesn't work, it says something like etc/adobe/ "file exists"
I tried to look at the mms.cfg through gedit and the file was empty, there was only overridegpuvalidation, I changed that manually from true to one, but still nothing. I tried so many things but the problem remains. in every browser.

---

### Post by kernelles on 2010-10-22
> **3dgard said:**
> Hey guys! I had the same problem, and I found the solution!

```
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
```The solution was posted on the following website:

[http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10](http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10)
  
This worked for me! Thanks

---

### Post by iferbas on 2010-10-23
i solve it!!!

just right cick on the video (configure flash) go to setting and then click on local storage and drag it to ilimit and that's it! full screen works perfectly... please post this on any ubuntu forums to help with this problem

---

### Post by luckstrikes on 2010-10-24
phew! works for me too! thanks for the lifesaving solution!

---

### Post by sticky_icky on 2010-10-28
**Re: Youtube fullscreen bug with dual monitors** 			
 			 			 		   		 		 		**I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  **I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  

      I wish to christ i could have found this years ago...  i have the  same  problem, main monitor is 1440x900, running an xfx geforce 7600gt,  and  everything but youtube works.  flash/youtube/ubuntu=HUGE #$^@##@   headaches for years.  i tried litterally hundreds of workarounds or   fixes, HOURS of time trying to get the stupid flash fixed for more than 2   minutes, and not one single thing worked, ever, until now.t

      ubuntu forums had been completely useless to me, in those  endeavors,  wasted much time for nothing, though, in fairness to the  buntu, i fully  acknowledge the fruitful efforts of the ubuntu team, the  linux world has  made HUGE strides forward since i started with  slackware7.   with  ubuntu, the reality is that aside from arbitrary  reference, i haven't  needed the forums, everything but flash, some  really obscure software,  works like a charm, since the nvidia driver  issues have been  sorted.(btw, for me, the only way to install properly  working nvidia  drivers/nvidia settings/flashplugin is with apt from  terminal after  stopping gnome...**not with synaptic from the desktop**)

     since nothing's ever worked for me, i didn't bother reading the  thread, i'd be shocked if it was mentioned... anyway, after a routine  cleaning/reinstallation of firefox i happened across this:[ http://www.addonfox.com/]("http://www.addonfox.com/"),   which icludes some really good addons for firefox....also some bs, the   converter, swifclick, and windowshopper addons pissed me off...

the real gem of that collection, which i had never found before is:

**[flashvideoreplacer 1.0.5]("https://addons.mozilla.org/en-US/firefox/addon/161869/")**

      it "replaces embedded flash videos with quicktime or windows media   player compatible videos."   WHAT THAT MEANS IS IT COMPLETELY REPLACES   THE WHOLE, STUPID, YOUTUBE/GOOGLEVIDEO GUI AND **EMBEDS IN ITS PLACE MPLAYER**.
(in the preferences,the selection for plugin/mimeType, is "windows media player (application/x-mplayer2)

hall-o-fu#%ing-luja!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

     _**this is the only thing that has ever worked for me**_,   and it seems to be a really solid addon, so far as i can tell, not   buggy, video looks great-not choppy, options exist to automatically   choose the quality of youtube videos, choose cache size(default is   2megs), enable post processing, all the gnome mplayer interface   settings, etc.  _it doesn't seem to change anything on any video sites except youtube/googlevideos, and optionally vimeo and blip.tv etc._  only problem is i haven't been able to get the youtube playlist to autoplay the next vid.

if  you are frustrated wit yt/google, try this.  i can confir, it works   with gnome mplayer on 10.04.1 LTS.  i have every video and audio   application i could find, though, not sure of the impact other packages   have on mplayer/vice-versa.
[B]
hope this works for you, NO need to thank me if it does, but--

         PLEASE[/B] **PLEASE PLEASE help others when you have solutions.**

god bless.



      I wish to christ i could have found this years ago...  i have the  same  problem, main monitor is 1440x900, running an xfx geforce 7600gt,  and  everything but youtube works.  flash/youtube/ubuntu=HUGE #$^@##@   headaches for years.  i tried litterally hundreds of workarounds or   fixes, HOURS of time trying to get the stupid flash fixed for more than 2   minutes, and not one single thing worked, ever, until now.t

      ubuntu forums had been completely useless to me, in those  endeavors,  wasted much time for nothing, though, in fairness to the  buntu, i fully  acknowledge the fruitful efforts of the ubuntu team, the  linux world has  made HUGE strides forward since i started with  slackware7.   with  ubuntu, the reality is that aside from arbitrary  reference, i haven't  needed the forums, everything but flash, some  really obscure software,  works like a charm, since the nvidia driver  issues have been  sorted.(btw, for me, the only way to install properly  working nvidia  drivers/nvidia settings/flashplugin is with apt from  terminal after  stopping gnome...**not with synaptic from the desktop**)

anyway, after a routine cleaning/reinstallation of firefox i happened across this:[ http://www.addonfox.com/]("http://www.addonfox.com/"),   which icludes some really good addons for firefox....also some bs, the   converter, swifclick, and windowshopper addons pissed me off...

the real gem of that collection, which i had never found before is:

**[flashvideoreplacer 1.0.5]("https://addons.mozilla.org/en-US/firefox/addon/161869/")**

      it "replaces embedded flash videos with quicktime or windows media   player compatible videos."   WHAT THAT MEANS IS IT COMPLETELY REPLACES   THE WHOLE, STUPID, YOUTUBE/GOOGLEVIDEO GUI AND **EMBEDS IN ITS PLACE MPLAYER**.
(in the preferences,the selection for plugin/mimeType, is "windows media player (application/x-mplayer2)

hall-o-fu#%ing-luja!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

     _**this is the only thing that has ever worked for me**_,   and it seems to be a really solid addon, so far as i can tell, not   buggy, video looks great-not choppy, options exist to automatically   choose the quality of youtube videos, choose cache size(default is   2megs), enable post processing, all the gnome mplayer interface   settings, etc.  _it doesn't seem to change anything on any video sites except youtube/googlevideos, and optionally vimeo and blip.tv etc._  only problem is i haven't been able to get the youtube playlist to autoplay the next vid.

if  you are frustrated wit yt/google, try this.  i can confir, it works   with gnome mplayer on 10.04.1 LTS.  i have every video and audio   application i could find, though, not sure of the impact other packages   have on mplayer/vice-versa.
[B]
hope this works for you, NO need to thank me if it does, but--

         PLEASE[/B] **PLEASE PLEASE help others when you have solutions.**

god bless.**I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  

      I wish to christ i could have found this years ago...  i have the  same  problem, main monitor is 1440x900, running an xfx geforce 7600gt,  and  everything but youtube works.  flash/youtube/ubuntu=HUGE #$^@##@   headaches for years.  i tried litterally hundreds of workarounds or   fixes, HOURS of time trying to get the stupid flash fixed for more than 2   minutes, and not one single thing worked, ever, until now.t

      ubuntu forums had been completely useless to me, in those  endeavors,  wasted much time for nothing, though, in fairness to the  buntu, i fully  acknowledge the fruitful efforts of the ubuntu team, the  linux world has  made HUGE strides forward since i started with  slackware7.   with  ubuntu, the reality is that aside from arbitrary  reference, i haven't  needed the forums, everything but flash, some  really obscure software,  works like a charm, since the nvidia driver  issues have been  sorted.(btw, for me, the only way to install properly  working nvidia  drivers/nvidia settings/flashplugin is with apt from  terminal after  stopping gnome...**not with synaptic from the desktop**)

anyway, after a routine cleaning/reinstallation of firefox i happened across this:[ http://www.addonfox.com/]("http://www.addonfox.com/"),   which icludes some really good addons for firefox....also some bs, the   converter, swifclick, and windowshopper addons pissed me off...

the real gem of that collection, which i had never found before is:

**[flashvideoreplacer 1.0.5]("https://addons.mozilla.org/en-US/firefox/addon/161869/")**

      it "replaces embedded flash videos with quicktime or windows media   player compatible videos."   WHAT THAT MEANS IS IT COMPLETELY REPLACES   THE WHOLE, STUPID, YOUTUBE/GOOGLEVIDEO GUI AND **EMBEDS IN ITS PLACE MPLAYER**.
(in the preferences,the selection for plugin/mimeType, is "windows media player (application/x-mplayer2)

hall-o-fu#%ing-luja!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
i realise that your problem is with chrome, but this is THE solution for the same problem in firefox, and i'm trying to get this info out there...
     [U][B]
this is the only thing that has ever worked for me[/B][/U],   and it seems to be a really solid addon, so far as i can tell, not   buggy, video looks great-not choppy, options exist to automatically   choose the quality of youtube videos, choose cache size(default is   2megs), enable post processing, all the gnome mplayer interface   settings, etc.  _it doesn't seem to change anything on any video sites except youtube/googlevideos, and optionally vimeo and blip.tv etc._  only problem is i haven't been able to get the youtube playlist to autoplay the next vid.

if  you are frustrated wit yt/google, try this.  i can confir, it works   with gnome mplayer on 10.04.1 LTS.  i have every video and audio   application i could find, though, not sure of the impact other packages   have on mplayer/vice-versa.
[B]
hope this works for you, NO need to thank me if it does, but--

         PLEASE[/B] **PLEASE PLEASE help others when you have solutions.**

god bless.

---

### Post by JosephC on 2010-11-04
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg


Beautiful fix, 3dgard. Thank you for posting it. I've been plagued by this problem for 2 years.


> **iferbas said:**
> i solve it!!!

just right cick on the video (configure flash) go to setting and then click on local storage and drag it to ilimit and that's it! full screen works perfectly... please post this on any ubuntu forums to help with this problem

I already used the above fix. If this also works, I wonder what the overarching explanation is.

---

### Post by OlaugeB on 2010-11-12
thank you! 10.10 here.

sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg

works well

---

### Post by Dark7man on 2010-11-17
Thanks dude! Worked a treat! :)  Much appreciated!

---

### Post by Money Man on 2010-11-19
> **3dgard said:**
> Hey guys! I had the same problem, and I found the solution!

```
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
```

The solution was posted on the following website:

[http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10](http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10)

This was the fix for me too. thanks

---

### Post by myolbug on 2010-11-21
I am running Mint 10 64bit and this halfway solved my problem. In Firefox: When I go to Youtbube, the video isn't there, the controls don' show etc.  If I click the lower right side of the screen, where the full screen button would be if I could see it, I can get it to go full screen, then I see it.  It will not play in lower size.  
However, using Opera, all flash works right the first time.

---

### Post by myolbug on 2010-11-24
Does anyone have any idea on this?  ON Mint 9 it's fine, but Mint 10 I can't get Youtube to work normally.

---

### Post by Crash~Override on 2010-11-26
> **3dgard said:**
> Hey guys! I had the same problem, and I found the solution!

```
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
```

The solution was posted on the following website:

[http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10](http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10)

Perfect! Excellent solution :)

---

### Post by realloc on 2010-11-27
This worked for me:

[PHP]#Install "CompizConfig Settings Manager"
sudo bash  # root shell
apt-get install compizconfig-settings-manager

# While you're in the shell, I recommend...

# Install extra plugins. The 'burn' effect is awesome and should be the
# default window close animation.
apt-get install compiz-fusion-plugins-extra
[/PHP]

Then go to **System > Preferences > CompizConfig Settings Manager**

...and activate the plugin "**Video Playback**".

This worked with my integrated Intel Video chip in an HP Pavilion DV4000.  My symptom was that Youtube video would freeze up when switched to fullscreen, but Hulu.com worked fullscreen.

This plugin must flip some OpenGL setting, because after activating this Hulu.com went from being choppy with low fps to smooth and T.V.-like (and YouTube went from freezing to working smoothly).

---

### Post by mrnatas20 on 2010-12-27
> **3dgard said:**
> Hey guys! I had the same problem, and I found the solution!

```
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
```

The solution was posted on the following website:

[http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10](http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10)

This worked for me. Also, I had to right click a flash movie, go into settings, and re-check "enable hardware acceleration." (I had unchecked it previously in attempting another 'fix' that didn't work)

Thank you!

---

### Post by alexcckll on 2010-12-30
I'm not sure about doing any of this.

All I know is that I cannot at present watch paid Seesaw.com content (mostly from the BBC) fullscreen at the moment - when I was able ot with Channel 4 content about 6 months ago.  Since then, all I'm running with is Lucid with all updates.

Laptop - Thinkpad R61i 7659-ABG.
Graphics - Intel X3100 
Symptoms - if I attempt full screen, I can hear audio, but locks the display up entirely.  I had to switch to a text console and reboot from there.

Please fix.

I have raised bug 695644 - [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/695644](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/695644)

I have not tested on my netbook, and the last iPlayer content I played - I played in a window rather than fullscreen.

---

### Post by JoeloRoss on 2011-01-31
> **3dgard said:**
> Hey guys! I had the same problem, and I found the solution!

```
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
```The solution was posted on the following website:

[http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10](http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10)

It works for me in Chrome also works in Firefox whit Cooliris. ;)

---

### Post by lodp on 2011-02-03
Editing /etc/adobe/mms.cfg didn't work for me. But I found a **much simpler solution:** I just right-clicked the video (non-fullscreen) went to "Settings" and unchecked "Enable Hardware Acceleration". Now fullscreen works on all sites, in both Firefox and Chrome.

I'm on Kubuntu 10.10 - 64bit, Adobe Flash 10.1.102.65ubuntu0.10.10.1, and I've got an ATI Mobility Radeon HD 3600 GPU, running on proprietary drivers (fglrx).

---

### Post by bboyandru on 2011-02-13
Hi,
I have Intel GMA 4500 video card and these commands, in terminal, helped me
sudo mkdir /etc/adobe 
echo "OverrideGPUValidation=true" >~/mms.cfg 
sudo mv ~/mms.cfg /etc/adobe/

restart firefox

from [http://www.techdrivein.com/2010/11/fix-youtube-video-freeze-while-in-full.html](http://www.techdrivein.com/2010/11/fix-youtube-video-freeze-while-in-full.html)

---

### Post by hansmex on 2011-02-16
Iferbas,

Thank you, setting memory to max storage was the solution!!
THANKS YOU

hansmex

---

### Post by cumanacr on 2011-02-26
> **3dgard said:**
> Hey guys! I had the same problem, and I found the solution!

```
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
```The solution was posted on the following website:

[http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10](http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10)

Thanks, it worked for me too!!!

---

### Post by dannystaple on 2011-03-06
> **cumanacr said:**
> Thanks, it worked for me too!!!

This kind of worked for me - no more display lock ups, but a few videos in, the Adobe Flash Plugin itself crashed. Saying that - I've been seeing this a lot on other platforms I use (OSX, Winblows) running Flash lately. Time to look up flash plugin crash fixes...

---

### Post by burcs on 2011-03-09
Having similar issues. Full screen works, it's just very choppy. Tried the fix posted here (mms.cfg) and it gave the red overlay bug on Youtube. Deleting that folder I created fixed it.

Also, my "settings" is grayed out in Flash.

[IMG]http://i.imgur.com/RsPgR.png[/IMG]
________________

Have tried upping the storage settings in the Global settings but didn't help. Nor did enabling "Video playback" in Compiz. Reinstalling Flash through Synaptic neither. Problem in both Chromium and Firefox.

Pretty sure it's the hardware acceleration, but since I can't get to the settings not sure what to try. Card is an x1950. Any ideas?

---

### Post by chreko on 2011-03-13
> **3dgard said:**
> Hey guys! I had the same problem, and I found the solution!

```
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
```

The solution was posted on the following website:

[http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10](http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10)

This did work for me as well. But I wonder why? Since all users had an Intel GPU it seems that there is still a bug in the Intel-xorg driver, which needs to be handled.

And I almost forgot to say thanks to 3dgard!

---

### Post by opiumpoetry on 2011-03-13
here's what worked 4 me [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?p=10513659#post10513659[/COLOR]]("http://ubuntuforums.org/showthread.php?p=10513659#post10513659") i uninstalled Adobe Flash first

---

### Post by masajimckee on 2011-03-19
I've been trying to do this for awhile but when i try it it says ```
cannot create director '/etc/adobe': File exists
```

can anyone help??? i'm dying here!

---

### Post by racie on 2011-03-20
> **masajimckee said:**
> I've been trying to do this for awhile but when i try it it says ```
cannot create director '/etc/adobe': File exists
```

can anyone help??? i'm dying here!

Perhaps try uninstalling then reinstalling flash.

One user posted that it was fixed after dragging up the storage meter.  That didn't work for me, so I used the command line like someone suggested.  Terrific find!  I was worried that my integrated graphics card was just THAT bad.  :P

Here it is again if y'all have missed it and don't feel like going back a page. ;)

```
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
```

---

### Post by verdomde on 2011-05-11
> **masajimckee said:**
> I've been trying to do this for awhile but when i try it it says ```
cannot create director '/etc/adobe': File exists
```

can anyone help??? i'm dying here!

I'm sure it's a bit late now- but this just means that folder already exists. start from the second line in the code and all will be well- although these lines didn't improve anything for me. (natty)

---

### Post by Erik500002 on 2011-07-02
Wow man, fixed my issue on maverick was getting pretty annoying couldn't fullscreen any video. Now works like a charm thanks!

---

