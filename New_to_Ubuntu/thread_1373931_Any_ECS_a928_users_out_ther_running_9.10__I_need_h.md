---
title: "Any ECS a928 users out ther running 9.10?  I need help, total Ubuntu noob."
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Mixam on 2010-01-06
Hello everyone,

I just started using Ubuntu 9.10 on my old ECS I-Buddie 4 A928.  I was actually surprised that everything seemed to install quite well to get the computer up and running without me having to find any drivers.  I just booted up today, so there might be some things missing still.  The first couple things that I'm noticing might be a bit of a problem are:

1) looks like 2 of the usb ports aren't working (the back two)
2) closing the lid does not put the system to sleep/hibernate/suspend.  I've gone into system/preferences/power management to set it up, it just did not work.  I went to the top right corner and put the system in to suspend or hibernate and that worked so I'm looking at either a) Ubuntu can't detect the lid being closed on this model or b) the sensor is broken.

Well those are the two problems I have for now.  I'm hoping there is an uber Ubuntu guy out there who is using this same system with 9.10 who can confirm for me whether these are problems with Ubuntu itself, something I have to enable somehow through added software or that it should be working and thus my system is broken.  I could really use the lid/sleep functionality as I have a cat now and I don't want him jamming on the keyboard all the time, so leaving it open and on isn't really an option.

Thanks for your help,
Mixam

---

### Post by Fika on 2010-01-06
1. Did you look under system > administration > disk utility? Should show the usb drives there.

2. Not sure about that.

---

### Post by Mixam on 2010-01-06
> **Fika said:**
> 1. Did you look under system > administration > disk utility? Should show the usb drives there.

Um it's the usb ports that aren't working, not a usb drive...  I do have a usb drive but it is not hooked up right now.  I tried plugging my usb mouse into the back two usb ports and neither worked.  The front two both do work.  So I have no idea why checking out what drives are connected to the system is going to do to help?

---

### Post by tmshih on 2010-02-16
Have you tried running Ubuntu or other distro's off of a Live CD to check if the USB ports still work? I now on my A928 the BIOS has trouble booting off of USB keys.

I actually run Xubuntu 9.10 on my ECS A928, but it's a bit buggy compared to 9.04. Most of the bugs involve stalls during booting. 

The ECS A928 tends to generate more heat than other systems so I don't bother with suspend or hibernate. There are broad range of systems that have problems with suspend/hibernate so you might want to search and see what they say.

---

### Post by Mixam on 2010-02-17
> **tmshih said:**
> Have you tried running Ubuntu or other distro's off of a Live CD to check if the USB ports still work? I now on my A928 the BIOS has trouble booting off of USB keys.

I actually run Xubuntu 9.10 on my ECS A928, but it's a bit buggy compared to 9.04. Most of the bugs involve stalls during booting. 

The ECS A928 tends to generate more heat than other systems so I don't bother with suspend or hibernate. There are broad range of systems that have problems with suspend/hibernate so you might want to search and see what they say.

I don't know how or why, but the usb ports just started working all of a sudden a little while back.  Maybe it was one of the automatic updates?  As for the lid sensor, it was broken.  The little rubber piece that sticks out somehow got bent back and was stuck under the lid.  So I took off the plate just below the lcd and fiddled around till I managed to get it back out.  I now have it set up to do whichever of the suspend/hibernate that actually saves everything to the hdd then shuts off.  The one that suspsended to ram was pretty useless as I don't think a desktop chip can be turned into low power mode, so the screen went off, but the computer still kept on running.

The one I have it set to now is practically like shutting the computer down, and takes about as long to boot back up after opening the lid.  But at least all my programs are open and as I left them.  The only problem I have had with using this method is that sometimes after waking back up the sound no longer works.  I have to restart to get the sound working again.  I have no idea why, but I rarely use sound anyways, so this method works for me.

So my original problems have been solved but I was hoping I could ask you some quick questions since you are running a similar OS.  I forget what the difference is, but I think it has to do with kde/gnome.  I'm running a p4 1.8A with 512Mb of ram for reference.  Anyways, my questions:

1) Any ideas on why the sound won't work after the computer wakes up again?
2) How is your video performance?  I don't remember it being quite so bad when I had it running windows xp a long time ago.  For instance my youtube videos stutter alot and google street view takes forever to load.  It might just be a driver issue, maybe I need to use a different driver?
3) How much ram are you using?  I saw a site online that said you could use 1Gb if it was the right ram, but I remember when it came out the box said it could only take up to 512Mb.  Perhaps my video issue is simply not enough ram to run Ubuntu and video at the same time, especially since 64Mb goes to the integrated video.

Aside from the video and sound issues, the system runs great on Ubuntu.  I can open a lot of tabs in Firefox and it barely slows it down.  Open office takes a bit to start up, but once it's open it works great.  I can't wait to try out Crome on Ubuntu, I was using it as my browser on XP and I heard it is in beta for Linux now.  Its a shame I'm moving into a studio apartment in a few months, I'll have to buy a new laptop because I won't have the space to set up a permanent location for the desknote, and as it does not have a batter or wireless internet, every time I wanted to use it I would have to plug in a cat 5 cord and the power.  The desknote was supposed to tide me over untill we had a place with room for a new desktop, but we opted to get a bigger yard and a smaller place and now I do not have the room for either a desktop or the desknote (unless I want to be setting it up every time I want to use it.  It's a shame I'll have to pay for windows 7 in my new laptop since I can't find a good one at a good price without windows on it.  I'm currently looking at the 17.3" i3 or i5 model Acer/Gateway laptops with or without discrete video card (depending on the price).

---

