---
title: "[SOLVED] Sort of stupid question on sudo authentication"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by ooobooontooo on 2009-01-06
Hi,

How come when sudo prompts for a password, it is the password of the current user rather than the root? I mean if you want to do su, you need the password of root right? I thought sudo as a one time action using the root status...how come it only asks for the user's password? Thanks in the advance.

---

### Post by gettinoriginal on 2009-01-06
The person installing the system is the primary "user" and therefore is the only one with root privileges unless they authorize others.  The reason for "su" asking for password is just a precaution to keep the first user from damaging the system accidentally.

---

### Post by cjv8888 on 2009-01-06
password of the root or the administrater of the system is one and the same.  By sudo,you are being root for a short time.

---

### Post by jerome1232 on 2009-01-06
> **ooobooontooo said:**
> Hi,

How come when sudo prompts for a password, it is the password of the current user rather than the root? I mean if you want to do su, you need the password of root right? I thought sudo as a one time action using the root status...how come it only asks for the user's password? Thanks in the advance.

Yes, only users that are in the admin group can use sudo, the first user is automatically put in the admin group. Any user that is in the admin group is for all intents and purposes as powerfull as the root account.

I often see a little missinformation out there regarding sudo.

The advantage is you don't have to give out a root password and you can also create half-admins, a good read is [here]("https://help.ubuntu.com/community/RootSudo").

---

### Post by jerome1232 on 2009-01-06
----double post----

---

### Post by Abu_Dayya on 2009-01-06
'su' is a command to Switch Users. any user can use that command and login with another user. Thats why you need to know the password for the second user. it doesn't matter if that second  user is root or any other user.

'sudo' means Super User DO. which means that the user wants to perform a command as a super user (a.k.a. root). And as a security standard, no one can know that root password except the system administrator who access the machine as root. So, if you want to perform a task or a command that only the root user can perform, you type sudo before it. But before that, the system administrator (root user) need to specify that this specific user (you for example) can use sudo to do this and this. The root user specify this in a file called 'sudoers'. I think its located in /etc/sudoers. In a default installation of ubuntu, the sudoers file has an entry in it that says grant sudo privilege to your user account on all files and commands of the system. Thats why you can type sudo just with any command or application in the system

---

### Post by jowilkin on 2009-01-06
I believe another advantage is that there is no root username for hackers to try to use. They need to guess a username with sudo privileges and a password for that username instead of just trying to guess the password for the "root" username.

---

### Post by Abu_Dayya on 2009-01-06
> **jowilkin said:**
> I believe another advantage is that there is no root username for hackers to try to use. They need to guess a username with sudo privileges and a password for that username instead of just trying to guess the password for the "root" username.

But you can login as root. You can say 'su - root' and switch to the root user account

---

