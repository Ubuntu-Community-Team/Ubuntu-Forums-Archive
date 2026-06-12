---
title: "Running setup.sh"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by scrooks on 2010-11-15
I have seen similar threads to this, but have been unable to successfully recreate them. Perhaps someone could assist me.

I "unzipped" the tar.gz file in question and it resides on my desktop in a folder "Webmin-1.520." Naturally, I want to initiate the program now via setup.sh, but am confused as to the next step.

I figure that I have to access the directory in terminal, so I ran "cd ~/Desktop," and I have a feeling I need to get inside the folder. Unfortunately, this is as far as I got. Is part of the problem the location of the folder? Should I create a directory for it?

If this is not enough information I will try to provide more.

Thank you

---

### Post by rampageoberon on 2010-11-15
Hi,

Firstly before you run any scripts on your system its best to know (perhaps read the script if it makes sense to you). Webmin scripts should be okay but always good to check.

To run it you might need root so precede below command with sudo

```
~/Desktop/Webmin-1.520/setup.sh
```

Hope that helps.

---

