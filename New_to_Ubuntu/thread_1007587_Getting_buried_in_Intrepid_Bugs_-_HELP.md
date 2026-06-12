---
title: "Getting buried in Intrepid Bugs - HELP"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by nowhere@cox.net on 2008-12-10
Hi all, I have 2 machines. One is a small Dell desktop running desktop 8.10 upgraded from 7.10 to 8.04 to 8.10 and one is a desktop running 8.10 server fresh install, with ubuntu-desktop installed. I am being completely overrun with bugs without solutions right now.

The 1st system has an integrated intel 865G card and I cannot set the resolution. I tried to post the problem here: [http://ubuntuforums.org/showthread.php?t=1006502]("http://ubuntuforums.org/showthread.php?t=1006502") but no response yet. 

Now today the other system encryptfs is acting up and won't mount the Private folder and can't get my files. Also today, I can no longer mount my USB hard drive from Nautilus (worked fine yesterday). There are no errors in any logs anywhere. Clicking on the drive in the left pane just does nothing. I can mount it from the terminal and it works however. 
Also on this system going about 3 weeks now with no solution is USB connecting to my VMWare XP system to sync my iPhone. Used to work fine in Gutsy with the same version of VMWare Server now it doesn't work very well ([http://ubuntuforums.org/showthread.php?t=999563]("http://ubuntuforums.org/showthread.php?t=999563"))

Lastly I have a wireless Mythbuntu with a marginal signal (my laptop sitting next to it is full strength). In addition, every time it loses connection and reconnects, some window about the keyring pops up and forces me to enter a password for the keyring to reconnect the network. Never had to do this before. 

If you know anything about these things let me know!
Thanks

---

### Post by gettinoriginal on 2008-12-11
I cannot answer most of your post, but the keyring box should have a tick box for not asking again.

---

### Post by gettinoriginal on 2008-12-11
Try these for your resolution problem;  Hope they help :p

[http://ubuntuforums.org/showthread.php?p=6313158](http://ubuntuforums.org/showthread.php?p=6313158)

[http://forum.soft32.com/linux2/screen-resolution-ubuntu-ftopict52834.html](http://forum.soft32.com/linux2/screen-resolution-ubuntu-ftopict52834.html)

[http://www.linuxforums.org/forum/ubuntu-help/80129-please-help-x-resolution-problems.html](http://www.linuxforums.org/forum/ubuntu-help/80129-please-help-x-resolution-problems.html)

---

### Post by gettinoriginal on 2008-12-11
This might help with the reception problem

[http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=7314](http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=7314)

---

### Post by nowhere@cox.net on 2008-12-11
Thanks for the post orig! 

1. For some reason, whenever I lose connection, it asks, even if told not to. It does this on my laptop with my portable router is some circumstances too. It's like Ubuntu forgets that it's connected to this AP before.

2. Unfortunately, none of the links helped fix the screen res thing. Although I ran an xrandr command I saw in one of them and the output might spark someone to think of a solution
```
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 2048 x 2048
VGA connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS connected 1152x864+0+0 (normal left inverted right x axis y axis) 388mm x 291mm
   1280x1024      85.3 +   85.0     85.0     75.0     60.0  
   2048x1536      60.0     60.0  
   1920x1440      60.0  
   1856x1392      60.0  
   1792x1344      75.0     60.0  
   1600x1200      85.0     85.0     75.0     70.0     65.0     60.0  
   1680x1050      84.9     74.9     69.9     60.0  
   1600x1024      60.2  
   1400x1050      85.0     74.8     70.0     60.0  
   1440x900       59.9  
   1280x960       85.0     75.0     60.0  
   1360x768       59.8  
   1152x864      100.0     85.1     85.0     85.0     75.0     75.0     70.0     60.0* 
   1024x768       85.0     85.0     75.1     75.0     70.1     60.0     43.5  
   832x624        74.6  
   800x600        85.0     85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     85.0     75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        87.8     85.0     70.1  
   640x400        85.1  
   640x350        85.1  

```

3. I had a buddy give me 300 feet of CAT6 cable. I'm going to crawl around in the attic and run a downstairs wired switch... Thanks tho! BTW, the WiFi card is one of the PCI cards and someone just told me the little antenna on the back of the card is notoriously too close to the PC case. That could be the problem. I used to have a wireless bridge (802.11b) and it worked better since it was a seperate unit. The machine with the tuner cards had no spare slot for a wifi card so I used a bridge. Worked for 4 years but just too slow now for streaming...

I will post the output of xrandr on my post for help in the graphics forum...

Thanks again. If you have any other ideas I would love to hear em!

---

### Post by nowhere@cox.net on 2008-12-11
Ok I fixed the resolution issue almost. See the resolution here: [First Plea for Help]("http://ubuntuforums.org/showthread.php?t=1006502")

Now as I finish this up, yet another problem surfaces. I can no longer mount drives from within nautlius. Using mount works fine but not nautilus. I'll make another thread for that later...

Thanks for the video help, on to the others...

---

### Post by Sef on 2008-12-11
> Now as I finish this up, yet another problem surfaces. I can no longer mount drives from within nautlius. Using mount works fine but not nautilus. I'll make another thread for that later...

I wonder if you got some bad hardware, or possibly a bad install.

1) If you run the live cd, how does it work?

2) Run [memtest86]("http://memtest86.com"), to check your ram.  The newer version is available on that link, or go into grub to run an older version.  (To get into grub, push escape when first booting.)

---

### Post by gettinoriginal on 2008-12-11
Have you tried this for the resolution problem ??

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by nowhere@cox.net on 2008-12-12
> **gettinoriginal said:**
> Have you tried this for the resolution problem ??

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Yeah I saw that one. The problem is determining the modline which that wiki doesn't address. It's working well enough for me now so I am going to move on to some of the other problems.

The highest priority for me is the nautilus mounting since I have little ones that mount their PSPs, and cameras that don't have sudo rights or even know much about the command line...

Thanks!

---

### Post by nowhere@cox.net on 2008-12-12
> **Sef said:**
> I wonder if you got some bad hardware, or possibly a bad install.

1) If you run the live cd, how does it work?

Actually it was working earlier this week. To be clear, I have an NTFS hard drive and USB hard drives and they show up just fine in the left pane of nautilus but they will not mount from there. Clicking on them once used to mount them then a second time to navigate to them. Also there is a mount option on right click. Now it does literally nothing. Not one thing changes in the system logs too. Very weird...

I did accidentally leave backports and proposed checked for repos and let it upgrade so I got a bunch of upgrades. I wish there were a way to revert back to a certain day.

If I uncheck those repos and reload, the newer packages will show as different. Is there a way to go back to that point?

Thanks!

---

### Post by gettinoriginal on 2008-12-12
Is NTFS enabled in:

cat /proc/filesystems

---

### Post by nowhere@cox.net on 2008-12-20
Actually I dont see NTFS in the output BUT the automount seems to work sometimes. When I am on the console it seems to mount almost always but not totally. It won't automount at all remotely through freeNX. It used to work fine.

Thanks again for sticking with me.

---

### Post by nowhere@cox.net on 2008-12-29
Here's an update on the bug list. The nautilus mount works fine when logged in from the console but not through the NX. 

The latest update on the Intrepid kernel has broken the Disk Usage Analyzer for me on my laptop. I haven't updated anywhere else yet.

So I am pretty much in a state of maintaining at least one bug active at all times. Right now I still have 3 annoying ones active.

---

