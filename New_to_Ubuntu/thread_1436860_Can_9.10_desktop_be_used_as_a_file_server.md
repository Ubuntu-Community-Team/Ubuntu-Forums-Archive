---
title: "Can 9.10 desktop be used as a file server"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by Marbella on 2010-03-23
I am going to install Ubuntu and was asking if it is possible to use the desktop version as a home file, email server for 5 computers.
Can I run Windows XP on the client machines and Ubuntu as the server.

Or do I need the server version of Ubuntu.

---

### Post by cgroza on 2010-03-23
Yes, it can be... Every thing you can do on a server edition you can do it on the desktop edition as well.

---

### Post by r-senior on 2010-03-23
Yes you can use the desktop version. You just need to add the appropriate packages, like Samba for example.

Obviously if the box doesn't really get used directly, you may want to uninstall stuff like OpenOffice to save space, retaining the desktop for administration without having to use the terminal all the time.

---

### Post by Paqman on 2010-03-23
Absolutely, you can install any of the server packages on the desktop version, and vice versa.

---

### Post by WitchCraft on 2010-03-23
> **Marbella said:**
> I am going to install Ubuntu and was asking if it is possible to use the desktop version as a home file, email server for 5 computers.
Can I run Windows XP on the client machines and Ubuntu as the server.

Or do I need the server version of Ubuntu.

As long as you only run WindowsXP, it will work perfectly.
If you mix XP and Vista/7, you might get into problems with windows shares/samba.
Don't know about Ubuntu, but I heared the new Vista/7 SMB can cause problems if you don't run the latest version of Samba (git).

You can use Samba for windows shares/smb.


On the other hand, you can use OpenSSH for ssh shares, and access them from windows via dokan/sshfs. No problem there, except that it's a little bit more difficult than samba.

The advantage of sshfs over SMB is you can share your drives securely over the internet, any transmission is 4096 Bit RSA encrypted.

---

