---
title: "Video Resolution....the Achilles Heel of Linux ???"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-03-07
Well it's been 2 or 3 weeks now that I have tried to resolve my video res problem. Several people have given suggestions but no actual fix action has come out of it. I have wandered around the web looking at Linux sites and it seems that video interfacing and resolution in particular seems to be a reoccurring problem with Linux distros.

Now I am new to Linux and thus far have been impressed with it's capabilities BUT it has been a sobering realization that some things are not going to be easy in Linux. I hooked my Kodak camera up to the USB port and Ubuntu jumped all over it. After several minutes downloading all the jpegs are on the hard drive now. But when it comes to something like resetting one's screen resolution from 800 x 600 to 1440 x 900 it is a lesson in frustration and futility.

IF Linux plans on seriously garnering a bigger piece of the worldwide homeuser OS pie then things like changing video res have got to be as easy as changing your desktop theme. People just aren't going to screw around for weeks trying to do something.

I give up. I'll stay at 800 by 600 on Linux and boot up under Microsoft when I want to see 1440 by 900.

It's disappointing because I had high hopes for Linux.

---

### Post by 4Orbs on 2009-03-07
Are you unable to install the correct driver for your graphics card? If you've been working on this for two weeks, I presume you know which card you have and which driver is required to work with your card. Which version of Ubuntu are you using?

Is this on a wubi install, in a virtual machine or a physical installation on a real partition?

---

### Post by ozark_hillbilly on 2009-03-07
if your wanting to get your feet wet on this problem, here you go:

