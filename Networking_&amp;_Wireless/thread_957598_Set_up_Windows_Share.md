---
title: "Set up Windows Share"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by 5circles on 2008-10-24
[I'm trying to take baby steps on networking interconnections, but still running into problems on simple stuff]

I want to set up a Windows share for a folder on a Ubuntu machine (with a static IP).  I'm trying to follow the instructions in [https://help.ubuntu.com/8.04/internet/C/networking-shares.html](https://help.ubuntu.com/8.04/internet/C/networking-shares.html)

First navigated to the folder (my user's home folder).  Right clicked and selected 'sharing options'.  Then selected 'share this folder' - left the default share name.  received a message about  not having permission to create a usershare - ask administrator to grant you permissions to create a share.  OK, that makes some sense.  

Rather than give permission to the user to create the share, I decided to create it as the administrator.  sudo nautilus (isn't there an easier way?), navigate to the folder, right click and select 'sharing options'.  But when I try to share the folder I get a message that the sharename is already a valid system share name.   

[COLOR="Blue"]I can't figure out how to get rid of the sharename.  It doesn't show up in /var/lib/samba/usershares or with 'net usershare list'.[/COLOR]

While I'm trying to figure out a solution, I try to share as a different name.   This works.

Now I can see the share when I browse the network, but there are now two workgroups/domains.  LAN (set up in the Network administration app), and WORKGROUP that just appeared.  Figured out that WORKGROUP is the Samba workgroup, edited /etc/samba/smb.conf and restarted.  Now the share is in the right workgroup, but WORKGROUP is still there.  [COLOR="Blue"]Will WORKGROUP just disappear?  After a restart?[/COLOR]

I can see and access this share via 'places | network' from another Ubuntu machine (DHCP) and from Windows.

But when I try 'places | connect to server | Windows share' I get a message 'Can't display location "smb://ubuntu/" , No application is registered as handling this file'.  [COLOR="Blue"]How do I fix this? - it looks like Samba isn't set up right.[/COLOR]

Sorry this is so long.  I thought it was a simple issue, but....

Thanks
Mike

---

