---
title: "Funky laptop with Ubuntu"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by Flasimbufasa on 2009-05-13
Specs to start off:
Ubuntu 9.04
1 Gig Ram
IGP Radeon 340M
Compaq Presario 2100 Series

Alright, so to start off with, the video driver. I can not seem to enable 3D, nor manage to install the propriety driver.

The drive IS 3D compatible, and I have experimented with the x.org file, without any avail. Caused the system to not boot to the log in screen, had to restore the out of box version.

I checked the propriety drivers, The card is not even listed, the entire page is blank. I do not know what that means ;-;

I checked the synapic package manager, and tried installing the Radeon related drivers, Bad idea:
Every time this has caused Ubuntu to load, but when it gets to bringing up the login screen, the screen has static on it, and some weired characters on the top of the screen, usually wiht a big green box in the center.

I tried the xfix [for the video driver in the system rescue boot menu option] but it did nothing, I had no clue what to do, so I just now reinstalled it.


******
Another problem I am having:
FN+F5= switch display screens [S-video out]  I can not figure how to enable this, I went to a few sites, however I just got confused as to what they were talking about.

---

### Post by skymera on 2009-05-13
> 
Alright, so to start off with, the video driver. I can not seem to enable 3D, nor manage to install the propriety driver. 

Your graphics chip is unsupported by AMD (FGLRX). You need to use the open-source version.

>  The drive IS 3D compatible, and I have experimented with the x.org file, without any avail. Caused the system to not boot to the log in screen, had to restore the out of box version. 

If you add the driver line to read "ati". it should automatically select the best driverr for you. Search the forums or Google as to where to add the driver line. ( I would show you now, however im at college with no access tio Ubuntu.)

> I checked the propriety drivers, The card is not even listed, the entire page is blank. I do not know what that means ;-; 

You're not supported anymore in Jaunty.

> I checked the synapic package manager, and tried installing the Radeon related drivers, Bad idea:
Every time this has caused Ubuntu to load, but when it gets to bringing up the login screen, the screen has static on it, and some weired characters on the top of the screen, usually wiht a big green box in the center. 

 Sounds about right :) 

> I tried the xfix [for the video driver in the system rescue boot menu option] but it did nothing, I had no clue what to do, so I just now reinstalled it. 

It was probably trying to boot with the wrong driver.


> ******
Another problem I am having:
FN+F5= switch display screens [S-video out]  I can not figure how to enable this, I went to a few sites, however I just got confused as to what they were talking about. 

Hmmm, this should work when you have the correct driver running.

---

### Post by Flasimbufasa on 2009-05-13
._.

All that I can say... Just... Thank you so much! :D
This really has straightened out A LOT of issues I have been having-

I found ***_A_*** site that is about Jaunty and Radeon drivers, however the driver used, is not one that is *ideally *compatible with my video card.

LINK: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)
Okay, so does this mean I must look up the older driver [I know where to get it] that I want and just change all the command lines myself?
OR
Can I just follow these steps in that guide and just change x.org myself to what I want it to do?


Oh and one last thing:
This made me laugh:
     
>   [quote]I checked the synapic package manager, and tried installing the Radeon related drivers, Bad idea:
Every time this has caused Ubuntu to load, but when it gets to bringing up the login screen, the screen has static on it, and some weired characters on the top of the screen, usually wiht a big green box in the center. Sounds about right :smile: [/quote]By the way: You are godly ^^;
Just saying.


LONG LIVE LAPTOPS THAT ARE 4 YEARS OUT OF DATE! YEAH!! ;D

EDIT:
After reading this I discovered a major flaw in my idea of making this driver thing work [good thing I reread a few times]

>  the new driver doesn't support any of the older ATI cards anymore. Which cards does ATI no longer support? *The ATI Radeon 9500-9800,X300-X2100,Xpress.  See the complete list [[1]]("http://wiki.cchtml.com/index.php/9.4") here.* If your card is on that list, you are restricted to the 9.3 driver - however since 9.3 driver doesn't support xorg-xserver 1.6, it will not work with Jaunty! This guide currently is for installing 9.4.

---

