---
title: "How do I set up a (wireless) network?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by funky_uncle on 2009-01-19
Hi, I'm feeling kinda smug that I got a wireless router to work with both my laptop and my netbook, though I'm not 100% sure exactly how I did it. Pretty much a noob at anything networkish.

Anyway, I'd like to share files between my desktop and laptop, but I can't for the life of me figure out how to do that. I suppose I need to create a new network somehow, and connect both computers to that (as well as the internet of course). I searched these forums and the help files but I'm none the wiser.

I'm running Mint (I think it uses the Hardy Heron kernel) on my desktop and Eeebuntu on my laptop.

---

### Post by Titan8990 on 2009-01-19
If they are both using the same router to connect to the internet then they are already on the same network. This is handled by your router than functions as a DHCP server and assigns addresses to your computers within the same network.

You just need to set up a server program that will host and share files.

NFS would be ideal for this: [http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

---

### Post by funky_uncle on 2009-01-19
> **Titan8990 said:**
> NFS would be ideal for this: [http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)I guess I'm noober than I thought, that pretty much went over my head...

I right click and go to "Share Options" on a folder, click on "Share this folder" and I get this:

[I]'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.[/I]

I AM the administrator. Or so I thought.

(This happens only on my desktop PC, not on the laptop.)

---

