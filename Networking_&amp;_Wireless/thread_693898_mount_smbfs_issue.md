---
title: "mount smbfs issue"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by drivel on 2008-02-11
Hi,guys

I have a home server to share files and samba is running on it.
Now,I get 2 laptops,one is running Ubuntu Gutsy and the other is running Windows XP.

On the homeserver,samba's sharing a dir name "data"
[data]
  comment = Botu Share Stuff
  broseable = yes
  path = /media/data
  writeable = yes
  public = no
  follow symlinks = yes
  wide links = yes

and in the /media/data,there is a dir named "watch" linked to "/home/botu/watch"

the problem is,when I open the share dir in Windows,I can enter dir "watch"
but when I mounted the share dir on Ubuntu,using command
"sudo mount -t smbfs //10.0.52.69/data /media/data/ -o username=botu"
I cannot enter dir "watch",it tell me  "No such file or directory"
In the smbclient,everthing works fine,how to fix that?

Best regard,
Botu.

---

### Post by ridetheteapot on 2008-02-11
this is just a guess, cause sshfs does the same kind of thing...
the link in the mounted directory point to a local link (like it actually trie to go to /home/botu/watch on the local machine). The follow symlinks option hasn't worked for me when mounting ssh shares (in fact the links disappear when using this option)
Just try to create the /home/botu/watch on the local machine an see if nautilus points you to the empty folder.

this link and quote from the post might help you out more though
[http://ubuntuforums.org/showthread.php?t=349794](http://ubuntuforums.org/showthread.php?t=349794)

> 
Samba server does not allow symlinks that refer to files
outside of the share, so in Samba versions prior to 3.0.5, most symlinks to
files with absolute paths (ie beginning with slash) such as:
ln -s /mnt/foo bar
would be forbidden. Samba 3.0.5 server or later includes the ability to create
such symlinks safely by converting unsafe symlinks (ie symlinks to server
files that are outside of the share) to a samba specific format on the server
that is ignored by local server applications and non-cifs clients and that will
not be traversed by the Samba server). This is opaque to the Linux client
application using the cifs vfs. Absolute symlinks will work to Samba 3.0.5 or
later, but only for remote clients using the CIFS Unix extensions, and will
be invisbile to Windows clients and typically will not affect local
applications running on the same server as Samba.


the last post in the thread says to set "unix extensions = no" in your smb.conf

---

