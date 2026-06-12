---
title: "ssh and sshfs, disappearing folders"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by nac.est on 2009-01-19
I had never used ssh before, but I tried using it to connect my desktop to my laptop, both running ubuntu 8.10. The user name on both is "marco".
Following some guides, this is what I did:

```
1) "invoke-rc.d ssh start" on the laptop
2) "ifconfig eth0 192.168.12.10" on the laptop
3) "ifconfig eth0 192.168.12.11" on the desktop
4) "ssh -X marco at 192.168.12.10" on the desktop
```

Then, having installed sshfs, working on my desktop:

```
5) sudo mkdir /media/laptop
6) sudo chown marco:marco /media/laptop
7) sudo adduser marco fuse
8) sudo chown root:fuse /usr/bin/fusermount
9) sudo chown root:fuse /dev/fuse
10) sudo sshfs -o transform_symlinks marco@192.168.12.10:/home/marco/ /media/laptop/
```

At this point the file system was mounted. So I could do:
```
gksudo "nautilus --browser"
```
and browse the files on my laptop.

After copying some things from laptop to desktop, I tried browsing the laptop's Documents folder, and discovered it was not there any more! Also the Pictures and Videos folders have disappeared, while all the other folders and files are there...
Those folders are not there even if I look directly on the laptop, and rebooting has no effect.

So, why have my files been deleted? It shouldn't be an stupid error on my part, because I didn't delete anything at all through sshfs, only copied.
Maybe there was a conflict between the two identically named "marco" users? Nothing else comes to mind...

Sorry for the long post, and thanks in advance for the help.

---

### Post by nac.est on 2009-01-20
I've realised that also some other files are missing, without an apparent logic.
I'd like to understand the cause of the problem, because I'm afraid of connecting the 2 pc's again... also, it'd be nice to have those files back!

---

### Post by emarkd on 2009-01-20
Ok, I'll try to help if I can.  I use sshfs between my laptop and server and it works great for me.

First, backup your files.  I don't know how you could've lost some, but I'd make a backup anyway.

Second, can you simply ssh from the desktop to the laptop?  If so, the laptop is correctly configured and there's nothing else to do there.  That's the beauty of sshfs - all you need on the server is ssh access.

Third, try mounting the remote folder using this commandline:

```
sudo sshfs marco@192.168.12.10:/home/marco/ /media/laptop/ -o idmap=user -o allow_other -o uid=1000
```

That's assuming that 1000 is your uid on the desktop.  It is if that's the username you made when you installed Ubuntu.  You can make sure by running 'id' from the terminal.

Now see what you've got - and don't use gksu to launch nautilus.  You should be the owner of the file and have full access to them, so just launch nautilus from the accessories menu.  Never use gksu on nautilus unless you're SURE you need it.  One slip of the delete key and you could be very screwed.

One note:  there's a known bug between nautilus and sshfs in 8.10.  You'll be able to read/delete/rename files but not write because nautilus mistakenly thinks the remote drive is full.  You can fix this by upgrading to the newest version of sshfs, but it's not packaged yet so you'll have to build it from source.  If you don't want to do this, you can still write to the laptop but you'll have to use 'cp' from the terminal.

---

### Post by nac.est on 2009-01-22
emarkd, thanks for the detailed reply!

I won't be at home for the next few days, so I'll try this when I get back.

I used gksudo for nautilus because it wouldn't let me browse the remote folders otherwise. I'll do it with the options you said next time.

---

