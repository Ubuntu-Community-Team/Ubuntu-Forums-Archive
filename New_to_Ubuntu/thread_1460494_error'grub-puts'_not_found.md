---
title: "error:'grub-puts' not found"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by MisFitt on 2010-04-22
I have just upgraded Karmic to Lucid,all seemed well until on booting I get
error:'grub-puts' not found and the curser blinks at me and I haven't been able to find how to repair it,yet.
Thanks in advance
(This should be in installations and upgrades I think,sorry)
I dual boot with xp
sda1 is flagged as boot(xp)
sda2 extended has an' lba 'flag and 
sda6 is linux,Lucid,Ext4
I am searching thru' all the posts re MBR problems and nothing comes up when I search for "the symbol 'grub-puts-not found'

---

### Post by cariboo on 2010-04-23
I've never seen that error message before, is there any more to it?

---

### Post by MisFitt on 2010-04-23
> **cariboo907 said:**
> I've never seen that error message before, is there any more to it?

Oh thank you for answering,that can't be good coming from you(staff),wow.
it says:
error:the symbol 'grub_puts_' not found
grub rescue> -(cursor)
 and I have no idea what to type,oh dear

---

### Post by MisFitt on 2010-04-23
Could you please tell me if I could replace/repair the MBR,any links that I could understand,step by step?
I'm at a loss here,no Google references nor forum posts so far that aren't too highly technical.

---

### Post by MisFitt on 2010-04-23
> **MisFitt said:**
> Could you please tell me if I could replace/repair the Grub,any links that I could understand,step by step?
I'm at a loss here,no Google references nor forum posts so far that aren't too highly technical.

It's now the next morning and I cannot boot into anything but the Live disk.
My windows and karmic which I installed back to the Ubuntu partition are otherwise inaccessible and I can't follow the notes I took as I sought answers,trying different fixes I found on various posts and google.
I have only the one machine at the moment.
Fortunately everything I need is backed up safely on an external hard disk but that's not the point.I know my system could be fixed.
There are big gaps in what I know and what I can do.
I'm going to delete both partitions and install XP and Jaunty again,64 bit.It was stable,for me anyway.
Anyway,I'm disheartenned by my experience of the last few weeks.I've spent more time fixing and trying to fix than using it for what I bought it for,video production.
I'm venting in my own post because I REALLY need to.

---

### Post by xumuk37 on 2010-04-23
you can load the kernel manually if you know that it's there for true...
```
grub rescue>root=/dev/sdX # with /boot partition
grub rescue>linux(or kernel depends of your grub version) kernel_image_name.img
```

don't forget to use <tab> to can see available options...

you always can boot windows reinstalling grub from Live CD, it makes update and auto-detects windows partitions...

---

### Post by MisFitt on 2010-04-23
OK,thankyou for that,that goes in the notebook for sure.
Unfortunately I went ahead and deleted both partitions to get a new start.Then,as I was installing xp it wouldn't boot back into the dvd during install so I tried 4 times,tried installing Jaunty(my dvd burner chose today to die)BUT I found one disk that would install,karmic(which has had 3 kernel crash alerts thus far btw)so that's what I'll live with until I get a new dvd burner.

"don't forget to use <tab> to can see available options...

