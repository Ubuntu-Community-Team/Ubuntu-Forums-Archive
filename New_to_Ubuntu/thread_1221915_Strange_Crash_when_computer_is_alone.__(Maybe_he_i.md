---
title: "Strange Crash when computer is alone.  (Maybe he is lonely.)"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by sixtyfootersdude on 2009-07-24
Good Morning,

I am brand new to Ubuntu and just installed it on a new to me computer.  

My problem is that I am getting strange crashes.  As far as I can tell they only happen when the computer is not being used.  Basicly whenever the computer is left idle it will freeze (no mouse movement, nothing).  I have not experienced any of these crashes when I was at the computer.  They only happen when I am away from the computer.  

This makes me wonder if it has something to do with automatic sleeping, screen dimming or something like that.  

I am unsure if this is a software or hardware problem.  The computer that I am running ubuntu on did not have an OS on it when I got it so I was not 100% sure that the computer was functional.  

I did a quick search of these forms to see if I could find anyone with the same issue but didn't find anything.  If someone could point me in the right direction that would be super.  I think what I should determine is:

1) If it is a hardware or software issue
2) How to disable sleep and other things on timers

but I thought I could post here to see if anyone had any insight.  

Thanks,
Jake

---

### Post by LowSky on 2009-07-24
go to power management under system  and turn off suspend when idle and see if that fixes the issue

---

### Post by Moe Z on 2009-07-24
Click System, Preferences > Screen Saver.. and then change setting as you wish.. may b u should set 'never' if u don't want to sleep over times

---

### Post by sixtyfootersdude on 2009-07-24
I have set the power management preferences so that it will never sleep and so that it will not put the display to sleep. Is that what you meant by: 

> go to power management under system  and turn off suspend when idle and see if that fixes the issue

I also disabled the screen saver.  

We will see if any of those things work.  

I am also running the top command so I can see what is running where it crashes.  (Would there be a better command for this?)

Jake

---

### Post by nyk on 2009-07-24
Hey, since you mentioned the screensaver, that sparked something that happened to me back when I first installed Ubuntu. i would put the screensaver on random, and for the most part it worked, but for some (i think the 3-D Sierpinski Triangle was one), it would freeze up my whole system. Rather than figure out what the problem was, I just turned off all screensavers, and it worked afterwards. Although I never knew for sure, I thought there may have been RAM and or graphics card usage issues (aka, memory leaks).

To see if this is a problem, try the demo screensaver that you had on when it crashed

---

### Post by sixtyfootersdude on 2009-07-24
Wow this is amazing!  I am 99% sure that just turning off the screen saver solved the problem.  

On a similar note, I just tried to hibernate the computer but I got an error that looked like this:

> ....  PM: Note enough free swap

