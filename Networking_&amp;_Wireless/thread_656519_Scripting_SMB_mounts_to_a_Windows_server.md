---
title: "Scripting SMB mounts to a Windows server"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by opus_az on 2008-01-02
If I 'browse' to smb://user:pass@ip.address/share I can add a file and edit the file. Same if I use the 'Connect to Server...' wizard.

So I know my server permissions are correct and a smb connection works.

But scripting the mount isn't quite working yet. I can add a file but I can't edit the file I added.

```
sudo mkdir /mnt/share
sudo mkdir ~/share
ln -s /mnt/share ~/share
sudo mount -t cifs -o username=user,password=pass //ip.address/share /mnt/share
```

I have samba-common, smbclient and smbfs isntalled.

I've tried dozens of recommendations from this and other forums but nothing seems to work, and now I'm just banging my head against the same wall.

Any suggestions? Ubuntu 7.04 and Windows 2003 Server.

---

### Post by murmel on 2008-01-02
This is how I mount my Windows computers:
Install smbfs
```
sudo apt-get install smbfs
```
Create the folder where you want your windows share to be mounted *(I use in this example /mnt/C*
```
sudo mkdir /mnt/C
```
Then edit fstab
```
sudo nano /etc/fstab
```
and add *(192.168.0.1 is the ip to the computer you want to mount and C$ is the folder on the server that is shared /mnt/C is the folder you mount it to)*
[i]You can use the computers hostname instead of the ip address!
```
//192.168.0.1/C$     /mnt/C   cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```
Now create the file .smbcredentials
```
sudo nano /root/.smbcredentials
```
and add
```
username=YourUsername
password=YourPassword
```
and change it's premissions
```
sudo chmod 700 /root/.smbcredentials
```
now remount /etc/fstab
```
sudo mount -a
```

I hope this will work for you!

**Update:**
If it takes ages to shut down your computer, you'll have to edit a script named umountnfs.sh in /etc/init.d/ and add "cifs" to it.
You'll also have to rename it in /etc/rc0.d/ and /etc/rc6.d/ from (I think) S31umountnfs to K15umountnfs.
Do it like this:
```
sudo nano /etc/init.d/umountnfs.sh
```
change it from
```
[...]
               nfs|smbfs|ncpfs) umount -f "$mp";;
[...]
```
to
```
[...]
               nfs|smbfs|ncpfs|cifs) umount -f "$mp";;
[...]
```*Added "|cifs"*
Then rename it in /etc/rc0.d/ and /etc/rc6.d/
```
sudo mv /etc/rc0.d/S31umountnfs /etc/rc0.d/K15umountnfs
sudo mv /etc/rc6.d/S31umountnfs /etc/rc6.d/K15umountnfs
```
*Maybe it's called something else than "S31". If this doesn't work, just search for it, like this*
```
sudo updatedb
locate umountnfs
```

- Simon

---

### Post by opus_az on 2008-01-02
Nope, but thanks. Same thing. I can add a file but I can't edit the added file.

Grrr...

Any other suggestions?

---

### Post by murmel on 2008-01-02
> **opus_az said:**
> Nope, but thanks. Same thing. I can add a file but I can't edit the added file.

Grrr...

Any other suggestions?
Have you thought about giving the right premissions from Windows? You maybe haven't given it write premission

---

### Post by opus_az on 2008-01-02
Hi again. My permissions are good. This is a fileserver that's been in use for Windows clients. Besides, browsing in the File Browser to smb://user:password@ip.address/share works just fine, and so does using the 'Connect to Server...' wizard.

---

### Post by murmel on 2008-01-02
```
sudo mkdir /mnt/share
sudo mkdir ~/share
ln -s /mnt/share ~/share
sudo mount -t cifs -o username=user,password=pass,file_mode=0777,dir_mode=0777 //ip.address/share /mnt/share
```

Tried that?

---

### Post by opus_az on 2008-01-02
Nope. Same thing.

I've tried all these suggestions on two live Ubuntu computers but I guess it's possible both have the same thing interfering with this. Maybe something with me installing kde-desktop on top of the default gnome, or something else I forgot during all my testing.

I have a 'virgin' install of Ubuntu on another computer but won't have access to it til tomorrow.

Thanks for all your help. It seems I've been on the right track so at least I know I'm not missing anything too obvious.

Thanks again :)

---

### Post by murmel on 2008-01-03
> **opus_az said:**
> Nope. Same thing.

I've tried all these suggestions on two live Ubuntu computers but I guess it's possible both have the same thing interfering with this. Maybe something with me installing kde-desktop on top of the default gnome, or something else I forgot during all my testing.

I have a 'virgin' install of Ubuntu on another computer but won't have access to it til tomorrow.

Thanks for all your help. It seems I've been on the right track so at least I know I'm not missing anything too obvious.

Thanks again :)
Hehe, are you using the Live CD trying to mount? I've read about others with problems when trying to mount from it.. But I have no idea... Try with a clean install? Install **smbfs** and mount it?

---

### Post by opus_az on 2008-01-03
LOL, no not using a Live CD. Bad choice of words there. i mean two computers that are in use in the office, they're 'live'. I'll futz the the virgin Ubuntu (probably another unfortunate adjective) later today.

LOL

---

### Post by murmel on 2008-01-03
> **opus_az said:**
> LOL, no not using a Live CD. Bad choice of words there. i mean two computers that are in use in the office, they're 'live'. I'll futz the the virgin Ubuntu (probably another unfortunate adjective) later today.

LOL

hehe, now I get you!

---

### Post by opus_az on 2008-01-03
Rats! Same thing on a clean install of Ubuntu. Tried it now on three different servers; win2003 and win2000. I'd suspect my servers but that wouldn't explain why everything is fine if I browse to smb:// or use the 'connect to server...'.

I have a Debian virtual machine I'll try tomorrow. I also have a clean install of win2k3 I can try tomorrow. 

It's not killing me so I guess it's making me stronger. :-)

---

