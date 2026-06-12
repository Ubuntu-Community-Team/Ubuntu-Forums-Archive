---
title: "Can't see Windows Network Shared Files"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by doninsa on 2010-04-03
Nautilus Network shows Windows Network named MSHOME, but clicking on this icon produces an error that says "Failed to retrieve share list from server."  Where do I look to resolve this problem?  

The Windows network MSHOME does have files that are being shared and I can see them when I boot to Windows XP.  It's just in Ubuntu that I can't see these files.

---

### Post by davidvasta on 2010-04-03
If you have "other" PCs on the network you should be able to see them all when you browse the network. But if they are all on different WORKGROUPS this may present a problem as they might not all want to talk. 

At home here I have a few server, lucky me, that I share files and other stuff with. You should be able to use the PLACES> CONNECT TO A SERVER option and just use the WINDOWS SHARE and enter the IP if you know it.

The default WORKGROUP Ubuntu sets you share to is MSHOME and most XP PCs set the default workgroup to WORKGROUP so unless they are named the same thing you may have some issues. 

See if that helps.

-David

---

### Post by mike2357 on 2010-04-03
Also, does your Windows computer have a firewall which is blocking access from your Linux computer?  That could be the problem.

---

### Post by doninsa on 2010-04-03
> **davidvasta said:**
> If you have "other" PCs on the network you should be able to see them all when you browse the network. But if they are all on different WORKGROUPS this may present a problem as they might not all want to talk. 

At home here I have a few server, lucky me, that I share files and other stuff with. You should be able to use the PLACES> CONNECT TO A SERVER option and just use the WINDOWS SHARE and enter the IP if you know it.

The default WORKGROUP Ubuntu sets you share to is MSHOME and most XP PCs set the default workgroup to WORKGROUP so unless they are named the same thing you may have some issues. 

See if that helps.

-David

Problem solved!!  I was able to connect by using PLACES > CONNECT TO A SERVER > WINDOWS SHARE and entering the IP address of the Windows XP machine.  Thanks for the help.

---

### Post by doninsa on 2010-04-03
> **mike2357 said:**
> Also, does your Windows computer have a firewall which is blocking access from your Linux computer?  That could be the problem.

Good thought.  I do have a firewall, Zone Alarm Pro.  And I'm connected through a Linksys router.  And, the Ubuntu network connection is a Wireless card.  I tried turning off the firewall but that didn't help.  But, since my original post I've been able to connect the the Windows XP computer by going through PLACES > CONNECT TO A SERVER > WINDOWS SHARE and entering the IP address of the Windows machine.  David Vasta had the solution.

---

### Post by jasewell on 2010-10-17
When I upgraded to Ubuntu 10.10 Maverick I could no longer get Linux to see a Windows XP PC. I could connect to the Windows XP by using Places, Connect to Server, Windows Share and then inserting the IP address of the Windows XP but not by inserting the name of the Windows XP PC. Thus there was no DNS lookup. By adding the line:-
name resolve order = wins lmhosts bcast
to the etc/samba/smb.conf file and then after using sudo restart smbd the problem was solved. To get the Windows XP PC to see the Linux PC sometimes using sudo nmbd restart fixes this.
The Ubuntu 10.10 Maverick upgrade loads only a minimum smb.conf file which leaves lots of configuration options out. See the smb.conf file that Samba loads when it is first installed.

---

### Post by Morbius1 on 2010-10-17
> The Ubuntu 10.10 Maverick upgrade loads only a minimum smb.conf file  which leaves lots of configuration options out. See the smb.conf file  that Samba loads when it is first installed.The default smb.conf in Ubuntu or any linux distro shows only a subset of the options that have been set by default or are configurable. If it were to show and explain all of them it would be hundreds of lines long. To get a concise list of all the default options run the following command:
```
testparm -sv
```

---

