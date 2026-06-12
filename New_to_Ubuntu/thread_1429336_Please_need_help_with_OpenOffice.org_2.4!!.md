---
title: "Please need help with OpenOffice.org 2.4!!"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by technicalnewbie on 2010-03-13
Hi, I have OpenOffice.org 2.4 and am having some technical difficulty. I keep getting this error message:

"OpenOffice.org could not save important internal information due to insufficient free disk space at the following location: /home/myusername/.openoffice.org2/user/backup 
You will not be able to continue working with OpenOffice.org without allocating more free disk space at that location.
Press the 'Retry' button after you have allocated more free disk space to retry saving the data"

Can u please help me resolve this because I've looked on the Internet and can't find a solution and I have no idea how to fix it!  Any help would be greatly appreciated!!! Thank you so much in advance!!

---

### Post by n0dix on 2010-03-13
Probably your $HOME partition is full, it means, you need to remove, copy, etc, information to get more space.
Please, post the output of:
```
$ df -h 
```

---

