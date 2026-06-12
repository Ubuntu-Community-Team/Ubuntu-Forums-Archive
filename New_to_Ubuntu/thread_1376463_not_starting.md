---
title: "not starting"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by bobanshirl on 2010-01-09
I have not had any replies to my other thread ie Can I get into Ubuntu to recover my emails.I have had a few posts/threads which refer me to other threads/posts but no one,and I mean no one,has come right out with,No you cant,you will have to reinstall.Please will someone tell me then I can Reinstall.Bob

---

### Post by blazemore on 2010-01-09
Can you please tell us exactly what problem you are having?
Without that information, it is unlikely anybody here can help you!
Thanks :-)

---

### Post by abhe on 2010-01-09
> **blazemore said:**
> Can you please tell us exactly what problem you are having?
Without that information, it is unlikely anybody here can help you!
Thanks :-)


yes , try to provide some important info about the problem that you have

---

### Post by bobanshirl on 2010-01-09
Sorry I thought you knew about my other post the one previous to this one titled Wont Start,it has everything in it.

---

### Post by s.fox on 2010-01-09
Do you mean [this]("http://ubuntuforums.org/showthread.php?t=1374761") thread?

-Silver Fox

---

### Post by nothingspecial on 2010-01-09
If the contents of your email are saved to the disk then yes you can.

Down load a ubuntu live cd and boot with it.

The hard disk of your computer should appear on the desktop called volume or disk or something like that. If it`s not there have a look in your places menu.

If it`s in neither of those places then open a terminal and type ```
sudo fdisk -l
```

This will list all the disks/partitions attached to your computer with the syntax /dev/sda1 /dev/sdb1 etc etc. Decide which is your computers internal disk and then mount it.

```
sudo mkdir /media/buntu
```

```
sudo mount -t *[COLOR="Red"]type[/COLOR]* /dev/[COLOR="Red"]sdb1[/COLOR] /media/buntu
```

substitute type for the file system type ntfs, ext3 etc (the fdisk -l command will have told you)  and substitute /dev/sdb1 for the correct partition.

Then in your places menu click file system and go media > buntu and go get your emails.

---

### Post by kansasnoob on 2010-01-09
First of all did you see this:

[http://ubuntuforums.org/showpost.php?p=8627484&postcount=12](http://ubuntuforums.org/showpost.php?p=8627484&postcount=12)

I don't personally use Wubi but I've posted that link and several people have been able to get their Wubi booting.

Since I don't use Wubi I can't be sure, but I know I can access everything inside my Windows XP from my Ubuntu installation just by installing "ntfsprogs" either from Synaptic or:

```
sudo apt-get install ntfsprogs
```

**Just be warned that ntfsprogs gives you full read & write capabilities in NTFS so you can alter and destroy Windows program files, etc!**

So I would think if you properly install Ubuntu in a true dual boot that you would be able to access the files within Wubi also. I just have no idea what file names to look for and such.

---

