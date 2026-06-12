---
title: "/home not mounting on boot"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by Rayve on 2010-02-16
I don't know if this happens from a Menu > Restart or a total shutdown and reboot, but lately I've been at the terminal (trying to get sound working in Karmic, just did, yay!) so I've been typing "sudo reboot now" to restart.

Every time I reboot (at least in this fashion), it comes up and does a filesystem check after GRUB loads and such, and then says it is unable to mount /home and to hit Esc to enter a recovery shell.  From the recovery shell, I just hit Ctrl+D to exit and the Ubuntu splash screen comes up as normal.

Is this something I should worry about?

---

### Post by kaltoza on 2010-02-16
Good job on the sound. 
Try running this command to restart your system rather

sudo shutdown -r -t 0 now

see if this helps

---

### Post by Rayve on 2010-02-16
kaltoza,

That worked great!  No fsck on restart, and for the first time, I heard the Karmic start up sounds.  :)  Thanks!

---

