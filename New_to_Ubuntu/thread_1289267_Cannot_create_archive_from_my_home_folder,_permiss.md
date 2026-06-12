---
title: "Cannot create archive from my home folder, permission denied."
date: 2009-10-12
forum: New to Ubuntu
---

### Post by philinux on 2009-10-12
Right click on my home folder, select create archive.


```
An error occurred while adding files to the archive.

Permission denied
```

Very odd.

---

### Post by MelDJ on 2009-10-12
maybe hidden protected files in it?

---

### Post by philinux on 2009-10-12
It does not list any files. I tried running nautilus from terminal but no errors showed up. Any file in your home should have the correct permissions. There are thousands of files.

---

### Post by keplerspeed on 2009-10-12
Ah, thats because home is actually has root permissions. Just that folder. Right click, permissions to see. /home is root but /home/phil is yours. So was it the home folder or phil folder?

---

### Post by MelDJ on 2009-10-12
hm..mine doesn't

---

### Post by philinux on 2009-10-12
> **keplerspeed said:**
> Ah, thats because home is actually has root permissions. Just that folder. Right click, permissions to see. /home is root but /home/phil is yours. So was it the home folder or phil folder?

/home/phil

---

### Post by keplerspeed on 2009-10-12
Ah ok. How about creating an archive via the terminal, and see if you can get an error that way?

And ensure thunderbird or other apps are closed, I have had issues copying .mozilla folders etc if the app is running.

---

### Post by philinux on 2009-10-12
No errors, so far, using tar from terminal.

---

### Post by pedro3005 on 2009-10-12
Can you create files at your desktop?

---

### Post by philinux on 2009-10-12
> **pedro3005 said:**
> Can you create files at your desktop?

Yep no problems.

---

### Post by keplerspeed on 2009-10-12
When in home folder try a:
```

ls -l -a

```
Scan through as see if anything has incorrect file permission, ie belonging to root!

---

### Post by philinux on 2009-10-12
Yep been looking through the permissions.

Couple are root.

drwxr-xr-x  5 root   root      4096 2009-03-05 22:55 ..
-rw-r--r--  1 root   root      1137 2009-04-04 15:06 Desktopxorg.conf_backup

These could be the problem. The tar command got the permission denied error too.

Deleted the Desktopxorg.conf_backup file.

What the heck are the ..s

---

### Post by keplerspeed on 2009-10-12
Quite likely the problem. Or you could just create the archive as root, leaving everything as is.

---

### Post by philinux on 2009-10-12
> **keplerspeed said:**
> Quite likely the problem. Or you could just create the archive as root, leaving everything as is.

The only thing that was root now was the examples folder. Changed those permissions and still get permission denied.

Heck this my user folder.

---

### Post by philinux on 2009-11-02
Bump

---

### Post by philinux on 2009-11-03
Anyone sorted this?

---

### Post by whitethorn on 2009-11-03
Well whenever I tar my home folder I usually do it from the terminal as root with a preserver ownership flag.  You might want to try doing that.

```

sudo -i
cd /home
tar -cpzvf phil.tar.gz phil/

```

I think that should be about right.

---

### Post by Mud.Knee.Havoc on 2009-11-03
Where are you trying to save the archive?  Not in your home directory, I hope...

---

### Post by philinux on 2009-11-03
> **Mud.Knee.Havoc said:**
> Where are you trying to save the archive?  Not in your home directory, I hope...

Trying to save the archive to my desktop. It fails with the error in the first post after about 10 seconds. But no explanation is given even running it from terminal.

---

### Post by Niniel on 2009-11-03
Uhm, doesn't that mean that you *are* trying to save it to the Home directory? After all, Desktop is a subfolder of /home/your name...

---

### Post by philinux on 2009-11-03
> **Niniel said:**
> Uhm, doesn't that mean that you *are* trying to save it to the Home directory? After all, Desktop is a subfolder of /home/your name...

Were should I save it too?

I know what the previous poster means as /home is owned by root. But my desktop is within my user therefore there should be no permissions problem.

---

### Post by whitethorn on 2009-11-04
Have you tried running the commands I gave you?  If you did, it should've created a file called phil.tar.gz in /home/.  You can then chown the file and move it wherever you want.  

sudo -i logs you in as root, and the -p in tar means keep the permissions and file ownership so your homefolder will be archived in full with the proper permissions so root remains root and your user remains your user.

---

### Post by philinux on 2009-11-05
> **whitethorn said:**
> Have you tried running the commands I gave you?  If you did, it should've created a file called phil.tar.gz in /home/.  You can then chown the file and move it wherever you want.  

sudo -i logs you in as root, and the -p in tar means keep the permissions and file ownership so your homefolder will be archived in full with the proper permissions so root remains root and your user remains your user.

I gave up.

I have a second hard drive I use for testing new versions of ubuntu.

So I just used nautilus, without gksudo and copied everything over, no permission problems at all using that.. Re-installed karmic to disk 1 and copied stuff back the same way. All up and running with ext4 and grub2.
Thanks anyway.

---

### Post by 3rdalbum on 2009-11-05
You're trying to create an archive of:

/home/phil

And you're trying to create it in this directory:

/home/phil/Desktop

I'm sure there's a problem with this somewhere...

---

### Post by philinux on 2009-11-05
> **3rdalbum said:**
> You're trying to create an archive of:

/home/phil

And you're trying to create it in this directory:

/home/phil/Desktop

I'm sure there's a problem with this somewhere...

Sure is. I'll try to set the destination as my user on disk 2.

Be right back

---

### Post by philinux on 2009-11-05
Set destination as disk two. Error pops up after about 10secs

---

### Post by COKEDUDE on 2011-06-09
I also have this problem.

---

### Post by jtarin on 2011-06-09
> **whitethorn said:**
> Well whenever I tar my home folder I usually do it from the terminal as root with a preserver ownership flag.  You might want to try doing that.

```

sudo -i
cd /home
tar -cpzvf phil.tar.gz phil/

```

I think that should be about right.Works for me.

@philinux...maybe you have an app writing a log. Try logging out and switch to another terminal.

---

