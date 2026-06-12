---
title: "Accessing a Windows XP network"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by U2XS on 2007-04-16
I am running Ubuntu with the GNOME GUI.  I have a windows XP network set up and I'd like to access the files on the network through Linux.  I imagine that it can be done, but i don't know how.  

Does anyone have a link to a tutorial?  Or is it easy to explain?  Thanks

---

### Post by electricshoes on 2007-04-16
If you allow sharing on the XP machine then you can set Samba up in Ubuntu.
Look here.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server)

---

### Post by poscogrubb on 2007-04-16
Here's another (more readable, IMO) resource on Samba: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

If you only need to access the Windows XP box from Ubuntu (and not the other direction), you only need the Samba client, smbfs, installed in Ubuntu, not the full-blown Samba server.
Check this out: [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

I installed smbfs, and it was relatively straightforward.

However I've been a little leery of opening up my Windows box with write-able shares. So I'm also looking into mounting my Windows hard drives via ssh (install Cygwin [http://www.cygwin.com/](http://www.cygwin.com/) or some other SSH server on the Windows box, then see [http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)). I know it's probably a bit slower because of the encryption, but I'd pay that price for a little peace of mind.

Are there any other ways to access filesystems between Linux and Windows?

---

