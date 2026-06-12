---
title: "How to edit etc/group and have root privileges?"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by tlfree on 2010-03-03
Hello friends,

I am trying to set up a web server now for the first time (I never used linux before in my life) and trying to make it secure, so I found out I should not let root ssh login, so I wrote "PermitRootLogin no" in /etc/ssh/sshd_config.

After this, I made a new user called jay and I wanted to give myself all the permissions so that I could still do everything.

I added this line to etc/sudoers as a website instructed me:
```
jay ALL=(ALL) ALL
```
and somehow most things worked. :o

But sometimes, even if I use sudo, I receive a message saying I do not have permission.

So I want to edit etc/group now so that I can stop having these problems but I'm confused. This is what I see:
```

root:x:0:
daemon:x:1:
bin:x:2:
...
ssh:x:110:
lpadmin:x:111:
admin:x:112:
jay:x:1000:

```
What do I need to write to make myself like root? Do I just edit

```

root:x:0:root,jay
daemon:x:1:
bin:x:2:
...
ssh:x:110:
lpadmin:x:111:
admin:x:112:
#jay:x:1000:

```

to this way? And then I will not see messages about not having permission anymore?

---

### Post by halitech on 2010-03-03
Root should be disabled in Ubuntu by default as well as in ssh so did you enable the root login or are you using a distro other then Ubuntu?

did you edit the file with gedit (or similiar) or did you use visudo?

---

### Post by mcduck on 2010-03-03
so you are actually trying to make your system more secure by removing the very things that make it secure (like normal users not always running with full permissions to do anything in the system)?

The part about not allowing root logins through SSH is valid, and very good idea indeed. But you don't, and shouldn't, give your normal user account the same permissions root has. That will pretty much ruin your security, and is completely unnecessary anyway since you can just login as your normal user and use "sudo" for admin tasks exactly like Ubuntu does by default. Just make sure that your user is in the "admin" group and you have everything you need for remote administration without messing with the system's security :)

---

### Post by tlfree on 2010-03-03
> **halitech said:**
> Root should be disabled in Ubuntu by default as well as in ssh so did you enable the root login or are you using a distro other then Ubuntu?

did you edit the file with gedit (or similiar) or did you use visudo?

Hi, I just clicked a button and my host (linode.com) created an image with ubuntu 8.04 LTS and it was set this way. I edited the files with nano.

> **mcduck said:**
> Just make sure that your user is in the "admin" group and you have everything you need for remote administration without messing with the system's security :)

Thanks for this info, so if I comment out jay and put jay after admin like this it will work fine?

```

root:x:0:
daemon:x:1:
bin:x:2:
...
ssh:x:110:
lpadmin:x:111:
admin:x:112:jay
#jay:x:1000:

```

---

### Post by bodhi.zazen on 2010-03-03
Before you go editing system files take the time to read and understand what you are doing =)

If you want a graphical too to assist you take a look at webmin.

Otherwise, read the man pages !!!

1. Normally the root account is locked in Ubuntu, so there  is no need to disable root logins via ssh.


With a VPS, however, the root account may well be enabled.

2. You do not need to manually edit /etc/groups or /etc/password, use the commands 

To see the groups your user is in use id

```
id jay
```

To add your user to a group use usermod

```
usermod -G admin -a jay
```

[http://linux.die.net/man/8/usermod](http://linux.die.net/man/8/usermod)

Once your user has sudo access, lock the root account if needed

```
sudo usermod -p ! root
```

You can edit /etc/sudoers with the visudoers command. By default this will use vi, so to use nano ..

```
# become ROOT
sudo -i
EDITOR='nano'
visudo
```

You should see a line for the admin group.

---

