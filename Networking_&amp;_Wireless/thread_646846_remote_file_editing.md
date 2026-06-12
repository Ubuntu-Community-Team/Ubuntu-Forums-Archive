---
title: "remote file editing"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by Jordanwb on 2007-12-21
I have proftpd and openssh installed and it's working but I don't like using putty and nano to edit my PHP files on Server 7.10 Is there some kind of program I can install to be able to remotely edit files using FTP or some other protocol?

---

### Post by heindsight on 2007-12-21
One option would be to use sshfs.
this allows you to mount a directory from the remote server (which is running sshd). 
Once you've done that, you can use <insert favourite text editor here> to edit your files.

Have a look at:
[https://help.ubuntu.com/community/SSHFS]("https://help.ubuntu.com/community/SSHFS") and
[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/")

---

### Post by Jordanwb on 2007-12-21
Okay I installed it okay. It gives instructions on mountinf in Linux but not for Windows.

*Edit*

I found this: [http://www.wynia.org/wordpress/2007/02/08/sshfs-on-windows-via-samba-shares-on-ubuntu-vmware/](http://www.wynia.org/wordpress/2007/02/08/sshfs-on-windows-via-samba-shares-on-ubuntu-vmware/) would that work for me?

---

### Post by heindsight on 2007-12-21
oh, didn't realise you were trying to do it on a windows machine :?
I'm afraid I don't know how to do *anything* in in windows, :redface:
but that vm approach looks like it should work. I would tend to agree with the person who
commented that it seems like overkill though. perhaps someone who knows something about 
windows could suggest a simpler solution...

---

### Post by Jordanwb on 2007-12-21
It was my fault because it didn't specify I was using Windows. I looked at vmware but that looks to complicated. If anyone can confirm that VMware will do what I need I'll install it.

---

