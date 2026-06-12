---
title: "How to Use alien"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2009-04-18
I was installing a program when Terminal told me: ```
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm
```

What does this mean? How do I use alien?

Another supposedly simpler alternative was to install with: ```
dpkg -i
```
The problem is this:
```
dpkg: requested operation requires superuser privilege
```
It says that I have to be logged-in as a "superuser", which I would think to be the Ubuntu-version of a Windows Administrative User. But if I installed only 1 user (mine) and the Ubuntu is running (which can only happen if I am logged-in to the only user available) wouldn't this, by default already be the superuser? Why does this not seem to be the case?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by amingv on 2009-04-18
alien lets you convert packages from non-debian based distros (like RPM) into DEBs (debian installable packages).

You won't be able to install it with dpkg, not even if you do
```
**sudo** dpkg -i <package name>.rpm
```
Which is what it's asking you to do.

try this instead:

```
sudo aptitude install alien
```

and then

```
sudo alien -d -i <package_name>.rpm
```

What this does is:
sudo: Super User DO; do something as superuser
alien: calling the "alien" program
-d: convert to debian package (the default option, just added for clarity)
-i: install converted file
<package_name>.rpm: the RPM you want to install

---

### Post by Anthon on 2009-04-18
Apart from any 'normal' user there is always a user named 'root'. Logged in as that user you can do everything on the computer, which is kind of dangerous.
To run a single command as 'root' use
   sudo command_with_arguments
The first time you do this in a 10 minute or so timespan you will be asked to provide your password, to prevent misuage by someone walking up to your machine

To install a .rpm package first convert it to .deb using the alien package (which you might need to install first with:
  sudo apt-get install alien
)
After that use 
  sudo dpkg -i packagename.deb
to install the .deb package 

But before doing that I recommend searching for the .deb package on the internet you might be able to find it and that is normally better tuned to Ubuntu/Debian.

---

### Post by wabbalee on 2009-04-18
on ubuntu when executing commands with superuser privileges you do:
'sudo whatevercommandyouwant' it then prompts you for root password, you type your password (the only one you ever put on the system) it will not show anything on screen when you type it if in a terminal, then enter.

alien usage:
'alien package.rpm'

all without quotes

but why don't you use the package manager to install software on your system? like synaptic or adept or gdebi?

---

### Post by RedStarYellowSun on 2009-04-18
Thanks for your speedy responses! They are quite informative.

The installation involves more than 1 rpm, though. The instructions bring me to a folder full of rpm's and tells me to use:```
rpm -Uvh *rpm
```
How does using alien affect this command, then?
Do I just tweak it into this?```
sudo alien -d -i rpm -Uvh *rpm
```

Thanks for your time.

Take care,
RedStarYellowSun Thanks!
PS: Does anyone know a good book or website that teaches Terminal commands? Thanks!

---

### Post by Bradtek on 2009-04-18
Have you or have you not checked to see if there is already a .deb package of the app you want to install ?
Have you checked if it is in the repositories ?
What is the app you are trying to install ?

.rpm files are not made for Ubuntu they are made for Red Hat based distros.
eg. Open Suse, Fedora

---

### Post by juancarlospaco on 2009-04-18
Search for " **Alien GUI** " on **Launchpad**!

---

### Post by glotz on 2009-04-18
alien only converts the packages, it doesn't install them. Type **man alien** to see the manual page.

---

### Post by 3rdalbum on 2009-04-18
> **RedStarYellowSun said:**
> ```
rpm -Uvh *rpm
```
How does using alien affect this command, then?
Do I just tweak it into this?```
sudo alien -d -i rpm -Uvh *rpm
```

Close but not really :-)

```
sudo alien *.rpm
```

Says:

sudo - do the following as administrator
alien - name of the program
*.rpm - specifies all files that end in ".rpm".

It will convert all the RPM files to Debs. If you need to install the Debs simultaneously, you can do this:

```
sudo dpkg -i *.deb
```

which does exactly as it sounds: installs (-i) all (*) debian packages in the directory.

---

### Post by RedStarYellowSun on 2009-04-18
To 3rdalbum: Thanks for teaching me this. I certainly learned something. Same goers to glotz, juancarlospaco, and Anthon. Thank you.

To Bradtek: Answering you question, thanks for having me chesk for a .deb file. I assumed that since the tar.gz with RPM's was the file automatically downloaded in the "download" page, I thought that they had already recognised my Linux distribution and sent me the one appropriate for it.
The program I am trying to install is OpenOfice.Org 3.0.1 . Since my upgrade to Ubuntu 9.04, I found that it downgraded Open Office to 3.0.0 . The thing is that I rely on some of the features of 3.0.1 that cannot be found on mere 3.0.0, like the Printer Manager (I have problems with HPLIP and I can't print on Windows Vista due to some compatibility problem).
Okay, so I downloaded the DEBS version on tar.gz and it gave me the folder "OOO300_m15_native_packed-1_en-US.9379" with a "DEBS" folder in it. The instructions tell me to use:```
dpkg -i -&#8211;force-overwrite openoffice.org*.deb \ desktop-integration/openoffice.org-debian-menus*.deb
```
But knowing that I have to use sudo, I modify it to:```
sudo dpkg -i -&#8211;force-overwrite openoffice.org*.deb \ desktop-integration/openoffice.org-debian-menus*.deb
```
And I got:```
jutumang@jutumang-laptop:~$ cd Desktop
jutumang@jutumang-laptop:~/Desktop$ cd OOO300_m15_native_packed-1_en-US.9379
jutumang@jutumang-laptop:~/Desktop/OOO300_m15_native_packed-1_en-US.9379$ cd DEBS
jutumang@jutumang-laptop:~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS$ sudo dpkg -i -&#8211;force-overwrite openoffice.org*.deb \ desktop-integration/openoffice.org-debian-menus*.deb
[sudo] password for jutumang: 
dpkg: unknown option -

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
jutumang@jutumang-laptop:~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS$
```
What happened?
I know that I deviated from the instructions, which only tell me to use the code with need of "cd"-ing to the folder. But when I just input it, it gives me basically the same thing:```
jutumang@jutumang-laptop:~$ sudo dpkg -i -&#8211;force-overwrite openoffice.org*.deb \ desktop-integration/openoffice.org-debian-menus*.deb
dpkg: unknown option -

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
```
What do I do?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by umeshkumar on 2012-11-24
I have a rpm package which consists of script files,properties files and jars.

On ubuntu 12.04 i am using alien to install my rpm package.

sudo alien -icvk myrpmpackage.rpm

This installs the rpm package with script files and jars, but skips the properties files. 
How do i get properties file be included in installed package ?

---

### Post by sisco311 on 2012-11-24
From the [code of conduct](http://ubuntuforums.org/index.php?page=policy) that you agreed to when you created your account:

> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

Old thread closed.

---

