---
title: "[SOLVED] Run as root? Help please"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by sp176 on 2008-12-29
I have been trying to install video drivers, and I have been following the instructions from a company website.

It seems to run fine until I get a message saying the installation must be run as a root user.  I am the only user of my computer, and I assumed I had full administrative access.  Can you please tell me what I may be doing wrong.

---

### Post by SuperSonic4 on 2008-12-29
```
sudo <command>
```

sudo means run as root for the following command only. It is much safer than XP where the first user was always admin

---

### Post by damis648 on 2008-12-29
I recommend you do not use drivers for a manufacturer's site, they can cause update problems later. What model card do you have, and have you tried System>Administration>Hardware Drivers?

---

### Post by Michael.Godawski on 2008-12-29
hi, 

the root account is disabled by default in Ubuntu.

To run applications or commands with root privileges you have to add a sudo or gksudo in front of the command, for instance
```

sudo apt-get install foo
```

For more info have a look here:

[LIST]
[*][http://godawski.oxyhost.com/rootsudo.html](http://godawski.oxyhost.com/rootsudo.html)
[/LIST]

---

### Post by Coder543 on 2008-12-29
or if you are not familiar with the terminal, use gksudo <command>

---

### Post by mkvnmtr on 2008-12-29
No one can give you instructions on how to log in as root. Just use sudo before any commands you use. You might should read up on the process a bit first. Someone is sure to post you some links.

---

### Post by Michael.Godawski on 2008-12-29
> **mkvnmtr said:**
> No one can give you instructions on how to log in as root. Just use sudo before any commands you use. You might should read up on the process a bit first. Someone is sure to post you some links.

We do not recommend login as root first because of the forum policy, secondly because it is not a good idea. Too many things can break. Too much frustration can be caused. If you search the internet you will find what you need. 

Information is free. But only the user is responsible for the consequences of a root-account.

The usual user do not need to be root whole the time.

The advantage of sudo/gksudo is the temporally gain of super-user rights. Just for the task at hand.

---

### Post by sp176 on 2008-12-29
I am using a NVIDIA GEFORCE 7600 GS.  I went to the company website.  Would it be better to use the system/administration/hardware drivers?

P.S. thanks a lot for the sudo command supersonic.  I had no idea what that meant before. lol

---

### Post by damis648 on 2008-12-29
It would be much better to use System>Administration>Hardware Drivers.

---

### Post by jimmy the saint on 2008-12-29
yes.  Just use the restricted driver.  If there are two available, pick the one that is NOT 177 as that has caused many issues for many people.

---

### Post by sp176 on 2008-12-29
Oh man, that was so easy.  Thanks a lot everyone

---

### Post by SuperSonic4 on 2008-12-29
Yeah, that's a big difference from windows, repositories and package managers are the order of the day in ubuntu and linux.

Don't forget to mark as solved ;)

---

