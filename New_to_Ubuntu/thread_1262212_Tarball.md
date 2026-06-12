---
title: "Tarball?"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Shenachie on 2009-09-09
This is going to be a classic no doubt but I have searched through the forum to no avail.

I bought a rather expensive Linux mag and it said blah blah tarball routine blah blah..

Right thinks I this must be very basic stuff and not worthy of explaining. which is all very well and good if you are on the first step and not ground level...LOL

Can some kind person point me in the right direction as to how and what a tarball does please?

Thanks in advance.

---

### Post by credobyte on 2009-09-09
> [COLOR=Gray]DEFINITION -[/COLOR] Tarball is a jargon term for a tar archive - a group of files collected together as one. The term suggests a ball of tar, the sticky coal derivative used as an adherent and sealant in roofing and other construction work. Tar (for Tape ARchive) is a Unix command that creates a single file called an archive from a number of specified files or extracts (separates) the files from such an archive. A tar archive has the file suffix .tar. The files in a tar archive are not compressed, just gathered together in one file. A popular archive handler for Windows systems, WinZip, can be used to extract the files from a tar archive. Stuffit Expander, an archive handler used for Macintosh systems, also extracts files from a tar archive. 


Enjoy :)

---

### Post by Shenachie on 2009-09-09
Thanks Credobyte.

Not sure what that means but no doubt it is useful. :)

Shenachie

---

### Post by credobyte on 2009-09-09
> **Shenachie said:**
> Thanks Credobyte.

Not sure what that means but no doubt it is useful. :)

Shenachie

It's just a type of archive - similar to RAR/ZIP's ;)

---

### Post by davo11 on 2009-09-09
A tarball is basically a collection of files that together when _compiled_ make up a program. The programs are provided in tarballs so you can modify them and so they are compatible with any program. Generally they come in .tar.bz2/.tar.gz. The .bz2 and .gz are just compression extensions used to make the file smaller, think like .zip in windows.
I'll tell you what to do with these but advise that, to install programs use synaptic package manager or find a _binary_ for your program. Synaptic will do it all for you and if you find the binary for your platform you're all set (apart from dependencies which I'll explain later).
Ok. Here we go. To get rid of the .bz2 or .gz just right click the file and click extract. Now open up the terminal applications>accessories>terminal and navigate to the folder the file is in "cd /???/???/???/???.tar". Now type "tar -xvf <filename>". This uncompresses it and lets you get at the files inside.
What to do with those files you'll have to look somewhere else. I'm needed somewhere else!

---

### Post by jonobr on 2009-09-09
on my first training coarse for linux, (a while ago now) I cam out with the same problem,.

Ok, what am I missing with tar.
The way it was explained, I figured it was some way of compressing a bunch of files.

I explained it to my linux Suse loving boss at the time, and man did he berate me.

He gave a very animated demonstration of how it was like putting a whole load of gaffer tape around a bunch of files,
Then he performed another jiration showing how that gaffer taped bundled could then be compressed.

Reading your post made me laugh out loud thinking of my old boss and his funny way,.


Thanks

jonobr

---

### Post by Volt9000 on 2009-09-09
It is my understanding, and someone please correct me if I'm wrong here, that a .tar file is not a compressed archive but rather just a collection of files without any compression, all thrown together.

Exactly like jonobr's boss explained...

---

### Post by jonobr on 2009-09-09
yes, but your missing the habd and body movements that accompanied the explanation.....

:-)

---

### Post by mbsullivan on 2009-09-09
> 
It is my understanding, and someone please correct me if I'm wrong here, that a .tar file is not a compressed archive but rather just a collection of files without any compression, all thrown together.

Exactly like jonobr's boss explained...

That's right... 

In practice, though, I think when people *talk* about, *use*, or *distribute* "tarballs", they normally are tarred and then compressed, like so:

[bunch of files] -> tar -> tarball -> < zip > -> compressed tarball

Where < zip > is normally either "gzip" or "bz2" type compression. Thus, tarballs, in practice, will probably have extensions of .tar, .tar.gz, .tgz, or .tar.bz2.

Mike

PS: In summation: I'd say that a tarball is an archive file (which is sometimes compressed). It is *typically* used as a distribution-independent way to distribute source code.

Some Linux distributions, such as [Slackware]("http://en.wikipedia.org/wiki/Slackware"), use tarballs in their package management systems, sort of like Ubuntu uses .deb files. Does this help? :)

---

### Post by relay_man on 2009-09-09
Tar/tarball.... everything you wanted to know and then some.  :)

[http://kb.iu.edu/data/acfi.html](http://kb.iu.edu/data/acfi.html)

---

