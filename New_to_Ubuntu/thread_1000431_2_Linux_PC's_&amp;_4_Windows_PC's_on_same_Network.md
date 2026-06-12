---
title: "2 Linux PC's &amp; 4 Windows PC's on same Network ?"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by gyrene2083 on 2008-12-02
Here is my setup on my network
4 XP Pro Boxes
1 Laptop Ubuntu Gnome Install 8.10 
1 HTPC Ubuntu Command Line Install 8.04 

I want to be able to share files from all the machines, how should I set up my network? I know SMB is for Linux -> Windows shares, and NFS is for Linux -> Linux boxes. So, do I setup SMB on all the PC's and NFS on the two Linux boxes? 

4 Xp Pro's - SMB?
2 Linux boxes - SMB and NFS?

Thanks for all the help.

---

### Post by Dj Melik on 2008-12-02
I think you got it :). Thats how my set up is.

---

### Post by gyrene2083 on 2008-12-02
Is there anything special I need to do to configure NFS?

---

### Post by Kellemora on 2008-12-03
Hi G and D

I'm watching this thread too!

I have 8 machines here, only 2 are Windows, 4 are Ubuntu, 1 is CentOS, the other is whatever I boot that day to test things on.

Using Samba for ALL of them.  The only problem we have is each upgrade that comes down the pike brings down the entire LAN and it takes anywhere from 8 to 24 hours to get it back up and running again.

Not good when you have 3 or 4 employee's on the clock with nothing to do but twiddle their thumbs for a day or more.  And I'm to old to be working from sunup until after midnight and some weekends.

Everything is configured by the book, and when it works, it works perfectly.  But when it falls, it falls hard and nothing will get it going again quickly.

Most of the time we can do three reboots on each of the computers in quick succession and the LAN will start working.  But some machines are persnickety as heck and won't come up at all.

And since the latest kernel update, our primary file server has been down for 35 hours, until I finally rolled back to the last kernel.  Now it's working fine again.  Fine being relative to the next LAN crash.

If I had to make a vote on the quality of Networking in Ubuntu, on a scale of 1 to 10, it would barely squeak by with a 2.
By the same token, the ONLY machines we have had zero networking problems with have been the CentOS machine, up now for 98 days, and the two Windows machines, they don't have counters that I know of for up time.  No Ubuntu machine has made it past 4 days before a LAN crash in 3 months time.

TTUL
Gary

---

### Post by brettg on 2008-12-03
"The only problem we have is each upgrade that comes down the pike brings down the entire LAN and it takes anywhere from 8 to 24 hours to get it back up and running again."

What?

---

### Post by gyrene2083 on 2008-12-03
K,
I'm pretty sorry to hear about your troubles with Linux. As for me and my NFS adventure, it took me most of the day to figure out how to mount the share on the server, (real Linux n00b) I finally was able to do it, Now the problem I am having is that when I mount the share(which is on my HTPC) on from the laptop it mounts ok but I can't see any files or write to it. <sigh> So, I am hoping that someone will let me know what permissions I'm missing as I am thinking it's a permissions issue.

I will keep you abreast as to the status of my project.

---

### Post by Kellemora on 2008-12-04
Hi Gyrene

Having the same problems here too, nothing automatic works, but we can do nearly everything manually.

We have YET to get rsync to find a remote hard drive, mounted or unmounted.  But it works fine from command line on local drives.
The irony of it, if we do a copy n paste to a mounted drive, it uses rsync to make the transfer without a hitch.

We've been doing most things manually ever since I installed Ubuntu.  At first I just figured it was a learning curve I had to get past, but now I'm finding that I'm doing it right, it just don't work as expected.  I can do the same things on CentOS (a RedHat clone) and it works just as expected without a hitch.

I've learned a lot, which lets me get around some of the many bugs, but personally I feel these problems should have been addressed years ago and no longer still be present.

You've probably already learned that if you go into the network controls it still shows that NO Ethernet Card exists!  Don't know how I did it, but on one of my machines I could select to use eth0 or eth1 for the LAN and keep it separate from the eth0 used for the internet.  I liked that, now I can't find it at all anymore and have one machine using eth1 that should be using eth0 since it don't even have an eth1 to work from, yet it works just fine, manually.

The ONLY thing about Ethernet that does work right is I have full internet connection on every computer through a hub to a router to the modem to the cable.  It don't matter how I mix or match things, or move things around, it just WORKS, just as it's supposed to do.

My son stops to visit from time to time and just simply plugs his wireless receiver into the router and his lap top connects to the internet without him changing a darn thing.

But as far as file sharing with all the computers.  I have to go through and use the GO/Location and type in the IP address of each computer and MOUNT the folders required at that desk, since they don't appear under Places/network as they should.

