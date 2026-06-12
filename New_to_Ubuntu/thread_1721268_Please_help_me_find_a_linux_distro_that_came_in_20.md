---
title: "Please help me find a linux distro that came in 2006"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by chandin69 on 2011-04-04
I'm trying to follow the instructions in this PDF:
[http://mason.gmu.edu/~kthirum1/FILES/ns2.pdf](http://mason.gmu.edu/~kthirum1/FILES/ns2.pdf)

It's dated December 3rd 2006. Its to install this software called NS(Network simulator)

Can someone please tell me where I could find an ISO file for a decent linux distro that came out before that date so the instructions in the pdf can be applied?

I plan to use it in a virtual machine.

Any help is much appreciated

---

### Post by snowpine on 2011-04-04
You can find old Ubuntu releases here:

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by Rubi1200 on 2011-04-04
You could try searching on Distrowatch:
[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by conneco on 2011-04-04
Is it to use a specfic version because network simulator is [http://www.nsnam.org/]("http://www.nsnam.org/")  < there

---

### Post by chandin69 on 2011-04-04
Thanks. I'm downloading ubuntu 6.10 edgy at the moment.

If I execute the following after installing 6.10
```
sudo apt-get install tcl8.4 sudo apt-get install tcl8.4-dev
sudo apt-get install tk8.4 sudo apt-get install tk8.4-dev

```

Would I get the same versions that the author of the PDF was expecting(Since this was meant for 2006)?

If not how can i get older versions/compatible versions of those programs that would work?

---

### Post by madmax75 on 2011-04-04
You might have problems donwloading packages for 6.10 Egdy, since it probably is not supported anymore.

I know that they keep packages for older releases around somewhere, but can't remember where exactly. Maybe this will help you:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by davidmohammed on 2011-04-04
this sounds like a lot of work -

look [here]("https://launchpad.net/~wouterh/+archive/ppa") - Wouter Horre has a ppa that you can directly install ns-2 on ubuntu.

---

### Post by snowpine on 2011-04-04
> **chandin69 said:**
> Thanks. I'm downloading ubuntu 6.10 edgy at the moment.

If I execute the following after installing 6.10
```
sudo apt-get install tcl8.4 sudo apt-get install tcl8.4-dev
sudo apt-get install tk8.4 sudo apt-get install tk8.4-dev

```

Would I get the same versions that the author of the PDF was expecting(Since this was meant for 2006)?

If not how can i get older versions/compatible versions of those programs that would work?

6.10 has reached its "end of life." This means no more updates, bug fixes, security patches, new software, etc. 

I think you'll need to edit your software sources to point to "old-releases.ubuntu.com" if you want to install anything from the 6.10 repos. Can't really say for sure, as I neither use nor recommend using obsolete releases.

---

### Post by chandin69 on 2011-04-04
I need to use NS2 with EURANE extensions.
Eurane only works with NS upto version 2.30.

---

### Post by davidmohammed on 2011-04-04
This is a very specific question on a specialized subject - so you may not get many direct answers.

However - given that someone has managed to produce a very recent ppa for NS-2, I strongly suspect that you will be able to compile the software source directly using the latest ubuntu.

Where the original instructions said use a particular version of tcl, for example,  I would assume the current versions of tcl in the current ubuntu will be OK to compile against.

---

### Post by jmszr on 2011-04-04
chandin69,

This may be of some help: [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) also [https://soniahamilton.wordpress.com/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/](https://soniahamilton.wordpress.com/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/) .

---

