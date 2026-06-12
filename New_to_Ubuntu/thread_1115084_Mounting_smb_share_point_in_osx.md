---
title: "Mounting smb share point in osx"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by jaytek13 on 2009-04-03
I am having an issue mounting a share point in osx. I shared my "music" folder, and I can connect to it from osx, but I am getting a cannot mount volume error. 

The samba log files indicate this error:

create_connection_server_info failed: NT_STATUS_ACCESS_DENIED

So I'm assuming it's a permissions issue... I've changed the group owner of the music directory to the sambashare user. I've also added my user, the directory owner, to the sambashare group. Any other ideas?

---

### Post by stchman on 2009-04-03
> **jaytek13 said:**
> I am having an issue mounting a share point in osx. I shared my "music" folder, and I can connect to it from osx, but I am getting a cannot mount volume error. 

The samba log files indicate this error:

create_connection_server_info failed: NT_STATUS_ACCESS_DENIED

So I'm assuming it's a permissions issue... I've changed the group owner of the music directory to the sambashare user. I've also added my user, the directory owner, to the sambashare group. Any other ideas?

Is this an Ubuntu machine that you are trying to mount or a Windows machine?

---

### Post by jaytek13 on 2009-04-03
Ubuntu... I did everything the tutorial was said to do (right click on file to share->sharing options->share this folder). It installed samba, I can access the folder from osx, it just won't mount, and kicks out with that permissions error in the samba log files on the ubuntu machine.

---

### Post by stchman on 2009-04-03
> **jaytek13 said:**
> Ubuntu... I did everything the tutorial was said to do (right click on file to share->sharing options->share this folder). It installed samba, I can access the folder from osx, it just won't mount, and kicks out with that permissions error in the samba log files on the ubuntu machine.

If you are doing shares between Ubuntu and OS X then Samba is the wrong choice IMO.  Remember Samba is a reverse engineered SMB protocol method for Windows computers to connect to Unix shares.

A much better choice would be to use NFS or ssh.  I have a tutorial on NFS shares.

[http://www.stchman.com/share_NFS.html](http://www.stchman.com/share_NFS.html)

I am not sure of OS X implementation of NFS but it is probably very similar.

The ssh is another excellent method as well.

---

### Post by jaytek13 on 2009-04-03
Thanks... i'll check out your nfs tutorial. 

The point of this was to create a mount point for my media so I could use my macbook to sync with my iphone with itunes using the media on my linux machine, as I don't want to have the media on the laptop for space reasons (and, having already jailbroken the phone once and reverting back to default on the phone, I don't want to have to resort to that again because of the reduced battery life I noticed with the jailbroken phone), so ssh I don't think would work here.

---

### Post by jaytek13 on 2009-04-03
Solved... I had to add my user using smbpasswd. After doing so I am now able to mount the volume.

---

