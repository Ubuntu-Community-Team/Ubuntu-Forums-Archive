---
title: "Can't browse network shares from Windows on a machine running 14.10"
date: 2014-12-03
forum: Networking &amp; Wireless
---

### Post by KeithLM on 2014-12-03
So I'm testing out the Live USB just to verify some stuff with my new hardware.  I create a folder on a hard drive, share it, Ubuntu installs samba, and I give it full permissions.  Windows sees the Ubuntu box, sees the share, but says I don't have permission.  On the Ubuntu box I browse the local network, drill down through the Windows network, select the Ubuntu box, select share, and again, no permissions.  I check the share via Ubuntu gui, full permissions are supposedly set.

So simple question, how do I successfully share this with everyone?  All I want to do is test out copying large files to and from this system and see if the speeds match another Ubuntu system.  I just need a quick and dirty share, nothing special, just a plain old samba share.  I've been doing these for decades, but every time a new version of Ubuntu comes along there is always a new trick to it.  I even tried creating one in smb.conf and restarting the services, and I get the exact same behavior.  So I have no idea how Ubuntu is doing this, as it doesn't modify smb.conf when I create shares via the gui, but they appear to Windows, they just aren't browseable.  So they are useless.  I really was expecting this to be point and click.  I've tried a tool called "Personal File Sharing" but it only allows bluetooth sharing, because it's other packages are missing.  Too bad it doesn't say what those packages are, or I'd install them.  

Do I have to create a guest user account or something?  I'm making these 777, and giving full access via the network.  If there's someplace to configure samba that needs additional settings, I can't seem to find it.  And I'm not being prompted by windows for a username or password. It just says see my administrator to get permissions.  Even after a reboot of the Ubuntu box (I set it up the Live USB with persistent info) the shares exist, but the exact same behavior is exhibited.

I tried to mount via another Ubuntu system and it will mount the drive if I provide a username of ubuntu and no password.  So I tried mounting the drive on windows selecting the option to use different credentials.  There I'm told the network folder is currently mapped using a different user name and password and I must disconnect that.  Clearly it is not mounted, and I of course set this to guest in the first place so that shouldn't be an issue.

---

