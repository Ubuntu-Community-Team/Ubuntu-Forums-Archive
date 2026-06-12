---
title: "Mounting NFS over xisiting directory"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by Aetherius on 2008-10-21
Just a question of curiosity.

If i mount a networked directory (eg my /home stored on a server at work) to my laptops home directory (over the top of the existng home directory) what exactly happens?

In practice, its like your home vanishes replaced with the networked folder, to reappear at unmount.

I'm guessing the inode for /home just points to the nfs share rather than at the location on disk that my home is stored?

Any input is greatly appreciated :)


(Sidenote: the reason I'm so curious is that I could set up my /etc/fstab and auto mount this "home", which would effectively mean, my laptop would be completely different at home and at work.)

---

