---
title: "How do I share folders between two Ubuntu Ibex PCs?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by diablo75 on 2009-01-29
I'm looking for a guide or a carefully written blog that describes the steps to easily share folders between two Ubuntu Ibex PCs on a LAN.  I've tried to do this myself and have failed miserably (you can read what I've tried [here]("http://ubuntuforums.org/showthread.php?t=1053938")).

---

### Post by sandyd on 2009-01-29
hmm... ive tried here
[http://garytang.livejournal.com/2060.html](http://garytang.livejournal.com/2060.html)

and it works

---

### Post by UbuntuNerd on 2009-01-29
check this guide maybe it can help you:
[http://my.opera.com/ubuntunerd1/blog/share-files-between-two-ubuntu-computers-via-ssh]("http://my.opera.com/ubuntunerd1/blog/share-files-between-two-ubuntu-computers-via-ssh")

---

### Post by diablo75 on 2009-01-29
> **carlee said:**
> hmm... ive tried here
[http://garytang.livejournal.com/2060.html](http://garytang.livejournal.com/2060.html)

and it works

I followed this to the T, and still have no share.  :(

---

### Post by diablo75 on 2009-01-29
> **UbuntuNerd said:**
> check this guide maybe it can help you:
[http://my.opera.com/ubuntunerd1/blog/share-files-between-two-ubuntu-computers-via-ssh]("http://my.opera.com/ubuntunerd1/blog/share-files-between-two-ubuntu-computers-via-ssh")

I'll give this a shot, I guess.  I just don't understand WHY I have to resort to using a tunnel on my own LAN to get two PCs to share a folder.

---

### Post by diablo75 on 2009-01-29
> **UbuntuNerd said:**
> check this guide maybe it can help you:
[http://my.opera.com/ubuntunerd1/blog/share-files-between-two-ubuntu-computers-via-ssh]("http://my.opera.com/ubuntunerd1/blog/share-files-between-two-ubuntu-computers-via-ssh")

This works.  I wish I didn't have to resort to using SSH.  Not so much for my own sake, but how many newbies out there are going to hit the snags I have in the last couple of days trying to get this to work and give up on Ubuntu because it's "too dumb to know how to share a folder with another PC that's running the exact same OS."  And Mark Shuttleworth is alleging he wants Ubuntu to target Mac OS X.  It just isn't gonna happen unless stupid networking stuff like this isn't made more failsafe and self fixing.  An example of self-fixing should be things like automating the opening of ports somehow, so the user isn't required to install and run firestarter, isn't required to even know what the hell a "port" is.  At most it shouldn't get any more demanding of the user than to have them type in an admin password so as to grant permission, and that should include opening ports and whatever else is required to share a folder!

The ideal file sharing experience should be as easy as right-clicking on a folder, enabling it to share, and then walking over to the other PC to browse for that share in Network.  3 steps, all within the GUI, should be all it takes to do something like this.  I shouldn't be required to open a terminal.  I shouldn't have to manually install software.  I am suddenly very disappointed with Ubuntu and really really regret having to state that I suddenly feel it's no where near being ready for "the big time".

---

### Post by UbuntuNerd on 2009-01-29
you can do that by installing "samba" file sharing but what I don't like about it is every time you upgrade you have to configure things again, also the connection at least for me was there sometimes and then not there I didn't like it.

---

### Post by diablo75 on 2009-01-29
> **UbuntuNerd said:**
> you can do that by installing "samba" file sharing but what I don't like about it is every time you upgrade you have to configure things again, also the connection at least for me was there sometimes and then not there I didn't like it.

I did this, two posts up or so.  And it didn't work, even after a restart of both PCs and I double-checked my firestarter policies.

---

### Post by b0b138 on 2009-01-29
> The ideal file sharing experience should be as easy as right-clicking on a folder, enabling it to share, and then walking over to the other PC to browse for that share in Network. 3 steps, all within the GUI, should be all it takes to do something like this.

Actually, it is that easy. You right click a folder, click sharing options, check share this folder. If it hasnt been installed yet, it will now want to install a network protocol. IMO, the reason nothing is installed by default is so you have the choice of what to use. Samba is probably the most common as it will allow you to talk to windows over a network. (You could also use nfs.) After samba is installed, you will need to log out and log back in so your privileges are active on the new sambashare group.

Now, since you've installed firestarter, I'd imagine you need to open the ports for samba to get though. A quick google search found ```
UDP ports 137 and 138
TCP ports 139 and 445 
```

Hope this helps some :guitar:

---

### Post by diablo75 on 2009-01-29
> **b0b138 said:**
> Actually, it is that easy. You right click a folder, click sharing options, check share this folder. If it hasnt been installed yet, it will now want to install a network protocol. IMO, the reason nothing is installed by default is so you have the choice of what to use. Samba is probably the most common as it will allow you to talk to windows over a network. (You could also use nfs.) After samba is installed, you will need to log out and log back in so your privileges are active on the new sambashare group.

Now, since you've installed firestarter, I'd imagine you need to open the ports for samba to get though. A quick google search found ```
UDP ports 137 and 138
TCP ports 139 and 445 
```

Hope this helps some :guitar:

I have all of these ports open on both PCs but I still don't see anything show up in Places>Network, even after samba has been installed on both of them and shares designated on a specific folder.  I'm on the verge of formating both PCs.

---

### Post by kidux on 2009-02-24
> **diablo75 said:**
> This works.  I wish I didn't have to resort to using SSH.  Not so much for my own sake, but how many newbies out there are going to hit the snags I have in the last couple of days trying to get this to work and give up on Ubuntu because it's "too dumb to know how to share a folder with another PC that's running the exact same OS."  And Mark Shuttleworth is alleging he wants Ubuntu to target Mac OS X.  It just isn't gonna happen unless stupid networking stuff like this isn't made more failsafe and self fixing.  An example of self-fixing should be things like automating the opening of ports somehow, so the user isn't required to install and run firestarter, isn't required to even know what the hell a "port" is.  At most it shouldn't get any more demanding of the user than to have them type in an admin password so as to grant permission, and that should include opening ports and whatever else is required to share a folder!

The ideal file sharing experience should be as easy as right-clicking on a folder, enabling it to share, and then walking over to the other PC to browse for that share in Network.  3 steps, all within the GUI, should be all it takes to do something like this.  I shouldn't be required to open a terminal.  I shouldn't have to manually install software.  I am suddenly very disappointed with Ubuntu and really really regret having to state that I suddenly feel it's no where near being ready for "the big time".
I agree wholeheartedly. It's really f*&^%$d up that SMB works by browsing for it through the network after having shared a folder with it, but NFS takes so much more effort to make work.

---

### Post by Bölvaður on 2009-02-24
> **kidux said:**
> ....but NFS takes so much more effort to make work.

no it doesnt.

1. download ntfs server and client
2. add a line to /etc/exports on the server machine : /data/share	192.168.1.1/24(rw,async) for an example
3. add a line to /etc/fstab on client: 192.168.1.112:/data/share/ /mnt/share/ nfs rsize=8192,wsize=8192,timeo=14,intr

or instead of step number 3 you can make a small file containing the mount command and just execute it every time you want to mount the shared folder.

reliable and easy.

---

### Post by kidux on 2009-02-24
> **Bölvaður said:**
> no it doesnt.

1. download ntfs server and client
2. add a line to /etc/exports on the server machine : /data/share	192.168.1.1/24(rw,async) for an example
3. add a line to /etc/fstab on client: 192.168.1.112:/data/share/ /mnt/share/ nfs rsize=8192,wsize=8192,timeo=14,intr

or instead of step number 3 you can make a small file containing the mount command and just execute it every time you want to mount the shared folder.

reliable and easy.
As opposed to right clicking a folder, telling it to share, and then going to the "client" and browsing through the network. That is much more simple, especially when you start talking about multiple shares through multiple machines. Which is easier, editing each client individually to tell it where all those shares are, or having the server simply share it and then all the clients browse for it, unless there is something I am missing?

---

### Post by TalioGladius on 2009-02-24
Create a share on one box, mount it with fstab on the other.  Pretty simple.

---

### Post by laithbsoul on 2009-02-24
press alt-f2 and enter shares-admin then add the folder you want to share and access it from other computer by going to places->network

---

