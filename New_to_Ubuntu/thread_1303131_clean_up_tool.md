---
title: "clean up tool"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by hduguay on 2009-10-27
Hi there

I was wondering if there is a clen up tool for jaunty similar to a defrag for windows.

---

### Post by |Mitch| on 2009-10-27
[http://ubuntuforums.org/showthread.php?t=140920&highlight=clean](http://ubuntuforums.org/showthread.php?t=140920&highlight=clean)

explains everything you need

---

### Post by oldfred on 2009-10-28
If you are looking for defrag that is not required in Ubuntu. Although they may add something in the future for ext4 as part of the changes to ext4 and Karmic. Files are handled totally differently in ext3 or ext4 formats and there is very little advantage to defragging.

If you do the housecleaning as Mitch's post recommends just note that if you have separately added programs via .deb files deborphan will also delete them as they were not installed thru synaptic.

---

### Post by falconindy on 2009-10-28
> **oldfred said:**
> If you do the housecleaning as Mitch's post recommends just note that if you have separately added programs via .deb files deborphan will also delete them as they were not installed thru synaptic.
That's not really accurate. The process hidden behind apt-get is simply a download and install of individual .deb files. Ever looked in apt's cache directory? It's full of .deb packages. deborphan's logic is flawed in that it can't distinguish between a package that functions alone with no outside dependencies, and an actual orphaned package. Because of this, deborphan can just as easily wrongly remove a package that Synaptic installed.

Bottom line: if you want to use deborphan, look over its output before you start yanking out packages.

---

### Post by MelDJ on 2009-10-28
for housekeeping: bleachbit, available in synaptic

---

### Post by MrWES on 2009-10-28
> **hduguay said:**
> Hi there

I was wondering if there is a clen up tool for jaunty similar to a defrag for windows.

System | Administration | Computer Janitor

I believe it's only available in versions 9.04 and up.

Bill

---

### Post by MelDJ on 2009-10-28
> **MrWES said:**
> System | Administration | Computer Janitor

Bill

don't 
see: [http://beginlinux.wordpress.com/2009/05/14/ubuntu-9-04-cleanup-with-computer-janitor/](http://beginlinux.wordpress.com/2009/05/14/ubuntu-9-04-cleanup-with-computer-janitor/)

---

### Post by tuxninja on 2009-10-28
I would recommend Ubuntu Tweak, you can find it [[COLOR="Red"]here[/COLOR].]("http://ubuntu-tweak.com/downloads")

---

### Post by QLee on 2009-10-28
[QUOTE=falconindy]That's not really accurate. The process hidden behind apt-get is simply a download and install of individual .deb files. Ever looked in apt's cache directory? It's full of .deb packages. deborphan's logic is flawed in that it can't distinguish between a package that functions alone with no outside dependencies, and an actual orphaned package. Because of this, deborphan can just as easily wrongly remove a package that Synaptic installed.[/QUOTE]

That's not really accurate either, deborphan doesn't do anything to the packages in the package cache, it looks for orphaned packages that are installed on your system. It wouldn't delete a package from the cache even if it removed it from an install.

[QUOTE=falconindy]Bottom line: if you want to use deborphan, look over its output before you start yanking out packages.[/QUOTE]

I second this very good advice.

---

### Post by philinux on 2009-10-28
Same advice for computer janitor. Look over what it's suggesting. The version in Karmic seems more mature.

---

### Post by delphiexile on 2009-10-28
Firstly there is no fragmentation with ext3/4 filesystems , so you do need to defrag. Cleaning up system will not increase speed , but only will free disk space , I read the proposed how-to , i advice you to install Bleach Bit , you can find it in Add/Remove , or by typing:

```
sudo apt-get install bleachbit
```

You''l find the software in Applications-> System Tools-> BleachBit as Administrator. Check what you want to delete .

Good luck.

---

### Post by QLee on 2009-10-28
> **delphiexile said:**
> Firstly there is no fragmentation with ext3/4 filesystems , so you do need to defrag.

You probably mean to say "don't" need to defrag.

I agree with that.

Actually, fragmentation does happen but because of filesystem design is not the problem it has been on Windows systems.

Edit: It might become more of a problem on a partition that is critically low on unused space.

---

### Post by philinux on 2009-10-28
> **delphiexile said:**
> Firstly there is no fragmentation with ext3/4 filesystems , so you do need to defrag. Cleaning up system will not increase speed , but only will free disk space , I read the proposed how-to , i advice you to install Bleach Bit , you can find it in Add/Remove , or by typing:

```
sudo apt-get install bleachbit
```

You''l find the software in Applications-> System Tools-> BleachBit as Administrator. Check what you want to delete .

Good luck.

Fro fragmentation of ext3/4 see here. It does happen. [http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

Same advice for bleachbit, be happy with what it's doing before you hit the Y key.

---

### Post by vinan on 2010-01-03
Bleach bit is an awfull tool, 
i was botherted by disk problem, in my system disk, witch is a 50gb disk
could not understand why, then i found bleach bit

freed me 23gb of junk

[IMG]http://img5.imagebanana.com/view/na1ceko3/Bleachbit.jpg[/IMG]
[http://img5.imagebanana.com/view/na1ceko3/Bleachbit.jpg](http://img5.imagebanana.com/view/na1ceko3/Bleachbit.jpg)

[IMG]http://img5.imagebanana.com/view/na1ceko3/Bleachbit.jpg[/IMG]


thanks

Vinan

---

