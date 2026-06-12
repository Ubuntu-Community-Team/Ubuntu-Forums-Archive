---
title: "Easy Home Network OS Install"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by expatCM on 2009-04-06
I am just planning for when version 9.04 is released where I will fresh install all machines.  I would like to install on one machine and copy or mount the CD on one machine and then install on four clients on the network.  My dream is to have more or less duplicated installations and to automate the process as much as possible.

I had been thinking of using Replicator which is in the repositories until I installed it and looked at the man page and the pdf user guide.  In 2004 I imagine that this was a great initiative but since there is still mention of use of a floppy I wonder if this is really for me.

I know that remastersys exists but this is not quite what I want to do.  I was wondering what else....  I would prefer to work through the network rather than walk round with a CD.

It seems to me that I could put an image of one install on the server and restore that but since the clients hardware is a bit different I wonder if there would be any headaches.

Can anyone make any recommendations of how to approach this?   I am not going to implement until May but I would like to start thinking the process through …....

---

### Post by nandemonai on 2009-04-06
[http://www.debuntu.org/how-to-unattended-ubuntu-network-install](http://www.debuntu.org/how-to-unattended-ubuntu-network-install)

---

### Post by halitech on 2009-04-06
you could use the network install using ssh but I'm not entirely sure how to do it. I know it requires use of a preseed file that you have to edit yourself but not much beyond that. I think you will still need to boot from a cd on each machine unless each machine can boot from the network and then you could set up a PXE boot system.

---

### Post by expatCM on 2009-04-06
I had never heard of debuntu.org ...  looked at the article and it does appear to be well presented and cover all the bases.  Thanks for sharing this.

The conclusion I came to was that in the time it would take to set his up I would be just as well off making a CD from one machine after finalizing the setup with remastersys and then walking round.

I guess it is "seek and yea shall find" but not always the solution you anticipated.....

---

