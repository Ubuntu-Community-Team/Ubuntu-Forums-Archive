---
title: "The always recurring &quot;windows share&quot; on Dapper..."
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by Foxen on 2006-10-17
Allright, I am tinkering with samba on my laptop and it has been quite a while since I fiddled with samba(about a year ago and then on Fedora Core setting up a file server for my previous work), so I am feeling a little rusty here... this is what I've come up with so far:

in fstab
//fraggelbox/C$ /home/myname/fraggelbox/C smbfs noauto username=myname,password=mypassword,uid=1000,umask=777 0 0

Now, wouldn't that line make it possible for me to just type mount /home/myname/fraggelbox/C to make it mount and give me write, delete, read and execute permissions? I wan't to be able to mount this share as a user, not using sudo if possible but the important thing is that I don't have to type the whole "sudo mount -t smbfs //server/share /mountpoint/blabla -o username etc" every time I want it connected... and I don't want it to connect automagically since this is a laptop and it might not be accessible all the time...

Any suggestions? If you suggest making a script to do it, then please give me the n00b treatment as in tell me exactly how to make the script and what "chmod" it should be set to, haven't worked with scripts before...

On another note, I will probably be posting a loosely crafted guide howto get your damn Mobility Radeon X1600 working with 3D in Ubuntu Dapper with bits and pieces from Edgy if anyone wants to read about it...

---

