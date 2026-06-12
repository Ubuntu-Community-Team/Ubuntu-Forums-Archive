---
title: "Remote Desktop"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by Diametric on 2009-12-02
So, I'm working my way through a beginners Linux book and would like to be able to continue my lessons while at work.  At work, I have an XP Pro set up and at home a Ubuntu 9.10 laptop.  How can I access a shell from work?  At home, I have a 128 WEP wireless network - work is a typical corporate network setup.  What securty measures should I observe?  I've got plenty of network experience, just never between Linux and Windows via the public internet.  Thanks in advance.
 
-Diametric

---

### Post by earthpigg on 2009-12-02
> How can I access a shell from work? 

ssh on your ubuntu machine, PuTTY on your windows machine, port forwarding on your router at home.

this is the guide that i used when i first decided to give ssh a shot: [http://wiki.archlinux.org/index.php/SSH](http://wiki.archlinux.org/index.php/SSH)

replace:

pacman -Sy openssh
with
sudo apt-get install ssh

and dont worry about the daemon stuff, ubuntu does that for you. install ssh, configure /etc/ssh/sshd_config, and restart.

---

### Post by earthpigg on 2009-12-02
o, and some ISP's block port 22 to make you think you need to pay for a 'business' account or some rubbish.

use some other random port.

---

### Post by Diametric on 2009-12-02
Cool.  Thanks for the reply.  I'll give it a whirl and see what happens.  If I get it to work, I'll post as such so others may beifit.

---

