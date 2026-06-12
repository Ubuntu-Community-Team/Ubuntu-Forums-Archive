---
title: "I jailbroke my ipod and connected via SSH but the folder i need to accsess is locked"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Kedster on 2009-05-06
Alright 
so today I jailbroke my ipod touch 2nd gen and put aome apps from cydia on it, including the NES emulator 

so then I needed to used SSH and nautilus as the client to access it and that went well I think. I can roam around the entire system or whatever, except the folder I need is

/var/mobile/Media/ROMs/NES
but 1 I cant write to a folder past "mobile" so i cant mave rom files there 
2 there is no folder "ROMs/NES" and That wouldn't have been a problem if i could have made one but I cant

---

### Post by kelbizzle on 2009-05-07
You may have to change the owner of the folder. 

Try this:
> chown -R yourusername /var/mobile/Media/ROMs/NES

---

### Post by Alterax on 2009-05-07
> **kelbizzle said:**
> You may have to change the owner of the folder. 

Try this:

Well, that's only got the problem that if you don't have access to alter a folder, you probably can't set ownership on it either.

The command will need to be run by logging in as root.  The default root password is **alpine** and is reasonably well-known, so you may want to change it with the passwd command once you set the permissions on the NES folder.

---

