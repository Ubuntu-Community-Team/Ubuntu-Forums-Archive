---
title: "Recover user profile"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by dippyjax on 2010-01-23
I'm very new to Ubuntu and I have fallen at the first hurdle!  I have deleted the main user and need to get it back.

I started with @louise and when I added a new user profile, I accidently deleted the main one, I now can't get to any of the @louise files and can't set up a new user with that name as one already exists?! :confused:

Thanks,

---

### Post by Barriehie on 2010-01-24
Once logged in, as any user, from the terminal:
```

cd /home
ls

```
and see if the deleted user still has a directory and IF it has any files in it.  I've only deleted a user once so I'm a bit rusty on the state of the directory after user deletion.  If the files are there you'll probably have to be root to have access to them and you'll have to change the owner:group permissions for the new user to use them.  You'll have to copy/move them over to the new user profile.

HTH,
Barrie

---

### Post by nothingspecial on 2010-01-24
There are a number of ways you can go about this

The easiest one is to create a new user and copy the files across. 

Reboot and hold down escape and login to a root recovery shell.

```
adduser louise 
usermod -G adm,dialout,cdrom,audio,fuse,plugdev,admin -a louise
exit
```

Login as louise
```

gksudo nautilus /home/@louise
```

copy all the data you want across to /home/louise then transfer ownership to louise

```
sudo chown -R louise:louise /home/louise/
```

Your done.

When you are comfortable and sure you have everytthing you need you can delete the @louise home directory.

There is a way to recover @louise but I am unsure of the exact syntax. Feel free to wait for that answer before you do this.

---

