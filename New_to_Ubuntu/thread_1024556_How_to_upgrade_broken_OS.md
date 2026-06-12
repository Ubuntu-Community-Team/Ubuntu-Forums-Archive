---
title: "How to upgrade broken OS?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by Luffer on 2008-12-29
I've got a problem with my current Ubuntu install which means it won't boot. Everyone has told me to install Intrepid (I'm using Heron).

My question is, how do I install the new version over the old version easily? I can burn a new boot disc no problem, but then what, how do I remove the old Ubuntu? Will the disc detect an existing installation and upgrade it? Will it mess up my GRUB menu? I'm scared of the terrible consequences of doing the wrong thing.

---

### Post by nebu on 2008-12-29
when you install interpid....

you just select the partition where the hardy installation is there.... and format it and install it all over again.....

this will erase all data that u have stored in this partition

---

### Post by RichardLinx on 2008-12-29
Are you dual booting? If your not then you can just install Ubuntu no strings attached. However, If your dual booting and don't wish to accidentally erase another partition (With Windows on it for example) then you should take note of which partition Ubuntu is on and then install over said partition when you're installing a later version of Ubuntu.

---

### Post by arckeda on 2008-12-29
I recommend you create a new partition then reinstall and copy back your files, though that maybe a little complicated for you, try looking into gparted.

---

### Post by Luffer on 2008-12-29
Created a new boot disc with 8.10 on it, but it won't boot that either. After seeing the splash screen for a while it goes to a black screen with blinking cursor top right and just stays like that.

If I opt for the straight install option without going to the OS first that fails too! It goes through a few checks which all report [OK] but then the whole thing just stops.

What do I do now? This whole thing is such a mess, I just want my OS back.  Gibbon worked fine but now the install disc wont even boot!!!

---

### Post by mapes12 on 2008-12-29
> **Luffer said:**
> Created a new boot disc with 8.10 on it, but it won't boot that either. After seeing the splash screen for a while it goes to a black screen with blinking cursor top right and just stays like that.

If I opt for the straight install option without going to the OS first that fails too! It goes through a few checks which all report [OK] but then the whole thing just stops.

What do I do now? This whole thing is such a mess, I just want my OS back.  Gibbon worked fine but now the install disc wont even boot!!!IMHO stay with 8.04LTS. If the Live CD doesn't work then try the [alternate CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"). But before you do anything get your [partitions setup correctly]("http://www.psychocats.net/ubuntu/partitioning"). [Gparted]("http://gparted.sourceforge.net/") will take care of things.

Backup /home before hand to keep your personal settings, files, bookmarks and the like. Transfer it back once your fresh installation is complete.

---

### Post by waspbr on 2008-12-29
1. make sure you have burned a good liveCD, check for errors, you can do that at the live menu.

2. at the live menu press f4 (or f6 can't recall exactly), this will bring up other boot options, choose safe graphics (or something like that). see if it boots now.

---

### Post by Luffer on 2008-12-30
If I boot in safe graphics mode then it eventually dumps me at a command prompt. Now what?

---

### Post by steveneddy on 2008-12-30
Unless you have something that needs to be saved and the install is broken, just do a total reinstall.

---

### Post by Luffer on 2008-12-30
/me bangs head on wall.....

I'm trying to do a complete re-install! The Live CD doesn't work! I don't know why my exisitng install doesn't work and I don't understand why the LiveCD won't boot. All I know is it doesn't and I been have searching for a solution for ages!

---

### Post by albinootje on 2008-12-30
> **Luffer said:**
> /me bangs head on wall.....

I'm trying to do a complete re-install! The Live CD doesn't work! I don't know why my exisitng install doesn't work and I don't understand why the LiveCD won't boot. All I know is it doesn't and I been have searching for a solution for ages!

Try the alternate installation cdrom as someone already suggested.
Make sure you've made backups of your important data.

[http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-alternate-i386.iso](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-alternate-i386.iso)

---

### Post by Luffer on 2008-12-30
How does the alternate CD differ from the standard one? why would that work when the regular disc doesn't?

---

### Post by earthpigg on 2008-12-30
> **Luffer said:**
> How does the alternate CD differ from the standard one? why would that work when the regular disc doesn't?

it's text based and simpler. less to go wrong.

only *slightly *less easy to use.

---

### Post by Luffer on 2008-12-30
Okay, but then if the GUI doesn't boot now, why would it be any different when it's installed. I thought the LiveCD was a test to see if your machine was compatible. Won't I still be stuffed with an OS that doesn't boot?

I don't understad how the old LiveCD booted fine, but a "new improved" one fails. I am obviously under the misguided impression that new versions are supposed to be better!

So far I've tried to put Ununtu on three different machines at various times. Not once has it ever been succesful, the only machine it ever worked on was this laptop. Then an "upgrade" screwed the whole thing and now nothing works again. Sorry if I appear a bit pissed off, but that's because I am after so many problems and failed attempts.

I've been in threads full of exactly these sorts of converstations, I've never had any of my problems resolved. Then someone comes along and preaches to me about how wonderful Ubuntu is, well sorry, but I've yet to see a single thing that is good about it. And belive me I've tried!

---

### Post by Michael.Godawski on 2008-12-30
Sometimes there is simply such a compatibility issue which won't let you install Ubuntu.

Let's face it. Ubuntu is great for many users. For some it does not work.

Ubuntu is great but not the end of the horizon. There are different distributions to try out.

If you are willing to stay with Linux perhaps you will find your distribution. 

If you said you tried everything I believe you,
but remember we are volunteers, and we do not feel good when a "pissed off" person tells us how bad Ubuntu is. 

Good luck.

---

### Post by albinootje on 2008-12-30
> **Luffer said:**
> Okay, but then if the GUI doesn't boot now, why would it be any different when it's installed. I thought the LiveCD was a test to see if your machine was compatible. Won't I still be stuffed with an OS that doesn't boot?

I don't understad how the old LiveCD booted fine, but a "new improved" one fails. I am obviously under the misguided impression that new versions are supposed to be better!

So far I've tried to put Ununtu on three different machines at various times. Not once has it ever been succesful, the only machine it ever worked on was this laptop. Then an "upgrade" screwed the whole thing and now nothing works again. Sorry if I appear a bit pissed off, but that's because I am after so many problems and failed attempts.

I've been in threads full of exactly these sorts of converstations, I've never had any of my problems resolved. Then someone comes along and preaches to me about how wonderful Ubuntu is, well sorry, but I've yet to see a single thing that is good about it. And belive me I've tried!

By using the alternate cdrom you have the chance to do the install, and configure the GUI later.
And concerning "newer versions are suppose to be better".
First of all Linux software is usually in development to make things better, but all programmers make mistakes, that's what bug-reports are for.

Apple has an easy job here (No word joke, mr.Jobs), because they deliver both software *and* hardware, it's so easy for them to have full control over what they deliver. Same goes for Sun MicroSystems for their Sparcs.
For Microsoft it's more difficult, but not so much because most hardware vendors drool over Microsoft since years.
For Linux it's more difficult, several hardware vendors still don't care at all or not so much about Linux.
That means that it's harder for Linux and Xorg developers to support all possible hardware.

This is where you can contribute.
Find out the specifications of your hardware and find out who else has the same hardware and how those problems are fixed or not yet fixed.

If you don't have time for that, then go back to the Ubuntu release which worked for you, it's no shame at all to run the Ubuntu Hardy Heron LTS till 2011.
And if you have problems with that, try Fedora 10, LinuxMint, Mepis, Mandriva, Slackware or Debian.
There's a lot of choice.

---

### Post by Luffer on 2008-12-30
> **Michael.Godawski said:**
> Sometimes there is simply such a compatibility issue which won't let you install Ubuntu.


But it used to work so I know it /should/ be compatible. It was an upgrade that caused all the problems and through no fault of my own I now have a dead OS and no way to get back. At least no way that is within my capability!

---

### Post by albinootje on 2008-12-30
> **Luffer said:**
> But it used to work so I know it /should/ be compatible. It was an upgrade that caused all the problems and through no fault of my own I now have a dead OS and no way to get back. At least no way that is within my capability!

It was working in 8.04 and not in 8.10, right ?
What's the problem with backing up your data and install 8.04 ?

---

### Post by Luffer on 2008-12-30
No, it was running Gutsy the upgrade to Heron screwed things up. Someone suggested installing Itrepid. But none of the LiveCDs I have will work, the whole thing is a mess frankly and I don't know where I am any more!

---

### Post by albinootje on 2008-12-30
> **Luffer said:**
> /me bangs head on wall.....

I'm trying to do a complete re-install! The Live CD doesn't work! I don't know why my exisitng install doesn't work and I don't understand why the LiveCD won't boot. All I know is it doesn't and I been have searching for a solution for ages!

Can you please boot with the "noapic nolapic" boot options at the installation cdrom prompt ? 
Press F6 to be able to do that.

---

### Post by handydan918 on 2008-12-30
> **Luffer said:**
> No, it was running Gutsy the upgrade to Heron screwed things up. Someone suggested installing Itrepid. But none of the LiveCDs I have will work, the whole thing is a mess frankly and I don't know where I am any more!
I think we should start there. Try booting a different computer with one of the cd's you made, just to see if it is correct. If it is, we can try something else.

---

### Post by albinootje on 2008-12-30
> **Luffer said:**
> But none of the LiveCDs I have will work

Do you still have the Gutsy cdrom ?
If so, what do you get when you boot from that.

I think that we should first find out whether your cdrom- or dvd-drive is still functioning properly, and also faulty RAM could be causing problems like this.

Trying your live-cdroms in another machine, as was suggested by someone else, is a good idea.

---

### Post by Luffer on 2008-12-30
> **albinootje said:**
> Do you still have the Gutsy cdrom ?
If so, what do you get when you boot from that.

No I don't have that disc anymore, is there any way I can get that iso? I could try it again if I can get a copy.

> **albinootje said:**
> 
I think that we should first find out whether your cdrom- or dvd-drive is still functioning properly, and also faulty RAM could be causing problems like this.

The check on the LiveCD menu says the disc is fine and I don't have any other issues with CDs or DVDs on the machine.

> **albinootje said:**
> 
Trying your live-cdroms in another machine, as was suggested by someone else, is a good idea.

I might be able to do that, but not really sure what it will prove... other than the CD is good, which if the check on the boot menu is to be believed is fine anyway.

---

### Post by OldTimeTech on 2008-12-30
Yes, but once you and us know the cd is fine, then we can move on from there....

Second, if you could give us the specs on the machine your trying to use the cd on, that could also help....

Third, if you can't get into the machine that you had gutsy on that the heron screwed up, you probably are unable to backup your data (that is sad) if you can get in through the terminal, you could still back up your home section...yes it's some work through terminal but can be done.  Anyway, if you can't get in at all, then download gparted and wipe the disc clean and try again with your cd that has hardy on it.

---

### Post by Luffer on 2008-12-30
> **OldTimeTech said:**
> Yes, but once you and us know the cd is fine, then we can move on from there....


Why is there any reason to suspect the CD is at fault? It burnt successfully, the CD check is fine. I don't see how that could be the issue here?

> **OldTimeTech said:**
> Second, if you could give us the specs on the machine your trying to use the cd on, that could also help....

It's a Toshiba Satellite A210-11P:

Turion 64 X2 TL-56 1.80Ghz
2GB RAM
200GB HDD
ATI HD 2600
Realtek High Defintion Audio
Atheros wifi

> **OldTimeTech said:**
> Third, if you can't get into the machine that you had gutsy on that the heron screwed up, you probably are unable to backup your data (that is sad) if you can get in through the terminal, you could still back up your home section...yes it's some work through terminal but can be done.  Anyway, if you can't get in at all, then download gparted and wipe the disc clean and try again with your cd that has hardy on it.

I don't have any data I need to save, I'm quite happy to do a completely clean install. The problem is getting the CD to a point where I can get to the installation!

---

### Post by albinootje on 2008-12-30
> **Luffer said:**
> No I don't have that disc anymore, is there any way I can get that iso? I could try it again if I can get a copy.

Here's Gutsy : [http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

> 
The check on the LiveCD menu says the disc is fine and I don't have any other issues with CDs or DVDs on the machine.

Okay, well done.

---

### Post by albinootje on 2008-12-30
> **Luffer said:**
> Why is there any reason to suspect the CD is at fault? It burnt successfully, the CD check is fine. I don't see how that could be the issue here? 

Linux installation cdroms burned at a high speed of burning *can* give problems. That's a proven fact from the past.

---

