---
title: "Router Needs Reboot when using vsftp in VirtualBox!"
date: 2015-03-06
forum: Networking &amp; Wireless
---

### Post by RavenLX on 2015-03-06
This has got to be *the* most mysterious thing I have ever encountered. Can someone please explain this?

Host machine: SolydXK Linux (SolydXK.com - Tracking Debian Jessie/Testing)
Guest Machine via VirtualBox: Ubuntu 14.04 Server, bridged networking (I tried the others and this is the *only* way to get the host and guest to communicate, apparently)

On Guest: vsftpd set up with two virtual ftp accounts: test1.com and test2.com.
Trying to use limits.conf (have /etc/pam.d/vsftp set up to use limits) to limit user upload file size (maximum file size allowed). 

Not only does that not work, any time I make changes to limits.conf or restart vsftpd or even just restart the virtual machine, my** entire internet connection goes down** to the point where the _*only*_ way to get it back is to literally turn off and back on the DSL router/modem (ISP provided device which is NetGear brand).

When I say goes down, I mean not even my other devices/machines on the same WiFi network will get internet access until the modem/router is shut down and powered on again.

Does anyone know what may be happening here? I tried another virtual machine with the exact same setup but instead of vsftpd installed, proftpd was installed. No problems whatsoever on that VM and never any loss of internet when using the VM with proftpd. (NOTE: neither VM has two ftp servers installed. One has *only* vsftpd and the other has *only* proftpd plus both have apache/LAMP setup.)

This is really weird. Is there a bug in vsftp? It seems it hasn't been updated since 2012. Is that project abandoned?

---

### Post by ajgreeny on 2015-03-07
> bridged networking (I tried the others and this is the *only* way to get the host and guest to communicate, apparently)What sort of communication are you wanting to use and talking about?  
Have you set up a shared partition between host and guest?
Do you have VBox-Guest-Additions installed?

---

### Post by RavenLX on 2015-03-07
> **ajgreeny said:**
> What sort of communication are you wanting to use and talking about?

Host: FileZilla
Guest: vstpd server (with virtual login)

Want to use FileZilla on the host to access an FTP account on the Guest.

> **ajgreeny said:**
> Have you set up a shared partition between host and guest?

Not partition no. Shared directory, yes. But it's not being used for the FTP.

> **ajgreeny said:**
> Do you have VBox-Guest-Additions installed?

Yes.

---