you always can boot windows reinstalling grub from Live CD, it makes update and auto-detects windows partitions..."
I don't understand how you can boot windows using the live cd and what does "it makes update" mean?
Thanks for your help,truly appreciated
(for my future reference:[http://www.uluga.ubuntuforums.org/showthread.php?t=1443763](http://www.uluga.ubuntuforums.org/showthread.php?t=1443763))
and
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by ajnueva on 2010-04-30
Oh, my God!

I upgraded to 10.04 from 9.10 yesterday the 29th of april, and it happened the same to me!

I have GRUB2, and 2 physical HDs installed:

- the fist HD was the original of my PC, with Windows Vista. It's named sda, and has 2 partitions: sda1 (Vista), sda2 (Vista recovery)

- the second HD is sdb, with 4 partition I created months ago, when I installed 9.10. These partitions are: sdb1 (/), sdb2 (swap), sdb3 (/home), sdb 4(fat32)

I remind there was a question the system made my during the upgrade... To be honest, I didn't understand it properly. The system asked my something (I don't really remember) related to the partitions. I had to choose: sda, sda1, sda2, sdb, sdb1, sdb2, sdb3 or sdb4. I finally chose both sda1 and sdb1, and nothing else. I presume my problem comes from here. How can I fixed it? Help!!!!

---

### Post by seadart on 2010-04-30
I have exactly the same problem. I have/had Windows 7 on first partition, a very small spare bit then Ubuntu 9.10. after that was the scratch file for Ubuntu and another spare bit. On upgrade I had a funny message about unable to complete network upgrade but it continued anyway. At the end was the message about where to put Grub. First choice was use my local version - I assumed this was to do with the dual boot so I choose that. Then the list of where to put Grub, even though I thought the first question meant leave it alone! I chose the third partition thinking this was Ubuntu.
On boot I get Symbol Grub_Puts not found etc.
Yes all is backed up frequently on second hard drive and less often to external. Data is on second hard drive.
If I make a live cd of 10.04 will that be able to fix Grub?
I have a second computer.

---

### Post by fkrull on 2010-04-30
I've got exactly the same problem and I've got Windows 7 with two harddisks, too.

---

### Post by fkrull on 2010-04-30
Here's what helped me to start the system: I apparently installed grub on the wrong harddisk. I just pressed F8 during the bios startup and selected the other harddisk to start from. The system started and I could install grub on the other disk.

I hope this helps in your case, too.

---

### Post by DrewT on 2010-04-30
Well this is certainly the worst upgrade experience I've had since coming to Ubuntu/Linux a couple years ago.

I have no Windows (or other non-Ubuntu) installation on my system (except in Virtual Box, which I'm sure doesn't matter for Grub purposes!). I do have two hard drives -- a 250G with an old Ubuntu installation (probably 9.04), and a 1000G with 9.10. During the upgrade to 10.4, I was asked to select the disk/partition to install Grub. The correct answer, of course, is I wanted it installed where it already is. No clues were offered as where that might be. Indeed there was no indication of which hard drive was which -- just a list of partitions. But it seemed that I could only select one option (clicking in the others did nothing), so I went with it. And now I can't boot (I'm getting the error described in this thread). Nor can I find an intelligible explanation of how to fix the problem. I have tried reinstalling Grub from the Live CD -- to various partitions -- and all fail (instantly and fatally). I've tried booting from the other drive, but all I get is a blinking cursor -- not even a prompt.

I hope somebody comes up with a solution to this soon, since I'm supposed to be working.

---

### Post by DrewT on 2010-04-30
The closest thing to a fix I've found so far is on this page: <http://grub.enbug.org/Grub2LiveCdInstallGuide> . Unfortunately I can't get past the eighth listed command because the shell environment on the 10.4 Live CD doesn't include the grub-mkconfig command (or apt-get), and I don't see any way to start a more complete shell. I might get around these problems by starting a shell in the boot partition (sda1), but I don't know enough about all these mount commands to feel safe in that setting. (In fact I don't feel safe running these commands in the installer shell.)

---

