---
title: "hard drive space depleting"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by g3k0 on 2010-09-30
I have a linux box which has its disk space depleting at the rate of 5.4 megs/minute.  If the 65Gig partition was empty, it would take a little over 8 days to be filled.  I only have 3.6Gigs available at the moment.

How can I find whatever process is causing the disk to be used so quickly?? I have been playing with the du command all day looking for the file in question.  Any pointers(no pun intended)???

Thanks

---

### Post by migs73 on 2010-09-30
Type 'top' into terminal, it'll tell you what processes are running and using CPU time. It'll maybe give you a pointer.

---

### Post by g3k0 on 2010-09-30
Thanks for the tip.

I found a file that is increasing in size rapidly.  The file is /var/bandwidth

I find it strange though that at the moment it is only 229 but increasing at about 6Megs a minute.

Anyone know the purpose of this file, what is writing to it, and why mine is increasing so rapidly?

Thanks

---

