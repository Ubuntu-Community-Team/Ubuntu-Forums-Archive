---
title: "Adobe PDF problem"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by dpreed77 on 2009-06-11
Hi, I am having a problem with a PDF form. I cannot open it, I get an error:
"Warning: This form is not supported with the current version of Adobe or Adobe Reader. Upgrade to the latest Version for full support." 
I do not have adobe installed. I have not not had had a problem with PDF files before, but this is a form that I have had to fill out. Is there a program other than Adobe that I can use?

Thanks in advance, 
Dennis

---

### Post by keplerspeed on 2009-06-11
You could add the medibuntu repo and install acroread via synaptic. Acroread may be useful.

Follow this to add the medibuntu repo:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by halitech on 2009-06-11
are you trying open the form online?

---

### Post by dpreed77 on 2009-06-11
I have the file on my computer, is not online.

---

### Post by benj1 on 2009-06-11
why don't you try evince, it comes as standard with ubuntu.

where are you trying to open it?

---

### Post by dpreed77 on 2009-06-11
Hi, I tried evince. I get the previous error message.

---

### Post by halitech on 2009-06-11
look for PDFedit in synaptic. Evince, acroread, etc are readers and will not allow you to edit pdf files.

---

### Post by dpreed77 on 2009-06-11
Hi, I tried PDF editor, it does not help. I am pretty new to Ubuntu. I installed Medibuntu, but I am not sure where to go from there? Can anyone help with the acroread thing?
Thanks

---

### Post by Mornedhel on 2009-06-11
I think halitech and the others misunderstood. You are not trying to edit a PDF, you're trying to fill a form within the PDF, right ?

If you have correctly installed Medibuntu, the acroread package should show up in Synaptic. Try

```
sudo apt-get install acroread
```

According to apt-cache show acroread, it's the version 9 of Adobe Reader and it has forms support.

---

### Post by dpreed77 on 2009-06-11
Hi, I tried the code suggested (copy and pasted) and I received an error message:
E. Couldn't find package acroread
Did I install medibuntu wrong? Everything seemed to go ok?

---

### Post by halitech on 2009-06-11
can you post the output of
```
cat /etc/apt/sources.list
```

---

### Post by Mornedhel on 2009-06-11
Could you post the contents of the file ```
/etc/apt/sources.list
``` and of the directory ```
/etc/apt/sources.list.d
``` so we can check your Medibuntu repositories are in fact enabled ?

As a previous poster pointed in this thread, the instructions to enable Medibuntu can be found here : [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

---

### Post by dpreed77 on 2009-06-11
Hi again, 
I downloaded acroreader from the Medibuntu webpage and have the tar.gz file. Can someone explain how to install this file? Thanks!

---

### Post by dpreed77 on 2009-06-11
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

---

### Post by dpreed77 on 2009-06-11
dennis@dennis-laptop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
dennis@dennis-laptop:~$ 
dennis@dennis-laptop:~$ /etc/apt/sources.list.d
bash: /etc/apt/sources.list.d: is a directory
dennis@dennis-laptop:~$

---

### Post by 73ckn797 on 2009-06-11
Go here and follow the directions: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by sanika on 2009-07-02
You can download the latest version of acroread from [ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.1.2/](ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.1.2/). There is an excellent post about installer formats [http://blogs.adobe.com/acroread/](http://blogs.adobe.com/acroread/). The post mentions the commands to be used for different installers.

-Sanika

---

