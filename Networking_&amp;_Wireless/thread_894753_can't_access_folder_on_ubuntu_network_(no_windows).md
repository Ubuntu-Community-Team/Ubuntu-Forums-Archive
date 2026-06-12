---
title: "can't access folder on ubuntu network (no windows)"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by wolfen69 on 2008-08-19
i want to setup a network between my desktop and laptop. i installed samba and have nfs-common on both machines. i created 2 shared folders. 1 on the laptop and 1 on the desktop. on the desktop, when i go to places>network i see both machines and can access the shared folder on the laptop from the desktop. on the laptop, when i go to places>network, i only see windows network. i can find the desktop machine in windows network, but when i try to access the folder, it says: "failed to mount windows share".

i've spent many hours trying everything i can find, but still no luck. any ideas? any help will be MUCH appreciated.

---

### Post by wolfen69 on 2008-08-19
update: on the laptop,i can now see both machines when i go to places>network, without having to go into windows network. however, i still get "failed to mount windows share" when trying to access the desktop folder. I'M GOING BACK TO WINDOWS! just kidding. there must be a network guru somewhere. please?

i'm assuming this is a problem with the desktop machine, since nothing on it (shares) will mount from the laptop.

---

### Post by Iowan on 2008-08-19
The usual questions: You installed the server? Is it (smbd) running? Both machines are in the same workgroup? Desktop doesn't have firewall interfering?

Try **nmblookup -T '*'** from laptop to see if desktop shows up.

---

### Post by wolfen69 on 2008-08-20
thanks for the reply. i'm at my wits end here. i've spent the last 12 hours trying everything i know, and everything i can find online. i'm beginning to think it's impossible to network these 2 computers. 

i've set the domain name the same for both. i have nfs-common, nfs-kernel-server, and samba. both users are part of sambashare group, file sharing services are started, samba is started. i don't know what else to do. 

ok, (i took a break there) i have it now that i can access the laptop perfectly. (access files, make changes) but i still cant get past "failed to mount windows share" when using the laptop to access the desktop. maybe mount them manually?

thanks for any replies. i'm almost there! c'mon guys.

---

### Post by cariboo on 2008-08-20
Have you tried using the /etc/samba/smb.conf file from the laptop on the desktop?

Jim

---

