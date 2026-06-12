---
title: "Is there a stable Ubuntu that is effectively supported?"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by Franknfurterhotmale on 2010-05-11
I had distro 8 on a dual boot with XP but the Ubuntu hard drive failed so I downloaded 10.04 and installed it. After wasting hours on it trying to make the sound work and see if it will run for five minutes without freezing I discover it's no better than a beta.
So I tried 9.10.
That installed without putting an entry in any boot sector- so I had a linux file structure on one hard drive but no way of booting it.
Now I'm trying 9.04. That installed fine and boots properly, unfortunately the download speed for the proprietary nvidia drivers is 4KB/sec which gave an estimated delivery time of 3+ hours. After half an hour the program reported a fatal fault and stopped. I accepted the option to try again the program has been hanging for ten minutes. 
While the add-remove program is running (or hanging) no other program will run.
I used to be a fan of Ubuntu but now the OS are decidedly flakey, are much more difficult to manage than they were when I knew nothing about it, and the software server is delivering data a little bit slower than a telephone modem.
When installing all the above Ubuntu distros the install program spent hours at various points in the install sequence, I suspect trying to download data from a server and then giving up.
Is there a stable version that is supported by a server that can supply the update and install data?

Frank

---

### Post by Grenage on 2010-05-11
I would stick to 10.04, instability/crashes point more towards hardware issues.

---

### Post by Zintha on 2010-05-11
> **Grenage said:**
> I would stick to 10.04, instability/crashes point more towards hardware issues.
10.04 has had very few issues from me. Consistant crashes/issues with multiple versions suggests hardware, not software, problems. 

So i'd agree with Grenage on this one.

---

### Post by Tony Flury on 2010-05-11
> **Zintha said:**
> 10.04 has had very few issues from me. Consistant crashes/issues with multiple versions suggests hardware, not software, problems. 

So i'd agree with Grenage on this one.

Not running 10.04 (still on 8.04 for other reasons) but sounds like hardware to me.

Might be worth doing a memory check from the Grub menu.

---

### Post by gandaran on 2010-05-11
hi,
I had a lot of problems with 9.10 and 10.04 that just refused to work on my new laptop, I did a bios update and now any new version of linux works smoothly, could be your case too!

---

### Post by Franknfurterhotmale on 2010-05-11
OK,
I'll give 10.04 another go.
My freezes always happen when it is trying to download updates.
My hardware is not new but it's not bad, maybe it can't work that slowly.

Frank

Athlon 64 dual core 4000+
3GB RAM
Creative Audigy II
GeForce 7600 GS
ALive SATA2-GLAN motherboard
SIS 900 network card- not supported by Win 7 but supported natively by Ubuntu and Win XP
Ubuntu running on a SATA drive

---

### Post by Grenage on 2010-05-11
Those specs are decent.  As has already been mentioned, it can't hurt to run a memory test.

---

### Post by LOIREE on 2010-05-11
I'd say 9.04 is best, as more or less modern, yet the most stable. 9.10 is buggy. 10.04 is hell. But then, and I'm risking now to get fired upon with rotten tomatoes, I use Xubuntu, since is smaller and faster.... ;)

---

### Post by 3rdalbum on 2010-05-11
You know, there's more than one Ubuntu server. Go to the Software Sources panel to try a different server in your country, or click the "select best server" button to have it done for you.

---

### Post by perham on 2010-05-11
the funny thing about 10.04 is that since it comes with grub 2, there's no option for not letting ubuntu ruin the mbr. I'm having grub 2 on my pc, and I don't have problems, but everyone who I offered a convert to ubuntu, comes back to me, and makes me fix his now broken pc because grub 2 had been installed where it should not be. I still don't get what was wrong with grub legacy that they replaced it with grub 2. grub legacy can be installed on a partition instead of the mbr, can be configured in a much easier way, and it could stay that way. in fact, the grub legacy version which came with 9.04 is now nowhere to be found. grub package installs a vanilla version of grub legacy which does not contain uuid and find --set-root commands and it does not read ext4 partitions. it's a pitty that they left developing such a great and stable program for a new, buggy and heavy one with less practical usability and more fairytale features.

---

### Post by philinux on 2010-05-11
> **Franknfurterhotmale said:**
> OK,
I'll give 10.04 another go.
My freezes always happen when it is trying to download updates.


Is this wired or wireless, if wireless I would give wired a go.

---

