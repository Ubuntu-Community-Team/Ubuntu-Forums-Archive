---
title: "Trying to view/transfer files in dual install"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by VaderX5 on 2011-01-23
I used Wubi to install Ubuntu onto a HDD that also has Windows XP on it. This was about 2 hours ago, so I assume everything is the most current release. While in Ubuntu, I'd like to be able to view image files (photos) that are in folders in Windows. I'd really like to be able to move these files from Windows to Ubuntu. Is this possible?

FYI, I've got about 2 hours of experience using Linux, so go slow. :)

Thanks in advance!

---

### Post by Bucky Ball on 2011-01-23
Firstly, welcome.

Let me get it straight: You've done a Wubi install inside Windows or you have a dual-boot situation where you get the options to boot Windows or Ubuntu when you switch the machine on?

---

### Post by VaderX5 on 2011-01-23
Thanks for the reply!

I can choose the OS, so i guess it's dual-boot.

---

### Post by Bucky Ball on 2011-01-23
Great, so it should be simple. In the left column of file manager do you see something like '15Gb Drive' (or whatever size the Windows partition you are attempting to access is)? Click that and you should be able to mount it, get to the files and put them where you want. ;)

---

### Post by Paqman on 2011-01-23
Wubi mounts the Windows filesystem at /host, btw.

---

### Post by beew on 2011-01-23
wubi is not a dual boot. It is a program in Windows for you to try out Linux. It lives in a Windows folder and can be uninstalled like other Windows programs.

In a dual boot both OS are on equal footing. You need to partition your hard drive first to make a dual boot.

---

### Post by VaderX5 on 2011-01-23
> **Bucky Ball said:**
> Great, so it should be simple. In the left  column of file manager do you see something like '15Gb Drive' (or  whatever size the Windows partition you are attempting to access is)?  Click that and you should be able to mount it, get to the files and put  them where you want. ;)
So... I don't see 'file manager' anywhere.:confused:

> **Paqman said:**
> Wubi mounts the Windows filesystem at /host, btw.
I don't know what that means. 

> **beew said:**
> wubi is not a dual boot. It is a program in Windows for you to try out Linux. It lives in a Windows folder and can be uninstalled like other Windows programs.

In a dual boot both OS are on equal footing. You need to partition your hard drive first to make a dual boot.
I downloaded the install file, then downloaded and ran Wubi. I told it to partition 30GB for the install. When I turn the machine on, I get a black screen w/ white writing that  asks me whether I want to boot with MS Windows XP or Ubuntu. It *seems* like equal footing, but I could be wrong.

---

### Post by Bucky Ball on 2011-01-23
Sounds like it's installed to me. As I thought. Just go to 'Places' and open any folder. There is the file manager.

---

### Post by bcbc on 2011-01-24
Go to Places, Computer, File system, host

That's how to navigate to /host - and it's like C:\ on windows (or if you installed on D: then D:\)

You can also go to a terminal (CTRL-ALT-t) and run
```
nautilus /host
```

---

### Post by VaderX5 on 2011-01-24
Ok, I was able to use both the 'places' and (CTRL-ALT-t) methods to access the files I needed. 

After several years of admiring from afar, I'm really stoked to be getting into this OS. 

Thanks guys!

---

### Post by Bucky Ball on 2011-01-24
Great news. Enjoy your new OS, the learning curve, and welcome to Linux. I admired from afar for awhile also but once I got here I was hooked! ;)

---

