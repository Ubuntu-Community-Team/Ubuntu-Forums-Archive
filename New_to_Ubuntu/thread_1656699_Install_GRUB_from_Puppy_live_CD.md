---
title: "Install GRUB from Puppy live CD"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-12-31
OK I had some major problems with one of our library computers so I used a puppy live CD to reformat swap and /partitions 5 set them to ext4. I couldn't get any Ubuntu CD to work live or install. I still can only boot using the live puppy CD. I think I now need to install GRUB or GRUB2? But I can't figure out how to do that from the puppy CD even Knoppix won't load from CD. Please give some beginner instructions. I think step one is mounting the / which is the whole Drive except for the 3GB swap.After that I am lost. The GRUB directions page says to download the files from Ubuntu CD but that I can't do only puppy will load thank you

---

### Post by QLee on 2010-12-31
> **cmcanulty said:**
> OK I had some major problems with one of our library computers so I used a puppy live CD to reformat swap and /partitions 5 set them to ext4. I couldn't get any Ubuntu CD to work live or install. I still can only boot using the live puppy CD. I think I now need to install GRUB or GRUB2? But I can't figure out how to do that from the puppy CD even Knoppix won't load from CD. Please give some beginner instructions. I think step one is mounting the / which is the whole Drive except for the 3GB swap.After that I am lost. The GRUB directions page says to download the files from Ubuntu CD but that I can't do only puppy will load thank you

Well, if you've formatted the partitions, there won't be an operating system to boot to, so installing GRUB to the MBR isn't going help you much and you'd have no place to point it to look for the next stage and menu. If you can't get the Ubuntu live CD to work, could you download and try the Alternate CD for installation?

[Edit] Or maybe figure out why the live CD isn't booting.

---

### Post by cmcanulty on 2010-12-31
OK I'll try that wouldn't there be a way from within puppy to set it up I can connect to web in puppy, thanks

---

### Post by Rubi1200 on 2010-12-31
I believe Puppy uses GRUB, so on that account you could theoretically use it to install/reinstall GRUB.

You also need to know if it is using GRUB2 or GRUB-legacy.

From the command line on Puppy, run this to find the version:
```
grub-install -v
```But, of course, QLee is right about the point of doing this (only makes sense if there is something there for GRUB to boot).

If you can get access to the Internet on Puppy, I suggest you download and run the boot info script linked at the bottom of my post.

Get the results back to us so we have a better idea of what we are dealing with.

Thanks.

---

### Post by cmcanulty on 2010-12-31
ok thanks will try that I work again at lib Mon eve so no news until then
I run the tech there but am a volunteer.

---

### Post by QLee on 2010-12-31
[QUOTE=Rubi1200]...
If you can get access to the Internet on Puppy, I suggest you download and run the boot info script linked at the bottom of my post.

Get the results back to us so we have a better idea of what we are dealing with.[/QUOTE]

With all due respect, Rubi1200, and I truly do respect your work, I've read a lot of your posts. The only two partitions on the drive have been formatted according to the first post. I don't think the boot info script would give us any useful information at this point. It's just going to tell us where the MBR is looking for the non-existing /boot. We would likely be better off discovering why the live CD can't boot because we'll need some install CD for Ubuntu.


[Edit] 
@ cmcanulty It might help somewhat to tell what the major problems were that caused you to reformat so we could determine if it was a hardware problem or a software problem. Also detail what errors you have booting live CD.

And one more question for you, because it isn't clear to me from the context of your OP. You didn't format the swap partition as ext4, did you? You referred to "them".

---

### Post by Rubi1200 on 2010-12-31
> **QLee said:**
> With all due respect, Rubi1200, and I truly do respect your work, I've read a lot of your posts. The only two partitions on the drive have been formatted according to the first post. I don't think the boot info script would give us any useful information at this point. It's just going to tell us where the MBR is looking for the non-existing /boot. We would likely be better off discovering why the live CD can't boot because we'll need some install CD for Ubuntu.

QLee, one of the things that makes this community so special is the fact that we all help each other, in whatever way possible.

I respect and value your input (I have also read a lot of your posts too).

I tend to be rather cautious when it comes to these types of situations because, not that this is the case here, I have seen posts where the user said "well, I *only* did this or that" and the results of the script showed a completely different picture.

I do agree that we need to find out why the LiveCD is not working at this point.

Perhaps, if the thread starter feels comfortable doing so, it would be worthwhile trying the Alternate CD?

Best regards.

@cmcanulty: I think it would also be helpful if you could post the specifications for the computer in question.

---

