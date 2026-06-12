---
title: "Trouble configuring wine. can you help?"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by scrypt on 2010-01-12
Hello all.

Im newish to Ubuntu so apologies in advance.

I am trying to install and run World of Warcraft on Ubuntu.

I am using this guide 

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I am having trouble quite early on with this command :

Sudo winecfg

I ran to firstly configure wine.

I got this output :

-laptop:~$ sudo  winecfg
wine: /home/mark/.wine is not owned by you

As you can see it says that /home/mark/.wine is NOT owned by me.

Am I right to be alarmed by this??

any help will be appreciated.

Why is it saying .wine is Not owned by me?

---

### Post by Hospadar on 2010-01-12
When you run a command with 'sudo', the command gets run as [the user named] root, which is the administrator in a unix (linux/osx/bsd/etc) environment.

So wine checks to make sure the wine directory is owned by the same user as the one running winecfg, (and remember, when you 'sudo winecfg' you're actually running as root), because when you later run wine as yourself (not root via sudo) you'll need read and write access to the whole directory (and winecfg might create some files while being run as root, which would later be un-writeable as your regular user).

Sooo,
I'd just say run winecfg without sudo, I can't think of a reason why you'd need root.  All it does is modify configuration data inside the wine folder, and there's no need to have root for that.

A side note which will help, the ~/.wine directory is where everything wine is stored, all the files which make up your fake c drive, anything you install through wine goes there, all wine configuration, etc, etc.  It's actually possible as well to have multiple wine directories since some programs require different wine configurations.

---

### Post by telovin on 2010-02-02
Hi Hospadar,
Even I get the same error. How to modify configuration of wine folder? any idea how to do it?

---