I did some searching and found this post: [http://ubuntuforums.org/showthread.php?t=862557&page=3](http://ubuntuforums.org/showthread.php?t=862557&page=3)

Where it suggests that the free -m command will give you some insight.  These were the results:

```
mrjake@mrjake-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           245        240          4          0          4         51
-/+ buffers/cache:        184         60
Swap:          172        120         52
mrjake@mrjake-desktop:~$ 
```

I assume that because my swap<used it cannot work.  But what is swap?  I assume that used is the space in RAM that is used.  If I need to increase the SWAP how can I do this?

Thanks a lot for the help,

Jake

---

### Post by NullHead on 2009-07-24
I'm guessing that when the computer would auto-sleep when it's idle, it would crash because it looks like both your ram, and swap are full. 

I would upgrade the ram on that PC. Depending on its age, it may not be worth it. As long it's not freezing anymore, I guess you should just use it as is. 

Still, some extra ram would help.

---

### Post by sixtyfootersdude on 2009-07-24
Hmm, this is strange.  I am getting very frequent crashes and they are now occuring when I am using the computer instead of when it is left alone.  

I wrote a bash script to print the results of free -m every 5 seconds so that I can see what is in memory before a crash.  During my last crash there was only 10 mega bytes of space left.  Is this normal?  It says that total I have 245.  Is this too few?  Is it possible that I have problematic ram?  Would upgrading be a sure fix?  

In general I only have between 10 and 20 free mega bytes of ram.  

Is it likely that this is a hardware problem or could this be a software problem?  

Would switching to Ubuntu light be a better choice?  

Any tips?  

Thanks

---

### Post by pbotros1234 on 2009-07-25
That is not much memory at all, the recommended RAM for the most basic Ubuntu (Xubuntu) is 256 MB RAM.

Increase your swap partition, that should help a lot. Boot off the Live CD, and go to System > Administration > Partition Editor. Increase your swap partition size, and decrease the others if you need to make room for a bigger swap. This should help.

---

### Post by sam_delta on 2009-07-25
with that amount of ram, i would try to make swap bigger, or i would even consider installing xubuntu, since it is better suited for old hardware

a bit of explanation:
swap is a space in your harddrive reserved to be used as "RAM" in case your system runs out of ram, of course, the harddrive is much slower than ram memory, so while swap helps when you run out of memory, it stills sacryfies performance. 
when you run out of ram and swap, the system will most likely crash since it can not handle the memory requests

for more info on swap
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

sam

---

### Post by Moe Z on 2009-07-25
Normally, i recommend your swap partition size to double of ur actual RAM size.. it's working perfectly for my system.

---

### Post by sixtyfootersdude on 2009-07-25
Ok, I think that I am starting to understand.  I think that on windows virtual memory works in a similar way to swap but I am pretty sure that virtual memory can dynamically adjust how much it wants to use.  (Up to a maximum set by the user).  (Your description was super sam_delta).

But I guess that swap memory in Ubuntu is a seperate partition?  Does that mean that I could use a flash drive for swap?  (Not that I want to but *could *I?).  

Thanks for the help guys.  

Jake

---

### Post by sixtyfootersdude on 2009-07-25
Ok I haven't increased the swap space yet but I noticed something strange.  

I looked in Places -> Computer and saw these folders:
- 17.8 GB Media
- CD-Rom/DVD-ROM Drive
- CD-RW Drive
- Floppy Drive
- File System

I am confused what the difference between the Filesystem and the 17.8 GB Media drives.  Upon looking in the properties of the file system i noticed that there is only 74.2 MB of free space and only 2.0 GB is being used.  Having so little free space seems dangerous to me (although it is probably less dangerous since the swap partition is where virtual memory is kept).  

Assuming that my 17.8 Media drive is functinal I would like to give it all to the file system.  Is there anyway that I can do this?  Would the process for doing this be the same as allocating space for the swap partition?  

Why is my file system so small?  

Thanks,
Jake

---

### Post by oldfred on 2009-07-25
Check your partitioning with sudo fdisk -l  and df -h for usage.

If you do not have much data in your media drive and it is next to your root / partition you can adjust partition sizes with gparted from the CD. You cannot adjust mounted partitions, so you cannot change them while in Ubuntu. Back up before changing partitions just in case.

---

### Post by LewRockwell on 2009-07-25
> **sixtyfootersdude said:**
> Ok I haven't increased the swap space yet but I noticed something strange.  

I looked in Places -> Computer and saw these folders:
- 17.8 GB Media
- CD-Rom/DVD-ROM Drive
- CD-RW Drive
- Floppy Drive
- File System

I am confused what the difference between the Filesystem and the 17.8 GB Media drives.  Upon looking in the properties of the file system i noticed that there is only 74.2 MB of free space and only 2.0 GB is being used.  Having so little free space seems dangerous to me (although it is probably less dangerous since the swap partition is where virtual memory is kept).  

Assuming that my 17.8 Media drive is functinal I would like to give it all to the file system.  Is there anyway that I can do this?  Would the process for doing this be the same as allocating space for the swap partition?  

Why is my file system so small?  

Thanks,
Jake

you could always take a screenshot while in partition editor and then post that here

when creating a post you will notice a place to attach the screenshot if you scroll down a bit

also, relating your computer's make, model, build/part number(s) and other information gives us the greatest opportunity to help you thoroughly in the shortest amount of time...and with the fewest amount of posts...

.

---

### Post by sam_delta on 2009-07-25
looks like your not using the whole drive for your ubuntu filesystem, when installing, theres an option ¨guided partitioning, use entire disk¨, BUT its not the default option if there is another partition in the disk.

no problem here, u can reassign that 17 gig spsace for your file system as long as you are able to boot a live cd and edit the partitions.(with that amount of ram, live cd could be painfull slow)

if you do not feel confortable editing partitions or could not boot the live cd, just reinstall, but make sure you select the option ¨guided, use entire disk" when partitioning the disk. (guided partitioning will allso automaticly set swap space)

also about the swap: 
 although swap space is normally a partition, you can also make "swap files", without the need to resize the partition

about your question, yes it is posible to use a usb disk as swap, u just formatt it as "swap" or make a swap file in the disk and mount it as swap. if you really want to make that, i can post detailed instructions.

sam

---

### Post by sakusa on 2009-07-27
> **nyk said:**
> Hey, since you mentioned the screensaver, that sparked something that happened to me back when I first installed Ubuntu. i would put the screensaver on random, and for the most part it worked, but for some (i think the 3-D Sierpinski Triangle was one), it would freeze up my whole system. Rather than figure out what the problem was, I just turned off all screensavers, and it worked afterwards. Although I never knew for sure, I thought there may have been RAM and or graphics card usage issues (aka, memory leaks).

To see if this is a problem, try the demo screensaver that you had on when it crashed
I recently started using the 'Skyrocket' screensaver with screen lock, and had my first system freeze today after I left it idle for about half an hour. Have turned off the screensaver based on this thread. My RAM is 1.0GB, currently 27% utilized, and zero utilization of 2.8GB swap.

Are there any recommended 'crashproof' options out there for the screensaver? 

Am on Ubuntu 9.04 

Thanks in advance

---

### Post by sacredfaith on 2010-03-20
Interesting - I'm experiencing (still) the same problem with the skyrocket screensaver and "lock screen when..." checked.

 However, something that I've been doing as a workaround is as follows:

*When the screensaver is up*
1) Move the mouse
2) Type in the login password (even though there is no window to type this in) and press enter

So far, I'm able to get back in every time - so maybe this could help the developers zero in on the problem. To me, it seems as though it's simply not displaying the login screen.

Hope that helps

-sf

---

