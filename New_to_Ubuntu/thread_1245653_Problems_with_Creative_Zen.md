---
title: "Problems with Creative Zen"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by Spencer Caplan on 2009-08-20
I have an old 20 GB Creative Zen Sleek Photo. I do not use it for music because I have a newer iPod, but I wanted to use it as sort of an external harddrive to be able to transfer music from my Ubuntu laptop onto my Windows desktop. When I plug it into my Ubuntu laptop it shows up as having not 20 GB of storage, but 2.6 GB. I have tried using my Windows computer to reformat the player, but that did not help the problem. Does anyone have any solutions to this problem?

---

### Post by Spencer Caplan on 2009-08-21
So, are there any ideas?

---

### Post by Penguin Guy on 2009-08-21
Make sure it is plugged in, then [[COLOR="Blue"]run[/COLOR]]("http://www.psychocats.net/ubuntu/terminal") [COLOR="Green"]sudo fdisk -l[/COLOR] and post the results back here.

---

### Post by brunolabs on 2009-08-21
Try Gnomad2 from the repos.

---

### Post by Spencer Caplan on 2009-08-21
> **Penguin Guy said:**
> Make sure it is plugged in, then [[COLOR=Blue]run[/COLOR]]("http://www.psychocats.net/ubuntu/terminal") [COLOR=Green]sudo fdisk -l[/COLOR] and post the results back here.
Here is what it said, it looks like info on the computer's harddrive, not the Creative's:

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9175    73698156   83  Linux
/dev/sda2            9176        9546     2980057+   5  Extended
/dev/sda5            9176        9546     2980026   82  Linux swap / Solaris

---

### Post by Spencer Caplan on 2009-08-21
> **brunolabs said:**
> Try Gnomad2 from the repos.
I tried it but it does not recognize my Creative.
It says: No jukeboxes found on USB bus

---

### Post by Spencer Caplan on 2009-08-21
Just to clarify, I know that the problem does not reside with my Creative because it works and functions fine with Windows.

---

### Post by Spencer Caplan on 2009-08-22
Nothing at all?

---

### Post by RedRat on 2009-08-22
Do a search in Synaptic for Creative Nomad. You will see several programs and libraries that are needed. I would suggest that you install kzenexplorer and perhaps neutino also. You will need, and they will probably be installed, libnjb5 and libnjb-cil. i am assuming that you have gnomad2 installed.

---

### Post by Spencer Caplan on 2009-08-22
I will give that I try, and let you know how it works out. Yes, I have Gnomad 2 installed already.

---

### Post by Spencer Caplan on 2009-08-22
> **RedRat said:**
> Do a search in Synaptic for Creative Nomad. You will see several programs and libraries that are needed. I would suggest that you install kzenexplorer and perhaps neutino also. You will need, and they will probably be installed, libnjb5 and libnjb-cil. i am assuming that you have gnomad2 installed.

kzenexplorer doesn't recognize my Zen Sleek Photo. Neutino did not show up in Synaptic. So.... Now I am still at a loss.

---

### Post by RedRat on 2009-08-23
> **Spencer Caplan said:**
> kzenexplorer doesn't recognize my Zen Sleek Photo. Neutino did not show up in Synaptic. So.... Now I am still at a loss.

OK, it shows up in my synaptic but I am running 8.04 Hardy so there may be a problem with 9.04 which you appear to be running. This might be the difference between distros then. I will defer to those with experience with 9.04.

---

### Post by PGScooter on 2009-08-23
> **RedRat said:**
> OK, it shows up in my synaptic but I am running 8.04 Hardy so there may be a problem with 9.04 which you appear to be running. This might be the difference between distros then. I will defer to those with experience with 9.04.

to find out which repository it comes from, run ```
apt-cache policy <packagename>
```

There could also be a difference if one is running 32-bit and the other 64-bit.

Spencer Captain, what does ```
lsusb
``` output when you have the usb device plugged in?

---

### Post by RedRat on 2009-08-23
> **PGScooter said:**
> to find out which repository it comes from, run ```
apt-cache policy <packagename>
```

There could also be a difference if one is running 32-bit and the other 64-bit.

Spencer Captain, what does ```
lsusb
``` output when you have the usb device plugged in?

When I run that I get:
neutrino:
  Installed: 0.8.4-7
  Candidate: 0.8.4-7
  Version table:
 *** 0.8.4-7 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
        100 /var/lib/dpkg/status

