---
title: "editing program does not have permissions to edit /etc/sudoers"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by hmmchacha on 2009-07-05
Hi, I have Ubuntu 9.04 and Windows Vista on dual boot - installed about 3 weeks ago, and I'm a total beginner with Linux so please keep it simple :)

I installed Firestarter but wanted to have it starting up automatically on start-up. It currently only works when selected from the internet panel and the Username and Password are input.

I used the text editer "sudo gedit /etc/sudoers", but according to the /etc/sudoers that text editor DOES NOT have the permissions to edit those files, which remained Read-only.

The intention is to add a line to the /etc/sudoers file:

[COLOR=#bd3030]username[/COLOR]   ALL= NOPASSWD: /usr/bin/firestarter

It bothers me that the file cannot be edited. Is it a bug or is there another way?

---

### Post by helpineed on 2009-07-05
The sudoers file must be edited with the visudo command (I don't know why). Use:
```
sudo visudo
```
Visudo works is vi and you might have to look up how to use it (vi is a bit confusing at first glance.)

---

### Post by 3rdalbum on 2009-07-05
> **helpineed said:**
> The sudoers file must be edited with the visudo command (I don't know why). Use:
```
sudo visudo
```
Visudo works is vi and you might have to look up how to use it (vi is a bit confusing at first glance.)

If you use Visudo, it will check the syntax of the file before saving its contents. This prevents you from accidentally breaking your system.

---

### Post by CatKiller on 2009-07-05
Hold up.

> **hmmchacha said:**
> I installed Firestarter but wanted to have it starting up automatically on start-up. It currently only works when selected from the internet panel and the Username and Password are input.

You don't need Firestarter running all the time. Firestarter is a configuration tool for IPTables, which is already running all the time.

> I used the text editer "sudo gedit /etc/sudoers", but according to the /etc/sudoers that text editor DOES NOT have the permissions to edit those files, which remained Read-only.It's by design that you have to edit the sudoers file in a particular way. But you shouldn't be running gedit with sudo. You should use [gksudo for graphical applications]("http://www.psychocats.net/ubuntu/graphicalsudo").

---

### Post by 3rdalbum on 2009-07-05
> **CatKiller said:**
> You don't need Firestarter running all the time. Firestarter is a configuration tool for IPTables, which is already running all the time.

Yes, that's true; I'm sorry I didn't properly read that part of the post before giving my advice. Firestarter only sets up the firewall rules - the actual firewall is inside the kernel and therefore runs all the time.

If you don't have any server software installed on Ubuntu you don't even need a firewall.

---

### Post by hmmchacha on 2009-07-10
Thanks for the gksudo and vi suggestions.

My terminal is not starting the editing programs so this is getting more complex:

hmm@hmm-laptopUbuntu:~$ ls -l /etc/sudoers
-rw-r----- 1 root root 557 2009-06-10 19:28 /etc/sudoers
hmm@hmm-laptopUbuntu:~$ gksudo gedit /etc/sudoers
hmm@hmm-laptopUbuntu:~$ sudo visudo /etc/sudoers
sudo: /etc/sudoers is mode 0640, should be 0440

apparently this is a weird problem. Can you suggest anything to help start the editing program?

---

### Post by SuperSonic4 on 2009-07-10
It looks like the ownership of sudo has changed, probably because of editing.

You may be able to boot into recovery mode and type in ```
chmod 0440 /etc/sudoers
``` but please wait for someone else to verify/prove wrong this for I'm far from sure

---

### Post by Mornedhel on 2009-07-10
> **SuperSonic4 said:**
> It looks like the ownership of sudo has changed, probably because of editing.

You may be able to boot into recovery mode and type in ```
chown 0440 /etc/sudoers
``` but please wait for someone else to verify/prove wrong this for I'm far from sure

chmod, not chown, for starters.

---

### Post by hmmchacha on 2009-07-10
i've tried chown and chmod (this is a more complete version of what's in the terminal)

hmm@hmm-laptopUbuntu:~$  ls -l /etc/sudoers
-r--r----- 1 root root 557 2009-06-10 19:28 /etc/sudoers
hmm@hmm-laptopUbuntu:~$ sudo chmod u+w /etc/sudoers
[sudo] password for hmm: 
hmm@hmm-laptopUbuntu:~$ sudo gedit /etc/sudoers
sudo: /etc/sudoers is mode 0640, should be 0440
hmm@hmm-laptopUbuntu:~$ sudo chmod ug+rw /etc/sudoers
sudo: /etc/sudoers is mode 0640, should be 0440
hmm@hmm-laptopUbuntu:~$ sudo chmod ug+rwx /etc/sudoers
sudo: /etc/sudoers is mode 0640, should be 0440
hmm@hmm-laptopUbuntu:~$ ls -l /etc/sudoers
-rw-r----- 1 root root 557 2009-06-10 19:28 /etc/sudoers
hmm@hmm-laptopUbuntu:~$ gksudo gedit /etc/sudoers
hmm@hmm-laptopUbuntu:~$ sudo visudo /etc/sudoers
sudo: /etc/sudoers is mode 0640, should be 0440

---

### Post by CatKiller on 2009-07-10
Really. Stop messing around with the permissions on your sudoers file. It won't work. It's by design.

If you absolutely **have** to edit that file by hand, use **sudo visudo**. Everything else will fail.

Otherwise, use the graphical tools.

---

### Post by juanoleso on 2009-07-10
> **CatKiller said:**
> Really. Stop messing around with the permissions on your sudoers file.

I like being able to mess with everything, a plus to linux!  =-D

but,

> **CatKiller said:**
> It won't work. It's by design.

He is quite right, from what i've read it is hard coded.

---

### Post by niteshifter on 2009-07-10
Hi,

For a file with permissions mask of 0640:
chmod ug+rw  is the same as chmod 0660 - won't work for /etc/sudoers
chmod ug+rwx is the same as chmod 0770 - won't work       "

Use this:
```
sudo chmod 0440 /etc/sudoers
```

or boot into recovery mode and use
```
chmod 0440 /etc/sudoers
```

For further illumination on permissions mode number vs symbolic ...
For a file with permissions mask of 0644:
chmod ug+rw  is the same as chmod 0664
chmod ug+rwx is the same as chmod 0774

---

### Post by Mornedhel on 2009-07-10
> **niteshifter said:**
> For further illumination on permissions mode number vs symbolic ...
For a file with permissions mask of 0644:
chmod ug+rw  is the same as chmod 0664
chmod ug+rwx is the same as chmod 0774

Whoa whoa whoa, you're simplifying. chmod ug<whatever> doesn't set o's permissions to read-only as chmod 0664 and chmod 0774 do.

Maybe I'm just being pedantic today, though.

---

### Post by niteshifter on 2009-07-11
> **Mornedhel said:**
> Whoa whoa whoa, you're simplifying. chmod ug<whatever> doesn't set o's permissions to read-only as chmod 0664 and chmod 0774 do.

Maybe I'm just being pedantic today, though.

Indeed it does not set o's - it doesn't touch them at all:
```

touch testfile.txt
chmod 0644 testfile.txt  # touch should have made 0644, but make sure
ls -al
total 16
drwxr-xr-x   2 dlk dlk  4096 2009-07-11 02:41 .
drwxr-xr-x 135 dlk dlk 12288 2009-07-11 02:37 ..
-rw-r--**r--**   1 dlk dlk     0 2009-07-11 02:41 testfile.txt

chmod [COLOR="Red"]ug+rw[/COLOR] testfile.txt
ls -al
total 16
drwxr-xr-x   2 dlk dlk  4096 2009-07-11 02:41 .
drwxr-xr-x 135 dlk dlk 12288 2009-07-11 02:37 ..
-[COLOR="Red"]rw-rw-[/COLOR]**r--**   1 dlk dlk     0 2009-07-11 02:41 testfile.txt

chmod [COLOR="Red"]ug+rwx[/COLOR] testfile.txt
ls -al
total 16
drwxr-xr-x   2 dlk dlk  4096 2009-07-11 02:41 .
drwxr-xr-x 135 dlk dlk 12288 2009-07-11 02:37 ..
-[COLOR="Red"]rwxrwx[/COLOR]**r--**   1 dlk dlk     0 2009-07-11 02:41 testfile.txt

```

---

