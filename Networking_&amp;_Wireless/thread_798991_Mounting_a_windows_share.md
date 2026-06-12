---
title: "Mounting a windows share"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by lowebb on 2008-05-18
Not specific to Mythbuntu, but if just happens there is no 'handy' network places graphical viewer in it. 

How do I mount a windows share via a terminal? I thought 

sudo mount -t smbfs -o username=xxxx,password=yyyy //WindowsShare/Videos /home/mythtv/videos/WindowsShare

should work but I'm getting a 'check the share is available message'

Appreciate any help!

Exact error is...
mount: wrong fs type, bad option, bad superblock on ......

---

### Post by jetsam on 2008-05-18
You can get past that error message by installing the smbfs package.

```
sudo apt-get install smbfs
```

You may also need to install winbind to be able to reference netbios names from the command line.  

I'd also suggest you use **-t cifs** instead of **-t smbfs**, which is deprecated.  

For more details, there's a good how-to by Dmizer on mounting with cifs here:
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

Note the part of the how-to on modifying nsswitch.conf in the pre-work section.  You'll need to do this if you're installing winbind for the first time.

---

### Post by lowebb on 2008-05-19
Cool mate, cheers for the help. I hope this missing package is the issue but it seems strange that I'm able to view shares on my Windows computer from the Mythbuntu server but not able to do the reverse. I would have thought that both were capable without additional package installs

---

### Post by Iowan on 2008-05-19
[Here]("http://ubuntuforums.org/showthread.php?t=800313&highlight=cifs") is another option I "discovered" today.

---

