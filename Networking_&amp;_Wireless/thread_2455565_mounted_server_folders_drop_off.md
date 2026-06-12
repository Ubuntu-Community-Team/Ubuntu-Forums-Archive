---
title: "mounted server folders drop off"
date: 2020-12-22
forum: Networking &amp; Wireless
---

### Post by wobblewoo on 2020-12-22
Hello.

Im running Ubuntu 20.04.1 LTS and have mounted shares on my Unraid server (shared as SMB and NFS) using a method i found online. Im no expert but this has worked upto the latest Ubuntu update.

I used getit to edit the fstab file:
sudo gedit /etc/fstab

Then added this line for each share. Its been working for a couple of years no problems.
//192.168.0.xxx/unraidshare  /media/share  cifs  guest,uid=1000,iocharset=utf8  0  0

This works fine and i can access the share in Linux, infact ive just done it whilst typing this.

But, if i now mount the unraid share on my Mac and do anything to it, - i've just created a new empty folder, i now cant access it on my Ubuntu machine.

I get:
Oops! Something went wrong.
Unhandled error message: Error when getting information for file "/media/share": Stale file handle

And i have to reboot the Ubuntu machine to fix it.

Can anyone help with this error or with a way to mount shares automatically on reboot. Im on a private LAN, the ubuntu machine is my Plex server and the media is stored on my Unraid server.

Many many thanks.

---

### Post by #&amp;thj^% on 2020-12-22
Maybe helpful: [https://linuxhint.com/ubuntu_20-04_-mounting_nfs/](https://linuxhint.com/ubuntu_20-04_-mounting_nfs/)
One more tip if I may, **Please don't use GUI applications with "sudo" **(gedit). Quick way to get in trouble.
Use instead "sudoedit" EG:
```
sudoedit gedit /path/to/whatever
```

---

### Post by TheFu on 2020-12-22
I prefer sudoedit too.
Does sudoedit work that way?  To my knowledge, it uses either the default editor, nano, or whichever program is in the EDITOR environment variable.
```
export EDITOR=gedit
sudoedit /path/to/whatever
```

Most people wold put the export line into their "/.bashrc and forget about it. It wold work on every login as expected.

There are a few environment variables like that which seem to have been forgotten.  PAGER is another.

As for cifs mount issues, there see to be as many as their commercial NAS devices ever made, all because they run old, stripped down, samba implementations and haven't been updated in years.

If MacOS wasn't involved, I'd say to use NFS too, but uid and gid numbers need to match for client machines. To get osx and ubuntu uids to match is not something for a beginner.

---

