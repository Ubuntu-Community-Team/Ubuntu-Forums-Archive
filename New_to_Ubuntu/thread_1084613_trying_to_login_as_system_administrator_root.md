---
title: "trying to login as system administrator root"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by funkyali on 2009-03-02
Hi

I'm trying to install LAMP. I'm from a windows background and this is my first lamp installation.

I'm busy following the lamp installation guide. [http://www.apachefriends.org/en/xampp-linux.html#377](http://www.apachefriends.org/en/xampp-linux.html#377)

I downloaded the tar and in the terminal window I type 
```
su
```
it askes me for a password I enter in my password (I'm the only user on this pc/network). It then waits a bit then gives me the following error
```
su : Authentication failure
```


Any ideas where I could be going wrong?

---

### Post by Simian Man on 2009-03-02
Ubuntu comes with the root account locked.  The forums have some kind of fascist ploicy against describing how to unlock it, but if you search the web you will find out how.  You could also use
```
sudo su
```
or
```
sudo bash
```

to get around this.

---

### Post by Kobalt on 2009-03-02
There is no facist policy aboout the use of su / sudo ... 

Please read this for more information : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by obaid on 2009-03-02
funkyali, to execute a command as root in ubuntu, use sudo

[COLOR="Red"]sudo *command*[/COLOR]

this will execute command as root.
-----------------------------------------------------------

have you tried to search apt-cache for lamp before you download the source ?

sudo apt-get update
sudo apt-cache search lamp

first line to update your ubuntu repos. second command to search for lamp package. read through the output to find your package name, then install it with:

sudo apt-get install lamp (incase lamp package name was simply lamp)

------------------------------------------------------------------------------

do you know that there is search funtionality in this forum.
did you know that if you query google for "install lamp in ubuntu" you will get some good results ?!!

what is your opinion ?

---

### Post by funkyali on 2009-03-02
Thanks everybody,

I know about sudo command but did not realise I could use that instead of SU.
I've not searched anythign I just went ot the xammp for linux site and downloaded. Whats the apt-cache for? I'll do some more searches.

---

### Post by obaid on 2009-03-02
read apt-cache manual.
type "man apt-cache" in your terminal.

---

### Post by Zvezdichko on 2009-03-02
The commands are:

sudo su

then

passwd

and you type your new pass

Then, you will be able to log in using only su.

---

### Post by donkyhotay on 2009-03-02
The reason for the policy on logging in as root is because the average user doesn't need it and logging in as root is a bad habit to get into. There are *very* few tasks requiring root access that can not be done with sudo and all of these tasks are advanced enough that any user that doesn't already know how to turn on the root account on their own has no business attempting these tasks. Admittedly this sometimes does create confusion when someone learning ubuntu is used to doing this from another distro or someone migrating from windows is following instructions designed for another distro, but it's the best way ubuntuforums can come up with to stop the spread of bad security practices on linux.

---

### Post by marco123 on 2009-03-02
> **obaid said:**
> funkyali, to execute a command as root in ubuntu, use sudo

[COLOR="Red"]sudo *command*[/COLOR]

this will execute command as root.
-----------------------------------------------------------

have you tried to search apt-cache for lamp before you download the source ?

sudo apt-get update
sudo apt-cache search lamp

first line to update your ubuntu repos. second command to search for lamp package. read through the output to find your package name, then install it with:

sudo apt-get install lamp (incase lamp package name was simply lamp)

------------------------------------------------------------------------------

do you know that there is search funtionality in this forum.
did you know that if you query google for "install lamp in ubuntu" you will get some good results ?!!

what is your opinion ?

This is how it is done.  You simply preface the command with "sudo" which means super-user do.

Cheers, Marco.

---

### Post by egalvan on 2009-03-02
> **funkyali said:**
> Hi

I'm trying to install LAMP. I'm from a windows background and this is my first lamp installation.

Any ideas where I could be going wrong?

Are you trying to install a **program named LAMP**,

or the **software stack named LAMP** (Linix,Apache,MySQL,PHP/Pearl/Python)?

From the web site you reference, it seems the **stack** is what you are trying to install.

links to ubuntu-specific LAMP-stuff

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

[http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html)



As for down-loading and installing software yourself,
 be aware of up-date and dependency problems that can crop up.

Much better to use apt-get or, if you have a GUI, then Synaptic.
This will take care of updates and dependencies.

---

