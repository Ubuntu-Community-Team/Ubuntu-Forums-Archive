---
title: "Help Please: Basic Samba Configuration Howto Please"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by rdbe on 2008-02-20
I have the following situation:

Live Ubuntu 7.10 CD finds my network shares (in this case Applerox  and Fantom 160) flawlessly under the Workgroup Folder through the standard file manager.

My hard drive installed Ubuntu version finds the Workgroup Folder but shows no shares.

I did enable file sharing based on another post that I found and it supposedly installed the necessary files for viewing my shares under Samba. This, however, did not work - and that is why I am writing this request for your kind assistance. Obviously, I am missing something quite basic since the "out of the box" live CD has no problems in this regard. Thank you for your help and I am sorry if this has been asked before.

David

---

### Post by lswest on 2008-02-20
can you see the shares if you (in nautilus) enter smb://[path to share] (something like smb://192.168.2.70/shares/  or so) in the address bar?  for me i can never just see shares, i always have to change to them like that.  Not really a problem for me, as i only have a printserver running, but see if you can connect to the servers like that.

---

### Post by rdbe on 2008-02-20
Re: Help Please: Basic Samba Configuration Howto Please
can you see the shares if you (in nautilus) enter smb://[path to share] (something like smb://192.168.2.70/shares/ or so)? for me i can never just see shares, i always have to change to them like that. Not really a problem for me, as i only have a printserver running, but see if you can connect to the servers like that.
__________________

I will try that at home - right now I am at work (using a Mac that has all this capabilities out of the box) - still love Linux though.

Thanks for the response. I really appreciate it.

---

### Post by lswest on 2008-02-20
no problem, i mean, if that works, you can create a mount shortcut on your desktop to the share points (it's what i do at school with my school drive)

---

