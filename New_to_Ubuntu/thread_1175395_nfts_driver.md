---
title: "nfts driver"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by Harpie Queen on 2009-06-01
Hi, I'd like to get a driver for my nfts external hard drive. I can do an install either graphically, through terminal (give me full command though please, I am new) or by downloading the deb and double clicking on it.

Thanks!

---

### Post by Bodsda on 2009-06-01
Hi,

The two main utilities needed for interacting with ntfs filesystems are ntfs-3g and ntfsprogs

```
sudo apt-get install ntfs-3g ntfsprogs
```

Hope this helps,

Bodsda

---

### Post by Lemuel111 on 2009-06-01
Hi I'm totally new to Linux and I have downloaded several files/drivers onto my Ubuntu 9 desktop but I'm struggling to find how to install them. I have extracted the files but I don't know what to do next. Can anyone help?

---

### Post by Didius Falco on 2009-06-01
Hi Lemuel111 and welcome to the Ubuntu forums!

You need to start a new thread. It's considered impolite to "hijack" someone elses' thread. Besides, you'll get a lot more response with a new thread, especially if you give it a title that clearly indicates the problem you are having.

It helps a lot if you give as much information as you can in the first post, too. In your case, you should give the complete names, including the extensions (the part after the "." in the file name) of the files you are trying to install, and any other information you think might help us to help you.


Regards,

Didius

---

### Post by Lemuel111 on 2009-06-01
Sorry about that. How do I start a new thread?

---

### Post by neo.patrix on 2009-06-01
What kind of packages you have downloaded? Debian? Best thing would be install packages via package-manager, rather than random downloads.

---

### Post by Lemuel111 on 2009-06-01
RutilTv014; wpa_supplicant-0.49 & rtl8181 if that means anything to you.

---

### Post by neo.patrix on 2009-06-01
> **Didius Falco said:**
> 
You need to start a new thread. It's considered impolite to "hijack" someone elses' thread. Besides, you'll get a lot more response with a new thread, especially if you give it a title that clearly indicates the problem you are having.



Maybe you need a new thread...

No those files do not mean much to me. But they do not look like Ubuntu/Debian packages either. Are those driver files that you normally use for installing on windows or are those files you have downloaded from certain website with big fat label "Linux Support"?

---

### Post by Lemuel111 on 2009-06-01
Basically I'm having problems connecting to the internet via my wireless G+ Belkin USB adapter. I have read a number of sites so called solving the problem but my lack of knowledge means I'm still not solving the problem. For example "file:///media/disk/Using the Belkin USB Wireless G key under Linux.htm" recommends a download. Instructions = 1. download the archive 2. expand it (how I ask??) 3. go into archive's directory with cd.
Tried 1. & 3. but then Terminal tells me that I have gtk+ 2.0 missing!! I download a gtk+ bundle but then the 'read me' says only install what you need & use this package if you know what you are doing (which I don't!). So I'm stuck as I don't want to do anything I shouldn't.

---

