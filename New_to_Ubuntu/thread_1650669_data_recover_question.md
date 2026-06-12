---
title: "data recover question"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by TuLesto on 2010-12-22
Greetings to you all. 

A while back my sister borrowed my external hdd to do a backup of her windows data because she was moving from PC to Mac. She backed up her stuff to my external harddrive moved the data transfer cable from the Windows box to the Apple computer, inserted the cable and then somehow accepted a prompt to set the drive up for a Time Machine backup without thinking. she didn't backup the apple computer's data since there was nothing to backup. All that happened was Time Machine stamped the Apple's native harddrive format (HFS+ i think) over the FAT32 format the external hdd had initially. the drive is a Western Digital WD1001FALS Caviar Black 1TB harddrive

Okay that's the history now the question. 

Would it be safe to format the HDD back to FAT32 so that windows can handle the task or should I do it with Ubuntu instead and save money?

How would I go about getting the job done on ubuntu?

Edit: I have windows 7 if there is any significance to that concerning the question.

---

### Post by JustinR on 2010-12-22
Hi,

The program 'TestDisk' is just what your looking for. Look for it in the Ubuntu Software Center.

---

### Post by TuLesto on 2010-12-22
Thank you for submitting so soon!! the community on ubuntuforums is awesome!

---

### Post by TuLesto on 2011-04-07
UPDATE: I still haven't recovered the data from the hard drive as I am in fear that this application won't do the job. Should I worry further or is it just as good as any other data recovery software? Would I perhaps benefit by buying a data recovery software for my Apple MBP instead?

---

### Post by Paqman on 2011-04-07
> **TuLesto said:**
> UPDATE: I still haven't recovered the data from the hard drive as I am in fear that this application won't do the job. Should I worry further or is it just as good as any other data recovery software? 

Testdisk (and Photorec that comes with it) are excellent tools, some of the best i've ever used. Go for it.

Just to be clear: do not format the drive. The less writes you perform on it, the less data will be lost before you can recover it.

To recover your data you will need a location with at least as much free space as the size of the data you want to recover. Your files will be written to this location during recovery.

---

### Post by TuLesto on 2011-04-11
Thanks a lot, I'll get to it some time this week.

---

### Post by crispy_420 on 2011-04-11
I would say avoid using the drive at all until after recovery is done.

---

### Post by sirgogo on 2011-04-11
If TestDisk doesn't work, you may have to find and clean the drive headers manually using a hex editor. Since you had Windows previously, you should contact them and they will assign a technician to your case and help you through everything (they're really good about this). They answer all your questions and provide you with the utilities (there are a few Microsoft power-tools/utilities, as well as several Ubuntu tools).

But that should only be in case TestDisk doesn't work. Also, I suggest you don't write anything to disk. Doing so will write over the hex headers/encoding in place on the drive. Just be careful!

---

