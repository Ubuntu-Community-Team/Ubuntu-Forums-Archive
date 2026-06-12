---
title: "A few things i need help with."
date: 2010-06-20
forum: New to Ubuntu
---

### Post by Icewiing922 on 2010-06-20
Hi ubuntu people ! I've been using ubuntu for a while now (about 4 months) and ive just decided to get some help with some issues i have. I must note i am VERY new to everything in linux. i hardly know how to do anything with terminal. but i get along. please explain to me slowly lol.
1st of all. i have looked and searched the threads here and either could not find anything or the methods didn't work. so.

For a start. 
1. Before ubuntu updated to 10.04 LTS i used to have a passworded hard-disk. where only i could access it by typing in a password. is there anyway to get that back in the new 10.04 LTS version i have ?

2. While playing and using any video player. i get a message pop up saying "Can't play a text file without video" on a few video players that i have. I am using MKV files. they are 24~ minutes long. and i have tried over 70 other episodes. 

3. Finaly it is a graphics card issue i guess. but i have about 6 lines which like.. tear the screen at the bottom. its sometimes makes shadows of texts or image behind it. but it is a 1 pixle like. all the way across the screen. i know this is not the Monitor it'self because i use the same monitor for TV and Xbox 360. works fine. I also cant make the resolution higher than 1024 x 768. If i do. the TV comes up with a message which says something like "Out of range". 

Thanks guys please assist on these issues as soon as you can thank you ^^. 

(Also please say if this is the wrong place to post this. I really have no clue where to put it. the forum confused me ! lol) 

Linux lover - Icewiing :D

---

### Post by wesleybishop on 2010-06-20
here try this out for question #1 [http://www.youtube.com/watch?v=M4JYkZxnhJw](http://www.youtube.com/watch?v=M4JYkZxnhJw)

---

### Post by wesleybishop on 2010-06-20
> **Icewiing922 said:**
> 
2. While playing and using any video player. i get a message pop up saying "Can't play a text file without video" on a few video players that i have. I am using MKV files. they are 24~ minutes long. and i have tried over 70 other episodes. 


Have you tried installing restricted extras and what player are you using?

---

### Post by wesleybishop on 2010-06-20
> **Icewiing922 said:**
> 
3. Finaly it is a graphics card issue i guess. but i have about 6 lines which like.. tear the screen at the bottom. its sometimes makes shadows of texts or image behind it. but it is a 1 pixle like. all the way across the screen. i know this is not the Monitor it'self because i use the same monitor for TV and Xbox 360. works fine. I also cant make the resolution higher than 1024 x 768. If i do. the TV comes up with a message which says something like "Out of range". 

I think I know the solution to your problem but I need to know are you using a LCD or a CRT monitor and what type of graphics card you are using.

---

### Post by Icewiing922 on 2010-06-21
> **wesleybishop said:**
> Have you tried installing restricted extras and what player are you using?

I've tried reinstalling the programs if that is what you mean? 
I have tried. 
VLC media player
Movie player. (i think came with Ubuntu)
GNOME Mplayer.

---

### Post by Icewiing922 on 2010-06-21
> **wesleybishop said:**
> I think I know the solution to your problem but I need to know are you using a LCD or a CRT monitor and what type of graphics card you are using.


LCD monitor 
Nvidia GeForce 6200
My monitor was released about a year ago. so quite new.

---

### Post by Ozymandias_117 on 2010-06-21
> **Icewiing922 said:**
> I've tried reinstalling the programs if that is what you mean? 
I have tried. 
VLC media player
Movie player. (i think came with Ubuntu)
GNOME Mplayer.

