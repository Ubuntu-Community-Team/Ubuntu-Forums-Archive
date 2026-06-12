---
title: "Unable to lookup (name) via gethostbyname()"
date: 2005-09-17
forum: Networking &amp; Wireless
---

### Post by websurrfr on 2005-09-17
I just reinstalled Ubuntu and now my network cards don't work.  They worked perfectly fine right away with my last installation.  Now I get an error whenever I try to use a sudo command that says "unable to lookup danlaptop via gethostbyname().  It also gives me this error as soon as I login to Ubuntu.  My wireless card is eth1.  Anyone have any suggestions?  Thanks.

Also, typing ifconfig does nothing.  (No errors, or command not available, just nothing).  Typing iwconfig displays lo, eth0, and sit0 as no wireless extensions.  eth1 displays my wireless card.

---

### Post by bsussman on 2005-09-17
A complete wipeout and reinstall? Sounds like some things are left over that depend on your machine name and it is now different.

type in:
 ```
 > uname -a
``` 
 
 if the name of your machine (second field) is not danlaptop then that may explain it.  I just reproduced this on my machine.


Although the message appears to point to internet communications, it is not. Many functions will use the communications layer(s) even when dealing locally.

have you set a root password?  this may be inconvenient to fix other wise.

No use going through the steps until you report back what your machine name is now - I do not want to mislead you!

---

### Post by websurrfr on 2005-09-17
Thank you for your reply.  the result of uname -a was:

Linux danlaptop 2.6.12-8-386 #1 Tue Aug 30 22:41:30 BST 2005 i 686 GNU/Linux


And I have not set a root password...not really sure how to either


my prompt in the shell is daniellaptop@danlaptop:~$ if that helps at all

---

### Post by websurrfr on 2005-09-18
I managed to fix the problem by formatting and installing ubuntu again.  I'm pretty sure I did it exactly the same way as the last install too...weird

---

### Post by bsussman on 2005-09-18
Good that it is working as expected now.

The details and complexities are so great that we will probbly never know how it got messed up.

When my clients call me and ask "What happened?" I usually tell them to ship me the video tapes from the cameras pointed at their kb, screen and brain ;-)

---

