---
title: "Update Manager Hung"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by lotusalive on 2009-05-18
My new Jaunty update is great !  But, suddenly the Update Manager won't install, just hangs...  I have it set to install all updates in the background.  Was using belnet repo for about 2 days, and it hung, by itself, which I fixed with a sudo apt-get command, YAY...  But still Update Manager is hung with these, and won't install them:

libmgp123-0, and mpg213

Version 1.4.3-4ubuntu1.1: 

  * SECURITY UPDATE: Integer signedness error in the store_id3_text function
    in the ID3v2 code in mpg123 before 1.7.2 allows remote attackers to cause
    a denial of service (out-of-bounds memory access) and possibly execute
    arbitrary code via an ID3 tag with a negative encoding value. (LP: 370031).
   - src/libmpg123/id3.c: Inline patch from upstream SVN rev 1920.
   - [http://www.mpg123.org/cgi-bin/viewvc.cgi/tags/1.7.2/?view=log](http://www.mpg123.org/cgi-bin/viewvc.cgi/tags/1.7.2/?view=log)
   - CVE-2009-1301

And Terminal does this:

sol@sol-desktop:~$ sudo apt-get install updates
[sudo] password for sol: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package updates
sol@sol-desktop:~$ 

Any suggestions welcome.  Thanks in advance FOR EVERYTHING !

---

### Post by taurus on 2009-05-18
There is no updates package.  I believe you are looking for these two commands from a terminal.

```
sudo apt-get **update**
sudo apt-get **upgrade**
```

---

### Post by lotusalive on 2009-05-18
YE-AH !  That worked !  I feel all light-headed !  The computer understood it, even tho' I did not !  lol  ):P    :)  Thank you Taurus !

---

### Post by lotusalive on 2009-06-02
Will somebody help me by guiding me to a good dual-boot in Jaunty with 

Windows...?  Only because: a) Where I need to go for business requires 

Internet Explorer... (yuk), and b) My graphics card isn't updated enough

for going to Second Life in Linux...(2 year old Dell emachine with Intel 

card...)

---

