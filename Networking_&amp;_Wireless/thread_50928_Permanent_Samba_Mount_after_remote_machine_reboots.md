---
title: "Permanent Samba Mount after remote machine reboots"
date: 2005-07-21
forum: Networking &amp; Wireless
---

### Post by Dogmeat on 2005-07-21
Hi, I have a Ubuntu server running amuled, and I need it to save the temporary / incoming files into another machine running winxp. I mounted it with autofs, hoping it would restore the connection if the xp machine reboots, but when it does, the mount gets screwed up, i can't use it and cant umount it because its in use. 

I was wondering if there is a way to keep a share mounted all the time (except when the remote machine is rebooting of course) and remounting it when the share becomes avaliable again automatically?

On a side note, is it possible to discover what is preventing a mount from being umounted so I can kill it and umount it without having to reboot the box?

---

### Post by Hemulen on 2005-10-24
Have you tried using the timeout option and symlinks to the mountpoints?

I've been usin autofs and it works great for me. I configured 'auto.master' to run 'auto.homelan' with a timeout of 5 seconds. In 'auto.master' I point the moutpoint to '/misc' and in my 'auto.homelan' I mount a share named 'media'. I create a folder named '/homelan' and put my symlinks there 'ln -s /misc/media /homelan/media' and it has been working so far.

I tried to kill mountpoints using umount with f and l switches without any luck. This is also the only method I know to work on a laptop that switch between wired an wlan networks, I need to wait for the timeout before switching if I have touched anything on the mounted share.

---

