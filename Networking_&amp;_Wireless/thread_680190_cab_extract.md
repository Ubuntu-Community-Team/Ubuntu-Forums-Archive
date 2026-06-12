---
title: "cab extract?"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by buccaneere on 2008-01-27
[HTML]E: Couldn't find package cabextract[/HTML]

Where does one get this critter?

---

### Post by buccaneere on 2008-01-27
Any ideas?

[HTML]chuckhp@chuckhp-laptop:~/bcm43xx$ wget ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe
--19:48:37--  ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe
           => `sp34152.exe.1'
Resolving ftp.hp.com... 15.217.49.21, 15.200.2.21
Connecting to ftp.hp.com|15.217.49.21|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp34001-34500 ... done.
==> PASV ... done.    ==> RETR sp34152.exe ... done.
Length: 4,494,456 (4.3M) (unauthoritative)

100%[======================================================================================>] 4,494,456    107.93K/s    ETA 00:00

19:49:15 (122.22 KB/s) - `sp34152.exe.1' saved [4494456]

chuckhp@chuckhp-laptop:~/bcm43xx$ cabextract sp34152.exe
The program 'cabextract' is currently not installed.  You can install it by typing:
sudo apt-get install cabextract
bash: cabextract: command not found
chuckhp@chuckhp-laptop:~/bcm43xx$ sudo apt-get install cabextract sp34152.exe.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cabextract
chuckhp@chuckhp-laptop:~/bcm43xx$ sudo apt-get install sp34152.exe.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sp34152.exe.1
chuckhp@chuckhp-laptop:~/bcm43xx$ sudo apt-get install cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cabextract
chuckhp@chuckhp-laptop:~/bcm43xx$ [/HTML]

---