### Post by Sef on 2009-01-06
> **Sort of stupid question on sudo authentication**From the [Ubuntu code of Conduct]("http://ubuntuforums.org/index.php?page=policy") (Section 11, #1:

> There are no stupid questions. You're not a stupid person simply because you do not know how to do something, or do not have the answer to a question. Everyone was a green user at one point in time. :)

---

### Post by jerome1232 on 2009-01-06
> **Abu_Dayya said:**
> But you can login as root. You can say 'su - root' and switch to the root user account

Actually you can't, the root account is locked in Ubuntu, that will result in an authentication failure. You can get a root shell using sudo though.

```
sudo -i
sudo -s
```

---

### Post by mcduck on 2009-01-06
> **Abu_Dayya said:**
> But you can login as root. You can say 'su - root' and switch to the root user account

That wouldn't work, since "su" would ask for root's password..

If you want to open a root shell, use "sudo -i". ("sudo su" quite works also, but it doesn't load root's environment variables correctly so you should use "sudo -i" instead.)

---

### Post by EnGorDiaz on 2009-01-06
> **Abu_Dayya said:**
> 'su' is a command to Switch Users. any user can use that command and login with another user. Thats why you need to know the password for the second user. it doesn't matter if that second  user is root or any other user.

'sudo' means Super User DO. which means that the user wants to perform a command as a super user (a.k.a. root). And as a security standard, no one can know that root password except the system administrator who access the machine as root. So, if you want to perform a task or a command that only the root user can perform, you type sudo before it. But before that, the system administrator (root user) need to specify that this specific user (you for example) can use sudo to do this and this. The root user specify this in a file called 'sudoers'. I think its located in /etc/sudoers. In a default installation of ubuntu, the sudoers file has an entry in it that says grant sudo privilege to your user account on all files and commands of the system. Thats why you can type sudo just with any command or application in the system


no su is full root sudo is not "full" root

---

### Post by jerome1232 on 2009-01-06
> **EnGorDiaz said:**
> no su is full root sudo is not "full" root

I don't understand how sudo isn't "full" root, I can get full root privileges with it and I can get a root shell with it.

Why do you believe su = full root and sudo doesn't?

---

### Post by donkyhotay on 2009-01-06
Because you can configure sudo to allow a user more permissions then the average user but not full access. With a default installation though the first user does have full access with sudo exactly as if they were logged in as root so there isn't any real difference. But say you wanted to create an account where a user can use synaptic but has no other administrative privileges. You could configure the sudoers file to give them this limited access while your account of course retains it's full access privileges.

---

### Post by bodhi.zazen on 2009-01-06
sudo and su are obviously different programs.

While the most commonly are used to access root, you can use either to access a different user.

su bodhi
sudo -u bodhi

By default sudo uses the users password but if you prefer it can be configured to use the target password.

Either way if you wanted to sudo -u bodhi you would need to configure sudo to allow you to run a command as bodhi and in the process can configure sudo to use either your user password or bodhi's password.

For details see :

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

### Post by ooobooontooo on 2009-01-06
Thanks guys for all the answers. I can see now why sudo and su ask for different passwords.

@Sef
Thanks for raising my self-esteem :D

@EnGorDiaz
sudo and su both give you "full" root power. Sudo basically gives you root standing for one command. At least that's how it is to my understanding.

---

### Post by bodhi.zazen on 2009-01-06
Not exactly.

Both commands allow you to change roles , or run commands as another user, usually root. 

With su you need to know the target password.

With sudo you need to be given permission in /etc/sudoers.

You can obtain a root shell with sudo -i

You can run graphical applications as root with gksu

The *major* difference between them is su is all or none. Enter the root password and you can do as you wish. sudo allows you to give access to some but not all commands as root.

Another *major* advantage of sudo is that it uses the users password, thus the admin can give you the privilege of say restarting the apache server WITHOUT giving away the root password.

IMO sudo also has superior logging of what a user does with these privileges.

---

### Post by ooobooontooo on 2009-01-06
Ahh. Thanks for clearing that up...I always thought they were the same...thanks a lot.

---

### Post by Abu_Dayya on 2009-01-07
> **jerome1232 said:**
> Actually you can't, the root account is locked in Ubuntu, that will result in an authentication failure. You can get a root shell using sudo though.

```
sudo -i
sudo -s
```

Actually you can. I just did it
```

Abu_Dayya@PC:~#su - root
Password:
root@PC:~#echo You Can SU To Root
You Can SU To Root
root@PC:~#exit
logout
Abu_Dayya@PC:~#

```

---

### Post by mcduck on 2009-01-07
> **Abu_Dayya said:**
> Actually you can. I just did it
```

Abu_Dayya@PC:~#su - root
Password:
root@PC:~#echo You Can SU To Root
You Can SU To Root
root@PC:~#exit
logout
Abu_Dayya@PC:~#

```

Yes, you can, IF you have enabled root account by giving it some password.

On the default setup (of Ubuntu) you can't, because "su" asks for root's password, and you can't know it.

```
mcduck@hyperion:~$ su - root
Password:
su: Authentication failure
mcduck@hyperion:~$

mcduck@hyperion:~$ sudo -i
[sudo] password for mcduck:
root@hyperion:~#
```
(note that I used my own password in both examples, since it's the only password I have for my system. I don't know root's password because I haven't enabled the root account.)

---

### Post by jerome1232 on 2009-01-07
> **Abu_Dayya said:**
> Actually you can. I just did it
```

Abu_Dayya@PC:~#su - root
Password:
root@PC:~#echo You Can SU To Root
You Can SU To Root
root@PC:~#exit
logout
Abu_Dayya@PC:~#

```

As mcduck says your either using another distribution of Linux or you enabled the root account on that computer. 

As a side note "sudo su -" works to gain a root shell much like "sudo -i".

See the exclamation mark in roots entry in /etc/shadow, that means the account doesn't allow logins. That is how Ubuntu ships is with root locked. Your's is obviously not locked.
```
$ sudo cat /etc/shadow | grep root
root:!:12422:0:88999:7:::

```

from man shadow

>        If the password field contains some string that is not valid result of
       crypt(3), for instance ! or *, the user will not be able to use a unix
       password to log in, subject to pam(7).

---

### Post by capnthommo on 2009-01-07
> **jerome1232 said:**
> Yes, only users that are in the admin group can use sudo, the first user is automatically put in the admin group. Any user that is in the admin group is for all intents and purposes as powerfull as the root account.

I often see a little missinformation out there regarding sudo.

The advantage is you don't have to give out a root password and you can also create half-admins, a good read is [here]("https://help.ubuntu.com/community/RootSudo").
thanks jerome, that sudo info link is interesting. it explains it pretty clearly.  i half understand  now.
cheers
nigel

---

### Post by bsilver6 on 2009-02-10
Hi,
Sorry to bump a solved thread, but I wanted to add my thanks for the informative posts and to add my usage scenario to see if I understand correctly.
I have a small family system with four users (who are trusted - as long as they don't do something accidentally). They must all be ordinary, unprivileged users for day-to-day PC use, but I need to be able to run as root from all of these accounts -- or so I thought before reading this thread.
What I really need, I think, is not to be able to temporarily run as root, but to be able to temporarily run as a member of the admin group.
My solution is instead of adding all of these users to the sudoers file, I have created a new "administrator" user as a member of the admin group, and when the ordinary users need to elevate their priveleges they run
```
su administrator -c "sudo <command>"
```
I have created a custom command to do this, called "admindo."
The disadvantage is that the password must be entered twice (once for su, once for sudo), but this seems to be the correct way to do this.
What do you think?

---

### Post by ooobooontooo on 2009-02-10
I'm sorry. I don't really see how that is different from adding the users themselves to the sudoers file. Because you're using the "sudo" command from "administrator", the end result is that you do something with root power anyway...right?

---

### Post by jerome1232 on 2009-02-10
> **ooobooontooo said:**
> I'm sorry. I don't really see how that is different from adding the users themselves to the sudoers file. Because you're using the "sudo" command from "administrator", the end result is that you do something with root power anyway...right?

The difference is that you have to know the admin's account password to get root privileges. Otherwise if you just add the other users to the admin group they can authenticate anything with their own passwords. This way you can get root privieleges by "su"ing to the admin account (requires the admin accounts pw, then sudoing the command (again requires that admin accounts password).

---

### Post by ooobooontooo on 2009-02-10
Right, but according to bsilver6, the users are all trusted, so wouldn't it just be extra authentication in this context no? Unless what you said is what bsilver6 meant and he didn't want to give the administrator password to everyone...

---

