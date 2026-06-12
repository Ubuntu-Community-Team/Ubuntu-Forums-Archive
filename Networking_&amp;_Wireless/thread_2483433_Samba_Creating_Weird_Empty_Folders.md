---
title: "Samba Creating Weird Empty Folders"
date: 2023-01-30
forum: Networking &amp; Wireless
---

### Post by clbraddock on 2023-01-30
On Ubuntu 22.04 LTS whenever I restart samba with: "sudo services smbd restart" it creates a bunch of weird folders in my shared folder. The folders are things like ARM64, IA64, x64, W32MIPS, W32PPC, etc.  They are all empty. I can delete them with rmdir but when I restart smbd again they are back. Why is it making these folders? Thanks!

---

### Post by clbraddock on 2023-01-30
Nevermind. I forgot to add the [share name] when I created the share. Realized this when testparm -s didnt return it. Seems to be working correctly now.

---

### Post by TheFu on 2023-01-30
You'll need to look at the settings for the shares.  There are 2 types.  system-wide settings are in /etc/samba/smb.conf and there are end-user shares which I've never used.  I don't recall the exact command to see them.  Perhaps something like 'net use'?  I know that Morbius1 has posted the command a few times in these forums, so if you search for his samba-related posts here, you'll find it.

To see the system-wide config file, there's a command that parses it and outputs what the parser understands.
```
testparm 
```

---

