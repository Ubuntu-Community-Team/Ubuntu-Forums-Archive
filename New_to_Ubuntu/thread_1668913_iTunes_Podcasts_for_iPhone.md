---
title: "iTunes Podcasts for iPhone"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by tonycm1 on 2011-01-16
I have a dual boot system with Windows XP and Ubuntu 10.04

I'm trying to ween myself off windows and was wondering if there was a way I can still get all my subscribed podcasts to sync with my iPhone in Ubuntu.

I've heard of a few solutions in Rhythmbox but none seem to access the iTunes store for content.

I also tried installing iTunes through Wine but that didn't work :(

Ideas?

---

### Post by robsoles on 2011-01-17
To access Apple's more recent devices from your Ubuntu OS you will be needing a Virtual Machine (I use and recommend closed source edition of [www.virtualbox.org]("http://www.virtualbox.org")), in which you need to run either MS Windows or a fairly recent release of MAC OS X.

As you know(?), itunes will be quite happy to run there.

Apple retain a great deal of rights over their recent products, their EULA contains jargon and specifics that (in my opinion) boil down to: Don't try to read/write/manage our devices with 3rd party software unless it is endorsed and licensed by us. Don't try to reverse engineer the device to provide a 3rd party 'solution' for the device. We sold you the device, the reason it goes belongs to us and we reserve the right to withdraw it's usage from you on practically any ground at any time.

Sorry, with a bit of luck my post will attract somebody with better (at least nicer/more hopeful perhaps ;)) advice :)

---

### Post by PhillyKingston on 2011-01-19
I have installed the latest Virtualbox (4.0.0 r69151) PUEL installed, for the USB support, on Ubuntu 10.10 64-bit with a Windows 7 64-bit VM.  I installed iTunes on the VM and seem to have everything working perfectly, but when I sync my iPod the podcasts will skip or glitch on the iPod.  The downloaded items appear to be fine when I listen to them in the VM through iTunes.  I am curious if anyone else is having problems with this, and has any thoughts on what I can do to stop the skips from occuring?

---

### Post by PhillyKingston on 2011-01-19
x

---

### Post by robsoles on 2011-01-20
> **PhillyKingston said:**
> I have installed the latest Virtualbox (4.0.0 r69151) PUEL installed, for the USB support, on Ubuntu 10.10 64-bit with a Windows 7 64-bit VM.  I installed iTunes on the VM and seem to have everything working perfectly, but when I sync my iPod the podcasts will skip or glitch on the iPod.  The downloaded items appear to be fine when I listen to them in the VM through iTunes.  I am curious if anyone else is having problems with this, and has any thoughts on what I can do to stop the skips from occuring?

(1) Have you set a USB filter referring to the ipod in the VM's USB list? If so, are you keeping system focus on the running VM as you plug the ipod in to manage using itunes in the VM?


(2) Does your ipod mount any file-space, visible to Ubuntu, when you plug it in to access in your VM? Have a look using "System"->"Administration"->"Disk Utility" and if you find any reference to the ipod in there, see if it offers you to unmount it - if you find something to unmount then unmount it and try transferring from your VM to the ipod again.


If it is a mis-write to the ipod, as I suspect (plays fine in VM, skips/skippy on ipod), then itunes should be *good enough* to report communication failures - if it is any form of communication failure I expect that something from the host operating system is trying to access something about the ipod while the VM should have sole control.

---

### Post by Paqman on 2011-01-20
It might be easier just to copy all your podcasts into Google Reader and just use that on your phone. Cut Itunes out of the loop.

---

### Post by PhillyKingston on 2011-01-21
robsoles: I have set the USB filter to refer to my iPod, but I did not maintain focus on the VM while I was sync'ing the iPod with iTunes.  Is maintaining focus on the VM really nessecary?
 
The iPod does appear mounted in ubuntu when I just connect it, without the VM running.  I believe that the mount is not visible when I have VBox running, but I can double check that.
 
I am assuming it is a mis-write to the iPod as well.  Just not sure why that is occuring.  I read something elsewhere that indicated there might be a problem reading from an external USB HDD, when mounting the directory as a shared directory in the VM and then syncing to the iPod.  I am going to try moving my iTunes podcasts to a local HDD this weekend and see if I am having the same issues.  Does that sound possible, it doesn't make much sense to me?
 
