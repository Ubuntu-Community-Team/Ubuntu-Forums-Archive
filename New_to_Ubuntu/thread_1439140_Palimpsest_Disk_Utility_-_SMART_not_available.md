---
title: "Palimpsest Disk Utility - SMART not available"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by guv999 on 2010-03-25
Hi.   I have used this for some time, and all has been well.  Tonight it keeps displaying a message 'SMART is not available' so is not monitoring the hard drive at all.
I have no idea why it has happened, but any help would be appreciated.  i have lost a hard drive previously so quite like this program.
Thanks for any advise

---

### Post by cariboo on 2010-03-25
Check your bios and make sure SMART monitoring is turned on.

---

### Post by guv999 on 2010-03-27
Thanks.   I checked BIOS and it was indeed disabled for some reason.    
Even after re-enabling it Palimpsest does not want to recognise it anymore.
So I downloaded G-Smart and that is working grand.

---

### Post by Alex_L33 on 2010-03-27
This is not solved - I have the exact same problem on my two Ubuntu 9.10 machines, quite how recently this stopped working I don't know im afraid.

---

### Post by cyrex on 2010-03-31
I second that. this is NOT solved, whoever put it that away did not verify it. This appeared recently since i checked almost a week ago and when i updated with the update manager it started to appear as **Smart is not available.**

---

### Post by dE_logics on 2010-03-31
Why not just reconfigure the corresponding package?

---

### Post by ttanev on 2010-03-31
Well, I have the same problem here too, but I need something more than that :) I need the functionality of the palimpsest from lucid with the benchmark and the other bangs and whistles :) If it is possible in Karmic Koala of course ?
Firstly I blamed my SB750 /AMD/ that was configured in AHCI /was RAID/ but it's not that. I don't remember if the problem was from update, just didn't pay attention about that till now.

---

### Post by sancho panza on 2010-03-31
I too have the message "SMART is not available" since today. I have been using it a lot off late as I have a few bad sectors on my drive, but it is not working anymore, for no apparent reason. All other disk monitoring utilities are working fine (G-smart etc.)

Please reopen this thread.

---

### Post by w8ye on 2010-04-01
I also have the notation that SMART is not turned on for my internal drive
 
 The SMART works for my external Free Agent Seagate drive
 
 My internal drive is a SMART drive
 
 It is a Seagate ST9250 410AS 2 1/2"
 
 My Computer is a Satellite A205 S5879
 
 There is nothing in my computer setup screen about turning the SMART function "ON"
 
 I do get the idea that smart access is "locked" on my hard drive. I know the command to unlock it but do not know how to use it.

You have closed out this thread as solved. Please reopen it.

---

### Post by chanakyakv on 2010-04-01
Hey,

Even here!! I have been using Palimpsest Disk Utility. It was working fine atleast until 15 days ago.
But for some reason it now says that "Smart not available" !!
This is not solved!! Please reopen this thread.

---

### Post by social_flea on 2010-04-01
Just restarted after 7 days and I am having this problem too. But the strange thing is, it is working on my external 2TiB USB WD 20EADS hard drive that doesn't have smart support according to GSmartControl. :o

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Second Generation Serial ATA family
Device Model:     WDC WD3200JS-22PDB0
Serial Number:    WD-WCAPD3709177
Firmware Version: 21.00M21
User Capacity:    320,072,933,376 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Apr  1 09:45:25 2010 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

---

### Post by chrisccoulson on 2010-04-01
As I've just commented on the bug report that was opened, I'll post the same response here for people who didn't see that:

> 
Thank you for your bug report. However, this is intentional as a 
workaround for [bug 445852]("http://launchpad.net/bugs/445852"), and is explained in the changelog for the 
last devicekit-disks upload (which should have been viewable in 
update-manager when you updated):

