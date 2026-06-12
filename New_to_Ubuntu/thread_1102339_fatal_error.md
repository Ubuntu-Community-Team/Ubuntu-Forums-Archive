---
title: "fatal error"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by teen eagle on 2009-03-21
when i was  trying to add new user some thing wrong had happened, i made 

the new user the administrator,then i wanted to delete the new user,So i 

opened (Users and Groups),but i didn't find any user in users list even 

the (root),so i tried to make it by (Terminal) but no any command had worked
```
sudo: no passwd entry for root!

```

and i couldn't logged in as root,SO i want to delete the new user and return to the previous status cause now their is two users the first doesn't need to write sudo and the other doesn't accept any command on terminal

---

### Post by llamabr on 2009-03-21
I couldn't follow your little story.

What, exactly, did you type into the terminal?

---

### Post by teen eagle on 2009-03-21
any thing , after making the new user the first user started to write this
```
eagle@pc:~$ sudo apt-cache search blender
sudo: no passwd entry for root!

```
 when i write any command begging with sudo

---

### Post by teen eagle on 2009-03-21
see also when i write any command with out sudo
```
eagle@pc:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
eagle@pc:~$ 

```

---

### Post by teen eagle on 2009-03-21
please any body help me

---

### Post by teen eagle on 2009-03-21
up up up

---

### Post by blackgr on 2009-03-21
do this
cat /etc/passwd | grep root 
and give me the output

---

### Post by teen eagle on 2009-03-22
first thank you for trying helping me 
second cat cat /etc/passwd | grep root nothing happend
thrd when i restarted the pc a strange screen showed to me and that was written in it 

the GDM user "gdm" doesn't exist , please correct GDM configuration and restart GDM

please help me now i am talking from other pc by windos and every body in my home is joking on me because i was speaking about ubuntu for weeks and now i cant enter to it

---

### Post by kpatz on 2009-03-22
Type 'ls -l /etc/passwd*' and tell us what you see.

There may be a backup of the password file you can restore (on my system there's a file called "passwd-".  You will have to boot into recovery mode or from a Live CD to gain root access.

---

### Post by teen eagle on 2009-03-22
```
ls -l /etc/passwd*
syntax eror near unexpected token `|'
```

---

### Post by teen eagle on 2009-03-22
up up up

---

### Post by presence1960 on 2009-03-22
> please help me now i am talking from other pc by windos and every body in my home is joking on me because i was speaking about ubuntu for weeks and now i cant enter to it

Hopefully lesson learned. Use Linux and let others ask you about it, or if it comes up in conversation. No one likes a reformer or evangelist.

---

### Post by Volt9000 on 2009-03-22
> **teen eagle said:**
> ```
ls -l /etc/passwd*
syntax eror near unexpected token `|'
```

Er, you sure that's exactly what you typed? It's complaining about a pipe when there is none in that command...

After the ls that's a hyphen and a lower-case L, not a bar.

Copy and paste the command directly into Terminal:

```

ls -l /etc/passwd*

```

---

### Post by presence1960 on 2009-03-22
follow this tutorial to put the original user back in the admin group.

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by kpatz on 2009-03-23
> **teen eagle said:**
> ```
ls -l /etc/passwd*
syntax eror near unexpected token `|'
```Is that the actual message you saw (did you copy/paste it into your post, or did you type it yourself, as it has a typo...)

Try:
```
echo /etc/passwd*
```

Also try

```
ls -l /etc | grep passwd
```

A bogus file with a pipe character in /etc could be getting interpreted as bad syntax by the shell.

---

