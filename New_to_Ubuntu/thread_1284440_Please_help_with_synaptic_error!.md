---
title: "Please help with synaptic error!"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by itsbrad212 on 2009-10-06
so i was trying to install phpBB on ubuntu 9.04 when there was an error. but now, whenever i to go into synaptic, i get an error where it says i need to run sudo dpkg --configure -a

when i tried that, i got this another error. if you need to know more info, just leave a post. sorry i didnt have time to write down everything. but just ask and i will

---

### Post by OpenGuard on 2009-10-06
What was the second error ( after dpkg command ) ?

---

### Post by alchamech on 2009-10-06
i guess there was no other error lol

---

### Post by itsbrad212 on 2009-10-06
> **OpenGuard said:**
> What was the second error ( after dpkg command ) ?
o sorry i have run into another problem:

Unable to get exclusive lock
This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.

what do i do. i know i have none open!!!

---

### Post by itsbrad212 on 2009-10-06
> **alchamech said:**
> i guess there was no other error lol
i posted my other problem on the thread          :)

---

### Post by OpenGuard on 2009-10-06
Open Terminal and execute the following commands:
```
sudo apt-get clean
sudo apt-get -f update
```

---

### Post by itsbrad212 on 2009-10-06
> **OpenGuard said:**
> Open Terminal and execute the following commands:
```
sudo apt-get clean
sudo apt-get -f update
```
heres the first error. the second error won't come up, but this error seems to be more important

[http://itsbrad212.emenace.com/upload/ubuntu-error.jpg](http://itsbrad212.emenace.com/upload/ubuntu-error.jpg)

(i just put it on my image hosting site, so hope it works):guitar:

---

### Post by itsbrad212 on 2009-10-06
> **OpenGuard said:**
> Open Terminal and execute the following commands:
```
sudo apt-get clean
sudo apt-get -f update
```

o sorry heres the second error

[http://itsbrad212.emenace.com/upload/ubuntuerror2.jpg](http://itsbrad212.emenace.com/upload/ubuntuerror2.jpg)

---

### Post by itsbrad212 on 2009-10-06
i figured out on my own i went into root terminal and typed:

```
sudo rm /var/lib/dpkg/lock
```

and

```
sudo rm /var/cache/apt/archives/lock
```

then i updated the sources


:lolflag::lolflag::lolflag::lolflag::lolflag::lolflag:

---

### Post by Toriam on 2010-04-23
Thank you! This solved my problem.

---

