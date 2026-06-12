---
title: "login failure &quot;.ICEauthority...&quot;"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by stoppage on 2009-04-11
When I log into Ubuntu (8.04 running Gnome desktop) a message now pops up...
„Gnome session manager can't unlock..ICEauthority...“ and I can't get any further.
Sytem has been running ok for months. I checked permissions with failsafe terminal...
ls -l/home/tony.ICEauthority returns..-rw------1 tony tony 2135.....date etc.
I can only get in as root from the recovery mode. Can anybody help me out here please?

---

### Post by taurus on 2009-04-11
At the GUI login screen, press <Ctrl><Alt>F2 and log in with your username and password.  Then, post the output of this command.

```
ls -la ~
```

---

### Post by stoppage on 2009-04-11
The return from command ls -la is lenghty...in terminal I dont know how to copy. By the way what is ls -la ~
as you've entered above?
ls -la /home/tony.ICEauthority returns"cannot access...no such...."

---

### Post by albinootje on 2009-04-11
> **stoppage said:**
>  I can only get in as root from the recovery mode. Can anybody help me out here please?

Can you remove that file as root, then reboot, and try again ?

---

### Post by taurus on 2009-04-11
How about

```
ls -la /home
ls -la ~/.ICEauthority
```

---

### Post by stoppage on 2009-04-11
On an 8.04 livecd....
**ubuntu@ubuntu:~$ ls -la /media/disk/tony **
total 6971 
dr-xr-xr-x 90 1000 1000    4312 2009-04-11 18:48 . 
drwxr-xr-x  6 root root     128 2009-04-11 13:11 .. 
drwxr-----  3 1000 1000      80 2008-11-04 09:34 .adobe 
drwxr-xr-x  2 1000 1000     336 2008-11-07 22:15 ALICE 
-rw-r--r--  1 1000 1000   19407 2008-11-04 08:45 ALICE INFO.odt 
drwx------  2 1000 1000      72 2008-11-04 09:34 .aptitude 
......
....
....
..... 
**-rw-------  1 1000 1000   21135 2009-03-29 15:10 .ICEauthority **
drwxr-xr-x  2 1000 1000      48 2009-01-23 07:31 .icons 
drwxr-xr-x 12 1000 1000    8440 2009-04-02 21:46 Images 
-rw-r--r--  1 1000 1000   37844 2008-11-15 02:28 installed-software 
.....
.....
.... 
[B]ubuntu@ubuntu:~$ ls -la /media/disk/tony.ICEauthority 
ls: cannot access /media/disk/tony.ICEauthority: No such file or directory 

and I haven't yet deleted.....bloody .ICE file
[/B]

---

### Post by stoppage on 2009-04-11
Deleted .ICEauthority file, made no difference

---

### Post by sandyd on 2009-04-11
> **stoppage said:**
> On an 8.04 livecd....
**ubuntu@ubuntu:~$ ls -la /media/disk/tony **
total 6971 
dr-xr-xr-x 90 1000 1000    4312 2009-04-11 18:48 . 
drwxr-xr-x  6 root root     128 2009-04-11 13:11 .. 
drwxr-----  3 1000 1000      80 2008-11-04 09:34 .adobe 
drwxr-xr-x  2 1000 1000     336 2008-11-07 22:15 ALICE 
-rw-r--r--  1 1000 1000   19407 2008-11-04 08:45 ALICE INFO.odt 
drwx------  2 1000 1000      72 2008-11-04 09:34 .aptitude 
......
....
....
..... 
**-rw-------  1 1000 1000   21135 2009-03-29 15:10 .ICEauthority **
drwxr-xr-x  2 1000 1000      48 2009-01-23 07:31 .icons 
drwxr-xr-x 12 1000 1000    8440 2009-04-02 21:46 Images 
-rw-r--r--  1 1000 1000   37844 2008-11-15 02:28 installed-software 
.....
.....
.... 
[B]ubuntu@ubuntu:~$ ls -la /media/disk/tony.ICEauthority 
ls: cannot access /media/disk/tony.ICEauthority: No such file or directory 

and I haven't yet deleted.....bloody .ICE file
[/B]
[B]ubuntu@ubuntu:~$ ls -la /media/disk/tony.ICEauthority 

should be

[/B]**ubuntu@ubuntu:~$ ls -la /media/disk/tony/.ICEauthority **

---

### Post by taurus on 2009-04-11
> **stoppage said:**
> On an 8.04 livecd....
**ubuntu@ubuntu:~$ ls -la /media/disk/tony **
total 6971 
**[COLOR="Red"]dr-xr-xr-x 90 1000 1000    4312 2009-04-11 18:48 . [/COLOR]**
drwxr-xr-x  6 root root     128 2009-04-11 13:11 .. 
drwxr-----  3 1000 1000      80 2008-11-04 09:34 .adobe 
drwxr-xr-x  2 1000 1000     336 2008-11-07 22:15 ALICE 
-rw-r--r--  1 1000 1000   19407 2008-11-04 08:45 ALICE INFO.odt 
drwx------  2 1000 1000      72 2008-11-04 09:34 .aptitude 
......
....
....
..... 
**-rw-------  1 1000 1000   21135 2009-03-29 15:10 .ICEauthority **
drwxr-xr-x  2 1000 1000      48 2009-01-23 07:31 .icons 
drwxr-xr-x 12 1000 1000    8440 2009-04-02 21:46 Images 
-rw-r--r--  1 1000 1000   37844 2008-11-15 02:28 installed-software 
.....
.....
.... 
[B]ubuntu@ubuntu:~$ 

That is your problem right there.  You don't have write permission, w, to your own $HOME.

From Ubuntu LiveCD, run

```
sudo chmod 755 /media/disk/tony
ls -la /media/disk
```
Reboot and see what happens this time when you log in.

---

### Post by stoppage on 2009-04-12
Thanks, you were riht, permissions problem, I'm back in but with these (755) permissions I have no Email access and open office won't allow me to store new documents.Also all /home folders have this "locked" symbol, although they open o.k.
Heeeelp, Panic!

ubuntu@ubuntu:~$ sudo chmod 755 /media/disk/tony 
ubuntu@ubuntu:~$ ls -la /media/disk 
total 4 
drwxr-xr-x  6 root root  128 2009-04-11 13:11 . 
drwxr-xr-x  3 root root  100 2009-04-12 13:59 .. 
drwxr-xr-x 90 1000 1000 4280 2009-04-12 01:09 tony 
drwx------  4 root root   96 2009-04-11 13:11 .Trash-0

---

### Post by taurus on 2009-04-12
Are you still running off the LiveCD or from the harddrive now?

---

### Post by stoppage on 2009-04-12
I'm on the hard drive...I used GUI permisions tab to give r/w to all folders under /home, that's probably not the most reliable method but everything seems o.k.

---

### Post by stoppage on 2009-04-13
....and many thanks for the help and patience

---