In other words, it's NOT that we can't get to them or that the LAN itself is down, it isn't.  smbtree shows ALL the shares.  But places/network can't find a single one, even though they are right in front of it's nose.

I have dumped network manager and installed Wicd and it has helped with a lot of little aggravations that were bugging the heck out of me.

But having to do everything MANUALLY takes a LOT of TIME!

We just had some more updates again today and true to course, the LAN dropped out until we rebooted each machine three times.

I think you said you were using NFS and Samba?
I tried that and had some shared files showing up twice on the desktops and only one of them would keep the permissions correct.  So I removed NFS and that problem went away.

Good Luck
TTUL
Gary

---

### Post by gyrene2083 on 2008-12-04
Hello Kellemora,

I really wish I could help shed some light on your problem, but I'm just really starting out in Linux. Back in '96 my buddy showed me RedHat, and I wished I would have learned it back then, instead I chose to learn more about windows, not that I regret learning windows although I still can't figure out somethings about it but that's neither here nor there. 

The sole purpose for me to learn Linux now is two-fold, one I got injured at work and I'm at home these days and bored out of my mind so I picked up my old tech books and started reading them again. Secondly, I built a command line base Home Theater PC, and I'm using XBMC as the gui. The pc is a gem I love it and so do the kids. I love it more though. lol... So, below is how I have my home network setup...

XP Pro - Hooked up to the network - SMB installed
3 XP Pro - Laptop's wireless  - setup to windows network
1 Ubuntu 8.10 Laptop - With SMB - NFS Client installed on it
1 HTPC 8.04 command line install - NFS Server - Client installed on it.

With the HTPC I finally figured out how to get my second drive to mount automatically. Everytime I would reboot I was having to reset it manually. I changed a few things in /etc/fstab and /etc/exports files and it is working now. Now I have to figure out how to mount that on my Intrepid Laptop. I can do it manually but when I reboot it disappears. 

So I'm going to look into squaring that away. My other problem I am faced with is when I am able to mount the share on my Intrepid pc, I can't seem to see the files or directories, I'm thinking a permissions issue, but since I am not using a gui on the HTPC box, everything is by hand. Kind of brings me back to the 'ole commodore 64 days in my friends house. lol I enjoyed those dos based games back then. 

The long of it is I need to get that HTPC Sharing a drive, so that I can write to it from various boxes in the house. Feel free to chime in with thoughts comments or ideas, as I am still learning my way around the terminal area.

---

### Post by Kellemora on 2008-12-04
Hi G

I'm a noob also!  And like you, I did play with Red Hat a little in days of yore!

My first computer was a Heathkit Heath/Zenith Octal Entry.  After that I purchased an Apple One motherboard and kit.  Then worked my way up through the various Apples, the Lisa System and Mac's.  Installed a Wang VS system at work after Lisa and had to move into PC's to be compatible with clients and what they were running.

Sorta let WinDOZE take over my life after that!

My purpose in using Red Hat was not so much for a working computer program as instead for the ability to control serial based hardware like temperature controllers, lighting and things like that, that technically only needed to pulse a serial port.
Had no monitor for the output while running the program, was using an Integral Data Systems 9 pin dot matrix printer to print a line of log every 15 minutes.  It only took 3 wires from a serial port to run the printer.  Back when things were simple, hi hi........

From using Windows I tried my hand as some assembly language, even broke down and purchased the microsoft macro assembler to see if what I had written would work.  It didn't and that was the end of that, hi hi........

I have not yet figured out how to access even CDs or DVDs on other machines using Ubuntu.  In Windows you just SHARE the device.  I've not found a way to do that in Ubuntu, but found a workaround in CentOS.

In any case, after about 10 years away from anything Linux related, I just started getting my feet wet again too, simply because of the support groups here on the Ubuntu forums.  And the backup teams that keep Ubuntu up and running with updates.

Once they get all the bugs out, I can easily see Ubuntu giving Mickey$oft a run for their money, hi hi..........
I'm actually looking forward to that day with great enthusiasm, hi hi.........

TTUL
Gary

---

### Post by HermanAB on 2008-12-04
Note that it may be easier to intall Services for UNIX (NFS) on Windows, than to get Samba to work on Linux.

I avoid Samba like the plague - it is just not worth the trouble.

Cheers,

Herman

---

### Post by gyrene2083 on 2008-12-04
Well I would love to get this up and running and I am working hard at it. Between googling, and this forum, as well as some books, I'm progressing slowly but surely, I managed to transfer a 170 meg file from the client to the server, but the transfer took a little over a half hour. That is unacceptable. 

So, if anyone has any ideas on how I can improve this by all means please lend this 'old Marine a hand.

---

