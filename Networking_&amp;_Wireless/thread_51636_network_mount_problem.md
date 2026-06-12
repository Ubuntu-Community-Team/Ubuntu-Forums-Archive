---
title: "network mount problem"
date: 2005-07-24
forum: Networking &amp; Wireless
---

### Post by synaptic revolt on 2005-07-24
I have my mp3s on an XP box on the network mounted as /media/mp3. After a while, I can't access the directory anymore. Well, I guess I can access it, but I get I/O errors when I ls it. I also can't remove it, I get a "Device or resource busy" message.

What gives?

---

### Post by varunus on 2005-07-24
You're using samba to mount it, right?  I'm assuming with "smbmount?"  When you try to unmount, is there still an application open that was using the /media/mp3 folder?  Like, did you leave your music player open?  Even if you're not playing anything, it might cause problems...

What music player do you use, also?

---

### Post by synaptic revolt on 2005-07-25
[QUOTE=varunus]You're using samba to mount it, right?  I'm assuming with "smbmount?"  When you try to unmount, is there still an application open that was using the /media/mp3 folder?  Like, did you leave your music player open?  Even if you're not playing anything, it might cause problems...

What music player do you use, also?[/QUOTE]

I'm just using mount, from [http://www.ubuntuguide.org/#mountunmountnetworkfolders](http://www.ubuntuguide.org/#mountunmountnetworkfolders) . I'm pretty sure nothing is using it, unless nicotine isn't exiting properly or something. The box is being used as a webserver and for file sharing.

---

### Post by gruepig on 2005-07-26
Are you cd'ed into /media/mp3 when you are trying to unmount it?  That's one of the most common causes for "Device or resource busy".  You can also use the command 'lsof' to see what's using the mounted filesystem.

---

