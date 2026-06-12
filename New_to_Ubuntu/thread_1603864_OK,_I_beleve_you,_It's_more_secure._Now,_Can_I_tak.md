---
title: "OK, I beleve you, It's more secure. Now, Can I take control of my PC!"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by linverno2.0 on 2010-10-23
To do any important thing I have to provide a password!
Ok, I can accept this concept in case he accept my password
but he didn't

I'm try to use su and I give him password fo "ahmed" user
which is only user in the system
he give me that:
[INDENT]ahmed@Lab:~$ su
Password: 
su: Authentication failure
ahmed@Lab:~$ 

[/INDENT]And when I try to use SUDO
he give me that:
[INDENT]ahmed@Lab:~$ sudo ahmed
[sudo] password for ahmed: 
ahmed is not in the sudoers file.  This incident will be reported.
ahmed@Lab:~$ 
[/INDENT]Now I have to add "ahmed" to sudoers file, as he want
When I search for how to do that
all I found is I have to use root user to do it
but I can't use root already

What Can I do now
I spend all the morning try to install  "Nokia QT" and firefox 4.0 beta
and it's lead me to do a bunch of administrative stuff
until now I did not install anything
and I starting to be upset


by the way this is what UBUNTU give me when I try to install QT and Firefox
1- Installing of QT give me Segments Failure
2- Installing of Firefox 4.tar.bz2 give me
    tar: Unexpected EOF in archive
    tar: Unexpected EOF in archive
    tar: Error is not recoverable: exiting now

---

### Post by linverno2.0 on 2010-10-23
PC: Maybe this subject have been opened before, and maybe a lot of threads in this forums talking about this subject.
I'm sorry if I can't search for those threads, because I'm already read a lot of articles and Blog posts today
And follow a lot of How-To articles.
and I get tired, really.
in windows to install any software all what I need is Double-Click and press OK, and some "Next" buttons.
Why UBUNTU doesn't make it like this?

---

### Post by HermanAB on 2010-10-23
So, basically what you are saying is that you forgot your password.

Reboot the machine and select single user mode (Ubuntu calls it recovery mode), then reset your password:

From the grub boot menu, select "recovery mode"
Then select "Drop to root shell"

You are root (the prompt is '#' )
passwd username
Give the new password, twice.
reboot

---

### Post by cchhrriiss121212 on 2010-10-23
> **linverno2.0 said:**
> 
in windows to install any software all what I need is Double-Click and press OK, and some "Next" buttons.
Why UBUNTU doesn't make it like this?
In Ubuntu you install everything through a package manager, and not by downloading from websites. Open up either software center or synaptic package manager and install anything using that, firefox and qt are both in the repository.

---

### Post by coffeecat on 2010-10-23
> **linverno2.0 said:**
> in windows to install any software all what I need is Double-Click and press OK, and some "Next" buttons.
Why UBUNTU doesn't make it like this?

Because Ubuntu makes it easier. As cchhrriiss121212 says, open up Applications > Software Center and you'll even save on the number of clicks. :wink:

---

### Post by sandyd on 2010-10-23
> **linverno2.0 said:**
> To do any important thing I have to provide a password!
Ok, I can accept this concept in case he accept my password
but he didn't

I'm try to use su and I give him password fo "ahmed" user
which is only user in the system
he give me that:
[INDENT]ahmed@Lab:~$ su
Password: 
su: Authentication failure
ahmed@Lab:~$ 

[/INDENT]And when I try to use SUDO
he give me that:
[INDENT]ahmed@Lab:~$ sudo ahmed
[sudo] password for ahmed: 
ahmed is not in the sudoers file.  This incident will be reported.
ahmed@Lab:~$ 
[/INDENT]Now I have to add "ahmed" to sudoers file, as he want
When I search for how to do that
all I found is I have to use root user to do it
but I can't use root already

What Can I do now
I spend all the morning try to install  "Nokia QT" and firefox 4.0 beta
and it's lead me to do a bunch of administrative stuff
until now I did not install anything
and I starting to be upset

**are you the first user on this computer?**

by the way this is what UBUNTU give me when I try to install QT and Firefox
1- Installing of QT give me Segments Failure
[B]```

apt-get install qt4-dev-tools libqt4-core libqt4-dev libqt4-gui libqt4-assistant libqt4-designer libqt4-dev libqt4-network ibqt4-sql-mysql libqt4-sql-sqlite libqt4-webkit libqt4-xml libqtgui4
```
there.[/B]

2- Installing of Firefox 4.tar.bz2 give me
    tar: Unexpected EOF in archive
    tar: Unexpected EOF in archive
    tar: Error is not recoverable: exiting now
[B]
```

add-apt-repository ppa:ubuntu-mozilla-daily/ppa
apt-get update
apt-get install firefox-4.0
```[/B]

---

### Post by Old_Grey_Wolf on 2010-10-23
Odd, your computer is named "Lab", and you are not in the sudoers file.

:lolflag:

---

### Post by CharlesA on 2010-10-23
Things that make you go "Hmm..."

---

### Post by perspectoff on 2010-10-23
sudo passwd ahmed

Now enter the password you want to be associated with ahmed.