He means type this in a terminal: ```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by wesleybishop on 2010-06-21
go to administration then click on hardware drivers make sure you are using the recommended version. Then go back to administration click on Nvidia X Server Settings check and make sure you LCD resolution and MHZ match what you have in the Nvidia settings panel.

---

### Post by wesleybishop on 2010-06-21
> **Ozymandias_117 said:**
> He means type this in a terminal: ```
sudo aptitude install ubuntu-restricted-extras
```

Exactly :guitar:

---

### Post by wesleybishop on 2010-06-21
Okay so give us a update have any of the 3 problems been solved? If so which ones.
Thanks):P

---

### Post by SoFl W on 2010-06-21
> **Icewiing922 said:**
> 1. Before ubuntu updated to 10.04 LTS i used to have a passworded hard-disk. where only i could access it by typing in a password. is there anyway to get that back in the new 10.04 LTS version i have ?

A simple answer without having to watch a video.
[http://ubuntuforums.org/showthread.php?t=1467629](http://ubuntuforums.org/showthread.php?t=1467629)

---

### Post by Icewiing922 on 2010-06-21
> **wesleybishop said:**
> go to administration then click on hardware drivers make sure you are using the recommended version. Then go back to administration click on Nvidia X Server Settings check and make sure you LCD resolution and MHZ match what you have in the Nvidia settings panel.

Ok thanks. Where am i looking in the NVIDIA X Server Settings program ?

---

### Post by Icewiing922 on 2010-06-21
> **Ozymandias_117 said:**
> He means type this in a terminal: ```
sudo aptitude install ubuntu-restricted-extras
```

Unfortunately after trying this. putting in password. going through all the checking whatever. And restarting my computer, i still get the same error message.

---

### Post by Icewiing922 on 2010-06-21
> **SoFl W said:**
> A simple answer without having to watch a video.
[http://ubuntuforums.org/showthread.php?t=1467629](http://ubuntuforums.org/showthread.php?t=1467629)

Ok this is perfect ! thanks for your help SoFl. 

and sorry [wesleybishop]("http://ubuntuforums.org/member.php?u=907051"). this thread was easier to understand :D

---

### Post by wesleybishop on 2010-06-21
> **Icewiing922 said:**
> Ok this is perfect ! thanks for your help SoFl. 

and sorry [wesleybishop]("http://ubuntuforums.org/member.php?u=907051"). this thread was easier to understand :D

No problem :p

---

### Post by VastOne on 2010-06-21
This thread could be a sticky for "new users - how to ask for and get quality help on the forums"

Well done everyone

:popcorn: :KS :guitar:

---

### Post by Icewiing922 on 2010-06-21
I still need help with the 2nd and 3rd issues. Anyone Found anything new out? The 3rd more so as it can be hard to read things on the computer. thanks.

---

### Post by VastOne on 2010-06-21
Number 2 looks like a bug....

See [_[COLOR="Red"]Here[/COLOR]_]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/489104")

with a fix committed for the next release

---

### Post by VastOne on 2010-06-21
For number 3 have you done what wesleybishop suggested and check that the restricted drivers are loaded?

System/Administration/Hardware Drivers make sure the bottom one is enabled? 

Or you can go to System/Preference/Appearance to the Visual Affects tab and select Extra and the hardware drivers will be installed for you from there

You will need to restart once they are loaded.

---

### Post by Icewiing922 on 2010-06-21
Ok these are some screen shots of the above locations. I noticed it said my monitor is CRT. Which it is not.

---

### Post by VastOne on 2010-06-21
> **Icewiing922 said:**
> Ok these are some screen shots of the above locations. I noticed it said my monitor is CRT. Which it is not.

How do you have this monitor connected? VGA?  Is the 6200 card a DVI card?  Does the monitor have DVI input?

Edit, I see that the 6200 is DVI capable.  What is the brand and model number of your LCD monitor?

---

### Post by Icewiing922 on 2010-06-21
[B][SIZE=2]Foehn & Hirsch 19 inch HDTV
[/SIZE][/B]

Dunno about the model number. but they only have one of those

---

### Post by VastOne on 2010-06-21
> **Icewiing922 said:**
> [B][SIZE=2]Foehn & Hirsch 19 inch HDTV
[/SIZE][/B]

Dunno about the model number. but they only have one of those

OK, this does have DVI input, are you connecting that way with a DVI cable?

---

### Post by Icewiing922 on 2010-06-21
From computer to monitor im connecting via VGA

---

### Post by VastOne on 2010-06-21
> **Icewiing922 said:**
> Ok these are some screen shots of the above locations. I noticed it said my monitor is CRT. Which it is not.

From within the second pix that you are showing, see if you can change the resolution to 1366 * 768, which is the maximum res that this monitor/tv can handle.  If you can, report back and I will advise you on how to make this permanent.

---

### Post by VastOne on 2010-06-21
> **Icewiing922 said:**
> From computer to monitor im connecting via VGA

Did you get a DVI cable with this TV?

---

### Post by Icewiing922 on 2010-06-21
> **VastOne said:**
> From within the second pix that you are showing, see if you can change the resolution to 1366 * 768, which is the maximum res that this monitor/tv can handle.  If you can, report back and I will advise you on how to make this permanent.

Ok. everything seems to be working with that. but It's stretched. vertically i think. Any way to make it its native resolution? (1440 x 900)

---

### Post by Icewiing922 on 2010-06-21
> **VastOne said:**
> Did you get a DVI cable with this TV?

No and i just looked. and it has no DVI on the tv.

---

### Post by VastOne on 2010-06-21
> **Icewiing922 said:**
> Ok. everything seems to be working with that. but It's stretched. vertically i think. Any way to make it its native resolution? (1440 x 900)

Did you see 1440 * 900?  

If [[COLOR="Red"]_this_[/COLOR]]("http://www.foehn-hirsch.com/19-lcd-tv.html#spec_pop") is your LCD, ith should have DVI input...

---

### Post by Icewiing922 on 2010-06-21
> **VastOne said:**
> Did you see 1440 * 900?  

If [[COLOR=Red]_this_[/COLOR]]("http://www.foehn-hirsch.com/19-lcd-tv.html#spec_pop") is your LCD, ith should have DVI input...


[http://www.savapoint.com/product/Foehn-Hirsch-19-inch-Freeview-LCD-HDTV,6357](http://www.savapoint.com/product/Foehn-Hirsch-19-inch-Freeview-LCD-HDTV,6357) 

 This is the one i have and...

no there is no resolution of that on there. :(

---

### Post by VastOne on 2010-06-21
> **Icewiing922 said:**
> [http://www.savapoint.com/product/Foehn-Hirsch-19-inch-Freeview-LCD-HDTV,6357](http://www.savapoint.com/product/Foehn-Hirsch-19-inch-Freeview-LCD-HDTV,6357) 

 This is the one i have and...

no there is no resolution of that on there. :(

From that page ---


Connections
* RF TV/CATV 75ohms coaxial x 1
* Video In Video:RCA 75ohms composite video x 1
* YPbPr component input x 1
* PC In HDMI / DVI / VGA
* Audio In L/R RCA-1
* Scart RGB/CVBS in, CVBS out x 1
* HDMI x 1 up to 1080P

You should have a DVI connection on it and in the second picture there it shows it right next to the VGA plugin.  My advice is to get a DVI cable and see if that makes a difference.

---

