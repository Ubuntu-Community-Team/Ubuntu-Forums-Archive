---
title: "No permissions when mounted network device"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by frolle on 2007-06-06
Hey :)

I have been researching a lot, but i havnt been able to find any find. I am for the moment accessing my shared folder (located on my win2003 server) with the following command: 
```
sudo mount -t smbfs //10.0.0.8/FROLLE /media/FROLLE -o username=Administrator,password=frolle
```

It mounts the device perfectly, but i do not have any permissions. I have checked on my winserver, but i do have permissions to do whatever i want. 

Any suggestions?

Thanks in advance

//frolle

---

### Post by mitch.c on 2007-06-07
You might want to try something like this:
```
$ sudo mount -t smbfs //10.0.0.8/FROLLE /media/FROLLE -o username=Administrator%frolle,dmask=775,gid=plugdev
```
I use the 'plugdev' group because all users are a member of this group, but you could use some other group. The 'dmask' option will set the access rights to r/w (no I don't know why the rw option doesn't do it all).

[[COLOR="Red"]UAResolved[/COLOR]]("http://ubuntuforums.org/showthread.php?t=377083")

---

### Post by frolle on 2007-06-08
Thanks for answering. I found the error. I had a ! in the in of the password i used, so i got a bash error. I changed the pass on the win server and its running great now :)

---

