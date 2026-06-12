---
title: "how to: Restore UBUNTU to original after many changes"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by squrl on 2010-09-22
I have searched but find nothing. 
Is it possible to restore Ubuntu to original after many additions changes and modifications. I guess I'm asking if you can load the original files to get back to square one without doing a complete reinstall. 
I have saved th /home directory including the hidden files with the idea of starting over from scratch but I'm not even sure that will work. 

Any suggestions appreciated or ideas where to start looking.

Thanks

Version 10-04 on a P4 Dell

---

### Post by spiky001 on 2010-09-22
I havn,t seen an answer for this be prepared for reinstall i,m preaty sure you cant do it

---

### Post by theozzlives on 2010-09-22
If you backed up /home,then your cool. This time make a separate /home partition, then you won't have to back up if you do a fresh install again. I know I re-installed many times when I was new.

---

### Post by Jesus_Valdez on 2010-09-22
What about the "Computer Janitor"?

---

### Post by walt.smith1960 on 2010-09-22
The only solution I know is to clone the partitions(s).  Keep a recent functioning backup and I keep an image of the partition after installing restricted extras, printers, etc.  If an operating system becomes too flaky, I delete the partition, recreate it and restore the partition image. I'm back in business in less than 30 minutes without having to reconfigure everything.  I haven't used it but clonezilla gets pretty good reviews. I use shareware that I paid for [http://www.terabyteunlimited.com/image-for-linux.htm](http://www.terabyteunlimited.com/image-for-linux.htm).  It has saved me hours of disk shuffling and driver searching etc. etc.  Image for Linux does support incremental backups which clonezilla so far doesn't.

---

### Post by Mark Phelps on 2010-09-23
> **Jesus_Valdez said:**
> What about the "Computer Janitor"?

NO, repeat again, NO!

I made the mistake of using this "cleaner" and it rendered my PC unbootable.

Same risk as using the registry "cleaners" in MS Windows.

Basically, there is no roll-back capability in Ubuntu.  Yes, you can uninstall apps and individual packages, but there is no equivalent of the System Restore function of MS Windows.

---

### Post by PriceChild on 2010-09-23
If you tell us what you've changed/modified then sure, we can help you revert it.

dpkg is capable of reverting packages to standard configurations.

---

