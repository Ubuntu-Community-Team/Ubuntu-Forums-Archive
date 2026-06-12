---
title: "can't install software"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by zankuu tenshouken on 2010-11-26
when i try to download software from software center 99% completes but after this it say
ubuntu version 10.10
~package operation failed~


~~~~~~~~~~details~~~~~~~~~~
nstallArchives() failed: Setting up tzdata (2010o-0ubuntu0.10.10) ... 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109. 
dpkg: error processing tzdata (--configure): 
 subprocess installed post-installation script returned error exit status 128 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 tzdata 
Setting up tzdata (2010o-0ubuntu0.10.10) ... 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109. 
dpkg: error processing tzdata (--configure): 
 subprocess installed post-installation script returned error exit status 128 
~~~~~~~~~~~~~~end~~~~~~~~~~~~
(i used compiz advanced desktop effects in this example)

this happened temporarly before i reinstalled ubuntu for 5 mins then it started to download normally


offtopic:is there an anti-virus for ubuntu?

---

### Post by Perfect Storm on 2010-11-26
Is it on a clean install? Have you installed all the updates first?
When/how did the error happen? Have you installed anything previously?

```
offtopic:is there an anti-virus for ubuntu?
```
Not really needed. Though there's anti-virus applications you can use to scan for windows virus on Windows via Ubuntu.

---

### Post by sikander3786 on 2010-11-26
Welcome to the forums :-)

Please go to Applications > Accessories > Terminal and post the output of

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

It would prompt you for a password but won't show any symbols or * when you type it. Just type blindly and hit enter and copy/paste the whole output here for both the commands.

And please use proper code tags # to wrap the output separately from post menu. [/code] at the end and [code] at the beginning of those outputs individually.

Regarding Anti-Virus, Ubuntu, in fact Linux doesn't need one. You can Google for that.

---

### Post by zankuu tenshouken on 2010-11-26
same thing happened(i was speaking to A.I)

---

### Post by zankuu tenshouken on 2010-11-26
nvm

it started to work after i runned the first command
(i'am not used to linux)
offtopic:is there anyway to run windows programs on linux?

---

### Post by sikander3786 on 2010-11-26
> it started to work after i runned the first command

It should've. But we needed to see the output as to find what was causing the problems and if the problem is completely gone or not.

Glad it is fixed for you anyway :-)

Happy Ubuntu-ing!

---

### Post by Penguin=) on 2010-11-26
> **zankuu tenshouken said:**
> nvm
offtopic:is there anyway to run windows programs on linux?


Yes there is this program called Wine, you can download it via the Ubuntu Software Center.

---

