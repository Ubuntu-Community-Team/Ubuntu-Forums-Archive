---
title: "Can not browse windows shares"
date: 2019-02-19
forum: Networking &amp; Wireless
---

### Post by open4junk on 2019-02-19
My system: lubuntu 18.04.2 - fully updated
Machine: Aspire One 756
RAM: 4 GB
Samba, cifs-util, smbclient, etc, installed

Issue: open pcmanfm, local p.c. and windows network icons displayed. Double click on windows network icon and an empty window is displayed with smb:/// on the search line. After searching for a resolution I have discovered a way to avoid having to type in the ip address of the desired pc to which I want to connect (inserted client max protocol = smb3 in smb.conf and bookmarked each p.c. connection). However, this seems like a lot work so, I ask is there any information about when or if there is going to be a solution to this issue? I am just a user not a programmer, so I am not sure if I even understand the technical aspects of correcting this, at the same time it would seem that since this is a prevalent problem it would be addressed-and maybe it is so I am just asking.

thx

---

### Post by Morbius1 on 2019-02-19
Yep browsing for smb hosts is broken. Doesn't mean you can't access them explicitly but you cannot discover them - at least not if the other machine is running Windows. Discovering another Linux or MacOS machine is a different story. Please see this for a workaround if applicable: [https://ubuntuforums.org/showthread.php?t=2384959](https://ubuntuforums.org/showthread.php?t=2384959)

Side note: Not that it matters but the setting of max protocol to smb3 is unnecessary:
> (inserted client max protocol = smb3 in smb.conf and bookmarked each p.c. connection)
If you run the following command:
```
testparm -sv /dev/null | grep "client max protocol"
```
You will see that client max protocol is set to "default" and per the man pages for smb.conf:
> The value default refers to SMB3_11.

---

### Post by wgrobinson on 2019-09-06
I have been chasing this problem literally for years.  Browsing a Windows network has never worked for me over many years and many distros.  I find most of the discussion regarding this as utterly useless and pointless. Until I fouldthis "it's broken' thread I wasted hours trying things that didn't work using commands that were syntacicly incorrect. I programmed my first computer in 1966 and I find this long-time broken basic function - well - disgusting.  Thanks for allowing me to stop trying to fix this - this time.

---

### Post by coffeecat on 2019-09-06
OP hasn't been back since shortly after they posted. Old necro-hijacked thread closed.

@wgrobinson, if you want help, please start your own thread.

---

