---
title: "make command not found"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by lilsancho on 2009-10-07
Hi guys,

i`m trying to install a program but am getting;
bash: make command not found

i`ve tried to do; sudo aptitude install build-essential but i get the following...

user@SmartQ:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No candidate version found for build-essential
No candidate version found for build-essential
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 83 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_US:en",
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
E: Directory '/var/log/apt/' missing
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done


any ideas?

Thanks :)

---

### Post by sisco311 on 2009-10-07
> **lilsancho said:**
> Hi guys,

...
**E: Directory '/var/log/apt/' missing**
...

any ideas?

Thanks :)

That's odd. 

Try to (re)create the missing directory:
```
sudo mkdir /var/log/apt/
```
```
sudo apt-get update
```

---

### Post by lilsancho on 2009-10-08
Hi Sisco

Thanks very much :) that worked perfectly 

Cheers

---

