---
title: "Cannot login"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by LethalLavaLand on 2009-01-18
I'm using Ubuntu Studio with WMware Workstation. Just some moments ago I installed VMware Tools. I had unpacked the install files into folder /tmp/ in my home directory. After installation I deleted the files in tmp.

I don't know if I deleted something important or if it's the VMware installation that caused the trouble but after rebooting I could no longer logg in using a normal GNOME session.

I get the error message:
-------------------------------------------------
/etc/gdm/Xsession: Beginning session startup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /mkdtemp: private socket dir: Permission denied
-------------------------------------------------


If I try to log in using failsafe gnome I get the error message:
-------------------------------------------------
Could not open or create the file "(null)"; this indicates there may be a problem with your configuration, as many programs will need to create files in your home directory. The error was "Failed to create file '/tmp/gconf-test-locking-file-RKCUNU': Permission denied" (errno = 13).
-------------------------------------------------

If i log in using "failsafe terminal"-session I get a terminal to work with; but I have no idea what I'm supposed to do.

---

### Post by hailukah on 2009-01-19
I haven't had this problem, but you may want to check that 

a.  Your /tmp directory is still there

b.  /tmp has the right permissions

c.  Your disk isn't full

To check a and b open a terminal (Applications | Accessories | Terminal) and run 
```
ls -l / 
```

You should see a line marked
```
drwxrwxrwx  35 root root  4096 2009-01-19 19:24 tmp
```

If this line is missing you then the /tmp directory has been deleted.  If the first part of the line is not drwxrwxrwx then the permissions are not correct.

To create the directory open a terminal and run
```
sudo mkdir /tmp
```

To change the permissions (which will also need to happen if you just created the directory) run
```
sudo chmod 777 /tmp
```

If the /tmp directory was present with correct permissions you may need to check if your disk is full.  A full disk can cause odd problems. Run
```
df
```
and look for a line such as
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4             10262272   6416556   3324416  66% /
```
You'll be looking for the line that has / under the column 'Mounted on'.  If the Used column is over 90% you may need to look into removing some files or getting a larger drive.

---

### Post by LethalLavaLand on 2009-01-21
Ah, thank you. I had managed to screw up the permissions.

Thanks a lot, saved my day :).

---

