---
title: "How is it that I cannot gain root access?"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by moebob24 on 2009-05-26
So I am the only user of my Linux box and in the history of my PC I have only assigned 1 and only 1 password to anything for this computer. 

Yet when I try to get root access, the password is rejected. 

```

user@Ubuntu:~$ su
Password: (I type it in)
su: Authentication failure

```

What is going on here??

---

### Post by Mornedhel on 2009-05-26
The root account is disabled by default in Ubuntu.

To get a root shell, please use sudo -i.

Activating the root account is possible but not recommended.

Edit: Rephrasing to better suit your question : you're not root. root is a separate account with a (nonexistent) separate password.

---

### Post by moebob24 on 2009-05-26
> **Mornedhel said:**
> The root account is disabled by default in Ubuntu.

To get a root shell, please use sudo -i.

Activating the root account is possible but not recommended.

Edit: Rephrasing to better suit your question : you're not root. root is a separate account with a (nonexistent) separate password.

I know what root is but I have been able to access it in previous version of Ubuntu. But I guess I still can, thanks for the help though.

---

### Post by Jusdogmatik on 2009-05-26
have you tried 

```
sudo su

```When I do this it gives me root acsess. See:

```
justin@justin-desktop:~$ sudo su 
[sudo] password for justin: 
root@justin-desktop:/home/justin# 


```Just a note but passwords are case sensitive. That just might be your problem.

---

### Post by moebob24 on 2009-05-26
> **Jusdogmatik said:**
> have you tried 

```
sudo su

```When I do this it gives me root acsess. See:

```
justin@justin-desktop:~$ sudo su 
[sudo] password for justin: 
root@justin-desktop:/home/justin# 


```Just a note but passwords are case sensitive. That just might be your problem.

Oooo another way. What is the difference between the two. When I enter them into the term. they each print different things

```

sudo -i 
root@linux:~#

```
and
```

sudo su
root@linux:/home/me#

```

Are these different locations. The second one put me into my home folder while the first one put me into the file system folder called "root".

---

### Post by Jusdogmatik on 2009-05-26
Oh. Well I learned something new today.

---

### Post by LowSky on 2009-05-26
personally I just use sudo or sudo -i

sudo -i is great if i have a bunch of stuf to do and dont want to be constanlty typing sudo

---

### Post by mcduck on 2009-05-26
> **moebob24 said:**
> Oooo another way. What is the difference between the two. When I enter them into the term. they each print different things

```

sudo -i 
root@linux:~#

```
and
```

sudo su
root@linux:/home/me#

```

Are these different locations. The second one put me into my home folder while the first one put me into the file system folder called "root".
"sudo -i" loads root's environment variables correctly, acting exactly as if you had logged in as root (easily noticeable from the command moving you into root's home directory).

"sudo su" doesn't do that, so you end running as root but with your normal user's environment.

You should use "sudo -i".

In the same way "gksudo" loads environment variables correctly for graphical applications, while "sudo" dosn't. So always use "gksudo" with graphical applications.

(and the reason why "su" doesn't work is because it asks for the *target user's* password, so in this case you'd need to give root password. Which you don't have..)

---

### Post by clonne4crw on 2009-05-26
I'm confused... :?

I just do a $ sudo -i 
and stay root the session. Typing 'sudo' is just too much for me to remember. :D

---

