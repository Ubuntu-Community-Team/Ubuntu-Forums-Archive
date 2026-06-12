---
title: "Samba - going slightly mad"
date: 2005-10-16
forum: Networking &amp; Wireless
---

### Post by ubuntovec on 2005-10-16
I just want to set up home network with two computers, one with ubuntu and another with windows xp. 

problem: from my xp computer i can not access files on ubuntu. (but from ubuntu i can see files on xp). i get "you do not have permission to blabla something".

i have tried (almost) everything. what is wrong?

---

### Post by blaroe on 2005-10-16
Have you set up /etc/samba/smb.conf to specify the directory(s) you want to share?

If not, there are some useful Samba HOW-TO's in the forum to get things going.  Do a quick search here.  Find the simplest smb.conf configuration you can that serves your needs.

Hope this helps....
bl

---

### Post by wjp.reg on 2005-10-16
[QUOTE=ubuntovec]I just want to set up home network with two computers, one with ubuntu and another with windows xp. 

problem: from my xp computer i can not access files on ubuntu. (but from ubuntu i can see files on xp). i get "you do not have permission to blabla something".

i have tried (almost) everything. what is wrong?[/QUOTE]

Did you use ```
sudo smbpasswd -a user
``` to add a password for the windows user to gain access to the linux box?

---

### Post by ubuntovec on 2005-10-16
no go. could someone PLEASE post his/her smb.conf file.... thank you very much

---

### Post by shandar on 2005-10-16
Hm. This probably doesn't help very much, but when I installed Breezy I simply used the shared folders applet to chose what folders I want to share and also set up a name and workgroup. Then to access my files from windows I just click the share and logon to it with my ubuntu username and password...

---

### Post by majikstreet on 2005-10-16
[http://www.ubuntuforums.org/showthread.php?t=26438&highlight=samba+howto](http://www.ubuntuforums.org/showthread.php?t=26438&highlight=samba+howto)

Follow that to the dot.

Works great!

But, at least in my case, samba doesn't want to start a boot, so I have to do "sudo /etc/init.d/samba start" to get it up when I want to use it... If someone knows how to fix that- it'd be great :)

---

### Post by ubuntovec on 2005-10-16
now it works. i do not know why. hokus pokus. i hate that. oh, well...

---

### Post by kwaanens on 2005-10-16
[QUOTE=majikstreet]But, at least in my case, samba doesn't want to start a boot, so I have to do "sudo /etc/init.d/samba start" to get it up when I want to use it... If someone knows how to fix that- it'd be great :)[/QUOTE]

System > Administration > Services
Make sure Samba is checked to run at boot.
Hope it helps!

- Ketil

---

