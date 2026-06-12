---
title: "can't find root in users &amp; groups"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by spearfish on 2011-01-24
I just installed Ubuntu 10.10 on my laptop and when I open the Users & Groups control panel, it just shows a single user (myself).  It does not show "root" like it did in Ubuntu 8.  So, can anyone please tell me how I set the password for root?  I'm the only user on my laptop, so that makes me the admin :)  I can't even *find* root in Users & Groups.

Thanks ;)

---

### Post by sikander3786 on 2011-01-24
Root account is disabled by default in Ubuntu. And giving instructions on how to enable root account is prohibited on Ubuntuforums ;-)

You might already know that you can use sudo for all of the tasks that need root privileges.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

And that is meant to keep you and your PC safer and stable.

---

### Post by spearfish on 2011-01-24
> **sikander3786 said:**
> Root account is disabled by default in Ubuntu. And giving instructions on how to enable root account is prohibited on Ubuntuforums ;-)

You have *got* to be joking.  How is a new user supposed to learn how to use their computer then?  Well, I searched around another (more user-friendly) forum and found the following:

"Ubuntu is one of the few Linux distributions out there that will not enable the root account."  Yes, you are supposed to do everything with "sudo" however there are some setup programs that require it the root password and won't let you use sudo.

I seem to have solved my problem with:  <snip>

Hooray, now I can install my Dell printer drivers.  The Dell setup script I downloaded from their driver website prompts the user for the system/root password.  Even though I am logged on as an administrator with full privileges on my system, it won't accept my own account password.

---

### Post by sisco311 on 2011-01-24
> **spearfish said:**
> You have *got* to be joking.  How is a new user supposed to learn how to use their computer then?  


[thread=1486138]Forum policy on log-in-as-root tutorials[/thread]

> **spearfish said:**
> 
Hooray, now I can install my Dell printer drivers.  The Dell setup script I downloaded from their driver website prompts the user for the system/root password.  Even though I am logged on as an administrator with full privileges on my system, it won't accept my own account password.

Yep, that script is poorly written... However if you run it as root, it won't prompt you for a password:
```
sudo path/to/driver
```

---

### Post by cariboo on 2011-01-24
There seems to be a bit of a misunderstanding here, we have nothing against telling someone how to enable the root account, as long as you also explain the dangers of running as root all the time.

What we don't want is someone explaining how to login as root from the login page.

> "Ubuntu is one of the few Linux distributions out there that will not enable the root account." Yes, you are supposed to do everything with "sudo" however there are some setup programs that require it the root password and won't let you use sudo.

If you need to run something as root, use sudo -i, this will drop you to a root prompt

---

### Post by matt_symes on 2011-01-24
Hi

```
I seem to have solved my problem with: $sudo passwd root
```

I prefer sudo -i or sudo su, as you don't have to enable the root account, but you still get to a shell with root privileges (and only one password to remember).

Kind regards

---

