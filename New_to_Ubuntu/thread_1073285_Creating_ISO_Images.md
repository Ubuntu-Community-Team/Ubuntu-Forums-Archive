---
title: "Creating ISO Images"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by psychx on 2009-02-18
What program would you recommend for creating a standard ISO file from a file directory? I searched and found something about mkisofs - but have not gotten it to work. Any suggestions are appreciated, thanks!

---

### Post by Doug11 on 2009-02-18
Have you tried to run magiciso in wine?

---

### Post by konqueror7 on 2009-02-18
have you tried 'ISO Master'? its in the repos, its i usually use...

---

### Post by binbash on 2009-02-18
mkisofs -V label-name -r /home/asdasd/directoryname/asdasd/name/ > iso-image.iso

---

### Post by psychx on 2009-02-18
When executing the mkisofs command, I get this error:

genisoimage: Directories too deep for 'directory name here' (7) max is 6.

Can I change the max directories allowed?

---

### Post by binbash on 2009-02-18
Hmm never saw this error but i think this will fix that : 

Cut the directory which you gonna make iso and paste it to home folder than re-try to make iso  :)

---

### Post by psychx on 2009-02-18
I thought it would fix it, but still getting the same error. It is because of the CD in which I need to make, requires there to be about 8 directories deep at one point.

---

### Post by binbash on 2009-02-18
Yah that is the error.Check man genisoimage

PS : man genisoimage says that you can ignore that directory sh.it with -D prefix.Try this but first read the man page of genisoimage! : 

mkisofs -V label-name -r /home/asdasd/directoryname/asdasd/name/ > iso-image.iso -D

---

### Post by Archmage on 2009-02-18
I think k3b can do the trick, too.

---

### Post by psychx on 2009-02-18
Perfect! Thank you very much!

---

