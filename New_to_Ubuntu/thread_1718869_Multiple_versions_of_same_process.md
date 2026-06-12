---
title: "Multiple versions of same process"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by Zenmij on 2011-04-01
Hi.

Was just running a SCummVM game alongside VLC when everything grinded to a halt. Had to do a hard reboot. Now when I restart, I have multiple copies of the same processes spawning.

Need some help with this because my system becomes unresponsive after a while and a search yielded nothing.

Many Thanks


[ATTACH]187730[/ATTACH]

---

### Post by wt8008 on 2011-04-06
When you see multiple processes of the same program, this is a normal occurrence. Programs can spawn off multiple threads to attempt to be more productive, and the way you have htop setup, it shows each individual thread of all the programs. 

Try using a tree view and see if the threads share a parent process. If they don't that means you really have two different processes open.

Example try
```
ps aux | grep firefox
```
and
```
ps auxH | grep firefox
```
One prints processes and the other prints threads and processes

---

