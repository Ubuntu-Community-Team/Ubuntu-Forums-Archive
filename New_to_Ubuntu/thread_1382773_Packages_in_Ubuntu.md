---
title: "Packages in Ubuntu"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by vanhornd on 2010-01-16
Hello,

When I'm trying to get and install a package in Ubuntu I get stuff like this quite often and its kind of discouraging. It probably would help me if I understood what the root problem is and what the error implies:

sudo apt-get install phpmyadmin
Reading package lists . . . Done
Building dependency tree
Reading state information . . . Done
Some packages could not be installed.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  phpmyadmin:  Depends:  php5-mcrypt but it is not installable
E:  Broken packages

My version of Ubuntu is Karmic Koala.

---

### Post by Paqman on 2010-01-16
Open up Synaptic > Edit > Fix broken packages > Apply marked changes > Apply.

---

### Post by SaucE on 2011-01-16
I am having the exact same issue.  

OS: Ubuntu 9.04
root@x:~# apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  phpmyadmin: Depends: php5-mcrypt but it is not installable
E: Broken packages

---

### Post by yeats on 2011-01-16
Can (either of you) do ```
sudo apt-get -f install
``` and then post the output?  (Use CODE tags - use the # button when composing).

This does the same thing as what Paqman suggested, but with enough feedback that might provide clues to the problem.

---

### Post by SaucE on 2011-01-16
```
root@x:~# sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
```

Here you are.

---

### Post by gmargo on 2011-01-16
Do your upgrade first; that's probably what is interfering.
```

$ sudo apt-get update
$ sudo apt-get dist-upgrade

```reboot if needed, then try to install again.

---

### Post by migs73 on 2011-01-16
> **SaucE said:**
> ```
root@x:~# sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
```

Here you are.

Worryingly you are logged in as root!
Have you done this for a reason??

---

### Post by SaucE on 2011-01-16
> **gmargo said:**
> Do your upgrade first; that's probably what is interfering.
```

$ sudo apt-get update
$ sudo apt-get dist-upgrade

```reboot if needed, then try to install again.

Did exactly as you said.

```
sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  phpmyadmin: Depends: php5-mcrypt but it is not installable
E: Broken packages
```

---

### Post by SaucE on 2011-01-16
Sorry for double post.  Not sure why it posted twice.

---

### Post by gmargo on 2011-01-16
Do you have some packages from a ppa repository installed? That could be interfering.

I suggest giving  **aptitude(8)** a try.
```

$ sudo aptitude -V install phpmyadmin

```The reason I like aptitude is because it will suggest solutions to incompatibilities like you are probably experiencing here.

---

### Post by SaucE on 2011-01-16
I get an entirely different error with that.

```
sudo aptitude -V install phpmyadmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  phpmyadmin [4:3.1.2-1ubuntu0.2]
The following NEW packages will be installed:
  dbconfig-common{a} [1.8.40ubuntu1]
The following packages will be REMOVED:
  libdns45{u} [1:9.5.1.dfsg.P2-1ubuntu0.4]
0 packages upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
FATAL -> Failed to fork.
```

---

### Post by oldos2er on 2011-01-16
9.04 reached its end-of-life last October, so you might want to try the old releases repos: [http://atlanticlinux.ie/blog/?p=143](http://atlanticlinux.ie/blog/?p=143)

---

