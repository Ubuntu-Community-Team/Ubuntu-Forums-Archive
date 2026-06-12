---
title: "Somebody tell me how to add a password to samba"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by Joey French on 2006-10-13
Hi all, just started using smb4k for KDE to administer samba. I've got one winXP box and one Kubuntu edgy box. The edgy box has the printer. I can see everything on both boxes, but can't get to the edgy box-from the edgy box. When I click on the edgy box, it asks for authentication, so I use my username and password, no deal. Interestingly, the Win XP box gave no trouble when the password was added, and can browse that system freely. I want the winXP box to be able to use the printer and the large USB harddrive with my music collection on the edgy box.

I just need to know how to get the password authentication, then I will be good.

Thanks, Joey

---

### Post by almax00 on 2006-10-13
smbpasswd <user> -- substitute an actual user name for <user>. you can also use root for <user> i believe.

---

### Post by Joey French on 2006-10-13
Thanks, I'll give that a try. Last time I tried to set it up, I ended up breaking sudo. Hehe...

Joey

---

