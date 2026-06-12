---
title: "New to Ubuntu 9.04, please help! Error message"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by xFlowx on 2009-06-29
Hi! I'm very new to Ubuntu, I just started using it last night. I keep trying to install Adobe Flash player, but my update thingy keeps giving me this error message: "Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 1 in source list /etc/apt/sources.list.d/pidgin-ppa.list (dist parse), E:The list of sources could not be read.'"

I don't know how to report a bug,  otherwise I would have already. But I have no idea how to fix this, and it's really starting to bug me because I just switched over from Windows...and I don't have any music on this computer.

Thank you for any and all help!

---

### Post by halitech on 2009-06-29
can you open a terminal and paste the results of
```
cat /etc/apt/sources.list
```

---

### Post by oldos2er on 2009-06-29
Please enter the following into a terminal, and post the output here:
```
cat /etc/apt/sources.list.d/pidgin-ppa.list
```

---

### Post by jerome1232 on 2009-06-29
--edit--

Looks like some people have posted before looking at the contents of the file, just do that instead of moving it out like i was suggesting.

---

### Post by xFlowx on 2009-06-29
> **halitech said:**
> can you open a terminal and paste the results of
```
cat /etc/apt/sources.list
```
 When I did that, I got
```
flow@ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
flow@ubuntu:~$ 

```

---

### Post by xFlowx on 2009-06-29
> **oldos2er said:**
> Please enter the following into a terminal, and post the output here:
```
cat /etc/apt/sources.list.d/pidgin-ppa.list
```

When I did that, I got [codecat /etc/apt/sources.list.d/pidgin-ppa.list[/code]

---

### Post by oldos2er on 2009-06-29
> **xFlowx said:**
> When I did that, I got [codecat /etc/apt/sources.list.d/pidgin-ppa.list[/code]
  
 Please copy and paste the text within the code box, without the "code" marks.

---

### Post by xFlowx on 2009-06-29
> **oldos2er said:**
> Please copy and paste the text within the code box, without the "code" marks.
  Haha, oops. Now I got:
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) main

---

### Post by jerome1232 on 2009-06-29
It should be

```
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main 

```

To make that happen you could do this

```
gksu gedit /etc/apt/sources.list.d/pidgin-ppa.list
```
then change the line, save then try installing flash

---

### Post by xFlowx on 2009-06-29
> **jerome1232 said:**
> It should be

```
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main 

```To make that happen you could do this

```
gksu gedit /etc/apt/sources.list.d/pidgin-ppa.list
```then change the line, save then try installing flash

When I did that, it spit this out :
```
 flow@ubuntu:~$ deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main
bash: deb: command not found
flow@ubuntu:~$ deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main
bash: deb: command not found
flow@ubuntu:~$ sudo cat deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main > /etc/apt/sources.list.d/pidgin-ppa.list
bash: /etc/apt/sources.list.d/pidgin-ppa.list: Permission denied
flow@ubuntu:~$ sudo apt-get update
[sudo] password for flow: 
E: Malformed line 1 in source list /etc/apt/sources.list.d/pidgin-ppa.list (dist parse)

```I have no idea what to do Dx And I must leave for school soon.

---

### Post by oldos2er on 2009-06-29
Run the "gksu gedit...." command first.

---

### Post by xFlowx on 2009-06-29
> **oldos2er said:**
> Run the "gksu gedit...." command first.


That did nothing..o____o

---

### Post by jerome1232 on 2009-06-29
Maybe an easier way :

```
sudo -i
echo "deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main" > /etc/apt/sources.list.d/pidgin-ppa.list
apt-get update
exit
```

This you can copy paste and it'll work.

---

### Post by xFlowx on 2009-06-29
> **jerome1232 said:**
> Maybe an easier way :

```
sudo -i
echo "deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main" > /etc/apt/sources.list.d/pidgin-ppa.list
apt-get update
exit
```This you can copy paste and it'll work.


Ahh! Thank you so much, it's working now!

Now if I could only get my webcam driver installed...XD

---