### Post by Franknfurterhotmale on 2010-05-11
Using the same cd which I downloaded the iso for three days ago and burned and verified using my iMac I have booted the pc four times.
On none of those was I given the option to run a memory test like previous distros I've used, and while the first two installs were flakey, it actually installed.
Attempt 3 was reporting "93% configuring hardware" when I returned to it four hours after I started and in attempt 4 running off the disk the terminal does not recognise the command memtest. 
Previous versions of Ubuntu work fine as VMs on both my iMac and the pc that 10.4 won't load on.
I know VMs talk to the hardware through the host machine, so running 10.4 as a vm is an option, but life's too short for me to try to troubleshoot something in a VM that I know doesn't work on the real computer.
For crying out loud, I've got an old G3 Macbook that is dual boot Tiger and Ubuntu-for-Mac. This may explain why I'm taking the failure of 10.4 so badly.

Frank

---

### Post by philinux on 2010-05-11
As soon as you boot the livecd hit any key when the graphic appears. Then check cd for defects.

From the release notes.
Boot options hidden by default on Desktop and Netbook LIVECDs
The Ubuntu 10.04 LTS Desktop and Netbook CDs feature a new boot interface that is non interactive by default.
To configure advanced boot options, press any key at the first boot screen.

---

### Post by QIII on 2010-05-11
It is important to note that "Lucid is Hell!" is inaccurate.  "Lucid is  Hell for me!" is valid.
 
 There are likely millions of people using Lucid.  When it goes right,  they  do not come here asking why it is working.
 
 But it is certainly clear from the fact that people come here for help  that it is hell for some.

I have been using Ubuntu since Warty, and I have found that each new version has its frustrations, but is generally better than the last.  Lucid has been, by far, the best of the bunch for me.  However, as a sample size of 1, I am not a statistically valid representation.

Others have made some suggestions regarding the LiveCD you have created.  Any fault there should be eliminated to rule out that as a possibility.

Can you get a Live session to run?

Did you do an md5sum check on your original .iso download?

If that checks, when the LiveCD first starts, chose to check the disk for defects.

If that checks, do Memtest from the LiveCD.  A good memtest takes a long time.  Sometimes overnight.  Remember that *nix systems can be more sensitive to impending disk and memory failure than Windows.

If all those check, we need to rule out hardware as an issue -- or see  if launchpad mentions any difficulties with your hardware setup.

---

### Post by Franknfurterhotmale on 2010-05-11
After my last post I tried to create a VM. Half way through VMWare stopped installing reporting that either the cd or player were faulty so I burned a new cd from the iso, cleaned the lens and started to install again ..... and read the next posts.
I hashed the iso- miles off the md5 for the 64bit which I thought I'd downloaded but spot on for the 32 bit.
Downloading the 64 bit iso using Vuze- it does it in ten or so minutes and the install finished on the pc. This time it's not hanging while I download updates despite me trying to force it by using firefox at the same time.
looks as if my cd was deteriorating each time I put it in.
The current install failed to import my settings from the other OS though.
It's a pity that Ubuntu tries to install despite defects in the media rather than aborting as soon as they are detected.
I'll look for a more local update site after I've installed the 64 bit.
Thank you very much everybody who contributed, my faith has been restored.

Frank

---

### Post by spydeyrch on 2010-05-11
> **Franknfurterhotmale said:**
> 
I hashed the iso- miles off the md5 for the 64bit which I thought I'd downloaded but spot on for the 32 bit.
Frank

I saw your comment about the x32 10.04 and it reminded me of something,  hope it helps; it is something I recently ran into just a few days ago:

