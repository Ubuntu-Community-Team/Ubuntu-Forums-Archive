---
title: "tar command"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by navaneethan on 2009-07-15
> % tar -xvzf filename.tar.gz


In this command x is used to extract this archieve

can we this command without x ?

what happens?

what is the difference between archieve and zip?

---

### Post by starcraft.man on 2009-07-15
In the command, x indicates extract from tar, v is the verbose option, and z indicates your combining it with gunzip (removes the gz).

Without x option, you aren't extracting, so no.

As to the difference between archive and zip, it's quite simple. Tar is an archiving utility, all it does is make all the files into one big package. It doesn't actually compress the archive, at all, in fact you'll usually find tar files to be bigger than sum totals of the files. Gzip is the compression you run on the package after, this then as you can imagine compresses the tar archive down to reduce space. When your using something like zip or rar on Windows, happens in one step.

---

### Post by ~sHyLoCk~ on 2009-07-15
For [more info]("http://unixhelp.ed.ac.uk/CGI/man-cgi?tar")

---

### Post by n8bounds on 2009-07-15
Always a good idea to read the supplied manuals. Lots of people spend/spent lots of time making them easy for you to get. They are almost all online, as mentioned previously, or available from your terminal. Just type there:

man tar

and press Enter. Just press Q to leave that screen. Page up/down and arrows work as you might expect.

---

