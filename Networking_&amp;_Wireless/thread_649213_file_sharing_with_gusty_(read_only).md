---
title: "file sharing with gusty (read only)"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by syncdram on 2007-12-24
Ok i have 3 computers 2 running gusty and one running fawn. All 3 are networked. On all 3 computers i have folders that are shared on each pc. I can see all 3 pcs on my network on any one of the 3 computers. I can see the shared folders on any one of my three computers. I can open the shared folders on anyone of my 3 computers but i cant drag or drop between any of them or open any pictures. says i do not have permission. Can some one please tell me how to straighten this out so whatever computer i'm sitting at i have full rights over the network please. Ken:confused:

---

### Post by Meatetarian on 2007-12-24
How are you sharing the files?

The way your post reads it sounds like you're maybe using Samba?

If that's the case, you need to edit /etc/samba/smb.conf and modify the shares you want write access to by adding "writable = yes".

Sorry if you already knew that all that and I was no help whatsoever!   D=

---

### Post by syncdram on 2007-12-25
Thanks for the quick reply. Yes i am using samba, I will edit those shares and let you know how i made out. Here is what i think your talking about.

 [downloads]
path = /home/syncdram/Desktop/downloads
available = yes
browsable = yes
public = yes
writable = no



comment = shared foler on desktop
[Pictures]
path = /home/syncdram/Pictures
available = yes
browsable = yes
public = yes
writable = no
comment = shared folder on desktop

These are the 2 folders i have shared i guess i have to change no to yes for writable?:)

---

### Post by syncdram on 2007-12-25
Ok changed no to yes on each of my networked pc's that have shares, rebooted went back in to the network and now none of any of the computers are showing up.  Do i need to do more?:confused:

---

### Post by Meatetarian on 2007-12-26
Sorry it took so long for the reply!  Maybe you've got this sorted out by now, but if you pasted those lines right from your smb.conf, then it might be an easy fix -- I think you spelled "browseable" wrong.

In case that doesn't work, though, here's one of my shares as an example.  While I don't understand why, I know my Windows box couldn't see my shares until I included the volume information.

[WriteShare]
   path = /media/sdb1/WriteShare
   comment = Write Share
   browseable = yes
   writable = yes
   volume = BIGHD

Hope that helps!

---

