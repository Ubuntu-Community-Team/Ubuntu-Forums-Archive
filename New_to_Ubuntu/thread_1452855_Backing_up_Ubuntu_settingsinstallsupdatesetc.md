---
title: "Backing up Ubuntu settings/installs/updates/etc"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by gallow737 on 2010-04-12
Okay, so I installed Ubuntu not too long ago because of complications with Windows, and I'm enjoying it immensely.  Unfrotunately it has come time that I need to get Windows back.  I have a lot of web design and video editing to do and I need access to the Adobe suite of programs (Premiere, After Effects, Fireworks, Photoshop, etc).  

The problem, however, is that my computer was finicky with Windows before by not allowing it to install and boot up after I reformatted my hard drive and tried reinstalling.  I need to try it out again because I really need Windows access (I have VirtualBox but I don't have nearly enough RAM available to free up to be able to support running these programs).  

If my windows problem persists, and I can't actually get it back loaded onto my computer, it will likely be after I have my HD formatted for Windows (it will allow me to go through the first phase of Windows installation, but it won't boot up into the install manager).  So basically what I'm asking is if that's the case and I need to get back into Ubuntu for my day-to-day computing operations, is there a way I can save/backup all the programs and updates I've installed so I don't have to do it again?  I'm just curious, I've spent the last month or so getting this computer setup to my liking but something came up and I really need to get back into Windows, sadly.  Adobe has a deathgrip on my job productivity.

So yeah, is there a way to do this or will I have to bite the bullet and just start fresh if that's the case?

---

### Post by mk1w86 on 2010-04-12
I'm not quite sure what the problem you're having with Windows is.  What version is it and is it a normal installation disk or a restore disk you are using? :-s

You could dual boot, by resizing your Ubuntu partition and creating an NTFS formatted partition for Windows from your Ubuntu LiveCD using Gparted.  The Windows installer might work then.  Afterwards you would have to reinstall Grub, there is a guide to dual booting here:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you do find you need to back up the entire system you might want to take a look at Clonezilla, it will let you restore Ubuntu or Windows easily once the system is backed up:

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by gallow737 on 2010-04-12
My Windows problem stems back a ways.  I've used 3 different Windows install disks (had to borrow a couple from friends) and kept getting the same problem, while at the same time doing things that were supposed to fix it according to a bunch of internet methods while searching for the issue.  The problem persisted.  

Basically what happened was when I had Windows I got hit with viruses.  Nothing that could hamper my productivity, but it was definitely annoying, and virus scans and spyware/malware programs wouldn't remove it.  Basically when I search for something in a search engine, when I would click the link it would not take me to the place I wanted to go and would instead redirect me to another website.  

I decided to attack it full on and just reinstall Windows.  So I did and upon rebooting the computer and after going through the "Which HDD do you want to install to?" it reformatted the drive and restarted to go into the windows install but it gave me this error:

NTLDR is missing 
Press Ctrl Alt Del to Resta

After searching on Google (using a netbook), I found several fixes.  The Windows disk I had didn't have a safe mode prompt, which is what I needed, in order to copy a file that would supposedly fix the problem, so when I got a copy that did have that on there I copied the files I needed to fix this problem.  

Then I did it all over again and sure enough I got the same error.  For two days I tried fixing this using all manners of advice to fix it, and nothing worked.  Then I installed Ubuntu in 10 minutes and waved goodbye to Windows.  But my web design and video production freelancing has caught up with me and I need those Adobe programs back, so this is why I'm asking about backing up the files, in case I get the same problems with Windows.

---

### Post by r-senior on 2010-04-12
If you have plenty of memory (> 2GB), have you considered running Windows in a virtual machine using something like VirtualBox? Apart from being able to reliably run Windows software, you can also savepoint the VM in case of viruses and other issues.

EDIT: subject to licenses, assuming you have legit installation disks, etc, etc, etc.

---

### Post by gallow737 on 2010-04-12
I pointed out in the first that I had run VirtualBox with Windows on it but don't have enough RAM to free up.  I only have 2GB of RAM.  On VirtualMachine system I delegated 1GB of RAM to run Windows which isn't enough for the Adobe Programs.

I suppose I could always just go buy more RAM, lol.  Not sure if I have the processing power for more though... at least not enough to be able to run VirtualBox quick enough to run these programs.  AMD Athlon 64 X2 Dual Core 4200+.  I think they're 2.4ghz.  I've never installed RAM on my computer before so I don't know.  I'm not much of a hardware guy

If I could be able to process more RAM (maybe 2 more GB of it) so I can delegate more than 2GB of RAM for the VirtualMachine that would be an awesome fix, because I really don't want to get rid of Ubuntu.  The 2GB of RAM on my Windows OS ran the programs perfectly fine.

---

### Post by mk1w86 on 2010-04-12
> **gallow737 said:**
> My Windows problem stems back a ways.  I've used 3 different Windows install disks (had to borrow a couple from friends) and kept getting the same problem, while at the same time doing things that were supposed to fix it according to a bunch of internet methods while searching for the issue.  The problem persisted.  

Basically what happened was when I had Windows I got hit with viruses.  Nothing that could hamper my productivity, but it was definitely annoying, and virus scans and spyware/malware programs wouldn't remove it.  Basically when I search for something in a search engine, when I would click the link it would not take me to the place I wanted to go and would instead redirect me to another website.  

