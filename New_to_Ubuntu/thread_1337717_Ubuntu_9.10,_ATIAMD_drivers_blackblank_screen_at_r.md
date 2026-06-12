---
title: "Ubuntu 9.10, ATI/AMD drivers black/blank screen at reboot"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by u.b.u.n.t.u on 2009-11-25
**PROBLEM**
Installing the recommended ATI driver will result in black/blank screen.


**SOLUTION**
Revert back to the default graphics driver.

Deleting the xorg.conf file, then rebooting, will automatically reconfigure the default working graphics driver.


**MEHTOD**
1. restart your computer (warm or cold boot)
2. select to start ubuntu (if you have a dual boot system)
3. select ```
Ubuntu, Linux 2.6.31-15 generic (recovery mode)
```
4. select ```
root Drop to root shell prompt
```
5. at the root prompt type the following (root prompt and code as per below)
```
root@ubuntu:~# rm /etc/X11/xorg.conf
```
6. restart your computer
7. log into ubuntu as per normal

8. do NOT install the following again! ;)

[IMG]http://img187.imageshack.us/img187/8937/screenshothardwaredrive.png[/IMG]

---

### Post by Zoot7 on 2009-12-01
I had to boot in recovery mode and remove xorg and then re-install my Nvidia driver after upgrading to 2.6.31-15.

---

### Post by TryingLinuxAgain on 2009-12-03
This is too bad!  :-(
I was a new Ubuntu user and was completely happy with 9.x that I had downloaded from the web.  Had used it for several months.

Then, yesterday, I upgraded to 9.10 and had this problem.

Unfortunately I didn't find this post until after I started to re-install, so now I'll have 9.10 and the original one.  My plan is to backup my local email files (which I had just finally converted a few days ago) then wipe the whole thing and try 9.10 again.

Ubuntu is getting close to something that could unseat windows - but still have to work around stuff like this!

---

### Post by mistermudd on 2009-12-22
I had this issue, and it drove me nuts. Still does actually. Is there anyway to get 3D effects working?

---

### Post by maxrpowell on 2010-03-22
[SIZE=3]Does anyone know of anyone who has a fix for this problem (or is that not possible). I know that I had full support for #D graphics on 8.10 and 9.04. Links Please.[/SIZE]

---

