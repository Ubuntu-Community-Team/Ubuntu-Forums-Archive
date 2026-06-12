---
title: "Installing binary from tarball"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by doctor.dan on 2010-02-08
Hi all,

This may be a very simple question, but I figured I was in the right forum.

I'm trying to install a binary package from a tarball. I have no issue extracting the files from the binary or even executing the binary file to run the program. What I want to know is what is best practice in terms of placing the contents of the archive so that it can be run by all users, and so that it can be run simply by typing the name of the binary so that it runs regardless of what the present work directory is.

The specific program I am trying to install is MRIcron ([http://www.cabiatl.com/mricro/mricron/install.html](http://www.cabiatl.com/mricro/mricron/install.html)). I downloaded the Linux x86 64bit GTK2, extracted the archive and can run the program by cd-ing into the extracted directory and runnin ./mricron.

That's all good and well, but I was wondering where I should place the mricron directory to make sure that all users can run the program. I've done a fair amount of googling but none of the resources go beyond extracting the files and executing the binary.

---

### Post by wojox on 2010-02-08
Anything I download outside the repo's I put in the /opt directory. ;)

---

### Post by Enigmapond on 2010-02-08
I agree...anything I compile or download from other sources always goes to /opt and I've never had any problems.

Cheers!

---

### Post by Bachstelze on 2010-02-08
It should go in /usr/local. Typically, when you download a binary, it is statically linked, so you just need to copy it into /usr/local/bin.

---

### Post by doctor.dan on 2010-02-09
> **Bachstelze said:**
> It should go in /usr/local. Typically, when you download a binary, it is statically linked, so you just need to copy it into /usr/local/bin.

Thanks Bachstelze. I've copied my binary folder into /usr/local/bin but cannot run it from the terminal by typing the name of the binary (in the same way that I can by typing, say, *firefox* into the terminal). Do I need to add the directory that contains my binary to the path or is there some other way to go about this?

---

### Post by Bachstelze on 2010-02-09
What is in the "binary folder"? Yopu must copy your binary into /usr/local/bin, not a folder that contains it.

---

### Post by doctor.dan on 2010-02-09
Thanks for your help Bachstelze.

---

