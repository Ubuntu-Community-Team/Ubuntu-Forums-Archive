---
title: "GDM issue in 10.10: bare desktop after login - fixed but little idea how/why"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by viipu on 2011-02-25
Two purposes for this post:

[LIST=1]
[*]To help anyone with a similar issue.
[*]Getting help with finding out what was wrong in the first place.
[/LIST]
[B]
The issue[/B]: after I had to force shutdown, on reboot only the bare desktop loaded up, with a functional cursor but no panels etc. [ALT]+[F2] wouldn't load up, couldn't get the Terminal going, and got no Recovery Console, however Virtual Console worked; running an update and install on Ubuntu Desktop did nothing though. (If you're looking for help, you get to Virtual Console by pressing [CTRL]+[ALT]+[F2] - or if that looks strange, try [F3]-[F6]; log in as prompted with your admin account. You should be able to return to your graphical interface with Ctrl+Alt+F7)

So I launched Firefox through a link; obviously everything WORKED, it just wasn't accessible. Also, logging in other users worked as normal, but unfortunately my main account was the only admin account. I've learnt my lesson now, backup accounts FTW :oops:


**The solution**: I didn't want to revert to the default desktop settings and lose my settings, if that could be avoided, so ended up with this command, run in Virtual Console, found [here]("http://ubuntuforums.org/showthread.php?t=1461537#10") (with massive thanks!):

> **lidex said:**
> 
```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```


**The babble:** What does that command actually do? Reverts the desktop to some sort of default setup, yes, but what default? I got my Desktop back exactly as it was before all this hassle, so I suppose it wasn't a problem with my settings but rather a bug with an app?

That is, all except for the (Evolution?) Clock/Calendar app work as before, but I suspect that app was somehow the reason behind it all; I'll report back on that if I figure it out. (It "unexpectedly quitted" or some such, and after trying to reload the system froze in the first place, and had to force shutdown)

Sorry if there's a lot of obvious and dumbed down stuff, but it wasn't obvious to me so I thought I'd put it all in. Also, didn't find anything exactly easily accessible regarding this issue, apologies if this is repetition. I know the joy is in finding, but when you don't really even know where to start looking...

Running Ubuntu 10.10 on an Acer Aspire One D255 Netbook, integrated Intel GMA 3150 - I know this might all boil down to the pish they call a Linux driver at Intel  :roll:


**The bottom line:** which logs/files/settings should I look at to see what went wrong, and how can I prevent this from happening in the future?

Cheers y'all!

---

### Post by acrazyplayer on 2011-02-26
the command you used did just what it looks like, it re-installed gdm "gnome desktop manager" 

dpkg stands for "debian package" so the second part was telling the computer to configure the application for your setup. 

I do not know where to look for these files or locations that hold your settings for your current desktop but I think most are located in "gconf-editor" you can get there by "alt+F2" and typing that in.

to find out quick things about commands just type in either "help" or "man" before the command depending on how much you want to learn about it. 

to exit "man" perss the "q" button

anymore questions than feel free to ask.

---

### Post by viipu on 2011-02-26
Cheers, yeah I figured it's a reinstall and reconfigure etc, hopeless wording on my part I suppose, what I meant is why did it fix my problem? Sheer luck? 

The way I understand it, either there was a problem with gdm itself, or the clock applet, or maybe both (or something else altogether). The only thing I can figure the reinstall actually visibly having done is disabling the clock applet from the panel settings. Why would reconfiguring gdm disable that? If it just reconfigured the package, with my original settings, how did it know to disable the offending app? Not saying I'm not happy it did, getting it back is the problem but I'll get there.


Point being, why? Why, why, WHY? Or should I just be happy it works and shut up?

Anyhow, thanks a lot. Here I was thinking dpkg means depackage. Not that that's really even a word.

---

### Post by acrazyplayer on 2011-02-27
While searching I found that gdm actually sands for gnome display manager :) anyway close enough. I also think why it worked out is because gdm contains in itself many things, its not just one file. so it may have overwritten whatever was messed up with your account but didn't overwrite the settings and then when you tried it all out it found that evolution add-on was your problem,and then removed it.

There are many things I don't know how the heck it works but I am very happy it does :D

---

### Post by MLawrence on 2011-05-27
well it didnt work for me.
im on a new ubuntu 10.04 install. 
HP-G60 notebook with a AMDTurion64bit. 
I came from using Linux Mint Julia, and decided to use Ubuntu since it had a bigger community. Installing ubuntu took hours compared to Mint. In anycase, I felt ubuntu would be a safer bet long-term. ive only been on a linux system for 4 days, and ive feel ive inadverently caused every possible problem. "everything that CAN go wrong, WILL."

when ubuntu was firsr installed, the first thing I did was set about customizing my desktop. 
I wanted to setup the cube desktop. I noticed that compiz was NOT already pre-installed. 

(I downloaded my appropriate os through torrent supplied by official ubuntu website)
I downloaded and installed compiz through the ubuntu software center. I went into the compiz config, and tuned everything I wanted for the desktop cube (disabling desktop wall etc.) but the settings just will not apply. I went to system>preferences and could find no option to turn on visual effects. I went into compiz config and NONE of the settings I selected were applied.

I assumed my nvidia graphics driver was the problem.

I went to system>administration>additional drivers and saw a choice of 2 (and only two) drivers:
"NVIDIA accelerated graphics driver (version 173)"
and
"NVIDIA accelerated graphics driver (version current) [Recommended]"

The 173 was already installed and running. So I decided to install and run the recommended.

When I rebooted, my panels were gone. alt+f2 did not bring up terminal. all I could do was right-click and create new folders, or change my desktop background.. 
Unlike viipu here, I didnt have the know how to activate firefox from terminal or virtual console, so im typing this entire message from my android phone. ill google running firefox from terminal.

Summary: In the process of trying to work compiz to work, ive lost control of my desktop I have tried the sudo command given by viipu here, to no avail. Every reboot, just brings a dead blank desktop. (thankfullu, alt+T brings up terminal).

---

