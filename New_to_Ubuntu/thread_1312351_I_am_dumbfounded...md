---
title: "I am dumbfounded.."
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Naranwien on 2009-11-03
Hey there.

I installed Ubuntu 8.04 about a week ago. Everything was good, until I sat down and opened Gimp to do some drawing with my Wacom tablet. 
It's just more like a glorified cursor now than anything, can't be drawn with anyhow. 
So I looked around on how to get it to work. And I have been looking for several days now and I am absolutely dumbfounded. I am normally a Windows Xp user, but since last virus attack and windows crashing and the installation CD being lost I gave up. Anyhow, basically I don't understand anything at all about what I'm supposed to do to get my wacom tablet working.

I keep looking at all these guides and helpsections, I don't know what i am looking for for starters, secondly, all I see in the documents are a bucketload of commandlines. No clickable links, no downloadable drivers, nothing (Yeah, stupid winbdows user, I know, lazy too). So, I'm guessing it's all supposed to be written into some document by hand or what? Or some kind of commandprompt or? I am in desperate need of help. I really wanna stick with this Ubuntu thingy, cause I am sick of Windows and all the crap, viruses, stupid .dll files ALWAYS messing everything up. 

So, please help a silly windows user eh? Cause as far as I'm concerned I could be looking at chinese symbols and understand just as much... nearly, not THAT bad ;)

---

### Post by wilee-nilee on 2009-11-03
With a quick Google search I found this which is a manual so you might check it out I don't use gimp. [http://docs.gimp.org/](http://docs.gimp.org/)

---

### Post by werecatomega on 2009-11-03
1. go to System/Admin/Synaptic Package Manager
2. in the quick search, search gimp
3. the first one should be gimp, so right-click it, and press mark for re-installation
4. press apply and wait

if this doesn't work, i'm not sure what it is.

---

### Post by Naranwien on 2009-11-03
I don't think it's a problem with Gimp, it's the tablet that's not working. It doesn't have any pressure sensitivity like it used to. And I have to press the pen down for the cursor to move, whereas before I could just hold it above the surface slightly and the cursor would move. So basically, I can't draw with it.. very frustrating.

---

### Post by ranch hand on 2009-11-03
I believe, I do not have one, that wacom support is getting better out of the box.

One thing that I would do is edit your sources list to enable "backports".  I have Hardy and it is getting a little "old".

I want one of those buggers so I have been watching for this kind of thing here on the forums.

