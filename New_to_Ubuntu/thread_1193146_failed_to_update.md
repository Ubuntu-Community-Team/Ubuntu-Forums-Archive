---
title: "failed to update"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by ejlal on 2009-06-21
[SIZE=3]everytime i try to update using update manager or synpatic i get an error message says:
 "Could not download all repository indexes" (The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.) so  i googled it ,as a result i changed the download server but still i get the same message,some advice me to edit my source.list file i removed all its contents and run these two command in a terminal 
sudo apt-get update
sudo apt get upgrade 
this is what the outcome was:
[/SIZE][SIZE=3]
ejlal@TOSHIBA:~$ sudo apt-get update
sudo: unable to resolve host TOSHIBA
Reading package lists... Done
ejlal@TOSHIBA:~$ sudo apt-get upgrade
sudo: unable to resolve host TOSHIBA
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/SIZE]
 
[SIZE=4]why its not finding any updates? 
am using ubuntu hardy on my toshiba nb11-11r laptop
am a newbie to ubuntu/linux 
so [/SIZE][SIZE=4]i will appreciate  detailed solutions 
if u need any info just tell me what u want and where i can get it
thanks 
[/SIZE]

---

### Post by ugm6hr on 2009-06-21
Output from:
```
cat /etc/apt/sources.list
```

---

### Post by sanemanmad on 2009-06-21
I know you are not looking for a solution to this but what the heck :)

> sudo: unable to resolve host TOSHIBA

Not a big deal... You will probably want to add an entry in /etc/hosts like the following

```
127.0.0.1  TOSHIBA
```

---

### Post by ejlal on 2009-06-21
[SIZE=3]there is no output to cat /etc/apt/sources.list

[/SIZE]

---

### Post by ejlal on 2009-06-21
[LEFT][SIZE=3]thanks [/SIZE][SIZE=3]sanemanmad,[/SIZE][SIZE=3] i did as u suggested and its gone now though i have no clue what was:
sudo: unable to resolve host TOSHIBA 
 i learn as i go so  i will appreciate if u explained it to me
 [/SIZE]
[/LEFT]

---

### Post by Sef on 2009-06-21
>  		[SIZE=3]there is no output to cat /etc/apt/sources.list[/SIZE]

What does it say when you do that in the terminal?

---

### Post by ejlal on 2009-06-21
[SIZE=3]it says nothing just an empty line i gues
here:
ejlal@TOSHIBA:~$ cat /etc/apt/sources.list

ejlal@TOSHIBA:~$ 
[/SIZE]

---

### Post by theozzlives on 2009-06-21
OP deleted the contents of his sources.list, therefore has no repositories. Do you have a file that says sources.list~? If you do go```
sudo rm etc/apt/sources.list
``` Then ```
sudo mv etc/apt/sources.list~ etc/apt/sources.list
```

---

### Post by ejlal on 2009-06-21
yes i eleted the contents of sources.list,so if i do these two commands ,will solve it?

---

