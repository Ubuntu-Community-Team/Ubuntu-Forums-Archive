---
title: "A remote user question"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by EclipseOTO on 2010-08-14
So, I have a very small hard drive on this laptop and have been curious if I could set some sort of system up like that have at most schools/institutions, where all of a users files and settings are stored on a centralized server and you can use any computer attached to the network to access those files and what not.  

Here arises my question; What exactly is this called and does anyone have a good guide or advice on doing this using ubuntu?

Thanks a ton,
Pete

---

### Post by NCLI on 2010-08-14
What you describe is called Distributed Computing, but it's really only a viable option when it's a local server, unless you have an extremely fast and ultra-reliable Internet connection.

I'd recommend simply getting a bigger HDD.

---

### Post by EclipseOTO on 2010-08-14
Ah, I do have a local server, I'm running a NAT'd device in my room off another server I built! :)

---

### Post by NCLI on 2010-08-14
> **EclipseOTO said:**
> Ah, I do have a local server, I'm running a NAT'd device in my room off another server I built! :)

And you're not planning on taking the laptop anywhere else?

If so, you could technically setup an SSHFS connection between your laptop and the server, and make it mount it as your /home at startup. :D

Do you have any experience with SSH?

---

### Post by EclipseOTO on 2010-08-14
It's a laptop only in name unfortunately... it has ~5 minutes of battery.  I have a little experience with SSH but am not sure what SSHFS is.  I guess the other problem would be that the laptop connects to the network wirelessly, so mounting the partition on startup becomes more challenging, since it connects to the network via network manager after I've signed in on the computer.

---

### Post by NCLI on 2010-08-14
> **EclipseOTO said:**
> It's a laptop only in name unfortunately... it has ~5 minutes of battery.  I have a little experience with SSH but am not sure what SSHFS is.  I guess the other problem would be that the laptop connects to the network wirelessly, so mounting the partition on startup becomes more challenging, since it connects to the network via network manager after I've signed in on the computer.

Could you be satisfied with simply mounting a partition for data instead of replacing your /home?

SSHFS is a method of securely accessing a remote filesystem(FS) via SSH. Do you already have SSH set up on the server? If you do, this won't take long.

---

### Post by drdos2006 on 2010-08-14
Check this out for shared files.
> 
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 

Addendum:	On the Server machine
Needed to add Group of users on the machine designated as the server. Added the group via Webmin because that was what I was using. If that does not work then on the Server machine:
sudo addgroup MyGroupName
Added /sharedfiles on server
Needed to change group permissions for /sharedfiles
sudo chgrp MyGroupName  /sharedfiles
//**
Client: Mounted /sharedfiles from terminal as /sharedfiles, can be set in /etc/fstab with :
sudo mount  <serverIPaddress>:/sharedfiles  /sharedfiles in /etc/fstab
Copied files as test and it worked.

regards

---

### Post by EclipseOTO on 2010-08-14
Yeah, I do, but I just thought it would be nice to be able to easily maintain settings between the 3 non-server computers on the network.  If there isn't an easy way to do this I guess I should just resort to using network storage

EDIT:  Sorry [drdos2006]("http://ubuntuforums.org/member.php?u=530536"), didn't see your message, thanks for the advice, I'll give that a try.

---

### Post by NCLI on 2010-08-14
> **EclipseOTO said:**
> Yeah, I do, but I just thought it would be nice to be able to easily maintain settings between the 3 non-server computers on the network.  If there isn't an easy way to do this I guess I should just resort to using network storage

Well there is. Just setup an Ubuntu One account, go to your home folder, press control+h, then mark the settings folders you want synced. That's probably the easiest way.

I can't remember how you do it in Lucid though, so you're on your own there. Once 10.10 rolls around, you simply right-click the files/folder, and mark them for syncing with UbuntuOne.

If you need more assistance, I'll be back in approximately 8 hours, though I expect someone else will assist you further if need be.

---

### Post by EclipseOTO on 2010-08-14
I think I can figure it out from here, thanks y'all!

---

