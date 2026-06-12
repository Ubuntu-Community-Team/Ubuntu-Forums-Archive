---
title: "Wubi installer not running"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by Elsoreth on 2010-08-09
I am relatively new to linux, but for the last few weeks I have been working on getting myself used to Ubuntu (Lucid).  I used wubi to set it up under XP, and everything on that computer worked absolutely perfectly.  Now that I'm discovering I do things faster in Ubuntu than in XP, I feel it's time to get it working on my laptop.

However, it's not being as easy as it was for the first computer I set it up on.  My first attempt was to simply download Wubi, with the expectation that it would download ubuntu as it did on the first computer I set up.  This was not to be.  Instead, when I try to run the wubi exe in XP, the wubi process loads for a second or two before ending without doing anything visible. 

Searching through the forums, I have seen one or two others that have run into the same issue, but of the people I saw those that got Ubuntu operational set up a real partition, something I'd like to avoid for now.  

My second attempt at putting ubuntu on the laptop was to look through past wubi releases, to see if any would run.  Going backwards chronologically, the first that seemed to work was a release of 8.04.  With the idea that once in I could just upgrade, I ran that install.  The (wubi) install was unable to complete, my best assumption is that it ran into issues with my firewall.  But I thought, then, "This is good, I'll just make an 8.04 live cd and install from that."

Which worked, sort of.  The only problem was it took 20 minutes to load into ubuntu, I believe it was being held up while setting up swapping.  I figured I'd deal with that once updated, and began trying to set up the proper updates, only to find that even though the connection seemed to work out of the box, it was slower than it should have been.  I was downloading things at the lightning-fast speed of 400 B/s, with an estamated download time of 4 days before I had enough packages to update.  

So, the upshot is, does anyone know if there's a fix for the initial wubi not doing anything issue?  The next thing I plan to attempt is to try and update 8.04 to Lucid off of my live cd, but I really am curious about that first issue.  Also, if anyone has any ideas why accessing the internet with my Ubuntu 10.04 and Lubuntu 10 live disks is normal, while the install of 8.04 is so slow, I'd be interested.  (before someone asks, yes it sticks around after restarting, I tested even with the 20 minutes it took each time.)  

In case it will help, some of my computer information is as follows:
Thinkpad T42 laptop
Windows XP professional, version 2002 service pack 3

Network adapter is "Dual-Band Wi-Fi Wireless Mini PCI Adapter", from Atheros

