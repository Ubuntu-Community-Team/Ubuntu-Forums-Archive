---
title: "How do you install a tar.gz file?"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by acidpiper on 2009-12-05
Please could someone tell me how to install a tar.gz file, I have several programmes i have downloaded but don't know how to install, i have searched and found nothing - is this cause it is really easy?

Thanks in advance

---

### Post by The_Pirate_King on 2009-12-05
It depends on what you are trying to install.  What is it you are trying to install? 

A tar.gz file is a form of archive, so you can try unpacking it and seeing what's inside.  That might help you figure out what you need to do.  Sometimes installing software [for example, flash player] is as easy as copying a file into a few folders.

Also, it might be easier to see if there is a ".deb" file available for the program you are trying to install, because a .deb file pretty much configures everything for you through Synaptic Package Manager. 
Unless it's flash player.  DO NOT try to install flash player from ".deb"... it could cause severe problems with your package manager.

---

### Post by ibuclaw on 2009-12-05
> **acidpiper said:**
> Please could someone tell me how to install a tar.gz file, I have several programmes i have downloaded but don't know how to install, i have searched and found nothing - is this cause it is really easy?

Thanks in advance

Where did you download these files?

A tar.gz is just a zip file.
My initial assumption is that the source code for these applications is kept inside. If that is the case you have to build it yourself.

See here for the moderately simple guide to ./configure; make; make install.
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

But it might just be worth seeing if the software is already available in the Ubuntu software repository first.
(hint: the Software Centre probably won't have terminal-based applications, so have a look in Synaptic first).

Regards
Iain

---

### Post by acidpiper on 2009-12-05
I have downloaded some video editing software - i know that Kino is available but i wanted to try a few, and i have discovered the different themes you can download
are tar.gz and and tar.bz the same?

Thanks

---

### Post by kevdog on 2009-12-05
tar is a tape archive (or one big file where all the individual files are attached end to end) and gz and bz2 are the compression schemes.  gz = gzip and bz2 = bzip2.  bzip2 usually provides better compression efficiency but is slower.  gz is older and more widely known and used but probably more efficient.  There are other newer compression schemes you probably might have heard of also: zip, lzma, lzip, lz, 7zip, etc.  

To unzip a tar.gz file its:
tar zxvf <archive.tar.gz>

To unzip a tar.bz2 file or archive its:
tar jxvf <archive.tar.bz2>

---

### Post by ibuclaw on 2009-12-05
> **acidpiper said:**
> I have downloaded some video editing software - i know that Kino is available but i wanted to try a few, and i have discovered the different themes you can download
are tar.gz and and tar.bz the same?

Thanks

.tar.gz and tar.bz2 are both zip archives.

They differ in that bz2 has a slightly better compression algorithm than gz - but is not as quick at decompressing for seldom reasons.

Which site are you downloading these from? That would give a hint as to **what** the contents are and **where** the contents is intended.

Regards
Iain

---

### Post by JBAlaska on 2009-12-05
Often there is a README file, that *may* give install instructions.

---

