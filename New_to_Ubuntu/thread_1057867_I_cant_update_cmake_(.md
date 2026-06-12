---
title: "I cant update cmake :("
date: 2009-02-02
forum: New to Ubuntu
---

### Post by xmango on 2009-02-02
Granted my knowledge is very basic, but I at least thought myself able to update this program.  I have failed though.... I tried 

> sudo apt-get update
sudo apt-get upgrade

This is after I installed the repository in /etc/apt/sources.list

I tried the Snyaptic Package manager, and I even tried to download the binary from the cmake website and follow the readme.txt but to no avail :(

Any help that could be given would be much appreciated

---

### Post by taurus on 2009-02-02
What repo did you add to your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```
Also, what does readme.txt tell you to do when you download the source (or binary) code?

---

### Post by xmango on 2009-02-02
Heh sorry for not responding. After several minutes I stumbled on this. [FIX]("http://ubuntuforums.org/showthread.php?t=899754") and it solved my problem :)  Thank you for your response though

---

