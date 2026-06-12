---
title: "Programme installation probs"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by John Hale on 2009-01-17
Hi Guys,
        I tried to install limewire today but halfway through the installation, it froze trying to install sunjava6-jre . I left it an hour and still no sign of the install bar moving, I tried ctrl-alt-del but I think it's a windows thing, so I just shutdown th computer. Now wen trying to over install I get the message below:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I then typed that in terminal, but get  "requested operation requires superuser privilege" and don't know how to do that I tried sudo -u name|password but with my own typed and can't workout what to do next why the installation failed and what to do.

John

---

### Post by ken22 on 2009-01-17
Just
```
sudo dpkg --configure -a
```

should do it.

---

### Post by John Hale on 2009-01-17
Now when I try to install limewire I get erroe satisfy all dependencies (broken cache)

how do I proceed?

Thanks

John

---

### Post by ken22 on 2009-01-17
How are you installing this?

Did you get the .deb from limewire.com?

You could check your software sources to make sure you have universe and multiverse enabled.

---

### Post by John Hale on 2009-01-18
Yep there's a tick in both boxes

---

### Post by John Hale on 2009-01-18
Just had this error message now:

E: /var/cache/apt/archives/sun-java6-bin_6-07-3ubuntu2_i386.deb: subprocess pre-installation script returned error exit status 1

---

### Post by clive littlewood on 2009-01-18
Hi

Try frostwire, it's Limewire for Linux.

I find it much better than Limewire   !!!     :)

Clive

---

