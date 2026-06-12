---
title: "ndiswrapper name change"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by Lostin60's on 2008-11-28
:mad:I just installed ndiswrapper, however it is now called ndiswrapper-commom. This is what I tried
daniel@daniel:~$ sudo ndiswrapper -i ~/desktop/bcmw15.inf
[sudo] password for daniel: 
couldn't open /home/daniel/desktop/bcmw15.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
daniel@daniel:~$ sudo ndiswrapper-common -i ~/desktop/bcmw15.inf
sudo: ndiswrapper-common: command not found
ndiswrapper-common is shown as installed in package manager. I am at a loss.

---

### Post by Ayuthia on 2008-11-29
> **Lostin60's said:**
> :mad:I just installed ndiswrapper, however it is now called ndiswrapper-commom. This is what I tried
daniel@daniel:~$ sudo ndiswrapper -i ~/desktop/bcmw15.inf
[sudo] password for daniel: 
couldn't open /home/daniel/desktop/bcmw15.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
daniel@daniel:~$ sudo ndiswrapper-common -i ~/desktop/bcmw15.inf
sudo: ndiswrapper-common: command not found
ndiswrapper-common is shown as installed in package manager. I am at a loss.

It should be ndiswrapper instead of ndiswrapper-common.  The problem that you are having is that you are using the number one instead of a lower-case L in bcmw**l**5.inf.  Please try:
```
sudo ndiswrapper -i ~/desktop/bcmwl5.inf
```

---

### Post by Lostin60's on 2008-11-30
Thank you. I had figured that out, almost by accident, a few days ago. I appreciate your time and effort anyway. I have a feeling that this is a very common issue. Also the l. I scoured the character charts for days looking for that character..lol. Might be worth a sticky post? Again, thank you.

Lostin60's

---

