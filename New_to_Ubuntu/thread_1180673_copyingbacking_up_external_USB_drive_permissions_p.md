---
title: "copying/backing up external USB drive: permissions problems"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by rocka on 2009-06-07
Hi everyone,

I have a friend who is a drummer. He bought a laptop with Vista on it and now wants to run XP on it instead. He gave me the HDD out of his laptop so I can copy it to my larger HDD for backup in case something goes wrong.

Trouble is, only some directories get copied, some fail with a permissions error.

How can I change the permissions of the whole drive so I can copy every single file and keep the directory structure intact?

thanks in advance for your help ;)

---

### Post by kpkeerthi on 2009-06-07
What type of filesystem it has?

---

### Post by rocka on 2009-06-07
> **kpkeerthi said:**
> What type of filesystem it has?

I don't know: whatever Vista creates these days. I don't have much to do with windows unless I can help it. This one's a "mates rates" job. . .

---

### Post by kpkeerthi on 2009-06-07
You need a tool called ntfs-config. You can find some intructions (its for feisty though but the principle is the same for later Ubuntu versions) here: [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

---

### Post by theozzlives on 2009-06-07
Have you tried using sudo yet? Vista comes with NTFS.

---

### Post by kayvortex on 2009-06-07
Vista will have ntfs wont it (based on the principle that Vista is just XP with a new graphics theme)? And, if I'm reading the situation right, you're copying the files over by mounting both in your ubuntu-box, so ntfs-3g will already be installed and configured correctly, surely?

If you're the one mounting it, you should be able to control what permissions you have. Take a look and see what permissions you do have on the disk first:
```
ls -l /media
```
or /mnt if that's where it's mounted.

Also, bear in mind that if you're copying to an eternal hard drive, then it'll probably be formated as vfat, so that means no files over 4Gb!

---

### Post by rocka on 2009-06-07
> **theozzlives said:**
> Have you tried using sudo yet? Vista comes with NTFS.

No, not yet - I'm not confident using sudo without knowing what it's going to do [I got bitten once like that before...] So far it's just been drag'n'drop...

---

### Post by theozzlives on 2009-06-07
> **rocka said:**
> No, not yet - I'm not confident using sudo without knowing what it's going to do [I got bitten once like that before...] So far it's just been drag'n'drop...

sudo will give you the permissions that you need:
```
sudo cp -rv /source /destination
```

---

### Post by rocka on 2009-06-07
> **kpkeerthi said:**
> You need a tool called ntfs-config. You can find some intructions (its for feisty though but the principle is the same for later Ubuntu versions) here: [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

Hi,
that didn't seem to do anything, I ran the command listed on that page
sudo apt-get install ntfs-config
but it didn't create a new menu item like it says it would in the picture on that page...

---

### Post by kpkeerthi on 2009-06-07
May be logout and log back in so the panel refreshes. You could just run it using **ntfs-config** command in a terminal or ALT + F2.

---

### Post by rocka on 2009-06-07
Hi all,
and thanks for your quick replies...

this is getting weirder all the time.
I ran ntfs-config in a terminal and it flashed an error message too quick to see then disappeared.

Now, the USB drive is not seen, not by Nautilus or by the terminal:


```
merlin@merlin-desktop:~$ ls -l /media
total 4
lrwxrwxrwx 1 root root    6 2009-02-09 18:24 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-02-09 18:24 cdrom0
merlin@merlin-desktop:~$
```

---

### Post by JCoster on 2009-06-07
Was mounting the drive successful?  You need to mount the drive before it will be shown by that command.

---

### Post by rocka on 2009-06-07
I guess it must have been one of those "bad timing" things - it seems the external case I was using has stopped working. I've tried two different drives in it, including one that was working fine before, but now the computer doesn't even recognize that it's connected.

Now I've just got to cross my fingers and hope that the HDD still works when it goes back in the laptop...

That won't be till next weekend, so I guess I'll have to wait and see.

:-|

---

