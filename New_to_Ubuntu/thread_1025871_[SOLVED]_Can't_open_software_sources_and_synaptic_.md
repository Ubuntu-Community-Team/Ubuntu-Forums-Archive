---
title: "[SOLVED] Can't open software sources and synaptic package manager!"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by marcgh on 2008-12-30
Whenever I try to open 

system:administration:software sources
or
system:administration:synaptic package manager

mouse cursor will spin for 10 to 20 seconds after that nothing happens.

any ideas?
thanks in advance

---

### Post by fooman on 2008-12-30
try updating the repositories from a terminal and see what errors pop up,  then post them back here for someone to take a look at.

open a terminal (appications > accessories > terminal) and type or copy/paste the following into it:

```
sudo apt-get update
```

press enter followed by your password and see what happens.

---

### Post by wolfen69 on 2008-12-30
just try rebooting first. sometimes things can get hung up.

---

### Post by marcgh on 2008-12-30
> **fooman said:**
> try updating the repositories from a terminal and see what errors pop up,  then post them back here for someone to take a look at.

open a terminal (appications > accessories > terminal) and type or copy/paste the following into it:

```
sudo apt-get update
```

press enter followed by your password and see what happens.
this is what I got :

user@user-ubuntu:~$ sudo apt-get update
sudo: unable to resolve host user-ubuntu
[sudo] password for user: 
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy Release.gpg                          
Ign [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy/main Packages
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy/restricted Packages
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy/main Sources
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy/restricted Sources
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy/universe Sources
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://gh.archive.ubuntu.com](http://gh.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
user@user-ubuntu:~$

---

### Post by fooman on 2008-12-30
try this one in a terminal and post the results back here again:

```
cat /etc/hosts
```

---

### Post by marcgh on 2008-12-30
> **wolfen69 said:**
> just try rebooting first. sometimes things can get hung up.
Thanks for the suggestion but it did not work.

---

### Post by marcgh on 2008-12-30
> **fooman said:**
> try this one in a terminal and post the results back here again:

```
cat /etc/hosts
```
I got this :

user@user-ubuntu:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 user-ubuntu.WORKGROUP

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
user@user-ubuntu:~$

---

### Post by dubhear on 2008-12-30
how many account do you have...

...if you got any else account try to use them instead and see if it helps

---

### Post by fooman on 2008-12-30
you need to edit the /etc/hosts file.  run this command to open gedit as root so you can make the edit:

[FONT=monospace]
[/FONT]```
[FONT=monospace]gksudo gedit /etc/hosts[/FONT]
```[FONT=monospace]

when it opens,  remove the ".WORKGROUP" from the second line...so that the top section looks like this:

[/FONT]```
127.0.0.1 localhost
127.0.1.1 user-ubuntu
```

then save and close the file.

try synaptic again and see if its fixed.

---

### Post by marcgh on 2008-12-30
> **dubhear said:**
> how many account do you have...

...if you got any else account try to use them instead and see if it helps
Not sure I understand your question.
If it is user accounts I have only one: user

---

### Post by dubhear on 2008-12-30
this just cought my attention, from your later posts

in terminal you get:
sudo: unable to resolve host user-ubuntu

but try the foomans latest post if it helps and tell us more

---

### Post by ajcham on 2008-12-30
> **fooman said:**
> you need to edit the /etc/hosts file.  run this command to open gedit as root so you can make the edit:

[FONT=monospace]
[/FONT]```
[FONT=monospace]gksudo gedit /etc/hosts[/FONT]
```[FONT=monospace]

when it opens,  remove the ".WORKGROUP" from the second line...so that the top section looks like this:

[/FONT]```
127.0.0.1 localhost
127.0.1.1 user-ubuntu
```

then save and close the file.

try synaptic again and see if its fixed.

I think you will need to do this from a Live CD environment - otherwise you will experience the same error when trying to use gksu. Be sure to amend the gedit command above to refer to the /etc/hosts file on your HD, rather than the one in the live environment.

---

### Post by BatsotO on 2008-12-30
Your command line shows that your hostname is user-ubuntu, but the line in etc/hosts said user-ubuntu.WORKGROUP. I wonder how does it happen.

---

### Post by marcgh on 2008-12-30
> **fooman said:**
> you need to edit the /etc/hosts file.  run this command to open gedit as root so you can make the edit:

[FONT=monospace]
[/FONT]```
[FONT=monospace]gksudo gedit /etc/hosts[/FONT]
```[FONT=monospace]

when it opens,  remove the ".WORKGROUP" from the second line...so that the top section looks like this:

[/FONT]```
127.0.0.1 localhost
127.0.1.1 user-ubuntu
```

then save and close the file.

try synaptic again and see if its fixed.
I don't know how to thank you for your assistance, I did as you wrote, restarted the computer and try to open both.....PERFECT.

Thanks again!

---

### Post by marcgh on 2008-12-30
following the forum rules, should we clode this thread as solved?

---

### Post by BatsotO on 2008-12-30
No! Istill wonder how come that WORKGROUP get in the hosts.
Well but that just me. :confused:

---

### Post by marcgh on 2008-12-30
> **BatsotO said:**
> No! Istill wonder how come that WORKGROUP get in the hosts.
Well but that just me. :confused:
Thanks for your concern. But I think I know.
You have to know that I am close to zero in networking - even with XP.
when, 3 days ago I installed Ubuntu I could not connect to the local network and - in XP - you check if you are at the same workgroup.
I think I put this somehow in the network settings.
sorry for the trouble but thanks again

---

### Post by ajcham on 2008-12-30
> **BatsotO said:**
> No! I still wonder how come that WORKGROUP get in the hosts.
Well but that just me. :confused:

@marcgh: is your Ubuntu box networked with Windows machines?  I've read that the .WORKGROUP bit may be related to that.

EDIT: Oh, NM, you figured it out!

---

### Post by dubhear on 2008-12-30
just mark the thread as solved, and dont forget to thank fooman

that's all

---

### Post by BatsotO on 2008-12-30
You should consider installing samba and search the forum for windows share.
And don't be sorry about your trouble, that's why most of us here in the first place, trouble.

---

### Post by fooman on 2008-12-30
> **marcgh said:**
> ....
I think I put this somehow in the network settings.
sorry for the trouble but thanks again

yep,  that will do it...i've done it myself that exact same way,  which is why i was familiar with a fix.

no trouble at all...glad i could help.  :)

---

### Post by marcgh on 2008-12-30
> **ajcham said:**
> @marcgh: is your Ubuntu box networked with Windows machines?  I've read that the .WORKGROUP bit may be related to that.

EDIT: Oh, NM, you figured it out!
Yes, on the network there are 3 other machines:

1x PC PIII running XP pro sp2 for the kids ( but yet NO internet on it )
1x laptop for general use
1x Free comm internet radio

Laptop & PC and this machine ( when running XP ) are all in WORKGROUP

I will follow the suggestion from BatsotO.

Thanks to all of you!

---

