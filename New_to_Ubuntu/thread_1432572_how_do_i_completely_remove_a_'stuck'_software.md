---
title: "how do i completely remove a 'stuck' software?"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by shindou01 on 2010-03-17
Dear friends..I'm a complete newbie to Ubuntu, i've just installed it on my laptop (Compaq Presario CQ40-401AU with 2GB ram) a couple of days ago.I was using windows 7 before and i am really pleased about using Ubuntu.

I installed Ubuntu Karmic Koala and I've managed to somehow connect my modem and use it to connect to the internet, did some updating and downloading softwares using the software center and update manager. 

Yesterday i got a .deb software (ztemtEVDO) that's supposed to be an additional software to use my modem to make calls and send text messages (I use ZTE AC2726 for my modem). It's installed successfully but the software wouldn't start no matter what I did so I decided to remove it. This is where my problem begun. When I opened the computer janitor, the package ztemtEVDO was there and i thought that i can remove it from there. I had it removed there, not sure what happened next but it seems that the software is still there and somehow it's 'stuck' there...I tried to search for solutions here in the forum and i tried some of it like using :

sudo apt-get install -f

and i got this

armz@armz-laptop:~$ sudo apt-get install -f
[sudo] password for armz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ztemtevdo
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 166394 files and directories currently installed.)
Removing ztemtevdo ...
ztemtvcdromd: no process found
dpkg: error processing ztemtevdo (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 ztemtevdo
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried other commands as well but most of them came out the same. I tried to use Synaptic Package Manager to remove it to no avail. The software is still listed there and since then everytime I try to install another software or update existing ones this error message keeps coming out in the details...

E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:

Can anyone help me please?
Thanks in advance

Sorry for the ridiculously long first post....

---

### Post by Ozymandias_117 on 2010-03-17
You can try
```
sudo dpkg-reconfigure -a
```
That may help you.

---

### Post by shindou01 on 2010-03-18
Thanks for the advice...
i just tried it and it came out like this

armz@armz-laptop:~$ sudo dpkg-reconfigure -a
[sudo] password for armz: 
 * Disabling power management...                                         [ OK ] 
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 * Checking battery state...                                             [ OK ] 
acpid stop/waiting
acpid start/running, process 3891
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.


Any other methods?cause after that command i tried to get an app using apt-get but i still get the same error message

armz@armz-laptop:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ztemtevdo
The following NEW packages will be installed:
  compizconfig-settings-manager
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/638kB of archives.
After this operation, 4,166kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 166394 files and directories currently installed.)
Removing ztemtevdo ...
ztemtvcdromd: no process found
dpkg: error processing ztemtevdo (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 ztemtevdo
E: Sub-process /usr/bin/dpkg returned an error code (1)


Anyway, thanks for trying to help...
Anyone else care to try and help?

---

### Post by shindou01 on 2010-03-18
Anyone? Can anybody please point me in the right direction?

---

### Post by Drenriza on 2010-03-18
cant you say

sudo apt-get --purge ztemtEVDO

---

### Post by shindou01 on 2010-03-18
armz@armz-laptop:~$ sudo apt-get --purge ztemtEVDO
[sudo] password for armz: 
E: Invalid operation ztemtEVDO

This is all I got...

Thanks anyway...

I just spent the last couple of hours reading the Ubuntu pocket guide trying to find commands i could use and i found one but it doesn't resolve the problem... I ended up with these instead :

armz@armz-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ztemtevdo
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 166394 files and directories currently installed.)
Removing ztemtevdo ...
ztemtvcdromd: no process found
dpkg: error processing ztemtevdo (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 ztemtevdo
E: Sub-process /usr/bin/dpkg returned an error code (1)
armz@armz-laptop:~$ sudo apt-get -f remove
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages will be REMOVED:
  ztemtevdo
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 166394 files and directories currently installed.)
Removing ztemtevdo ...
ztemtvcdromd: no process found
dpkg: error processing ztemtevdo (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 ztemtevdo
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone else up to the challenge?

---

### Post by mechro on 2010-03-18
> **shindou01 said:**
> armz@armz-laptop:~$ sudo apt-get --purge ztemtEVDO
[sudo] password for armz: 
E: Invalid operation ztemtEVDO

This is all I got...

Thanks anyway...

Anyone else up to the challenge?

Should that be all lowercase letters? Your error messages have it in lowercase.

---

### Post by shindou01 on 2010-03-18
> **mechro said:**
> Should that be all lowercase letters? Your error messages have it in lowercase.

Unfotunately, it doesn't make a difference....I still ended up with these :

armz@armz-laptop:~$ sudo apt-get --purge ztemtevdo
[sudo] password for armz: 
E: Invalid operation ztemtevdo

Thanks...

---

### Post by Drenriza on 2010-03-18
Is their a chance that your system has locked the files, and that is the reason to why you cannot remove them from the system?

---

### Post by shindou01 on 2010-03-18
> **Drenriza said:**
> Is their a chance that your system has locked the files, and that is the reason to why you cannot remove them from the system?

I don't think so...I tried searching for files related to the application but they're already gone...So i don't think that the files are locked by the system, because although the ztemtevdo is still listed in the synaptic package manager, the files related to it are gone already...Any ideas?

---

### Post by Paddy Landau on 2010-03-18
Try the following. I'm not at all sure that it will work, but as it seems to be confused about the files, it just may 'reset' what it's doing.


[LIST=1]
[*]Bearing in mind what Drenriza said, perhaps you should reboot first.
[*]Let's clear out obsolete programs: [FONT=Courier New]sudo apt-get -y autoremove[/FONT]
[*]Clear the cache: [FONT=Courier New]sudo apt-get -y clean[/FONT]
[*]Reinstall the package, exactly as you did the first time.
[*]Then, uninstall it: [FONT=Courier New]sudo apt-get purge ztemtevdo[/FONT]
[*]Repeat steps 2 and 3.
[/LIST]

Here's hoping.

---

### Post by plucky on 2010-03-18
Do the re-install and see if that works.

As a last resort,you can remove the package information from the dpkg status file.The file is located in ```
/var/lib/dpkg/
``` and is called **status**

It is a good idea to make a copy of the file first just in case you do it incorrectly.
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.backup
gksudo gedit /var/lib/dpkg/status
``` and search for **ztemtevdo** and remove all the information about that package.

Then run ```
sudo apt-get update
``` from a terminal to update the package information.

Good luck

---

### Post by shindou01 on 2010-03-18
> **Paddy Landau said:**
> Try the following. I'm not at all sure that it will work, but as it seems to be confused about the files, it just may 'reset' what it's doing.


[LIST=1]
[*]Bearing in mind what Drenriza said, perhaps you should reboot first.
[*]Let's clear out obsolete programs: [FONT=Courier New]sudo apt-get -y autoremove[/FONT]
[*]Clear the cache: [FONT=Courier New]sudo apt-get -y clean[/FONT]
[*]Reinstall the package, exactly as you did the first time.
[*]Then, uninstall it: [FONT=Courier New]sudo apt-get purge ztemtevdo[/FONT]
[*]Repeat steps 2 and 3.
[/LIST]

Here's hoping.

Well too bad it didn't work with your method Paddy...Thanks though....
Off to trying Plucky's method...

---

### Post by shindou01 on 2010-03-18
> **plucky said:**
> Do the re-install and see if that works.

As a last resort,you can remove the package information from the dpkg status file.The file is located in ```
/var/lib/dpkg/
``` and is called **status**

It is a good idea to make a copy of the file first just in case you do it incorrectly.
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.backup
gksudo gedit /var/lib/dpkg/status
``` and search for **ztemtevdo** and remove all the information about that package.

Then run ```
sudo apt-get update
``` from a terminal to update the package information.

Good luck
Great!
Thanks a lot plucky....It works!!
Thank you so much people....
You've all been a great help for me in my quest for understanding Ubuntu....
Problem solved...

Once again I thank you...
(It's real nice to be in this community....)

---

