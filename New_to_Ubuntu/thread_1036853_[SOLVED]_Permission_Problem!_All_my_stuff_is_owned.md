---
title: "[SOLVED] Permission Problem! All my stuff is owned by someone called &amp;quot;1000&amp;quot;"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by jonpon on 2009-01-11
Hi
 Im having problems with permissions! 
It all started after I stupidly messed up my normal user account.
 So after saving my data to an external hard drive I deleted my account and as root created it new.
now I pasted my old desktop into the new account but all the item belong to a user called "1000"
Theres no user with this name.
How can I change the permissions of all my stuff back to me!
I tried creating an account called "1000" but numerical account names aren't  allowed.

---

### Post by spiderbatdad on 2009-01-11
I believe this thread will help: [http://ubuntuforums.org/showthread.php?p=4968235](http://ubuntuforums.org/showthread.php?p=4968235)

---

### Post by lazyart on 2009-01-11
1000 is the user id of the first user created in an Ubuntu system.

To change the permissions,```
chown -R ~ user:user
```
changing "user" to your username.

---

### Post by jonpon on 2009-01-11
> **lazyart said:**
> 1000 is the user id of the first user created in an Ubuntu system.

To change the permissions,```
chown -R ~ user:user
```
changing "user" to your username.


Thanks for replying
I tried it but still all the things on my desktop are locked and belong to someone else

---

### Post by lazyart on 2009-01-11
oops.. slip sudo in the front of that command.

---

### Post by jonpon on 2009-01-11
> **lazyart said:**
> oops.. slip sudo in the front of that command.

umm,
 with or without 'sudo' 
chown -R ~ jonpon:jonpon

nothing is happening
all the stuff on my decktop still belongs to '1000'

---

### Post by sisco311 on 2009-01-11
> **jonpon said:**
> umm,
 with or without 'sudo' 
chown -R ~ jonpon:jonpon

nothing is happening
all the stuff on my decktop still belongs to '1000'

~ = the current user's home folder
if you are logged in as root, ~ is /root
if you are logged in as jonpon, ~ is /home/jonpon

so try:
```
chown -R jonpon:jonpon /home/jonpon
```
assuming that jonpon is your login name and /home/jonpon is your home directory

---

### Post by newbee70 on 2009-01-11
> **jonpon said:**
> Hi
 Im having problems with permissions! 
It all started after I stupidly messed up my normal user account.
 So after saving my data to an external hard drive I deleted my account and as root created it new.
now I pasted my old desktop into the new account but all the item belong to a user called "1000"
Theres no user with this name.
How can I change the permissions of all my stuff back to me!
I tried creating an account called "1000" but numerical account names aren't  allowed.

Have you gone into System / Administration / Users:Groups

and tried to change it there?

---

### Post by handydan918 on 2009-01-11
First of all, help us to help you. Post some actual information. 
Try this;
 ```
cd /
```
Then:
```
ls -l /home
```

You might also just consider changing you present uid back to 1000, like so:

```
usermod -u UID <username>
``` Where <username> is your actual username.

---

### Post by jonpon on 2009-01-11
> **sisco311 said:**
> ~ = the current user's home folder
if you are logged in as root, ~ is /root
if you are logged in as jonpon, ~ is /home/jonpon

so try:
```
chown -R jonpon:jonpon /home/jonpon
```
assuming that jonpon is your login name and /home/jonpon is your home directory

I tried:
```
 sudo chown -R jonpon:jonpon /home/jonpon
```
it had no problem with the command but nothing changed:confused:

---

### Post by jonpon on 2009-01-11
[QUOTE=handydan918;6533558]First of all, help us to help you. Post some actual information. 
Try this;
 ```
cd /
```
Then:
```
ls -l /home
```

This is what I got
```


jonpon@jonpon-laptop:~$ cd /
jonpon@jonpon-laptop:/$ ls -l /home
total 8
drwxrwxrwx 23 jonpon ff     4096 2009-01-11 17:43 jonpon
drwx------ 30 ubuntu ubuntu 4096 2009-01-11 18:01 ubuntu
jonpon@jonpon-laptop:/$
``` 
Does that help any?

---

### Post by handydan918 on 2009-01-11
Try ```
usermod -g jonpon jonpon
```
and if that doesn't fix it (which it probably won't)
then do:
```
usermod -uo 1000 jonpon
```

