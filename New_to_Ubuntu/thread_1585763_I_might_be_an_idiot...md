---
title: "I might be an idiot.."
date: 2010-10-01
forum: New to Ubuntu
---

### Post by duttydutdut on 2010-10-01
Maybe I don't know what I'm doing. I put the cd in my drive. I click install i set up the time keyboard blah blah the next window is partition...and I need to choose one..but it is blank no options no anything..I need help.

---

### Post by duanedesign on 2010-10-01
To make sure I understand your issue, when you get to this part in the install process you have no options in the drop down menu (where this one says SCSI3 (0,0,0,)...)?

---

### Post by duttydutdut on 2010-10-01
correct

---

### Post by Daniel0108 on 2010-10-01
> **duttydutdut said:**
> correct
That's strange...
Then Ubuntu don't find your harddrive :P
Try using an external harddrive and see if Ubuntu finds that harddrive. If yes, there is a problem with your harddrive...
Yours,
Daniel

---

### Post by duttydutdut on 2010-10-01
thank you. Of course not good news. But better than no news at all. I appreciate you taking the time. Hopefully soon I will be a happy ubuntu user.

---

### Post by Daniel0108 on 2010-10-01
> **duttydutdut said:**
> thank you. Of course not good news. But better than no news at all. I appreciate you taking the time. Hopefully soon I will be a happy ubuntu user.
No problem ;)
Now just make the thread solved and fix your hard drive :)
Happy Ubuntu-using ;)
Yours,
Daniel

---

### Post by prshah on 2010-10-01
> **duttydutdut said:**
> I click install i set up the time keyboard blah blah the next window is partition...and I need to choose one..but it is blank no options no anything..I need help.

What version of Ubuntu are you trying to install? Use 10.04, which is the current latest version.

Are you trying a full (partition) install, or a "within Windows" (wubi) install? If you are using a wubi install then you do not need to create partitions.

If you are using a full (partition / cd boot) install, and your hard disk drive is not recognized, please check:
[indent]a) You are using a recent (9.10 / 10.04) install disk.
b) You may have to change BIOS options if you are using a SATA disk. Post back for more details about this if you feel it is required.[/indent]

Information about your hardware will help us to pinpoint problems.

---

### Post by Silent Warrior on 2010-10-01
If you were running Windows before and it crashed (unclean shutdown), the drive might get hidden from Linux - it's happened to me a few times. The solution to that is to boot into Windows and shutdown/reboot cleanly, and the drive should make a grand return.

---

### Post by Mark Phelps on 2010-10-01
You might also get the same situation if your PC already has four primary partitions allocated.  Ubuntu then would NOT be able to create any more partitions, so there would be no point in showing you a page with partitioning options.

Boot into the Ubuntu LiveCD mode, open a terminal, and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list the partitions already present on your drive.

---

### Post by duttydutdut on 2010-10-03
ok i have a sata hard disk...it runs good I want to change my bios options...I had windows vista and something screwed up..got fed up with it decided to use ubuntu. Mother in law was using it and I think she clicked on everything..pop/ups virus. My computer was built by my brother amd 1/2 ghz unsure of the motherboard. Pretty outdated by todays standards but decent enough.

---

### Post by uRock on 2010-10-03
Can you boot the CD in live mode? (without making changes) 

If yes, open the System Menu and go to Administration> Partition Editor or GParted, whichever is listed and take a screenshot of the current partitions?

To take a screenshot, open the Application menu and go to Accessories> Screenshot. After taking the screenshot you can then upload the picture by using the Paper Clip circled in the picture below.

---

### Post by duttydutdut on 2010-10-03
sorry about the delay i was trying to fix it myself. But now I have been beaten. Here is my screenshot.
[IMG]file:///tmp/moz-screenshot-2.png[/IMG][IMG]file:///home/ubuntu/Desktop/Screenshot.png[/IMG][ATTACH]171263[/ATTACH]
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by duttydutdut on 2010-10-03
Does that help at all?

---

