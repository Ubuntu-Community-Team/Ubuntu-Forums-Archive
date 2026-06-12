---
title: "my ubuntu doesnt work like normal :("
date: 2010-06-05
forum: New to Ubuntu
---

### Post by 29732 on 2010-06-05
Well, this is the story:

Once, when the update manager showed up, what I usually do is click install. And when I did, it (of course) showed up my box to type the password in. And when I did, I clicked ok, it showed that it was starting, it read the packages, but then, nothing. It didnt even update.

I had a similar problem when i was installing a script from gedit.
It showed the box to run it terminal, cancel, etc. and I clicked what I was supposed to on a video, so I clicked on run in terminal, and the terminal just popped up for a split second, then nothing.
So I just runned it on terminal and amazingly, it started to work.

Now I have a few corrupt programs on ubuntu like wine and fprint and I uninstalled them via software center, but I never figured out how to remove ALL the traces of those programs (because I'm just getting used to ubuntu, I dont know how to use it completely) and I can't reinstall ubuntu (I can, but I'm not allowed to. Long story.).

So is there a way to fix all of it or do I have to live with it??
:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by XubuRoxMySox on 2010-06-05
There's a way-kewl simple little graphical tool called Computer Janitor that helps clean things up when I make a mess of them. Install that and run it. Then write back and let us know if it worked!

Hoping,
Robin

---

### Post by cogier on 2010-06-05
If dixiedancer's option does not work you might like to consider a fresh install.

---

### Post by 29732 on 2010-06-05
I cant really install ubuntu again

As I said, long story

---

### Post by 29732 on 2010-06-05
> **dixiedancer said:**
> There's a way-kewl simple little graphical tool called Computer Janitor that helps clean things up when I make a mess of them. Install that and run it. Then write back and let us know if it worked!

Hoping,
Robin



REALLY weird....

It wont start from menu.... I'll try by terminal

---

### Post by 29732 on 2010-06-05
IS there a way to run it by terminal??

---

### Post by jwbrase on 2010-06-05
> **29732 said:**
> IS there a way to run it by terminal??

```
sudo computer-janitor-gtk
```

Assuming you're using GNOME.

Why can't you reinstall? Is it someone else's computer?

---

### Post by sidzen on 2010-06-05
> **29732 said:**
> IS there a way to run it by terminal??
You may want to go to this page and see if it can give answers you seek:
[https://help.ubuntu.com/community/Grub2#Command](https://help.ubuntu.com/community/Grub2#Command) Line and Rescue Mode

---

### Post by pizza-is-good on 2010-06-05
```
sudo apt-get purge wine
```

will remove everything that has to do with wine. Give it a try.

'glitches' always show up. The best way to get rid of them is a fresh install. I know you said that you can't do that, but if you are not being watched while you use the computer, nobody would ever know the difference... and it shouldn't take you more than 30 minutes. My lucid lynx installed in 15 minutes....

---

### Post by 29732 on 2010-06-05
> **jwbrase said:**
> ```
sudo computer-janitor-gtk
```

Assuming you're using GNOME.

Why can't you reinstall? Is it someone else's computer?

Used to be mine.....

Now its my mom's

---

### Post by 29732 on 2010-06-05
> **pizza-is-good said:**
> ```
sudo apt-get purge wine
```

will remove everything that has to do with wine. Give it a try.

'glitches' always show up. The best way to get rid of them is a fresh install. I know you said that you can't do that, but if you are not being watched while you use the computer, nobody would ever know the difference... and it shouldn't take you more than 30 minutes. My lucid lynx installed in 15 minutes....

It's dual-booted with vista

---

### Post by pizza-is-good on 2010-06-05
> **29732 said:**
> It's dual-booted with vista

Yeah, its no problem to do a fresh install even if it is dual booted. I'll walk you through it if you want.... As I said, it probably won't take more than 30 minutes.

---

### Post by 29732 on 2010-06-05
> **pizza-is-good said:**
> Yeah, its no problem to do a fresh install even if it is dual booted. I'll walk you through it if you want.... As I said, it probably won't take more than 30 minutes.

And it won't erase everything on Vista?


I also might need to keep a few things on ubuntu....
But I doubt it will be a problem

---

### Post by 29732 on 2010-06-05
Oh, and I have a corrupt copy of Ubuntu...
One of MY screwups :)

Computer Janitor doesn't show anything since I killed wine

---

### Post by 29732 on 2010-06-05
Huh, and now admin tools are working

But google chrome remains the same...

This is the error:
Your profile could not be opened correctly.

Some features may be unavailable.  Please check that the profile exists and you have permission to read and write its contents.

Is that fixable?
And BTW,
does purge work for other programs?

---

### Post by pizza-is-good on 2010-06-05
> **29732 said:**
> And it won't erase everything on Vista?


No, as long as the vista partition is not touched, then no. BUT, there is always a risk of data loss when messing with partitions. I can't guarantee that no data will be lost, but I can tell you that I've messed with partitions A LOT, and I've never had problems. It is a small risk that you have to take.

Do this for me:

run this in the terminal, and post the output
```
fdisk -l
```

That'll let me know what to look for.

---

### Post by pizza-is-good on 2010-06-05
> **29732 said:**
> 
does purge work for other programs?

yes, purge works for all programs. you need the correct package name, but that's easy to get by ALT+F2 and then typing the program name, then click on the program in the list below, and the name that appears in the line above is the package name.

---

### Post by 29732 on 2010-06-06
It looks like the issue is solved since I purged WINE....

But what about the google chrome error?
I don't really want to uninstall it since it saved a few account of mine.

See post #15

One time I did try reinstalling it and it had the same error message, although it's not a big problem, I can still access internet form it, the error message is simply annoying, and it won't show my history.

---

### Post by gandaran on 2010-06-06
> but I never figured out how to remove ALL the traces of those programs
when you remove a program completely the user configuration files are left behind, if you reinstall it, it will still be using those configuration files, to remove them go to the hidden user home folder look for the problem program files (maybe in .gconf or .config) and just delete them, then you can restart the program, it will just create a new profile.

---

### Post by 29732 on 2010-06-06
> **gandaran said:**
> when you remove a program completely the user configuration files are left behind, if you reinstall it, it will still be using those configuration files, to remove them go to the hidden user home folder look for the problem program files (maybe in .gconf or .config) and just delete them, then you can restart the program, it will just create a new profile.

I kind of thought it would leave behind something....
But I never knew how to remove the traces
Thanks
I just might try that

---

### Post by 29732 on 2010-06-06
But then, can I remove specific files out of chrome so it wont erase my passwords, etc. and still run normally?

---

### Post by acrazyplayer on 2010-06-06
I'm gonna be honest here. Even if you have 20 passwords it wont take that long to enter them all back into chrome, but you do know that anyone who sits down on the computer can very easily see your passwords in about three clicks of the mouse?

---

### Post by 29732 on 2010-06-06
well, what about if me (or my mom) forgot them?????????????

---

### Post by pizza-is-good on 2010-06-07
> **29732 said:**
> well, what about if me (or my mom) forgot them?????????????

You could always create a locked spreadsheet that has all your passwords. It's a little safer than storing them in a browser, but I'm sure that since the file is only locked and not encrypted, for a real hacker it wouldn't be hard to see the contents of the file...

---

### Post by 29732 on 2010-06-07
And strangely nuff, Ubuntu started to freak out...

It just now changed my appearance...
But other than that, it's working fine

---

### Post by 29732 on 2010-06-07
And it reset Compiz
ARGH!!!!!!!!
That is unexpected.

---

### Post by 29732 on 2010-06-07
And it occasionally doesn't refresh the taskbar.......

WHAT IS GOING ON?!?!?!?!

---

### Post by 29732 on 2010-06-07
I purged google chrome, but to no avail, it still shows the error message (see post 15)
Is there a way to actually fix that?

---

### Post by oldsoundguy on 2010-06-07
I use Ubuntu Tweak.  Not only does it manage your download sources, it has a very GOOD clean up program in it.  Program is segmented so you can choose what you want to clean up.

It also has some other options I have yet to try.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Find your build and install the appropriate one.

---

### Post by sydbat on 2010-06-07
29732 - how did you install Ubuntu? Did you install it via wubi (meaning you put the CD in while Windows was running and installed it like a program)? If so, I have found that wubi installs always corrupt due to the fragmentation of the NTFS (Windows) file system.

If you do choose to reinstall properly, we will help you out, step by step.

In the mean time, back up everything.

---

### Post by 29732 on 2010-06-07
I don't think i installed with wubi, although it gave me the option

All I did is download it from ubuntu.com and burn it to an empty disk (and no, not a data disk)  

And then i restarted the laptop and booted from there

The first time I installed it I shut down the computer in the middle of installing it (I forgot to do something)  

The next time I did, I didn't remove the corrupted partition because I didn't remember how to do it and put it as a separate partition

I let it finish installing it and booted the OS
I know which one was corrupted so that is not the problem 
And after a few days of using Ubuntu I installed a lot of crap and updates (my fault)
So what do you think is the problem?

---

### Post by pizza-is-good on 2010-06-08
> **29732 said:**
> And it occasionally doesn't refresh the taskbar.......

WHAT IS GOING ON?!?!?!?!

It really just sounds like a very corrupted installation of the OS. They happen sometimes.

> **29732 said:**
> I don't think i installed with wubi, although it gave me the option

All I did is download it from ubuntu.com and burn it to an empty disk (and no, not a data disk)  

And then i restarted the laptop and booted from there

The first time I installed it I shut down the computer in the middle of installing it (I forgot to do something)  

The next time I did, I didn't remove the corrupted partition because I didn't remember how to do it and put it as a separate partition

I let it finish installing it and booted the OS
I know which one was corrupted so that is not the problem 
And after a few days of using Ubuntu I installed a lot of crap and updates (my fault)
So what do you think is the problem?

OK, so you did a full install. 

My first install of Ubuntu, I did believe that it was the Updates that messed it up. I'll never find out really. My guess is that there was a few things wrong with the installation already, and the updates didn't quite agree with it so it all crashed with them.

If a few bits or bytes get copied wrong to the computer during the installation, that can corrupt it all later. It is best fixed with fresh install.

I doubt that the corrupted partition is the problem, but do this:

Go to your terminal, and type the following:
```
fdisk -l
```then post the output to us, so we can see your partitions. (When you copied it, highlight it in your post, and click the pound (or number) key in the options above. That will give it CODE tags)(running this on the terminal will NOT damage your system)

I will again say it, the best and quickest way to fix this will be a fresh install. If you post the output of fdisk, we will be able to delete that corrupted partition and make sure that is not the problem.

---

### Post by 29732 on 2010-06-08
when i type in fdisk, it doesn't do anything...
it asks for more info

---

### Post by Miljet on 2010-06-08
```
sudo fdisk -l
```

Make sure to add the -l. That is a small L, not a one.

---

### Post by 29732 on 2010-06-09
Yes, that's what I did, and strangely nuff, it is now showing me the info

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0260f13d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29708   238628889    7  HPFS/NTFS
/dev/sda2           37596       38913    10580992    7  HPFS/NTFS
/dev/sda3           29709       37596    63356929    5  Extended
/dev/sda5           34492       37462    23859200   83  Linux
/dev/sda6           37462       37596     1077248   82  Linux swap / Solaris
/dev/sda7           29709       34289    36796416   83  Linux
/dev/sda8           34290       34492     1622016   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mmcblk0: 505 MB, 505413632 bytes
4 heads, 51 sectors/track, 4838 cylinders
Units = cylinders of 204 * 512 = 104448 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           2        4839      493449+   6  FAT16
Well...? 
Oh and BTW, I got the go for reinstalling Ubuntu
*jumps happily*

---

### Post by pizza-is-good on 2010-06-09
Thanks for the info, it will help us.

So I take it you'll want to re-install?

---

### Post by 29732 on 2010-06-09
Is there another way?

If not, then sure

---

### Post by 29732 on 2010-06-09
And, I forgot how to change partitions manually

any help there?

---

### Post by Metrop021 on 2010-06-09
> **29732 said:**
> Is there another way?

If not, then sure

i skimmed over this thread and judging by the abnormal amount of problems you've had it's probably the best way.

> **29732 said:**
> And, I forgot how to change partitions manually

any help there?

You mean delete a partition? There should be a partitioner in system>administration

---

### Post by 29732 on 2010-06-09
*blank stare*

---

### Post by sydbat on 2010-06-09
I agree that it would be best if you could do a fresh install. Back everything up first, then boot up your LiveCD. In there is the partitioner. Use it to remove the 4 Linux partitions you have. (you can also do this via the installer)

Then, when you go to install, use the manual partitioner to set up a /, /home, and /swap. This way, if you ever bork your system again, or want to change Linux distro, your /home will be unaffected.

---

### Post by 29732 on 2010-06-09
Whoa, whoa, whoa!!!

I just want to do everything with the installer.
Can you make it simple, step-by-step?
Thanks

---

### Post by pizza-is-good on 2010-06-09
> **29732 said:**
> Whoa, whoa, whoa!!!

I just want to do everything with the installer.
Can you make it simple, step-by-step?
Thanks

OK, here we go. Lets do this.

Save any files that you care about(if you have any) to an external drive. If you don't have a LiveCD, make one. Turn off ubuntu. This will be your last time on this particular ubuntu machine. :(

OK, now boot from the CD.
Go to try Ubuntu without installing.

Once in Ubuntu, open up GParted.

Delete
/dev/sda3
/dev/sda5
/dev/sda6
/dev/sda7
/dev/sda8

You do that by selecting each one in the list below the 'graph' of your HDD, right click on each one, and then delete.
Then click on the green check mark above, when you hover over it, it says apply.

Wait for it, it might take a while.

OK, you now have 2 options.

Option 1 - simplest.
You would begin the installation now.

Option 2 - slightly more complicated.
You would create an extra partition, that would be your /home. This way, if you ever had to install again, you could keep all your files. This is what sydbat was saying.

**Option 1** - go to step 2 of Option 2 installation. Skip the step about selecting where to put your /home directory.

**Option 2** - steps 4 & 5 I'm not sure of what order they are in, so watch out. 

1. I don't know how much space is that 'empty' space that you created. This is where you make the decision. I would give 10-15 GB to ubuntu.

Click on the empty area in the graph in GParted, right click, and create new partition. Give it a size that is good enough to leave 10-15 GB for ubuntu. Move the slider to the left to change its size. This will be your personal data or /home folder. The file system should be ext4. It should also say 'Primary Partition'.
Create it. Wait for it to be done.

2. When it is done, close GParted.

3. Click on the install Ubuntu now icon on the desktop.

4. Go through it, when you get to the point where you select the partition, click on the option that says something like 'use the largest continuous amount of empty space'. I believe it is the last one.

5. You'll eventually get to a point where it asks about your /home directory. Tell it to be in the partition you created before.

6. Go through it until it is done.

I hope it is clear enough.

Even if you are installing, you'll still be running the LiveCD, so you can always open up Firefox and ask away here.

Good luck.

~pizza

---

### Post by 29732 on 2010-06-09
Thank you sooo much!!!!! 

I will try that!
:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks
lol 
I'm running Windows right now

---

### Post by pizza-is-good on 2010-06-09
> **29732 said:**
> Thank you sooo much!!!!! 

I will try that!
:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks:ks
lol 
I'm running Windows right now

No problem. Let me know how it goes.

---

### Post by 29732 on 2010-06-09
Instead of making a /home, can't I simply make a FAT32 Partition?

---

### Post by pizza-is-good on 2010-06-10
> **29732 said:**
> Instead of making a /home, can't I simply make a FAT32 Partition?

The only reason you'd do that is to see it in windows. A valid point. The problem with FAT32 is that the biggest file allowed by it is 2^32 -1 bytes, or 4 GB - 1B. So if you ever want to put HD movies or big stuff in it, you won't be able to.

If you want to do that, I'd suggest you format it as NTFS.

I personally don't know what kind of fragmentation problems can occur if you use a windows file system on a linux machine.

---

### Post by sydbat on 2010-06-10
> **pizza-is-good said:**
> The only reason you'd do that is to see it in windows. A valid point. The problem with FAT32 is that the biggest file allowed by it is 2^32 -1 bytes, or 4 GB - 1B. So if you ever want to put HD movies or big stuff in it, you won't be able to.

If you want to do that, I'd suggest you format it as NTFS.

I personally don't know what kind of fragmentation problems can occur if you use a windows file system on a linux machine.Yes, format a shared partition as NTFS, or just mount your Windows partition.

As for fragmentation - you have to go into Windows on a regular basis and run the defrag app. I found (when I still had Windows on my box) that the shared partition started to slow down after a month or so and running the defrag sped things up. 

The other problem was booting back into Windows and finding it took forever (relatively speaking) to get to a usable desktop, all because the share seemed to "corrupt" (for lack of a better word) the way Windows saw it.

---

### Post by 29732 on 2010-06-10
Okay, I'll
 make it a /home, and i'm going to start the reinstall....

Please stay with me, all right?

---

### Post by 29732 on 2010-06-10
It worked!!!!!!!!!!!!
Thankyouthankyouthankyouthankyouthankyouthankyouthankyouthankyou!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by pizza-is-good on 2010-06-10
> **29732 said:**
> It worked!!!!!!!!!!!!
Thankyouthankyouthankyouthankyouthankyouthankyouthankyouthankyou!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Great!

I'm glad you got it working.

~pizza

---

