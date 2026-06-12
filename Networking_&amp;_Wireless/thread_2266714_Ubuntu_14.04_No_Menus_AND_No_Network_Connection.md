---
title: "Ubuntu 14.04 No Menus AND No Network Connection"
date: 2015-02-24
forum: Networking &amp; Wireless
---

### Post by TeeJaye on 2015-02-24
I'm having 2 issues simultaneously.  I did a quick search for solutions, but all of the fixes to one problem seem to assume the other doesn't exist!

Problem 1 - when I boot to Ubuntu I get only the desktop background.  No menus or other GUI elements
Problem 2 - Ubuntu can't seem to see my network connection (hardwired), so it can't download any packages to address Problem 1.  Network and Internet work fine in Windows (dual-booting)

Apologies if a solution actually is already kicking around here somewhere, and I just didn't search thoroughly enough.

Hope you folks can help!

[EDIT] MORE DETAILS

Ubuntu 14.04

router ping returns "connect: Network is unreachable".

Almost brand new install.  Logged in successfully once after installation.  GUI and Network worked.  Installed Steam.  Logged off.  On next boot, encountered these problems.

I am brand new to Linux (if that wasn't obvious already)

---

### Post by TheFu on 2015-02-25
Please post the exact output (copy/paste) of all commands. Don't want to misinterpret stuff, right?
Also, please use "code tags" so things line up and are easier to read.

Best to ask 1 question at a time.
Problem 1:  Before login, click the "gear", select "Unity", then login as normal.

That should get you into the main system, as installed.  I've never used steam.

[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) - has links to learn Linux in a directed way - not through google where the lack of background is a major problem.

---

### Post by TeeJaye on 2015-02-25
Thanks for the reply.

Let me follow up with a *very *stupid question:  How can I copy/paste output to a website when the machine generating the output isn't connected to the internet?  Am I stuck typing everything out by hand, or is there an easy solution I'm not thinking of?

I'll switch to code tags, and provide some more output once I'm back at my machine tonight.  You'll probably have to point me towards some commands to input, though.

Problem 1:  I don't even have a gear to click.  As soon as I boot to Ubuntu, all I get is a desktop background.  As far as I can tell there is no way to interact with the GUI (including logging in).  If I Ctrl-Alt-F1 out to the command prompt I can log in that way and enter commands, but that seems to be about it.

Thanks for the link; I will definitely check it out, as I agree that google is not a perfect tool for learning a new OS from scratch :)

---

### Post by TheFu on 2015-02-25
Before you try anything below - have you tried mouse chords on the desktop?  left button, right button, middle button, LM, LR, MR and LMR all together?  May need to hold the chord for 5 sec for the any menu to be displayed.  Also, try alt-F2, see of a run cmd dialog comes up.  Then you can run any program you like - try **xterm -sb**.

> **TeeJaye said:**
> Let me follow up with a *very *stupid question:  How can I copy/paste output to a website when the machine generating the output isn't connected to the internet?  Am I stuck typing everything out by hand, or is there an easy solution I'm not thinking of?

Redirect to a file?  This is a common technique used on Unix-like systems.  Or just copy/paste into a text file and use a flash drive/floppy/usb storage to move it to another device. Old school "sneaker net."

Don't type it all.  That isn't likely to be 100% accurate and that is what we are after.

> **TeeJaye said:**
> I'll switch to code tags, and provide some more output once I'm back at my machine tonight.  You'll probably have to point me towards some commands to input, though.
  Adv Reply.

> **TeeJaye said:**
> 
Problem 1:  I don't even have a gear to click.  As soon as I boot to Ubuntu, all I get is a desktop background.  As far as I can tell there is no way to interact with the GUI (including logging in).  If I Ctrl-Alt-F1 out to the command prompt I can log in that way and enter commands, but that seems to be about it.
Ah - you chose auto-login. I've never used that. Sorry. There is a way to turn it off - don't know it off the top of my head. Sorry. IMHO, auto-login is a bad, bad, bad idea.

> **TeeJaye said:**
> 
Thanks for the link; I will definitely check it out, as I agree that google is not a perfect tool for learning a new OS from scratch :)

Google doesn't know background, so the answers are all about 6-12 months advanced beyond what someone new to Unix systems can understand. Sometimes the results are very out-of-date or were written by a noob who didn't understand subtle differences in systems. Sometimes the specifics have changed, so doing what those random websites say is not correct anymore.  For example, in 12.04 and later, DNS is handled differently than how it was handle the prior 20+ yrs. Things change sometimes.

All those years ago when I was learning, we didn't have forums and my peers in the lab would just say RTFM. They taught me how to research answers for myself by being mean, but after a few months, I became expert at finding answers on my own.  The local manpages are awesome and correct for your system. Google doesn't always/usually return the info for the exact version of a program that is on your system. Usually, it is close enough, but not always.

Searching for help on a Linux commands:
* whatis {topic} - **whatis firefox**
* man -k {topic}  - same as apropos {topic}  - **man -k browser**
Then use **man firefox** to learn more details.

---

### Post by TeeJaye on 2015-02-25
Wow, thank you for your patience.  I appreciate the detailed response.

