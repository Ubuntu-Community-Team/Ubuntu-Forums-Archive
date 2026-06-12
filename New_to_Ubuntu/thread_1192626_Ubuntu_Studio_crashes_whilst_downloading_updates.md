---
title: "Ubuntu Studio crashes whilst downloading updates"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by Dave.YNA on 2009-06-20
Hello All,
          I'm really hoping someone can help me with my issue. I have downloaded and installed the AMD 64 bit version of ubuntu studio for my PC. The problem is that every time I try to run the update manager, it starts downloading then about half way through the transfer rate drops and eventually the PC completely freezes. Cant move the mouse or anything.

I have re-installed the OS 4 times now and re-downloaded the ISO file twice. 

Ive also done a google on this and not returned much so its looking pretty unique at the moment.

Any help would be greatly appreciated as this is a core feature.

Thanks in Advance
Dave

---

### Post by Eisenwinter on 2009-06-20
What happens when you do the following command in terminal:

```
sudo apt-get upgrade
```

Try that, and see what the error message is.

---

### Post by Dave.YNA on 2009-06-20
Hi, I get the following message.

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

Thanks for the help.

---

### Post by Atnas on 2009-06-24
Hey! I had this same problem with Ubuntu Studio, so I searched the forums a bit. A lot of the sudo commands that people were advising others to use just didn't work for me, even though those others actually got it to work.

There's a partial solution. On my installation of Ubuntu Studio, I'm presented with the dpkg was interrupted message whenever I try to start a package manager, and typing the 'sudo dpkg --configure -a' command you quoted in your above post just runs it through the package that hangs again. In order to be able to download any other packages, I found that pressing alt+f2 and then running "gksu nautilus", navigating to /var/lib/dpkg/updates, and deleting any files there works a charm.

Unfortunately this doesn't fix the problem entirely, as when I tried to resume the specific package that hung (in my case it was part of OpenOffice) it gave me the whole E: dpkg was yada yada yada again.

I'll let you know if I come across anything else. Ubuntu Studio is great, it would  be a shame if something like this were to happen often or persist once it arose.

---

