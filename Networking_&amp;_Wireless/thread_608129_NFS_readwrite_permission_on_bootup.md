---
title: "NFS readwrite permission on bootup"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by Oak37 on 2007-11-09
Hi guys,
I installed NFS a few weeks ago and have had great success with it. However I got sick of mount the volumes I needed everytime I booted up my laptop so I googled around and edited the fstab file. That worked too but I'm having trouble with read write permissions. In the fstab file, under options, I have rw entered but when I view the volumes I can't create a new file or paste new files into the volume. Here's an example of what is in the fstab file:
```
192.168.2.3:/home/david/Desktop/PAM /home/david/PAM	nfs	auto,sync,user,rw	0	0
```
Any ideas?
Thanks :)

---

### Post by satx on 2007-11-09
Use SAMBA and smb4k to manage filesharing, etc.

---

### Post by Lambert on 2007-11-09
> **Oak37 said:**
> Hi guys,
I installed NFS a few weeks ago and have had great success with it. However I got sick of mount the volumes I needed everytime I booted up my laptop so I googled around and edited the fstab file. That worked too but I'm having trouble with read write permissions. In the fstab file, under options, I have rw entered but when I view the volumes I can't create a new file or paste new files into the volume. Here's an example of what is in the fstab file:
```
192.168.2.3:/home/david/Desktop/PAM /home/david/PAM	nfs	auto,sync,user,rw	0	0
```
Any ideas?
Thanks :)

Did you have problems rw when mounting manually from the command line? 

> **satx said:**
> Use SAMBA and smb4k to manage filesharing, etc.

could you explain this more. I have a linux server, with a linux laptop and imac sharing an nfs folder from the server. This set up works perfectly for me. What would samba offer that nfs doesn't?

---

### Post by Oak37 on 2007-11-10
> **Lambert said:**
> Did you have problems rw when mounting manually from the command line? 
No, I have the read write permissions when I mount it manually.

So far I've only networked Ubuntu PCs, so I was avoiding using Samba until I decide to bring in my Windows PCs.

---

### Post by satx on 2007-11-10
Lambert-

Sorry, misread your post. NFS in that environment is probably best.

SATX

---

### Post by Lambert on 2007-11-10
> **satx said:**
> Lambert-

Sorry, misread your post. NFS in that environment is probably best.

SATX

Ok thanks, I'm still learning this stuff as I just set up a server for the first time for central storage. Just curious if I was missing something. 

If I had a windows pc I would have to look samba I guess but I have no interest in a pc with windows at the moment.

---

### Post by Lambert on 2007-11-10
> **Oak37 said:**
> No, I have the read write permissions when I mount it manually.

So far I've only networked Ubuntu PCs, so I was avoiding using Samba until I decide to bring in my Windows PCs.

try adding nosuid to the options

```

192.168.2.3:/home/david/Desktop/PAM /home/david/PAM	nfs	auto,sync,nosuid,user,rw	0	0

```

---

### Post by Oak37 on 2007-11-10
> **Lambert said:**
> try adding nosuid to the options

```

192.168.2.3:/home/david/Desktop/PAM /home/david/PAM	nfs	auto,sync,nosuid,user,rw	0	0

```
Didn't work. When I manually mount them I use the sudo command, do you think that would be causing the issue? Thanks for your help so far

edit: After looking around it seems that if the user ids are different for the two computers then read-write permission won't be given. However when I checked the uids of both computers they are both set to 1000. There was also some mention of maproot but I'm not too sure how that works

---

### Post by Lambert on 2007-11-10
this is puzzling but I'm also new to using nfs so maybe someone else sees something. It can be mounted manually or automatically but why does permissions vary depending how it's mounted?

I'm now wondering the difference when a mount is done from fstab compared to a sudoer. I don't have this problem though so what is different?

Next step I would suggest is looking at the /etc/exports file on the exporting pc to see how that's set up. But there shouldn't be a problem there if you can rw when mounted from cli.

After trying to mount from fstab, also check the /var/log/messages file for any output related to the process.

---

### Post by Oak37 on 2007-11-10
Both the user ids and the group ids all match up and seem fine so I'm at a loss where to go next with this :confused: Still, it's not essential (I can still read and access the remote files) and I learned a lot of new things on the way which is what it is all about!
I looked at the exports file and everything was working fine there and I could see no mention of it in the messages log. Thanks for your help, much appreciated :)

---

