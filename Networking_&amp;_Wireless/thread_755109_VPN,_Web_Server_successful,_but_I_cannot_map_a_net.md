---
title: "VPN, Web Server successful, but I cannot map a network drive on Ubuntu machine in XP"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by Valkhorn on 2008-04-14
Here is the issue. I'm new to Ubuntu/Linux and I've set up the 64 bit server version with a GUI as a web server in a full LAMP environment.

[LIST]
[*]I can VPN into my Linux machine from Windows XP
[*]I can connect to my Linux machine in Windows and Remotely so it does act as a web server
[*]I can access my Windows XP Machine from Ubuntu without a problem
[/LIST]

BUT

I simply cannot map a network drive in Windows XP. When I attempt to do so, I can see the box (I named it ValkLinux) but I can't select it and hit ok. When I right click and select properties, I get "You do not have the appropriate access rights for this server."

I have Samba installed, I have it set up to look for MSHOME (which is the network name in XP), and I have set up a login/password for an SMB user.

Any help would be appreciated.

---

### Post by superprash2003 on 2008-04-14
have you added the samba user to the samba user's list?? try following the samba guide here [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by Valkhorn on 2008-04-15
> have you added the samba user to the samba user's list?? try following the samba guide here [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

Sure have and it doesn't work. It doesn't even prompt me for a login/password.

---

### Post by superprash2003 on 2008-04-15
is the samba username and the windows username the same??that might be the problem

---

