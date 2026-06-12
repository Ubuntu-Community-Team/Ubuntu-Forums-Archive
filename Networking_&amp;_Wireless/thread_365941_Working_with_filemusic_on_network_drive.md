---
title: "Working with file/music on network drive"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by dtf on 2007-02-20
I have a home network with using samba.  On the network I have music files and Open Office documents as well as others.  My problem is some applications do not work well with ubuntu network management for samba.  For example, I can not seem to play my mp3 files with any of the music applictions I have available.  Another problem I have is that I can not seem to print my odt files to the network printer.  All of this works fine once I mount the samba shares but I cannot find a way to do this without writing my own short script.  Since I am not the only user of ubuntu in the house and I want to make this easy for my kids I was hoping there was a way to this provided by ubuntu or alternatively have my network drives mounted when the computer boots.

Any idea or comments.  Thanks.

---

### Post by spd106 on 2007-02-20
1) Samba shares can be mounted at boot by adding them to the /etc/fstab file. This is rather non-trivial for beginners, but if you follow a guide it should be relatively painless. See [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) for an introduction.

2) For music sharing I have found that the easiest way is to import the music into rhythmbox, then activate daap sharing. You will also need to have avahi (service discovery) running. 
Now you should be able to play music through rhythmbox on any other PC, just like Macs do with itunes.

3) I recommend using just CUPS for printing rather than involving samba, if you can avoid it.

---

### Post by dtf on 2007-02-21
spd106 - 

Thanks for the help and web site.

spd106 writes:
3) I recommend using just CUPS for printing rather than involving samba, if you can avoid it.

The reason I chose to use samba and not CUPS for printing is that my print server is build using DSL linux and the choice of printer drivers is limitted.  Also some computers are dual boot in my house so it was easier for me to load the printer drivers on each computer and have the samba print server just pass the data through to the printer.  It actually work well for me and I do not have to mess with it much.  But then again I am novice at this and I am sure there are better ways to do the job.

---

### Post by zes on 2007-02-23
about the music share problems. i´m with the same problem on a laptop.

only with vlc i can play music from a network folder (external usb disc on desktop pc)., but before play any file vlc copy it to a tmp folder on laptop, an i have to wait copy is finished for play the song. will be the same with rythmbox?, i want a appz that plays network files "on fly", like streaming, i don´t want to wait for a copy from desktop to a tmp floder on laptop, i can do it manually....

thx

---

### Post by spd106 on 2007-02-23
Yes, rhythmbox and I think a few others like banshee support DAAP (see [http://daap.sourceforge.net/](http://daap.sourceforge.net/))

It's so easy to use, it's unbelievable. Just be sure to enable 'service discovery' in the network-admin capplet or toggle the setting in /etc/default/avahi-daemon.

---

