---
title: "No login window 10.4"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by chaunzaggaroth on 2010-06-13
I am running Ubuntu 10.4 amd64.  I've been using it for a few weeks.  I was shuting down and in the process ubuntu hung.  I waited a few minutes and the gui was still displaying a shutdown screen but the loading bar had stopped.  I shutdown the computer manually(held the power button until it shutdown).  Once I rebooted, I am taken to the normal login screen, but there is no window for loging in.  I can see the background fine, but I lack the window which allows me to login.  I can use the other shells fine in the cli.  I am able to do everything I was before through them.  But, I can't seem to login at the gui.

---

### Post by chaunzaggaroth on 2010-06-13
Still haven't been able to figure it out.  Anyone have an idea?

---

### Post by -humanaut- on 2010-06-13
Are you using a nvidia card by chance?

---

### Post by chaunzaggaroth on 2010-06-13
> **-humanaut- said:**
> Are you using a nvidia card by chance?

Nope, I'm actually using integrated graphics, i3 processor laptop.  It's worked plenty fine up until I shut it off manually during the shutdown.

---

### Post by chaunzaggaroth on 2010-06-13
Is there a way I could log into tty7 without the gui interface?  Could I log into tty7 using a different shell?  Perhaps after loging into tty7 with a different shell, I could start the gui with the "startx" command.

---

### Post by diablo75 on 2010-06-13
Are you using the default theme for your login screen or one that you downloaded?  Just curious.

---

### Post by chaunzaggaroth on 2010-06-13
> **diablo75 said:**
> Are you using the default theme for your login screen or one that you downloaded?  Just curious.

the default

But, I was wondering if I could possibly change the default theme or reload the default theme.  Perhaps I broke it in the process of shutting my computer down incorrectly?

---

### Post by diablo75 on 2010-06-13
Have you tried booting under a previous kernel?

To gain access to the grub2 menu during boot, hold down the Shift key right after POST.  There may be a previous version you can select and see if it works.  Just a shot in the dark.

---

### Post by shardvexspangler on 2010-06-13
Um... confusing.
 
Try booting rescue.  (Ubuntu failsafe in the grub menu.)
Try using ubuntu from command line, and work it from there, use "startx" command, work it from there.
 
Weird....???

---

### Post by chaunzaggaroth on 2010-06-13
Well I booted with Grub and tried ever kernel.  I managed to get through by using failsafe in recovery mode and loging in with root.  From there I attempted to switch users and it brought me back to the login screen.  The login screen still doesn't display the window for loging in.

---

### Post by diablo75 on 2010-06-13
> **chaunzaggaroth said:**
> Well I booted with Grub and tried ever kernel.  I managed to get through by using failsafe in recovery mode and loging in with root.  From there I attempted to switch users and it brought me back to the login screen.  The login screen still doesn't display the window for loging in.

You might try to see if you can disable the login window all together.  There's an option to do that in your System>Administration menu, where you can tell it to automatically log a user in.  I'm not suggesting this as a fix, but as an experiment to see if it works under normal circumstances.  Might then check to see if any updates are pending.

---

### Post by shardvexspangler on 2010-06-13
Just some tests:
 
Try using a different theme?
 
Try making a new account, maybe "backup", then try logging into that.
 
It sounded by the last post, that you used switch users. (I think?) Try logout instead.
 
Maybe if you tell us if you did something before you shut it down the first time, like changing settings.

---

### Post by chaunzaggaroth on 2010-06-13
I'm at the Desktop in root.  I went to system > administration >login screen settings

The window is grayed out (locked).  There is a button to unlock it, but upon pressing it, the window is still locked.

---

### Post by shardvexspangler on 2010-06-13
I am stumped. Maybe try a different theme, or try both options: either switch user or log out. Did you ajust any settings when you shut down that first time?

---

### Post by chaunzaggaroth on 2010-06-13
> **shardvexspangler said:**
> Just some tests:
 
Try using a different theme?
 
Try making a new account, maybe "backup", then try logging into that.
 
It sounded by the last post, that you used switch users. (I think?) Try logout instead.
 