I think....
If that errors on you it may be because of the "o" option. You could try it with just the "u".

---

### Post by jonpon on 2009-01-11
```
jonpon@jonpon-laptop:~$ sudo usermod -g jonpon jonpon
jonpon@jonpon-laptop:~$ sudo usermod -uo 1000 jonpon
jonpon@jonpon-laptop:~$ sudo usermod -u 1000 jonpon
jonpon@jonpon-laptop:~$ 

```
but no change

---

### Post by handydan918 on 2009-01-11
> **jonpon said:**
> ```
jonpon@jonpon-laptop:~$ sudo usermod -g jonpon jonpon
jonpon@jonpon-laptop:~$ sudo usermod -uo 1000 jonpon
jonpon@jonpon-laptop:~$ sudo usermod -u 1000 jonpon
jonpon@jonpon-laptop:~$ 

```
but no change

Let's see ```
cd /
```

```
ls -l
```

again

---

### Post by jonpon on 2009-01-11
> **handydan918 said:**
> Let's see ```
cd /
```

```
ls -l
```

again



This time it was more spectacular

```

jonpon@jonpon-laptop:~$ cd /
jonpon@jonpon-laptop:/$ ls -l
total 22632
drwxr-xr-x   2 root root       4096 2008-12-19 17:39 bin
drwxr-xr-x   3 root root       4096 2008-12-02 17:10 boot
lrwxrwxrwx   1 root root         11 2007-11-11 21:23 cdrom -> media/cdrom
drwxr-xr-x  12 root root      14460 2009-01-11 19:25 dev
drwxr-xr-x 128 root root      12288 2009-01-11 17:44 etc
-rw-r--r--   1 1000 jonpon 23042785 2007-11-21 20:06 GoogleEarthLinux.bin
drwxr-xr-x   4 root root       4096 2009-01-11 01:43 home
drwxr-xr-x   2 root root       4096 2007-04-18 05:15 initrd
lrwxrwxrwx   1 root root         33 2008-12-02 17:10 initrd.img -> boot/initrd.img-2.6.22-16-generic
lrwxrwxrwx   1 root root         33 2008-06-21 00:19 initrd.img.old -> boot/initrd.img-2.6.22-15-generic
drwxr-xr-x  16 root root      12288 2008-05-16 11:32 lib
drwx------   2 root root      16384 2007-11-11 21:23 lost+found
drwxr-xr-x   3 root root       4096 2009-01-11 17:43 media
drwxr-xr-x   2 root root       4096 2007-04-12 11:11 mnt
drwxr-xr-x   3 root root       4096 2008-12-21 00:19 opt
dr-xr-xr-x 136 root root          0 2009-01-11 17:42 proc
drwxr-xr-x  36 root root       4096 2009-01-11 13:40 root
drwxr-xr-x   2 root root       4096 2008-12-19 17:39 sbin
drwxr-xr-x   2 root root       4096 2007-04-18 05:15 srv
drwxr-xr-x  12 root root          0 2009-01-11 17:42 sys
drwxrwxrwx  14 root root      12288 2009-01-11 19:25 tmp
drwxr-xr-x  13 root root       4096 2008-06-15 11:16 usr
drwxr-xr-x  15 root root       4096 2007-04-18 05:28 var
lrwxrwxrwx   1 root root         30 2008-12-02 17:10 vmlinuz -> boot/vmlinuz-2.6.22-16-generic
lrwxrwxrwx   1 root root         30 2008-06-21 00:19 vmlinuz.old -> boot/vmlinuz-2.6.22-15-generic
jonpon@jonpon-laptop:/$ 
```

---

### Post by handydan918 on 2009-01-11
sorry. after the ```
cd /
```it should have been ```
ls -l /home 
```

Which is why you got such voluminous output...

---

### Post by jonpon on 2009-01-11
But I just tried
```
jonpon@jonpon-laptop:/$ cd /
jonpon@jonpon-laptop:/$ ls -l /[COLOR="Red"]home[/COLOR]
total 8
drwxrwxrwx 23 jonpon ff     4096 2009-01-11 17:43 jonpon
drwx------ 30 ubuntu ubuntu 4096 2009-01-11 18:01 ubuntu

