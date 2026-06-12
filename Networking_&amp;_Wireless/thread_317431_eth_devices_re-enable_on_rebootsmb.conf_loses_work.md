---
title: "eth devices re-enable on reboot/smb.conf loses workgroup"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by urbancontra on 2006-12-12
I posted this in the beginner forum a couple days ago, but didn't get any replies.  Maybe someone here can shed some light on things.

I installed Kubuntu 6.10 a couple days ago and got pretty much everything I need working on my own, but I have a few questions I can't figure out on my own. I haven't found anything with Google or the search here (maybe my search isn't good enough!)

I have Samba running on this box to share out folders to my Xbox. I edit /etc/samba/smb.conf with my workgroup name and everything is awesome. After I reboot, though, I can't reach my shares with my xbox. I open up smb.conf again, and the "workgroup =" and "server string =" lines are gone. The rest of the stuff I added manually is there. What gives? I followed these directions originally to get it working: [http://www.xboxmediacenter.com/wiki/index.php?title=Linux_File_Sharing_%28using_samba%29](http://www.xboxmediacenter.com/wiki/index.php?title=Linux_File_Sharing_%28using_samba%29)

Also, every time I reboot, I have to disable ath0 (a wireless card in my box I only use in case of emergencies) and eth1 (my motherboard has 2 NICs and I dont use the other one). I do this through the "network settings" area in "system settings" from the K menu. I'm obviously a long-time WIndows user and I don't know what the terminal commands are for a lot of things, including this. Is there a better way to tell linux to disable these devices permanently?

---

### Post by TorenC on 2006-12-12
Ok, the overwriting files thing it really strange. What are the timestamps on the smb.conf file?

As for the interfaces thing, you try manually editing the /etc/network/interfaces file, or you could install knetwork-manager and just let it handle everything (unless you're statically addressing your machine, then don't install it).

---

### Post by urbancontra on 2006-12-12
Okay, the ONE TIME i try to repro a problem and I can't.

The difference is, usually when I reboot the system, X shuts down, then I get a black screen and have to reboot using the case button.  THIS time, the reboot was clean, and smb.conf didn't change.

So, what's causing it to lose that info when I don't get a clean reboot?

My ethernet devices were all enabled after the clean reboot, though.  I'm gonna try knetworkmanager and see if I have better luck.

---

### Post by KittyChunk on 2007-05-29
I'm running Kubuntu 7.04 on my laptop, and I'm getting the same problem with something erasing chunks of the smb.conf file periodically. Particularly the Workgroup and Server String info, which is fairly important on our network of a few hundred (Windows) computers, and the user authentication section, which obviously borks access if it's partially or completely missing.

It usually happens after a system reboot or shutdown - simply restarting Samba on a running system preserves the file as it should. Any thoughts as to what could be causing this?

---

### Post by urbancontra on 2007-05-29
I installed Ubunbtu 6.10 shortly after because of all the weird problems I was having and everything worked fine.  Not the most elegant solution, but I'm still clueless as to the cause of the problem.

---

