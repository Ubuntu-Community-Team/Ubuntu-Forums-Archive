---
title: "Problems cant access Ubuntu software center, Synaptic Package Manager"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by Alif Radzi on 2011-03-23
i just tried out to change my ubuntu into macOSX theme..however after i restart my computer
i cant access my Ubuntu software center, Synaptic Package Manager, even for some command on terminal will also occurs an error..

**In Ubuntu Software Center (error)**
*There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.*
[COLOR=Blue]
[I][B]Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.[/B][/I][/COLOR]

**In Synaptic Package Manager**
Unable to get exclusive lock
*This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.*
(i cant even access to synaptic package manager)

**In Terminal**

t[COLOR=Blue][B]eyalif@teyalif-Compaq-Presario-CQ40-Notebook-PC:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
teyalif@teyalif-Compaq-Presario-CQ40-Notebook-PC:~$ dpkg --purge -a
dpkg: requested operation requires superuser privilege
teyalif@teyalif-Compaq-Presario-CQ40-Notebook-PC:~$ sudo su
root@teyalif-Compaq-Presario-CQ40-Notebook-PC:/home/teyalif# sudo su
root@teyalif-Compaq-Presario-CQ40-Notebook-PC:/home/teyalif# apt-cache search *
root@teyalif-Compaq-Presario-CQ40-Notebook-PC:/home/teyalif# apt-get -f install dream chess
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@teyalif-Compaq-Presario-CQ40-Notebook-PC:/home/teyalif# 
[/B][/COLOR]

---

### Post by barbedsaber on 2011-03-23
It's great that you're trying to make the output more readable with the different colour, but it doesn't help

You can put ```
 tags around them by highlighting them and clicking on the hash above the message feild.

[CODE]it should look like this
```

---

### Post by oklokl on 2011-03-23
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
In my case


sudo apt-get remove *name Services*
error Services Put it

System out..
Reboot

---

### Post by fabricator4 on 2011-03-23
> **Alif Radzi said:**
> 
(i cant even access to synaptic package manager)


See if a re-boot fixes the problem.  If not, open a terminal and type the following:

```

sudo dpkg --configure -a

```

If there was an update or install that did not finish normally then this should finish the process and put everything back to normal.

Chris

---

### Post by Alif Radzi on 2011-03-23
teyalif@teyalif-Compaq-Presario-CQ40-Notebook-PC:~$ sudo apt-get install -f
[sudo] password for teyalif: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

teyalif@teyalif-Compaq-Presario-CQ40-Notebook-PC:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process


theres no running programs or what so ever..but still i cant access with my correct password

---

### Post by Dutch70 on 2011-03-23
There is something else running, to find out what it is, try this...
```
fuser /var/lib/apt/lists/lock
```

or this... 
```
lsof|grep /var/lib/apt/lists/lock
```

---

### Post by oklokl on 2011-03-23
ex>
sudo cat ( )
ex> sudo cat system 
=[print view number]
or
gnome-system-monitor view
sudo kill 779
ex> sudo apt-get remove ttf-mscorefonts-installer
re> sudo apt-get install system name
sudo apt-get install -f

---