So it looks like it is in the universe packages.

---

### Post by Spencer Caplan on 2009-08-26
> **PGScooter said:**
> to find out which repository it comes from, run ```
apt-cache policy <packagename>
```There could also be a difference if one is running 32-bit and the other 64-bit.

Spencer Captain, what does ```
lsusb
``` output when you have the usb device plugged in?

It displays:

Bus 001 Device 002: ID 041e:413d Creative Technology, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by SunnyRabbiera on 2009-08-26
> **Spencer Caplan said:**
> Just to clarify, I know that the problem does not reside with my Creative because it works and functions fine with Windows.

Well there the thing, Ubuntu is not windows so not all devices might work.
This is no fault of ubuntu or linux, but it is the fault of those who make these devices.

---

### Post by Spencer Caplan on 2009-08-27
> **SunnyRabbiera said:**
> Well there the thing, Ubuntu is not windows so not all devices might work.
This is no fault of ubuntu or linux, but it is the fault of those who make these devices.

I know that it is not a Linux issue. As I am now discovering, Creative is a very Windows based product which is annoying to say the least. It looks as if there is really nothing I can do about that so in the future I may just look for more Linux friendly products.

---

### Post by Paqman on 2009-08-27
> **Spencer Caplan said:**
> Creative is a very Windows based product which is annoying to say the least.

Normally their Zen product line uses MTP, which is a Microsoft technology, but fully supported on Linux. I have a 16GB Zen myself, and Gnomad normally spots it fine, as do other apps using the same technology, such as Iriverter and media players.

Check to see if your firmware is up to date. [Creative]("http://it.creative.com/knowledgebase/6773.asp") note that they've updated the MTP on your device at some point.

---

### Post by Forceflow on 2009-08-27
Here's what I do to get my Zen working:

Plug it in
Ubuntu recognizes it and mounts it
UNMOUNT it (right clik on desktop -> unmount), but keep it plugged in
Start gnomad
gnomad mounts it again, recognizes it

---

### Post by Spencer Caplan on 2009-08-27
> **Forceflow said:**
> Here's what I do to get my Zen working:

Plug it in
Ubuntu recognizes it and mounts it
UNMOUNT it (right clik on desktop -> unmount), but keep it plugged in
Start gnomad
gnomad mounts it again, recognizes it

First of all, thank you. That gets gnomad to recognize my player, and understand that it has 20 GB of memory, not 2.6. But, I can only seem to get gnomad to transfer by tracks, not entire folders, therefor my music is put onto it as a blob, (not sorted by artist/album), also some of the tracks are missing. Is there a way to transfer by folder? Could the missing tracks be due to my old Creative not accepting all music formats?

---

### Post by RedRat on 2009-08-27
> **Spencer Caplan said:**
> First of all, thank you. That gets gnomad to recognize my player, and understand that it has 20 GB of memory, not 2.6. But, I can only seem to get gnomad to transfer by tracks, not entire folders, therefor my music is put onto it as a blob, (not sorted by artist/album), also some of the tracks are missing. Is there a way to transfer by folder? Could the missing tracks be due to my old Creative not accepting all music formats?

I believe that the Creative Zen does everything by ID3 tags and NOT file names. That is the way the Creative Zen manager does everything. That is how it sorts by Artist, Album, Music Type, etc. Your "missing" files probably just lack the tags. I would suggest that before uploading to the Zen that you make sure that all the tags are on your mp3 files. I use Amarok to make sure that all my tags are there. It can sometimes be laborious but if you want to set up your playlist it needs to be done. There are other software apps out there that can also insure that all your mp3s have tags, e.g., EasyTag. Some of these are in the repos.

---

### Post by Spencer Caplan on 2009-08-28
> **RedRat said:**
> I believe that the Creative Zen does everything by ID3 tags and NOT file names. That is the way the Creative Zen manager does everything. That is how it sorts by Artist, Album, Music Type, etc. Your "missing" files probably just lack the tags. I would suggest that before uploading to the Zen that you make sure that all the tags are on your mp3 files. I use Amarok to make sure that all my tags are there. It can sometimes be laborious but if you want to set up your playlist it needs to be done. There are other software apps out there that can also insure that all your mp3s have tags, e.g., EasyTag. Some of these are in the repos.

Thanks, this seems to be working. I will update this should I have any further issues.

---

