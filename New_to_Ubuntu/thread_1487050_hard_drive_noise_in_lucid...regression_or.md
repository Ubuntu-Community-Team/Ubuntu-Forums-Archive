---
title: "hard drive noise in lucid...regression or ?"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by Knacker on 2010-05-18
Hi,
I've been using ubuntu for a while. Ages ago, I (and many others) had a problem with rhythmic hard drive clicking. As I recall, the root of the problem had something to do with ubuntu querying the drive too often (I'm still too much of a doofus to remember or really understand what exactly that means...). There were work arounds and then, I think, it was fixed. 

I'm getting the same rhythmic clicking noise, I've looked around and not found anything new on this (all posts date from '08), so I'm wondering if this is something that others are experiencing, if there's something wrong with my drive and if the same procedures for stopping the problem still apply from 2008. 

Anyone smarter than me have any ideas or suggestions about this?

Many thanks in advance!

(running ubuntu 10.04, updated, on a Lenovo T61p)

---

### Post by QIII on 2010-05-18
Several possibilities.

Memory/Swap:  Are you using a lot of physical memory and swap?  If your are consistently pegging your memory and using swap, the drive will have to work to find what it has squirreled away there.

Bad sectors:  Your drive may be continuously attempting to read bad sectors, which it can't do.  So it keeps trying and trying.

Mechanical faults:  Bad spindle or loose components.

Head Crash:  The worst of all.  Your drive is physically damaging the platters.  This will not resolve and you will eventually lose the drive and all of your data.  This is a job for your friendly data-recovery specialist, who will gladly empty your wallet.

Is your drive SMART enabled?

---

### Post by Knacker on 2010-05-19
thanks so much for replying! 

i just assumed that it was a software/ubuntu problem. looks like i've got some potential issues with my drive itself that i need to look into. 

drive is SMART enabled and showing at least one scary indicator (airflow temperature) -- doesn't exactly explain the noise i was having -- which doesn't sound like mechanical disk failure, but still maybe warrants a disk replacement. 

still interested in hearing about anyone else that has encountered this, but for the moment, i'll mark this as solved and try to find money for a new HDD. 

thanks again!:)

---

### Post by zemex34 on 2010-10-24
[http://ubuntuforums.org/showthread.php?p=10013044#post10013044](http://ubuntuforums.org/showthread.php?p=10013044#post10013044)

---

### Post by HermanAB on 2010-10-24
$ sudo service syslog stop

---

