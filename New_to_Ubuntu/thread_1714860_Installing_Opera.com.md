---
title: "Installing Opera.com"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by wsl on 2011-03-26
Hi,

I went to Opera.com to downloadand installOpera_11.01.1190_i386.deb in myUbuntu 6.06. Finally, a messagebox shown:
Could not open 'Opera_11.01.1190_i386.deb'
The package might be corruptedor or you are not allow to open the file. Check the permissions of the file. 

How can I install Opera? Thank you.

---

### Post by goldblattster on 2011-03-26
I'm not sure if that version of Opera is compatible with the (non-supported) Dapper. You should probably install it from your repos and see if works from there.

---

### Post by NightwishFan on 2011-03-26
wsl you might be better off upgrading to a newer version of Ubuntu like 10.04. I doubt opera would work, but you can try with:
```
sudo dpkg -i /path/to/opera.deb
```

Make sure you replace the path to opera to the correct location of the opera deb.

---

### Post by beew on 2011-03-26
What is Ubuntu 6.06? Did they use to release in June? Was it released in June 2006???

@OP, why still using such an ancient version whose support has ended years ago?

---

### Post by Zill on 2011-03-26
> **beew said:**
> What is Ubuntu 6.06? Did they use to release in June? Was it released in June 2006???...
[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

---

### Post by wsl on 2011-03-26
> **NightwishFan said:**
> wsl you might be better off upgrading to a newer version of Ubuntu like 10.04. I doubt opera would work, but you can try with:
```
sudo dpkg -i /path/to/opera.deb
```Make sure you replace the path to opera to the correct location of the opera deb.



Thank you NightwishFan. 
Here is what I tried.
a@0:~/Desktop$ ls
frobate-00ccfc09cf.desktop  opera-11.01-1190.i386.linux
opera_11.01.1190_i386.deb   opera-11.01-1190.i386.linux.tar.bz2
a@0:~/Desktop$ sudo dpkg -i opera_11.01.1190_i386.deb
Password:

(Reading database ...
dpkg: serious warning: files list file for package `opera' missing, assuming pac kage has no files currently installed.
88614 files and directories currently installed.)
Preparing to replace opera 11.01.1190 (using opera_11.01.1190_i386.deb) ...
Unpacking replacement opera ...
dpkg-deb: file `opera_11.01.1190_i386.deb' contains ununderstood data member dat a.tar.lzma   , giving up
Segmentation fault



I think my PC and my versin of Ubuntu is too old.
Thank again. I will try to stay with Firefox 1.5.0.12eol.
FireFox 4 is too new to my PC.

---

### Post by Frogs Hair on 2011-03-26
I downloaded the package and used Gdebi package installer for Opera 11 alpha , beta , and stable.

---

### Post by wsl on 2011-03-26
Now comes other question when I try to uninstall KPPP, it showed that:

E: I wasn't able to locate a file for the opera package. This might mean you need to manually fix this package. (due to missing arch)
E: I wasn't able to locate a file for the opera package. This might mean you need to manually fix this package. (due to missing arch)


Well, better not to try install something by myself but select from "Add/Remove..."

How should I fix this problem?

---

### Post by NightwishFan on 2011-03-26
Try:
```
sudo apt-get remove opera
```
If that does not work run:
```
sudo dpkg --force-all -r opera
```

Still though, 10.04 should work, try Xubuntu 10.04 if you have an older computer. It will be worth it to upgrade.

---

### Post by wsl on 2011-03-26
> **NightwishFan said:**
> Try:

Still though, 10.04 should work, try Xubuntu 10.04 if you have an older computer. It will be worth it to upgrade.

Thank you NighwishFan!

I checked Wiki that Xubuntu is no more light enough.
"Tests were conducted by DistroWatch on a Dell Dimension 4500 desktop machine, with an Intel 2 GHz processor and 384 MB of memory in April 2009, that compared Xubuntu 9.04 against an Xfce desktop version of Debian 5.0.1 Xfce. These showed that Xubuntu used more than twice the RAM as Debian in simple tasks. Xubuntu also ran out of RAM doing everyday tasks, indicating that 384 MB of RAM was inadequate." ([http://en.wikipedia.org/wiki/Xubuntu](http://en.wikipedia.org/wiki/Xubuntu), 2011.03.26.)

---

### Post by waynefoutz on 2011-03-26
Lubuntu is the one you want.



> The minimum system requirements for Lubuntu 10.10 are described by Mario Behling as "comparable to Pentium II or Celeron systems with a 128 Mb RAM configuration, which may yield a slow yet usable system with lubuntu."[29]

Chief developer Julien Lavergne has stated that the minimum RAM to install Lubuntu 10.10 is 256 MB. [http://en.wikipedia.org/wiki/Lubuntu](http://en.wikipedia.org/wiki/Lubuntu)

---

### Post by wsl on 2011-03-30
> **waynefoutz said:**
> Lubuntu is the one you want.
 
Yes, thank you. I found Lubuntu days ago, too.
 
Howevr, some mistakes, Lubuntu has not installed successfully but Ubuntu6.06 cannot start now. It shows 
grub rescue>
 
I tried to find any command I can use by typing hlep but "Unknown command" responded.
 
I try "ls" and responded
(hd0) (hdo,7)....(hd0,1) (fd0)
 
What should I do to go back to start Ubuntu I installed? Any way to see all commands in grub rescue>?
 
 
Tks.

---

### Post by wsl on 2011-04-03
I have finally formated whole HD and install MS Win and Lubuntu. However, I got bad time on installing Lubuntu 10.10 on Pentium III 933MHz 256MB mem PC many times. Yet, I am now running well with Lubuntu 10.04.

---

### Post by NightwishFan on 2011-04-03
> **wsl said:**
> I have finally formated whole HD and install MS Win and Lubuntu. However, I got bad time on installing Lubuntu 10.10 on Pentium III 933MHz 256MB mem PC many times. Yet, I am now running well with Lubuntu 10.04.

Excellent! I am glad you got it working. :)

---

