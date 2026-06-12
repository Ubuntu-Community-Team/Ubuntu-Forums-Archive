---
title: "Edubuntu - Configure LDM to start KDE not Gnome? 4 Questions."
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by siafulinux on 2007-08-22
[SIZE="2"]Hi all...

I have 4 questions here, the first is my main priority right now. Thanks for your help on this. I probably just missed something, but I cannot find anything on this.

I recently installed Edubuntu as a server on a 1.2ghz machine with 512 MB RAM. I have one system set up as a client using the Thinstation Universal Boot Disk. Everything boots fine, the system finds the server and boots into ldm. Had to lower the resolution on the server to get Gnome or KDE to load on the client. But it works.

Here are my questions:

1. This is my main concern right now. How do I get KDE to be the default login in the ldm display manager? I have searched all over and cannot find anything about it. I have to manually select it and with my family, they won't do it and then get annoyed with me.  :-) Besides there has to be a file somewhere to edit for this, but I cannot find it.

2. My second main problem is the sound. It works through the client just fine, however, lowering the volume doesn't affect the actual volume levels? 

3. I thought the client files were under /opt/ltsp/i386/ ? Why then does my server need to be at a lower resolution? Is there any way to change that so that the server uses it's own xorg.conf set up and the clients use the /opt/ltsp/i386/etc/X11/xorg.conf independently? Or is it doing this already and I just messed something up?

4. And lastly, as far as the network itself goes, how can I change the DHCP IP ranges for the clients? Ie: Instead of being 192.168.0.x, how can I change it to 192.168.1.x? I tried editing the /etc/ltsp/dhcpd.conf file, but then the client won't boot. What am I missing? The reason I want to change it is so that it will access my file server at 192.168.1.x.

Thanks for any assistance!

Siafu

[/SIZE]

---

