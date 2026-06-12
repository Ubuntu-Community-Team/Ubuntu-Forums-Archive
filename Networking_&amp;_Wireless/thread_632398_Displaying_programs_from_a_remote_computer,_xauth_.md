---
title: "Displaying programs from a remote computer, xauth problem?"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by nkjvcjs on 2007-12-05
I am logging into a Beowulf cluster at school from my laptop, and trying to run GaussView

I am following the instructions at this site:
[http://www.uic.edu/depts/accc/hardware/argo-new/gaussview.html](http://www.uic.edu/depts/accc/hardware/argo-new/gaussview.html)

I can't use simple X forwarding since I have to submit the job to run the program to one of the slave nodes.  Xhost is also disabled on the cluster, so I have to use xauth.

On my laptop, I do 
xauth list:
and get back:
neflinux/unix:0  MIT-MAGIC-COOKIE-1  a52dfed041a5bfb43457c17327bbf870
localhost.localdomain/unix:0  MIT-MAGIC-COOKIE-1  a52dfed041a5bfb43457c17327bbf870

so I have tried adding both lines via xauth add on argo,

but, when I go to the next set of directions, I am listed as at mbrbc048.XXXXXXXX.uic.edu

since this is not what is in the xauth, when I submit my little shell script to the node, it cannot connect to my xserver.

Any suggestions?

Thanks so much,

Nicole

---