### Post by Flasimbufasa on 2009-05-14
*headdesk*

I am having to resort to the open source driver as it seems. I haven't any clue how to do this however.

Where I am:

>  $ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon IGP 330M/340M/350M [1002:4337]
After that step of this guide: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
I get lost. It seems jumbled and I fail to follow where to go next. Hardware Drivers under system admin is completely blank, I did not upgrade from the Intriped to Jackle, so I do not see the necessity of the rest between editing the x.org file and the finding if the driver is supported.

So now I am inclined to ask: Where is the driver? x.org is a file, right? how can it be a driver if this is what it says whenever I open it?

> Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
I am so fail at ubuntu :cry:

EDIT:

Ran another command mentioned:
> $ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.


SGI, according to the site, is supposed to be ATI???


WHAT AM I DOING WRONG ;~; [/freaking out spazz suff]

---

### Post by Flasimbufasa on 2009-05-14
*Sigh*
Alright, I have found another site that had what someone did to enable their ATI graphics card.

All that applied to me:
>  sudo su
dpkg-reconfigure xserver-xorg


now my x.org is like this:

>  Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


At this point, the guy had everything filled out, however, I just fail at this... ;-;

site: [http://ubuntuforums.org/showthread.php?t=1133931&page=20](http://ubuntuforums.org/showthread.php?t=1133931&page=20)
Hasplu is the person I got this from.

---

### Post by Flasimbufasa on 2009-05-14
Alllriightyy thenn..

I am about to give up for the night, One more post to my already long string of failures...

Something called "Git Repository" caught my eye while searching for what to do next...

Anyone know anything about this? If so I will read more on it, but right now, school project.

> 
$ mkdir /tmp/src
$ cd /tmp/src
# Now, place the git_xorg script in this directory
$ chmod a+x git_xorg.sh

I got to there on the guide [I just now realized I skipped half of the stuff on the page.... Dang I am intelligent..]

Anyways: Help would be highly appreciated.
Thanks.

---

### Post by AndThenWhat on 2009-05-14
All that 'dpkg-reconfigure xserver-xorg' does is resets your xorg.conf file to how it was when you first installed Ubuntu.  I just searched the net and it sounds like that card is unsupported by the 'fglrx' driver.  Does anything come up if you run "sudo dpkg-reconfigure xserver-xorg" and then go to (System -> Administration -> Hardware Drivers) ?

---

### Post by Flasimbufasa on 2009-05-14
I am getting nothing at all. It appears that I am having to use the open source drivers, but I honestly have no clue what I need to do. I am getting so lost in all this stuff...

I mean I have gone through 4 or 5 different ways of installing this driver now, I think.
Each time:

FAILURE

*headdesk*

I beat this driver in Windows, I am not going to give up doing the same in Ubuntu. Even though.. It does appear to be winning at the moment...

---

### Post by AndThenWhat on 2009-05-14
Okay, I found a post of someone with your video card who got 3d to work on Hardy.  He installed the following packages from the Debian Sid repositories:

xserver-xorg-video-ati_6.8.192-1_i386.deb
xserver-xorg-video-mach64_6.8.0-1_i386.deb
xserver-xorg-video-r128_6.8.0-1_i386
xserver-xorg-video-radeon_6.8.192-1_i386

You need to find similiar packages (they may not have the exact numbers).  I would try going to (System -> Administration -> Software Sources) and adding "deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) unstable main contrib non-free". After you reload your packages you may find the ones listed above in Synaptic with that repository enabled.  However, as soon as you install those packages you need to remove that entry in Software Sources because they are from Debian's unstable repository meaning most of the packages in it may be broken or have a negative affect on your system if you install them.

---

### Post by Flasimbufasa on 2009-05-14
I did what you said, and found that I had those installed already, however needed to be updated. I am updating and such at the moment.

Reboot? What next?

I shall proceed to reboot then, I have nothing to lose, I have a backup disk

---

### Post by Flasimbufasa on 2009-05-14
Uhmmm well this sure is... different...

I logged out and back in:

Screen size is a lot smaller, my x.org is the same, no difference in the repo's.

<<
>>

Uhmm Well seeing as how I could log in, I guess I shall reboot [I so hope this works]

---

### Post by AndThenWhat on 2009-05-14
Have you succeeded in getting 3D to work with those new drivers?

---

### Post by Flasimbufasa on 2009-05-14
Well I have gone about what you said;

No visual effects on desktop, no changes to the x.org, screen resolution is smaller, cannot change.

Uhmm what now?

EDIT:
Nothing is newer. I do not have any new support, nothing in repo's still.
The x.org files are completely blank as they were in first post. =/

---

### Post by AndThenWhat on 2009-05-14
Try going into a terminal (Application -> Accessories -> Terminal) and typing "compiz --replace" (no quotes). If that works correctly then your desktop effects should be enabled. If not, then it may give you a helpful error message.  By the way, press CTRL+C in the terminal to end that command if it gets rid of your window borders or whatever and then run the command "metacity --replace" (no quotes).

---

### Post by AndThenWhat on 2009-05-14
If the effects do work then you can permanently turn them on by going to (System -> Preferences -> Appearance) and go to the Visual Effects tab and set it to Normal.

---

### Post by Flasimbufasa on 2009-05-14
I can not do the desktop method [tried it already and got an error saying that it isnt able to, not sure right now, will post or edit it in later.]

Error with the first code:
>  not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
a
The code to fix this returned with [I could not type, so I had to go into ctrl+alt+f1 to try it]

>  Unable to load X

---

### Post by AndThenWhat on 2009-05-14
Well if I were you I would make this an ongoing project to figure it out. Unfortunately, you ATI users usually always have a hell of a time figuring out this kind of stuff. I recommend searching the web in your free time and maybe you can fix it even though it seems you have one of those troublemaker graphics cards. This seems relevant to the output you posted above:

[http://ubuntuforums.org/showthread.php?t=627088&page=2](http://ubuntuforums.org/showthread.php?t=627088&page=2)

Also, try posting this again in the Multimedia & Video form. They will know way more about this kind of thing than I do.

---

### Post by Flasimbufasa on 2009-05-14
>  you ATI users

Ahem. I appologize I picked up Ubuntu 2 weeks ago and am trying to install what I have, Trust me, if I could, I would get another laptop, but this was free and my parents will not get me a new one.

>  Also, try posting this again in the Multimedia & Video form. They will know way more about this kind of thing than I do.
Alright I shall do that. Should I copy and paste everything in those 5-6 posts of mine that state what happens when I did something?

---

### Post by Jive Turkey on 2009-05-14
You simply cannot use the proprietary driver for that chip, it wont work, use the open-source driver.

in your xorg.conf file, inside the device section, place an entry that says:
```
Driver     "ati"
```

Also note that compiz and desktop effects will not work, don't even try.

If you had a proprietary driver working on a previous version of ubuntu, using you may consider reverting back to that version.  An older version of xserver may be compatible with the driver that is compatible with your chip.

I post this with these assumptions in mind:
AMD-ATI state on their site that your graphics chip is not supported by the driver, or is not listed as being supported by their driver.

consider nvidia hardware for your next purchase if you need good 3d performance.

---

### Post by Flasimbufasa on 2009-05-14
You sure do sound sure.

Well then how come earlier, before trying to install those packages [which I am now uninstalling], did i have my laptop working perfectly with the highest effects, screens swishing and sticking to walls? 

That worked quite well.

So Since you are here, how does that "Open source driver" work? Nothing/no one has been able to explain it yet... ;-;

EDIT:
Appears that i cannot find the packages. Time for another system restore...

EDIT V2:
Wow... I feel bad now... thanks Jive for the code line, that is what was missing! :D

Uhmmm Yeah I got all functions back. I am about to go in and mess with x.org a little ^.^

Anyways I appreciate the help. [Now I just gotta get that little 3d rendering this card has]

EDIT V3:
X.org is still empty except that 1 line I added. Is this normal?

---

### Post by Flasimbufasa on 2009-05-14
Alright so here is what I did:

Installed the 4 packages mentioned earlier.
Inserted the driver line in x.org.
Edited x.org
Worked like a charm

[Solved]

---

