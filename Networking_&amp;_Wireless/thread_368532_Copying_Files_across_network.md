---
title: "Copying Files across network"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by scottsanpedro on 2007-02-23
Hi,
I have two linux Ubuntu servers running. They are both on the same LAN. One is the production intranet (temporary) and the other the new to be permanent intranet.  
I want to copy files across from the live box to the new box. Its running PHP Nuke.

Everytime I copy the files across (via samba share) not all the files copy across.

Is there a way to copy all files? Is it because some files are hidden? Is it because the system is live and there are file locks?

Many thanks for your time

Scott

---

### Post by scottsanpedro on 2007-02-23
anyone?

---

### Post by scottsanpedro on 2007-02-23
Hi,
I have two linux Ubuntu servers running. They are both on the same LAN. One is the production intranet (temporary) and the other the new to be permanent intranet.
I want to copy files across from the live box to the new box. Its running PHP Nuke.

Everytime I copy the files across (via samba share) not all the files copy across.

Is there a way to copy all files? Is it because some files are hidden? Is it because the system is live and there are file locks?

Many thanks for your time

Scott

---

### Post by ViRMiN on 2007-02-23
I used scp to copy files between Linux hosts.  Using public/private keys you can get files over without being prompted for passwords.  There should be some HOWTO's around for setting this up.  I use it for automating file transfers which run via cron jobs in the middle of the night

---

### Post by TheWizzard on 2007-02-23
> **scottsanpedro said:**
> Hi,
I have two linux Ubuntu servers running. They are both on the same LAN. One is the production intranet (temporary) and the other the new to be permanent intranet.  
I want to copy files across from the live box to the new box. Its running PHP Nuke.

Everytime I copy the files across (via samba share) not all the files copy across.

Is there a way to copy all files? Is it because some files are hidden? Is it because the system is live and there are file locks?

Many thanks for your time

Scott


how do you copy them?

---

### Post by bapoumba on 2007-02-23
Threads merged.

---

### Post by koenn on 2007-02-23
see also
[http://ubuntuforums.org/showthread.php?t=368480](http://ubuntuforums.org/showthread.php?t=368480)

---

### Post by ViRMiN on 2007-02-23
Cheers bapoumba, did notice the cross-posting!

---

### Post by ViRMiN on 2007-02-23
I've been rar'ing up specific files/directories on my FC6 boxes and scp'ing the .rar's to other machines in case of HDD failure.  Nothing elaborate at all... just gives me the ability to get stuff back in a machine failure.

---

