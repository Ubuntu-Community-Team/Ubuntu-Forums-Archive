---
title: "newbie stuck windows/linux fileshare"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by zeus123 on 2007-07-01
Im a newbie to linux and im a newbie to networking so your gonna have to be patient!

All my files are on a partition of a windows desktop which is hardwired to my wireless router.
My linux machine connects to the router wirelessly and is providing an internet connection.

All I want to do is access my files on the windows machine from my linux machine.

I folliowed this help page....
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

but I get stuck because I dont know what is wants me to enter for the hostname (netbios name), username and password. I also dont know what my linux ip address is.

When I used to use windows on both machines it was simply a matter of right clicking the partition and clicking on "share this folder" and it was visable from the other windows machine. No hostname, username or password was ever set.

Any help would be great! Ive been clicking for 2 days now and am board of going around in circles.

---

### Post by Gallows on 2007-07-01
> but I get stuck because I dont know what is wants me to enter for the hostname (netbios name), username and password. I also dont know what my linux ip address is.

To find out your linux ip address from a command shell

```
ifconfig
```

The netbios name is normally the the shortname of your linux box (but it doesn't have to be) to find out use

```
hostname
```

Your username and password will depend on how you've setup samba - try the account you use to login but it's probably worth posting your smb.conf (found in /etc/samba/) if you want more help

---