(I can post more info if it'll help.)

I apologize for the longevity of my post, and the roundabout ways I've tried to deal with the problem.

---

### Post by garvinrick4 on 2010-08-09
**Upgrade from 8.04 LTS to  10.04 LTS**

 **Network  upgrade for Ubuntu desktops (Recommended)**

 You can  easily upgrade over the network with the following procedure.   
 
[LIST=1]
[*] Press Alt-F2 and type update-manager --devel-release  
[*] Click the **Check** button to check for  new  updates.  
[*] If there are any updates to install, use the **Install   Updates** button to install them, and press **Check** again after that is complete.  
[*]A  message will appear informing you of the availability of the new  release.  
[*] Click **Upgrade**.  
[*]Follow the on-screen instruction
[/LIST]

---

### Post by Elsoreth on 2010-08-09
> **garvinrick4 said:**
> **Upgrade from 8.04 LTS to  10.04 LTS**

 **Network  upgrade for Ubuntu desktops (Recommended)**

 You can  easily upgrade over the network with the following procedure.   
 
[LIST=1]
[*] Press Alt-F2 and type update-manager --devel-release  
[*] Click the **Check** button to check for  new  updates.  
[*] If there are any updates to install, use the **Install   Updates** button to install them, and press **Check** again after that is complete.  
[*]A  message will appear informing you of the availability of the new  release.  
[*] Click **Upgrade**.  
[*]Follow the on-screen instruction
[/LIST]

I knew about that, actually, the problem is that it would have taken four days to do it that way with my network oddities.

Edit: I'm sorry if that sounded gruff.  I know how to update, what I'd be really interested in is if anyone knows something about the wubi 10.04 not running in certain forms of xp.

---

### Post by bcbc on 2010-08-09
Look in the wubi log file to see why wubi.exe didn't work on 10.04: go to windows explorer, enter %temp% in the address bar and look for the wubi-10.04-revxxx.log file.

Try running it off the 10.04 CD.

---

### Post by Elsoreth on 2010-08-09
> **bcbc said:**
> Look in the wubi log file to see why wubi.exe didn't work on 10.04: go to windows explorer, enter %temp% in the address bar and look for the wubi-10.04-revxxx.log file.

Try running it off the 10.04 CD.

Running a search for all log files in the temp directory does not come up with a wubi-10.04 log, surprisingly.  I do, however, find the log file for the wubi-8.04 version that worked.  Also, there is a log file for a wubi-8.10 that must have been created during my search for usable wubi versions, but those are the only two.  Also in temp I find a huge number of "pyl" .tmp files with the wubi icon, I assume one for every time I attempted to run wubi.

The 10.04 cd wubi installer does the exact same thing the non-cd one does, start up a process and then close it without doing much else.  The live cd itself works...mostly.  Although I had thought I tested it before, when opening up the 10.04 live cd I get an "unrecoverable desktop error," right before starting up.  I did not see anything otherwise wrong with the boot.

---

### Post by bcbc on 2010-08-09
> **Elsoreth said:**
> Running a search for all log files in the temp directory does not come up with a wubi-10.04 log, surprisingly.  I do, however, find the log file for the wubi-8.04 version that worked.  Also, there is a log file for a wubi-8.10 that must have been created during my search for usable wubi versions, but those are the only two.  Also in temp I find a huge number of "pyl" .tmp files with the wubi icon, I assume one for every time I attempted to run wubi.

The 10.04 cd wubi installer does the exact same thing the non-cd one does, start up a process and then close it without doing much else.  The live cd itself works...mostly.  Although I had thought I tested it before, when opening up the 10.04 live cd I get an "unrecoverable desktop error," right before starting up.  I did not see anything otherwise wrong with the boot.

I just tried the wubi.exe version from [http://wubi-installer.org/](http://wubi-installer.org/) and it seems to work fine, mind you I'm not on my xp box.

---

### Post by Elsoreth on 2010-08-09
> **bcbc said:**
> I just tried the wubi.exe version from [http://wubi-installer.org/](http://wubi-installer.org/) and it seems to work fine, mind you I'm not on my xp box.

This is what I find strange, it worked perfectly as well for me on a different XP computer.  The only conclusion I can come up with is that there is some setting I have on one computer that interferes, but I know not what.

EDIT: I went back to make sure I'm not the only one.  [http://ubuntuforums.org/showthread.php?t=1137395](http://ubuntuforums.org/showthread.php?t=1137395)

---

### Post by bcbc on 2010-08-09
> **Elsoreth said:**
> This is what I find strange, it worked perfectly as well for me on a different XP computer.  The only conclusion I can come up with is that there is some setting I have on one computer that interferes, but I know not what.

EDIT: I went back to make sure I'm not the only one.  [http://ubuntuforums.org/showthread.php?t=1137395](http://ubuntuforums.org/showthread.php?t=1137395)

Did you uninstall the 8.04 version first? I wonder whether there's something incompatible between them.

I really have no idea what you could try to get around this.

---

### Post by Elsoreth on 2010-08-09
> **bcbc said:**
> Did you uninstall the 8.04 version first? I wonder whether there's something incompatible between them.

I really have no idea what you could try to get around this.

I did my best to uninstall it, that is I used the "add/remove software" manager.  I'm currently defragging that computer, as it's been several years, but I'm doubtful it will help with this particular issue.

Thank you for trying, though.  =|

---

