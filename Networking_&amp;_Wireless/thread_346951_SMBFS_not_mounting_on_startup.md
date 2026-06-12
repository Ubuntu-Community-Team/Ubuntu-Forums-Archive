---
title: "SMBFS not mounting on startup"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by cookieofdoom on 2007-01-26
Well, I hate to start this new thread because it seems like somebody out there must have had my problem, or that I must be doing something wrong. I've searched and searched, but not found anything, though.

I'm running a Buffalo network drive (drivestation) and I've actually managed to get my drives to mount properly by altering my fstab and then doing "sudo mount -a". I had Amarok go through and index my music and I could listen to my music. It works extremely well. When I go to boot, however, everything takes forever. I load Ubuntu with no problems, but when I log into my account I get an error message telling me that HAL failed to initialize properly (sometimes I get this message, sometimes I don't). After I click okay to the message I have to wait forever for my panels, and a significant portion of GNOME to load. Then when I go to access network drives my system hangs and I get an error message about 15ish seconds later. The only way for me to fix it is to "sudo umount /media/lanmultimedia" (and other drives) and then "sudo mount -a".

This all makes very little sense to me. I've taken the entries out of my fstab so that I can boot, add them again, and do mount -a. I figure that something is loading before I have network access. To be honest, I'd be happy with a script that loads the entries on startup, but I'm unsure what this would look like as I'm not to experienced with Linux.

The entries in my fstab are as follows:
> //192.168.11.4/multimedia /media/lanmultimedia smbfs credentials=/root/.smbcredentials 0 0
//192.168.11.4/david /media/landavid smbfs credentials=/root/.smbcredentials 0 0
//192.168.11.4/public /media/lanpublic smbfs credentials=/root/.smbcredentials 0 0

Any help is greatly appreciated!

---

### Post by MetalMusicAddict on 2007-01-26
You have Samba and smbfs installed?

---

### Post by cookieofdoom on 2007-01-26
As far as I know. I installed smbfs, I know that much. If I didn't have those installed I would not be able to make them work at all, right?

---

### Post by Medieval_Creations on 2007-01-26
Have you double checked to make sure SAMBA is running properly on the the server?

---

### Post by MetalMusicAddict on 2007-01-26
> **cookieofdoom said:**
> As far as I know. I installed smbfs, I know that much. If I didn't have those installed I would not be able to make them work at all, right?

Make sure you have those 2 packages installed. We'll go from there.

---

### Post by dannyboy79 on 2007-01-26
smbfs is going out the door! use cifs, it's the future.

---

### Post by streeto on 2007-01-26
Have you tried connecting directly to the share via smbclient?

$ smbclient -U username //192.168.11.4/multimedia

I once had problems mounting shares using smbfs, and bad authentication was one of the causes. Also, I now use cifs, which I recommend over smbfs (solved my problems with character sets, among other things).

-st.

---

### Post by cookieofdoom on 2007-01-26
> **dannyboy79 said:**
> smbfs is going out the door! use cifs, it's the future.

I must admit, when I first read your post I was confused. I didn't even know I could use cifs, but I figured I'd give it a try, worst case scenario I'd have to change settings back again. I changed to cifs, and it worked! I'm so happy! Start up still feels a tiny bit slow, but that's probably just it mounting the drives.

What's great is that now I can access my media from anywhere since I'm running an ftp server. Thank you all very much for helping me. I knew there had to be a simple solution.

---