devicekit-disks (007-2ubuntu6) karmic-proposed; urgency=low

  * Add 11-disable-smart-probing.patch: Disable ATA SMART probing on ATA
    disks. It causes hardware damage to a lot of SSD disks. This is a
    workaround, until a real fix in libatasmart is found. (LP: #445852)
 -- Martin Pitt <martin.pitt@ubuntu.com > Thu, 25 Mar 2010 18:47:35 +0100

See [https://edge.launchpad.net/ubuntu/+source/devicekit-disks/007-2ubuntu6](https://edge.launchpad.net/ubuntu/+source/devicekit-disks/007-2ubuntu6)


See [https://launchpad.net/bugs/553282]("https://launchpad.net/bugs/553282")

---

### Post by chanakyakv on 2010-04-01
I reported this as a bug, and this is the reply I got.

----------------------------
[Bug 553282] Re: palimpsest / gnome-disk-utility stopped working normally from recently - incorrectly says that "SMART is not available" !!
	
Thank you for your bug report. However, this is intentional as a
workaround for bug 445852, and is explained in the changelog for the
last devicekit-disks upload (which should have been viewable in update-
manager when you updated):

devicekit-disks (007-2ubuntu6) karmic-proposed; urgency=low

 * Add 11-disable-smart-probing.patch: Disable ATA SMART probing on ATA
   disks. It causes hardware damage to a lot of SSD disks. This is a
   workaround, until a real fix in libatasmart is found. (LP: #445852)
 -- Martin Pitt <martin.pitt@ubuntu.com  >   Thu, 25 Mar 2010 18:47:35 +0100

See [https://edge.launchpad.net/ubuntu/+source/devicekit-](https://edge.launchpad.net/ubuntu/+source/devicekit-)
disks/007-2ubuntu6

** Package changed: gnome-disk-utility (Ubuntu) => devicekit-disks
(Ubuntu)

** Changed in: devicekit-disks (Ubuntu)
      Status: New => Invalid

---

### Post by chrisccoulson on 2010-04-01
> **chanakyakv said:**
> I reported this as a bug, and this is the reply I got.

I already commented in this thread too ;)

---

### Post by Rubi1200 on 2010-04-01
Ok, so Palimpset was working for me until the latest updates from Update Manager. Then, suddenly, not working. Plugged in an external HD and it works on that! Therefore, the problem surely has to be with something in Ubuntu.
It would be really helpful if someone could respond to this.
Btw, marking it for re-installation did not help.
Thanks in advance.

---

### Post by chrisccoulson on 2010-04-01
> **Rubi1200 said:**
> Ok, so Palimpset was working for me until the latest updates from Update Manager. Then, suddenly, not working. Plugged in an external HD and it works on that! Therefore, the problem surely has to be with something in Ubuntu.
It would be really helpful if someone could respond to this.
Btw, marking it for re-installation did not help.
Thanks in advance.

Did you not read the comments above?

---

### Post by Rubi1200 on 2010-04-01
Sorry, no, because I posted a new reply at the beginning of the thread and only saw afterwards that there had been a response. Next time I will pay more attention!
In any event, is it possible to download and install a previous version of devicekit that will show SMART for the HD?

---

### Post by chrisccoulson on 2010-04-01
> **Rubi1200 said:**
> Sorry, no, because I posted a new reply at the beginning of the thread and only saw afterwards that there had been a response. Next time I will pay more attention!
In any event, is it possible to download and install a previous version of devicekit that will show SMART for the HD?

You could just downgrade to the release version of devicekit-disks (it's still in the archive)

---

### Post by MRCeltic on 2010-04-01
I had this same issue I tried going to an older version but couldn't get smart to come back up.  My Solution was to reinstall 9.10, without an internet connection.  Then open synaptic and search for devicekit-disks select it, then goto package > lock version.  I also did this for libatasmart4 and i haven't had a problem since.

---

### Post by chanakyakv on 2010-04-02
Sorry. I could not delete my own post. So left this here.

---

### Post by Rubi1200 on 2010-04-02
Thanks MRCeltic!!!! I tried re-installing the older package but Synaptic was not happy. Have now re-installed 9.10 and locked the 2 packages; works like a charm. 
Nice one!

:D

=D>

---

### Post by thomasyen on 2010-04-02
Had the same problem here. Thanks for all of your help!

---

### Post by munchkinmunchkin on 2010-04-05
I have the same problem, after updating devicekit-disks 007 2ubuntu5 to devicekit-disks 007 2ubuntu6, SMART stopped working in Palimpsest.

I have force installed version 3 to fix the problem, does anyone know how to get and install version 5 as it was working fine, and I don't have any SSD disks so not a problem?

Version 5 is not on the versions list only version 3.

---

### Post by sarang on 2010-04-22
I am not using any SSD disks and wanted to re-enable SMART. The following seems to work.

```
sudo gedit /lib/udev/rules.d/95-devkit-disks.rules
```

Locate the following lines (about 1/3 the way into the file; search for "smart")

```

# ATA disks driven by libata
#KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="ata", ENV{DEVTYPE}=="disk", IMPORT{program}="devkit-disks-probe-ata-smart $tempnode"

```

Uncomment the second line by removing the # from its front, so you should have

```

# ATA disks driven by libata
KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="ata", ENV{DEVTYPE}=="disk", IMPORT{program}="devkit-disks-probe-ata-smart $tempnode"

```

Save the file and reboot and SMART should work.

---

### Post by stressmonkey on 2010-04-24
thanks! that fixed the problem very easily for me. now i can view the SMART data. yay

---

### Post by Gadgetech on 2010-04-24
Thanks, sarang. Worked for me. Should work fine since I don't have and SSD's. Too bad I'm seeing drive errors now, but it's better to know about it than not I guess.

---

### Post by MRCeltic on 2010-05-01
Ok SO yesterday I installed Lucid Lynx, Palimpsest there is no way to go back through synaptic.  So you will have to edit the code like sarang stated or download the original package from the bug report.  One you download the original file just extract make configure and install-sh executable and open them in terminal.

On a final note I do like the newer version of palimpsest, there are a few minor additions, that actually help me when im working as i use Ubuntu as my main machine at work.  So these few new additions are kinda nice.

---

### Post by darkhelmetchris on 2011-01-10
> **sarang said:**
> ```
sudo gedit /lib/udev/rules.d/95-devkit-disks.rules
```
...


Thanks sarang, this also worked for me.  I can now see my SMART data again.  Nice work.

---

### Post by alecz20 on 2011-02-24
> **sarang said:**
> I am not using any SSD disks and wanted to re-enable SMART. The following seems to work.

```
sudo gedit /lib/udev/rules.d/95-devkit-disks.rules
```

Locate the following lines (about 1/3 the way into the file; search for "smart")

```

# ATA disks driven by libata
#KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="ata", ENV{DEVTYPE}=="disk", IMPORT{program}="devkit-disks-probe-ata-smart $tempnode"

```

Uncomment the second line by removing the # from its front, so you should have

```

# ATA disks driven by libata
KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="ata", ENV{DEVTYPE}=="disk", IMPORT{program}="devkit-disks-probe-ata-smart $tempnode"

```

Save the file and reboot and SMART should work.


Awsome, It worked like a charm. Thanks!

---

