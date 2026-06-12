---
title: "Downloading new software"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by babaikaushik on 2011-05-07
Hello,

Do we always need to use Ubuntu Software center to install new softwares or we can directly download them from portal and then install it like windows ?

For instance, can we download the chrome browser setup directly from Google portal and install it ?

Cheers 
Kaushik

---

### Post by Rex Bouwense on 2011-05-07
You don't need the Ubuntu Software Center to download programs but it makes it easier and generally they are installed without error and work out of the box.  You shouldn't have to fiddle with it to get it to work properly.

---

### Post by Norm24 on 2011-05-07
You could use Gdebi package installer.

---

### Post by 3rdalbum on 2011-05-07
> **babaikaushik said:**
> Hello,

Do we always need to use Ubuntu Software center to install new softwares or we can directly download them from portal and then install it like windows ?

For instance, can we download the chrome browser setup directly from Google portal and install it ?

Cheers 
Kaushik

You can, but:

a. Why would you want to trawl around websites to find software, when you can just do a quick search in Software Center to find and install whatever you need?

b. You'd really want to find a Debian package (.deb). Google Chrome has a Debian package, and so do a lot of proprietary software vendors' software. That's the easiest "offline" installation method that just involves a double-click.

Otherwise you've got things like binary installers which, like the installers on Windows, take up a lot of room and sometimes install supporting libraries that you already have. Because of Linux's tighter security model you'd also need to set the executable permission to the file first, and maybe even drag it into the terminal or run it as root. A bit fiddly.

Most open-source software is typically distributed as source code, which is really not something you want to get into. Just go to Software Center.

c. The programs in Software Center get security updates and sometimes bugfix updates, and these will be pushed straight out to you. Software in Debian packages, binary installers or source code form will NOT get security updates unless you manually download them and install the new versions yourself. A pain.

In short, stick to Software Center wherever possible. If you can't find the program in Software Center, then you should be able to find a repository or PPA that can be added to Software Center that will allow it to find the program.

---

### Post by eriktheblu on 2011-05-07
There's several different ways to install software in Ubuntu.

Chrom has a .deb, but I think there is also a PPA (might just be for beta).

---

### Post by babaikaushik on 2011-05-07
Thanks Gurus for sharing the information

---

