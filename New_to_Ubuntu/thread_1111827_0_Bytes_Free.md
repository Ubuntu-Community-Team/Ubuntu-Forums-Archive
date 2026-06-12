---
title: "0 Bytes Free"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by expatCM on 2009-03-31
I do not understand this ..........

I have a SATA drive which is used to store data only.  The operating system is on another drive.  The drive has a formatted size of 459GB and according to df -h 447GB is used which results in the message 0 bytes free appearing.   It was fine yesterday and nothing has been deleted from the drive.  Files were written to the drive yesterday.

The files on this drive are in folders and if I look at the properties of the folders they total 319GB.........  not 447GB.

There are no hidden files or backup files on the drive.

So where has this space gone and how do I get it back.

The default suggestion seems to be empty trash and the root trash. Well I have done that out of completeness but since the folders and on the operating system drive I do not see how this can be part of the equation.

But now I am a bit short of ideas.  Any suggestions?

---

### Post by Sam Lars on 2009-03-31
Hmm... you could try the Disk Usage Analyser (baobab) to look and see if there's something big you're missing.
There's also the possibility that it's been mounted as read-only.  Does it still show that way after a reboot?

---

### Post by expatCM on 2009-04-01
Bad hair week it appears .......

The system would not reboot.  Started loading Ubuntu and then checked the volumes and gave up.  Generally an error of ICRC UNC IDNF ABRT.  There is some mixed view of what this means but the general google view seems to be that the drive is toast.

I unplugged the data cable to this drive and rebooted ......  no problem the desktop loaded....  

So ..  I guess it is going to be some black magic with the live CD to try and recover the data and then install a replacement...... 

I think I could have done without this .....  pity the S.M.A.R.T. reporting did not report.

---

