---
title: "Error with sources.list file"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by ericstrom on 2011-03-14
Currently using Ubuntu Lucid

I am trying to add the following entry to my /etc/apt/sources.list file so I can download some software:

deb [http://lib.stat.cmu.edu/R/CRAN/bin/linux/ubuntu](http://lib.stat.cmu.edu/R/CRAN/bin/linux/ubuntu) lucid/

I double click on the file and the software sources box opens. I select the "other sources" tab and then select add. I add the above entry and hit add source. Then click "close" button. Then I get a message saying :

"The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software.

You need a working internet connection to continue."

I have two selections at that point ....Reload or Close. I select Reload and get a message that an error has occured:

W: GPG error: [http://lib.stat.cmu.edu](http://lib.stat.cmu.edu) lucid/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 51716619E084DAB9

What does this mean, what am I doing wrong and how do I fix it ?

---

### Post by mikewhatever on 2011-03-14
From the link:
```
**gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9**

and then feed it to apt-key with

**gpg -a --export E084DAB9 | sudo apt-key add -**

```

---

