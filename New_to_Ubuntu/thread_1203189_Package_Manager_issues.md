---
title: "Package Manager issues"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by govantim on 2009-07-03
On the right hand side of the top panel a STOP sign appeared, when putting mouse pointer over it this message appears .............................. An error occurred,please run Package Manager from the right click menu or apt-get in a terminal to see what is wrong. The error message was :'Error:Opening the cache ( E:Encountered a section with no Package : header, E: Problem with MergeList /var/lib/apt/lists/gb. archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages, E: The package lists or status file could not be parsed or opened.)' This usually means that your installed packages have unmet dependencies  :confused:

I right clicked over this sign to start Package Manager but got this message, E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

What's gone wrong ????

---

### Post by nhasian on 2009-07-03
try updating ubuntu to make sure all the packages are up to date.  open a terminal and type:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by govantim on 2009-07-03
> **nhasian said:**
> try updating ubuntu to make sure all the packages are up to date.  open a terminal and type:

```
sudo apt-get update && sudo apt-get upgrade
```

Applications - add/ remove, got this message ....... This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by govantim on 2009-07-03
> **nhasian said:**
> try updating ubuntu to make sure all the packages are up to date.  open a terminal and type:

```
sudo apt-get update && sudo apt-get upgrade
```

stephen@stephen-desktop:~$ sudo apt-get update
[sudo] password for stephen: 
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_GB
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_GB
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg [189B]                  
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB [52.6kB]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_GB
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [49.6kB]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB [4640B]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB [35.2kB]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB [47.5kB]
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg [189B]          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release         
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release [49.6kB]            
Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [48.4kB] 
Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [1330B]
Get: 12 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources [14.6kB]
Get: 13 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources [14B]
Get: 14 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages [12.1kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources                 
Get: 15 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources [2888B]
Get: 16 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages [14B]
Get: 17 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources [14B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Sources                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources
Get: 18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages [102kB]
Get: 19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Packages [2092B]
Get: 20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources [33.6kB]
Get: 21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Sources [611B]
Get: 22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages [29.0kB]
Get: 23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources [8659B]
Get: 24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages [675B]
Get: 25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources [639B]
Fetched 496kB in 1s (389kB/s)                  
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
stephen@stephen-desktop:~$ sudo apt-get install -f
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by austinpsycho on 2009-07-03
I assume you tried synaptic? one of the things on the bottom of the synaptic window is broken packages.. if you find any; update them, and violla..

---

### Post by govantim on 2009-07-03
> **austinpsycho said:**
> I assume you tried synaptic? one of the things on the bottom of the synaptic window is broken packages.. if you find any; update them, and violla..

When opening synaptic got this, E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by nhasian on 2009-07-03
i have two more suggestions:

try changing the source from where you download your updates from in System->administration->Software sources.  On the first tab labeled *Ubuntu Software* change the dropdown menu *Download from* to other, and select a mirror close to you.

after that you can try:

```
sudo apt-get update && sudo apt-get install -f
```

---

### Post by govantim on 2009-07-03
> **nhasian said:**
> i have two more suggestions:

try changing the source from where you download your updates from in System->administration->Software sources.  On the first tab labeled *Ubuntu Software* change the dropdown menu *Download from* to other, and select a mirror close to you.

after that you can try:

```
sudo apt-get update && sudo apt-get install -f
```

SUCCESS, thank you nhasian and all others for your time and your patience, ):P):P

---

### Post by austinpsycho on 2009-07-03
Did you do any manual editing of the config files involved; I been poking around other forums; and it turns out that they don't accept comments in the /etc/apt/preferences file.

---

### Post by govantim on 2009-07-03
> **austinpsycho said:**
> Did you do any manual editing of the config files involved; I been poking around other forums; and it turns out that they don't accept comments in the /etc/apt/preferences file.

Everything seems fine now, but no, I didn't alter anything, two days ago my internet connection went down, something to do with Avahi ?? couldn't access synaptic etc, put pc on this morning and net connection ok :confused:

---

