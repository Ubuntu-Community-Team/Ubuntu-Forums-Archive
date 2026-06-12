---
title: "Windows shares are lost after several minutes"
date: 2018-10-15
forum: Networking &amp; Wireless
---

### Post by heldmar on 2018-10-15
Hi, I am working on an office environment which is all Windows based except for me. 

The office has a Windows server that is shared among all persons in the office through Active Directory. I was able to set up my access through Samba long time ago, I initially had no issues, after a while (and probably a Windows Server update which I am not informed of) I lost connectivity and it resulted in me having to tweak my samba configuration to make sure it used SMB2 protocol (forced).

Now, the issue I have is that when I turn on my computer and I plug my ethernet cable to start my day it would open the share (through Gnome File Explorer), I am able to access everything, however, if I for example leave it opened and then lock my computer and get back, or if I simply don't open the sharing for a while, etc, it simply "loses" the connectivity. What I mean is if after I log in to my computer I don't immediately open the Windows share and use it, or if I open it but not actively use it for a while, when I try back it will simply fail and give me an error saying it has "An Unhandled Exception" and won't open it. I have to disconnect from the Ethernet and re-connect again in order for it to "remember" the network share and therefore work again. This makes no sense, because the server uses an internal IP of the 10.X.X.X type, so it is not changing IPs or anything.

This is kind of frustrating, I mean, it doesn't seem to be a configuration issue because it partially works, printers for example always work and they all are in the same network, it only will fail after a while. I haven't been able to find anything in the log files, in fact, I don't even know in which specific log file to look for as for samba logs it generates a log per each device you see online + generic logs, so I don't really know where to look and where I have looked there is nothing that gives me any hint.

I hope someone has had this issues and knows how to fix it, it seems to be something stupid but I can't find it.

---

### Post by TheFu on 2018-10-15
Have you tried troubleshooting using smbclient and NOT using the GUI?
Simplify and test is a general method for troubleshooting.

You can mount CIFS shares using either autofs or /etc/fstab which won't use GVFS like the GUIs do.

The logs are in /var/log/samba/ - look for errors and warnings.

Just a few thoughts.

---

