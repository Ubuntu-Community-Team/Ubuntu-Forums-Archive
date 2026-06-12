---
title: "Ubuntu/Windows Networking"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by microbyte on 2007-07-29
I'm sure you're all tired of these questions, and I did try searching all over for an answer, but I still can't find a solution.

I'm looking to get my new Ubuntu PC to work with my other windows ones through the network I have set up, as well as possibly doing printers too.

The only problem is, I can't quite get anything to work. I've installed samba, read the guide by stormbringer, and can see my linux pc from my windows ones, but I can't access it at all.

Any ideas on how to achieve my goal? I'm wishing there was a simple way like apt-get please fixmynetwork or something. ;-)

Thanks!

---

### Post by bash4fun on 2007-08-01
did you modify already any security
settings in "/etc/samba/smb.conf" at all?
because you will have to create an
samba user or enabling anonymous logon
to provide access from a windows pc
onto a share or service

---

### Post by ugm6hr on 2007-08-01
> **microbyte said:**
> Any ideas on how to achieve my goal? I'm wishing there was a simple way like apt-get please fixmynetwork or something. ;-)


Not that easy - but not far off :)

[http://ubuntuforums.org/showpost.php?p=3113048&postcount=2](http://ubuntuforums.org/showpost.php?p=3113048&postcount=2)

Have a look at my sig below.

---

### Post by microbyte on 2007-08-01
Okay, I did get some stuff to work.

I found I was able to browse my other network computers using smb://their.ip.address. I think part of the problem was the file browser put it like this: smb:/// with three slashes.

I then mapped one of my computers to a folder in my home directory. It seemed to be working pretty good.

I still can't access the Ubuntu one from my Windows PCs. I did add a user for one of my XP PCs, but still no go.

I'm not using WINS, so I just tried to browse it in My Network Places, and map it with it's IP address, but nothing worked.

Any more ideas?

---