```

no change there!

---

### Post by ajcham on 2009-01-11
> **handydan918 said:**
> sorry. after the ```
cd /
```it should have been ```
ls -l /home 
```

Which is why you got such voluminous output...
Also, **/home** is an absolute path, so there is no need to use **cd /** before **ls- l /home**

---

### Post by chex_m8 on 2009-01-11
can we also see the ouput of
ls -l /home/jonpon

---

### Post by ajcham on 2009-01-11
> **jonpon said:**
> But I just tried
```
jonpon@jonpon-laptop:/$ cd /
jonpon@jonpon-laptop:/$ ls -l /[COLOR="Red"]home[/COLOR]
total 8
drwxrwxrwx 23 jonpon ff     4096 2009-01-11 17:43 jonpon
drwx------ 30 ubuntu ubuntu 4096 2009-01-11 18:01 ubuntu

```

no change there!

(EDIT. Deleted silly question.)

Would you mind posting the output of ```
ls -l /home/jonpon
```
Obviously, if any of the lines in the output relate to personal files or folders (stuff you don't want us seeing the names of) feel free to erase those lines, but please post as much as you can.

---

### Post by jonpon on 2009-01-11
> **chex_m8 said:**
> can we also see the ouput of
ls -l /home/jonpon
```

jonpon@jonpon-laptop:~$ cd /
jonpon@jonpon-laptop:/$ ls -l /home/jonpon
total 28
drwxrwxrwx 18 jonpon root 4096 2009-01-11 14:02 Desktop
drwxr-xr-x  2 jonpon ff   4096 2009-01-11 01:45 Documents
lrwxrwxrwx  1 jonpon ff     26 2009-01-11 01:43 Examples -> /usr/share/example-content
drwxr-xr-x  2 jonpon ff   4096 2009-01-11 01:45 Music
drwxr-xr-x  2 jonpon ff   4096 2009-01-11 01:45 Pictures
drwxr-xr-x  2 jonpon ff   4096 2009-01-11 01:45 Public
drwxr-xr-x  2 jonpon ff   4096 2009-01-11 01:45 Templates
drwxr-xr-x  2 jonpon ff   4096 2009-01-11 01:45 Videos
jonpon@jonpon-laptop:/$ 
jonpon@jonpon-laptop:/$ 

