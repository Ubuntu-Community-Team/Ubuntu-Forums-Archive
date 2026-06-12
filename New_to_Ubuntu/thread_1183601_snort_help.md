---
title: "snort help??"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by lord-of-war on 2009-06-10
ubuntu 9.04

Hey guys im having a problems, it all started after i tried to install "snort".

This is what happened, i typed "sudo apt-get install snort"
Then this error came up:

[FONT=Arial][I]"nick@nick-desktop:~$ sudo apt-get install snort
Reading package lists... Done
Building dependency tree       
Reading state information... Done
snort is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up snort (2.7.0-22ubuntu1) ...
 * Stopping Network Intrusion Detection System  snort                            * No running snort instance found
 * Starting Network Intrusion Detection System  snort                    [fail] 
invoke-rc.d: initscript snort, action "start" failed.
dpkg: error processing snort (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 snort
E: Sub-process /usr/bin/dpkg returned an error code (1)
nick@nick-desktop"[/I][/FONT]

Ever since that, its not letting me install any new applications, any time i try to install something like nessus.

"sudo apt-get install nessus"

[I]"nick@nick-desktop:~$ sudo apt-get install nessus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgdchart-gd2-noxpm libnessus2
Suggested packages:
  nessusd
The following NEW packages will be installed:
  libgdchart-gd2-noxpm libnessus2 nessus
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 410kB of archives.
After this operation, 1102kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe libgdchart-gd2-noxpm 0.11.5-6 [47.6kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe libnessus2 2.2.10-3 [113kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe nessus 2.2.10-3 [249kB]
Fetched 410kB in 3s (120kB/s)  
Selecting previously deselected package libgdchart-gd2-noxpm.
(Reading database ... 114751 files and directories currently installed.)
Unpacking libgdchart-gd2-noxpm (from .../libgdchart-gd2-noxpm_0.11.5-6_amd64.deb) ...
Selecting previously deselected package libnessus2.
Unpacking libnessus2 (from .../libnessus2_2.2.10-3_amd64.deb) ...
Selecting previously deselected package nessus.
Unpacking nessus (from .../nessus_2.2.10-3_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up snort (2.7.0-22ubuntu1) ...
 * Stopping Network Intrusion Detection System  snort                            * No running snort instance found
 * Starting Network Intrusion Detection System  snort                    [fail] 
invoke-rc.d: initscript snort, action "start" failed.
dpkg: error processing snort (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libgdchart-gd2-noxpm (0.11.5-6) ...

Setting up libnessus2 (2.2.10-3) ...

Setting up nessus (2.2.10-3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 snort
E: Sub-process /usr/bin/dpkg returned an error code "[/I]


Do i need to unistall snort? I've tried but i cant find it. I get the same error whenever i try and install anything, if someone can help me out i would greatly appreciate it.

---

### Post by Hospadar on 2009-06-10
what happens when you "sudo apt-get remove --purge snort"

---

### Post by cariboo on 2009-06-10
I've never used snort, but most service start up scripts are located in /etc/init.d, if snort is located there then try in a terminal:

```
sudo apt-get purge snort
```

---

### Post by lord-of-war on 2009-06-10
> **Hospadar said:**
> what happens when you "sudo apt-get remove --purge snort"

i get this 

[FONT=Arial][I]"nick@nick-desktop:~$ sudo apt-get remove --purge snort
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  snort*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
nick@nick-desktop:~$"

[/I]ts still interupting all my install/downloads [/FONT]and thank you i appreciate your help.

@cariboo, its not located in there

---

