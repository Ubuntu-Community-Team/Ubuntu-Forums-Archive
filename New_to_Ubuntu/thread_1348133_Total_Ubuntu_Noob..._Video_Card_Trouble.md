---
title: "Total Ubuntu Noob... Video Card Trouble"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by Lee2010 on 2009-12-06
Hi I'm 17 and for the past month now I have been on a linux kick... I have downloaded MANY different forms of Linux and now I have made Ubuntu 9.10 my permanent OS but I am completely new to gnome... My ATI RAGE 128 PRO will not set to a resolution above 800x600 is there anything I can do? I tried to go into xorg.config but nothing happened... I have a Sun 24" monitor and 800x600 is not very useable... Any help would be nice... Remember I am 17 and relatively new to Linux and especially new to gnome so don't give me too much of a hard time.... I am trying to learn this so I don't have to use an OS that just slows down my computer.... and also is there any software that I need to download just to make Ubuntu better? Thanks

---

### Post by bradleypariah on 2009-12-06
I apologize if you have already tried this, but normally for an ATI driver, all you have to do is click:
[B]System > Administration > Hardware Drivers

[/B]If your card is even remotely new, the closed-source ATI driver should be listed there.
You would just need to hi-lite it and click "Activate".

Let us know if you've already tried that, if it works, or whatever the case may be.

Cheers!

---

### Post by Lee2010 on 2009-12-06
I tried that already and nothing happened... The ATI Rage 128 Pro is not new... it is kinda old...

---

### Post by presence1960 on 2009-12-06
> **Lee2010 said:**
> I tried that already and nothing happened... The ATI Rage 128 Pro is not new... it is kinda old...

Unfortunately AMD/ATI dropped support for linux drivers on their older cards.

---

### Post by Lee2010 on 2009-12-06
Well is there any way to change the resolution to anything higher than 800x600?

---

### Post by presence1960 on 2009-12-06
> **Lee2010 said:**
> Well is there any way to change the resolution to anything higher than 800x600?

I am sure there is but i am the wrong person to tell you how. I have an Nvidia card and they play very nicely with Linux so I really have no experience with your problem. I remember reading in here that you can use the open source driver but may lose a little functionality. Sit tight until someone who knows about this issue comes along. Sorry I can't be of more assistance.

---

### Post by Lee2010 on 2009-12-06
Thanks for your help anyway I'm glad to see this forum is quite nice :D

---

### Post by bradleypariah on 2009-12-07
Alright, well now that the obvious is out of the way, would you mind telling us what in your xorg.conf file you tried?  I used to have a similar issue with an ATI card.  

