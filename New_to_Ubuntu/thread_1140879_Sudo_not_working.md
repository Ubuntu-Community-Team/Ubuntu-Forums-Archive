---
title: "Sudo not working"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by kinngg on 2009-04-28
After upgrading to 9.04 I'm facing a new problem which involves this message when i try running sudo, or try logging into root in terminal 


chilin@chilin-laptop:~$ root
The program 'root' is currently not installed.  You can install it by typing:
sudo apt-get install root-system-bin
bash: root: command not found
chilin@chilin-laptop:~$ sudo apt-get install root-system-bin
sudo: /etc/sudoers is owned by gid 1001, should be 0

---

### Post by Anthon on 2009-04-28
If you have not created a password for root, I think you should boot from CD and chown the /etc/sudoers file after mounting your root filesystem somewhere.

---

### Post by kansasnoob on 2009-04-28
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by steve101101 on 2009-04-28
change you just use chown to change the owner of that file??

---

### Post by rhcm123 on 2009-04-28
> **kinngg said:**
> After upgrading to 9.04 I'm facing a new problem which involves this message when i try running sudo, or try logging into root in terminal 


chilin@chilin-laptop:~$ root
The program 'root' is currently not installed.  You can install it by typing:
sudo apt-get install root-system-bin
bash: root: command not found
chilin@chilin-laptop:~$ sudo apt-get install root-system-bin
sudo: /etc/sudoers is owned by gid 1001, should be 0

did you chmod or chown /etc/sudoers? if so, then you should boot the recovery cd and then change the ownership to root. heck, if root owns it you can *in theory* get a root terminal (sudo -i) and change the appropriate permissions. im sensesing the recovery cd though, based on this post.

---

### Post by kansasnoob on 2009-04-28
I was serious with that link "Fix Broken Sudo" written by Aysiu!

I know it works and it's spelled out as simple as simple can be!

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Anthon on 2009-04-28
> **steve101101 said:**
> change you just use chown to change the owner of that file??
You need to do that as root, hence the suggestion to boot from a CD to do that

---

### Post by rhcm123 on 2009-04-28
You also said this happened during an update? Consider then filing a launchpad bug, as this may be distro-wide.

---

