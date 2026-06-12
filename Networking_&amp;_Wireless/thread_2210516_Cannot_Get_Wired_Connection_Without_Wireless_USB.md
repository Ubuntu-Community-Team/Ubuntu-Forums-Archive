---
title: "Cannot Get Wired Connection Without Wireless USB?"
date: 2014-03-11
forum: Networking &amp; Wireless
---

### Post by arsenic-creed on 2014-03-11
Okay, I hope this is the right section and not a repeat. I looked for something like this but couldn't find anything.
I have a wired connection and I was trying to set up a wireless one for my tablet. I have a wireless adapter but I've never managed to set up a connection on Windows or Ubuntu with it so I tried my sister's wifi USB adapter. I couldn't get that to work either and, honestly, I don't care any more. I give up.
The problem I'm having now is that, as the thread title said, my wired connection won't hook up without the wifi USB plugged in now and I, stupidly, did not keep track of the different ways I tried to get the wifi things to work so I can't just directly backtrack. I was thinking it might be because my computer keeps going into aeroplane mode but I don't know how to get it to stop. I can't turn off aeroplane mode without being able to get into the network connections, I can't get in there without the USB plugged in, and any time I unplug the USB or restart my computer it goes back into aeroplane mode.
Connect automatically is on for the wired and off for the wifi (as I just thought to check).
Is aeroplane mode a completely ridiculous idea for why it's doing this? Is there a way to get it to stop that?
Thanks for any help any one can provide.

(P.s. I'm on 12.10 and also have a Windows 7 dual boot but I don't seem to be having the wired problems there [which increases the likelihood of it being the aeroplane mode, I think, because Windows doesn't do that].)

---

### Post by arsenic-creed on 2014-03-12
I've gotten it now. I had to sudo open /etc/network/interfaces and edit it again. I guess I must have changed something when I was trying to get the USB adapter to work (I don't actually remember doing that but, considering my memory, that isn't all that odd) so I had to change it back.

---