Maybe if you tell us if you did something before you shut it down the first time, like changing settings.

Sure I'll go ahead and try the above.  I was updating and installing some software before I shutdown.  It was nothing graphical.  If I remember right, I installed wireshark 1.2.9 and it's dependencies such as g++.  Is there a log file that can tell me exactly what I was doing?

---

### Post by chaunzaggaroth on 2010-06-13
I tried loging out...  and it brought me back to bash.  From there I logged in as my usual username.  I still couldn't access the login screen settings.  I shutdown and tried rebooting to see if anything has changed after changing the theme to clearlooks.  I still have no login window.  This is quite bizarre.

---

### Post by shardvexspangler on 2010-06-13
Sorry, I don't know!

---

### Post by chaunzaggaroth on 2010-06-13
> **shardvexspangler said:**
> Sorry, I don't know!

It's no problem.  Thank you for the support.  You and Diablo75 got me further than I had been before.  If worst comes to worst is there a way in witch I can reinstall ubuntu without losing any of the data I already have?  I don't mind rebuilding ubuntu.  Sure it'll take a few minutes, but it's no worries.  But, I'd still like to keep my accumulated files that are too large to store elsewhere.

---

### Post by marcoftheknight on 2010-06-13
> **chaunzaggaroth said:**
> Sure I'll go ahead and try the above.  I was updating and installing some software before I shutdown.  It was nothing graphical.  If I remember right, I installed wireshark 1.2.9 and it's dependencies such as g++.  Is there a log file that can tell me exactly what I was doing?

When you update using ubuntu you always are affecting your graphical system IF you allow for latest update I beleive the Xserver can be broken or something I cant remeber what exactly gets broken but your video driver have to be purged!

Purge your video drivers then reinstall them an that should work.
I had similar symtops after an update and had to purge ati drivers and reinstall.

Thanks

---

### Post by chaunzaggaroth on 2010-06-13
> **marcoftheknight said:**
> When you update using ubuntu you always are affecting your graphical system IF you allow for latest update I beleive the Xserver can be broken or something I cant remeber what exactly gets broken but your video driver have to be purged!

Purge your video drivers then reinstall them an that should work.
I had similar symtops after an update and had to purge ati drivers and reinstall.

Thanks

Thank you for the reply.  How would I go about purging the drivers, and further reinstalling them?

---

### Post by diablo75 on 2010-06-13
> **chaunzaggaroth said:**
> If worst comes to worst is there a way in witch I can reinstall ubuntu without losing any of the data I already have?

I'd wait to see if purging your video drivers (if you are able to find out how; I wouldn't know where to start with that...) does the trick...

But, like you said, if worse comes to worse and you want to do a reinstall...

I see two options.

1.  If you have an external hard drive with enough free space on it, boot from a Live CD, go to the Places menu and open the hard drive up on your system.  Copy the contents of your /home folder to the external.  Then reinstall Ubuntu, formatting the hard drive and starting from scratch.

2.  If you don't have an external and your primary linux partition is housing both your root partition and your /home partition... I've never tried this but I bet it would work....  By the way, I am assuming that when you installed Ubuntu you selected "Guided" when it asked you how you wanted to partition the drives.  Guided creates 2 partitions:  One for the the whole OS with your home folder included, and another much smaller partition for the Swap.  

Boot from a Gparted Live CD.  Shrink the primary linux partition down by about 20GB (or more if you wish).  You'll end up with a gap of 20 gigs that isn't allocated to anything.  Next, boot from an Ubuntu Live CD, open your hard drive up.  Delete everything except the home folder (and use CTRL-H to reveal hidden stuff).

Then proceed to install Ubuntu from the live CD.  When you get to the partitioning section, select manual partitioning.  Tell it to use the 20GB unallocated space for your root (root is represented with a single / slash) and to format it.  Then tell it to use the partition that you just shrank as your new /home partition (and to NOT format it at all, but leave it as it is).  The swap partition should automatically be detected and used as is.  