### Post by cmcanulty on 2010-12-31
The problem was it would stick on the screen saying press this for boot or this for config? and a restart would get it going then it wouldn't go past that screen at all this week.So now I have a swap at 3GB and a ext4 partition at 70+GB but no way to boot except with live puppy CD. I am home as lib is closed for holiday until mon I will post that mon eve when I work again thank you.I guess I can't just copy a grub file to the ext /partition?

---

### Post by QLee on 2011-01-03
Thought I'd add this so it will be fresh in your mind when you get to the library.

[QUOTE=cmcanulty]The problem was it would stick on the screen saying press this for boot or this for config? and a restart would get it going then it wouldn't go past that screen at all this week.[/QUOTE]

Well, that all happens before trying to boot Ubuntu. Those are the steps before the system tries to boot the first boot device that is optioned in the BIOS. From your description, if you mean locks-up on that screen then it sounds like a hardware problem. However, if it locks up on that screen then it couldn't boot the Puppy CD either. You're providing incompatible pieces of information.

[QUOTE=cmcanulty]So now I have a swap at 3GB and a ext4 partition at 70+GB but no way to boot except with live puppy CD.[/QUOTE]

Did you actually format them as you said in first post? If you did, as I mentioned, then there is nothing to boot to on freshly formatted partitions. Formatting is destructive, wipes out the data that was previously on the partitions. 

[QUOTE=cmcanulty] I am home as lib is closed for holiday until mon I will post that mon eve when I work again thank you.I guess I can't just copy a grub file to the ext /partition?[/QUOTE]

You could copy anything you want to the / partition but copying some unspecified grub file there wouldn't be useful. GRUB2, which you will want to use, is much more than one file and if you have formatted the partition there is nothing left for GRUB to boot.

If you formatted, you're going to have to reinstall, I fear you don't have a backup since you haven't mentioned it, so we need to figure out why the Ubuntu live CD isn't booting. Tell us what happens when you try to boot the Ubuntu live CD, describe it in words for someone who is not sitting in front of the computer and can't see what is happening.

---

### Post by cmcanulty on 2011-01-03
OK as I said first the Ubuntu install freezes on the first forward option whether I click install from CD or use live and then install from desktop icon. The puppy live CD runs fine. It seems that if I can run puppy live there ought to be a way to install Ubuntu from the live puppy CD but maybe not. I don't care about backup this is a public library computer and I just set up home page and a few addons and settings.I am going to start working on it at 330pm ET as soon as I get there. Thanks for all this advice. I reformatted because I read several times the way to completely fix a partition was to boot from live CD unmount partition and reformat then reinstall obviously I missed some major point. I study a lot but don't always get it correct.I run 8 Ubuntu Maverick public computers and 5 windows for office and librarians but I am a volunteer. One cool thing is next month we are changing to Evergreen open source library software.

---

### Post by QLee on 2011-01-03
[QUOTE=cmcanulty]OK as I said first the Ubuntu install freezes on the first forward option whether I click install from CD or use live and then install from desktop icon. [/QUOTE]

This is the first time you have described it that way. Now I understand what you are seeing. It's not as you described previously.

So the Ubuntu live CD does boot and gets to the desktop but actually fails when you select "install" from the desktop option. It also fails when you try to go directly to install from the live CD boot menu. 

[QUOTE=cmcanulty]The puppy live CD runs fine. It seems that if I can run puppy live there ought to be a way to install Ubuntu from the live puppy CD but maybe not.[/QUOTE]

The Puppy live CD does not have the files necessary for an Ubuntu install, though it probably does have a way to install Puppy.  

[QUOTE=cmcanulty]I don't care about backup this is a public library computer and I just set up home page and a few addons and settings.[/QUOTE]

A system backup would be able to restore to the formatted partition and you would already be back up and running after changing GRUB and fstab to the new UUID string (that happened when you formatted), if there is nothing wrong with your hardware.

[QUOTE=cmcanulty]I am going to start working on it at 330pm ET as soon as I get there. Thanks for all this advice. I reformatted because I read several times the way to completely fix a partition was to boot from live CD unmount partition and reformat then reinstall obviously I missed some major point. [/QUOTE] 

This is more of a Windows operating system mindset to reformat and reinstall. Rarely does a "partition" need fixing and rarely does a GNU/Linux system need reinstalling to fix something. It takes a massive mistake to get things so far messed up that they can't be fixed.

How did you determine the partition needed fixing, was there some error message, it might help us to understand what is going on with your system. Is there a chance the hard drive is failing? Is it finding too many bad sectors or something?

There is nothing wrong with you not knowing everything yet, that's why Rubi1200 and I and the others, who are just watching, are here, we're going to help you do it.

---

