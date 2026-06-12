---
title: "Networking with Win XP, custom install"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by beep1314 on 2007-08-15
How do I set up a network with a Windows XP computer?  I have a custom install w/ Ubuntu 7.04 - Fluxbox - XDM - Opera - Xfe - Synaptic - Linksys router.

Simple would be good,
Thanks

---

### Post by Steve1961 on 2007-08-15
As long as both machines are connected to the router just run the network setup wizard on the windows machine and then right click any files or folders you want to share and check the appropriate settings.

On the ubuntu machine  go into system>administration>shared folders and define shared folders on your Linux box.  If you specify samba it will trigger an installation.  Then set the workgroup name in the general tab of the shared folders dialogue.

Install firestarter and make sure you create a rule for allowing the smb service through, and access from the windows box (IP address).  Also configure the firewall on the windows box to let the Linux box through it.

Make sure that the folders you share on the linux box have permissions set so that the windows box can access them.  Also a good idea to ensure both machines have a static IP (just make sure you give them IPs outside the DHCP range defined in your router).

Finally, go to Places>network and see if you can see the windows machine.  If not, just open nautilus Go>Location and type smb://ipaddressofwindowsmachine.

Phew!  There's a lot more to networking than this, but this should get you started.

Oops, some of the above instructions are for Gnome rather than Fluxbox, perhaps someone with more fluxbox expereince could advise.

---

### Post by beep1314 on 2007-08-15
I do not find a system>administration>shared folders with fluxbox....  Any hints?

---

### Post by beep1314 on 2007-08-15
Ok, I installed Samba with apt-get, and now my XP comp can see ubuntu.  I still can't open folders.  How do I set permissions in Fluxbox?  Plus I still can not see XP from ubuntu.

---

### Post by Steve1961 on 2007-08-15
You could try some of the generic instructions here

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

and here

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)

---

