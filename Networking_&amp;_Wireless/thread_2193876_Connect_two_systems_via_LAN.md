---
title: "Connect two systems via LAN"
date: 2013-12-15
forum: Networking &amp; Wireless
---

### Post by chris137 on 2013-12-15
Hi,
I got my PC and my notebook here and I am trying to connect them with a LAN-cable and transfer files between them.
The connection is up but I do not know how to proceed now.
I could connect with ssh but I would like to have a graphical interface where I have full access.
Is this even possible?
I don't want a shared folder but access to the complete drive.

I tried this because I wanted to download stuff with Deluge directly to the other's harddrive.
Besides I do not know how to properly connect the two systems I think this won't be possible with Deluge.
Am I wrong, are there alternatives or is this not possible at all?

&#8364;: Just came up with the idea to mount the drive like a network-drive.
I guess I'll have to make a few changes on my computer.
Important is just the direction notebook->PC.
It is not the drive where ubuntu is on but a second one. I hope this makes it more easy.

---

### Post by chris137 on 2013-12-15
The best solution is always the one you find yourself.
So did I.
My last idea (mount the drive) was not very easy - for me as a semi-beginner - but I managed to make it work.
I used the nfs-server and simply mounted the drive with its IP-adress I configured before.
I hope this will be useful for another user with the same problem.

---

### Post by chris137 on 2013-12-16
So I mounted 4 disk now.
Both SATA-disks I have inside my PC are accessable from my notebook but my two USB-drives not.
I do not know if it's by coincidence or not.
There were no errors when mounting it and there aren't now.
It just won't load.
Either via terminal (cd xx) oder in nautilus there just won't happen anything at all.

---

### Post by chris137 on 2013-12-17
Alright so I solved it now.
I had some help from someone who knows a little bit more but he isn't really sure either what led to the solution.
After a few tries a finally managed to access my USB-drives. But when I discovered then, that in exchange one of the other - before working - drives had the same issue now I nearly lost it.
But after a lot of typing, guessing, etc. I got it.
Probably the modes were not set properly.
chmod did not work so I did some stuff - as said not quite sure because I didn't get half of what I typed there.
I mounted my USB-drives so that they would not get a new dev name after every reboot.
With this I could put them into fstab and now everything works.

Sorry I can't provide you with any information on how I did it exactly, if you have a similar issue but I just can not remember.
I tried so many things, I just don't know.

---

