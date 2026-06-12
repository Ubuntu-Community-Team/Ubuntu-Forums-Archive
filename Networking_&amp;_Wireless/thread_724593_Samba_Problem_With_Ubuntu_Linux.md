---
title: "Samba Problem With Ubuntu Linux"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by ubuntoexpert on 2008-03-14
I have installed Ubuntu Linux and want to access files on my Windows network.  Ubuntu can see the network and the shares but will not allow me to mount the share.  Gives this error:

  smbmnt must be installed suid root for direct user mounts error=1.

Did some reseach and found a fix.  Did this command:

   sudo chmod u+s /usr/bin/smbmnt

tried again and get this error:

   libsmb based programs must *NOT* setuid root

so I entered the command:

   sudo chmod  -s /usr/bin/smbmnt

tried again and am back to the original error:

   smbmnt must be installed suid root for direct user mounts error=1.


A vicious catch-22 problem.

Ubuntu does not allow a user to run as root.  How can I access my Win network shares.  Please advise.  thanks.

---

### Post by mimada on 2008-03-14
I had a problem with the iptables firewall blocking Samba. Try installing Firestarter (a gui front-end for iptables) and enabling smb.

---

### Post by Iowan on 2008-03-15
How are you trying to mount the share? I've used the "Connect to Server" option under Places to put icons on my desktop.

---

### Post by ubuntoexpert on 2008-03-15
> **Iowan said:**
> How are you trying to mount the share? I've used the "Connect to Server" option under Places to put icons on my desktop.
thanks for ur replay

---

