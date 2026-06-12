---
title: "how can i get 2 ubuntu ws see each other?"
date: 2005-04-09
forum: Networking &amp; Wireless
---

### Post by lorap on 2005-04-09
i've 2 ubuntu workstations connected to the router.i've given ip addresses on my own so no need auto authorization.moreower i've defined a the same workgroup for both pc^s in the network settings.regardless all this i still can't get them seeing each other.
does anybody have any ideas?
thanks.
pavel

---

### Post by joshmachine on 2005-04-09
What does "seeing" consist of?  
Are you looking to do some samba shares?
ssh?

Step one is to see if they can ping each other.

Step two will dependon what exactly you are aiming to do, but if you want to do samba (i.e. windows network browsing) you will have to set up some shares.  I think this can be done through the gui tools included in hoary.

I personally prefer to install ssh servers on my machines then use scp to move stuff around.

Cheers.

---

### Post by lorap on 2005-04-09
hi!
yes,i do want to have shears and see what workstation's on,but i don't have any windowsed ws.all pc^s're running linux ubuntu.
i knew that you should use samba when you do have a windows ws or am i wrong?
thanks.
pavel

---

