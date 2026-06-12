---
title: "Problem Root Login With Ssh"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by issamneo on 2008-04-18
Hi all,
i want to acces an ubuntu desktop with ssh as root, but i can't.
i edit /etc/ssh/sshd_conf and change PermitRootLogin to yes, then i restart the ssh.
i think the user root isn't activate, when i done su root, it don't work, and when i look in users [graphical] i don't found a user root
but no result.
any help

---

### Post by jrib on 2008-04-18
Why not just login as your user who can sudo and use sudo like you do locally?  There's no need to ever login as root and it's a really bad idea to do it using ssh in my opinion.

---

### Post by issamneo on 2008-04-18
I FOUND IT
sudo passwd root  // to activate the root login

---

### Post by jrib on 2008-04-18
> **issamneo said:**
> I FOUND IT
sudo passwd root  // to activate the root login

completely unnecessary and not recommended.  You should really read through [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by rogirwin on 2008-04-18
Lots of good points but no overwhelming reason not to do it.

Sometimes I just like being root. I find myself typing "sudo this" and "sudo that" otherwise. eg when you are looking through lots of log files or trying to find something in /proc. Many of these files are only readable by root and it's not always clear which one I want.

I guess I'm used to it after years of using Slackware....

---

### Post by Kensey on 2008-04-18
> **rogirwin said:**
> Sometimes I just like being root. I find myself typing "sudo this" and "sudo that" otherwise. eg when you are looking through lots of log files or trying to find something in /proc. Many of these files are only readable by root and it's not always clear which one I want.

If you just want a root shell to work in from time to time, you don't have to activate the root account for it.  You can either:

$ sudo bash

which gives you a root shell with your environment variables intact, or

$ sudo su -

which gives you a root login shell.

---

### Post by jrib on 2008-04-18
> **rogirwin said:**
> Lots of good points but no overwhelming reason not to do it.

Sometimes I just like being root. I find myself typing "sudo this" and "sudo that" otherwise. eg when you are looking through lots of log files or trying to find something in /proc. Many of these files are only readable by root and it's not always clear which one I want.

I guess I'm used to it after years of using Slackware....


Well there's no reason to actually set a root password, though.  If you want a root shell, just run ```
sudo -i
```.  And really, if you know what you are doing, I don't care what you do on your machine of course.  But what I see happening too often is that users who are new to linux feel like ubuntu is depriving them of power by not letting them be root.  And that's not the case since you can use sudo for whatever it is you thought you needed root for.

In this case though, enabling root logins through ssh *is* a bad idea.  At least before, a cracker had to guess a username *and* password, now they just guess a password.

---

### Post by Iowan on 2008-04-19
You may need to modify **/etc/ssh/sshd_config** to allow root login.

---

