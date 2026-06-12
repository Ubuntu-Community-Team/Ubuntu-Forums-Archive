---
title: "login issue!"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by kedarbhatia on 2009-09-02
I have the  latest ubuntu release installed. 
unfortunately i happen to misplace my username  and password.
but i do have the root login and password,
               1. so i logged in from command line as root and did startx.the desktop shows up but mouse and keyboard dont seem to work.
                2. then i created anew  user by adduser command ,and then tried to login with this account. But even this failed and i got some error message about the /usr/user home directory .
what do i do ,
Do i reinstall my os ?

---

### Post by nothingspecial on 2009-09-02
What was the error message?

---

### Post by nhasian on 2009-09-02
well you can see what users the system has with this command:

```
cat /etc/passwd
```

once you find the username you can reset the password with this command:

```
sudo passwd username
```

substitute username with the name of the user whos password you need to reset.

---

### Post by kedarbhatia on 2009-09-02
ok. i reset the password for the username (as recommended )but problem still persists .

i tried to login with the new password and i get ..
 following  errors:

1.users HOME.dmrc file is being ignored.This prevents the default language from being saved .File should be owned by the user and have 644 permission .Users $ HOME directory should be owned by user and not writable by others .

when i say ok to this error...i get one more...

2.could not update the ICauthority file /user/home.ICEauthority 

i say ok to this error...i get one more...


3.Ther is a problem with config server (/usr/lib/libconf2-4/gconf-sanitycheck-2exited with status 256)

i say ok to this error...i get

a blank desktop with no icons..:confused:

---

### Post by nothingspecial on 2009-09-02
```
chown -R username:username /home/username
```
```
chmod 644 /home/username/.dmrc
```
```
chmod 644 /home/username/.ICEauthority
```

should do the trick.

obviously use your username.

You have to do this from the recovery shell. Press escape when you see grub reloading after restarting.

---

### Post by kedarbhatia on 2009-09-02
ok..

i  changed the ownership & modes using the series of commands u suggested.

the first error doesn't show .

the second & third are still there along with 2 other errors...
they are as follows:

4. Nautilus could not create the following folders:
/user/user/desktop,   /home/user/.nautilus .
before running nautilus please create these folders or set permissions such that nautilus can create them.

5.Error trying to start screensaver .Falied to change the dir /home/user 
(permission denied ) screensaver will not work in this session

....

---

