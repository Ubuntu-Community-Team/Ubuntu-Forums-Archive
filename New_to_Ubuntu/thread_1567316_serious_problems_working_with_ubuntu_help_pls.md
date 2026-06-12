---
title: "serious problems working with ubuntu help pls"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by Willye on 2010-09-03
i've installed ubunut 10.04 in my laptop pavilion 2000, but i've had serious issues trying to work normaly, i try to launch "ubuntu software center" and the system get blocked, whether i try to install software by command line, happens the same, i am checking the /var/log/messages and appears the next messages:

Sep  3 20:51:15 xxx-laptop kernel: [ 1773.163116] sd 2:0:0:0: [sda] Unhandled sense code
Sep  3 20:51:15 xxx-laptop kernel: [ 1773.163122] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep  3 20:51:15 xxx-laptop kernel: [ 1773.163132] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Sep  3 20:51:15 xxx-laptop kernel: [ 1773.163145] Descriptor sense data with sense descriptors (in hex):
Sep  3 20:51:15 xxx-laptop kernel: [ 1773.163151]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep  3 20:51:15 xxx-laptop kernel: [ 1773.163180]         00 0b 0b 20 
Sep  3 20:51:15 xxx-laptop kernel: [ 1773.163192] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Sep  3 20:51:15 xxx-laptop kernel: [ 1773.163206] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 00 0b 0b 20 00 00 08 00
Sep  3 20:51:15 xxx-laptop kernel: [ 1773.163277] ata3: EH complete
Sep  3 20:51:19 xxx-laptop kernel: [ 1777.485206] ata3.00: configured for UDMA/100
Sep  3 20:51:19 xxx-laptop kernel: [ 1777.485236] ata3: EH complete
Sep  3 20:51:23 xxx-laptop kernel: [ 1781.807263] ata3.00: configured for UDMA/100
Sep  3 20:51:23 xxx-laptop kernel: [ 1781.807288] ata3: EH complete
Sep  3 20:51:28 xxx-laptop kernel: [ 1786.118151] ata3.00: configured for UDMA/100
Sep  3 20:51:28 xxx-laptop kernel: [ 1786.118176] ata3: EH complete
Sep  3 20:51:32 xxx-laptop kernel: [ 1790.429163] ata3.00: configured for UDMA/100
Sep  3 20:51:32 xxx-laptop kernel: [ 1790.429191] ata3: EH complete
Sep  3 20:51:36 xxx-laptop kernel: [ 1794.851150] ata3.00: configured for UDMA/100
Sep  3 20:51:36 xxx-laptop kernel: [ 1794.851175] ata3: EH complete
Sep  3 20:51:41 xxx-laptop kernel: [ 1799.173290] ata3.00: configured for UDMA/100
Sep  3 20:51:41 xxx-laptop kernel: [ 1799.173323] sd 2:0:0:0: [sda] Unhandled sense code
Sep  3 20:51:41 xxx-laptop kernel: [ 1799.173329] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep  3 20:51:41 xxx-laptop kernel: [ 1799.173339] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Sep  3 20:51:41 xxx-laptop kernel: [ 1799.173351] Descriptor sense data with sense descriptors (in hex):
Sep  3 20:51:41 xxx-laptop kernel: [ 1799.173358]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep  3 20:51:41 xxx-laptop kernel: [ 1799.173387]         00 0b 0b 20 
Sep  3 20:51:41 xxx-laptop kernel: [ 1799.173398] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Sep  3 20:51:41 xxx-laptop kernel: [ 1799.173413] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 00 0b 0b 20 00 00 08 00
Sep  3 20:51:41 xxx-laptop kernel: [ 1799.173484] ata3: EH complete

---

### Post by jtarin on 2010-09-03
>  i try to launch "ubuntu software center" and the system get blockedExplain your terminology "system get blocked". How does it get blocked?
Your /var/log/messages has nothing to do with your problem. That's a system log and your having software problems.

---

### Post by Dies on 2010-09-03
> **jtarin said:**
> Explain your terminology "system get blocked". How does it get blocked?
Your /var/log/messages has nothing to do with your problem. That's a system log and your having software problems.

Really? You don't think a possible issue with the hard drive is relevant?


@Willye

Have you tested your hard drive? You should start there.

If you have any important data on the drive that you haven't backed up yet, now may be a good time.

---

### Post by jtarin on 2010-09-03
> **Dies said:**
> Really? You don't think a possible issue with the hard drive is relevant?


@Willye

Have you tested your hard drive? You should start there.

If you have any important data on the drive that you haven't backed up yet, now may be a good time.
Thats not what I said.....the OP posted he had a problem about getting blocked when installing or updating software. Hard drive is a separate problem and I think one problem at a time is enough, but I agree with you...I just don't like to panic if unnecessary.

---

### Post by Willye on 2010-09-03
ok guys, i've done file system check, and no errors, the thing is that i cannot use normaly the system, sometimes it get stuck for one or two min, which commands can i run to check the disk and O.S, why are appearing that messages in /var/log/messages when i try to install some software, thanks

---

### Post by jtarin on 2010-09-03
Because anytime you do anything on your computer you are accessing the disc and there will be output of some sort.....good and/or bad.Walk us through the steps of your software install.

[If you've got a S.M.A.R.T disk you can test it following these instructions]("https://help.ubuntu.com/community/Smartmontools")

---

### Post by Willye on 2010-09-04
> **jtarin said:**
> Because anytime you do anything on your computer you are accessing the disc and there will be output of some sort.....good and/or bad.Walk us through the steps of your software install.

[If you've got a S.M.A.R.T disk you can test it following these instructions]("https://help.ubuntu.com/community/Smartmontools")


if i try to install any software, ubuntu keep blocked one or two minutes:

root@xxx-laptop:/home/xxx# sudo apt-get install smartmontools 
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

---

### Post by jtarin on 2010-09-04
Try one of the other package managers. [Synaptic]("https://help.ubuntu.com/community/SynapticHowto"), [Aptitude]("https://help.ubuntu.com/8.04/serverguide/C/aptitude.html") or the Software Center in the main menu.

---

### Post by jtarin on 2010-09-04
[Here's a possible fix.]("http://www.linuxquestions.org/questions/debian-26/apt-get-update-gets-stuck-while-reading-package-list-on-my-slug-795324/")...read the entire thread before attempting anything. Then read it again.

---

### Post by Dies on 2010-09-04
> **Willye said:**
> if i try to install any software, ubuntu keep blocked one or two minutes:

root@xxx-laptop:/home/xxx# sudo apt-get install smartmontools 
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

You shouldn't need to install anything, disk utility *should* already be installed. Hit Alt+F2, in the run application dialog that comes up type "palimpsest", without the quotes of course, and hit enter.

Now select the drive and click on "SMART data" then click on "Run Self-test" and select the "Extended" test option then run it. If you have any errors/failures post them here.

By the way, SMART data is only an indication that a drive is failing or has issues. You should still test the drive using any utilities provided by the manufacturer. 

In the disk utility window you should have model information, once you know who manufactured your drive, head to their website and see if they have any diagnostic utilities. They typically provide utilities which you can use to boot the machine and test the hard drive.

This is probably a good time to test your memory too, most live CD's include an option to do this.

I don't know whether you have hardware issues or not, but I do know that attempting to diagnose operating system issues when there are possible hardware issues is pointless. You need to rule out any hardware issues first.

---

