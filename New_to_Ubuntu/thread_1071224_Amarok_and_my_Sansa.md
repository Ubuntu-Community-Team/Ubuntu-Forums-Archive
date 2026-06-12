---
title: "Amarok and my Sansa"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by turinturambar on 2009-02-15
So here I am with Amarok and a Sansa e270.  How do I get them to talk to each other?

It seems like I should go to the Devices tab in Amarok and click Connect.  If that's how to do it, what command do I type in?  I tried

mount /media/Sansa e270

but nothing happened when I clicked ok.

Does anyone know how to make Sansa and Amarok play nicely together?

Thanks in advance

---

### Post by SunnyRabbiera on 2009-02-15
Hmm, can you just use the sansa like a regular external drive?
You should not need amarok to manage music on a device like that.

---

### Post by turinturambar on 2009-02-15
Ah.  *slapping myself*  I COULD just drag and drop, couldn't I...

How barbaric...:)

I was hoping there was a way to do it within Amarok, like syncing in Windows Media Player, but if no one else can help me I may have to settle for dragging and dropping.  Thanks!

---

### Post by SunnyRabbiera on 2009-02-15
Well there isnt anything wrong with drag and drop, its old fashioned to some yes but I still use it.
I guess I am old fashioned though :D

---

### Post by Allochtoon on 2009-03-09
> **turinturambar said:**
> Ah.  *slapping myself*  I COULD just drag and drop, couldn't I...

How barbaric...:)

I was hoping there was a way to do it within Amarok, like syncing in Windows Media Player, but if no one else can help me I may have to settle for dragging and dropping.  Thanks!

I am looking for a solution to this.

I can automount my nokia 3110 classic without a problem in 'data storage' mode (microsd). I can drag n drop multiple tracks from my playlist in Amarok to my device via Dolphin. 

However, this results in Buffer I/O Error  lost page write. 

If i drag n drop 1 song at a time, it works without a problem. U can imagine this isn't a solution. Can the drag n drop of multiple tracks be modified in the amarok preferences & settings with a certain pause between tracks, so it mimics just copying 1 track at a time?

I dont give a crap about covers id3 tags and such, i just want to copy a playlist from amarok to my phone just in 1 folder.

---

### Post by Light Engine on 2009-03-11
> **turinturambar said:**
> Ah.  *slapping myself*  I COULD just drag and drop, couldn't I...

How barbaric...:)

I always like a more... hands on approach :D . Who needs all these slick sync applications anyway? You use Linux for a reason: Because you like playing around in file hierarchies, that's why. Don't you ever forget it :P 

In all seriousness, syncing with Amarok would be nice, but I'm so excited about my new Fuze that I don't feel like figuring it out.

I got a lot of invalid file names- I'm guessing I'll have to change a few album/song titles.

---

### Post by nanotube on 2009-03-18
> **Allochtoon said:**
> I am looking for a solution to this.

I can automount my nokia 3110 classic without a problem in 'data storage' mode (microsd). I can drag n drop multiple tracks from my playlist in Amarok to my device via Dolphin. 

However, this results in Buffer I/O Error  lost page write. 

If i drag n drop 1 song at a time, it works without a problem. U can imagine this isn't a solution. Can the drag n drop of multiple tracks be modified in the amarok preferences & settings with a certain pause between tracks, so it mimics just copying 1 track at a time?

I dont give a crap about covers id3 tags and such, i just want to copy a playlist from amarok to my phone just in 1 folder.

try using "cp" from the cli.

---

### Post by meperry64 on 2009-04-06
Yes, drag and drop works just fine - but the problem is I end up with ~5 out of 6GBs of music on the Sansa that is Unknown Artist/Unknown Album. 

This is all content I've ripped in Ubuntu 8.10 in Juicer or (2-3 albums) downloaded from Amazon.  

The same songs are recognized/ordered by artist & album under (PC) iTunes for my iPod, and Banshee also sees correct artist/album - although can't do anything with the Sansa due to the whole read-only permissions mess.

