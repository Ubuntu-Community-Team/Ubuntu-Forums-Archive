---
title: "Fstab help. Cant mount SMB shares with &quot;Spaces&quot; in the share names."
date: 2005-04-17
forum: Networking &amp; Wireless
---

### Post by MetalMusicAddict on 2005-04-17
Here is my current fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb5       /media/RipTemp    ntfs    umask=0222      0       0
/dev/hdd1       /media/Downloads    vfat        umask=000       0       0
//192.168.1.103/MP3s     /media/MP3s  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.103/Back-Up     /media/Back-Up  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
```
Heres what I was tryin to do:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb5       /media/RipTemp    ntfs    umask=0222      0       0
/dev/hdd1       /media/Downloads    vfat        umask=000       0       0
//192.168.1.103/Mp3s     /media/MP3s  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.103/Back-Up     /media/Back-Up  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.103/Bittorrent Server     /media/Bittorrent  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.103/Full Movies     /media/Movies  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.103/More Movies     /media/MoreMovies  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.103/Video (V)     /media/Video  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
```

Now "MP3s" and "Back-Up" get mounted fine but the shares with spaces in the names do not. Any ideas?

Also right now "Downloads" and "RipTemp" are local drives and dont get mounted in "Computer" all the time. Their in /media just not "Computer"

---

### Post by speedman on 2005-04-17
You have to escape the spaces with a backslash.

Examples:

//192.168.1.103/Bittorrent\ Server
//192.168.1.103/Full\ Movies
//192.168.1.103/More\ Movies

HTH


Regards,

SM

---

### Post by MetalMusicAddict on 2005-04-17
When I changed the fstab to this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb5       /media/RipTemp    ntfs    umask=0222      0       0
/dev/hdd1       /media/Downloads    vfat        umask=000       0       0
//192.168.1.103/Mp3s     /media/MP3s  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.103/Back-Up     /media/Back-Up  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.103/Bittorrent\ Server     /media/Bittorrent  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.103/Full\ Movies     /media/Movies  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.103/More\ Movies     /media/MoreMovies  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.103/Video\ (V)     /media/Video  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
``` 
I got this:
```
sudo mount -a
[mntent]: line 12 in /etc/fstab is bad
[mntent]: line 13 in /etc/fstab is bad
[mntent]: line 14 in /etc/fstab is bad
[mntent]: line 15 in /etc/fstab is bad
```

---

### Post by MetalMusicAddict on 2005-04-18
I noticed when I browse the shares it looks like this "Video%20(V)" I tried that in the fstab. That didnt work either. :(

---

### Post by PeterD on 2005-04-19
[QUOTE=MetalMusicAddict]I noticed when I browse the shares it looks like this "Video%20(V)" I tried that in the fstab. That didnt work either. :([/QUOTE]
 Try using doublequotes instead of \  ie //192.168.1.103/"Full Movies"  or you might need double back quotes like this //192.168.1.103/Full\\ Movies

---

### Post by MetalMusicAddict on 2005-04-19
[QUOTE=PeterD]Try using doublequotes instead of \  ie //192.168.1.103/"Full Movies"  or you might need double back quotes like this //192.168.1.103/Full\\ Movies[/QUOTE]
No Go. Weird. This seems like this would be common. Having a "Space" in a sharename.

---

### Post by speedman on 2005-04-19
From man fstab on a Ubuntu box:

If the  name  of  the  mount point contains spaces these can be escaped as ‘\040’.

In light of that perhaps this is worth a try:

//192.168.1.103/Full\040 Movies


Regards,

SM

---

### Post by MetalMusicAddict on 2005-04-19
"//192.168.1.103/Full\040 Movies" <- Didnt work

"//192.168.1.103/Full\040Movies" <- Did Work

That "space" after the zero was'nt needed. Thanx a bunch guys. :)

---

### Post by speedman on 2005-04-19
Good deal.  Glad to hear it worked out for you.


Regards,

SM

---

### Post by Mr. Electric Wizard on 2005-06-25
Hey man, you gotta put the whole path "//path/to/share name" in double quotes.

---

### Post by examancer on 2006-04-27
[QUOTE=Mr. Electric Wizard]Hey man, you gotta put the whole path "//path/to/share name" in double quotes.[/QUOTE]

This is incorrect. The only correct answer was using the /040 escape sequence instead of a space. I can verify that this does work...

//exa01/D\040Drive  /home/examancer/ddrive  smbfs  guest,uid=1000  0  0

the above line is from my working /etc/fstab

---

