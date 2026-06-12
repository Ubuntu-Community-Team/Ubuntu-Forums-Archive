---
title: "Copying files to windows box - Could not change permissions for"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by robertpolson on 2007-01-27
Whenever I copy a file to a windows samba shared folder,

I get a message:

Could not change permissions for 

"file name that I just copied" 

I am just a Linux noob and can only assume that when the files is copied, Linux tries to change the Permissions of that file on the windows box and cannot do that because there is no such thing in windows.

My windows samba shares are set to be "allow users to change files" and no password needed.

Is there any way to get rid of this message? Not that this is too big of a problem, it is just annoying to click "Ok" every time.

I am mounting them via cifs file system.

---

### Post by GrammatonCleric on 2007-01-27
I'm a little confused.  Is the share that you are copying to on Windows box or is the share on a linux box running samba?  SMB (Server Message Block) is what Microsoft Windows systems use.  Samba is free/open source version of SMB/CIFS that typically runs in non-Microsoft systems.

-GC

---

### Post by robertpolson on 2007-01-27
Found it. This post here fixes this:

[http://krusader.sourceforge.net/phpBB/viewtopic.php?p=8299](http://krusader.sourceforge.net/phpBB/viewtopic.php?p=8299)

"noperm" option is needed.

> This is an example from my /etc/fstab
//192.168.0.1/shared /mnt/moya cifs noperm,credentials=/root/.cifs_creds,uid=andreas,gid=andreas,iocharset=utf8 


---

