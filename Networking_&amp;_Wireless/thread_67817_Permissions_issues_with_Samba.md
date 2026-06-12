---
title: "Permissions issues with Samba"
date: 2005-09-21
forum: Networking &amp; Wireless
---

### Post by AndyCooll on 2005-09-21
I've been struggling with this for a week or two now and can't seem to get my head round the problem. I've been searching on these boards, trying the man pages (though often not understanding what I'm reading as I'm a Linux newbie), but nothing seems to answer my problem.  :-? 

One of my Linux boxes doesn't seem to allow a share access when logged on from another pc as a different user.

I have three networked pc's (2 Ubuntu's, 1 WindozeXP) I want to share both mine and my wife's home directory on each. We have the same logon and password on all the pc's.

I've successfully set up Samba, security=user, encrypt passwords etc. This is what I can access so far:
For both users on Linux1 box -  I can access all the Windows pc shares, all shares on that same Linux1 box, but only the shares on Linux2 of the user logged on (i.e if I'm logged on to Linux as me I can see my own share folder on Linux2 but not my wife's) 
For both users on Linux2 box - I can access all Linux1 box shares, All Windows shares, but not the other users shares
For both users on Windows pc - I can access all Linux1 box shares, All Windows shares, but again only the logged on users share folder on Linux2 box

I think this is a permissions problem with that Linux2 box not allowing shares access to folders other than their own. As far as I'm aware I've set up both Linux pc's in exactly the same way, however...

Anyone got any ideas? What parameters might I need to re-check to see if they are correct?

---

