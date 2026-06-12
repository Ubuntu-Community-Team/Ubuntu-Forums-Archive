---
title: "Ubuntu to Mac sharing problem. (need help with mount.cifs or equivalent)"
date: 2015-02-09
forum: Networking &amp; Wireless
---

### Post by Scott_Zimmerman on 2015-02-09
I'm an ubuntu newbie. So far just about everything on ubuntu has been easier to configure than I've anticipated, except for this, which has been an unresolvable nightmare.
 
Here's what I have:

a mac mini running os x 10.6
a pc running ubuntu version 14.04

All I want to do is mount one of my mac directories on my ubuntu machine (preferably in the /mnt directory), with full access to the permissions on that directory (so commands like chmod work)
And I need that shared directory to be accessible to the web server I'm running on my ubuntu machine. For instance if the permissions on a file are rw-rw-rw it should be readable to the webserver.

Here is what I've been using: sudo mount.cifs //mac-mini.local/sharename/ /mnt/Test -o username=myusername,password=mypassword,sec=ntlmssp,gid=1000,uid=1000

(it took me a while to get that far, by the way. almost every mount.cifs example I've seen leaves off gid, and uid, which makes the permissions break,uggggghh! People who write tutorials and manual pages
sure do a bad job of explaining the importance of options.)

Anyway, with that command everything works great, at first. Permissions work like it's a local drive. the web server works just like it's a local drive..  EXCEPT there is one HUGE bizarro problem which leads to catastrophe: on my mac, the smbd process starts out as 2.5 mb in memory use (which is fine. that's nothing), but it grows and grows and grows and grows and grows the more a I access files and subdirectories... real memory and virtual memory use will grow  to 1gig and beyond, and eventually everything goes to hell on the mac. The memory is never freed. Ubuntu can sit idle for a day, and the mac is still dedicating over a gig to that share for some unknown reason.  What I have to do is umount the directory on my ubuntu machine to free the memory on the mac (that command can take like 10 minutes instead of 2 seconds), and then remount. (Incidentally, the umount command usually makes the mac use up hundreds of megabytes of extra memory before finally releasing all the memory... what in the world is it possibly doing?) I'm running some perl and fortran programs on ubuntu, so I thought maybe they were the culprits somehow, but even a bunch of simple ls commands or vi edits can make memory use on the mac jump in 5, 6, 7 megabyte increments, never to be freed up again, until i do the umount....

Is this a bug in mac smb? Or does my mount.cifs command need to be written differently? Am I leaving off a crucial configuration point?

I've noticed that if I run nautilus and do a smb mount, the file permissions don't work (the web server can't access the mount--under /run/user/1000/gvfs) and the MAC STILL uses more and more
memory the more I access the share.... So nautilus triggers that memory quirk, too...... So smb via nautilus sucks.....

If I instead use nautilus to do an ftp or afp mount, there is no memory usage problem at all (so that's a plus!), but I have the same file permissions problem. (the webserver can't see a thing, and I've tried giving ultimate permissions in the /run/user/ etc. etc. directory) What am I supposed to be doing to get this to work?

I don't care if I use smb, ftp, or afp to share--I just want something that works and is accessible to scripting and the web server. What's the solution? it has to be simple?  I should note I've also played without with a command called mount_afp and it 'times out' which is obviously nonsense, since I know afp works on my machine... Why is this so hard???

---

