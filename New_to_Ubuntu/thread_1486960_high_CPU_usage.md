---
title: "high CPU usage"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by mustard greens on 2010-05-18
I am experiencing some type of phantom process running occasionally in my system to nearly 100% of my CPU while at idle.  this has persisted through a total hard drive reformat/reinstall of my system when upgrading to 10.04 (although I did keep my /home folder).  rebooting seems to help temporarily though it eventually comes back  
system monitor shows some type of unnamed listing in the first position with a shifting process id# and no CPU usage. (could not figure out how to post a screen shot here)  
also, I have found Gzip running occasionally at a high CPU% long after I have compressed/moved a file, though killing Gzip does not solve the overall problem.
another point is that system monitor sometimes (rarely) runs as high as 68% of CPU which doesnt seem quite right.
I have searched google/the forums and found multiple posts/bug reports which describe one process or another eating CPU/power in 10.04.  my sys monitor as well as top show no process eating the CPU.
any takers?

---

### Post by philinux on 2010-05-18
@mustard

As you are running lucid check the sticky in General Help re: Java. Bottom paragraph.

---

### Post by AshRice on 2010-05-18
Are you using any networked drives (NFS, sshfs)? I was experiencing similar issues which ceased when I started using the built in sftp instead.

Screenshot: have you tried the PrntScr Button?

---

### Post by mustard greens on 2010-05-18
thanks phil.  does this mean that sun java is a temp fix?

@ ash rice.  Im not sure what networked drives are, but Im pretty sure the answer is Im not.  I have a backup hard drive which is not currently powered though I have made backups during the last boot cycle.

as far as screen shots I can take the picture, I couldnt figure out how to attach without a url, or how to get a url for a picture anyway.

added note; I found metacity enabled under system>preferences>startup applications, even though I have enabled compiz.  unchecked metacity to see if that has any effect.

---

### Post by mike555 on 2010-05-18
for screenshots you can use a free service like ;  [http://tinypic.com/login.php](http://tinypic.com/login.php) , just upload a screenshot (it shouldn't be too big) and they will give you an address to give out .. just type the address to that picture in the forums.

---

