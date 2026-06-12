---
title: "file sharing"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by manny43 on 2010-07-08
Hello friends

Please show me how to share files between two computers running Ubuntu in home network?Thanks.

---

### Post by GreenN00b on 2010-07-08
From nautilus, the file manager - right click on a folder and select "Sharing options". After sharing the folder should be visible on the other computer.

---

### Post by manny43 on 2010-07-08
Thanks for your help.In order to see shared folder do i have to open network and search for that folder?

---

### Post by GreenN00b on 2010-07-08
Open network, should see the other computer in there somewhere, open it and should see the shared folders ...

---

### Post by bodhi.zazen on 2010-07-08
You can use several methods to share files, http, ssh (scp), ftp, samba, nfs, rsync

If you are sharing between linux boxes on a LAN, try nfs

If you are sharing with windows boxes use samba.

See also:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

You can configure the shares either graphically or from the command line. Same with mounting them on the client.

If you have a specific question about a specific protocol, please ask.

---

### Post by spiky001 on 2010-07-08
Can you explain what sort of thing you want to do and set up you have got

---

### Post by nothingspecial on 2010-07-08
Try this, if you want full access to each computer, from each computer.

On both machines```
 sudo apt-get install openssh-server openssh-client
```

One of them is installed by default but I can`t remember which one.

Now, on both machines right click the network icon and choose connection information and take a note of both machines ip address.

Then on machine A, in your menu, go Places > Connect To Server

In the top box choose ssh

In the next box put username@ip_address_of_the_other_machine

Check (tick) the add bookmark box and give your other computer a name in the Bookmark name box.

Repeat this process the other way round, from machine B

You will now have an entry in your places menu on each machine for the other one that you just have to click to access.

---

### Post by manny43 on 2010-07-08
I have a home network with five computers only one is running Vista all others running Ubuntu 9.10.In Vista i open network i can see all computers but i dont use Vista anymore and want to share photos with
all pcs running Ubuntu.

---

### Post by bodhi.zazen on 2010-07-08
> **nothingspecial said:**
> On both machines```
 sudo apt-get install openssh-server openssh-client
```One of them is installed by default but I can`t remember which one.

ssh client is installed by default (makes sense if you think about it) , although on some distros **cough* Fedora *cough** ssh server is also installed by default.

---

### Post by nothingspecial on 2010-07-08
Maybe sshfs is your freind then.

I use it on a netbook with a broken keyboard that I use as a digital photo frame.

It`s explained in this link

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by Morbius1 on 2010-07-08
> **GreenN00b said:**
> From nautilus, the file manager - right click on a folder and select "Sharing options". After sharing the folder should be visible on the other computer.
Did you try this?

---

### Post by nothingspecial on 2010-07-08
> **bodhi.zazen said:**
> ssh client is installed by default (makes sense if you think about it) 

Indeed it does.  


[SIZE=1](why are you a scary sith, you used to be a cuddly bear?)[/SIZE]

---

### Post by bodhi.zazen on 2010-07-08
> **nothingspecial said:**
> [SIZE=1](why are you a scary sith, you used to be a cuddly bear?)[/SIZE]

Someone "stole" my old avatar =)

---

### Post by gaines2166 on 2010-07-12
> **GreenN00b said:**
> From nautilus, the file manager - right click on a folder and select "Sharing options". After sharing the folder should be visible on the other computer.

> **GreenN00b said:**
> From nautilus, the file manager - right click on a folder and select "Sharing options". After sharing the folder should be visible on the other computer.

This works for me to see the folders on my wife's computer (we both use Ubuntu 9.04), but when I try to share my Shared Folder with her, I get this:

"'net usershare' returned error 255: net usershare add: failed to add share shared files. Error was Operation not permitted"

I was able to complete the Nautilus operation with a regular folder (I had to let Nautilus add the necessary permissions), but when I go to her computer and I try to open one of my folders, I get the message "Unable to mount location/Failed to mount Windows share"

When I first switched to Ubuntu, I started with my computer while my wife continued with Win XP, so I set up Samba.  I think also tried NFS because I couldn't seem to get easy file sharing going. Then I switched her to Ubuntu and removed Samba from both (and NFS ???).

Using Places->Network the Windows icon still shows up on both computers, so obviously something Samba is still being invoked(???).

Suggestions?

---

### Post by Morbius1 on 2010-07-13
> "'net usershare' returned error 255: net usershare add: failed to add  share shared files. Error was Operation not permitted"

I was able to complete the Nautilus operation with a regular folder (I  had to let Nautilus add the necessary permissions), but when I go to her  computer and I try to open one of my folders, I get the message "Unable  to mount location/Failed to mount Windows share"
You really need to start your own thread because somehow this one has already been marked **[SOLVED].**

When you do and if you're still interested in using Samba then I would suggest you post the output of the following commands so that everyone who sees it can find out what you're sharing and how you're sharing it:
```
net usershare info
sudo net usershare info
testparm -s
```

---

