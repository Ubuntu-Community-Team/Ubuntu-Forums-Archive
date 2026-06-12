---
title: "brother Printer"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by dbvoss on 2011-07-26
Hello every one.
                I am trying to install my Brother DCP J315W printer in ubuntu 11.04. But i just cannot get it to work. Can any one please help?

dbvoss:

---

### Post by walt.smith1960 on 2011-07-26
Hi and welcome.

Have you looked here?
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-J315W](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-J315W)

If so, what is it doing or not doing?  What type connection are you using? USB or Wireless?

---

### Post by lisati on 2011-07-26
*Thread moved to **Absolute Beginner Talk**.*

---

### Post by dbvoss on 2011-07-27
Hello walt,
            Thanks for your reply. I am using a USB connection i have installed the drivers from the Brother page but when i try to print nothing happens. When i try to print a test page i get this message -Cubs server error

There was an error during the CUPS operation: 'client-error-document-format-not-supported'.

---

### Post by walt.smith1960 on 2011-07-27
> **dbvoss said:**
> Hello walt,
            Thanks for your reply. I am using a USB connection i have installed the drivers from the Brother page but when i try to print nothing happens. When i try to print a test page i get this message -Cubs server error

There was an error during the CUPS operation: 'client-error-document-format-not-supported'.

I've not run into that error message so I'm just guessing.  Have you tried printing from different sources?  Something like from a web browser or office type document?  Linux support is via email.  Their Linux support people are in Japan but they do check and respond to their email.  There may be language issues though.  I asked about support for the built-in memory card readers.  The reply was that the card readers were supported by network connections but not by USB connections.  The truth is the opposite; the card reader is recognized under USB but not under wireless networking.  You've probably checked this but you could type the following in a web browser:  [http://localhost:631](http://localhost:631) and see if there's anything obviously amiss there.

---

### Post by dbvoss on 2011-07-28
Hello again Walt
                  I have now solved the problem, many thanks for your help.

dbvoss::

---

### Post by beew on 2011-07-28
> **dbvoss said:**
> Hello again Walt
                  I have now solved the problem, many thanks for your help.

dbvoss::

If you have solved your problem you should post your solution in case someone else comes across the same problem and needs help. It is bad manner to come and seek help and then just say I solved the problem and take off without contributing back. :)

---

### Post by dbvoss on 2011-07-30
The problem was with the driver I think. I downloaded and installed it from the Brother site three times, and on the third time it worked OK
dbvoss

---

### Post by walt.smith1960 on 2011-07-30
> **dbvoss said:**
> The problem was with the driver I think. I downloaded and installed it from the Brother site three times, and on the third time it worked OK
dbvoss

I'm glad you were able to solve your problem.  For others who may have similar issues and check this thread, the Brother drivers are 32 bit.  If you're using a 64 bit system, you must use command line installation.  If you're using 32 bit Ubuntu, you can just do the "before installation" steps as required (I think there are only two that apply) then use a package installer, Ubuntu software center or Gdebi.

---

