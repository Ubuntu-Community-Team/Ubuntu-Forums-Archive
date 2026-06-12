---
title: "grub-pc error"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by 416inversed on 2010-08-11
I have a dual-booting (10.04/XP) Acer Aspire D250. When I run upgrade from terminal, I've been getting the following error:

```
Setting up grub-pc (1.98-1ubuntu7) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 128
Errors were encountered while processing:
 grub-pc

E: Sub-process /usr/bin/dpkg returned an error code (1)

```although sometimes it's "exit status 20"

I've tried uninstalling/reinstalling grub-pc from Synaptic to no avail and as uninformed messing around with grub can bork your boot, I was hoping someone more informed could help.

---

### Post by 416inversed on 2010-08-11
Bump from last night.

Is it perhaps some conflict with BURG?

I tried uninstalling BURG last night to test my theory, but ended up borking into a GRUB rescue prompt. Reinstalling BURG fixed the bork, but the grub-pc error remains.

---

### Post by 416inversed on 2010-08-12
Anyone?

---

### Post by Fludizz on 2010-08-12
Have you tried running dpkg with debugging options? Might give some more information on what might be going wrong... (check dpkg -Dh for more info on debugging with dpkg.)

---

### Post by QLee on 2010-08-12
416inversed,

Have you tried sudo dpkg --configure grub-pc, what error does that drop?

Have you tried sudo dpkg -f install, what error does that drop?

---

### Post by 416inversed on 2010-08-12
> **Fludizz said:**
> Have you tried running dpkg with debugging  options? Might give some more information on what might be going  wrong... (check dpkg -Dh for more info on debugging with dpkg.)

I haven't because I wouldn't know where to start.

> **QLee said:**
> 
Have you tried sudo dpkg --configure grub-pc, what error does that drop?

```
Setting up grub-pc (1.98-1ubuntu7) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 20
Errors were encountered while processing:
 grub-pc

```

> **QLee said:**
> 
Have you tried sudo dpkg -f install, what error does that drop?

 ```

dpkg-deb: failed to read archive `install': No such file or directory

```

---

### Post by QLee on 2010-08-12
Okay, since I'm obviously not reading what I write, lets try an 
sudo apt-get -f install.

---

### Post by 416inversed on 2010-08-12
> **QLee said:**
> Okay, since I'm obviously not reading what I write, lets try an 
sudo apt-get -f install. :)

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up grub-pc (1.98-1ubuntu7) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 128
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by QLee on 2010-08-12
So we know the grub-pc package has not been configured for some reason.

We also know the system was not able to force the install.

You next might try purging the package grub-pc then reloading the lists (update), then trying the install of grub-pc again (or upgrade of the system). This is what you originally tried from the command line, isn't it, an upgrade of the system after an update?

---

### Post by 416inversed on 2010-08-12
> **QLee said:**
> So we know the grub-pc package has not been configured for some reason.

We also know the system was not able to force the install.

You next might try purging the package grub-pc then reloading the lists (update), then trying the install of grub-pc again (or upgrade of the system). This is what you originally tried from the command line, isn't it, an upgrade of the system after an update?

Thank you.

Even though I swear I did the same thing through Synaptic to no avail, purging & reinstalling from the command line seems to have worked. No error messages.

Now excuse me while I hold my breath & reboot my computer....

---

### Post by 416inversed on 2010-08-12
Ok. So the error message is gone, but now I get the old RUB screen instead of the pretty BURG.

Should I now  uninstall & reinstall BURG?

---

### Post by 416inversed on 2010-08-12
> **416inversed said:**
> Ok. So the error message is gone, but now I get the old RUB screen instead of the pretty BURG.

Should I now  uninstall & reinstall BURG?

To answer my own question, yes. I'll mark the thread as solved.

Thanks again QLee for your help!

---

### Post by QLee on 2010-08-12
> **416inversed said:**
> Ok. So the error message is gone, but now I get the old RUB screen instead of the pretty BURG.

Should I now  uninstall & reinstall BURG?

I'm sorry, I don't know anything about BURG, but that's probably what I would try, purge the package to git rid of any left over configuration then reinstall.

---

### Post by Elmer Fudd on 2010-08-12
> **416inversed said:**
> Ok. So the error message is gone, but now I get the old RUB screen instead of the pretty BURG.

Should I now  uninstall & reinstall BURG?

If you use BURG, as I do on all my installs, make this change to prevent Grub updates from re-taking control of the boot.

edit the /etc/kernel-img.conf
replace “update-grub” with “update-burg”

---

### Post by rolandixor on 2010-09-18
> **Elmer Fudd said:**
> If you use BURG, as I do on all my installs, make this change to prevent Grub updates from re-taking control of the boot.

edit the /etc/kernel-img.conf
replace “update-grub” with “update-burg”

this is the wrong file (if on maverick i think); edit /etc/kernel/postinst.d/zz-update-grub
change the line with update-grub to update-burg as above.

---

### Post by moravveji on 2010-11-16
QLee:
Can you also help me with this grub-pc problem? I use Ubuntu 10.04 and everytime, I receive this message:

> 
/usr/local/bin/perl: 34: =: not found
/usr/local/bin/perl: 35: =: not found
/usr/local/bin/perl: 36: =: not found
/usr/local/bin/perl: 36: =: not found
/usr/local/bin/perl: 37: =: not found
/usr/local/bin/perl: 40: =: not found
/usr/local/bin/perl: 67: Syntax error: "{" unexpected (expecting "do")
Setting up grub-pc (1.98-1ubuntu8) ...
/usr/local/bin/perl: line 34: =: command not found
/usr/local/bin/perl: line 35: =: command not found
/usr/local/bin/perl: line 36: =: command not found
/usr/local/bin/perl: line 36: =: command not found
/usr/local/bin/perl: line 37: =: command not found
/usr/local/bin/perl: line 39: =: command not found
/usr/local/bin/perl: line 67: syntax error near unexpected token `{'
/usr/local/bin/perl: line 67: `while (@ARGV && $ARGV[0] =~ /^-/) {'
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks in advance.

---

### Post by moravveji on 2010-12-12
> **416inversed said:**
> :)

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up grub-pc (1.98-1ubuntu7) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 128
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Hi all. I have a similar problem with grub-pc, and here is the error message I receive:
> 
root@ehsan:/home/ehsan# dpkg --configure grub-pc
Setting up grub-pc (1.98-1ubuntu9) ...
/usr/local/bin/perl: line 34: =: command not found
/usr/local/bin/perl: line 35: =: command not found
/usr/local/bin/perl: line 36: =: command not found
/usr/local/bin/perl: line 36: =: command not found
/usr/local/bin/perl: line 37: =: command not found
/usr/local/bin/perl: line 39: =: command not found
/usr/local/bin/perl: line 67: syntax error near unexpected token `{'
/usr/local/bin/perl: line 67: `while (@ARGV && $ARGV[0] =~ /^-/) {'
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 grub-pc

I suppose the problem goes with the perl, but have no idea how to figure it out.
Thanks in advance.

---

