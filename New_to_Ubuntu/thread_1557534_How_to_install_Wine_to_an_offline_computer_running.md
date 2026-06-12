---
title: "How to install Wine to an offline computer running Ubuntu 10.04"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by Prince Valiant on 2010-08-20
Hello,

I'm attempting to install Wine on a desktop running Ubuntu 10.04; the catch is, it doesn't have an internet connection.  

I have another computer dual-booting Windows and Ubuntu 10.04, with an internet connection.  

I read up on this, and it seems that I have to install a package called binfmt-support in order to successfully install Wine 1.2.  Maybe I missed something, but I can't figure out how to compile the package and install it.  The .deb wine file is easy, but that's second.  

I think this is a simple matter of teaching me how to compile and install binfmt-support.tar.gz, but that's only my hope.  If it's not, I think that I'll need a full tutorial.  The official ones were too complicated (I think- I may have missed the right one).

:-D

I'm working off of this site: [http://wiki.winehq.org/Ubuntu](http://wiki.winehq.org/Ubuntu).

Thanks!

-Val

---

### Post by Ms_Angel_D on 2010-08-20
just download the .deb files

Get wine here [https://launchpad.net/~ubuntu-wine/+archive/ppa/+packages](https://launchpad.net/~ubuntu-wine/+archive/ppa/+packages)

then if you need any dependent .deb files search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com) and download which ones you need.

then save them to flash drive or burn them to a disk.

---

### Post by XubuRoxMySox on 2010-08-20
Once you have [aptoncd]("http://aptoncd.sourceforge.net/") installed on both machines, it's really easy. Use a CD as a "repository!" Aptoncd is is in the repositories too.

Enjoy!

-Robin

---

### Post by Prince Valiant on 2010-08-20
Actually, I went back and did exactly what you said, Ms_Angel_D, before I saw your very quick reply.  It worked great. 

Thanks for both your suggestions!

-Val

---

### Post by ClrScr on 2010-08-30
> **Ms_Angel_D said:**
> just download the .deb files

Get wine here [https://launchpad.net/~ubuntu-wine/+archive/ppa/+packages](https://launchpad.net/~ubuntu-wine/+archive/ppa/+packages)

then if you need any dependent .deb files search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com) and download which ones you need.

then save them to flash drive or burn them to a disk.

Ms Angel! 

Please help me!
If I go to 
[https://launchpad.net/~ubuntu-wine/+archive/ppa/+packages](https://launchpad.net/~ubuntu-wine/+archive/ppa/+packages)
There is a directory called
  wine1.2 - 1.2-0ubuntu1~lucidppa1

that leads to [https://launchpad.net/~ubuntu-wine/+archive/ppa/+sourcepub/1238491/+listing-archive-extra]("https://launchpad.net/~ubuntu-wine/+archive/ppa/+sourcepub/1238491/+listing-archive-extra")
whihc in turn lists 13 files
> ttf-symbol-replacement_1.2-0ubuntu1~lucidppa1_all.deb (54.7 KiB) 
wine-dev_1.2-0ubuntu1~lucidppa1_all.deb (38.5 KiB) 
wine-gecko_1.2-0ubuntu1~lucidppa1_all.deb (38.5 KiB) 
wine1.2-dbg_1.2-0ubuntu1~lucidppa1_amd64.deb (18.7 MiB) 
wine1.2-dbg_1.2-0ubuntu1~lucidppa1_i386.deb (18.7 MiB) 
wine1.2-dev_1.2-0ubuntu1~lucidppa1_amd64.deb (1.5 MiB) 
wine1.2-dev_1.2-0ubuntu1~lucidppa1_i386.deb (1.5 MiB) 
wine1.2_1.2-0ubuntu1~lucidppa1.diff.gz (159.1 KiB) 
wine1.2_1.2-0ubuntu1~lucidppa1.dsc (2.3 KiB) 
wine1.2_1.2-0ubuntu1~lucidppa1_amd64.deb (9.5 MiB) 
wine1.2_1.2-0ubuntu1~lucidppa1_i386.deb (9.8 MiB) 
wine1.2_1.2.orig.tar.gz (21.4 MiB) 
wine_1.2-0ubuntu1~lucidppa1_all.deb (38.5 KiB)

are these the ones I should download?

thanks, and sorry for still being a newbie! (At least my mother loves me!)
J

---

### Post by Ms_Angel_D on 2010-08-31
Use the filter on the page. Set it so that it shows only packages for the version of Ubuntu your attempting to install on. So if your using 10.04 that would be Lucid.

1.2 is the stable version
1.3 is the latest version

You could also just use dixiedancer's suggestion and use aptoncd. It would make things very easy for you.

---

