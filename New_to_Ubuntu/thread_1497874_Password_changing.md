---
title: "Password changing"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by Primus1 on 2010-05-31
Hi all,

I'm new to Ubuntu and think I've chosen a good time to try it just when Lucid LTS is out. 
Been changing my password with the help of Help :). In Help it shows the 'user settings' screen showing 'Login name' and 'Home directory' but in my computer Users Settings those two are not shown. 
As far as I know I don't have a "root" password, just one shown as "Custom". Do I need a root password separate from my custom one? I changed my custom password using the random generator though it doesn't seem a very long one, is it safe do you think?

This is the first time I've asked a question and I've been trying to learn reading from the Help and this forum but it's easy to get lost.

Thanks for any help with this.

---

### Post by hansdown on 2010-05-31
Welcome to the forum Primus1.

In order to get elevated power in ubuntu, use the sudo command.It will ask for your password.

[https://help.ubuntu.com/10.04/administrative/C/terminal.html](https://help.ubuntu.com/10.04/administrative/C/terminal.html)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by @rizz on 2010-05-31
As far as i know you that you dont need to login as the root in ubuntu

Simply type sudo before doing any administrative work. It will ask for your sudo password.
Which i feel is your normal login password.

To change password use the passwd command.

If your password is not a dictionary word and mixes capital, lowercase alpha characters, numbers and a special character or two that should be safe enough.

But then again you know what they say  "No password is full proof" but if the your password meets the mentioned criteria that should be fine.:P

---

### Post by Bob Bertrands on 2010-05-31
When you installed ubuntu, you probably just picked one username and password. This user, when switching to root, will then automatically be able to do superuser task.
<snip>

---

### Post by lisati on 2010-05-31
> **Bob Bertrands said:**
> When you installed ubuntu, you probably just picked one username and password. This user, when switching to root, will then automatically be able to do superuser task.
<snip>

Please have a look here: [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by Primus1 on 2010-05-31
Ah, I see, don't need to concern myself with 'root', just learn the use of sudo. Thanks.
Opps, that was for Hansdown, thanks for the welcome. Just seen others replies and will read now (went to links from Hansdown)

Thanks for the help people, like I said, I'm new but understand the security of Ubuntu a little better now after reading the links provided

---