### Post by Spencer Caplan on 2009-09-09
> **Forceflow said:**
> Here's what I do to get my Zen working:

Plug it in
Ubuntu recognizes it and mounts it
UNMOUNT it (right clik on desktop -> unmount), but keep it plugged in
Start gnomad
gnomad mounts it again, recognizes it

When I plug it in, Ubuntu does not recognize it. Therefore I con not unmount it. gnomad does not recognize it either.

---

### Post by Capt_Zaphod on 2010-08-14
> **Spencer Caplan said:**
> When I plug it in, Ubuntu does not recognize it. Therefore I con not unmount it. gnomad does not recognize it either.

I have this same issue. :confused: I installed gnomad2, but, it didn't make a difference.

---

### Post by bloodshot13 on 2010-10-08
:confused:Forgive me if my post is very,very newbie. I also installed gnomad2,. But ubuntu 10.04 doesn't recognize my creative zen nomad xtra(Old school). Use terminal :~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 041e:4110 Creative Technology, Ltd Nomad Jukebox Zen Xtra
Bus 001 Device 002: ID 03f0:2504 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 and it shows my creative, but when I plug it into usb........... nothing....nothing changes on my creative or desktop. I try rhythmbox and doesn't recognize it either.](*,) I have a dell desktop computer that I use linux os only.

---

### Post by bloodshot13 on 2010-10-15
I can run kzenexplorer and gnomad2 in terminal as sudo, but when I try and play music I don't hear any sound. I've checked the mixer and it shows that it's not muted and sound level is up. My computer sound levels are up too. I know the computer sound works because I can hear music on start up of the computer(bongos,claps, snaps, ect.) and also hear music on the web(youtube and what not). any thoughts? Also I think it strange that it shows the creative nomad player is playing the song but in kzenexplorer I don't have a window showing any playback options(track time, volume, ect.):confused:

---

### Post by RedRat on 2010-10-15
> **bloodshot13 said:**
> I can run kzenexplorer and gnomad2 in terminal as sudo, but when I try and play music I don't hear any sound. I've checked the mixer and it shows that it's not muted and sound level is up. My computer sound levels are up too. I know the computer sound works because I can hear music on start up of the computer(bongos,claps, snaps, ect.) and also hear music on the web(youtube and what not). any thoughts? Also I think it strange that it shows the creative nomad player is playing the song but in kzenexplorer I don't have a window showing any playback options(track time, volume, ect.):confused:
I too have a similar problem with my 8.04 Ubuntu machine. If I run something like Amarok and have music playing, then visit YouTube, I cannot hear sound on YouTube. Vice-Versa, if I visit YouTube play a video then turn Amarok on, I hear no music from Amarok. I must completely go out of both FireFox and Amarok and chose one or the other. I use the Pulse Audio mixer. Now keep in mind that this is 8.04, I haven't seen this in 10.04.

---

### Post by bloodshot13 on 2010-10-16
I do have a track playlist and showing the track playing in gnomad2 but still no sound... I'm in a quandary...:). It's doing this whether I have another program running or not. I think their is a bug in gnomad2 because I stop the track and the whole program disappears!? I hear linux is the end all be all but I didn't have any trbl w/ windows and creative, maybe they're just hand in hand. I've spent alot of hours(learning crash course on ubuntu) about getting my little mp3 player to work and it's frustrating. I haven't tried much else out yet but so far I'm not impressed. I think if I find out why my creative is not showing that it is recognized by ubuntu or any player(gnomad2 or rhythmbox), then I that will probably fix it(maybe). I've noticed too that when I run sudo gnomad2 or kzenexplorer something else goes awry.... when I boot my computer up it gives me.....Could not update ICEauthority file /home/russell/.ICEauthority. I've read on a post how to fix and it worked but I can't open gnomad or zenexplorer as sudo without this error coming up agian. It's just stuff like this that makes linux kinda frustrating to us newbies and why alot of people don't want to use it. I'm trying to learn, but it is alot of time consumption. Sorry if I went out on a little rant, but that's my 2 cents. That and a buck will get you a cup of coffee.

---

### Post by tester10 on 2010-10-30
Hello, I have a problem with my Zen Micro stuck in Recovery Mode.
I am running Ubuntu 10.10
My case is similar to these:

