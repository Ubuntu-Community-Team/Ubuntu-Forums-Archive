---
title: "scp won't connect for some reason"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by beelzebufo on 2011-06-07
I have an ubuntu server set up and my blackbuntu machine (ubuntu 10.10) I have transferred files between them like this before but now it won't work, I backed up my bb machine as I broke.. well everything trying to get rid of duplicate files and now I get this.. of course I am an idiot and named them both the same thing so it's all that much more confusing.. anyway any help would be really awesome

s3ct10n_8@wreckingball:~$ sudo scp -p s3ct10n_8@192.168.1.3:/home/s3ct10n_8/Downloads s3ct10n_8@192.168.1.2:home/s3ct10n_8
s3ct10n_8@192.168.1.3's password: 
Connection closed by 192.168.1.2
lost connection

1.3 is the server
thanks in advance
beelzebufo

---

### Post by Toz on 2011-06-08
If they both have the same hostname you should change one ([http://ubuntuforums.org/showthread.php?t=1594488]("http://ubuntuforums.org/showthread.php?t=1594488"))

Afterwards, try with debugging enabled to help point point problem: ```
scp -v ...
```

---