### Post by Rubi1200 on 2011-01-03
As QLee already said, there is nothing wrong with not knowing everything. Linux has a learning curve, but we are here to help.

What we really need to know, now that you have described some of the issues in more detail, are the _full_ specifications for the computers in question.

Sometimes, not always, issues with freezing can be attributed to not enough memory or a graphics card that has issues.

Please post this information for us to help you troubleshoot this further.

Thanks.

---

### Post by cmcanulty on 2011-01-03
I will post specs when I get there but this was a sudden change from working fine to not booting at all and I made it worse by formatting /

---

### Post by cmcanulty on 2011-01-03
OK I can still mount puupy but the alternate Ubuntu CD won't boot or the normal ubuntu. I try to install puppy but it won't let me unmount sda1 to do it. The specs are CPU Intel Premium 4 2.6GHz 512 RAM it shows OS as Kernel Linux 2.6.33.2 of course that is just the Puppy mounted CD version Lupu 511 ATA Maxtor 6Y080LO Hard Drive I don't know what else you need.The grub-install -v command gives GNU GRUB 0.97 The above boot script gives command not found
Or hold on I tried tons of live CDs but currently it seems like an old Xbuntu 9.10 version is starting hold on for further developments!Oh well it crashed again
I can get a new alternate CD of Ubuntu 10.10 go to openiing screen where you pick language but it freezes there.

Further info now I have the puppy CD in and it is letting me format partitions so hopefully after that I can install Ubuntu. I am setting 20GB as /sda1 ext4  52GB as /Home  ext4 and 3GB as swap

---

### Post by migs73 on 2011-01-03
I would use puppy to check the HDD for errors, one of the reasons it boots and the others don't could be that it runs from RAM and does not require an HDD at all. 

Just a suggestion.

Mike

---

### Post by cmcanulty on 2011-01-03
OK I have the partitions set up and puppy installed but everything is different on it how can I run disk check? Still can't boot from Ubuntu CD can I install Ubuntu from console in puppy? To clarify I installed puppy to hard drive at least I think so that was the option I picked.

---

### Post by migs73 on 2011-01-04
> **migs73 said:**
> I would use puppy to check the HDD for errors, one of the reasons it boots and the others don't could be that it runs from RAM and does not require an HDD at all. 

Just a suggestion.

Mike

I shouldn't try to be helpful just before bedtime!!! What I had said is not true!!! Even Ubuntu should run from a live CD without an HDD. The only difference is once booted you can remove the CD for puppy as it is all in RAM.

Anyway still would be a good idea to check the disk from puppy since you can boot to it.

I don't know what the code required would be, only just started playing with puppy myself, but puppy does have fsck, so you could try this (**if any one else agrees!!**):

```
fsck -yv /dev/sda?
```

Change the 'sda?' to the correct identifier for your hard drive/partition.
y means autofix and v means verbose, so you can see what it is upto.

**Please wait till there is confirmation of this command, I know your system is bare but I wouldn't like to cause any damage!!!**

---

### Post by QLee on 2011-01-04
cmcanulty,

I'm sorry, but the timeslice you need to work on this is much later than I am usually here, perhaps it is the same for Rubi1200 or maybe Rubi1200 is still waiting for the answers to some questions, I can only speak for myself.


It would probably be a good idea to slow down, not just start trying everything you can think of. Both Rubi1200 and I asked you questions because we wanted to make a diagnosis of what might be wrong before we advised you how to proceed. It usually is fairly important to figure out what the problem is before trying to fix it. Instead you kept trying things, and continued telling us things did work, then they didn't work, then this worked, then it didn't and then you installed Puppy. I thought our goal was to get Ubuntu back. When we are inexperienced, and you said you are, it is usually a mistake to rush, it often gets us in worse shape if we don't consider and understand what our actions are going to do.

As I have mentioned, we need to be able to get the Ubuntu CD to boot so we can install Ubuntu. If we can't get it to boot, or to continue with the install once it has booted, we need to figure out why.

Rubi1200 asked for the *full* specifications of the computer. And explained that was to determine if perhaps a memory issue or a video card issue was getting in the way. 

Rubi1200 also asked for the results of running the boot info script, [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) And you replied that you would try that when you were at work on Monday.

I asked, "How did you determine the partition needed fixing, was there some error message, it might help us to understand what is going on with your system. Is there a chance the hard drive is failing? Is it finding too many bad sectors or something?"

Probably the first thing I would have tried once I got a CD to boot would have been run a memtest check, (Test Memory from the live CD boot menu) because a couple of successful passes of that would probably mean the mem and basic systems were OK. Not guaranteed but probably OK. Once booted to the live desktop, I probably would have opened GParted to see what it had to say about the hard drive. And/or I might have opened the Disk Utility to see if the drive was SMART capable, if it was I would have the SMART data to look at.