```

---

### Post by ajcham on 2009-01-11
[s]Could you do another ls -l, but list the contents of one of your folders?  For instance if some of the files you are having issues with are in Documents:
ls -l /home/jonpon/Documents[/s]

EDIT: Actually never mind, I see from your OP that you put all the stuff on your Desktop.  Try:
```
ls -l /home/jonpon/Desktop
```

---

### Post by jonpon on 2009-01-11
> **ajcham said:**
> [s]Could you do another ls -l, but list the contents of one of your folders?  For instance if some of the files you are having issues with are in Documents:
ls -l /home/jonpon/Documents[/s]

EDIT: Actually never mind, I see from your OP that you put all the stuff on your Desktop.  Try:
```
ls -l /home/jonpon/Desktop
```

Now that was Exciting!```
jonpon@jonpon-laptop:/$ ls -l /home/jonpon/Desktop
total 23304
-rw-rw-r--  1 1000 jonpon 4154047 2008-06-23 23:24 02 Spur 2.mp3
-rw-rw-r--  1 1000 jonpon  618532 2008-12-04 23:01 148.pdf
drwxrwxrwx  3 1000 jonpon    4096 2008-12-08 23:25 37361512_files
-rw-rw-r--  1 1000 jonpon   60387 2008-12-08 23:25 37361512.html
drwxrwxrwx  3 1000 jonpon    4096 2008-12-08 23:34 43734532_files
-rw-rw-r--  1 1000 jonpon   64627 2008-12-08 23:34 43734532.html
drwxrwxrwx  2 1000 jonpon    4096 2008-11-18 17:09 a few pictures
drwxrwxrwx 12 1000 jonpon    4096 2008-09-11 10:36 Bauernhöfe
-rw-rw-r--  1 1000 jonpon  760744 2008-12-09 21:58 eMail_20081209_155653_84.PDF
drwxrwxrwx  2 1000 jonpon    4096 2008-12-21 00:36 Email stuff
-rw-rw-r--  1 1000 jonpon   49425 2008-11-03 23:47 FNBETRI_DOC.pdf
drwxrwxrwx  3 1000 jonpon    4096 2008-11-26 15:42 funnies
drwxrwxrwx  4 1000 jonpon    4096 2008-11-27 23:22 geld
-rw-rw----  1 1000 jonpon 9910945 2008-09-11 23:17 gypsy
-rw-rw-r--  1 1000 jonpon  873442 2008-12-04 21:24 Hauptantrag-Arbeitslosengeld-II.pdf
-rw-rw-r--  1 1000 jonpon   46080 2008-11-17 14:34 Hilfe_bei_Mutterschaft.doc
-rw-rw-r--  1 1000 jonpon  463520 2008-12-09 23:21 horsefair.pdf
drwxrwxrwx  3 1000 jonpon    4096 2008-12-06 10:37 JonPost
drwxrwxrwx  8 1000 jonpon    4096 2008-12-08 19:17 jre1.6.0_11
drwxrwxrwx  6 1000 jonpon    4096 2008-12-05 00:55 Karhausen Immobilien Auktionen Grundstücksauktion Auktion_files
-rw-rw-r--  1 1000 jonpon    3582 2008-12-05 00:55 Karhausen Immobilien Auktionen Grundstücksauktion Auktion.html
-rw-r--r--  1 1000 jonpon   10235 2009-01-05 19:18 kontoauszug_09.12.2008.pdf
lrwxrwxrwx  1 root root         4 2009-01-11 12:55 Link to tmp -> /tmp
drwxrwxrwx  5 1000 jonpon    4096 2008-12-18 09:52 malen
drwxrwxrwx 19 1000 jonpon    4096 2008-10-20 19:10 Our Stuff
-rw-rw-r--  1 1000 jonpon  357998 2008-10-20 22:19 P1000173.jpg
-rw-rw-r--  1 1000 jonpon  395434 2008-10-20 22:20 P1000174.jpg
-rw-rw-r--  1 1000 jonpon  197494 2008-10-20 22:20 P1000175.jpg
drwxrwxrwx  2 1000 jonpon    4096 2008-08-27 20:51 Peace Is Possible
drwxrwxrwx  2 1000 jonpon    4096 2008-11-17 00:02 pics
drwxrwxrwx  2 1000 jonpon    4096 2008-11-18 15:05 pics2
-rw-rw-r--  1 1000 jonpon  137216 2008-09-01 17:50 Tagebuch 08- 14.07- Rußheim nach Fulda.doc
drwxrwxrwx  2 1000 jonpon    4096 2008-05-30 17:42 tom lehrer
-rw-rw-r--  1 1000 jonpon       0 2007-07-12 23:39 ursule~
-rw-rw----  1 1000 jonpon 5578752 2008-12-05 01:39 Winter 2008.pdf.part
jonpon@jonpon-laptop:/$ 

