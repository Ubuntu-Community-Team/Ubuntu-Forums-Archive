---
title: "Installing a program, assistance required please"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by Wheeeze on 2010-05-24
After inadvertently permanently deleting a folder with some miscellaneous text and PDF files (you can guess what's coming next!), I searched on this forum and found that someone mentioned that he'd used Magic Rescue.  I've downloaded it to my desktop as it is not in the list of applications and managed to unpack(?) the tar.gz file.  I now have the download and another folder labelled magicrescue-1.1.9.
This is now the limit of my capability and do not wish to add any more files than necessary in order to achieve the best possibility of recovering the deleted folder.  Would one of you kind souls please tell me what I need to do next to run magicrescue, please?  Thank you in advance.

---

### Post by MrOneEyedBoh on 2010-05-24
Here ya go bro

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Wheeeze on 2010-05-24
Thank you kind Sir, but the only help it gives me is this one liner: "If you have trouble installing a .tar.gz file, you can ask for help on the Ubuntu Forums". 
So, sorry to say, I'm out of my depth unless I can see some clear instruction.  Is there any chance that you can offer further help, please?

---

### Post by SlidingHorn on 2010-05-24
according to the packages site, magicrescue is in the repos:

```
sudo apt-get install magicrescue
```

[http://packages.ubuntu.com/lucid/magicrescue](http://packages.ubuntu.com/lucid/magicrescue)

---

### Post by Wheeeze on 2010-05-24
Thanks for that.  I opened Terminal, entered your command and after a few lines it states that "magicrescue is already the newest version.
The following packages were automatically installed and are no longer required:
  libbtctl4 libgnomebt0".  I don't see the program in the lists under Applications, so what do I do next please?

---

### Post by SlidingHorn on 2010-05-24
I've never used the program, so I'm not sure how it works.  However, I found this article which seems to explain it pretty well: [http://www.linux.com/archive/feature/126525](http://www.linux.com/archive/feature/126525)

**Edit:** Here's another good reference: [http://www.irongeek.com/i.php?page=backtrack-3-man/magicrescue](http://www.irongeek.com/i.php?page=backtrack-3-man/magicrescue)

---

### Post by Wheeeze on 2010-05-24
Really good info that you've pointed me to, thanks.  The thing is, I can't "find" the program to run it!  How do I do that?  Once I have it open I'll use the info that you posted last time and I should be ok.

---

### Post by SlidingHorn on 2010-05-24
AFAIK, it doesn't have a GUI, and has to be run directly from the terminal.  Someone can feel free to butt in and correct me if I'm wrong there.

---

### Post by aysiu on 2010-05-24
I don't know how well Magic Rescue works, but I've had a lot of good experiences using Photorec to recover deleted files (not just photos, despite the misleading name):
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles](http://www.psychocats.net/ubuntucat/recoverdeletedfiles)

---

### Post by gandaran on 2010-05-24
you need a gui for magicrescue, get it here [http://linux.softpedia.com/get/System/Recovery/GRescue-33865.shtml](http://linux.softpedia.com/get/System/Recovery/GRescue-33865.shtml), choose the ubuntu .deb package, to install double click the .deb package and hit the install button.
try also photorec which is one of the best recovery programs for linux, install the 'testdisk' package from synaptic package manager then to run the program open terminal and type 'sudo photorec'
also you have to run grescue with root or it won't work.

---

### Post by redbook4574 on 2010-05-24
> **SlidingHorn said:**
> AFAIK, it doesn't have a GUI, and has to be run directly from the terminal.  Someone can feel free to butt in and correct me if I'm wrong there.

Yep I've just had a look at it and it is a CLI interface and a bloody complicated one to boot just with a cursory glance, I would suggest finding a good guide to using it, but it will need to be run in terminal.

---

### Post by Wheeeze on 2010-05-24
Those posts at #9 and #10 are other good suggestions, thanks.  I don't wish to download anything else to try to keep the deleted files from being overwritten.

---

### Post by aysiu on 2010-05-24
> **Wheeeze said:**
> That too, is another good suggestion, thanks.  I don't wish to download anything else to try to keep the deleted files from being overwritten.
That's why you run the recover program off a live CD instead of installing it to the drive you're trying to recover deleted files from.

---

### Post by Wheeeze on 2010-05-24
Ah, good point.  I hadn't realised that one could see the file system on the hard disk when using a live CD.  Nevertheless, it is done now and on the desktop.  I have read about connecting an external drive to write recovered files to though...  Still looking for a way to start the program running if I could only find it!

---

### Post by aysiu on 2010-05-24
This is how you use Magic Rescue:
[http://www.itu.dk/people/jobr/magicrescue/manpage.html](http://www.itu.dk/people/jobr/magicrescue/manpage.html)

Yeah, it's confusing to me, too. That's why I recommend using Photorec instead. The link I posted earlier walks you through the entire process with screenshots.

---

### Post by Wheeeze on 2010-05-24
There was some good info there too, thanks.  Reading back through the last few posts, I feel like I'm missing something really obvious.  Do I take it that I put the unpacked program onto a CD?  What next - reboot?  Please bear with me - just to clarify, I haven't yet got the program running and that is the sticking point at the moment.

---

### Post by aysiu on 2010-05-24
> **Wheeeze said:**
> There was some good info there too, thanks.  Reading back through the last few posts, I feel like I'm missing something really obvious.  Do I take it that I put the unpacked program onto a CD?  What next - reboot?  Please bear with me - just to clarify, I haven't yet got the program running and that is the sticking point at the moment.
I really have no idea about Magic Rescue.

As I mentioned before, the link I posted walks you through Photorec step by step.

A brief overview, though, just so you get the concept:

1. Boot up the live CD (or live USB) of Ubuntu on the disk you want to recover deleted data from

2. Using Synaptic Package Manager (or *apt-get* or Ubuntu Software Center), install the package called *testdisk*

3. Plug in an external drive you can copy the recovered data to

4. Run the command ```
sudo photorec
``` (photorec is part of the testdisk package)

5. Follow the prompts so that you are scanning the empty space on the current drive and copying the recovered data to the external hard drive

6. Sort through the external drive to find the actual data you wanted recovered

---

### Post by Wheeeze on 2010-05-24
Very much obliged to you Sir, thank you.  It is far too close to the end of my day here in the UK so I'll have a thorough read tomorrow morning and see what I can do.  Thanks to the other contributers and if anyone has further suggestions, I'll see them in the morning.  G'night all!

---

