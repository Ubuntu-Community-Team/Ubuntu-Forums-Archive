---
title: "problems running the game icebreaker"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-04-29
this is no big deal just something i would like to fix for my wife. the game icebreaker avail from the appl/add/remove was working fine in 8.04. when i was testing ubuntu 9.04 had the problem with it not working. since i upgrade to 9.04 cant get it to work. here is the weird thing if i change to a guest desktop the game will work. however once i exit the game in the guest mode it wouldnt start at all.and i cant get it to work when at my desktop or my daughters. any ideas

---

### Post by carml on 2009-04-29
Did you try to reinstall the game under Jaunty?
It's just a shot in the dark.

---

### Post by rburkartjo on 2009-04-29
carml tried that but to no avail. tks though

---

### Post by rburkartjo on 2009-04-29
also tried the following
ray@ray-desktop:~$ sudo apt-get remove icebreaker-* --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting icebreaker for regex 'icebreaker-*'
The following packages will be REMOVED:
  icebreaker*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 213kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 162847 files and directories currently installed.)
Removing icebreaker ...
Purging configuration files for icebreaker ...
Processing triggers for man-db ...
Processing triggers for menu ...
ray@ray-desktop:~$ 

then tried to reinstall from appl/add/remove
same problem

---

### Post by rburkartjo on 2009-06-24
just wondering if anyone can still help. just cant figure out what to do. it if for my wife/tks

---

### Post by carml on 2009-06-24
Have you checked if there's a new version of icebreaker? It's an other shot in the dark,sorry.

---

### Post by rburkartjo on 2009-06-26
car tks for all your help but still cant get it to work. no big thing.

---

### Post by mikechant on 2009-06-26
Does it create a .icebreaker config folder in your home directory?
If so have you tried deleting this (don't forget to have 'display hidden files' on)?

This might explain why it works in the guest account - no existing config exists.

---

### Post by rburkartjo on 2009-06-26
mike tks for your kind advise. i have already looked no there is not one. and it just baffles me because when i open a quest account it will load but only once and be fully funtional. if you close it will not load again. my wife has alz (not a joke) and just loves to play this game

---

### Post by rburkartjo on 2009-06-26
also tried to open as root and received this error

ray@ray-desktop:~$ sudo -i
root@ray-desktop:~# icebreaker & exit
[1] 6618
logout
ray@ray-desktop:~$ Command 'icebreaker' is available in '/usr/games/icebreaker'
The command could not be located because '/usr/games' is not included in the PATH environment variable.
-bash: icebreaker: command not found

---

