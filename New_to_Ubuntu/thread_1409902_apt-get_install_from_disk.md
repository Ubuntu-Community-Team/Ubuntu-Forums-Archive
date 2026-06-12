---
title: "apt-get install from disk?"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by mdewet on 2010-02-18
Hi,

I recently installed the KDE desktop on my 9.04 virtual machine on a windows host just to check it out. 
```
sudo apt-get install kde
```
I found that I quite like it and would like to install it on another Ubuntu 9.04 machine also.

I have a very slow connection, so I would like to avoid downloading it again through apt-get install.  

Is there a way to retrieve the files downloaded the first time and using them to install KDE on the other Ubuntu system?

Thanks
Mdw

---

### Post by lijcam on 2010-02-18
Yes all deb package are cached in /var/cache/apt/archives

Copy all the debs to your other machine and rerun ```
sudo apt-get install kde
```

---

### Post by mdewet on 2010-02-18
Thanks Lijcam for the quick reply!

---

