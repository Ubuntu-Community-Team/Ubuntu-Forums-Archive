---
title: "2 more on files and AV"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by weezyrider on 2011-03-01
I've always used NOD32 as an AV. I see they have a beta version for Linux - has anyone used it? I'm asking as I download files for 2 XP freestanding computers that do not go online. They are for special software only. I want to keep virus checking downloads for them. 

The other question is about TAR.GZ files. I've asked about Stellarium, apparently the program is hinky at times, even in Windows. I have 10.2 running just fine on an XP laptop.
I can download 10.2 for Linux, but it is a TAR,GZ file, I can extract, but Ubuntu SUDO can't find it. The instructions I've seen assume you are UPGRADING a program, not downgrading it.  10.2 would be a DOWNGRADE. The current version is 10.6

Thanks,
Weezy

---

### Post by aeiah on 2011-03-01
i dont use antivirus software.. i assume the linux version will use the same database and methods as the windows version, so there shouldnt be a problem. there are other ones available too if NOD doesnt work out.

software in tar.gz packages are usually source code. there should be a README file that gives some information, but the usual way to compile, once you've extracted it to a folder, is: 
```

cd ~/path/to/folder/
./configure
make
sudo make install

```

you may get errors at any point if you havent got the required dependencies. its usually a good idea to rely on the ubuntu repositories to install software, since this manages dependencies and such for you.

if you can't find Stellarium in the ubuntu software center (i dont have the software center installed so cant check) you should be able to find it with synaptic, or on the command line you could issue:
```

sudo apt-get update
sudo apt-get install stellarium
```

---

### Post by weezyrider on 2011-03-01
It's in the software center but it won't run. I managed 10.5, but that won't run, either. So I want to try 10.2 as it was stable on 2K and XP. That's where windows had it all over Ubuntu. I could install any older stuff that would run! Sometimes I just don't want to upgrade. I don't care if it's free or not. New just might not work my way. W

---

### Post by Hedgehog1 on 2011-03-02
> **weezyrider said:**
> It's in the software center but it won't run. I managed 10.5, but that won't run, either. So I want to try 10.2 as it was stable on 2K and XP. That's where windows had it all over Ubuntu. I could install any older stuff that would run! Sometimes I just don't want to upgrade. I don't care if it's free or not. New just might not work my way. W

Hello again weezyrider,

All Linux computers are by nature immune to MS Windows damaging programs (which we call viruses).  MS Windows programs do not run on Linux natively.

The anit-virus options offered are based on being a good neighbor to our MS windows using friends; while a virus ridden email won't hurt your Ubuntu system, we don't want to forward that to a MS windows buddy.

You are (understandably) operating from the traditional MS windows point of view.  But just as the Macintosh OSX is not affected by MS Windows viruses, neither is your Ubuntu install.

I hope this helps you understand.

***The Hedge***

:KS

---

### Post by daggerstab on 2011-03-02
> **weezyrider said:**
> The other question is about TAR.GZ files. I've asked about Stellarium, apparently the program is hinky at times, even in Windows. I have 10.2 running just fine on an XP laptop.
I can download 10.2 for Linux, but it is a TAR,GZ file, I can extract, but Ubuntu SUDO can't find it. The instructions I've seen assume you are UPGRADING a program, not downgrading it.  10.2 would be a DOWNGRADE. The current version is 10.6

The problem with Stellarium is not in Stellarium itself, but with the current drivers. So, even if you built Stellarium 0.10.2 from source, it probably wouldn't run.

"sudo" means "super user do" - a command that executes the following command with super user ("root"/"administrator") privileges.

I don't know if you've  read this from your "Software" thread:
> **daggerstab said:**
> A user who had reported the same error   message like you has reported that the problem is fixed by updating from   these two PPAs:

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") 
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

It's possible that only the first may be sufficient.

See comment #50 and later here:
[https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/481669](https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/481669)

If you want to try building 0.10.2 from source, how to do it on Linux/Ubuntu is described on this page in the Stellarium Wiki:
[http://www.stellarium.org/wiki/index.php/Compilation_on_Linux](http://www.stellarium.org/wiki/index.php/Compilation_on_Linux)
That page is not in a very good condition at the moment, though.

---

