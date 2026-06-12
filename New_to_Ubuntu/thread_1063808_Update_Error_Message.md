---
title: "Update Error Message"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by AnimalMagic on 2009-02-08
I have started getting the following error when attempting to update ubuntu 8.04 64 bit:

> 
E: /var/cache/apt/archives/python-apt_0.7.4ubuntu7.4_amd64.deb: unable to open files list file for package `libebook1.2-9'


Strange thing is that I have 3 nearly identical machines all running 64 bit Ubuntu and two have updated just fine, but one is having this error. Any ideas?

---

### Post by taurus on 2009-02-08
Maybe a bad download.  Close update manager, add/remove, or synaptic if you have it open.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by AnimalMagic on 2009-02-08
No go... :-(

> 
Fetched 3403kB in 7s (460kB/s)                                                 
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/python-apt_0.7.4ubuntu7.4_amd64.deb (--unpack):
 files list file for package `libebook1.2-9' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/python-apt_0.7.4ubuntu7.4_amd64.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by houstonbofh on 2009-02-08
> **AnimalMagic said:**
> I have started getting the following error when attempting to update ubuntu 8.04 64 bit:



Strange thing is that I have 3 nearly identical machines all running 64 bit Ubuntu and two have updated just fine, but one is having this error. Any ideas?

Get a thumb drive and copy /var/cache/apt/archives/python-apt_0.7.4ubuntu7.4_amd64.deb from a good one to the bad one.  You got a bad download.  You will need sudo to write to /var/cache/apt/archives/ .

---

### Post by AnimalMagic on 2009-02-08
So where do I get a good one from ? :-)

---

### Post by taurus on 2009-02-08
Probably from one of the other "3 nearly identical machines all running 64 bit Ubuntu".

---

### Post by AnimalMagic on 2009-02-08
Yes, I figured that out for myself :-)

However it still doesn't work, same message... I'm thinking something else has been corrupted somewhere, but I have no idea where to look... :-(

---

### Post by taurus on 2009-02-08
Maybe /etc/apt/sources.list!

```
cat /etc/apt/sources.list
```

---

### Post by AnimalMagic on 2009-02-08
/etc/apt/sources.list appears to be equal with one of the other machines.

I unchecked the python update and got the same message with the other packages, so I think the problem lies elsewhere.

---

### Post by houstonbofh on 2009-02-08
> files list file for package `libebook1.2-9' contains empty filename
Try looking for libebook1.2-9 as well.  You can go to a known good system with the same architecture, and tar up the /var/cache/apt/archives directroy.  Leave out the **lock** file, and the directory in there.  Then wipe the directory on the broken system and extract the tar there.  Or if you have a fast connection, wipe the directory and update again.

---

