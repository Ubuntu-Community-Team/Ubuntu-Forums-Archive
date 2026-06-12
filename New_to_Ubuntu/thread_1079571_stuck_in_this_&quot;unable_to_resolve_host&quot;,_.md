---
title: "stuck in this: &quot;unable to resolve host&quot;, yet cannot edit /etc/hosts/"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by dcparham on 2009-02-24
stuck in this: "unable to resolve host insidecsh2", so i try to edit /etc/hosts/, yet cannot save changes to /etc/hosts/ - it says i lack permissions. so i try to change ownership via the cmd line "sudo chown webadmin /etc/hosts/" and i get 

"sudo: unable to resolve host insidecsh2
sudo: /etc/sudoers is mode 0755, should be 0440"

ALSO, when i use gksudo gedit /etc/hosts in the terminal - it pauses, then does nothing/goes right back to cmd line in the terminal.

what is the best way to approach these simple things that do not work? i'll feel every bit of help you provide, for i am an impressionable noob.

---

### Post by sisco311 on 2009-02-24
[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

---

### Post by taurus on 2009-02-24
The name of your machine, /etc/hostname, should be the same as in /etc/hosts.  Otherwise, sudo won't work and you are locked out of root privilege.

You need to boot into recovery mode from GRUB menu and get to root shell.  Make your correction from there.

---

### Post by dcparham on 2009-02-24
thx for your [plural] help! the instructions still resulted in getting the "unable to resolve hostname insidecsh2" during the recovery mode, but the "chmod 0440 /etc/suders" did work; after rebooting, in the terminal, "sudo chmod -R u+rw,g+rw /etc/hosts" wouldn't even see the file; had to "sudo cd /etc" - then "gksudo gedit hosts" and was able to change the line from 'a' to 'b':
'a'- 127.0.0.1 insidecsh2.companydomainname
'b'- 127.0.0.1 insidecsh2

now, the terminal works fine... and so proceeding to the next hurdle.  thx much!!

---

### Post by Claus7 on 2009-02-24
Hello,

I think that what you are trying to do is to alias hosts. No?

This link may help you:
[http://ubuntuforums.org/showthread.php?t=753026](http://ubuntuforums.org/showthread.php?t=753026)

Regards!

---

### Post by dcparham on 2009-02-27
thx, Claus7 - was not deliberately trying to alias a host, though not sure exactly what that means beyond "giving it a name other than its actual machine name.", if that's even correct in the first place.  at face value, i was simply trying to do something that kept crashing because of the hostname error.  thx for your comment though;)

---

### Post by Claus7 on 2009-02-28
Hello,

I thought that your problem had to do with not giving in the right place the right arguments. Yes, you are correct. That way you can connect to a host by giving only a name after the ssh command. Glad you solved your issue.

Regards!

---

