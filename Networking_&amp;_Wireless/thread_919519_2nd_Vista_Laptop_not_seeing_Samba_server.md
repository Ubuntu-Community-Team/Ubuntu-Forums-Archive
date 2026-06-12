---
title: "2nd Vista Laptop not seeing Samba server"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by esmurdo on 2008-09-14
Ok, I did a search and couldn't find an answer for my problem, so I'm hoping a new post will work.

I have a ubuntu 8.04 server setup with SAMBA for file and print serving (the printer issue will come later), and I can get my vista-based HP Pavilion 9910 to see it and connect to share the files.
But my problem lies in my wife's vista laptop is not even seeing the server. I've tried mapping, but I guess that doesn't work if the computer doesn't even see the server.

I have one user setup in ubuntu/samba, and the security is set to share. I've tried retracing my steps that I took to setup the first laptop, to include static ip, and WINS server. I may have missed a step, but I cannot remember what it is.

Any ideas?

---

### Post by gregphil on 2008-09-14
All machines need to be in the same "WORKGROUP".

Check your wifes machine (Control Panel=>System=>etc) for the workgroup or 'domain' setting.  If she doesn't need to connect to a work domain somewhere, change that to your Samba workgroup.

Also, you said you are using security=SHARE, but if somehow you are using security=USER you will need to add her as a user with smbpasswd -a HerUserName

It is possibile (with Vista....) that Microsoft has once agains "tightened security" and created some "user right" about access to network.  You could check in  "local security policy" "user rights" and see if she lacks any "right" named like that.

Good Luck.

---

