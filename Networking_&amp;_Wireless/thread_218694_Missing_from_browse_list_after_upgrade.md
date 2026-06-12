---
title: "Missing from browse list after upgrade"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by tog_benson on 2006-07-18
Hello all,

I just upgraded to Dapper.  All went well.

However, when I browse my workgroup, all computers on my network show up except for the recently upgraded dapper box.  We'll call this recently upgraded computer "ampersand".  Other linux servers and win machines are showing up fine.  The server acting as wins server & browse master seems to be functioning fine.

I can ping ampersand fine, but I cannot access it directly using "\\ampersand" in windows, nor from "smb://ampersand" (from other lin box.  Name resolution is working properly and resolving the correct ip for ampersand from all other machines.

ampersand can browse the network and connect to other samba machines.

It seems to be an issue with samba on ampersand but I cannot tell what it could be.  The conf file seems to be ok and the samba service has been restarted many times.

Thanks for any and all help,
tog

---

### Post by tog_benson on 2006-07-19
Well, I am an idiot.  When I was "restarting" samba, I was calling "/etc/init.d/samba restart" which seemed to silently succeed.  The init script was there but samba was somehow uninstalled in the upgrade.  Samba doesn't work so hot when it is not installed.  I installed it and all is rosy.

---

### Post by jrjr on 2006-07-19
> **tog_benson said:**
> Well, I am an idiot.  When I was "restarting" samba, I was calling "/etc/init.d/samba restart" which seemed to silently succeed.  The init script was there but samba was somehow uninstalled in the upgrade.  Samba doesn't work so hot when it is not installed.  I installed it and all is rosy.

It happened to me too. Checking Synaptic showed samba-common installed but samba itself not installed. 

I installed samba and did the restart. This box still does not show up in the network servers list....  thoughts?

Edit-
I found out that this box joined the default workgroup now (mshome). I wonder how this happened? Mshome did not show up at first. I checked it later and there it was and that told me what happened. Edit smb.conf to fix it :)

---