You can set the user ahmed to be an administrator in the User Management -> User Accounts -> Modify... -> Privileges and Groups section of System Settings, if you'd like.

---

### Post by CharlesA on 2010-10-23
Problem is that they aren't in the sudoers file.

That makes the thread sound a bit fishy tbh.

---

### Post by Old_Grey_Wolf on 2010-10-23
> **CharlesA said:**
> Problem is that they aren't in the sudoers file.

That makes the thread sound a bit fishy tbh.

Hum, you think so too.

---

### Post by coffeecat on 2010-10-23
> **CharlesA said:**
> That makes the thread sound a bit fishy tbh.

Well, not to worry.

> **linverno2.0 said:**
> [INDENT]ahmed@Lab:~$ sudo ahmed
[sudo] password for ahmed: 
ahmed is not in the sudoers file. [COLOR=red] This incident will be reported.[/COLOR]
ahmed@Lab:~$ 
[/INDENT]

The "Lab" sysadmin is going to hear about this.

---

### Post by perspectoff on 2010-10-23
> **CharlesA said:**
> Problem is that they aren't in the sudoers file.

That makes the thread sound a bit fishy tbh.

Yeah, I get what you're saying. He's not the original installing user.

But it's not an unusual question to want to create several administrative accounts on a single installation.

Clearly a second administrative user can only be created by the original administrative user (or by root).

You seem to be implying this user has no administrative rights whatsoever on the computer he is trying to modify, but that may not be the case. He may need to ask the original administrative user to give him the privileges if he doesn't, but that is also not outside the realm of possibilities.

You know, I have inherited entire networks for which the original administrative user(s) have long since retired. (Some Linux computers can function for years without intervention.) It is not rare that I have had to call a retired administrator to ask for root passwords so that I could take over administration of the inherited network.

This included a "lab" network for my university, many years ago. Students come and go, you know, and often it is students that have set up networks.

---

### Post by CharlesA on 2010-10-23
True.

However, if a new user was created and wasn't added to the admin group, they wouldn't have access to sudo.

If it's not their machine, they'd have to talk to whoever is in charge of it to give them admin rights. If it's their machine, they could just use su to switch to a user with sudo rights and add themselves to the admin group, or to the sudoers file.

That's why it sounds fishy.

---

### Post by sadaruwan12 on 2010-10-23
Bro First of all please let us that did you installed the or did some one installed it for you and let you use it after ward?

---

### Post by Old_Grey_Wolf on 2010-10-23
> **coffeecat said:**
> The "Lab" sysadmin is going to hear about this.

LOL. Those funny lines in the sudoers file something like
```

mailto "labadmin@school.ofhardknocks.edu"
mail_badpass on

```

---

### Post by linverno2.0 on 2010-10-23
guys I'm felling bad from your replies.

> Odd, your computer is named "Lab", and you are not in the sudoers file.

hings that make you go "Hmm..."

Problem is that they aren't in the sudoers file.
That makes the thread sound a bit fishy tbh.

The "Lab" sysadmin is going to hear about this.


Yeah, I get what you're saying. He's not the original installing user.

the computer is my computer and I name it Lab because it is like a lab for me
I'm doing all software experiments on it
And the Lab sysadmin who is going to hear about this is ME
and I didn't hear anything
And for your information I'm the original installing user
And I'm install it by my self and create one user
only one

My problem is so obvious I installed the system and create one user
and I **can't use root user** ... for mystery reason.

If you didn't face problem like this before
PLEASE put your tongue inside your mouth.
and [COLOR=#000000]don't accuse Others[/COLOR].

Thanks for your collaboration 

any way this is what I'll going to do

```
reinstall_ubuntu();
if (using_root)
{
     cout<<"Good";
}
else
{
      uniistall_ubuntu();
}

```

---

### Post by ezsit on 2010-10-23
> My problem is so obvious I installed the system and create one user and I can't use root user ... for mystery reason.

It is a shame NO ONE read your original post. You need to reset the root password. Ubuntu automatically assigns a password to root but disable's root login. At a command prompt, type:

**sudo passwd root**

This command will prompt you for your user password first and then prompt you type a new password for root and retype the root password a second time for confirmation. You will be told that the root password has been successfully changed. From here on out you will be able to su and enter the new root password you created. Hope this helps.

---

### Post by aysiu on 2010-10-23
It's a shame some people think setting a root password is the solution to any password problem. There's no reason to set a root password. That isn't the way Ubuntu is set up.

If it's a new user, just go to System > Administration > Users & Groups and change the user from a desktop user to an administrator.

If it's the first user, just fix /etc/sudoers and /etc/group by following these instructions:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by ezsit on 2010-10-23
The OP's initial problem was exactly how to use "su" and to do so requires setting the root password.

Also, what does it matter if Ubuntu is not set up that way. Isn't Ubuntu and Linux about empowering users and letting them decide how to use their computers?

---

### Post by linverno2.0 on 2010-10-23
ezsit
aysiu

Thank you very much both of you guys

First
I follow what's come in aysiu link
start with recovery mode and execute this command
**adduser *username* admin**
this command give me some of my lost privileges

Secound
I do as ezsit say
**sudo passwd root**

Now every thing is running OK
No I can add repositories and start installing desired applications.

Thank you again ezsit and aysiu

---