I decided to attack it full on and just reinstall Windows.  So I did and upon rebooting the computer and after going through the "Which HDD do you want to install to?" it reformatted the drive and restarted to go into the windows install but it gave me this error:

NTLDR is missing 
Press Ctrl Alt Del to Resta

After searching on Google (using a netbook), I found several fixes.  The Windows disk I had didn't have a safe mode prompt, which is what I needed, in order to copy a file that would supposedly fix the problem, so when I got a copy that did have that on there I copied the files I needed to fix this problem.  

Then I did it all over again and sure enough I got the same error.  For two days I tried fixing this using all manners of advice to fix it, and nothing worked.  Then I installed Ubuntu in 10 minutes and waved goodbye to Windows.  But my web design and video production freelancing has caught up with me and I need those Adobe programs back, so this is why I'm asking about backing up the files, in case I get the same problems with Windows.

It is possible there is still something on your hard drive e.g. corrupt MBR, causing problems that has not been cleared by just reformatting and reinstalling Windows, you could try wiping the entire drive using a tool such as DBAN (use the Quick Erase option):

[http://www.dban.org/](http://www.dban.org/)

Unfortunately you would loose you Ubuntu install, remember to back up any important data first!

---

### Post by gallow737 on 2010-04-12
Thanks, I'll look into it :)

---

### Post by gallow737 on 2010-04-13
> **mk1w86 said:**
> It is possible there is still something on your hard drive e.g. corrupt MBR, causing problems that has not been cleared by just reformatting and reinstalling Windows, you could try wiping the entire drive using a tool such as DBAN (use the Quick Erase option):

[http://www.dban.org/](http://www.dban.org/)

Unfortunately you would loose you Ubuntu install, remember to back up any important data first!

I'm trying this option and I'm getting this message:

"Dban finished with non-fatal errors" 

And it tries to do something with my floppy drive, but I son't have a floppy drive.  I re-ran it using the nofloppy command and it did the same thing.  I've seen dozens of questions just like this on the dban forums but they all went unanswered, which was rather inconvenient, lol.

Any ideas what's up?

---

### Post by mk1w86 on 2010-04-13
> **gallow737 said:**
> I'm trying this option and I'm getting this message:

"Dban finished with non-fatal errors" 

And it tries to do something with my floppy drive, but I son't have a floppy drive.  I re-ran it using the nofloppy command and it did the same thing.  I've seen dozens of questions just like this on the dban forums but they all went unanswered, which was rather inconvenient, lol.

Any ideas what's up?

Is there any more to the error message, also do you get the error straight after starting the wipe or after it has been running for a while?

The error about the floppy drive shouldn't be anything to worry about, DBAN is just trying to save the log file to a floppy disk. ;)

Another thing, are you using a SATA or IDE hard drive?  If you are using a SATA drive you could try disabling the ACHI mode in the BIOS if it is enabled.

---

### Post by zer010 on 2010-04-13
to make a full backup of Ubuntu use remastersys.  It will make an .iso of your entire current system.  * i'm not sure it will back up personal files or preferences.

---

### Post by mk1w86 on 2010-04-13
> **zer010 said:**
> to make a full backup of Ubuntu use remastersys.  It will make an .iso of your entire current system.

Good idea, I wish I'd remembered that. ](*,)

---

### Post by gallow737 on 2010-04-13
> **mk1w86 said:**
> Is there any more to the error message, also do you get the error straight after starting the wipe or after it has been running for a while?

The error about the floppy drive shouldn't be anything to worry about, DBAN is just trying to save the log file to a floppy disk. ;)

Another thing, are you using a SATA or IDE hard drive?  If you are using a SATA drive you could try disabling the ACHI mode in the BIOS if it is enabled.

Well it doesn't really matter because it seems all the problem was was my version of DBAN.  I rebooted using Hiren's Boot CD and ran DBAN on that and it worked perfectly fine.  Took up to 7 hours to do it to both my HDD's, but when I put in my Windows disk I went ahead and repartitioned the drives and installed Windows and with the exception of a boot order snafu, it seems all is going well right now.  Typing this on my netbook, my desktop is currently installing windows normally, so it looks like all is good.  

Thanks for your help though.  Had I not known about DBAN this NTLDR problem probably still would've persisted, istead I'm getting my computer back :)

I also found out that I can upgrade my computer up to 4GB of RAM on my motherboard, but since my version of XP only recognizes 3, I might just up it by 1 and install Ubuntu on VBox, that way I can delegate more RAM to running it.  

Thanks again for all your help guys, looks like I won't need to backup Ubuntu after all

---

### Post by mk1w86 on 2010-04-13
I'm glad your computer is working again. 8-)

Out of interest, what DBAN version did you use in the end and which one didn't work?  I know there is the latest 2.0.0 which is a preview release (although I think it's regarded as being as stable as a normal release), so was it an older version, such as 1.07 that you used?

---

### Post by gallow737 on 2010-04-13
I'm not exactly sure.  I used whichever version is on the Hiren's Boot CD.  I know the one I originally made was 2.0.  This one may have been the same, but it may have just been the burning utility that burned the ISO.  Maybe it didn't register something correctly, not sure.  Regardless, the version on Hiren's Boot Disk worked like a charm.  According to Hiren's page it's 1.0.7

---

### Post by gallow737 on 2010-04-13
Also, how do I change the threat title to [SOLVED]?

---

### Post by clancymf on 2010-04-13
Its in the thread tools in the top right

---