[http://ubuntuforums.org/showthread.php?t=967147](http://ubuntuforums.org/showthread.php?t=967147)

There appears to be a lot of tweeking possible but what is really needed, and I believe is improving, is more cooperation by the wacom folks.  I know some of people on the karimic testing forum were impressed with some of the things that they found.

---

### Post by Blacksyke on 2009-11-03
I cordially invite you to observe THIS: [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

Might help you out.  You may have to do additional fiddling if you have an Intuos4, but Wacom support appears to be an apt-get away.

The obstructions found at the link detail installing two packages, xserver-xorg-input-wacom and wacom-tools, using Synaptic or the command line.

Unless it got included while I wasn't looking in 9.10, there's no graphical setup utility like there is on Windows and Mac OS.

---

### Post by Naranwien on 2009-11-03
I'm gonna make an example now of what exactly it is I need help with. 

For example, I open up links that people give me (Thanks for the links, I really appreciate it) But then i run into things like this one for example.

"Basically for any Ubuntu release, always check first on [[COLOR=DarkRed]The Linux Wacom Project[/COLOR]]("http://linuxwacom.sourceforge.net/") if the version of the linux wacom driver you have in your distribution supports your model of tablet - use **System>Administration>Synaptic Package Manager**"

So I open the **Synaptic package Manager**. Okay, then what? I have no idea, it's like telling a person who has never seen a car before:

*"So first you need to press down the clutch, then you can change gears" - Okay, where's the clutch?*

I don't wanna sound rude, i hope I'm not. But what I need help with is -how- to get around in Ubuntu to make the changes I need to. I can look at a million pages about what needs to be done, but -how- I do that and where I find the options etc, I wouldn't have the slightest clue.

I know probably what I am asking for is alot, but basically I am that person who's "never seen a car before", I need step by step advice from a generous soul who's got the time for it. :)

---

### Post by ad_267 on 2009-11-03
8.04? How about upgrading to the most recent version of Ubuntu which will have a newer version of Gimp and better support for your devices.

---

### Post by Naranwien on 2009-11-03
Well, how do I install the newer version then? :D Haha

---

### Post by Blacksyke on 2009-11-03
The easiest way to get the Wacom packages installed may be to open a terminal window, and use the following command: ```
sudo apt-get install xserver-xorg-input-wacom wacom-tools
```

You'll have to give it your password.

If you're on 8.04, there may be some additional things to do, as detailed at [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) but I shall echo ad_267 and ask why you didn't grab the latest release when you installed?  The latest version of Ubuntu may just give you an easier time, not to mention updated versions of everything, including the GIMP.  Without being more familiar with 8.04, I couldn't go into the specifics of configuring the tablet beyond installing the software needed; perhaps someone else can help?  It would appear editing xorg.conf is needed for 8.04.

Be careful if you decide to give it a go and end up editing xorg.conf, as detailed at the link, as it's easy to explode things.  Using a new release will avoid this particular step!

---

### Post by Favux on 2009-11-03
Hi Naranwien,

You are using Hardy (8.04) correct?  Which Wacom tablet do you have?  Is it usb or serial?

You go in Synaptic Package Manager (in Administration).  Then click on the search icon, upper right.  Enter "wacom" (without the quotes".  The linuxwacom packages wacom-tools & xserver-xorg-input-wacom should pop up.  Make sure the box in front is green (installed).  If not click on it and and choose mark for installation.  Then pick the apply green arrow on top left and it'll install it for you.  Make sure you make a note of what version number they are.  You can reboot.

Next you'll have to configure your xorg.conf which is pretty simple and you're done.

There are a couple of graphic tablet configuration programs.  The one that comes with linuxwacom is called wacomcpl.  Enter it into a terminal and it pops up.

---

### Post by Naranwien on 2009-11-03
Well, a long time ago I downloaded Ubuntu 8.04 as a backup in case my Windows XP crashed. So when now finally my Win XP did crash I just used the CD I had so I wouldn't sit with a machine and no OS.

---

### Post by mivo on 2009-11-03
> **Naranwien said:**
> Well, how do I install the newer version then? :D Haha

9.10 has some issues, as it is brand-new, but in your case, I think trying 9.10 may indeed be the best approach. Driver support is likely to be better, and if nothing else, documentation is more likely to be on the same page as you are (and so will be many users).

If you haven't fiddled too much with your system yet, just doing a clean reinstall is the best approach. You can [get 9.10 here]("http://www.ubuntu.com/GetUbuntu/download"). Try the Live CD before you install, just to make sure your computer is properly supported (internet connection, etc.).

---

### Post by Naranwien on 2009-11-03
"Which Wacom tablet do you have?  Is it usb or serial?":

I'm just taking a wild guess here and writing down what's at the back of it. It was given to me by my bro and all I have is the tablet and the driver disk, which obviously doesn't work in Ubuntu.

WACOM
Model: CTE-440 (CTE-440/s)

It's USB by the way.

---

### Post by sloggerkhan on 2009-11-03
I have a wacom. Don't know about 8.04, but last I checked to use it all that's needed is edit>preferences>input preferences and for your wacom device enable everything. I think Ubuntu automatically has xorg setup to detect a tablet device.

---

### Post by ranch hand on 2009-11-03
Ok, you could probably look up my earliest posts and find pretty much the same problem, this is the Absolute Beginner Talk forum.

Did you find out what driver you need from the link you provided?

Go to your terminal Applications>Accessories>Terminal and right click on it.  Click on add to panel.  you can move it anywhere on either panel you want.

Click on the sucker and pull it up and run (just copy/paste);
```

gksudo gedit /etc/apt/sources.list

```
Hunt around on there and you will find something very similar to this from my 9.04 sources.list;
> 
    ## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

Note all the # or "hash" marks.  These indicate a comment that is not used by a program or script but clarifies it, or in this case disables the hashed stanza.  As I have done with the next to last line, unhash that line (it is hashed by default).

Save the file and close it.

Run
```

sudo apt-get update

```
This will get any/all newer stuff that has been "backported" to work in 8.04.

Go to synaptic and click on the "search" button and enter wacom and see what you get there.  Jaunty has 2 entries that come up, one installed by default.

If you know your right driver you could search for it too.  It might be in there.

Here is a good link to explain some things and help setting up your system;
[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

---

### Post by mivo on 2009-11-03
Sounds like a Graphire4, so it's an USB model, unless I'm mistaken.

---

### Post by ranch hand on 2009-11-03
Another good thing to do, I know this from lurking on wacom threads, is listen to whatever Favux has to say.

Seems to be quite the guru of wacom configuration.

Sorry Favux, if I stepped out of line there but I am just calling it as I see it.

---

### Post by Favux on 2009-11-03
Hi ranch hand,

Not a problem.  The more the merrier.  Besides I'll probably be hitting you up about Grub2 soon!


Hi Naranwien,

I think mivo's right, a Graphire4.  So the Hardy linuxwacom drivers should support it.  I think they're version 0.7.9-1 or maybe 0.8.1?  Right after usb support was added anyway.

So it's up to you.  You have to do some configuration either way.  Using xorg.conf in Hardy or Intrepid.  Or the wacom.fdi in Jaunty or Karmic.

How many buttons on the stylus?

---

### Post by Naranwien on 2009-11-03
Meh... still not working. :( I did all I was advised to do, and still no change. Should I install the newest version of Ubuntu? Would that help?

---

### Post by Naranwien on 2009-11-03
Stylus? o_O What's that? <hides>

---

### Post by Favux on 2009-11-03
Hi Naranwien,

Did you install the drivers through Synaptic?  It's the pen you write on the tablet with.

Next we have to configure xorg.conf.

First make a back up of your current, working xorg.conf. In a terminal enter (copy and paste):
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
sudo makes you super user/root.  That let's you edit system files.  So be careful.  To restore it from the command line you reverse it:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

```
We need to look at your current xorg.conf, so:
```
gedit /etc/X11/xorg.conf
```
Gedit is what Ubuntu calls Text Editor or gnome editor.
To actually edit it (which we don't want to do yet) you enter in a terminal:
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Naranwien on 2009-11-03
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "fi"
    Option        "XkbVariant"    "classic"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
    Load        "glx"
EndSection

***

That's what came up when i entered that "gedit /etc/X11/xorg.conf" into the terminal. It's like chinese to me. I have this feeling I am doing something wrong all the time, but I don't know what. <sobs>

Okay, my pen has 2 buttons. But I've never used them.

I went into that Synaptic thingy and installed that other thing in the list that didn't have the green square in front of it. Is that what you meant? xD

---

### Post by Favux on 2009-11-03
Hi Naranwien,

Happens to all of us.  Information overload.  Maybe we should knock off for the night and let you digest it all.  I can post the changes you need for the xorg.conf tomorrow.  I'm worried if we rush you you'll goof somewhere.

What do you think?

---

### Post by Naranwien on 2009-11-03
Yes. Sounds very good. I have to rush to class now also. Thank you so much for your patience. I am afraid I will make you bald after this event. Haha
I have entered into a competition (graphical) and I think I will have to pull out because I can't see my wacom tablet working in time for me to create and submit my project before Sunday midnight (est or something, american time, I'm in Finland)

---

### Post by Favux on 2009-11-03
Hi Naranwien,

I think we should have it working tomorrow.

Just answer these questions:
-how many buttons on the stylus?
-does the tablet come with a Wacom mouse (puck)?
-are there buttons on the tablet?

Once you answer I can have the xorg.conf ready.

---

### Post by Naranwien on 2009-11-03
> **Favux said:**
> Hi Naranwien,

I think we should have it working tomorrow.

Just answer these questions:
-how many buttons on the stylus?
-does the tablet come with a Wacom mouse (puck)?
-are there buttons on the tablet?

Once you answer I can have the xorg.conf ready.


The stylus has 2 buttons on it. One little one and one bigger one (longer more accurately)

There's no mouse, just the stylus.

There are two buttons on the tablet and one "scroller". I never knew until now, haha. Nothing happens when I push those buttons, only the "scroller" works. (screen scrolls up and down)

This is what it looks like [http://upload.wikimedia.org/wikipedia/commons/5/5f/Wacom_Graphire4_tablet.jpg](http://upload.wikimedia.org/wikipedia/commons/5/5f/Wacom_Graphire4_tablet.jpg)

---

### Post by Favux on 2009-11-03
Hi Naranwien,

Great, that's the information I needed.  I added the Wacom sections to your xorg.conf.  This should work.  This time you need to use the gksudo edit line.  gksudo is used for graphical programs like gedit rather than sudo.  You can copy and paste the whole thing or just add the changes.  Don't forget the entries in "ServerLayout"!  Just click on the attached xorg.conf to download it.

I noticed your "ServerLayout" lacks the mouse and keyboard entries.  But since it seems to working for you I decided to leave that alone.  Then to set up the tablet for Gimp you need to configure it's extended input devices as in the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").  Instuctions are near the bottom.  I think someone already gave you the link.

To use wacomcpl see "Section 3: Calibrating your Tablet" on this [HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").

Good luck!

---

### Post by Naranwien on 2009-11-04
Whoop! I copy pasted that text you gave me, and already my tablet is working! It's only the pressure sensitivity that's not. But I will follow the rest of your instructions and see what happens. Thank you SO much for your help. :D

---

### Post by Favux on 2009-11-04
Hi Naranwien,

Outstanding!  Nice work.  You're welcome.

Look how much you've learned already.  I bet you get pressure working too.

---

### Post by Naranwien on 2009-11-04
<cheers>

It's all working perfectly now, got the pressure thingy working! Again a BIG thanks!

Now, just a last question:
If I want to upgrade to Ubuntu 9.10 Can I use the same text or does it need to be modified yet again for 9.10? Not that I am planning on doing anything just yet, since I think it's too much for me to take in, being new to Linux and all that :D Right now I am just happy I can draw again, and since I don't feel I am lacking anything or have come across anything that bugs me too much so far (besides the wacom thing which is fixed now)
I would like to be able to run IMVU as well, but I tried it, and it crashes after like 30 seconds, plus it seems to be some problem with the graphics cause the avatar is really tiny, haha. But, one thing at a time. Thanks again. =D>

---

### Post by ranch hand on 2009-11-04
I would not recommend going to 9.10 until they had more experience than you have now.  It is a great release but it still has some problems.

9.04 is very stable and wacom is supposed to work real well there (I am on 9.04 right now).

If your box is working leave it alone and learn to use Ubuntu before messing with it.

I have no idea what IMVU is, but a quick search convinced me that I am too old to get into it.

---

### Post by Favux on 2009-11-04
Hi Naranwien,

I think ranch hand is right.  First learn some more about Ubuntu.  Intrepid (8.10) still uses the xorg.conf for Wacom.  When you go to Jaunty (9.04) you change to using the 10-wacom.fdi instead of xorg.conf for Wacom stuff.  So how you set up changes quite a bit.  You could still use the xorg.conf, but it's touchier.  And the same is true of Karmic (9.10).

The improvements in Gimp and linuxwacom are probably not worth the trouble to you right now.

---

### Post by Naranwien on 2009-11-05
Sounds good to me. I'm very happy with what I have now, happier than I was with Windows :) 
I remember when I switched from using adobe photoshop to Gimp. I got frustrated all the time, and many times I just wanted to switch back to adobe because I knew my way around it. But I stuck with it and now there's no way I would switch back to adobe. So what I am thinking is that I will get the same feeling about Linux once I get the hang of things. :D

And yeah, IMVU is not everyones cup of tea. I just like to take screenshots of my avatars and use for bases when I draw, so a bit sad that I can't get it working, but, my husband has windows on his comp stil (he's showing alot of interest in Ubuntu however, he thinks it looks awesome), so I can go on his comp and take screenshots of what i want in IMVU then send them to my e-mail. So not something I'm gonna start working up a sweat about if I can't get it working on Ubuntu.

Ohh, I just came to think of something. Not a big deal, but I was gonna watch a filmclip last night, I downloaded it, it's made with windows movie maker, it played in Totem Movie Player that came with Ubuntu 8.04, but it was acting like there was lag and there was no sound. I downloaded codecs and updates, but it still didn't work. What could have been the problem there?

---

### Post by ranch hand on 2009-11-05
You open a new thread for that problem.  That way each thread is one problem and easier for folks to  search for when they need a solution.

A discriptive title helps too.

You might want a different player.

---