Ubuntu (the system files/OS) will install in the new 20GB partition and will use the other partition as your home.  This way you don't have to copy data to an external hard drive first, but it is a bit risky because resizing a partition on rare occasions really screws stuff up (but I've not had a problem with Gparted before).  The other advantage of doing this is that in the future, if you have another big problem like this, you just format the root partition but keep the /home partition intact and just tell it to use it as is.

---

### Post by chaunzaggaroth on 2010-06-13
Thank you Diablo75.  I don't remember if I chose guided or not, but I'll be sure to check.  I'll try purging the graphics drivers and reinstalling them.  If that doesn't work, I'll use gparted to delete everything but the home folder.  From there I'll shrink the partition to just 20gb and I'll install ubuntu manually.  I'll use the entire drive except for the 20gb, which I will allocate as the home folder.

---

### Post by diablo75 on 2010-06-13
> **chaunzaggaroth said:**
> Thank you Diablo75.  I don't remember if I chose guided or not, but I'll be sure to check.  I'll try purging the graphics drivers and reinstalling them.  If that doesn't work, I'll use gparted to delete everything but the home folder.  From there I'll shrink the partition to just 20gb and I'll install ubuntu manually.  I'll use the entire drive except for the 20gb, which I will allocate as the home folder.

Just wanted to clarify something.  Don't shrink the partition down to 20 GB, but shrink it down BY 20GB or so (whatever you want).  You're just opening up a gap of free space to install a new / partition and leaving the current partition you have in place to be mounted as your /home partition.

So you'll probably go from something like this:

[FONT="Courier New"][.....Linux ext3/4 partition with everything][swap][/FONT]

to:

[FONT="Courier New"][/(root) ][............new /home............][swap][/FONT]

or:

[FONT="Courier New"][............new /home............][/(root) ][swap][/FONT]

---

### Post by chaunzaggaroth on 2010-06-14
> **diablo75 said:**
> Just wanted to clarify something.  Don't shrink the partition down to 20 GB, but shrink it down BY 20GB or so (whatever you want).  You're just opening up a gap of free space to install a new / partition and leaving the current partition you have in place to be mounted as your /home partition.

So you'll probably go from something like this:

[FONT="Courier New"][.....Linux ext3/4 partition with everything][swap][/FONT]

to:

[FONT="Courier New"][/(root) ][............new /home............][swap][/FONT]

or:

[FONT="Courier New"][............new /home............][/(root) ][swap][/FONT]

Thank you for the clarification.  I clearly misunderstood.  I will shrink the /dev/sda1 partition (ext4) by 20gb and install the new ubuntu partition in that space.  Before doing that though, I will make sure to delete everything excluding the home folder.

---

### Post by chaunzaggaroth on 2010-06-14
I shrunk the partition by 20gb.  How can I go about modifying the existing partition's contents.  It restricts me from doing so because I am not root.

---

### Post by chaunzaggaroth on 2010-06-14
I reinstalled ubuntu in the manner you suggested, Diablo75.  That allowed me to keep my home partition so I'm more than happy.  I just used a grep command to remove all but the specified partition.  i didn't encrypt the original installation so I only needed to create a su password on the live installation of ubuntu.  This was the command I used for in case anyone was wondering:

ls|grep -v home|rm -r

Make sure you're on the root of the partition before you do this. 

Thank you for all of the help!

---

### Post by diablo75 on 2010-06-14
> **chaunzaggaroth said:**
> ls|grep -v home|rm -r


That takes some balls.  Way to go!  I would have probably run "gksu nautilus" to open up a file browser as root and manually select everything to delete.  Glad to see you got everything you didn't need cleaned off and the new OS setup.

---

### Post by chaunzaggaroth on 2010-06-14
> **diablo75 said:**
> That takes some balls.  Way to go!  I would have probably run "gksu nautilus" to open up a file browser as root and manually select everything to delete.  Glad to see you got everything you didn't need cleaned off and the new OS setup.

Balls, lack of cause/effect analysis same thing right?  I'll go with the former to make myself feel better.  Thank you again for the help.  I'll be sure to remember gksu nautilus next time though.  

*wipes sweat of forehead*

---

