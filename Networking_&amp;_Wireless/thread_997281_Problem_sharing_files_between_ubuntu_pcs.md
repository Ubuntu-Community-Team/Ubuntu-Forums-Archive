---
title: "Problem sharing files between ubuntu pcs"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by nicocarbone on 2008-11-29
Hi everyone. I have a fairly complex network at home that consist in a WiFi router connected to the ADSL modem, two computers connected to it (one wired and one wireless) and another WiFi access point connected to the router (because the router is using a long distance antenna in order to connect to a neighbor house) with three PCs connected to it (two wired and my notebook by wifi). Of these computers, the notebook and one of the PCs connected to the access point have Ubuntu, and the others have Windows Vista or Windows XP.

My problems are:
1.I can't access folders shared by Ubuntu PCs from another PC with Ubuntu, but I can access these folders from the Windows PCs without problems. 
2.I can only access folder shared by Windows PCs from Ubuntu PCs if I write smb:// and the ip address of the Windows PC in Nautilus. If I go to Network in Places, Nautilus hangs for a while and don't find anything. 

Between Windows PCs there is no problem at all. I tested Ubuntu notebook in my campus network (which is even more complex than mine and also is a mix of Windows and Linux PCs) and it works fine. And I used Windows on both PCs that now have Ubuntu and never have a problem. I can use Remote Desktop using Vinagre between Ubuntu PCs with no problem and Internet works fine in all PCs.

I searched a lot and I can't find anyone with a similar problem. Sorry for the complicated and long post and for my lousy English, I hope I was clear enough for you to help me. Thanks you very much.

---

### Post by drbongo on 2008-11-29
You need to enable file sharing for the folders you want to share and/or put them in the public folder. You can right click on any folder and select sharing options to do this. Do this on all the ubuntu computers and you will be able to share files between them.

dsbongo

---

### Post by nicocarbone on 2008-11-29
Thanks dsbongo for your answer, but I am afraid that's not the problem. I did what you said and I have the folders shared in Ubuntu, and I can see them from the Windows PCs, but not from the other Ubuntu PC. Any other idea?

---

### Post by nicocarbone on 2008-12-13
No other ideas?? I'm still having problems with this and is very important for my work.

---