```

---

### Post by ajcham on 2009-01-11
[s]sudo chown -R /home/jonpon/Desktop jonpon[/s]
Sorry that should be:
```
sudo chown -R jonpon /home/jonpon/Desktop
```

---

### Post by jonpon on 2009-01-11
> **ajcham said:**
> [s]sudo chown -R /home/jonpon/Desktop jonpon[/s]
Sorry that should be:
```
sudo chown -R jonpon /home/jonpon/Desktop
```

I tried both,
Nothing happened```
jonpon@jonpon-laptop:~$ sudo chown -R /home/jonpon/Desktop jonpon
jonpon@jonpon-laptop:~$ sudo chown -R jonpon /home/jonpon/Desktop
jonpon@jonpon-laptop:~$ ls -l /home/jonpon/Desktop
total 23304
-rw-rw-r--  1 1000 jonpon 4154047 2008-06-23 23:24 02 Spur 2.mp3
-rw-rw-r--  1 1000 jonpon  618532 2008-12-04 23:01 148.pdf
drwxrwxrwx  3 1000 jonpon    4096 2008-12-08 23:25 37361512_files
-rw-rw-r--  1 1000 jonpon   60387 2008-12-08 23:25 37361512.html
drwxrwxrwx  3 1000 jonpon    4096 2008-12-08 23:34 43734532_files
-rw-rw-r--  1 1000 jonpon   64627 2008-12-08 23:34 43734532.html
drwxrwxrwx  2 1000 jonpon    4096 2008-11-18 17:09 a few pictures
drwxrwxrwx 12 1000 jonpon    4096 2008-09-11 10:36 Bauernhöfe
-rw-rw-r--  1 1000 jonpon  760744 2008-12-09 21:58 eMail_20081209_155653_84.PDF
drwxrwxrwx  2 1000 jonpon    4096 2008-12-21 00:36 Email stuff
-rw-rw-r--  1 1000 jonpon   49425 2008-11-03 23:47 FNBETRI_DOC.pdf
drwxrwxrwx  3 1000 jonpon    4096 2008-11-26 15:42 funnies
drwxrwxrwx  4 1000 jonpon    4096 2008-11-27 23:22 geld
-rw-rw----  1 1000 jonpon 9910945 2008-09-11 23:17 gypsy
-rw-rw-r--  1 1000 jonpon  873442 2008-12-04 21:24 Hauptantrag-Arbeitslosengeld-II.pdf
-rw-rw-r--  1 1000 jonpon   46080 2008-11-17 14:34 Hilfe_bei_Mutterschaft.doc
-rw-rw-r--  1 1000 jonpon  463520 2008-12-09 23:21 horsefair.pdf
drwxrwxrwx  3 1000 jonpon    4096 2008-12-06 10:37 JonPost
drwxrwxrwx  8 1000 jonpon    4096 2008-12-08 19:17 jre1.6.0_11
drwxrwxrwx  6 1000 jonpon    4096 2008-12-05 00:55 Karhausen Immobilien Auktionen Grundstücksauktion Auktion_files
-rw-rw-r--  1 1000 jonpon    3582 2008-12-05 00:55 Karhausen Immobilien Auktionen Grundstücksauktion Auktion.html
-rw-r--r--  1 1000 jonpon   10235 2009-01-05 19:18 kontoauszug_09.12.2008.pdf
lrwxrwxrwx  1 root root         4 2009-01-11 12:55 Link to tmp -> /tmp
drwxrwxrwx  5 1000 jonpon    4096 2008-12-18 09:52 malen
drwxrwxrwx 19 1000 jonpon    4096 2008-10-20 19:10 Our Stuff
-rw-rw-r--  1 1000 jonpon  357998 2008-10-20 22:19 P1000173.jpg
-rw-rw-r--  1 1000 jonpon  395434 2008-10-20 22:20 P1000174.jpg
-rw-rw-r--  1 1000 jonpon  197494 2008-10-20 22:20 P1000175.jpg
drwxrwxrwx  2 1000 jonpon    4096 2008-08-27 20:51 Peace Is Possible
drwxrwxrwx  2 1000 jonpon    4096 2008-11-17 00:02 pics
drwxrwxrwx  2 1000 jonpon    4096 2008-11-18 15:05 pics2
-rw-rw-r--  1 1000 jonpon  137216 2008-09-01 17:50 Tagebuch 08- 14.07- Rußheim nach Fulda.doc
drwxrwxrwx  2 1000 jonpon    4096 2008-05-30 17:42 tom lehrer
-rw-rw-r--  1 1000 jonpon       0 2007-07-12 23:39 ursule~
-rw-rw----  1 1000 jonpon 5578752 2008-12-05 01:39 Winter 2008.pdf.part
jonpon@jonpon-laptop:~$ 
```

---

### Post by ajcham on 2009-01-11
Strange&#8230;

Try:
```
sudo su
chown -R jonpon:jonpon /home/jonpon/Desktop
exit
ls -l /home/jonpon/Desktop

```

---

### Post by jonpon on 2009-01-11
> **ajcham said:**
> Strange…

Try:
```
sudo su
chown -R jonpon:jonpon /home/jonpon/Desktop
exit
ls -l /home/jonpon/Desktop

