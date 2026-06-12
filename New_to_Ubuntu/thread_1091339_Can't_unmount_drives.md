---
title: "Can't unmount drives"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Captain Legless on 2009-03-09
I have a couple of my drives showing up on my desktop and I can't unmount them. When I try to do so I'm told that I'm not privileged enough to unmount them and that I need 'root' access to be able to do so.

I am the only user of this machine, (it's my home PC), and  when I installed Ubuntu I don't remember having to differentiate between myself and root.

I have tried logging out and logging back in as 'root' but I'm asked for a password...which I don't have!!

Any ideas?

---

### Post by theozzlives on 2009-03-09
```
sudo umount <mountpoint>
```

---

### Post by Captain Legless on 2009-03-09
> **theozzlives said:**
> ```
sudo umount <mountpoint>
```

Could you expound on "mountpoint" please?

Why has this action taken place, I used to be able to mount and unmount drives at will?

---

### Post by byStanderone on 2009-03-09
...if i recall it right, this issue happens between gutsy and hardy when they are both installed on the same drive, tho on different partitions. haven't encountered this problem between, hardy and intrepid. tho u can sudo umount the drive thru the terminal, code: sudo umount /media/device (sda1...or whatever ur media is)

---

### Post by mikechant on 2009-03-09
> I have tried logging out and logging back in as 'root' but I'm asked for a password...which I don't have!!

The default Ubuntu setup does not activate the root account (no password set) so this is normal.
As per the previous posts, you get root access by prefixing commands with 'sudo' and typing your normal password when prompted. If you want to run a gui program such as nautilus (the file manager) as root, use 'gksu nautilus'.

---

### Post by Captain Legless on 2009-03-10
Thanks for that info. guys. I managed to unmount one of the drives using the terminal window but I still have one that I can't unmount.

This one is one that I have renamed as Drive F, I get the message 'not found'.

In addition. when I use the command:- gksu nautilus

I get the message :- ```
Initializing nautilus-share extension
seahorse nautilus module initialized
** (nautilus:17411): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```

What does that mean?

---

### Post by Captain Legless on 2009-03-11
Any helpers?

---

### Post by kpatz on 2009-03-11
Type "mount" by itself in a terminal window, see what you get.

Find the drive in the list.  It'll look something like this:

> 
/dev/sdb1 on /media/somethingorother type ... (more stuff)


See what it's mounted on (the /media/somethingorother above), and enter this command:

> 
sudo umount /media/somethingorother


obviously replacing /media/somethingorother with whatever your mount point is...

---

