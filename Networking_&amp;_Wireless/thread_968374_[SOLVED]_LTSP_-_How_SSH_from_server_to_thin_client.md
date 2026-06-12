---
title: "[SOLVED] LTSP - How SSH from server to thin client (or how to manage thin clients)"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by TeknoPhil on 2008-11-02
Hi,
I've been playing with LTSP server / client for the past few hours.

I was able to connect a diskless computer to a LTSP server without much problem. 

I can see the clients from the server using the Thin Client Manager.

Unfortunately, I am not able to SSH from the server to a thin client (i.e to shutdown the client). I can use xvnc4viewer to connect to the client (GUI) to shut it down but I would prefer to use SSH.

I would need help to successfully configure SSH so I can manage the clients.

Also, is there any other useful tools like Thin Client Manager that could help manage the clients?

Thanks a lot

---

### Post by TeknoPhil on 2008-11-03
I found the problem here:
[https://help.ubuntu.com/community/EdubuntuFAQ#How%20do%20I%20set%20the%20root%20password%20on%20the%20thin%20clients?]("https://help.ubuntu.com/community/EdubuntuFAQ#How%20do%20I%20set%20the%20root%20password%20on%20the%20thin%20clients?")

It was related to the root password on the thin clients.

> In order to debug individual thin clients it can be useful to be able to login in a text session on the thin client. To do this:

1.Login as normal and start a terminal (under applications->accessories menu).

2.Type sudo chroot /opt/ltsp/i386 and press return. You will be prompted for your password.
   
3.At the next prompt, type passwd and press return. You will be prompted for the root password for the thin clients.
  
4.If you're running gutsy (v7.10) or newer, you must now run sudo ltsp-update-image and reboot the thin client you wish to login to. 

Having done the above, you can go to any of your thin clients, hold <ctrl><alt> and press F1. You should now be able to login with the username root and the password you set (if you see the message stating "your account has expired, please contact your system administrator" you must return to the chroot environment and issue the command passwd -u (unlock account) . You should then be able to login to the thin client, as the root user, using the password you set above. 

---

### Post by eugeneccampbell on 2008-11-24
Edubuntu 8.10 LTSP -- all installed OK, client terminals up and running, but how do I access the Thin Client Manager? I've see reference to it as the new name in 7.04 for a completely reworked Student Control Panel in Dapper. I've seen instructions to access it from the System --> Administration and I've seen explanations of what it does. But my installation has nothing under System --> Administration. There is no mention of how to enter it anywhere on my system that I can find -- only how to use it after it while it is running and what happens the first time it is run. It seems to be an intergral part of the LTSP installation because searching Add/Remove comes up with nothing more to add. 

Searching under Synaptic shows only "python-tcm" which is already installed, with the heading "control ubuntu LTSP connections" and explanation "backend system to integrate with thin-client-manager front ends." Seems that's what I'm looking for. Here's the result of a search:

~$ locate tcm
/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/tcm825x.ko
/lib/modules/2.6.24-21-generic/kernel/drivers/media/video/tcm825x.ko
/opt/ltsp/i386/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/tcm825x.ko
/usr/lib/python2.5/site-packages/studentcontrolpanel/ltcm.py
/usr/lib/python2.5/site-packages/studentcontrolpanel/ltcm.pyc
/usr/lib/python2.5/site-packages/studentcontrolpanel/tcmplugins.py
/usr/lib/python2.5/site-packages/studentcontrolpanel/tcmplugins.pyc
/usr/share/doc/python-tcm
/usr/share/doc/python-tcm/changelog.Debian.gz
/usr/share/doc/python-tcm/copyright
/usr/share/pyshared/studentcontrolpanel/ltcm.py
/usr/share/pyshared/studentcontrolpanel/tcmplugins.py
/usr/share/pyshared-data/python-tcm
/usr/src/linux-headers-2.6.24-19/drivers/media/video/tcm825x.h
/usr/src/linux-headers-2.6.24-19-generic/include/config/video/tcm825x.h
/usr/src/linux-headers-2.6.24-21/drivers/media/video/tcm825x.h
/usr/src/linux-headers-2.6.24-21-generic/include/config/video/tcm825x.h
/var/lib/dpkg/info/python-tcm.list
/var/lib/dpkg/info/python-tcm.md5sums
/var/lib/dpkg/info/python-tcm.postinst
/var/lib/dpkg/info/python-tcm.preinst
/var/lib/dpkg/info/python-tcm.prerm

Can anyone tell me how to run this program so I can begin to control the clients? Is is supposed to be on my System menu under Administration, and if so, how do I place it there?

---

### Post by swarm on 2008-12-02
Back from the dead...

I have everything working on the thin client manager, except the screen previews...

When I go to that tab, it shows:

WARNING:root:Failure while authenticating Auth Error: password check failed!


Like I said, everything else works fine, and I do have a /etc/x11vncpassword, as described in [https://wiki.edubuntu.org/InstallX11VncOnLtspClients](https://wiki.edubuntu.org/InstallX11VncOnLtspClients)... this is an Ubuntu install.

ideas?

---

