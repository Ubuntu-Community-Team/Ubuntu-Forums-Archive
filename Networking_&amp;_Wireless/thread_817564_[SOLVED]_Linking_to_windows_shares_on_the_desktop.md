---
title: "[SOLVED] Linking to windows shares on the desktop"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by Stochastic on 2008-06-03
I'm attempting to incorporate a new Ubuntu box into a Windows network.  I can see the network locations via Places->Network->Windows Network->NetworkName and I can even browse everything fine, but I'd like to make symbolic links to the various computers on that network so that others using this box can easily find what they're looking for.  I attempted making links but failed.  Any suggestions?

---

### Post by merlin051 on 2008-06-03
Hi, i access my windows shares with the following method because i found the ubuntu gui confusing.

also requires you to #sudo mkdir /mnt/NAMEOFSHARE

sudo smbmount //mcp/Media /mnt/mediaonmcp -o username=Merlin051,workgroup=workgroup.local,uid=USERNAME,ip=192.168.1.20


As you can see change the command to suite your needs.

you will be prompted for two passwords, the first one is your root password, the second is your domain password.

hope this helps

---

### Post by Stochastic on 2008-06-06
I found this: [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently) and it's working great now.

---

