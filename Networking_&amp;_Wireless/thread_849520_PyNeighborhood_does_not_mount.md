---
title: "PyNeighborhood does not mount ?"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by AgentZ86 on 2008-07-04
Hi all

I installed fresh 8.04 and fully updated.

installed my applications.

PYNeighborhood will not mount, I browse to the files in the Pyneighborhood program and I get (Failed to mount) poppup message.

This use to work great on 7.10, and then I upgraded to 8.04, and it still worked great.

From fresh install it does not work ? 

Please advise what is needed or what I might be missing ?

Thanks

---

### Post by MatthewPlanchard on 2008-08-13
To get pyNeighborhood to mount properly, the mount commands have to be run with root privileges.  In the preferences dialogue, go to the SMB and CIFS tags and change the commands smbmount, smbumount, mount.cifs. and umount.cifs to read

```
sudo smbmount
sudo smbumount
sudo mount.cifs
sudo umount.cifs
```

You should also make sure that you've got permission to read and write to the folder where the shares will be mounted.  The easiest way to do that is to create a folder in your home directory (I use /home/[username]/mnt/lan) and then change the Mount folder option in the preferences to read /home/[username]/mnt/lan or whatever folder you choose.

Also make sure that you've removed the default file manager and added nautilus, pcmanfm, or your favorite file manager.

---

### Post by AgentZ86 on 2008-08-16
> **MatthewPlanchard said:**
> To get pyNeighborhood to mount properly, the mount commands have to be run with root privileges.  In the preferences dialogue, go to the SMB and CIFS tags and change the commands smbmount, smbumount, mount.cifs. and umount.cifs to read

```
sudo smbmount
sudo smbumount
sudo mount.cifs
sudo umount.cifs
```

You should also make sure that you've got permission to read and write to the folder where the shares will be mounted.  The easiest way to do that is to create a folder in your home directory (I use /home/[username]/mnt/lan) and then change the Mount folder option in the preferences to read /home/[username]/mnt/lan or whatever folder you choose.

Also make sure that you've removed the default file manager and added nautilus, pcmanfm, or your favorite file manager.

Thanks, 
In the mean time I installed smb4K and it works well enough, however I was getting use the the PyNeighborhood.

Do you know why this works without any other config in 7.10 by default and not in 8.04 ?

I've also noticed that when browsing to a network file location etc. and opening a file lets say open with-kompozer etc. I can't just hit the save button to save ? I have to browse the networks again to the location and save again to save it.
But I can save it if I browse to the shares location using the Places/network shortcut and then the files will save to their proper location without the need to browse around the network again ?

I'm not sure what it's like this but it's a bit annoying to browse to a folder, open a file then you can't save your changes without selecting other, then browsing around the network again.

Which is the only real reason I was installing the Pyneighborhood and/or smb4K and/or LinNeighborhood, which also does not work anymore with 8.04

I'll consider your solution again, but I want to research a little more.

Thanks again for the reply.

---