So just want to make sure I figure out a way to manage the Sansa using this same (non-PC/Mac) ripped content.

Thanks for any further suggestions.
Mp

---

### Post by dr.silly on 2009-04-06
The problem is with the tagging in your music files sansas are kind of picky about what version of the ID tagging you use. see [http://www.anythingbutipod.com/archives/2008/11/id3-tag-basics.php](http://www.anythingbutipod.com/archives/2008/11/id3-tag-basics.php) There are plenty of tools to retag your music ex easytag btw sound juicer rips in an outdated verson of ID tag

As for amarok compatability go

Settings -> Configure Amarok
then to media device tab
click add device select do not handle for the plugin
give whatever name you like
then find the folder where the sansa mounts when you plug it in, ex /media/SANSA\ E270 and enter that as you mount point
voila you can change folder format and stuff in the device configuration

---

### Post by meperry64 on 2009-04-06
Thanks for the suggestions.

Yes, understood I could re-tag the music but - even if Juicer tagging is outdated - everything else can read/sort on it except the Sansa.

In the interim I've config'd the Sansa w/Rockbox and the sorting issue is now solved.

Problem is - and as before - I still can't get Amarok to recognize this thing. The only challenge this poses is with playlist creation & editing (on-the-Sansa creation/editing in Rockbox is ridiculous, or I can manually create them in a text editor - whee!), so will keep looking.

Thanks again for your time & help with this.
Mp

---

### Post by Trent T on 2009-07-04
Hi all--
I have a Sansa E200P, and recently got it to talk to Amarok in Hardy Heron 8.0.4, thanks to this posting about Amarok and Ipods on another forum;

[http://www.linuxforums.org/forum/ubuntu-help/90452-how-configure-ipod-amarok.html](http://www.linuxforums.org/forum/ubuntu-help/90452-how-configure-ipod-amarok.html)

Here are the steps, modified for my Sansa E200P;
[B]
1) Connect your Sansa Player in MSC Mode--[/B]
   (Makes the Sansa look like a flash drive)
-- With Sansa player turned off, hold the rewind button in [<<] and plug your Sansa player into USB.  You will eventually get an icon on the desktop with its name.  A directory listing may also pop up.
[B]
2) Identify your Sansa Player to Linux;[/B]
-- Open a console window with bash prompt.
-- from console, **run df -h**
   This will list devices on the system.  One of them will be your Sansa;
   The pathway to mine is **/media/SANSA_E200P**
   Note the underline character in the Sansa player's name.
-- Go back to the desktop.
-- Right click on the desktop icon for your Sansa player.
-- Click Properties
-- Click Volume
-- In the Mount Point box, enter the name of your device exactly as your 
   system described it.  My player is **SANSA_E200P**
 -- Save and Close.
[B]
3) Identify your Player within Amarok[/B]
-- Launch Amarok
-- Go to Settings--> Configure Amarok --> Media Devices
-- Try clicking the [Autodetect] button.  
   It didn't work for me, but you never know...
-- When Autodetect fails, click on [Add Device]
-- Select Generic Audio Player
-- Enter the device name (anything, like My Kewl Sansa)
-- Enter the mount point.  Mine is /media/SANSA_E200P
-- Click [OK] to leave the configuration menu.  

**4) Launch your Sansa from within Amarok**
-- Go to the Amarok main menu.
-- The bottom tab on the left side is Media Devices. 
   Click it and select [Connect]
-- Amarok should pop up, allowing you to play from Sansa, 
   and move things around.

Best of luck,
Trent T

Disclaimer/Credits;

The information in this post was almost entirely copied from postings by Rudykong, here;
 
[http://www.linuxforums.org/forum/ubuntu-help/90452-how-configure-ipod-amarok.html](http://www.linuxforums.org/forum/ubuntu-help/90452-how-configure-ipod-amarok.html)

and ThunderUnderKilt, here;
[http://www.anythingbutipod.com/forum/showthread.php?t=24570](http://www.anythingbutipod.com/forum/showthread.php?t=24570)

---