```

after the ```
chown -R jonpon:jonpon /home/jonpon/Desktop
```
I got a long list of bad news```
-dateien/ruesselsheim2.jpg': Operation not permitted
chown: changing ownership of `/home/jonpon/Desktop/Our Stuff/getrappel/aktuelles-dateien/08-0405-sandweier.jpg': Operation not permitted
chown: changing ownership of `/home/jonpon/Desktop/Our Stuff/getrappel/aktuelles-dateien/ruesselsheim3.jpg': Operation not permitted
chown: changing ownership of `/home/jonpon/Desktop/Our Stuff/getrappel/aktuelles-dateien/1711-offnadingen.jpg': Operation not permitted
chown: changing ownership of `/home/jonpon/Desktop/Our Stuff/getrappel/aktuelles-dateien/aktuelles.htm': Operation not permitted
chown: changing ownership of `/home/jonpon/Desktop/Our Stuff/getrappel/aktuelles-dateien/08-0806-storchenhof.xcf': Operation not permitted
chown: changing ownership of `/home/jonpon/Desktop/Our Stuff/getrappel/aktuelles-dateien/kirsche2.jpg': Operation not permitted.....

```

---

### Post by ajcham on 2009-01-11
Did **sudo su** work OK?  This should have changed the prompt from **jonpon@jonpon-laptop:~$** to **root@jonpon-laptop:~$**

If it did not, then it seems sudo is not working.  This is quite probable, given that you are not using the first user account (which is the only one given sudo rights by default).  I'm a little puzzled though, because there is no error message saying this (it should say: jonpon is not in the sudoers file).

It should be possible to get to a root prompt and add your username to the admin group, but I'm not 100% sure how this is done.  I'll try to find out, but someone else may be able to provide you with the answer before me.

EDIT:
Okay, reboot the machine and from the GRUB menu select recovery mode.  You should get an option to 'drop to root shell' - select this.

At the prompt enter:
```
adduser jonpon admin
chown -R jonpon:jonpon /home/jonpon/Desktop
```

Now your files should be accessible, and we've added you back onto the sudoers list for when you next need it.

---

### Post by jonpon on 2009-01-11
> **ajcham said:**
> Did **sudo su** work OK?  This should have changed the prompt from **jonpon@jonpon-laptop:~$** to **root@jonpon-laptop:~$**

If it did not, then it seems sudo is not working.  This is quite probable, given that you are not using the first user account (which is the only one given sudo rights by default).  I'm a little puzzled though, because there is no error message saying this (it should say: jonpon is not in the sudoers file).

It should be possible to get to a root prompt and add your username to the admin group, but I'm not 100% sure how this is done.  I'll try to find out, but someone else may be able to provide you with the answer before me.

I logged on as root and gave jonpon the admin group rights and changed the main group jonpon fromm ff to root

this looked more promising
```
jonpon@jonpon-laptop:~$ sudo su
[sudo] password for jonpon:
jonpon@jonpon-laptop:~$ sudo su
root@jonpon-laptop:/home/jonpon# chown -R jonpon:jonpon /home/jonpon/Desktop
root@jonpon-laptop:/home/jonpon# exit
exit
jonpon@jonpon-laptop:~$ ls -l /home/jonpon/Desktop
total 23304
-rw-rw-r--  1 jonpon jonpon 4154047 2008-06-23 23:24 02 Spur 2.mp3
-rw-rw-r--  1 jonpon jonpon  618532 2008-12-04 23:01 148.pdf
drwxrwxrwx  3 jonpon jonpon    4096 2008-12-08 23:25 37361512_files
-rw-rw-r--  1 jonpon jonpon   60387 2008-12-08 23:25 37361512.html
drwxrwxrwx  3 jonpon jonpon    4096 2008-12-08 23:34 43734532_files
-rw-rw-r--  1 jonpon jonpon   64627 2008-12-08 23:34 43734532.html
drwxrwxrwx  2 jonpon jonpon    4096 2008-11-18 17:09 a few pictures
drwxrwxrwx 12 jonpon jonpon    4096 2008-09-11 10:36 Bauernhöfe
-rw-rw-r--  1 jonpon jonpon  760744 2008-12-09 21:58 eMail_20081209_155653_84.PDF
drwxrwxrwx  2 jonpon jonpon    4096 2008-12-21 00:36 Email stuff
-rw-rw-r--  1 jonpon jonpon   49425 2008-11-03 23:47 FNBETRI_DOC.pdf
drwxrwxrwx  3 jonpon jonpon    4096 2008-11-26 15:42 funnies
drwxrwxrwx  4 jonpon jonpon    4096 2008-11-27 23:22 geld
-rw-rw----  1 jonpon jonpon 9910945 2008-09-11 23:17 gypsy
-rw-rw-r--  1 jonpon jonpon  873442 2008-12-04 21:24 Hauptantrag-Arbeitslosengeld-II.pdf
-rw-rw-r--  1 jonpon jonpon   46080 2008-11-17 14:34 Hilfe_bei_Mutterschaft.doc
-rw-rw-r--  1 jonpon jonpon  463520 2008-12-09 23:21 horsefair.pdf
drwxrwxrwx  3 jonpon jonpon    4096 2008-12-06 10:37 JonPost
drwxrwxrwx  8 jonpon jonpon    4096 2008-12-08 19:17 jre1.6.0_11
drwxrwxrwx  6 jonpon jonpon    4096 2008-12-05 00:55 Karhausen Immobilien Auktionen Grundstücksauktion Auktion_files
-rw-rw-r--  1 jonpon jonpon    3582 2008-12-05 00:55 Karhausen Immobilien Auktionen Grundstücksauktion Auktion.html
-rw-r--r--  1 jonpon jonpon   10235 2009-01-05 19:18 kontoauszug_09.12.2008.pdf
lrwxrwxrwx  1 jonpon jonpon       4 2009-01-11 12:55 Link to tmp -> /tmp
drwxrwxrwx  5 jonpon jonpon    4096 2008-12-18 09:52 malen
drwxrwxrwx 19 jonpon jonpon    4096 2008-10-20 19:10 Our Stuff
-rw-rw-r--  1 jonpon jonpon  357998 2008-10-20 22:19 P1000173.jpg
-rw-rw-r--  1 jonpon jonpon  395434 2008-10-20 22:20 P1000174.jpg
-rw-rw-r--  1 jonpon jonpon  197494 2008-10-20 22:20 P1000175.jpg
drwxrwxrwx  2 jonpon jonpon    4096 2008-08-27 20:51 Peace Is Possible
drwxrwxrwx  2 jonpon jonpon    4096 2008-11-17 00:02 pics
drwxrwxrwx  2 jonpon jonpon    4096 2008-11-18 15:05 pics2
-rw-rw-r--  1 jonpon jonpon  137216 2008-09-01 17:50 Tagebuch 08- 14.07- Rußheim nach Fulda.doc
drwxrwxrwx  2 jonpon jonpon    4096 2008-05-30 17:42 tom lehrer
-rw-rw-r--  1 jonpon jonpon       0 2007-07-12 23:39 ursule~
-rw-rw----  1 jonpon jonpon 5578752 2008-12-05 01:39 Winter 2008.pdf.part
jonpon@jonpon-laptop:~$ 

