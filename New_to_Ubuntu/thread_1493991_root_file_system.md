---
title: "root file system"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by Orions on 2010-05-26
How to specify the install path and install files in the root file system?

---

### Post by -humanaut- on 2010-05-26
I'd have to recommend against installing files to the root filesystem unless you know exactly what your doing. Why not just change the permissions on the files?

---

### Post by Calash on 2010-05-26
> **Orions said:**
> How to specify the install path and install files in the root file system?

Is there a reason why you would want to do this?

Honestly I would not recommend doing this on any operating system, especially Linux.  If an application is expecting to be in one part of your operating system but you force it to another and it is not written to account for this you can cause problems.

Linux has an additional complication with how the security model and permissions are designed.

---

### Post by Orions on 2010-05-26
> **-humanaut- said:**
> I'd have to recommend against installing files to the root filesystem unless you know exactly what your doing. Why not just change the permissions on the files?
 
 
[http://ubuntuforums.org/showthread.php?t=1493098](http://ubuntuforums.org/showthread.php?t=1493098)
 
 This is why I need to install in root. At least i think so, because when I didn't change install patch (used default) some errors ocured in terminal screen and software didn't worked.

---

### Post by exodus_ on 2010-05-26
what you are REALLY needing is to be superuser, if I am understanding this correctly.

In ubuntu [The root account]("https://help.ubuntu.com/community/RootSudo") is disabled as per the Ubuntu security model.  This is a good thing because you can use sudo, gksu, or gksudo to temporarily elevate yourself to "root"

You should never really need to install anything in the "root directory"

If you're installing from a package, using sudo will ensure it goes into /usr like its supposed to, or even /opt if that's how it's packaged.

If you are compiling from source, you should use the --prefix option and point it to /usr/local like this:

```
./configure --prefix=/usr/local
```

You really dont NEED to do this but it is a super easy way to keep installed packages and your localy compiled programs seperate.. Basically easier to manage

further, once you configure your souce you need to make and then install it.

```
make
sudo make install

```

in this example, you configured and compiled the program as a normal user and then used sudo to "become root" and install it into /usr/local

Also, make sure you have the build tools you need installed.

---

### Post by banerjeerupak on 2010-05-26
Why is it not advisable to log in as root. 

When i log in as user, one of my NTFS partition doesn't get detected. So for the past one year, i've been logging in as root. Things are working alright for me.

---

### Post by exodus_ on 2010-05-26
> **banerjeerupak said:**
> Why is it not advisable to log in as root. 


Because the root account can be dangerous.  One single slip of the hand while root and POOF! your ENTIRE system is trashed. This is just one reason.  Read my link above to find out more.

Also, if you are having issues with an NTFS partition there are much safer and better weays to get it to work while logged in normally

---

### Post by Orions on 2010-05-26
> **exodus_ said:**
> Also, make sure you have the build tools you need installed.
 
What are those? (sorry, I'm total newbie in ubuntu)

---

### Post by Orions on 2010-05-26
And why could those errors apear?
 
Please input the absolute path for install[/usr/local/Mobile_Partner]: /aspire6 
Local path is: /usr/local/Mobile_Partner
Installing Mobile Partner...chmod: cannot access `/usr/local/Mobile_Partner/config': No such file or directory
cp: cannot stat `./config/fontconfig/fontconfig.properties': No such file or directory
cp: cannot stat `./config/fontconfig/fontconfig.SuSE.properties': No such file or directory
[ done ] 
Installing Driver...
/usr/local/Mobile_Partner/driver/ndis_driver
The current system can not support ndis feature
ADDRUNLEVEL=/etc/rc3.d
`/etc/rc3.d/S99runhwactivator' -> `/etc/init.d/runhwactivator'
`/etc/rc3.d/K10runhwactivator' -> `/etc/init.d/runhwactivator'
ADDRUNLEVEL=/etc/rc2.d
`/etc/rc2.d/S99runhwactivator' -> `/etc/init.d/runhwactivator'
`/etc/rc2.d/K10runhwactivator' -> `/etc/init.d/runhwactivator'
ADDRUNLEVEL=/etc/rc4.d
`/etc/rc4.d/S99runhwactivator' -> `/etc/init.d/runhwactivator'
`/etc/rc4.d/K10runhwactivator' -> `/etc/init.d/runhwactivator'
ADDRUNLEVEL=/etc/rc5.d
`/etc/rc5.d/S99runhwactivator' -> `/etc/init.d/runhwactivator'
`/etc/rc5.d/K10runhwactivator' -> `/etc/init.d/runhwactivator'
./driver/install: line 114: chkconfig: command not found
cp: cannot create regular file `/etc/acpi/suspend.d/': Is a directory
chmod: cannot access `/etc/acpi/suspend.d/010-huawei-suspend.sh': No such file or directory
Finished, press any key to exit
 
 Also I'm not able to start installed aplication. Theare is no shortcut in desktop, ok vith that, but why I can't launch application from installed files? Some of the files is marked with kind a lock emblem.

---

### Post by Calash on 2010-05-26
> **Orions said:**
> What are those? (sorry, I'm total newbie in ubuntu)

To start, click on the Applications menu at the top.  At the bottom is the Ubuntu Software Center.  Check here first for any software you want to install.  Compiling should be a last resort (Unless you are doing it to learn, install a bleeding edge applications, or personal preference) as you will not get updates automatically.

You can ignore my first response as I thought you wanted to install applications in /, the Root of the file system and not as Root (ie, Sudo).

---

### Post by Orions on 2010-05-26
The main problem is that, I can't launch my wireless data card in ubuntu system without installing software for it. If I had internet connection in ubuntu, I would install programms from software center. Ofcourse I want to learn something, but first thing I hawe to do is to get i-net connection in ubuntu.
 Always when I need some tips for terminal or something, I hawe to restart pc, chose system boot to win vista, write all info in some file or paper and again restart pc, see if it works and again, again..... :mad:
 And I haw alredy tryed to make broadband connection with ubuntu internet tools.

---

### Post by blur xc on 2010-05-26
> **Orions said:**
> The main problem is that, I can't launch my wireless data card in ubuntu system without installing software for it. If I had internet connection in ubuntu, I would install programms from software center. Ofcourse I want to learn something, but first thing I hawe to do is to get i-net connection in ubuntu.
 Always when I need some tips for terminal or something, I hawe to restart pc, chose system boot to win vista, write all info in some file or paper and again restart pc, see if it works and again, again..... :mad:
 And I haw alredy tryed to make broadband connection with ubuntu internet tools.

No offense, but it seems like you are biting off more than you can chew as a beginner.  Start here - [http://linuxcommand.org/](http://linuxcommand.org/)

Get the basics down so you can better understand what people are saying when they give you suggestions or instructions.

BM

---

### Post by Orions on 2010-05-26
Thanks for the link, theare is a lot good info for me, BUT to start learning ubuntu I hawe to get it connected to internet somehow, ringht?

---

### Post by blur xc on 2010-05-26
> **Orions said:**
> Thanks for the link, theare is a lot good info for me, BUT to start learning ubuntu I hawe to get it connected to internet somehow, ringht?

Your kinda in the middle of the whole chicken-egg thing.  

I guess I was lucky, Ubuntu detected and ran w/ my wifi card out of the box with me having to do absolutely nothing...

If I were you- I'd start a new thread as the title of this one is very misleading.  Post the exact make and model of your modem and state that you are trying to make it work using some vendor supplied driver.  You might get better results.

Good luck.

BM

---