All of this would have been with the intention of getting more data about the issue, trying to figure out possible causes for the symptoms seen. Trying to figure out the problem so it might be possible to determine the fix.

However, the bottom line is, in order to reinstall Ubuntu to the system we have to determine why the Ubuntu CD will not continue the install once it boots.

---

### Post by cmcanulty on 2011-01-04
I posted all the specs I could find from puppy and got the 2 partitions formatted and both will mount now. I am not sure how to do other things in puppy  I did try the tests you mentioned but all came back with command not found.I also tried the alternate install CD with no luck.I wonder now if knoppix will work as I think it is debian based and puppy is not. Knoppix is a lot easier to work with. I work again Thurs starting at noon. Sorry to be so mixed up the trouble is when I'm there I have such limited time.

---

### Post by Rubi1200 on 2011-01-04
Let's slow this down a bit.

Knoppix is a great suggestion, so I recommend you download and prepare it so we can get some things done.

When you are back at work, use Knoppix to boot the computer and then go to the terminal.

What I would like for you to do is run the following commands in the terminal and post the output back here so we can try and troubleshoot this for you.

```
lspci | grep VGA

free -m

sudo parted -l
```

EDIT: if you already have a Knoppix CD available let me know before Thursday which version please.

---

### Post by QLee on 2011-01-04
[QUOTE=cmcanulty]... Sorry to be so mixed up the trouble is when I'm there I have such limited time.[/QUOTE]

This frustration is not your friend, it and the rush it fosters is counter-productive.

Let's slow down and put Rubi1200 in control of the issue. Do only what is suggested and answer all questions and do not do anything else on your own, especially if it is because you think you can fix it now. Most of all, try to relax and be patient, there is considerable to learn through the process that can make you a better troubleshooter. I trust Rubi1200, I hope you can too. Troubleshooting can often work best if one troubleshooter is in charge and leading so your efforts are not scattered and confusing.

---

### Post by cmcanulty on 2011-01-04
OK will do by 1pm Thurs I will post as soon as I get info thank you.

---

### Post by cmcanulty on 2011-01-06
I got Xubuntu 9.04 to install and created separate boot and home partitions. For some reason that CD worked. now I am upgrading to Xubuntu 10.04 then hopefully to 10.10. I tried several Ubuntu CDs with no luck. Is there a way to get back to Ubuntu without doing it from a CD.Until 2 weeks ago this computer ran 10.10 Ubuntu with no problem.I will be at library until 7pm thank you.

---

### Post by Rubi1200 on 2011-01-06
Well it seems you found a solution, sort of...

I have used Xubuntu (and rather liked it), but do not know if there is an option to install other desktop environments.

I do wonder why you are creating a separate /boot partition?

It is, in most cases, quite unnecessary for desktop computers.

If I find more information, I will let you know.

One last thing, since you now have a working installation, it would still be helpful if you could post the results of the commands we asked for previously.

---

### Post by cmcanulty on 2011-01-06
I always put the OS on a separate partition from home to make upgrades or reinstalls easier though I guess it can also allow some problems to be carried over.OK will do even though I am now finishing up an installation of Xubuntu 10.04 then I will upgrade to 10.10 and also post those commands. It is so weird that I couldn't still get a Ubuntu CD to be booted I tried 9.04 up to 10.10. So I started with Puppy installed that to HD then went to knoppix and then Xubuntu. I remember a while back I had a similar situation on a real old computer that was also fine that died and the only way I could get it back up was start with a real old version and work my way up.The 10.04 should be done in a few minutes and I will then post the commands you gave me. Thank you.

---

### Post by cmcanulty on 2011-01-06
Here are the results as I said the boot script came back with command not recognized but now that I am somewhat recovered I guess the issue is why won't the Ubuntu CDs work. I tested them on other machines and they work fine
```

librarian@4:~$ lspci | grep VGA
02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
librarian@4:~$ 
librarian@4:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           496        399         97          0         84        142
-/+ buffers/cache:        171        324
Swap:         3153          0       3153
librarian@4:~$ 
librarian@4:~$ sudo parted -l
[sudo] password for librarian: 
sudo parted -l

```

---

### Post by cmcanulty on 2011-01-06
I got it up to xubuntu 10.10 then removed Xubuntu and got ubuntu bACK so solved don't know why it was such a mess but thanks all

---

### Post by Rubi1200 on 2011-01-07
Perseverance usually pays off :-)

This is an important learning experience and I hope that you will be able to use some of the tips and tricks we shared with you if this happens again.

---

