---
title: "How to install Netbeans IDE"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by MughalShahzad on 2010-04-25
Hello dears, I have downloaded NetBeans IDE, trying to install but following message appears

```

shahzad@shahzad-desktop:~$ sudo aptitude install /home/shahzad/Downloads/netbeans-6.8-ml-linux.sh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Couldn't find any package whose name or description matched "/home/shahzad/Downloads"
Couldn't find any package whose name or description matched "/home/shahzad/Downloads"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 252 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

shahzad@shahzad-desktop:~$ 


```kindly suggest me what to do

Thanks & Regards
Shahzad

---

### Post by KdotJ on 2010-04-25
Did you download the file? To my knowledge this isn the way to install the downloaded file. And then execute it. 

E.g 
change to the directiory where the file is

```
cd /Downloads
```

then execute the file name

```
./name-of-file
```


Or of course the easiest way, goto the ubuntu software centre and search for netbeans. Click install and away you go

---

### Post by nick_goodfate on 2010-04-25
[https://help.ubuntu.com/community/Netbeans](https://help.ubuntu.com/community/Netbeans)

---

### Post by sandyd on 2010-04-25
sudo apt-get install netbeans

---

### Post by da burger on 2010-04-25
> **MughalShahzad said:**
> ```
0 packages upgraded, 0 newly installed, 0 to remove and **252 not upgraded**
```

On an unrelated note you might want to update your system.

---

