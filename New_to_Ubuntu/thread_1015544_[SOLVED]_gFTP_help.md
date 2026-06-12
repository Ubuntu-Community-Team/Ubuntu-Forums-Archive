---
title: "[SOLVED] gFTP help"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by coronacolada on 2008-12-18
Hi - 

I'm trying to connect to my web site with gftp, and it will log in just fine, but there are no folders or files listed. If I try to login to "ftp.[websitename].com/[folder]/" it tells me the folder doesn't exist. Yet I can ftp in via Mozilla with the same address with absolutely no problem. unfortunately, Mozilla won't let me upload. What do I do?

thanks.

-tom

sic luceat lux

---

### Post by anim on 2008-12-18
Hmm.. Working fine for me. try logging into [www.[websitename].com/(folder)/](www.[websitename].com/(folder)/) instead of ftp.[websitename].com/(folder)/

---

### Post by coronacolada on 2008-12-18
Good thought, but it's a no go. I'm currently logged into "www.[websitename].com" , "ftp.[websitename.com]", and just plain old "[websitename.com]"

All have completely blank folders in gFTP. For the record, I was able to login to another site I maintain without issue. Perhaps this is more a hosting issue than an Ubuntu issue? the other site was SFTP, so that may or may not have anything to do with it. 

-tom

sic luceat lux

---

### Post by albinootje on 2008-12-18
> **coronacolada said:**
> Good thought, but it's a no go. I'm currently logged into "www.[websitename].com" , "ftp.[websitename.com]", and just plain old "[websitename.com]"

All have completely blank folders in gFTP. For the record, I was able to login to another site I maintain without issue. Perhaps this is more a hosting issue than an Ubuntu issue? the other site was SFTP, so that may or may not have anything to do with it. 

You want a graphical ftp-client ? 
Then try filezilla or konqueror in Ubuntu, and find out whether it's a gftp issue.

---

### Post by anim on 2008-12-18
Your right, it might be a hosting issue. Try running:
```

$ ftp
ftp> open www.{site}.com
(enter username/Password)
ftp> ls

```

If it's gFTP's problem you should see all your files listed in the terminal.

---

### Post by coronacolada on 2008-12-18
> **albinootje said:**
> You want a graphical ftp-client ? 
Then try filezilla or konqueror in Ubuntu, and find out whether it's a gftp issue.

Filezilla worked! I was excited about using gFTP, but the graphical client works just fine. It does turn up an "empty directory" that is higher than my actual content directory, which doesn't seem possible, but hey, at least I can log in now. I'm assuming that somehow gFTP is logging me directly into the empty directory. 

Thanks!

-tom

sic luceat lux

---

### Post by coronacolada on 2008-12-18
> **anim said:**
> Your right, it might be a hosting issue. Try running:
```

$ ftp
ftp> open www.{site}.com
(enter username/Password)
ftp> ls

```

If it's gFTP's problem you should see all your files listed in the terminal.

That also proved it was a gFTP problem. Thanks again! Glad to learn how to open it in terminal also. 

-tom

sic luceat lux

---

