---
title: "su / root"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by loyaleagle on 2009-04-23
I made the mistake to go into su ( created a password for it). I then rebooted. Am I still in super user or how do I sign off as super user or how do I check to see if I am still using super user privileges.

Thanks

---

### Post by duanedesign on 2009-04-23
close the Terminal window. This will end the root session.

You can tell if you are root:
```
duane@duane-laptop:~$ su
Password: 
root@duane-laptop:/home/duane# 
```

top one not root, bottom one root. Top one I am looged in as duane on duane-laptop. Bottom one I am root logged on to duane-laptop. Also notice  the dollar sign for normal user and number symbol for root.


Disabling your root account
	

If for some reason you have enabled your root account and wish to disable it again, use the following command in terminal...
	
```
passwd -l root
```
-
-

---

### Post by Hospadar on 2009-04-23
You'll only be root if you sign in as root, so if you just booted up normally and logged in with your normal username, you're not root, if you want to test, you can try making an empty folder or something in a root-only area like /usr

If that fails, you are not root, all good, if you are, there's some wierdness happening and we'll have to further investigate.

If you set a password for root, you may want to unset it, so that no-one can log in as root (although you'll still be able to use sudo, the default for ubuntu is no root password)

[http://blog.sushis-hideout.org/2008/11/18/setunset-your-ubuntu-root-password/](http://blog.sushis-hideout.org/2008/11/18/setunset-your-ubuntu-root-password/)

sudo passwd -l root

That command will unset (lock) the root password.

man passwd

for more info on what exactly goes on

---