[http://ubuntuforums.org/showthread.php?t=1083325](http://ubuntuforums.org/showthread.php?t=1083325)

P.S.  NO VIDEO CARD; onboard nvidia 7050 630i chipset

Ed

---

### Post by lykwydchykyn on 2009-03-07
If I may suggest another point of view...

Your graphics chip is made by Nvidia.  

Nvidia makes a proprietary driver for Linux.  This means that Nvidia has chosen to be solely responsible for the way their hardware functions with Linux.

Should you be disappointed in Linux, or in Nvidia?

Think about it:
```

IF Linux plans on seriously garnering a bigger piece of the worldwide homeuser OS pie then things like changing video res have got to be as easy as changing your desktop theme. People just aren't going to screw around for weeks trying to do something.

```
I could go on for pages about what the Linux development community is doing to address the hardware compatibility issues still out there, not the least of which is the [Linux driver project](http://www.linuxdriverproject.org/twiki/bin/view), but that isn't the point.

The point isn't what Linux wants.  The point is what you want:  do you want to run this OS? 

If you do, then as far as I can tell from reading your other thread and doing some searching, your chipset is not very Linux-friendly.  You can either wait for Nvidia to make it so, or drop a bit of cash on a seperate video card that does work with Linux.

---

### Post by stalkier on 2009-03-07
I have a XFX 8500GT video card that runs very nicely on Linux. You can get one for like $50 or so right now. It is a 512MB card (PCIe). Check TigerDirect.

---

### Post by LowSky on 2009-03-07
I know this might sound odd but try the 9.04 aplha... I know its normally a no no for me to even suggest to someone, but its worth trying. You shouldn't even have an issue as nvidia usually work awesomely

It has the newest Nvidia driver availible and works decently (It can break so be careful)

---

### Post by 4Orbs on 2009-03-07
OK, I took a look at that thread you linked. On your last post you posted the current xorg.conf.nvidia file. Now I want to know, is that file identical to your /etc/X11/xorg.conf file? Also, when you open the nvidia settings manager, do you have any options at all to change screen resolution?

---

### Post by ozark_hillbilly on 2009-03-07
4Orbs,

The nvidia conf file becomes the xorg.conf when I cp in terminal. When the screen locks up I have to revert in recovery mode back to the xorg.conf.bak file.

Interesting enuf is that when I go to the menu screen on the monitor before signing on  and check the resolution it says 1440 x 900. As soon as I sign on the monitor locks to a black screen with the out of range error message.

Also I cannot activate the nvidia drivers under Hardware Drivers with the nvidia xorg file installed. It says the xorg file is invalid.

Going to Screen and Graphics preferences is a "ring around the rosy." Nothing locks in when you change settings. It reverts back to Plug n Play 800 x 600. You can select LCD 1440 by 900  Generic or LG (my namebrand) and do a detect. But then it wants a driver file location. I have the LG driver on the desktop. But it's for a DOS environment I believe. Configuration test alwways fails as well. Even with the Plug n play 800 x 600 setting. 
Things are not linked up right somewhere.

---

### Post by ozark_hillbilly on 2009-03-07
I see the point your making. Unfortunately no one bothered to tell me that when you build your latest/greatest computer MAKE SURE there is no graphics compatibility issues with the mobo and LINUX. If you don't know you can't ask.

Now it's being suggested to spend more money on the computer to get graphics working.
If the proprietary drivers work under Win XP (which they do on my other partition) why is there so much difficulty on the Linux side. Is this a plot by nVidia to support MS and not Linux?

---

### Post by mrbiggbrain on 2009-03-07
```

IF Linux plans on seriously garnering a bigger piece of the worldwide homeuser OS pie then things like changing video res have got to be as easy as changing your desktop theme. People just aren't going to screw around for weeks trying to do something.
```

Im not trying to jump all over you, not at all, but rather exsplaine something which i have come to know as wholely true. 99.99% of linux users could care less about a bigger piece of the pie. why does linux appeal to me? linux is free open source fotware, and not in the sense that it costs nothing at all, but rather that most of its code is freely distributable, modifiable, and redistributable. 

I could care less if i wake up tomorrow and im the last ubuntu user on the planet, i love to hack apart my OS, write code, scripts, play with functions, and contrubute my best to the community.

id find that linux is improvable in any way, but to say its not easy to change resolutions is odd, iv done it quite a bit. many times people find linux hard becuse they wont give up windows ideals, they say when i do this, isnt this suppose to happen, instead of, ok that makes sence.

---

### Post by 4Orbs on 2009-03-07
In the other thread you mention having downloaded the 180 driver from nvidia's website. If you ran the install of that driver correctly, then you should stay away from the Hardware Drivers mgr because the mgr does not work with manually installed drivers. So you actually may have the 180 driver installed at this time.

Try adding to your xorg.conf file as root the "modes" line, so that the Display subsection of the Screen section looks like below. Save and reboot.

```
SubSection "Display"
Depth 24
Modes "1440x900" "1280x1024" "1024x768" "800x600"
EndSubSection
```

The reason I believe you may have the 180 driver installed correctly is because in one post you state that you booted into a higer resolution, then the screen went black after logging in. If, after doing the above, you can boot into a higher resolution... don't try to activate the driver from the Hardware Drivers mgr. If you can successfully boot, you can re-edit the xorg.conf and remove or change the resolutions (but I would leave the 1440x900 as-is).

---

### Post by lykwydchykyn on 2009-03-07
> **ozark_hillbilly said:**
> I see the point your making. Unfortunately no one bothered to tell me that when you build your latest/greatest computer MAKE SURE there is no graphics compatibility issues with the mobo and LINUX. If you don't know you can't ask.
I'm not sure what you're saying here.  You can't swing a dead cat in this forum without hitting someone with a hardware compatibility issue.  Did you build the computer intending to run Linux?
> 
Now it's being suggested to spend more money on the computer to get graphics working.

It's kind of weird being referred to in the passive voice.  I know my nick is hard to spell, but...  

I'm just telling you reality.  Anyone who has run Linux long enough (I'm on six years now) has run into a piece of hardware that just doesn't work.  If you want to run Linux, you buy another piece of hardware that does.  The situation is way better than it was 5 years ago, but it's not 100%.  
> 
If the proprietary drivers work under Win XP (which they do on my other partition) why is there so much difficulty on the Linux side. Is this a plot by nVidia to support MS and not Linux?

Probably less malice and more apathy.  Some might point out that Ubuntu doesn't have the latest drivers in the repos, but I'd point out that Windows doesn't have repos or Nvidia drivers included period.  They come on that disc that came with your motherboard.  Did the disc include Linux drivers?  I'm guessing no.  Thanks Nvidia.

Maybe 4Orbs can get you fixed.  Let's hope so, but frankly this probably won't be the last piece of hardware you end up with that doesn't work properly with Linux -- especially if you buy without checking out the compatibility situation first.  

Like I said, it's not about what Linux wants, it's about what you want.  What do you want?

---

### Post by Garrovick on 2009-03-08
I'm no expert, but I have an old computer with an old nividia 6200 PCI video card and a 1400x900 resolution monitor. I have no problems with it.  And when I loaded Ubuntu 8.10 as my sole OS, I received an update notice for the card's drivers

And, I was pleasantly surprised that my HP printer worked right. And there is a program for it too.

Just Talking Out Loud,

David

---

### Post by itlarson on 2009-03-08
This could be an excuse to upgrade to a new 1680x1050 monitor.  I've had good luck with this resolution and nvidia 6xxx.  Bigger is always better.  As for the old monitor- eBay.

---

### Post by ozark_hillbilly on 2009-03-08
Biggbrain,

Many people leave Microsoft in search of stability. I am one of them. I have no intention to write machine code or view hexadecimal values. I want a computer as a tool and not a hobby/pasttime. If your into assembling and compiling code that's great. It's not what I'm after.

 I believe over time Linux could become as commonplace among average home computer users as Microsoft. Serious programmers should not take offense towards those like me who want to try and use Linux. The learning curve is a daunting challenge for most average home users. I am willing to invest some time to learn the Linux OS to the point of being comfortable with it.

While trying to navigate in this Linux environment I can only hope the serious programmers will maintain their patience with we ignorant ones and maybe lend us a helping hand. It is easy to get frustrated when things don't work right. 

Ed

---

### Post by Cresho on 2009-03-09
I'll just say that I purchased stuff compatible with linux and windows xp.  I am very happy! :popcorn:

---

### Post by ozark_hillbilly on 2009-03-09
Cresho,

Was that by design or luck?

---

### Post by davidryder on 2009-03-09
Have you tried a different desktop environment (gnome, kde)?

---

### Post by ozark_hillbilly on 2009-03-09
DavidRyder,

Not sure what your asking. I am a virgin Linux user. Sorry.

---

### Post by saxofoner on 2009-03-09
Uh, am I the only one who can do everything, including dual monitor configs, from the nvidia-settings, gui-based manager?  It works flawlessly for me...

---

### Post by davidryder on 2009-03-09
```
sudo apt-get install kde
```
```
sudo apt-get install gnome
```

Log off
Choose options on the login screen and switch to the non-default environment. Gnome is used by default in Ubuntu so you will probably be choosing KDE.

---

### Post by webchimp on 2009-05-07
> **stalkier said:**
> I have a XFX 8500GT video card that runs very nicely on Linux. You can get one for like $50 or so right now. It is a 512MB card (PCIe). Check TigerDirect.

I've put a spare 500GT in my lounge Linux machine and am having driver probs.

In default mode I can only go up to 800x600, with the nVidia driver I can go up to 1024x768 but it only displays the middle portion on the screen. If you can imagine the outside couple of inches of display being off screen, thats what I get. I can get at the menus and such, I just have to use a bit of guesswork.

I'm outputting the signal to a standard tv via s-video. My older cards work fine, just have problems with the 8500.

AMD 64 x2 3800+
XFX 8500GT
MSI K9N6GM
512MB DDR2 (Could have sworn there was more in this machine)
Ubuntu 8.10 updated regularly

---

### Post by LowSky on 2009-05-07
> **webchimp said:**
> I've put a spare 500GT in my lounge Linux machine and am having driver probs.

In default mode I can only go up to 800x600, with the nVidia driver I can go up to 1024x768 but it only displays the middle portion on the screen. If you can imagine the outside couple of inches of display being off screen, thats what I get. I can get at the menus and such, I just have to use a bit of guesswork.

I'm outputting the signal to a standard tv via s-video. My older cards work fine, just have problems with the 8500.

AMD 64 x2 3800+
XFX 8500GT
MSI K9N6GM
512MB DDR2 (Could have sworn there was more in this machine)
Ubuntu 8.10 updated regularly


upgrade to 9.04, seems to have fixed some errors people where haivng with Nvidia drivers. dont forget to use the 180 driver under system >admin> drivers

then reboot and use the nvidia setting manager under system>admin to fix the display settings, please not you will need to be sudo to save changes. easiest thing it to run it fomr terminal

sudo nvidia-settings

---

### Post by webchimp on 2009-05-09
I've upgraded to 9.04, I'm using the 180 driver and nothings changed. I still get the same off screen desktop. I opened the settings screen using the terminal and nothing helped. Even changing down to 320x200 still had the top menu off the screen, although this time you could see the bottom edge of it.

Diagram (approximately):
[IMG]http://pics.webchimp.me.uk/ubuntu8500gt.PNG[/IMG]


I have a 7300gt that works fine, but the fan's a bit noisy and the only other spare card I have is a 6300 which like the 8500 is fanless but has an odd s-video socket that none of my cables fit.
[IMG]http://pics.webchimp.me.uk/ubuntu8500gt.jpg[/IMG]

---

