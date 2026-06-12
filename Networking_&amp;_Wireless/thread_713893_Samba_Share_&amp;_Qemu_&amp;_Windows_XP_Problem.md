---
title: "Samba Share &amp; Qemu &amp; Windows XP Problem???"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by mbshinde78 on 2008-03-03
Hello Friends :)

Newly joined this forum. I have a dual boot laptop, windows xp and ubuntu.

Installed Windows XP in ubuntu as well in QEMU as an image.

Now I shared a folder using samba called "Tunnel" to exchange data from Windows XP in VM of Qemu and Ubuntu.

I Run qemu llike below

qemu -hda -m 1024 -net nic -net user -smb $HOME/Tunnel windows.img

The windows xp boots and opens successfully. Now When I click on the Run and type \\10.0.2.2 for the samba shared folder. I can see the Tunnel Folder but when I click on it I get a message saying I donot have enough permissions to access the folder.

I have tried running qemu using sudo but failed. When I run qemu from root termial It won't run.

I have also tried the command net use e: \\10.0.2.2\Tunnel in windows (VM) command line but it says network path not found.

Could anybody please help me regarding this Issue?

Anybody can ask any question.

Thanks

Regards

Manoj

---

### Post by Eiríkr on 2008-03-10
There's no need to run qemu under sudo.  In fact, I strongly suspect its failure to run under the root account is a deliberate security measure.   

That aside, this sounds like a problem with Samba usernames and passwords.  After configuring Samba, you also need to make sure you add the username you're going to use to the Samba password file (which is *separate* from the Ubunutu system-wide password file) by typing this:
```
sudo smbpasswd -a USERNAME
```
... and then typing in the password you'd like to use at the prompt.  Most simply, your Samba and Ubuntu usernames are the same (the passwords don't need to be), as this avoids complications with having to map usernames.  Samba also uses the underlying Ubuntu filesystem permissions, so make sure the username you pick has permissions to the folder you're sharing.  

HTH,

Eiríkr

---

