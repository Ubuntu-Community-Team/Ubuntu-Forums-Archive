---
title: "Roll your own custom RDP thin client on Ubuntu"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by goughs on 2008-01-24
Does anyone know of any guides similar to the one at [http://www.unix-tutorials.com/go.php?id=3329]("http://www.unix-tutorials.com/go.php?id=3329"), for Ubuntu (7.10 preferably).

The URL above is a guide to get it working SuSE Linux, however I'd prefer my clients to be running on an Ubuntu system.  If there are no guides, can anyone point me in the right direction?  Any tweaks or changes that need to be done to make it compatible on Ubuntu?

I have attempted to follow the steps on a SuSE install, however I have major problems getting the damn thing to find my network.

Ideally I'd like to start the OS straight into an RDP session, with no method of escape back into Linux for the user.  We currently have a script set-up on Windows machines in order to do this, however the more tech-savvy users are able to break the script, and drop back into a Windows environment, which to get the script working must be logged on with Admin privileges, which is obviously not ideal.

---

### Post by daengbo on 2008-01-24
My answer won't be ubuntu. The easiest way to do this is to use K12LTSP. You can set the clients to boot from the network and connect via RDP. There is almost no setup for this.

You will need to install K12LTSP onto another machine, but the hardware requirements are pretty small since the clients will only use the server when they first boot.

[http://k12ltsp.org](http://k12ltsp.org)

Edubuntu may do something similar. I don't know.

---

### Post by goughs on 2008-01-24
Thanks, I'll take a look into that, it does seem an awfully large download/install for it (6 CDs or 1 DVD for version 6).

I've also taken a look at Thinstation too, has anyone any experience using this, or opinions on how it well it works/is likely to work.

Thanks again,
Ste

---