### Post by DrewT on 2010-04-30
Okay, now *this* is embarrassing. It seems that I downloaded and installed the wrong disk image -- server instead of desktop. (I guess that's why it wanted to download another 800+ megs of files during the install process.) I have no idea whether this is implicated in the grub problem, but I'm now downloading the correct image and crossing my fingers very hard that installing the desktop will restore everything to normal.

---

### Post by kennystoy on 2010-04-30
I have the same error message from upgrading from 9.10 to lucid .  
I just recently went from xp to ubuntu , 2 weeks ago.
I know very little about ubuntu , so I really need help , but in laymans terms.

---

### Post by Chronon on 2010-04-30
I successfully used this guide to fix this problem:
[http://grub.enbug.org/Grub2LiveCdInstallGuide](http://grub.enbug.org/Grub2LiveCdInstallGuide)

---

### Post by Chronon on 2010-04-30
> **DrewT said:**
> The closest thing to a fix I've found so far is on this page: <http://grub.enbug.org/Grub2LiveCdInstallGuide> . Unfortunately I can't get past the eighth listed command because the shell environment on the 10.4 Live CD doesn't include the grub-mkconfig command (or apt-get), and I don't see any way to start a more complete shell. I might get around these problems by starting a shell in the boot partition (sda1), but I don't know enough about all these mount commands to feel safe in that setting. (In fact I don't feel safe running these commands in the installer shell.)

I used a 9.10 Zenix (Ubuntu spin) LiveCD to do the fix and it had the grub-mkconfig program already installed.

---

### Post by nirdo on 2010-05-02
> **Chronon said:**
> I successfully used this guide to fix this problem:
[http://grub.enbug.org/Grub2LiveCdInstallGuide](http://grub.enbug.org/Grub2LiveCdInstallGuide)

Thanks! This guide worked out for me.

I too have a dual boot system with Win XP, and upgraded from 9.10 to 10.04. each one running on a separate HD.
The problem may have been related to installing GRUB on the wrong drive during the upgrade script. I remember the upgrade showing a list of partitions for grub to boot automatically, where I selected my Linux partition. Maybe I should have selected the other drive which is where my MBR resides

---

### Post by MisFitt on 2010-05-02
Hey Drew,sorry to hear that.
Have you begun your own thread?
I'm struggling myself but I did muddle thru' as you can see.
I'm sorry you guys showed up while I was away.
I'm still in trouble,needing to reinstall all over and taking OUT a possibly dodgy hard drive to start over as my xp is still useless.
Thanks for the links,I'm in the same boat so will be watching everyone's progress closely.
So,clearly I'm not the only one and I HAVE TO get this done right.

---

### Post by MisFitt on 2010-05-02
> **Chronon said:**
> I successfully used this guide to fix this problem:
[http://grub.enbug.org/Grub2LiveCdInstallGuide](http://grub.enbug.org/Grub2LiveCdInstallGuide)
That is fantastic information,thank you!

---

### Post by Trifidlebock on 2010-05-03
I had the same problem when upgrading 9.10.  All I did was use the Ubuntu cd to run rescue mode.  I selected my root partition when prompted.  Then, I choose the reinstall grub option.  After I rebooted it worked like a charm.

I hope that saves time for some people.

---

### Post by tstduke on 2010-05-07
The solution found at:
[http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)
Worked perfectly for me. I have a dual boot system with XP and 3 hard drives with multiple partitions on each.

---

### Post by MisFitt on 2010-05-09
> **tstduke said:**
> The solution found at:
[http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)
Worked perfectly for me. I have a dual boot system with XP and 3 hard drives with multiple partitions on each.
Thankyou so much for the link,goes in my book.
So everything's cool for you now?

---

### Post by kigango123 on 2010-05-09
> **tstduke said:**
> The solution found at:
[http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)
Worked perfectly for me. I have a dual boot system with XP and 3 hard drives with multiple partitions on each.

Solution worked perfectly

---

### Post by MisFitt on 2010-05-09
> **fkrull said:**
> I've got exactly the same problem and I've got Windows 7 with two harddisks, too.
YEAH,good one,SOLVED!

---

### Post by sallymc on 2010-05-14
I CAN HELP!  Have just had the exact problem, and fixed it.  Go to :

 ['alexandre ***jelly kernel***' french karmic]("http://www.google.com/search?hl=en&ei=Dg3tS8XnEqHYmwPSzq2qDg&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CBEQBSgA&q=%27alexandre+jelly+kernel%27+french+karmic&spell=1")

 on Google.  The first article is : 
**[Fix Symbol 'grub_puts'  Not Found When Migrating From  Ubuntu *Karmic*]("http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html")**

Follow his instructions and you will be delighted.  By the way, you will  need a second working computer in order to access these instuctions,  and a live Ubuntu CD to boot from.
Note that his first instruction :  
sudo fdisk-l

has a space after fdisk, before the dash.

Good luck and keep smiling.  I LOVE UBUNTU.

:smile: Sallymc

---

### Post by anthony.cirelli on 2010-05-14
sorry if I insult devote fans of ubuntu here, but I have this same error come up, during installation there was something written in poor grammar about "grub" and installing it on the boot partition, then this error happens.... I think it was very "Microsoft" of them to release a buggy upgrade and screw up the os load. Shame on them..... I'm calling this the new Microsoft Ubuntu 10.4:mad:

---

### Post by anthony.cirelli on 2010-05-14
if someone is having problems with the live cd not recognizing commands like chroot and apt-get for some stupid reason, I found out that if after the "/mnt" business, running this command fixed the error on my machine:

sudo grub-install --root-directory=/mnt --recheck /dev/sda

some other error flashed up briefly on reboot, but the system got past it and then loaded ubuntu 10.4 fine....

---

### Post by swan14 on 2010-05-18
Hi I have this problem too but having issues with the linked fixes.

When it says boot using a live cd does it have to be 10.04?

Also to bring up the terminal do I boot the system - i.e. the option that says "try ubuntu without making changes to my computer".

Any ideas?

When updating to Lucid I thought I chose the correct partition for Grub but apparently not.

Sam

---

### Post by swan14 on 2010-05-18
> **anthony.cirelli said:**
> if someone is having problems with the live cd not recognizing commands like chroot and apt-get for some stupid reason, I found out that if after the "/mnt" business, running this command fixed the error on my machine:

**sudo grub-install --root-directory=/mnt --recheck /dev/sda**

some other error flashed up briefly on reboot, but the system got past it and then loaded ubuntu 10.4 fine....

Ok after a fair bit of trial and error this command seemed to get the job done.

No probs now

---

### Post by pavel protin on 2010-11-02
in case it is of help to someone:

i had the same problem (with ubuntu as sole OS on a macbook air), and tried to solve it with the aforementioned [http://www.webupd8.org/2010/05/fix-s...ound-when.html]("http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html")

however, when it came to the last command ("grub-install /dev/sda"), i got a long message on the screen, telling me that this would be a BAD IDEA (yes, in caps). i had to force it (as in: "grub-install /dev/sda --force"). 

why i tell you this? - to let you know that "--force" seems not to have produced any bad side-effects.

have a nice day.

---

### Post by Crowbeach on 2011-01-25
I too encountered the same issue when upgrading from Karmic to Lucid. I read all of the previous posts on this thread but it was only after much gnashing of teeth and hurling of epithets that I finally got past this. It's interesting how everyone's situation is just a little bit different. I'm therefore posting mine in the hopes that it helps someone else down the road.

My scenario was a standalone system with a single O/S (Karmic, server edition) installed on it. I had three hard drives in total: one IDE that was the first and primary boot disk (enforced in the BIOS after a similar boot fiasco with the LAST upgrade I did) and two SATA drives that I had ganged together into a RAID1 configuration. The primary disk had been partitioned automatically by a previous installation of Ubuntu and contained a small (256MB) partition that mounted as /boot along with another partition containing the Linux software itself that mounted as root (there was a third partition that just looks like an extension, as it overlapped the boot partition). The disks in the RAID volume just contained data.

When upgrading to Lucid (for which I had to configure release-upgrades to Prompt=normal, using Prompt=lts did not work for some reason) I received the same question about which partition to install Grub2 onto. I actually chose the *correct* drive that already had Grub2 installed from Karmic - the primary IDE one - and avoided the "boot record" partition, but still got the incredibly helpful "the symbol grub_puts_ not found" error when the system rebooted after the upgrade.

I found that I was able to boot my system from the normal Ubuntu installation CD (Lucid server edition, 32 bit) by just selecting the "Boot from primary hard drive" or some such option. An error message about "disk not found" flashed up but otherwise I was in. What I found was that when I booted with the CD, my primary hard drive showed up as sda, which was mapped to hd0 via /boot/grub/device.map. Without the CD, running "ls" from the grub rescue prompt reported the primary hard drive as being hd2. I tried various ways to resolve the discrepancy but to no avail. The output from the boot info script was useful but did not fully explain why the problem was occurring. 

I could speculate that the "boot partition" grub was overriding the MBR grub - but who knows. At any rate, I finally did resolve the situation as follows:

[LIST=1]
[*]Booted the system via the CD as described above
[*]Completely removed grub2 via "sudo aptitude remove grub-pc grub-common" (I also added grub and grub2 to the list just to be sure)
[*]Renamed /boot/grub to /boot/grub.old so that the old config files would not get picked up
[*]Reinstalled as "sudo aptitude install grub2"
[*]When prompted I installed grub on ALL 3 disks but NOT the boot partition
[*]After the install ran "sudo update-grub" just to be pedantic about it
[*]Rebooted. 
[/LIST]
The screen still flashes "error: disk not found" shortly after loading grub but at least now it boots. Perhaps the boot partition is overriding the MBR, and that the "blocklist" warning means it is trying to load core.img from a hard-coded sector on the drive that no longer points to the file. Again, who knows. Since a separate boot partition no longer seems to be recommended I'm considering blowing it away and doing a full install again... Probably for the NEXT upgrade.

Speaking of which, this is my fourth upgrade of Ubuntu (I started with Dapper a number of years ago) and I have to say that not ONE upgrade has ever gone smoothly or as documented. After the first experience I tried to stick to LTS releases only but that obviously hasn't helped much. For Karmic I ended up with a complete reinstall rather than an upgrade because it just got too painful. My system really couldn't be much simpler, so it begs the question as to why it continues to be so difficult to upgrade Ubuntu time after time.

---

