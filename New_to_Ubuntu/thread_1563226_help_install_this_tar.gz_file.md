---
title: "help install this tar.gz file"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-08-28
installing these files still eludes me how would i extract and install this. i downloaded to my desktop
/home/ray/Desktop/clamav-0.96.2.tar.gz
tks i know others have asked before but still have problems

---

### Post by ranch hand on 2010-08-28
ClamAV should be on your computer now.  What is the benefit of what you have in tar?

What version of Ubuntu are you using?

---

### Post by rburkartjo on 2010-08-28
ranch the current anti virus version is out of date the current one is 0.96.2 and i would like to update. this seems to be a oncurring problem the repos are alway behind

---

### Post by rburkartjo on 2010-08-28
hey ranch off subject but have seem some of your tutorials they are great

---

### Post by Conzo on 2010-08-28
> **rburkartjo said:**
> installing these files still eludes me how would i extract and install this. i downloaded to my desktop
/home/ray/Desktop/clamav-0.96.2.tar.gz
tks i know others have asked before but still have problems


Best way to do this in the terminal

**Clam Antivirus** (to be listed as Virus Scanner in Applications > Accessories) **[http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)**

**sudo apt-get install clamav clamtk**

Operations available from a terminal session...

Update virus definitions: **sudo freshclam**

Scan files in your home directory: **sudo clamscan** 

Scan files in an entire directory: **sudo clamscan -r /<directory name>** 

Scan on the entire drive: **sudo clamscan -r /** 

Conzo!

---

### Post by ranch hand on 2010-08-28
If you double click on the bugger it should open in the archive manager and then you can extract it from there.

There should be a readme included that will tell you how to install it.

You probably better check to see if you have "build-essential" installed as you will need it on there.

---

### Post by ranch hand on 2010-08-28
Or better yet try the Conzo method.

I am not up on Clam at all as I feel no need to protect those that choose to use MS products.  This is not what I would call a good attitude but it is the one I have.  I do not recommend it to others.

---

### Post by rburkartjo on 2010-08-28
tks ranch will do tomorrow and if successful will mark thread as solved

---

