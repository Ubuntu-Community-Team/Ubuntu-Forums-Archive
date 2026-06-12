---
title: "Home Networking Windows/OSX/Ubuntu"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by igreulich on 2007-07-27
I am extremely frustrated with Ubuntu and its lack of ease of use in the home networking area.

I have a home network that Has 3 computers, and 1 network drive in it.

1 - Mac OS X Tiger/Windows Vista (Intel Mac)
2 - Windows XP Pro
3 - Ubuntu 7.04 Feisty Fawn

All that plus the network drive (NAS).

Mac and XP see one another just fine.
Max and XP are connected, and can transfer files with one another.
Ubuntu sees both XP and Mac.
Ubuntu can only connect to XP.
Mac won't let Ubuntu connect to it.
Ubuntu won't let Mac connect to it.
I have not tried to connect to Ubuntu from XP.
All 3 computers connect to NAS just fine

Ubuntu was great at setting up and installing everything I needed it to. Apache, MySQL, php, Teamspeak, VMWare, etc. (The Virtual XP INSIDE Ubuntu was easier to hook into my home network than Ubuntu has been). I want to continue to use Ubuntu as it has been nearly the best Linux experience I have ever had. But if I cannot resolve the networking issues soon, I will have to switch to something else.

Before you ask, I am trying to do all my networking via Samba, and I have Googled samba, ubuntu, mac, osx, xp, configuring, swat, setting up, help, and howto untill I have gone cross eyed. I have installed smb, smbclient, smbfs, and xinetd. I have read more on smb.conf than one person should have to to get all of this working.

Please, please, please help me. I want to stick with Ubuntu, really I do.

Let me know if I need to post any config files.

Ian the frustrated.

---

### Post by UltraMathMan on 2007-07-29
Have you checked out [SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba") especially the section "Configuring your computer as a server"? Following that section had my XP machine connecting to Ubuntu no problem - haven't tested the Mac though.

-Hope this helps :)

---

