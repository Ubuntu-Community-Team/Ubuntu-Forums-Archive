---
title: "Errors on shutdown CIFS network"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by steve_d on 2008-05-06
Workstation:
Ubuntu Hardy Heron
AMD dual core 4000+
2 gig ram
nvidia 8500GT

File Server:
AMD Duron
384 MB ram
500 gig HD
sharing NTFS partition

I've just recently followed a howto on mounting a windows networked drive as a location in ubuntu using CIFS.

This works perfectly and makes my life so much easier.

BUT on shutdown, the system hangs for much longer than it ever did before, and gives me errors. I have taken a picture of these errors, maybe someone knows what they mean, and can help me correct this problem.

Sorry for the blurry picture!

[IMG]http://i4.photobucket.com/albums/y149/steve_d/S3600018.jpg[/IMG]

Thanks!
-Steve

---

### Post by jetsam on 2008-05-06
They look like they are network manager related.  

I think it might work to disable roaming mode on your eth0 interface in network manager.  My understanding is that this means that network manager will no longer take charge of that interface.

I actually un-installed network manager on my gutsy server and desktop to get rid of similar errors.  You generally don't need it at all if you are only using a wired connection.

---

### Post by steve_d on 2008-05-07
Excellent, I changed the network manager over to dhcp and I don't get those messages anymore.

I'm hesitant to remove the network manager for now, never know if i have to go wireless at some point.

Thanks

---