Paqman:  It isn't a phone, it is an iPod only.  I probably should have put this in it's own thread, sorry.
 
Thanks for the ideas.

---

### Post by robsoles on 2011-01-21
> **PhillyKingston said:**
> robsoles: I have set the USB filter to refer to my iPod, but I did not maintain focus on the VM while I was sync'ing the iPod with iTunes.  Is maintaining focus on the VM really nessecary?

I got the impression, once at least, that if a VirtualBox VM with a device specific USB filter was focussed while the specified USB device was plugged in then it didn't mount in the Host and the VM had uninterrupted control of the device - can't seem to prove it right now though!

I expect once the VM has full control of the device you should be able to minimise the VM and go play with anything you like (don't unplug ipod without checking itunes is finished whatever you've started) and be able to expect the synced files to play from the ipod without skipping or other problems.

> **PhillyKingston said:**
> The iPod does appear mounted in ubuntu when I just connect it, without the VM running.  I believe that the mount is not visible when I have VBox running, but I can double check that.

It's just a chance I see that the host OS may be interfering with the transfers from itunes to ipod if file-space off the ipod is mounted - I'd use 'Disk Utility' to unmount it so that it is only unmounted and not powered down in the expectation that VirtualBox can have exclusive control of the device like that.

> **PhillyKingston said:**
> I am assuming it is a mis-write to the iPod as well.  Just not sure why that is occuring.  I read something elsewhere that indicated there might be a problem reading from an external USB HDD, when mounting the directory as a shared directory in the VM and then syncing to the iPod.  I am going to try moving my iTunes podcasts to a local HDD this weekend and see if I am having the same issues.  Does that sound possible, it doesn't make much sense to me?
I don't think you are using the 'shared folders' function of VirtualBox by which to access your ipod so I don't think this is the avenue to go down but it's your situation and you can go down any avenue you can see to try to get what you want out of it.
> **PhillyKingston said:**
> 
 
Paqman:  It isn't a phone, it is an iPod only.  I probably should have put this in it's own thread, sorry.
 
Thanks for the ideas.

I think you chose a fine place to post your problem: I had just been a smart-alec, saying how you could do it with VirtualBox, and you seem to have a situation that suggests that it isn't tenable to do it that way.

---

### Post by PhillyKingston on 2011-01-25
Ahh, well I never seemed to have a problem having the iPod mount in to Win7 through VB.  I would expect the same regarding the focus once the iPod is in there.
 
I generally wait to plug in the iPod until the VM is up and running.  I was waiting till all the podcasts had updated before I plugged in the iPod and had iTunes sync.
 
I am definately not using the shared folders to access the iPod, I am using the shared folders to access my downloaded content.  I have the content on an external USB HDD.  I noticed that when I was syncing the iPod the sync would take an unusually long amount of time.
 
I got too annoyed with all the skips and restarts of the podcasts and copied off all the linux downloaded material for comparision and booted into windows 7, and updated my podcasts and synced again.  I compared the windows downloaded material and the VB Win7 downloaded material with an MD5 comparision tool and only 36 of the 89 podcasts were identical.  So it seems like there is a network issue with using VB iTunes for downloading material, and possibley an issue with the USB transfers.
 
I guess I'll just need to do the updates periodically with Win7 until I can figure out a linux better solution, unless someone else has some ideas.  Thanks for the help though.

---

### Post by BHEJU on 2011-01-25
The MD5 thing might be related to the file systems mismatch.
I have used VB in the past and I never had issues with adding audio/video tracks to ipod / iphones. (However, I do not use sync. I manually add them).
Currently I use vwmware workstation (and copy trans manager cause I hate itunes). It works fine as well.

As for linux alternatives check out this Wikipedia page:
the best tool from my exp is GTKpod (but still not up to satisfactory standards).
[http://en.wikipedia.org/wiki/Comparison_of_iPod_managers](http://en.wikipedia.org/wiki/Comparison_of_iPod_managers)

---

