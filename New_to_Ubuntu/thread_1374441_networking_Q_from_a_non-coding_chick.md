---
title: "networking Q from a non-coding chick"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by ZKitty on 2010-01-06
Code gives me a headache... and as I already have one going, I really don't want to make it worse. Here's my issue:

I have a netbook with Ubuntu/Gnome/etc from Dell. Nice little thing. I got it connected to my internet just fine. I also have this desktop machine. It's called a Mac. It's an older PPC running OSX 10.5.8. Also on the wireless network. 

I want them to speak to each other. Share files, etc... 

I have DL'ed Fugu on the Mac and have no clue. I DL'ed Samba, not quite. At one point yesterday (and i have no clue how the heck I got it, since I can't repeat it), I got the Mac to show folders from the NB, but I couldn't open them... 

I've gone into terminal a few times since getting the NB in September. I know i need to learn a LOT more about Linux... but I would like to just get this set up... once and for all... 

Anyone here know both systems and can help? I've perused forums and done searches, and followed various foreign tech tutorials (screencaps were in various languages, but instructions were in English). Anyone? I'm kinda more of a Right brained person, and venture over to the left side once in a while... 

Anyone?

---

### Post by LinuxRules1 on 2010-01-06
I can help you with the ubuntu system but not the mac. you can easily configure the shared folders with the samba GUI. you can install it with this command.

```
sudo apt-get install system-config-samba
```

you will have to setup your password for samba so you can do that with this command.

```
sudo smbpasswd -a username
```

then to connect to the share on the ubuntu system you type this in the address bar.

```
smb://server/share
```

---

### Post by 3rdalbum on 2010-01-06
+1 - use the 'system-config-samba' package from Synaptic Package Manager. It puts a new item into your Administration menu - System > Administration > Samba. You can use this to set up shared folders.

---

### Post by juancarlospaco on 2010-01-06
Why Samba between 2 Unix?
[Use SSH]("apt:/openssh-server") and connect using **Places--->Connect to Server--->SSH**

*Fast, Secure, Easy*
:)

---

### Post by BamBamF16 on 2010-01-06
I have an intel MacBook, but I got a program called MacFusion working.  It is based off of MacFuse, but puts a nice GUI frontend on it.  It uses SSHFS, so you have to set up an SSH server on your Linux system.  At one time I had Netatalk (Bonjour type) working as well, but it put weird stuff on my system, so I took it off.  I haven't gotten the opposite direction to work (see Mac files in Ubuntu, no need for me).

---