``` But STILL all the stuff on my Desktop is owned by '1000'

NO WAIT,
ALL the folders have lost the little "x" in the corner but when I look who owns them it's still '1000'

---

### Post by ajcham on 2009-01-11
> **jonpon said:**
> But STILL all the stuff on my Desktop is owned by '1000'

I'm baffled - ***ls -l*** is clearly showing that you are the owner of the files. Lacking a better solution, may I suggest Ctrl+Alt+Backspace and logging in again?

---

### Post by jonpon on 2009-01-11
IT WORKED!!!!

Ive just changed the ownership graphicaly from my Desktop folder. This wasn't possible before
Thank you so much for your help

---

### Post by ajcham on 2009-01-11
Well I'm glad you can get your files again, but I'm still a little confused by some of the steps we went through.

Mostly, I can't figure out why sudo wasn't returning an error before you added yourself to the admin group. It seems strange that it would just sit silently, rather than telling you why it won't run the command.

---

### Post by jonpon on 2009-01-11
Yes, Strange that. 
Interesting to know the 'sudo su' changes to 'root@---' I'll try and us that in the furture
Thanks again
Jonpon

---

### Post by ajcham on 2009-01-11
> **jonpon said:**
> Yes, Strange that. 
Interesting to know the 'sudo su' changes to 'root@---' I'll try and us that in the furture


I wouldn't recommend that - sudo is a much better way of working, really. It was only because it wasn't working that I suggested trying 'sudo su' - on the off-chance that you'd have more luck, and if not allow us to see for certain that sudo wasn't doing its job.

---

