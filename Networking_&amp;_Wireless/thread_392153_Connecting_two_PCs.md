---
title: "Connecting two PCs"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by Roger D on 2007-03-24
Hi

I've got two PCs, my old PC and my new PC, both connected t o the Internet using wireless. Currently, I'm moving files from my old PC to my new PC by copying onto a USB stick. It occurs to me that it must be possible to mover files directly between the two PCs using my wireless LAN.

This must be a basic problem. Can anyone tell me how to start?

Regards

Roger D

---

### Post by 1/0 on 2007-03-24
Are they properly connected to a router? If so, they have IP numbers. Easiest way to file share is to use scp. Start GFTP and login with user name and password via SSH2 (or is it FTPS?) and that should be it.

---

### Post by PurplePenguin on 2007-03-24
I don't use a wireless network, but I'm assuming that connecting two computers will work pretty much the same way.

You can set up a network using either NFS or Samba.  If they're both linux machines, NFS will work (and I find it's quite easy to get up and running), but Samba will work between linux and windows.

I've never really used Samba, but I think it might be a bit more versatile... other people will hop in here sooner or later and probably support Samba.

[Here's a link that will get you started.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_share_folders_the_easy_way")  It's the section in the Ubuntu Guide showing you how to share folders easily (and the first link or two show you the basics, getting Samba up and running).

If I'm not mistaken, the first time you try sharing a folder, Ubuntu will realize that you don't have Samba installed and run the installer for you. (although I could be mistaken on this one!)

---

### Post by hoheszeh on 2007-03-24
I am not sure if it is the *best* way of connecting two local PCs, but thats how i did it 2 hours ago for the first time in my life.

I connected a desktop PC named "xerxes" with my laptop named "Leviathan". So what did i do?

(1) i told my Router to give both of these computers static IPs.

(2) I added a line to /etc/hosts on both machines. on xerxes i added the IP and name of Leviathan and vice versa on Leviathan.

(3) i installed ssh on xerxes only. 

```
sudo apt-get install ssh
```

(4) after that, on Leviathan i selected "places" from the ubuntu menu, then "connect to server". Here i choose SSH, entered xerxes for "server" and my username on xerxes in "username". After that a new icon was placed on my Desktop which allowed me to access xerxes and move data (xerxes is now my backup-machine)

I hope this helped.

---

### Post by Roger D on 2007-03-24
Thanks guys. It looks as though, for a fairly novice Ubuntu user like myself, shared folders is the way to go. Can anyone point me in the direction of a guide on how to use this GUI tood?

Best regards

Roger D

---

