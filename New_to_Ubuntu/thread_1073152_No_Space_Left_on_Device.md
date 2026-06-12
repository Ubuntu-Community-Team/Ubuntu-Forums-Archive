---
title: "No Space Left on Device"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by expatCM on 2009-02-18
My server is starting to throw up errors along the lines of “No Space Left on Device”

The server has two hard drives.  Generally one runs the o/s and the other data backup.

How do I know which drive is getting full?  (is there a command to list or monitor this?)

With a desktop install in order to clear deleted files from the system you can empty the user trash and also clear the root trash at .local/share/trash.  This does not appear to be  the same on a server.  How do you find and fully clear deleted files on a server?

---

### Post by Rolcol on 2009-02-18
Using the rm command will unlink a file automatically.  It does not send it to a trash but rather deletes it automatically.  You can use the df command to display the size and usage of drives.

```
df -h
```

The -h flag makes the output **h**uman readable by converting the size to kilobytes, megabytes, gigabytes, etc.

---

### Post by Kain000 on 2009-02-18
> **expatCM said:**
> My server is starting to throw up errors along the lines of “No Space Left on Device”

The server has two hard drives.  Generally one runs the o/s and the other data backup.

How do I know which drive is getting full?  (is there a command to list or monitor this?)

With a desktop install in order to clear deleted files from the system you can empty the user trash and also clear the root trash at .local/share/trash.  This does not appear to be  the same on a server.  How do you find and fully clear deleted files on a server?


Well if your not using raid you should be able to see your backup HDD under places > computer as a sata or pata or scusi drive from witch you can right click and view the drive properties, 

Otherwise you could view all the mounted File systems with the Gnome system monitor  system > admin > system monitor
found under the file system tab

To see where the space is being used (graphically) on said disk, use the disk usage analyzer tool under applications > accessories

I'm sure that there is a much more elegant CLI command such as 
```
lshw 
```
or to find files larger than a given variable, 
for hardware but one for sata devices but I dont kno.

---

### Post by cariboo on 2009-02-18
A server install without the gui, you don't have a trash can, when you delete a file, you delte it, it doesn't go into a trash can.

There are couple of things you can do to clear up space on your hard drive first at the prompt type:

```
sudo apt-get clean
```

This weill clean out archived packages in /var/cache/apt/archives.

```
sudo at-get autoclean
```

removes no longer needed dependencies.

If you need a gui to manage files use sftp. Open nautilus on your desktop computer and in the address bar type:

```
sftp://user@server
```

All of the above can be done remotely, without having to hook up a monitor and keybaord to the server.

Jim

---

### Post by expatCM on 2009-02-18
amazing responses .... thank you ...  :)

I ran df -ah and it was extremely obvious where the problem is.  An instant fix got me a small amount of space.  Moving things between the drives will be this evenings challenge for a more effective solution...

sftp://user@server -- I have wondered for many months if there was anything like this ........  what a great find :)

---

