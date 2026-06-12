---
title: "Edgy - Can't connect PCs on local network, but can reach the internet"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by tlsarles on 2006-10-12
I have 4 computers on my local network. 1 Runs Edgy, 2 run Dapper, 1 is XP. The XP and Dapper machines can all talk to each other fine. The Edgy box can not connect the local machines (I have tried several services : http, samba, and ssh). However it can access the Internet, and it can ping the local machines. I have no explanation for this. Any help would be appreciated. As far as I know I have no firewall, unless one is part of the default install.

---

### Post by SimonomiS on 2006-10-12
What did you do to get Dapper and XP connecting fine?

---

### Post by dannyboy79 on 2006-10-12
> **tlsarles said:**
> I have 4 computers on my local network. 1 Runs Edgy, 2 run Dapper, 1 is XP. The XP and Dapper machines can all talk to each other fine. The Edgy box can not connect the local machines (I have tried several services : http, samba, and ssh). However it can access the Internet, and it can ping the local machines. I have no explanation for this. Any help would be appreciated. As far as I know I have no firewall, unless one is part of the default install.

you're not using some kind of hosts allow and hosts deny in your smb.conf file are you? Also, what kind of error do you get when you try to connect via each of the ways. Please post the results of each connection. Also, are you sure they are all on the same subnet etc etc? Firewall issue?? Something sounds really weird about this and I am sure it's something very small! We'll figure it out just give us the info I asked for. Thanks and we'll chalk up another solution.

---

### Post by tlsarles on 2006-10-12
OMG, i figured it out, and its completely my bad.

I had statically set the edgy box's IP to the same as the dapper box I was trying to pull some files from. Sorry to waste your time.](*,)

---

### Post by miky on 2007-01-27
i am happy you have solved your problem, but there was interesting question...how did you make win xp and dapper visible to each other? i can connect from dapper to xp, but i do not see my dapper from xp at all.:confused: 
thanks

---

