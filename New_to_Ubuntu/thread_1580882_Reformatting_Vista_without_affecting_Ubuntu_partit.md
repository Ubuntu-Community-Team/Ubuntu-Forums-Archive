---
title: "Reformatting Vista without affecting Ubuntu partition"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by ebola1717 on 2010-09-24
I currently have Vista and Ubuntu dual-booted on my HP laptop.  I would like to reformat the Vista partition, but I don't want to affect the ubuntu partition.  I'm under the impression that the HP System Recovery just copies an image, and so would wipe out the ubuntu partition.  Is this the case, is there a way to reformat my windows partition without formatting the ubuntu side?  or should i just reformat it clean, and reinstall ubuntu? HP didn't give me recovery disks, though I believe there's a utility to make them, but I'm not sure if this is different from the built-in recovery.

---

### Post by TCHebb on 2010-09-24
Just boot from your Ubuntu LiveCD and go to System -> Administration -> GParted. In fact, if all you want to do is format the Windows partition, you can install GParted from the Software Center and run it under your normal Ubuntu installation.

---

### Post by ebola1717 on 2010-09-24
Sorry, I meant format and then reinstall windows on to the partition it's currently in.  So basically what using the recovery partition does, but without affecting my ubuntu partition.

---

### Post by john newbuntu on 2010-09-24
Frankly I am unsure on how the HP recovery works (whether it reformats the entire drive or just the main OS factory settings partition-wise).  But I would suggest making a backup image of your existing Ubuntu install using a tool such as "Clonezilla" on an external drive.

Should you lose Ubuntu in the worst case after recovery, you can re-create your Ubuntu partition like how you did before (resize vista from Win) and re-image Ubuntu from backup using Clonezilla.  This prevents re-installation of ubuntu + the updates + your customizations.

Edit: Thank you Sef for post #5

---

### Post by Sef on 2010-09-24
> ...re-image Ubuntu from backup using Clonezilla.

[Clonezilla web site]("http://clonezilla.org/")

---

### Post by ebola1717 on 2010-09-24
Yeah, I going with your option john newbuntu.  The HP system recovery seems to say it will only be reformatting my windows partition, so I think I'm fine.  It doesn't tell me that until I've already set it to start formatting the drives though, which is sort of silly.  Thanks for the advice.

---

### Post by Mark Phelps on 2010-09-24
> **ebola1717 said:**
> .. The HP system recovery seems to say it will only be reformatting my windows partition ...

Really? I'd be very surprised if it actually did that.

I've done HP recovery on several machines and in all cases, it completely reformatted the ENTIRE drive.

But, the recovery could be different for each make and model machine.

Have you checked with HP to confirm that it will NOT wipe and reformat the entire drive?

---