I usually run x64 software/os on my system. But I have a friend that wanted to try ubuntu and his machine is only x32 capable. So I downloaded the x32 version of 10.04. I tried to burn it to CD (for other reasons found in these two threads of mine: [thread #1]("http://ubuntuforums.org/showthread.php?t=1479071") & [thread #2]("http://ubuntuforums.org/showthread.php?t=1479197")) but every time, right at the end, it would fail. No matter what I tried, it would fail. I tried two different download sites from the ubuntu site, two different torrents, .iso burns through win7, ubuntu 10.04, and mint 8, max speed, and min speed. Nothing seemed to work. So eventually I just used a live usb to install the x32 and it worked fine.

Appearently there are tons of people that have experieinced the same thing with the x32 flavor. The .iso doesn't burn correctly. After I would try to burn it and get an error, if I put the CD back in, it would recognize it as ubnutu 10.04 (in all three of my OSs). I could boot off of it but not get the live cd to run properly. I could select install and it would act like it was installing but then would fail to boot up after the install or would just hang during the install. Oh, and that was after burning the .iso with varying combinations, using 4 different CDs.

Anywho, I hope that helps too some degree. The only way I could get around the issues that I had was to either use a live pen drive if I wanted/needed the x32 flavor or use an x64 flavor via cd or live pen drive.

-Spydey :guitar:

P.S. My friend's system is up and running now on an x32 flavor.

---

### Post by Franknfurterhotmale on 2010-05-13
Ultimately I burned the 64 bit iso to cd, as usual it verified, but this time I ran the cd in Windows and installed from there.
It seems to copy the setup files onto the target drive and then boot to them and install.
Seems to be going fine except I can't cancel package updates by clicking cancel, the cross button in the box or from the task bar. I get a download that I have tried to stop that does not appear in System monitor, but my computer is receiving data at the Ubuntu top speed of 4 KB/s. I make that 32 kb/s, 60% of dialup modem speed.
I've tried hunting for repositories in timezones where everyone is asleep or communications are better and the Synaptic Package Manager tells me it can't connect to the servers, and when I try the "find best" option the program tells me there are no repositories available and can't switch me back to UK. Then it downloads at the 4KB/s anyway.
Perhaps all Ubuntu servers restrict traffic to this so everybody can get a feed.

Frank

---

### Post by mastablasta on 2010-05-13
I don't see a major issue here, unless you have a limited connection. I mean you can just levae them to run in background. There is probably plenty upgrading going arround right now...
 
@spydeyrch
 
What programme did you use for the burn? Does this only happen in 10.04? I burned it with Nero in WinXP and it burned fine.

---

### Post by louieb on 2010-05-13
> **perham said:**
> the funny thing about 10.04 is that since it comes with grub 2, there's no option for not letting ubuntu ruin the mbr. ...

On both the alternate (text based installer) and the live CD installer (Ubiquity)  That option is right where its always been. 

Alternate CD - Just before the end of the install a screen is displayed - saying GRUB will be installed here - Do you want to change it?

Live CD - on the install summary screen - Press the "Advanced" button - Change where the IPL code of GRUB goes. 

Ruin the mbr - ouch - IMO it makes it better - GRUB is a much better boot loader.

---

### Post by spydeyrch on 2010-05-13
> **mastablasta said:**
> 
@spydeyrch
 
What programme did you use for the burn? Does this only happen in 10.04? I burned it with Nero in WinXP and it burned fine.


I used three different programs. One in Mint, one in Ubuntu 10.04 x64, and the third in windows - ISO Recorder v3.1. Each time I would burn it, it would have an issue in the end of the burn.It was the x32 flavor. My system is fine, I use x64, but I wanted a friend to try it out and he couldn't boot off of a USB.

I figured out a work-around. :)

-Spydey :guitar:

---

### Post by uRock on 2010-05-13
Jaunty has 5 months, Karmic has 11 months and Lucid has 35 months. Lucid is a bit buggy, but they are getting it straightened out.

---

### Post by Franknfurterhotmale on 2010-05-13
I've burned 9.04, 9.10, 10.04 32bit (twice) and 10.04 64 bit install disks using the disk utility package on my iMac, or "Burn" on the mac, one i did with nero on win XP.

I accept that slow downloads mean you have to walk away, but when you are troubleshooting, or finding out whether the OS actually works, which is what I have been doing for a week, it's very frustrating to have to wait four hours each time you try to load a proprietory driver to find the computer frozen at the end.

In fact the only thing that my 10.04 64 bit does is browse the internet. It can't download nvidia drivers, the sound doesn't work, a variety of other lumps of software either cannot be installed or cannot be found. Each stage of troubleshooting/installation starts with a four hour download before I can try to follow the forum instructions.

About three years ago I built a computer for a friend and installed Ubuntu instead of Windows as the OS. In those days it worked faultlessly. I wouldn't do it today, I'd advise her to get a Mac, or, if she wanted to do it on the cheap again, buy a ready made Windows pc.

Frank

---

### Post by uRock on 2010-05-13
> **Franknfurterhotmale said:**
> I've burned 9.04, 9.10, 10.04 32bit (twice) and 10.04 64 bit install disks using the disk utility package on my iMac, or "Burn" on the mac, one i did with nero on win XP.

I accept that slow downloads mean you have to walk away, but when you are troubleshooting, or finding out whether the OS actually works, which is what I have been doing for a week, it's very frustrating to have to wait four hours each time you try to load a proprietory driver to find the computer frozen at the end.

In fact the only thing that my 10.04 64 bit does is browse the internet. It can't download nvidia drivers, the sound doesn't work, a variety of other lumps of software either cannot be installed or cannot be found. Each stage of troubleshooting/installation starts with a four hour download before I can try to follow the forum instructions.

About three years ago I built a computer for a friend and installed Ubuntu instead of Windows as the OS. In those days it worked faultlessly. I wouldn't do it today, I'd advise her to get a Mac, or, if she wanted to do it on the cheap again, buy a ready made Windows pc.

Frank
?

---

