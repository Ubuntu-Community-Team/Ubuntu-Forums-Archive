---
title: "Problem with repository"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by CD4+ on 2009-05-07
Hello, today while trying to download archmage from the provided link via Synaptic manager i had an issue. The download failed and is showing me this error.. i am very new to LINUX as i used WINDOWS before

regards
CD4+

---

### Post by _Purple_ on 2009-05-07
Hello
Can you please post the exact error message that you get?

---

### Post by CD4+ on 2009-05-07
sorry i forgot to give the error... here is it 

>  E: Malformed line 55 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


---

### Post by _Purple_ on 2009-05-07
Can you run this command in terminal and paste the content of the file here?

```
gedit /etc/apt/sources.list
```

Which version of ubuntu are you using?

---

### Post by CD4+ on 2009-05-07
> # deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://mirror.in.th/ubuntu](http://mirror.in.th/ubuntu) jaunty main universe
deb [http://mirror.in.th/ubuntu/jaunty](http://mirror.in.th/ubuntu/jaunty) main 
can u tell me which book to read so that i get details of how to use commands ???

Ialso want to install NASM and C++ compiler..I dont know how to do that .. can some1 help???

regards
CD4+

---

### Post by _Purple_ on 2009-05-07
In the terminal, type the following command
```
gksu gedit /etc/apt/sources.list
```

Then in that file, replace the last line which is 
```
deb http://mirror.in.th/ubuntu/jaunty main 
```

with this line
```
deb-src http://mirror.in.th/ubuntu jaunty main universe
```


Then save the file and from terminal, run
```
sudo apt-get update
```
```
sudo apt-get install archmage
```

C++ compiler is g++. I think it is installed by default. If not, you can install it by running this command in terminal
```
sudo apt-get install g++
```

To install nasm, run
```
sudo apt-get install nasm
```


You can check this thread to learn more about ubuntu
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
Hope this helps.

---

### Post by Didius Falco on 2009-05-07
Hi,

You asked for Linux books - here is a whole series of courses available 24/7/365 for free:

[http://www.linux.org/lessons/](http://www.linux.org/lessons/)

You can get a free pocket guide in PDF format from here:

[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

Here is another site with Guides, HowTo's etc.:

[http://tldp.org/guides.html](http://tldp.org/guides.html)

That should get you started, and a quick google can always find you more.

Enjoy!!

Regards,

Didius

---

### Post by CD4+ on 2009-05-07
well even after the mentioned way the file is not opening.. even after archmage being installed. the .chm file is not corrupted as its running on windows xp.. please help

regards
CD4+

---

### Post by Boring Bloke on 2009-05-07
I think that the last line is the problem

deb [http://mirror.in.th/ubuntu/jaunty](http://mirror.in.th/ubuntu/jaunty) main 

should be

deb [http://mirror.in.th/ubuntu](http://mirror.in.th/ubuntu) jaunty main

---

### Post by _Purple_ on 2009-05-07
> **CD4+ said:**
> well even after the mentioned way the file is not opening.. even after archmage being installed. the .chm file is not corrupted as its running on windows xp.. please help

regards
CD4+

Which file didn't open?

---

### Post by jacksinn on 2009-05-07
You need to edit the last line of your sources.lst file to read:
deb [http://mirror.in.th/ubuntu](http://mirror.in.th/ubuntu) jaunty main 
As far as the additional error, can you clarify what is going on?

---

### Post by CD4+ on 2009-05-08
well, the .chm file which i want to open isnt opening even after following the way i was asked to do.

regards
CD4+

---

### Post by _Purple_ on 2009-05-08
I think you need to install xchm to open .chm files. 
```
sudo apt-get install xchm
```

---

### Post by CD4+ on 2009-05-08
thanks everyone for your precious time.Finally the way proposed by u all has worked.Now i am able to open chm files.

regards
CD4+

---

