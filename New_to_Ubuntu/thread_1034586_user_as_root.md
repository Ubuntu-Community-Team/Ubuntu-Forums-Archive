---
title: "user as root"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by rwltrz4 on 2009-01-08
I just installed ubuntu 8.04 and was wandering if for 1 person is it ok to set up just 1 user or should i set up 1 for admin and the other for day to day use for better security or in linux is there already a root user?

---

### Post by tuxxy on 2009-01-08
It should prompt you for a root password at install, this will differ from  your user password.

---

### Post by Facetious Falcon on 2009-01-08
Yep, there's already a root user known simply as 'root' this is never used for day-to-day operations. Your current account should be all you need for now you can use root on a temporary basis using the 'sudo' command.

---

### Post by iaculallad on 2009-01-08
Normally on Ubuntu installation, root account is disabled and you are required to create your first user. This first user has the administrative rights which can be used to configure and make changes on the system requiring the use of sudo/gksudo on commands.

---

### Post by handydan918 on 2009-01-08
> **tuxxy said:**
> It should prompt you for a root password at install, this will differ from  your user password.
Dude, do you USE Ubuntu?

Ubu will NOT let you set up a root account. You use sudo to elevate privileges to root temporarily.

---

### Post by oldos2er on 2009-01-08
"Ubu will NOT let you set up a root account."

 Actually it will, you just have to know what you're doing.

---

### Post by iaculallad on 2009-01-08
> **tuxxy said:**
> It should prompt you for a root password at install, this will differ from  your user password.

Root password or simply the first User account password? As Ubuntu by default disabled it's root account.

---

### Post by rwltrz4 on 2009-01-08
Ok well I just set it up and created a user and password at the prompts during installation so is this the one i use for day to day stuff and add/remove software, synaptics, etc?

---

### Post by tuxxy on 2009-01-08
> **handydan918 said:**
> Dude, do you USE Ubuntu?

Ubu will NOT let you set up a root account. You use sudo to elevate privileges to root temporarily.

Yes I do and Yes Ubuntu will allow you to create a root account as I said ;)

---

### Post by iaculallad on 2009-01-08
> **rwltrz4 said:**
> Ok well I just set it up and created a user and password at the prompts during installation so is this the one i use for day to day stuff and add/remove software, synaptics, etc?

Yes, that's the default account you are to use. And to access temporary root privileges, use sudo/gksudo on commands requiring elevated privileges.

---

### Post by oOarthurOo on 2009-01-08
> **rwltrz4 said:**
> I just installed ubuntu 8.04 and was wandering if for 1 person is it ok to set up just 1 user or should i set up 1 for admin and the other for day to day use for better security or in linux is there already a root user?

Just setup one user. The user you setup will be prompted for a password anytime you are about to do something that can affect the entire system. Think Vista's UAC, but not annoying or crippling to the usability of your computer.

Setting up one daily user and one admin user when really you are just one user adds nothing to the security. It only adds a layer of inconvenience to you.

---

### Post by iaculallad on 2009-01-08
> **tuxxy said:**
> Yes I do and Yes Ubuntu will allow you to create a root account as I said ;)

Ubuntu does not allow you to create the ROOT account on installation. As I mentioned earlier, ROOT account is disabled by default. And can be activated once you had created your first user, which is not recommended though.

---

### Post by theozzlives on 2009-01-08
When you perform administrative tasks, it asks for a password. The user logged on has to have admin rights, you use that users password. The first user is such a user.

---

### Post by rwltrz4 on 2009-01-08
OK !! Thanks guys for all the fast replies.

---

### Post by bodhi.zazen on 2009-01-08
See 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by handydan918 on 2009-01-08
> **oldos2er said:**
> "Ubu will NOT let you set up a root account."

 Actually it will, you just have to know what you're doing.

Well, of course. It IS still Linux, even "sudo-neutered"!

:D

---

### Post by oldos2er on 2009-01-08
"Well, of course. It IS still Linux, even "sudo-neutered"!"

 Shouldn't that be pseudo-neutered...?! Or pseudo-sudo-neutered....

---

### Post by handydan918 on 2009-01-08
> **tuxxy said:**
> Yes I do and Yes Ubuntu will allow you to create a root account as I said ;)

Tell ya what. Do an install and post a screenie of the point where you are prompted for a "root password" as well as a "user password".

Then I'll concede your point.

:P

---

### Post by tuxxy on 2009-01-08
> **handydan918 said:**
> Tell ya what. Do an install and post a screenie of the point where you are prompted for a "root password" as well as a "user password".

Then I'll concede your point.

:P

It doesn't sorry, I already said in another post that it must be done from terminal and I gave the command but post got removed as we only use sudo.

---

### Post by bodhi.zazen on 2009-01-09
> **tuxxy said:**
> It doesn't sorry, I already said in another post that it must be done from terminal and I gave the command but post got removed as we only use sudo.

That is a point of confusion.

You may enable the root account if you wish, we do not mind.

What we ask is that you teach new users how to use their system and how to use sudo. This includes such things as permissions and what not.

Too often people throw out something like "gksu nautilus" as a "solution" (for example) to a new users question, but never take the time to explain permissions.

In addition setting a root password can cause problems.

So we would appreciate if you, as an experienced user, would take the time to educate new users.

There are, however, times when you do need to set a root password. In that event we support doing so, but again would prefer if you also explained how to lock the root account again and also the "risks" or setting a root password.

So please just slow down a little and take the time to educate, I think that is what gets missed in many of these root password discussions.

Keep in mind the old saying when in Rome ...

If you started posting how to install sudo, recompile / install the patches, lock the root account, and use sudo rather then su on the Fedora Froums how would you be treated ? (yes, I know you can use sudo in Fedora or Debian or any distro, that is not my point).

---

