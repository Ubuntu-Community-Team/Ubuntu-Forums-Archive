---
title: "Ksedu Problem"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by teogin on 2007-12-06
A Ksedu Problem Prevent Me From Have Privilege Rights On Configure Manual Ip From Desktop Interface.  I Need To Do It By Command.
But I Do Not Know What To Do.
My Server Is 192.168.251.1 Mask:255.255.255.0
And I Want To Give To My Pc The Address 192.168.251.2.
Would You Help Me Please?

And Why When I Try To Give My Password It Refuses To Give Me Rights By Saying Ksedu Problem.
Recently, I Upgraded To Kubuntu 8.4 From Kubuntu 7.10.

Thank You In Advance.

---

### Post by aysiu on 2007-12-06
Are you trying to do *kdesu*?

*kdesu* is not the same as *ksedu*

---

### Post by teogin on 2007-12-07
Sorry, I am a newcomer in Kubuntu world. I tried to get into system settings for set a manual ip and I needed to have privilege rights by giving my password.  I gave it and it said that there is a (ksedu or kdesu) problem and it keeps being disable, so I cannot have access to my ethernet and wireless cards too.
So, I wonder if the command console would be the exit for my problem.  But I do not know the suitable commands.
Would you give me the recipy? I need to set a manual ip to my ethernet (eth0), a setting command for the mask and one for the gateway I have found the dns command.

Thank you in advance.

---

### Post by viking777 on 2007-12-07
There is an open bug on launchpad about a similar issue which also contains a workround: [https://bugs.launchpad.net/ubuntu/+source/kdesudo/+bug/172749](https://bugs.launchpad.net/ubuntu/+source/kdesudo/+bug/172749)

See if that fixes it for you.

---

