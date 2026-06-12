---
title: "Networking for newbies"
date: 2005-09-13
forum: Networking &amp; Wireless
---

### Post by jbrader on 2005-09-13
I've been using my two linux computers independently for a pretty good while now but I think I'm ready for a real home network. What I want is to be able to access the external firewire drive on my desktop from my lappy over the wireless network and to share the printer so I don't always have to swap wires around. And In a few months I'm probably gonna get a windows box for gaming. So does anybody out there know any good guides for NFS Samba and printer sharing. They don't need to be on a "For Dummies" level as I'm pretty computer savvy but should start from the beggining as networking is fairly new to me. Thanks.

---

### Post by s_p_a_r_k_y on 2005-09-13
if your getting a windoze boxen I suggest samba. Its not terribly difficult to setup. Take a look at /etc/samba/smb.conf file. At the bottom of the document are your shares. In the [global] section are your settings (netbios name...and the such, security levels...etc).

I suggest sharing printers through the cups backend. I recently setup this for a small real estate company and found a few good tutorials online through google. Give it a try, if ya come up dry i'll look something up.

---

### Post by johnv on 2005-09-13
Hey Guys,
I am new to Ubuntu and linux and I want to set up Ubuntu as a file/print server.  I have 1 other linux box running Xandros and 4 boxes running windows xp.  

Since I am new to both Ubuntu & Linux, i was wondering where I can find out how to set this up.  I tried to get it to recognize my windows network, it sees it but cannot connect to the shared drives at all.  Xandros box can connect and d/l files from the XP boxes no problem. 

Your help is greatly appreciated!
Cheers!

---

### Post by tbasten on 2005-09-13
[QUOTE=johnv]Hey Guys,
I am new to Ubuntu and linux and I want to set up Ubuntu as a file/print server.  I have 1 other linux box running Xandros and 4 boxes running windows xp.  

Since I am new to both Ubuntu & Linux, i was wondering where I can find out how to set this up.  I tried to get it to recognize my windows network, it sees it but cannot connect to the shared drives at all.  Xandros box can connect and d/l files from the XP boxes no problem. 

Your help is greatly appreciated!
Cheers![/QUOTE]

Use Samba, Samba is pretty powerful. It can be setup as a PDC etc... They are a few how-to's on the web. Dont have any one me at the moment but when i hop onto my computer i will post the url for the tutorial. Its pretty simple to setup though, just need alittle bit of patience and a computer to mess with till you master it.

It took me about 4 hours to get samba to do exactly what i want it to do

Regards

dYnA

---

