---
title: "Problem with shared files in a server using samba"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by Dano18 on 2007-05-19
I have a problem accessing files on a  home server (ubuntu server) from my home computer (ubuntu) using samba.  I can connect perfectly using places>connect to server and entering windows share and all the correct logon data.  The problem comes when i try to mount the windows share (I need to do this so that amarok will be able to access the music files on the server).
     The way the server is set up, there are four logons, each with their own folder in the home folder.  Also in the home folder is a folder called allusers, which contains a folder called music, where all the music is stored.  Each user has in his folder a shortcut (this is the windows term, not sure if its the same for linux?) to the music folder.
     The way we tried to set it up, each user would be able to have his own folder, and the shared folder on the server.  This works fine, except when I go to mount my folder on ubuntu.  I can access all of my files on the home server fine except for the music folder; it gives me this error: 
```
The Link "music" is Broken.  This link can't be used, because its target "/home/allusers/music/" doesn't exist.
```
Obviously my computer is interpreting the shortcut on the server to instead mean a shortcut to my own computer.  Is there a way to fix this without completely reconfiguring how the server works with respect to users?

---

