---
title: "updates unable to work. keeping internet from working"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by diserio.1 on 2009-08-07
I'm very uneducated with ubuntu. my little sister has it on her mini dell. This is the second time this problem has happened. She is notified to make updates but there is an error and says to manually run "dpkg --configure -a" but when this is done there is another error and it says that there are broken packages. I have tried to go to filters and fix the broken ones, but I have had no luck. I'm not sure what isn't working, what packages are broken, or really what a package even is. All I know is that she is unable to get on the internet because of this and I can't figure what to do. please help!!

---

### Post by Rocket2DMn on 2009-08-07
Can you please copy/paste here the entire output of
```
sudo dpkg --configure -a
```
If possible, wire the netbook onto your network with an ethernet cable, and the internet should pick up without needing to configure anything.  If the sytem isn't able to connect to the internet, run
```
sudo dpkg --configure -a > dpkg-error.txt 2>&1
```
then copy dpkg-error.txt file in the Home folder to a flash drive.  Then you can transfer the file to a computer with internet and post it here.

The error you are seeing appears when a package manager is interrupted during operation.

---

### Post by diserio.1 on 2009-08-07
Thank you.. I have the computer connected with the ethernet cable. I tried to do the updates again and now this is what came up in the error box.

E: /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-1ubuntu2.1_lpia.deb: failed in buffer_write(fd) (10, ret=-1)

then it says 5 broken packages

---

### Post by Rocket2DMn on 2009-08-07
Ok, please run
```
sudo apt-get clean
sudo dpkg --configure -a
```
That will clearn out the archived files, then reconfigure.  Does it work then, or do you see a different error?  If you see more, I need to see the entire output if at all possible.

---

### Post by diserio.1 on 2009-08-07
it's working! thanks a bunch!!

---

