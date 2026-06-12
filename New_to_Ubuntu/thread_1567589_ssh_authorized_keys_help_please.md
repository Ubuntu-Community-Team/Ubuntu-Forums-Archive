---
title: "ssh authorized_keys help please"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-09-04
I followed the book ubuntu unleashed 2010 edition
made folder .ssh in /home/user
cd into .ssh
ssh-keygen t dsa
it makes id_dsa and id_dsa.pub
touch authorized_keys
cat id_dsa.pub >> authorized_keys
chmod 400 authorized_keys
copy authorized_keys and id_dsa.pub to flash drive to copy to other computers .ssh folder

my problem is that I cant seem to get all 3 computer to use authorized_keys instead of the password for the computer for example
lance@Therese:~$ ssh aceraspire@momacer -p 22
aceraspire@momacer's password: 

instead of 
lance@bermudezl:~$ ssh lance@therese -p 22
Linux Therese 2.6.32-24-generic-pae #41-Ubuntu SMP Thu Aug 19 02:43:57 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

Last login: Fri Sep  3 23:05:38 2010 from bermudezl.local
this one did what i wanted no password asked for

I have edited the sshd_config file on lance@therese and lance@bermudezl
PermitRootLogin yes to PermitRootLogin no
#PasswordAuthentication no to PasswordAuthentication no
I had to leave this as #PasswordAuthentication no on lance@momacer with out the change otherwise I would get 
lance@bermudezl: ssh aceraspire@momacer -p 22
Permission denied (publickey).

authorized_keys works going from lance@bermudezl to lance@therese
asked for password going form lance@bermudezl to aceraspire@momacer
asked for password goning from lance@therese to aceraspire@momacer
Permission denied (publickey) going from aceraspire@momacer to lance@bermudezl
Permission denied (publickey) going from aceraspire@momacer to lance@therese

lance@bermudezl:~$ ls -l .ssh
total 16
-r-------- 1 lance lance 1821 2010-08-31 20:13 authorized_keys
-rwxrwxrwx 1 lance lance  736 2010-03-03 20:28 id_dsa
-rwxrwxrwx 1 lance lance  605 2010-03-03 20:28 id_dsa.pub
-rw-r--r-- 1 lance lance 1534 2010-09-03 22:29 known_hosts

aceraspire@momacer:~$ ls -l .ssh
total 36
-r-------- 1 aceraspire aceraspire 1821 2010-08-31 20:13 authorized_keys
-rwxr-xr-x 1 aceraspire aceraspire  605 2010-03-03 20:28 id_dsa.pub
-rw-r--r-- 1 aceraspire aceraspire  884 2010-09-03 22:49 known_hosts

lance@Therese:~$ ls -l .ssh
total 12
-r-------- 1 lance lance  605 2010-03-05 10:30 authorized_keys
-rwxrwxrwx 1 lance lance  605 2010-03-03 20:28 id_dsa.pub
-rwxrwxrwx 1 lance lance 3978 2010-09-03 22:50 known_hosts

---

### Post by Elfy on 2010-09-04
duplicate - closed

---

