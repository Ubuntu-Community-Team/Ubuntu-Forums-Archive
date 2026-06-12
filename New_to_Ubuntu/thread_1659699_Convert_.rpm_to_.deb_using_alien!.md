---
title: "Convert .rpm to .deb using alien!"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by gagea on 2011-01-04
hi friends,

I am trying to install an file MEGA-4-02.noarch.rpm to work under wine. I find out that if I convert it to .deb, I my be able to install it. But this is the error:

ubuntu@ubuntu:/media/DATA/Downloads$ sudo alien -i MEGA-4-02.noarch.rpm 
Unpacking of 'MEGA-4-02.noarch.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 168.

Please help me with this issue. 

Gagea](*,)

---

### Post by endotherm on 2011-01-04
well, I would first try redownloading the RPM , but based on your error (indicating an issue reading the rpm), alien may not be up to the task. on the fly conversion can be tricky at times, so I'm surprised that alien works as well as it does.

also since you have a linux installer format (.rpm/.deb) wine does not enter into the equation. if you want to install a package within wine, look for an .exe (windows executable format).

---

### Post by gagea on 2011-01-04
> **endotherm said:**
> well, I would first try redownloading the RPM , but based on your error (indicating an issue reading the rpm), alien may not be up to the task. on the fly conversion can be tricky at times, so I'm surprised that alien works as well as it does.

also since you have a linux installer format (.rpm/.deb) wine does not enter into the equation. if you want to install a package within wine, look for an .exe (windows executable format).

Thanks a lot for reply. It is what I want to install :

[http://www.megasoftware.net/mega_linux.html](http://www.megasoftware.net/mega_linux.html).

Can you please give me a quick instruction of how to install the .exe file in wine?

Thanks

---

### Post by gagea on 2011-01-04
> **gagea said:**
> Thanks a lot for reply. It is what I want to install :

[http://www.megasoftware.net/mega_linux.html](http://www.megasoftware.net/mega_linux.html).

Can you please give me a quick instruction of how to install the .exe file in wine?

Thanks


This is the wine error:

ubuntu@ubuntu:/media/DATA/Downloads$ sudo wine MEGA4_Setup.exe 
wine: '/home/ubuntu' is not owned by you, refusing to create a configuration directory there
ubuntu@ubuntu:/media/DATA/Downloads$ 

Thanks for help.

---

### Post by howefield on 2011-01-04
Try the instructions from here (different alien command to the one you used).

[http://www.megasoftware.net/mega_linux.html](http://www.megasoftware.net/mega_linux.html)

> MEGA 4 has been tested succesfully on the following versions of Linux: Red Hat (Kernel 2.6.20 and 2.6.23) and Ubuntu 7.1. In these operating system versions, you may use the following Wine releases (0.9.39, 0.9.46, 0.9.55, 0.9.56).
MEGA 4 RPM package can be installed directly on Red Hat versions mentioned above. In order to install MEGA 4 on Ubuntu, you need to follow two steps.
1. alien –k package.rpm (you will get a file called package.deb after this command)
2. dpkg –i package.deb

---

### Post by gagea on 2011-01-04
> **howefield said:**
> Try the instructions from here (different alien command to the one you used).

[http://www.megasoftware.net/mega_linux.html](http://www.megasoftware.net/mega_linux.html)


I am sorry It does not work. Here is the error message:

ubuntu@ubuntu:/media/DATA/Downloads$  alien -k MEGA-4-02.noarch.rpm 
Must run as root to convert to deb format (or you may use fakeroot).

or

ubuntu@ubuntu:/media/DATA/Downloads$ sudo alien -k MEGA-4-02.noarch.rpm 
Unpacking of 'MEGA-4-02.noarch.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 168.

Any further suggestion?

Thanks](*,)

---

### Post by bodhi.zazen on 2011-01-04
From the web site :

> MEGA 4 has been tested succesfully on the following versions of Linux: Red Hat (Kernel 2.6.20 and 2.6.23) and Ubuntu 7.1. In these operating system versions, you may use the following Wine releases (0.9.39, 0.9.46, 0.9.55, 0.9.56).

Lower in the page they claim it is kernel dependent as well:

> The installation of MEGA 4 LE depends on the X kernel that you use.

Although I am not sure what they mean by "X kernel".

It is highly likely you will need to use these exact systems / kernels and versions of wine.

You could try running the windows version with wine and in virtualbox

[http://www.megasoftware.net/mega_dos.html](http://www.megasoftware.net/mega_dos.html)

You can try to extract the archive (rpm) and manually install it

[http://www.cyberciti.biz/tips/how-to-extract-an-rpm-package-without-installing-it.html](http://www.cyberciti.biz/tips/how-to-extract-an-rpm-package-without-installing-it.html)

Manually installing might be copying files to the proper locations and/or running scripts.

The only other option would be to try to DL an older version of Ubuntu and post to their mailing list. Judging from the date of the software and kernel my guess is the project is unmaintained at this time.

---

### Post by blind2314 on 2011-01-04
> **gagea said:**
> This is the wine error:
 
ubuntu@ubuntu:/media/DATA/Downloads$ sudo wine MEGA4_Setup.exe 
wine: '/home/ubuntu' is not owned by you, refusing to create a configuration directory there
ubuntu@ubuntu:/media/DATA/Downloads$ 
 
Thanks for help.
 
 
This would imply to me that you're trying to write to your home directory as root..which, as you saw, won't work. Either run wine without sudo, or install wine as root, so it has access to root's home directory and can write the appropriate files.

---

### Post by gagea on 2011-01-04
> **blind2314 said:**
> This would imply to me that you're trying to write to your home directory as root..which, as you saw, won't work. Either run wine without sudo, or install wine as root, so it has access to root's home directory and can write the appropriate files.

Thanks a lot for the reply. I install the .exe file under wine and it does work now. I could not find a way to install .rpm file. 

We can announce this post as solved.

---

### Post by blind2314 on 2011-01-04
> **gagea said:**
> Thanks a lot for the reply. I install the .exe file under wine and it does work now. I could not find a way to install .rpm file. 
 
We can announce this post as solved.
 
I'm still somewhat new to actually posting here, but for future reference, I believe you can actually mark the thread as solved by using the "thread tools" link at the top of the page.

---

### Post by gagea on 2011-01-04
> **blind2314 said:**
> I'm still somewhat new to actually posting here, but for future reference, I believe you can actually mark the thread as solved by using the "thread tools" link at the top of the page.

Thank you.

---

