---
title: "Setting up Home Network"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by yashoda on 2007-10-30
Hi, I'm running Gutsy on my laptop, and XP on PC, each connected to a wireless belkin router.

Please advise me how to easily setup a secure wireless home network so that I can share files between the two computers, preferably without using the Terminal too much.

I've downloaded samba, and the Pyneighbourhood gui.  

Thank You.

---

### Post by sonicsmooth on 2007-10-30
As I understand, there are basically 2 ways: use SAMBA or use NFS.

Supposedly NFS is faster than SAMBA, but SAMBA will allow other Windows users to connect to your network if they are in your house, and will connect more "naturally" with your windows machine.  i'm not aware of any ubuntu tools that will allow you to set either of these up via a gui, but there may be one someplace; it looks like you found one.  Although I haven't gotten either of these to work in my setup (!!!argh!!!), in theory these are pretty simple to set up.  I'm pretty sure there are NFS cilents for Windows too.

I'm pretty sure in either case you need to set your router to issue the same IP address to each machine when it connects, but I'm not sure.  Certainly it must for the server.  Either that, or make sure the server's address is never released by the DHCP program coming from the router; that is, you must get the ip address, set the router to assign DHCP leases forever, and then never power either of them off.

Once you have a reliable IP address to your server from your router, you need to set up the /etc/hosts file in each of your client machines.  This allows the client machine to use the name of the server instead of the ip address.

At this point it makes sense to find the NFS-howto and the SAMBA-howto.

For NFS (which is all I remember), on the server side, you create (or modify) the /etc/exports file to tell the server which directories are available for sharing.  There are a few options which you can read in the howto.  On the client side you then add a line in your /etc/fstab which says the server name to use, the directory to import from, and the (currently blank) target directory which you just created on your client side.  Since I'm not on my actual machine at this exact moment I can't give you an example but I'm sure there's one in the howto.

Anyway, most of the howtos generally dive directly into the details without telling you the high level of what you're trying to do .  Hopefully this helps.  You can find the exact details in the howtos.

BTW this all assumes your wireless cards are connecting to the router to begin with.

Michael

---

### Post by yashoda on 2007-10-30
Hi Michael,

Thanks for replying.

Yup, everything's connecting to the router.  Will check the howto docs, n let u know.

---

