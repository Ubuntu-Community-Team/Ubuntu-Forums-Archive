---
title: "Need Some Help Fixing Synaptic Package Manager"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Stunn on 2009-01-19
Hey everyone, i just installed ubuntu a day ago and i love it. i am not really a coder so i dont understand what ubuntu is trying to tell me about the error with the synaptic package manager. so the error i get is:

[B]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 55 in source list /etc/apt/sources.list, E:The list of sources could not be read.'  
[/B]
and i cannot use the synaptic pkg manager and add/remove.

i look a little on the net but i couldn't make heads or tails of how to solve this. i did do a few tests and it told me the same thing:

[B]sam@samBuntu:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for sam: 
E: Type '“deb' is not known on line 55 in source list /etc/apt/sources.list
sam@samBuntu:~$ [/B]

i don't really know how to get to line 55 or  even what line 55 is, so help please !! lol.Thanks in advance and if any one can tell me how to avoid this problem it will be really appreciated.

                           Love and Peace.

---

### Post by Titan8990 on 2009-01-19
Line 55 is going to be the 55th line of the text file /etc/apt/sources.list.


Post its contents here.

---

### Post by BDNiner on 2009-01-19
yes there is an issue with line 55 of your /etc/apt/sources.list file. you can comment it out with # or post the contents here and try to figure out what is incorrect in the file.

---

### Post by Stunn on 2009-01-19
do i just type /etc/apt/sources.list. cuz it tells me no such file or directory... so am guessing thats not the way to do it so can u please be a little more specific cuz am really uneducated when it comes to this stuff. :) sorry :confused:

---

### Post by taurus on 2009-01-19
Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by mc4100 on 2009-01-19
> **Stunn said:**
> do i just type /etc/apt/sources.list. cuz it tells me no such file or directory... so am guessing thats not the way to do it so can u please be a little more specific cuz am really uneducated when it comes to this stuff. :) sorry :confused:

Just open a Terminal (Applications -> Accessories -> Terminal), and paste:
```
cat /etc/apt/sources.list
```
... and copy it here, so we can have a look.

---

### Post by drs305 on 2009-01-19
Type this in a terminal window:
```
gksudo gedit +55 /etc/apt/sources.list
```
It should open the text editor with the cursor on line 55 (after you enter your password and press ENTER).

---

### Post by oldos2er on 2009-01-19
Open a terminal and copy and paste this:

```
cat /etc/apt/sources.list
```

 then copy and paste the output here.

---

### Post by Stunn on 2009-01-19
wow dudes u guys are flippin' awesome with the response
here it is:

sam@samBuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”
sam@samBuntu:~$ 

Thanks

---

### Post by mc4100 on 2009-01-19
> deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
**&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main&#8221;**
There's the problem, and by the way, these are really, really out of date.
To remove these lines, press Alt+F2:
```
gksu gedit /etc/apt/sources.list
```
and delete the lines, then save. Finally, open a terminal again:
```
sudo apt-get update
```

Edit: Strictly speaking, you only need to delete that last line, but as I said it looks to surely be severely out-of-date software, and automatix is notorious for causing software management problems/system instability.

---

### Post by Stunn on 2009-01-19
wow that fixed it thanx for all you help. tho after i do the get update thing i get like E: Some index files failed to download, they have been ignored, or old ones used instead. but watever the synaptic package works so am happy. btw is there a place where i can fine a list of commands  so that am not completely useless when it comes to theres things ?? Thanks

---

### Post by taurus on 2009-01-19
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by Stunn on 2009-01-19
Thanx Again. Love and Peace

---

### Post by mc4100 on 2009-01-19
> **Stunn said:**
> Is there a place where i can fine a list of commands  so that am not completely useless when it comes to theres things ?? Thanks

[This]("https://help.ubuntu.com/8.10/basic-commands/C/") seems easy enough.

---

### Post by recon04 on 2009-07-25
>.> this seems like the perfect place to paste this  i seem to have the same problem as the first guy but my readout isnt the same as his so ill paste it here an see if i can get some help 

E: Type '‘deb-src' is not known on line 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


recon04@equlibrium:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

‘deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main’
‘deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main’
‘deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main’
‘deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main’
‘deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main’
recon04@equlibrium:~$

---

### Post by drs305 on 2009-07-25
Remove the quotes from all the lines in the last section:
Open with 
```

gksudo gedit /etc/apt/sources.list

```

> 
&#8216;deb-src [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main&#8217;
&#8216;deb [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main&#8217;
&#8216;deb-src [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main&#8217;
&#8216;deb [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main&#8217;
&#8216;deb-src [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main&#8217;


Change to:
> 
deb-src [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu) jaunty main


---

### Post by swoody on 2009-07-25
> **recon04 said:**
> &#8216;deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main&#8217;
&#8216;deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main&#8217;
&#8216;deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main&#8217;
&#8216;deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main&#8217;
&#8216;deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main&#8217;

There is your problem. You must edit the file, and remove the ' marks before **AND** after all those entries. Simply run:
```
gksu gedit /etc/apt/sources.list
```
That will open the file for you to edit. Just delete the ' marks, and save the file. Then run:
```
sudo apt-get update
```
and you should be good to go :)

---

### Post by recon04 on 2009-07-25
thanks for the help that fixed it right up guys :D

---

