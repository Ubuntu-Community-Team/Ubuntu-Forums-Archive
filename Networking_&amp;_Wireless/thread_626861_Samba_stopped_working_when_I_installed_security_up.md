---
title: "Samba stopped working when I installed security update"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by taelatus on 2007-11-29
I'm currently using Ubuntu Gutsy.  I managed to configure samba so I could share individual folders and access shared folders on the windows machines that are on my home network.  This was with samba version 3.0.26a-1ubuntu2.  A couple weeks ago a security update was issued for samba which I installed.  This updated my samba to version 3.0.26a-1ubuntu2.2.  Now I can't access any of the windows shared folders on my network.  I haven't changed any settings in my smb.conf file since before the update.  

I've attached a copy of my smb.conf to this thread.  I don't know much about configuring samba so it's very possible my problem is due to something I have (or have not) included in my config.  If my problem isn't due to how samba is configured, is there a way to rollback my update?  I know I can force synaptic to use the older version but my system indicates that it needs to remove the ubuntu-desktop package before that can be done.

---

### Post by taelatus on 2007-12-06
Bump.

---

### Post by jetsam on 2007-12-07
I don't have this actual bug, but for the downgrade, the following worked for me under a virtual machine running Gutsy:

```
sudo apt-get install samba-common=3.0.26a-1ubuntu2
```

and then:
```
sudo apt-get install samba=3.0.26a-1ubuntu2
```

Apt-get complained if I didn't do samba-common before samba.  

If you do this, you might want to go into Synaptic and lock both the samba and samba-common packages to version 1ubuntu2 so update manager doesn't keep telling you to update them.  Just search for each package, highlight it, and select package-->lock version from the menu.  You'll probably want to unlock them at some point in the future when an update comes along that hopefully won't break your network browsing.  

You'll probably need to reboot to see any change in browsing behavior.

Post back if that works.  I think a few people have this problem.

---

### Post by venkaya on 2008-01-08
Hello guys. I have this same problem, when I run Ubuntu 7.10 live cd I can see my windows network, after I install  and download the security updates I lost complete access to the network. I'm reinstalling now, and I will try to lock samba and samba commons as someone suggested. If someone knopws something about this PLEEEASE post back. thanks

---

