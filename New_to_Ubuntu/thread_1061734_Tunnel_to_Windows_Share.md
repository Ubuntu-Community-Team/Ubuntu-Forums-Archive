---
title: "Tunnel to Windows Share"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by horizonuser on 2009-02-06
Is it possible to ssh from ubuntu to a Windows share? I have a Ubuntu box in the office along with many windows servers. When I am out of the office I ssh in from my ubuntu laptop and then tunnel RDP to the Windows boxes. I would like to be able to mount a drive to a windows share over the same ssh connection too.

I tried adding a dummy interface to my ubuntu laptop (127.0.0.2) then configuring putty to forward 127.0.0.2:139 and 127.0.0.2:445 to the remote windows share but I can't get connected.

Can this be done? Am I doing something newbie'ish!!

---

### Post by taseedorf on 2009-02-06
well, yes it IS possible to do this, however, I'm not sure why one would take this approach when there are much better ways to access your windows shares remotely...

ANYWAYS....

have your ubuntu box at work mount the windows shares.......when you ssh to the box at work, you should be able to access the windows shares....

on your ubuntu box at work edit /etc/fstab

and add


<server>:</path/of/dir> </local/mnt/point> ntfs3g <options> 0 0

OR

You can also use shfs for this; it will let you mount a directory on one computer on the other using ssh. There's a howto in the Tips and Tricks forum on how to install shfs; here's some paraphrasing:

Open a terminal, type:

sudo apt-get install shfs-source shfs-utils
sudo module-assistant build shfs
sudo module-assistant install shfs
sudo chmod a+s /usr/bin/shfs*


shfs is now installed. To mount a folder on the other computer, you can use the command:

shfsmount username@othercomp:/path/to/wanted/folder /directory_to_mount_in


If you want to do this on bootup, add the following line to the end of your /etc/fstab file:

username:password@othercomp:/path/to/wanted/folder /directory_to_mount_in shfs defaults 0 0


Careful with storing your password in the fstab file though. You may want to use passwordless authentication for ssh; look that up on Google (you'll have to generate a key for the computer).

---