Look at this old thread of mine where somebody helped me out:
[http://ubuntuforums.org/showthread.php?t=1313849](http://ubuntuforums.org/showthread.php?t=1313849)

Not all the information relates, but it totally revolves around resolution, virtual resolution, and refresh rate.  This thread was from not too long ago, but it was before I started studying for my Linux Certification.  I was able to follow the guy pretty well.  Try seeing if any info in there is useful.  If nothing works, let us know and copy-and-paste your xorg.conf file on here for the "big dogs" to peruse.

---

### Post by ofb on 2009-12-07
While you're waiting for someone to come along with specfic advice, may I suggest googling 'karmic ati 128 rage pro'. Often google is better than the forum's built-in search. Chances are you'll find others have already asked about this.

Other than that, a little general advice: you may have to get another card. Legacy support for both ATI and Nvidia has fallen off since about Ubuntu 8.04. I've retired a few that are similar vintage.

To oversimplify how Ubuntu handles video, the base driver is open source. Then most people install the proprietory driver as bradleypariah recommends above. This is usually necessary to get 3D (games, effects, googleearth). However, some cards work fine with the open source driver and have no proprietory one.

Meanwhile I think you should ask around your friends for recently replaced cards sitting in their closets and try those. Off the top of my head, forget MX440SE and FX5200. I believe ATI Radeon 9600 works in Karmic. (Lot of people have trouble with that, but it seems to be with the laptop version, not AGP.) I'm doubting you're going to be able to get the old Rage going no matter what you tweak.

EDIT: bradleypariah came back while I was typing. Try what he says. You'll have a splendid adventure.

---

### Post by ST3ALTHPSYCH0 on 2009-12-07
ofb, I do have to disagree about the geforce mx440. I'm running one in Karmic up to 1600x1200 w/ 3d, but that's irrelevant.

@ OP, [ This](http://ubuntuforums.org/showthread.php?t=1319491&page=4;%20postcount=38) page has some pointers for editing your Xorg.conf. Post 38 tells how to derive and input modelines into your conf file. Post 34 has a link to my cheater's solution. Good luck.... resolution problems can be tricky.

---

### Post by ofb on 2009-12-07
ST3ALTHPSYCH0, no problem. You've got the MX440SE working no sweat? (SE is different from regular MX440. It was the more common discount version.)

EDIT - I just read your 'revolution' about that. Very slick. I'll have to try it.

---

### Post by ST3ALTHPSYCH0 on 2009-12-07
I've said it before. It was allegedly taken out b/c it would often mess up a working system.... but people with working system don't go randomly messing with their xorg.conf file, and the ones that do know how to fix their mistakes!

BTW, I'm not sure if I have the standard 440 or the SE. I'll have to see if I can't clarify that point.

---

### Post by Lee2010 on 2009-12-07
I'm not at home right now to check my xorg.config... I tried checking it last night and when I actually brought it up using the terminal it was blank. On another forum someone told me I should just get a new video card since mine is so old. I have an elsa synergy II somewhere would that work better in Ubuntu?

---

### Post by Lee2010 on 2009-12-07
Ok so I looked around and I tried using xrandr to add 1024x768 and nothing happened... Now when I try using xrandr this is what shows up

Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
  1024x768_60.00 (0x7a)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz

what am I supposed to do now?

---

### Post by Lee2010 on 2009-12-08
Is there anything I can do to change my resolution?!?! I'm beginning to wonder if I need to go back to my other linux distros....

---

### Post by Citadel1980 on 2009-12-08
I have an ATI x300 card which has been classified as a legacy card by ATI/AMD. Also the latest Linux Kernels do not support the proprietary drivers from ATI. The built- in drivers have to do the job.

I ended up installing Ubuntu 8.04.3 LTS (Long Term Service) - it allowed me to install the proprietary drivers for my x300 from ATI. You should also be able to use Ubuntu 8.10 and install the proprietary drivers.

I don't know how you can fix your resolution problems other than editing your xorg file or by just going into the preference menu and selecting Display and working from there.

If you can't get better resolution with the latest version of Ubuntu you might want to consider using an older release (8.04.3 LTS) or by buying a newer video card or getting an older Nvidia card like the 8400 GS or anything newer. My ATI card has a 2005 date of manufacture on it. My Nvidia card is circa 2007.

I bought a new Nvidia 8400 GS on Amazon for $28 last week and it works great. It's a cheap lowend card but it works. The difference is like night and day. I can use the proprietary Nvidia drivers by going to Hardware Drivers in Ubuntu. Install and reboot and everything works. Video works without stuttering, streaming video works, no tears/pixels or goofy colors when moving application windows. I run Google Earth without stutters, unlike the ATI card. I have XMBC installed and watch movies and videos. It just works!

A newer card may be your solution - something newer than your current card. And not something top of the line or crazy in price.

---

### Post by 3rdalbum on 2009-12-08
> **Citadel1980 said:**
> A newer card may be your solution - something newer than your current card. And not something top of the line or crazy in price.

The Rage 128 Pro is about 9 years old from what I remember. I wouldn't be surprised if there were never any proprietary drivers for that model. I'm not sure you could find a graphics card that will work in a computer that old.

Today, Xorg can configure itself without an xorg.conf file - that's probably why you don't have one or it appears "blank". If you turn off X temporarily and run the "sudo X --configure" command it should generate an xorg.conf for you, that you can edit as you see fit.

---

### Post by bradleypariah on 2009-12-08
> **3rdalbum said:**
> The Rage 128 Pro is about 9 years old from what I remember. I wouldn't be surprised if there were never any proprietary drivers for that model. I'm not sure you could find a graphics card that will work in a computer that old.

Wouldn't that depend on the slot-type itself, really?
My girlfriend has a quite old computer and I was able to just slap a couple 1GB sticks of RAM in it and I bought a simple 256MB Nvidea card for like $40.
I was naive and didn't even consider the age of the computer.  I saw it took AGP so that's what I bought.  It worked without a hitch.

Also, not for nothing, but it's also important to note that Linux is famous for not requiring everybody go out and buy new hardware.  Instead of throwing money at your problem, did you guys try clicking on ST3ALTHPSYCH0's link in his signature? 
[http://ubuntuforums.org/showthread.php?t=1320785](http://ubuntuforums.org/showthread.php?t=1320785)
He has a great & simple way to fix resolution in another post.

All you need to do is download ubuntu 8.04, burn a CD, boot from the live iso, and follow a few simple steps.  You're basically asking 8.04 to create a new xorg.conf file from scratch for you.  It seems everyone on this post is unintentionally ignoring/missing what he said yesterday.

The theory is there and it worked for him.  The whole procedure should take no more than a few minutes (besides actual download time).

---

### Post by ST3ALTHPSYCH0 on 2009-12-08
I don't mean to sound like a jerk, but it seems like a lot of people don't want to click a link and read another post. 
Anyway, my card is the standard mx440 not the SE, but the screens and graphics workaround should work regardless. In theory, the generic driver should run darn near anything, and you'll just have to explain to the xserver what you want send along the bus.

---

### Post by presence1960 on 2009-12-08
> **ST3ALTHPSYCH0 said:**
> I don't mean to sound like a jerk, but it seems like a lot of people don't want to click a link and read another post. 
Anyway, my card is the standard mx440 not the SE, but the screens and graphics workaround should work regardless. In theory, the generic driver should run darn near anything, and you'll just have to explain to the xserver what you want send along the bus.

I bookmarked that link. I also read it & reread it a few times. Even though I have no problem with the issue under discussion, it is always nice to learn and gain some knowledge. Also would be nice to point someone with this issue to that thread as a possible solution. Thanks for the link.

---

### Post by bradleypariah on 2009-12-09
> **ST3ALTHPSYCH0 said:**
> I don't mean to sound like a jerk, but it seems like a lot of people don't want to click a link and read another post.
Dude!  Seriously!  I was laughing my butt off reading what some people were writing in that thread, too.  It's like they open the thread and immediately post that they are having issues in there without actually trying what you suggested in post #1.  It's sad and hilarious all at the same time.  I've quoted myself three times.

---

### Post by ST3ALTHPSYCH0 on 2009-12-09
I just visited my post for the first time in a while. I forgot that I linked to it in my sig and haven't watched it. LOL, thanks for keeping up my slack!

---

### Post by sandyd on 2009-12-09
alright.

run this
```

sudo apt-get install xserver-xorg-video-ati
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```restart
if it doesn't work, then
```
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
sudo gedit /etc/X11/xorg.conf
```in the monitor section, add this
```

        Identifier   "0-Main"
        Option      "PreferredMode" "1024x768" //monitor resolution                 
        Option      "TargetRefresh" "60" //monitor refresh rate                                          
        Option      "Rotate" "normal"     //rotation (dont need this)                     
        Option      "Disable" "false"  //make sure its gonna be enabled

```ive added comments for refrence purposes

in the device section, add this
```

        Identifier  "Configured Video Device"
        Driver "ati"

```in section "screen"
add this
```
        Identifier      "Default Screen"
        Device          "Radeon 9600"
        Monitor         "Generic Monitor"
        DefaultDepth    24 //depth of color
        SubSection "Display"
                Depth           24 //depth of color
                Modes           "1440x900" //resolution
        EndSubSection

```EndSection

---

