---
title: "Brasero overburn option"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by crompie on 2009-02-27
I am trying to burn an image of a CD-ROM onto a blank CD, using Brasero. I am getting the following errors in the log file:

BraseroCdrdao stderr: ERROR: Length of toc (80:01:53, 360128 blocks) exceeds capacity of CD-R (79:57:74, 359849 blocks).
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: Please use option '--overburn' to start recording anyway.
BraseroCdrdao called brasero_job_get_action

The image file was created from a standard CD, so it should be possible to burn it to another standard CD. But Brasero says the image is too big to fit.

The log file also says "Please use the option "--overburn" to start recording anyway.

How do I set this option "overburn" in Brasero?

Thanks. :)

---

### Post by hyperyoda on 2009-02-27
> **crompie said:**
> I am trying to burn an image of a CD-ROM onto a blank CD, using Brasero. I am getting the following errors in the log file:

BraseroCdrdao stderr: ERROR: Length of toc (80:01:53, 360128 blocks) exceeds capacity of CD-R (79:57:74, 359849 blocks).
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: Please use option '--overburn' to start recording anyway.
BraseroCdrdao called brasero_job_get_action

The image file was created from a standard CD, so it should be possible to burn it to another standard CD. But Brasero says the image is too big to fit.

The log file also says "Please use the option "--overburn" to start recording anyway.

How do I set this option "overburn" in Brasero?

Thanks. :)

There was a bug in earlier versions, try Brasero 0.9.x.

Zach

---

### Post by crompie on 2009-02-27
Thanks for the tip. I'll try it and post the results...

---

### Post by binbash on 2009-02-27
yes bug at old versions.Download latest deb from  :
[http://www.getdeb.net/app/Brasero](http://www.getdeb.net/app/Brasero)

---

### Post by crompie on 2009-02-28
Thanks for the link to getdeb.

I installed Brasero 0.9.1 and this recognised that my image was larger than the disk reported capacity, and asked me if I wanted to use Overburn. Nice! I selected yes, and the disk was successfully burned. :P

Thanks for the help.

---

### Post by jalirious on 2012-02-20
brasero / k3b wouldn't let me "Not enough space even for overburn".

(I read that in a whiny voice)

So, at the command line 

cdrecord -overburn -dev=/dev/CDBURNER ~/downloads/precise-desktop-amd64.iso

(for me CDBURNER was sr0. You can check yours via cd /dev, ls -ltr)

708.2MB, ok on a verbatim cd.

---

### Post by overdrank on 2012-02-20
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

