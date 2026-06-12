---
title: "permission denied (publickey)"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-08-29
want key based so i dont have to put in the password of user or passphrase 

I have edited the ssh_config
   from #Protocol 2, 1 to Protocol 2 with out the #

I have edited the sshd_config
PermitRootLogin yes to PermitRootLogin no
#PasswordAuthentication no to PasswordAuthentication no

i have the same file changes on the other 2 computers. I have 3 computer all together 1 xbuntu and the other 2 are ubuntu. All have the authorized_keys with chmod 400 persmissons id_dsa.pub and known_host file
one has id_dsa and it will not talk to the other computer either

aceraspire@momacer:~$ ls -l .ssh
total 16
-r-------- 1 aceraspire aceraspire 605 2010-03-25 11:21 authorized_keys
-rwxrwxrwx 1 aceraspire aceraspire 736 2010-03-03 20:28 id_dsa
-rwxrwxrwx 1 aceraspire aceraspire 605 2010-03-03 20:28 id_dsa.pub
-rw-r--r-- 1 aceraspire aceraspire 1326 2010-08-29 14:12 known_hosts

attached is the ssh -vvv outuput

---

### Post by cariboo on 2010-08-29
Just to make sure all i's are dotted and the tee's are crossed:

[list=1]
[*] ssh-keygen -t rsa
[*] ssh-copy-id user@server
[/list]

for step one just press enter when asked for a passphrase, and then before you disble password login, type:

```
ssh user@server
```

You will be asked for your password, then you will be asked to login again. If everything works, then you can disable login password

---

### Post by lance bermudez on 2010-08-29
hey thinks for the help but I'm having trouble following you so here is what I did. I followed the book ubuntu unleashed 2010 edition 
made folder .ssh in /home/user
cd into .ssh
ssh-keygen t dsa
it makes id_dsa and id_dsa.pub
touch authorized_keys
cat id_dsa.pub >> authorized_keys
chmod 400 authorized_keys
copy authorized_keys and id_dsa.pub to flash to copy to other computers
on the other computer made sure they had the same file permission as on this one

---

### Post by lance bermudez on 2010-08-31
I have one computer that can talk to the other 2 computer but the other 2 can not talk to it. please someone help I want all 3 to be able to talk to each other.

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

### Post by jerome1232 on 2010-09-04
Do all of these machines have gui's?

It might just be easier to use Ubuntu's gui for setting up ssh keys.

So make sure password auth is enabled on all machines involved.


On client computer click Applications -> Accessories -> Passwords and Encryption keys.  Click File -> New, select Secure Shell Key, enter a description for your key it doesn't really matter what you put in there, then click create and setup, don't enter a password just click ok, it will ask you for the passphrase for the server, so enter the password you would normally use to login to the machine you are connecting to.

Rinse and repeat on each client.

Should work now. Test to make sure, then disable password auth on each server.

(I remember why I always give instructions via commandline now, gui's suck to walk through)

---

### Post by lance bermudez on 2010-09-04
yes they all have gui 2 are ubuntu and one is xubuntu. will this mess what what i have working already? Do i need a differet key for each machine or can they all use the same one?

---

### Post by apmcd47 on 2010-09-04
Try:```
cd
chmod 700 .ssh
cd .ssh
chmod 600 *
```

Your private key is wide open, and I bet your .ssh folder is too! ssh doesn't like that.

Andrew

---

### Post by jerome1232 on 2010-09-05
> **lance bermudez said:**
> yes they all have gui 2 are ubuntu and one is xubuntu. will this mess what what i have working already? Do i need a differet key for each machine or can they all use the same one?

They can all use the same one although that's technically insecure (a person gets a hold of your one key they have access to every machine)

---

### Post by lance bermudez on 2010-09-07
ok I have 
lance@Therese:~$ ls -l .ssh
total 12
-r-------- 1 lance lance  605 2010-03-05 10:30 authorized_keys
-rw------- 1 lance lance  605 2010-03-03 20:28 id_dsa.pub
-rw------- 1 lance lance 3978 2010-09-03 22:50 known_hosts
on all 3 computers

have also tried
lance@Therese:~$ ls -l .ssh
total 12
-rw------- 1 lance lance  605 2010-03-05 10:30 authorized_keys
-rw------- 1 lance lance  605 2010-03-03 20:28 id_dsa.pub
-rw------- 1 lance lance 3978 2010-09-03 22:50 known_hosts
on all 3 computer

lance@Therese:~$ ssh lance@10.0.0.2 -p 22
Permission denied (publickey).
aceraspire@momacer:~$ ssh lance@10.0.0.2 -p 22 
Permission denied (publickey).

lance@bermudezl can talk to lance@Therese
lance@bermudez can talk to aceraspire@momacer
lance@Therese no talk to lance@bermudezl
aceraspire@momacer no talk to lance@bermudezl
also no talk between lance@Therese and aceraspire@momacer

none of the computer will forward x either and i have the sshd_config set to allow x forwarding.

---

### Post by apmcd47 on 2010-09-07
> **lance bermudez said:**
> 

none of the computer will forward x either and i have the sshd_config set to allow x forwarding.

For X forwarding create a file ~/.ssh/config as follows:
```
Host *
     ForwardX11 yes
```
although you may prefer
```
     ForwardX11Trusted yes
```
I'll have to get back to you on the public key problem.

Andrew

---

### Post by apmcd47 on 2010-09-07
Okay, I haven't been paying too much attention to the details, but you seem to have the following machines:
[LIST]
[*]bermudezl
[*]therese
[*]10.0.0.2
[/LIST]

On one of these machines you have created these files:
[LIST]
[*]id_dsa
[*]id_dsa.pub
[*]authorized_keys
[/LIST]
and copied 
[LIST]
[*]id_dsa.pub
[*]authorized_keys
[/LIST]
over to the other two machines. Correct? You can ssh from the first machine to the other two using the key but not from the other two to any of the three machines. Correct?

You need a private key on each machine, and it is not obvious to me that you have done that. It has been stated by others in this thread that you should use a different private key for each machine and I agree to a point. But for the time being, copy the private key from one machine to another and see if it works for that other machine. What you do after that (if it works) is up to you.

Andrew

---

