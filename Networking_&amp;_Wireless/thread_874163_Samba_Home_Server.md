---
title: "Samba Home Server"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by ataide.carlos on 2008-07-29
Hi everyone!

I'm posting because I need help setting up a Home File Server. I have tried a Linux-based NAS Server, installing a clean Debian and even a default Ubuntu. None of those I got working perfectly right, there was always some things that weren't working properly.

So if anyone can give me some pointers in using Samba, I would be really grateful.
I want to set up a CLI Ubuntu Server, with Samba File Sharing. I just need to get one folder shared and created all other inside that one (Music, Videos, Documents, etc).
This folder is to be accessible to anyone, with no passwords, no nothing! Just a folder that's accessible through my home network to anyone.

That's really all I need. Pleaaase! someone help me do this!
Thanks in advance!

---

### Post by linux6994 on 2008-07-29
Setting up a Ubuntu pc as a file server is easier than you think.

1. Ensure that the other PCs usually windoze XP or Vista (sorry) are in the same workgroup as you Ubuntu. The default Ubuntu workgroup is WORKGROUP. Make sure the spelling and case are the same all the way around.

2. Install system-config-samba via Synaptic Package Manager this will install a easy gui that will feed your /etc/samba/smb.conf file.

3. Add the respective shares allowing access to all via the Samba gui. (System > Admin > Samba) Make the shared directories writable and visible.

I have found it best to share an external usb drive that will hold everyone's files. This way if you PC dies you can connect the external usb drive to anyones pc and not loose anything. It keeps everyone happy.

---