> [COLOR=#000000]Before you try anything below - have you tried mouse chords on the desktop? left button, right button, middle button, LM, LR, MR and LMR all together? May need to hold the chord for 5 sec for the any menu to be displayed. Also, try alt-F2, see of a run cmd dialog comes up. Then you can run any program you like - try [/COLOR]**xterm -sb.**

I have not tried chords.  Will be my first step tonight.

> [COLOR=#000000]Redirect to a file? This is a common technique used on Unix-like systems. Or just copy/paste into a text file and use a flash drive/floppy/usb storage to move it to another device. Old school "sneaker net."[/COLOR]

Sounds like a pretty good excuse to learn/practice some basic commands (file transfers and whatnot).

> [COLOR=#000000]Adv Reply.[/COLOR]

Haha sorry, looks like I was unclear right in the middle of a conversation about the importance of clarity.  When I said I might need help with commands, I meant commands to be entered into Linux to help diagnose my issues, not forum commands.  Thanks nonetheless :)  Adv reply is certainly handy.

> [COLOR=#000000]Ah - you chose auto-login. I've never used that. Sorry. There is a way to turn it off - don't know it off the top of my head. Sorry. IMHO, auto-login is a bad, bad, bad idea.[/COLOR]

Hmmm...doesn't sound like something I would have done intentionally, but that certainly doesn't mean I didn't do it!  I'll do some research on how to reverse that decision.



Thanks again for the detailed response.  I'll get reading and be back with some fresh screwups once I'm back on my computer this evening.
(and thanks for not being as mean as your lab-mates.  I swear I'll eventually learn to become self-sufficient anyway :) )

---

### Post by TheFu on 2015-02-25
> **TeeJaye said:**
> Wow, thank you for your patience.  I appreciate the detailed response.
...
(and thanks for not being as mean as your lab-mates.  I swear I'll eventually learn to become self-sufficient anyway :) )

Sorry - *internet words* didn't come out correctly.  You're doing just fine. I didn't mean to imply you weren't. I apologize.

If a login screen isn't being displayed and autologin isn't setup ... not good. I've never been in that situation myself. Best to wait an see what the truth is first.

---

### Post by TeeJaye on 2015-02-25
No need to apologize!  I was just marveling at how helpful you were being.  I wasn't taking any offense :)

So I've made a tiny bit of progress, but I don't feel much closer to success.

I tried some mouse chords.  No luck with any except for possibly the simplest of all:  Right-click.

After some messing around I discovered that the "Change Desktop Background" option in the right-click menu gets me to a place where I can navigate to "All Settings".

So I now have access to some settings.  Naturally, I gravitated to "Network" first, and now I am even more confused.  I have two options in the Network settings window.  "Wired" and "Network Proxy".  I assume Wired is where I should be.  Here's the thing:  Right at the top of that screen it says "cable unplugged".  I know that is not true, because the cable is most certainly there.  And I know the computer is capable of recognizing that the cable is there, because if I restart and boot to Windows, it works perfectly (tried this several times to be sure it wasn't a fluke).

As you may have noticed, I'm focusing on the Network problem, which is the opposite of what you suggested.  The reason being that I've been floating around the forums and it looks like the no-menus problem is pretty common with lots of potential solutions.  Unfortunately, they all seem to require downloading/updating/installing packages from the internet.  So it seems that getting my network up and running is the more pressing need.

Soooooooo....long question short:  where do I start on diagnosing a "cable unplugged" situation?  A quick browse for network connection issues turns up lots of wireless problems, and lots of "I can see the network, but not the internet", but I don't see a lot of "ubuntu thinks there's no cable plugged in"

Side note:  While fumbling around in the newfound settings menu, I was able to disable auto-login.  So at least there's that :)

---

### Post by TeeJaye on 2015-02-25
Total shift in direction now.  On a whim, I tried plugging an old wifi dongle into my comp.  It works!  So although ubuntu can't see the network wired, it can see it wirelessly.

So, for the moment, back to the invisible desktop problem.

---

### Post by TheFu on 2015-02-26
Ah - so you did have autologin enabled?
Did you click the "gear" and choose a different GUI before logging in? Did that solve this?

I can try to help with the wired ethernet thing - that is actually why I decided to try and help.  I don't run much GUI - or a desktop - so when you say what you clicked on, that means ZERO to me.  I haven't seen the normal ubuntu GUI in about 3 years.  However, you'll need to get a terminal opened for me to help.  Also, it would be easier if you could enable/install openssh-server then connect from a different machine so the GUI stuff isn't an issue as we troubleshoot.

---

### Post by TeeJaye on 2015-02-26
So after trying a bunch of GUI solutions, I did more damage than good so I eventually broke down and just did a fresh Ubuntu install.  During the course of the re-install, I saw the very enticing "enable auto-login" option, and can definitely believe that I was silly enough to click it the first time.  GUI issue seems to be resolved by the re-install (at least for now), but the network issue is still there. Sounds like that's the perfect state to be in if that's your area of expertise :)

On the network front, my status is still the same as it was prior to re-install:  

Wired network: Ubuntu thinks there is no cable plugged in (says "Cable Unplugged" via GUI, and pinging router from the command line says network unreachable).  Cable is not unplugged (works fine if I reboot to Windows).
Wireless network:  Ubuntu auto-recognized the dongle I plugged in, and I've got a good connection to network and internet.

I can get to the terminal, so that's working in our favor.

---

### Post by TheFu on 2015-02-26
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has troubleshooting steps.  I suspect an incompatible NIC. Run the commands, post the cmd and output back here. Please use "code tags" so things line up.

---

### Post by TeeJaye on 2015-02-26
Perfect, thanks.  I'll do this first thing tonight.

---

### Post by TeeJaye on 2015-02-26
-

---

### Post by TeeJaye on 2015-02-26
-

---

