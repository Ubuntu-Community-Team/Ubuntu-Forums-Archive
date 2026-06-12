---
title: "Reading and writing to nfs shares"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by saultpastor on 2007-01-17
This should be a quick question...

I have a laptop that travels from my home to my office.  It has Linux Mint on it.  It is set up to share files with a desktop at home and one at the office.  Here is my fstab to mount them:

The home box
```
192.168.0.101:/home/craig/Shared /media/HomeNetwork nfs user,rw
```

The office box
```
192.168.1.101:/home/sue/Shared /media/OfficeNetwork nfs user,rw
```

Both the home and office box are running PCLinuxOS, and the nfs commands to share files are identical:

```
all_squash,anonuid=65534,anongid=65534,async,insecure,rw
```

At the office I have full access to the shared folder (can copy, delete make folders etc.) from my laptop, but on the home box I can only read/transfer the files to my laptop.  I want to have full access to both.

Thanks for your time

---

### Post by lhtown on 2007-01-18
I don't think I understand. Where does Ubuntu come into this? Maybe the PCLinux forum would be a more appropriate venue or [www.linuxquestions.org](www.linuxquestions.org)

BTW, Ubuntu is a great operating system that is really easy to use if you haven't already tried it, you should download the liveCD and give it a whirl. I won't promise that networking will be any easier, at least yet, though.

---

### Post by saultpastor on 2007-04-09
> **lhtown said:**
> I don't think I understand. Where does Ubuntu come into this? Maybe the PCLinux forum would be a more appropriate venue or [www.linuxquestions.org](www.linuxquestions.org)

BTW, Ubuntu is a great operating system that is really easy to use if you haven't already tried it, you should download the liveCD and give it a whirl. I won't promise that networking will be any easier, at least yet, though.


Nice, thanks for the help.  If you read I am running Linux Mint (ubuntu based) on my laptop.  I happen to be an Ubuntu user since Hoary, PCLinuxOS box for my kids and one for my secretary which btw, set this up automatically, I wanted to get some ideas from ubuntu since that was the distro I was having problems connecting with.

If you don't have an answer, don't answer.

I figured it out on my own.

---

