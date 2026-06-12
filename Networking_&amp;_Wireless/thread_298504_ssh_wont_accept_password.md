---
title: "ssh wont accept password"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by craz on 2006-11-12
I am running ubuntu edgy.  I have the newest openssh-client and openssh-server packages freshly installed.  When I try to test in the terminal using ```
ssh localhost
```I get "Permission denied, please try again" after I input the correct password.  After the three tries I get Permission denied (publickey,password).  I know there is a problem with the publickey and password, and I need both to work.  For some reason shh wont recognize my password.  I have researched this for hours and nothing is working.  What should I do?  Thanks for any help.

---

### Post by FrodoB on 2006-11-12
Open a terminal and using gedit modify the ssh_config file:

$ sudo /usr/bin/gedit /etc/ssh/ssh_config

Find the line that says:

#   PasswordAuthentication yes

and remove the # sign making it:

PasswordAuthentication yes

Save it and now it should take your password only. Yes this is still secure.

Restart ssh:

$ sudo /etc/init.d/ssh restart

---

### Post by craz on 2006-11-13
Thanks so much for the input. :)   I uncommented that line, which seems like it should work, but I am still getting the same exact error.  I dont know what it could be, but it is starting to bother me. :mad: 
Does anybody know what else I could try?

---

### Post by psycho78 on 2006-11-13
did you  sudo /etc/init.d/ssh restart
after changing the config file?

---

### Post by craz on 2006-11-13
Yes, I did.

---

### Post by craz on 2006-11-13
What else could I try?

---

### Post by FrodoB on 2006-11-13
This is the whole process on a freshly installed Ubuntu machine from failing because there is no server installed until it just works.

1. Try on a fresh install, it fails like this:

user@ubuntu:~$ ssh localhost
ssh: connect to host localhost port 22: Connection refused


2. Install openssh-server

user@ubuntu:~$ sudo apt-get install openssh-server


3. Edit /etc/ssh/ssh_config

user@ubuntu:~$ sudo /usr/bin/gedit /etc/ssh/ssh_config


Find the line that says:

# PasswordAuthentication yes

and remove the # sign making it:

PasswordAuthentication yes


4. Restart the server:

user@ubuntu:~$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server...                             [ ok ] 

5. ssh to local machine:

user@ubuntu:~$ ssh localhost

The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is 4e:79:68:d9:76:e7:da:38:c4:2c:fb:d8:1a:7b:6f:9d.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.

Say yes to accept the key.

6. Enter your password:

user@localhost's password: 
Linux ubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by

7. You are in.

---

### Post by craz on 2006-11-13
Tried fresh install like you said.  It did the RSA key fingerprint and i said yes.  Once it got to the password, same deal.  I have no idea why it is being such a pain.  :confused:

---

### Post by FrodoB on 2006-11-13
You said that you installed the client, this was not necessary and you did not know. Maybe that caused a problem with your ssh keys? I don't know, and I don't remember how to regenerate keys at the moment. May not be the issue anyway.

---

### Post by Wicca on 2006-11-14
Just a wild guess:

$ sudo gedit /etc/ssh/sshd_config (mind the d)
Find # Authentication

Make sure beneath that is:

AllowUsers *your-name-here*
RSAAuthentication yes
PubkeyAuthentication yes

restart the deamon:
$ sudo /etc/init.d/ssh restart

Good luck.

---

### Post by craz on 2006-11-14
Oh my god Wicca your a lifesaver!  It works great now!  The problem was that the AllowUsers line was not there.  I owe you one :D

---

### Post by Wicca on 2006-11-15
you're welcome, glad I could help.

---

