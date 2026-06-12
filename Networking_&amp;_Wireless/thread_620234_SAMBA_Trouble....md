---
title: "SAMBA Trouble..."
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by fcoster on 2007-11-22
I have a Gutsy computer which is connected wirelessly to my router. It has all my music on it.  I like to do a simple samba share of the music folder so that I can listen to the music on my computer upstairs from downstairs.

I have shared the Music folder from the Administration->Shared Folders (or somesuch) option.

Downstairs, on my older slackware box, I used to use this command:

> mount -t smbfs -o fmask=444,dmask=555,guest //ubuntu-desktop/music /mnt/music

Until recently this has worked. (I'm unsure what changed; an update perhaps?). The Gutsy computer is still saying that it is sharing the music folder; and if I do a 

> ps -A | grep "smb"

I can see that the samba daemon is running. 

But when I run the command on my slackware box now, it times out and is trying to contact an IP that is not behind my router. (It is a 72.51... ip; not a 192.168 ip).

I can still ssh from the slackbox to the ubuntu-box. I just don't get it. Any thoughts?

Thanks again, as always; the ubuntu community is remarkable.

-fcoster

---

### Post by jetsam on 2007-11-22
It might be a simple solution to replace 'ubuntu-desktop' in your mount command with the lan ip address of the computer you're sharing from.  

Can you set your router to reserve a specific ip address for the computer with the music on it so its ip address is always the same?

---

