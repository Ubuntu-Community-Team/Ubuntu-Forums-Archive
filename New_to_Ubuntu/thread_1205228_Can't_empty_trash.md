---
title: "Can't empty trash"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by Coolsaber57 on 2009-07-05
Hi all,

I cannot seem to empty my trash folder.  When I do it points to some file and says that it doesn't exist.

I've tried the command 

> 
rm -rf ~/.Trash/*

But no luck, it still says that this file doesn't exist.

Anyone encounter this before?

---

### Post by taurus on 2009-07-05
I don't think there is a ~/.Trash.  There is a ~/.local/share/Trash though.

---

### Post by wojox on 2009-07-05
Can you see the file?

---

### Post by SunnyRabbiera on 2009-07-05
Not even a trash:/ directory?

---

### Post by izizzle on 2009-07-05
Move the file from the trash into your home directory (cut, paste) and "sudo rm -rf" it from there.

---

### Post by Coolsaber57 on 2009-07-05
> **taurus said:**
> I don't think there is a ~/.Trash.  There is a ~/.local/share/Trash though.

I tried rm -rf ~/.local/share/Trash 

It still says that the trash is full and when I try to use the GUI now to empty the trash, the option is grayed out.

> **wojox said:**
> Can you see the file?

No, no files.

> **SunnyRabbiera said:**
> Not even a trash:/ directory?

Huh?

---

### Post by wojox on 2009-07-05
Ok this happened to me once open

**Application/Accessories/Terminal**

```
gksu nautilus
```

Then go to your home folder.
From View menubar select **show hidden files**
Go to .local/share/trash
You'll see two folders **files** and **info**
Open both and delete everything.
Reboot

---

### Post by Sef on 2009-07-05
> Ok this happened to me once open

**Application/Accessories/Terminal**

 	Code:
 	gksu nautilus 
Then go to your home folder.
From View menubar select **show hidden files**
Go to .local/share/trash
You'll see two folders **files** and **info**
Open both and delete everything.
Reboot

gksu is for Ubuntu and Xunbuntu.  The OP is running Kunbuntu.

---

### Post by wojox on 2009-07-05
Oh my bad so then use kdsu?
Not sure 
Didn't see they were in kubuntu

---

### Post by Coolsaber57 on 2009-07-05
> **wojox said:**
> Oh my bad so then use kdsu?
Not sure 
Didn't see they were in kubuntu

Yeah we use Dolphin here Kland, lol.

Showing hidden folders did not reveal anything though.

---

### Post by Dark006 on 2009-07-05
Try:
```
sudo rm -rf ~/.local/share/Trash/files/*
```
That should hopefully fix it, it works for me anyway.

---

### Post by Coolsaber57 on 2009-07-05
> **Dark006 said:**
> Try:
```
sudo rm -rf ~/.local/share/Trash/files/*
```
That should hopefully fix it, it works for me anyway.

Nope, still says my trash is full.

---

### Post by wojox on 2009-07-05
Do it for both folders

```
sudo rm -rf ~/.local/share/Trash/files/*
```

```
sudo rm -rf ~/.local/share/Trash/info/*
```

Then reboot

---

### Post by Coolsaber57 on 2009-07-05
> **wojox said:**
> Do it for both folders

```
sudo rm -rf ~/.local/share/Trash/files/*
```

```
sudo rm -rf ~/.local/share/Trash/info/*
```

Then reboot

Done, no change, still says trash is full :mad:

---

### Post by taurus on 2009-07-05
Post the output of this command.

```
ls -la ~/.local/share/Trash/files
```

---

### Post by Coolsaber57 on 2009-07-05
> **taurus said:**
> Post the output of this command.

```
ls -la ~/.local/share/Trash/files
```

> me@computer:~$ ls -la ~/.local/share/Trash/files
total 12
drwx------ 2 chris chris 4096 2009-07-05 22:31 .
drwx------ 4 chris chris 4096 2009-07-05 19:53 ..
-rw------- 1 chris chris   67 2009-07-05 22:08 .directory
me@computer:~$


It seems that when I try to delete larger folder (>1GB) it tells me that the Trash is full.  However, smaller files/folders will be moved to the trash.

Is it a question of Trash can size? What is the limit?

---

### Post by Dark006 on 2009-07-05
This is just a wild guess(and prolly not right), but I'm wondering if what your trying to delete is immutable. Run this:

```
lsattr ~/.local/share/Trash/files/
```

If you get anything back that looks like this
```

----i-------------- /home/blake/Desktop/new file

```
and has that lone "i", that means the file or directory is immutable and you would have to run 

```
sudo chattr -i file
```
to make it not immuatable

---

### Post by Coolsaber57 on 2009-07-06
> **Dark006 said:**
> This is just a wild guess(and prolly not right), but I'm wondering if what your trying to delete is immutable. Run this:

```
lsattr ~/.local/share/Trash/files/
```

If you get anything back that looks like this
```

----i-------------- /home/blake/Desktop/new file

```
and has that lone "i", that means the file or directory is immutable and you would have to run 

```
sudo chattr -i file
```
to make it not immuatable

I don't get anything back with that command.

---

### Post by jrox717 on 2009-07-06
> **wojox said:**
> Oh my bad so then use kdsu?
Not sure 
Didn't see they were in kubuntu
for reference, it's kdesudo

---

### Post by psycosmyth on 2009-07-06
Had similar issue, got a thread on it but was permission related. Have you tried using kdsu Konqueror instead? I ended up using another distro on usb to delete the pesky file. Good luck.

---

### Post by Coolsaber57 on 2009-07-06
> **psycosmyth said:**
> Had similar issue, got a thread on it but was permission related. Have you tried using kdsu Konqueror instead? I ended up using another distro on usb to delete the pesky file. Good luck.

Isn't Konqueror the Web browser?

---

### Post by poosietgp on 2009-07-07
Hi try installing bleachbit from synaptics if it is supported.
then run it as root and check the system checkbox (under the system option you can find vaarious stuff it can delete like temp files and trash etc. just check all the stuff you want to remove from your system.) then click on the preview button to see how many spaces you can free and to see the files it will delete. if you are satisfied with the prview go ahead and click on the delete button.

hope this helps.

you can run bleachbit via gui or command line

---

### Post by psycosmyth on 2009-07-07
> **Coolsaber57 said:**
> Isn't Konqueror the Web browser?

It's a file browser too and so is Firefox. I once had a delete issue where Dolphin wouldn't move a file but Konqueror did. Just a wild thought. Let us know.

---