### Post by ejlal on 2009-06-21
ejlal@TOSHIBA:~$ sudo rm etc/apt/sources.list
rm: cannot remove `etc/apt/sources.list': No such file or directory
ejlal@TOSHIBA:~$ ls /etc/apt
apt.conf.d   sources.list   sources.list.d     trustdb.gpg  trusted.gpg~
secring.gpg  sources.list~  sources.list.save  trusted.gpg
  see two files which one should i delete???

u missed "/" in the codes u gave me,i am learning about the command line so i fixed it,now what next?

---

### Post by ugm6hr on 2009-06-21
> **ejlal said:**
> u missed "/" in the codes u gave me,i am learning about the command line so i fixed it,now what next?

What is the output now?

```
cat /etc/apt/sources.list
```

---

### Post by ejlal on 2009-06-21
[SIZE=2]deb [http://ftp-stud.hs-esslingen.de/ubuntu/](http://ftp-stud.hs-esslingen.de/ubuntu/) hardy main universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main
deb [http://ftp-stud.hs-esslingen.de/ubuntu/](http://ftp-stud.hs-esslingen.de/ubuntu/) hardy-updates universe main

do u thing it might be a connection problem? i tried to change my download server it kept getting the same results!! 
[/SIZE]

---

### Post by ugm6hr on 2009-06-21
Are you running the original Toshiba version of Ubuntu 8.04?

If uncertain, post output from:
```
uname -a
lsb_release -a
```

---

### Post by ejlal on 2009-06-21
ejlal@TOSHIBA:~$ uname -a
Linux TOSHIBA 2.6.24-19-lpia #1 SMP Mon Nov 3 15:25:26 UTC 2008 i686 GNU/Linux
ejlal@TOSHIBA:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 8.04.1
Release:    8.04
Codename:    hardy

---

### Post by ugm6hr on 2009-06-21
The file should contaain the following contents (I think):
```
deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted
```

To edit the file:
```
gksudo gedit /etc/apt/sources.list
```
[COLOR="Red"]
DO NOT CHANGE YOUR DOWNLOAD SERVER[/COLOR]
The preconfigured netbook remixes use lpia architecture, which WILL NOT work with any of the standard download servers.  If you get errors, it is simply because these servers are a bit slow; be patient (or upgrade to a full i386 9.04NBR).

Ref: [http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=38457&tstart=-1](http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=38457&tstart=-1)

---

### Post by ejlal on 2009-06-21
> **ugm6hr said:**
> [COLOR=Red]
DO NOT CHANGE YOUR DOWNLOAD SERVER[/COLOR]
The preconfigured netbook remixes use lpia architecture, which WILL NOT work with any of the standard download servers.  If you get errors, it is simply because these servers are a bit slow; be patient (or upgrade to a full i386 9.04NBR)

my server is in uk but am actually in sudan >africa ,u mean  this will work just fine?i thought it has to do with distance:confused:, beside do i have to do any work or this will reset it??? coz i had already changed it!!
  
many thanks!

---

### Post by ugm6hr on 2009-06-21
If you rewrite your sources.list as advised above, it will revert back to the default (correct) lpia repositories.

There are no local mirrors for the lpia repositories (as far as I know).  Hence, changing your download server to a different one will cause it to stop working.

---

### Post by ejlal on 2009-06-22
now i get this message:
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>GPG error: [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix Release: The following signatures were invalid: BADSIG F9FDA6BED73CDC22 Canonical Archive Automatic Signing Key <ftpmaster@canonical.com>Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.



:(this is killing me!!

---

### Post by ugm6hr on 2009-06-22
Your repositoires are still not as I suggested above.

To confirm, once more:
```
cat /etc/apt/sources.list
```

EDIT:
I have attached a sample sources file.  Download it to your Desktop.

Then:
```
sudo mv ~/Desktop/sources.txt /etc/apt/sources.list
```

Then:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ejlal on 2009-06-22
ejlal@TOSHIBA:~$ cat /etc/apt/sources.list
deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-remix main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-remix main universe multiverse restricted
ejlal@TOSHIBA:~$

---

### Post by ugm6hr on 2009-06-22
You have 3 extra (incorrect lines) in that file:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main restricted

These all need to be removed.  Or just copy the example attached above.

---

### Post by ejlal on 2009-06-22
[FONT=monospace]
now iget this messege:
An error occured

The following details are provided:
W: GPG error: [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix Release: The following signatures were invalid: BADSIG F9FDA6BED73CDC22 Canonical Archive Automatic Signing Key <ftpmaster@canonical.com>


[/FONT]

---

### Post by ejlal on 2009-06-22
W: GPG error: [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix Release: The following signatures were invalid: BADSIG F9FDA6BED73CDC22 Canonical Archive Automatic Signing Key <ftpmaster@canonical.com>
W: You may want to run apt-get update to correct these problems
ejlal@TOSHIBA:~$ 
 how many times should i do the sudo apt-get update!!!!!!!!!!! ](*,)

---

### Post by ejlal on 2009-06-24
where should i be looking for Canonical Archive Automatic Signing Key
i did hundreds of sudo apt-get update it doesnt seem to fix it.i have read some where,that  the reason t am getting this error is because there is something changed at canonical and it was suppose to be fix thru new updates or something.i will appreciate if u helped me to fix this coz i got another error somehow depends on the updates.
thanks

---

### Post by ugm6hr on 2009-06-25
The lpia repositories have caused problems for some people before.

Read this: [http://mydellmini.com/forum/ubuntu-netbook-remix/5948-update-manager-cant-authenticated-message.html](http://mydellmini.com/forum/ubuntu-netbook-remix/5948-update-manager-cant-authenticated-message.html)

Afraid I can't help, since I no longer use the lpia repositories.

---

