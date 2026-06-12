---
title: "Problem sharing via ssh"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by aquascrotum on 2010-03-19
Hi

I'm trying to share files between 2 ubuntu (both Karmic) PCs.

Sharing is working fine in one direction, however in the other I get a message after inputting info to the "Connect to server" dialogue box that "Cannot display location "sftp:// etc etc   Connection refused by server".

I've no idea why this is, I have firewall on both pc's deactivated.  SSH is installed on both machines.  I've checked I'm using the right IP address.

Any help would be appreciated...

---

### Post by aquascrotum on 2010-03-20
Bump!?

---

### Post by The Real Dave on 2010-03-20
Have the ssh server's started on the PCs? Try opening a terminal (Applications>Accessories>Terminal) and typing

```
sudo /etc/init.d/ssh start
```

Hit enter, give it your password, and hit enter again. Do this on the PC you wish to connect to, then try connecting again. 

Just a word on filesharing in Ubuntu, using SSH is very secure, but slower, as data is encrypted when being sent through SSH.

NFS is much less secure, but if your just sharing files on a home network, it's perfect, much quicker. There's a good guide [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo"), which is worth reading. There is a lot in it that isn't necessary if you don't need security, if your simply sharing on a home network for example. I can help you set up some shares, and automounts if you like.

---

