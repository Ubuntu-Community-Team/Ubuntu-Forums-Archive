---
title: "Virus scanning windblow partition?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by nathan28 on 2009-02-08
So I installed a Ubuntu dual boot on a Wintel XP laptop. Since I plan on getting a replacement laptop soon, I partitioned my hard disk as 15 GB on the linux side and 37 or so on the windblows side.

One thing on my to-do list is scan the windows disk for viruses from Ubuntu. I've been running XP for over three years without really running any virus scanners (partly b/c I hate their shovelwear approach).

My question is, what virus scanner should I grab to run this sort of thing?

---

### Post by bgates on 2009-02-08
Clamav is popular.  It's in Add/Remove.  I think it's just called Virus Scanner but if you type in clam it comes up.

---

### Post by Idaho Dan on 2009-02-08
nathan28,
all I know is I use AVG [Anti Virus Gold] on my XP partition and it works better than anything I have tried, and it is free. It only hogs resources when it is updating.

Dan.

---

### Post by seanc7 on 2009-02-08
You can download Bitdefender for Unices for free. Then you just need to use the NTFS utilities to mount the Win partition under Ubuntu and scan away.

Clamav is another good choice as well.

---

### Post by theozzlives on 2009-02-08
First do this:

[http://ubuntuforums.org/showthread.php?t=1015834]("http://ubuntuforums.org/showthread.php?t=1015834")

reboot, then:

```
sudo apt-get install clamav
```

then:

```
mkdir /tmp/virus
```
```
clamscan -ri --move=/tmp/virus /windows
```

---

### Post by nathan28 on 2009-02-09
> **theozzlives said:**
> First do this:

[http://ubuntuforums.org/showthread.php?t=1015834]("http://ubuntuforums.org/showthread.php?t=1015834")

reboot, then:

```
sudo apt-get install clamav
```

then:

```
mkdir /tmp/virus
```
```
clamscan -ri --move=/tmp/virus /windows
```

thanks, i couldn't figure out the gui for clamAV. i assume that "/windows" should be the actual location of the mounted windows disk; what's the purpose of moving the files into a temp directory?

---

### Post by Captain_tux on 2009-02-09
> **nathan28 said:**
> One thing on my to-do list is scan the windows disk for viruses from Ubuntu. I've been running XP for over three years without really running any virus scanners (partly b/c I hate their shovelwear approach).



Frankly, if you haven't checked for viruses or other malware on your XP for 3 years, you're assuredly a victim of some type of infection... you're probably better off reformating and reinstalling XP.

---

