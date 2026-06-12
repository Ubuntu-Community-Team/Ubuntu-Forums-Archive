---
title: "XV - Image View"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by thraxsa on 2009-04-06
Hey All,

Has anyone been able to put XV ( popular image viewer) on Ubuntu 8.10 ?

I used it on red hat all the time, but it is not part of the Ubuntu distro.

Can it be installed without making a mess and causing other programs to fail ?

If so, how ? I did find a tutuorial on-line but it appears that some of the links needed to obtain some libs are broken : (

Can anyone help ???

Cheers

---

### Post by nandemonai on 2009-04-06
> **thraxsa said:**
> Hey All,

Has anyone been able to put XV ( popular image viewer) on Ubuntu 8.10 ?

I used it on red hat all the time, but it is not part of the Ubuntu distro.

Can it be installed without making a mess and causing other programs to fail ?

If so, how ? I did find a tutuorial on-line but it appears that some of the links needed to obtain some libs are broken : (

Can anyone help ???

Cheers

I'd never even heard about Xv to be honest. I had a quick look around and could only find xvattr and xzvg in the repos.

Wiki says this "xv is still present in Slackware Linux 12.2 and SUSE Linux 10.0, although it is no longer bundled with most distributions as several free alternatives exist."

I'd say based on the age of the program and the fact it doesn't appear to be worked on anymore is going to hinder your chances.

You could try compiling from source. gl ;)

---

### Post by thraxsa on 2009-04-06
> **nandemonai said:**
> I'd never even heard about Xv to be honest. I had a quick look around and could only find xvattr and xzvg in the repos.

Wiki says this "xv is still present in Slackware Linux 12.2 and SUSE Linux 10.0, although it is no longer bundled with most distributions as several free alternatives exist."

I'd say based on the age of the program and the fact it doesn't appear to be worked on anymore is going to hinder your chances.

You could try compiling from source. gl ;)

thanks for your reply - I have ImageMajick , so that does the job.  I can't be stuffed screwing around with libraries etc just to put on one viewing program.

---

### Post by andrew.46 on 2009-04-06
Hi nandemonai,

> **nandemonai said:**
> Wiki says this "xv is still present in Slackware Linux 12.2 and SUSE Linux 10.0, although it is no longer bundled with most distributions as several free alternatives exist."

Indeed it *is* still present on slackware 12, I attach a screenshot to show this great little viewer still works and works well :-).

Andrew

---

### Post by thraxsa on 2009-04-06
It is just a shame that I can't xv working with Ubuntu 8.10 ... or can I ???

Just looking at that pic makes me want to try to install again .. can anyone help ???

---

### Post by andrew.46 on 2009-04-07
Hi,

Well it was a bit of an ordeal and one of the patches has gone awol but I managed it :-). I poached the slackware sources + patches, installed the appropriate -dev files for Intrepid and finally compiled it. I attach a screenshot so I can claim my full geek glory......

But I would not be confident in guiding anybody else through this, the software has not been touched for a long time, there are 3 big patches to add in. But if anybody wants to try have a look at [the sources directory for slackware in the xap series]("http://slackware.osuosl.org/slackware-12.2/source/xap/xv/"), download the relevant dev files (lists available on various blogs and then go for it :-). 

All the best,

Andrew

---

### Post by thraxsa on 2010-03-06
I actually manage to compile it myself and get it all running .. here is the the link I followed to get it going.  I used it bask in the red hat days.  I am not at all familiar with compiling software, so if I can get it working anyone can ... : )

[http://www.ulich.org/hints/xv_ubuntu.html](http://www.ulich.org/hints/xv_ubuntu.html)

---

