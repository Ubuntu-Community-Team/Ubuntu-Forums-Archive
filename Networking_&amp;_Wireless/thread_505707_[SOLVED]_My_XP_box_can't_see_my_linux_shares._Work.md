---
title: "[SOLVED] My XP box can't see my linux shares. Works the other way around"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by banjopikker on 2007-07-20
I have  xp pro installed on one of my computers and ubuntu feisty on the other. I have been trying for days to get my home lan to work correctly. I have samba installed and have followed the numerous advice that has been posted. My ubuntu box can see my shared files on xp but xp can't see the files on ubuntu. I can see the linux  box from  "my network places" , "view workgroup computers ". When I click on it,  it tells me that I don't have permission to view the resource. I have a DLink router. What am I doing wrong? Other than the networking problem everything else works great. Thanks

---

### Post by lisati on 2007-07-22
How are your Samba and SSH settings?

---

### Post by banjopikker on 2007-07-24
Hi Lisati,  I'm sorry I can't answer your question as I am a noobie when it comes to networking. I have always relied on windows to set it up  for me.  I have a D link router  with 4 computers connected, 3 of which are running XP Pro and this one with Uuntu feisty Fawn. I have opened a terminal and followed the instructions from this forum with no good results.  I didn't get any error messages . I can see the files and folders on my XP computer from ubuntu  ,but I can't see the ubuntu computer. I know I am missing a step somewhere but with my limited knowledge of networking, I am pretty much lost.  Thanks

---

### Post by scxtt on 2007-07-24
on the ubuntu host:

sudo smbpasswd -a <user>
(example: sudo smbpasswd -a banjopikker)

where <user> (and the password it prompts for) are the same as they are in windows, that's generally easiest ...

---

### Post by banjopikker on 2007-07-24
The password that I log onto windows is different than Ubuntu password.

---

### Post by banjopikker on 2007-07-24
Thanks a bunch . My goodness that worked. I was putting in the password for the ubuntu machine. I put in the logon and password for windows ,clicked on my network places and there they were. Thanks so much.

---

### Post by ZX3Junglist on 2007-07-24
Scxtt,

your advice worked like a charm, thank you.

For the completely initiated, in order to set the smb password for a user, I had to first go to **System -> Administration -> Users and Groups** and click **'+ Add User'** to create a user before adding the smbpasswd for it.

---

### Post by scxtt on 2007-07-24
smbpasswd wiill work w/ any existing linux account ... i only recommend using the same creds as your windows account since that's what will be passed first ... otherwise, you could use the "map network drive" and use "connect using a different user name" ... if you click on the share, and your windows creds don't work on the linux samba server, it should pop up a login box ...

---

