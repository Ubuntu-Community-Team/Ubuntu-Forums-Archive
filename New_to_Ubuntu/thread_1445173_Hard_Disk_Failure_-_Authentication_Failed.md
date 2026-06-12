---
title: "Hard Disk Failure - Authentication Failed"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by old_guy01 on 2010-04-02
I've had a perfectly good system for 2 years but I have just had a hard disk fail (2nd disk in the system).  The system still boots off the 1st disk and gets me to the log in screen, but no user/password combo gets me in.

Can I get past this and access the data or am I scr***d.  I understand that root and log in questions are frowned upon.  I just need a way to recover my data, if that is at all possible.  

I am a complete novice and do not understand ubuntu at all.  Up until now it just worked !!

Any assistance would be greatly appreciated

Thanks

---

### Post by mikewhatever on 2010-04-02
Assuming that root login can save the day, if the file system can't be read, is a major misconception. If you have a hard disk failure, use tesdisk to recover data.
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Do you mind telling why you think it is a disk failure.

---

### Post by old_guy01 on 2010-04-02
Hi Mike,

Thanks for the speedy response.  Most of what you said went over my head - but I can answer the hard disk part.  We had some bad weather recently so I turned off the system.  When I went to turn the system back on the 2nd drive was not being found in Bios. So I took it out of the Ubuntu box and had it tested at a local PC store.  Its really is dead. 

In its own right not a major disaster as it was only in there to act as a temp storage device.  I never expected to be shut out by a secondary drive failure.

At the moment I am system-less and have no access to the net from home of the files I would use.  Please keep any assistance at the ID 10 T level

---

### Post by mikewhatever on 2010-04-02
So, what's the current state of that drive?
Can you hear is spinning when powered up?
Is it recognized by the BIOS?
If the above are yes and yes, it might be possible to recover the files with tesdisk.

You can solve the 'systemless' situation by running the a live cd, but no internet is a problem, since you want be able to get tesdisk packages.

---

### Post by old_guy01 on 2010-04-02
OK Here is the state of Play:
The system is working perfectly at the hardware level.  The drive is shown in Bios and boots up.  Ubuntu goes through its start up procedure and stops at the log in screen.

My daughter has just arrived for Holy Week.  It seems that I have been storing her "Music" collection for the last year or so :o

When she connected to the house network the Ubuntu box appears as a  Windows share, even though I can't get into the box.  The log in screen in is still up and denies all access.  Even my daughter can't log on.

However on her laptop we can access the Ubuntu drive.  So at the moment we are copying all the family stuff on to her system (just in case).  I am now more confused than ever :P and still open to suggestions.  Although a re-install is not so critical as it was 2 hours ago if that is what it takes

---

### Post by Mark Phelps on 2010-04-02
edit:  removed

---

### Post by mikewhatever on 2010-04-02
I suspect you may have had your home partition on that drive, which would explain why you can't login. Anyway, if samba has access to it, it probably hasn't failed, and a file system check might fix it. You can do that from recovery mode with the following command:

fsck -A -y

In case you can't boot the recovery mode, boot from the live cd and post the output of <sudo fdisk -l>.

---

