---
title: "[SOLVED] root password  lost?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by jsf_pp on 2008-12-05
hi, I've just installed ibex and now, when i went to terminal and tried to be root this happened:

```
julio@Chulio-lappie:~$ su
Password: 
su: Authentication failure
julio@Chulio-lappie:~$ su
Password: 
su: Authentication failure
julio@Chulio-lappie:~$ su
Password: 
su: Authentication failure
julio@Chulio-lappie:~$ su
Password: 
su: Authentication failure
julio@Chulio-lappie:~$ su
Password: 
su: Authentication failure
julio@Chulio-lappie:~$ su
Password: 
su: Authentication failure
julio@Chulio-lappie:~$ su
Password: 
su: Authentication failure
julio@Chulio-lappie:~$ su

```

im fully positive i know my password, but it doesn't work.
can you help me with that?
thanks.

---

### Post by mikewhatever on 2008-12-05
Root account is disabled in Ubuntu, all versions, as far as I know. You can either use sudo or sudo su. For more info, look here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tarps87 on 2008-12-05
There is no root by default, this is to increase security.
It is recommended to use sudo instead e.g.
```
sudo apt-get install program
```
As long as you have root privileges you can use sudo, if you are the only user or the user you set up on install you will have root privileges. (Password is your usual password)

---

### Post by m_duck on 2008-12-05
> **mikewhatever said:**
> You can either use sudo or sudo su.Using```
sudo -i
```will also give you root privileges.

---

### Post by jsf_pp on 2008-12-05
well, i need to change sth in etc/apt/sources.list

but i cant cuz:

You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again.

so, how can i change sth in that file?

btw, im trying to do this:
[http://mynewbietips.blogspot.com/2007/06/installing-canon-pixma-ip1200-driver.html](http://mynewbietips.blogspot.com/2007/06/installing-canon-pixma-ip1200-driver.html)

thanks.

---

### Post by jsf_pp on 2008-12-05
> **m_duck said:**
> Using```
sudo -i
```will also give you root privileges.

thanks, it did work with this one.

---

### Post by glennric on 2008-12-05
To edit a file like /etc/apt/sources.list you should use sudo as mentioned above.  Type
```
sudo vi /etc/apt/sources.list
```
If you don't like vi change that to a text editor that you prefer.  Technically if your application is graphical (like gedit) you should use gksu instead of sudo.  For example
```
gksu gedit /etc/apt/sources.list
```

---

### Post by glennric on 2008-12-05
By the way, check out 
[Forum policy on log-in-as-root]("http://ubuntuforums.org/showthread.php?t=716201")
for more information on this.

---

### Post by Wrathchild9 on 2008-12-05
I advise you not to log in as root, I think you should use 'sudo' instead of it.

---

### Post by louieb on 2008-12-05
> **glennric said:**
> By the way, check out 
[Forum policy on log-in-as-root]("http://ubuntuforums.org/showthread.php?t=716201")
for more information on this.

> **Wrathchild9 said:**
> I advise you not to log in as root, but if you want so, you can change the root password from your account. I think you should use 'sudo'.
Hello Wrathchild9. welcome to Ubuntu forums. I see your new here. But not to Linux it appears. Think you should read glennric's link.

---

### Post by Wrathchild9 on 2008-12-05
> **louieb said:**
> Hello Wrathchild9. welcome to Ubuntu forums. I see your new here. But not to Linux it appears. Think you should read glennric's link.
Thanks for the welcome and the warning, I corrected the post :)

---

