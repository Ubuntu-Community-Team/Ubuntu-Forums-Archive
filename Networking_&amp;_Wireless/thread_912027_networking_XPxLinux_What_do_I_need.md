---
title: "networking XPxLinux What do I need?"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by davethewave83 on 2008-09-06
just curious how to get my windows network to become visible to Linux. I can connect to my windows OS through Rdesktop but if I go into Places>Network I see "Windows Network" so I go into that and it usually sees my workgroup, so I go into that and there are no pc's (just trying it now it doesn't even see the workgroup) so I am wondering what I need to purge/reinstall to get it to work correctly. It used to work perfect in Centos before trying Ubuntu. I also used to be able to make it work by entering the information manually in "connect to server" but this has stopped working after I re-installed Ubuntu 8.04. 

I'm pretty sure I need samba, so I will purge that and re-install but what else should I try? 

again, I do know the windows pc's are "touchable" from Ubuntu as I can ping them, trace them, rdesktop them.. I just cannot connect to shares. 

Thanks =)

**edit*
also why does it want to uninstall my ubuntu-desktop/wine when I wish to remove Samba-common? they are unrelated

---

### Post by arch0njw on 2008-09-07
Do you have a firewall running on your XP machine?  That might be interfering.

Also, from your Ubuntu machine, try this using the IP address of your Win XP machine.  If it asks for a password, enter the password you would use for Win XP.
smbclient -L ip.add.re.ss

When you remove anything referenced by a meta-package, it will try to remove the meta-package since you are effectively saying "no thanks, I'll handle these packages myself".  samba-common is in the meta-package "ubuntu-desktop".  I'm not sure why it tries to include wine in that; there could be a dependency there for windows file sharing.

---