[http://ubuntuforums.org/showthread.php?t=1529643&highlight=zen+micro](http://ubuntuforums.org/showthread.php?t=1529643&highlight=zen+micro)
[http://forums.techguy.org/miscellaneous-tech/682085-creative-zen-micro-stuck-recovery.html](http://forums.techguy.org/miscellaneous-tech/682085-creative-zen-micro-stuck-recovery.html)

I know it is not an Ubuntu problem, but i believe that reason is that the player is full with too much data+ the system files and there is almost no free space. For that reason it is unable to perform any of the operations 1-3 in recovery mode (1:Clean Up
2:Format All
3:Reload Firmware
4:Reboot)
It could only reboot which leads to the same screen with options, but only the other three operations could make it work normally.
I have tried to access it in Windows through the software that comes with it, but that is impossible in recovery mode.
Then I installed gnomad2 on Ubuntu 10.10 and tried to access it, but it starts "scanning jukebox library" and stays stuck there (the screen on the player changes from the recovery mode options the "docked" state which is the same as when the player software in Windows accesses it, but still there is a title "Recovery Mode" on the top of the screen).
So, I believe that the only way to make it work is to access the files on the player in recovery mode and clean some of them up through the PC so it can perform any of the operations 1-3 and then run normally.
I am pretty sure there is no problem with the battery as it charges normally.

My question is - is there any possibility to access the contents of the Creative Zen Micro in recovery mode besides through gnomad2? (i men not playing the music, but just seeing the files and being able to move/delete any of them)?

---

### Post by ENigma885 on 2010-10-30
@tester10
Your problem is different from that posted originally in this thread. I recommend u start a new thread. 
Btw, I personally access my Zen Mosaic through [[COLOR="Blue"]Banshee[/COLOR]]("http://banshee.fm/") 1.8.0. You can give it a try. To do so, open a Terminal window and paste the following
```
sudo add-apt-repository ppa:banshee-team/ppa && sudo apt-get update && sudo apt-get install banshee
```

---

### Post by RedRat on 2010-10-31
> **tester10 said:**
> Hello, I have a problem with my Zen Micro stuck in Recovery Mode.
I am running Ubuntu 10.10
My case is similar to these:

[http://ubuntuforums.org/showthread.php?t=1529643&highlight=zen+micro](http://ubuntuforums.org/showthread.php?t=1529643&highlight=zen+micro)
[http://forums.techguy.org/miscellaneous-tech/682085-creative-zen-micro-stuck-recovery.html](http://forums.techguy.org/miscellaneous-tech/682085-creative-zen-micro-stuck-recovery.html)

I know it is not an Ubuntu problem, but i believe that reason is that the player is full with too much data+ the system files and there is almost no free space. For that reason it is unable to perform any of the operations 1-3 in recovery mode (1:Clean Up
2:Format All
3:Reload Firmware
4:Reboot)
It could only reboot which leads to the same screen with options, but only the other three operations could make it work normally.
I have tried to access it in Windows through the software that comes with it, but that is impossible in recovery mode.
Then I installed gnomad2 on Ubuntu 10.10 and tried to access it, but it starts "scanning jukebox library" and stays stuck there (the screen on the player changes from the recovery mode options the "docked" state which is the same as when the player software in Windows accesses it, but still there is a title "Recovery Mode" on the top of the screen).
So, I believe that the only way to make it work is to access the files on the player in recovery mode and clean some of them up through the PC so it can perform any of the operations 1-3 and then run normally.
I am pretty sure there is no problem with the battery as it charges normally.

My question is - is there any possibility to access the contents of the Creative Zen Micro in recovery mode besides through gnomad2? (i men not playing the music, but just seeing the files and being able to move/delete any of them)?
Have you tried contacting Creative Tech Support? I have found them very helpful in the past. 

It really does sound as if you may a physical memory problems that may be beyond a simple software solution. If so, you may well have to return it to Creative.

---

### Post by gfd_2 on 2010-10-31
I'm running 10.04 and spent the last 4 hours through every gyration of "fixes" here on Ubuntuforums and was 99.9% unsuccessful.  For one brief and shining moment I was able to get 6 tunes moved to my 30 Gig Zen Xtra.  

I tried the whole ./configure, make, install process - bubkus.
downgraded the libmtb - bubkus. 
Rhythmbox fixes - bubkus.
Install, uninstall, reinstall gnomad - bubkus. 
Amorak - nothing.

BUT! **_Banshee_** did the trick! :guitar: I  was able to load 480 tunes with no issues!

---

