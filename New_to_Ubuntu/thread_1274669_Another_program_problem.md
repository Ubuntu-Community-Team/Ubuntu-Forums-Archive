---
title: "Another program problem"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by ssdt on 2009-09-24
I receive this error when i try accessing the add/remove:

[I]Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.[/I]

For the Synaptic I recieve this error and can't access any of them to install/update my programs 

[I]E: Type 'a' is not known on line 3 in source list /etc/apt/sources.list.d/pidgin-ppa.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
[/I]

Is there any way to get out of this situation?

Thank you

---

### Post by kansasnoob on 2009-09-24
> **ssdt said:**
> I receive this error when i try accessing the add/remove:

[I]Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.[/I]

For the Synaptic I recieve this error and can't access any of them to install/update my programs 

[I]E: Type 'a' is not known on line 3 in source list /etc/apt/sources.list.d/pidgin-ppa.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
[/I]

Is there any way to get out of this situation?

Thank you

Well post the output from Terminal of:

```
cat /etc/apt/sources.list
```

---

### Post by cranecreek on 2009-09-24
Did you change your sources.list. If I do that from the terminal I also have to do apt-get update from the terminal as well, else synaptic freezes up. Good luck.

---

### Post by ssdt on 2009-09-25
Here is the output that I recieved from the terminal:

```
## deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main universe restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe main multiverse restricted #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main universe restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe main multiverse restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security multiverse main universe restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security multiverse main universe restricted #Added by software-properties
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
```

---

### Post by NoaHall on 2009-09-25
You need to do "cat /etc/apt/sources.list.d/pidgin-ppa.list" and post output. That's where the error is ;)

---

### Post by ssdt on 2009-09-25
wierd but it just returned me with this 


datta@dell-desktop:~$ cat /etc/apt/sources.list.d/pidgin-ppa.list

a
a
datta@dell-desktop:~$

---

### Post by NoaHall on 2009-09-25
Then "gksudo gedit /etc/apt/sources.list.d/pidgin-ppa.list"
and remove the a's

---

### Post by ssdt on 2009-09-25
Thank you, that solved the issue. Thank you for the information.

---

