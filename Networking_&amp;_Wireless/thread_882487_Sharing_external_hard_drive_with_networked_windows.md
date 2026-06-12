---
title: "Sharing external hard drive with networked windows machine"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by Ban Mido on 2008-08-07
I used to use windows an i have an external hardrive which was shared in windows so my dad could save his music to it from his windows pc, but now i want to set it up so that i can be in linux using the hardrive and he can be on his pc and have access to it.

So how would i go about doing this:confused:?

-Ban Mido

---

### Post by jhazlecary on 2008-08-07
I just did this it was kinda fun. just install samba and create the share and give him a username on your box. there was one problem i hit but samba told me where to go to fix the config file to allow any user on the box to create shares. then all he has to do is use windows to map the drive as per normal but just use the linux-box user name and password

---

### Post by Ban Mido on 2008-08-07
Im kind of a noob to linux so could you maybe explain that a little more clearly. And where do i get samba.

---

### Post by jhazlecary on 2008-08-15
sorry about the time it took me to get back to you im a n00b too i have only been using this OS for about a month. so-- Samba i believe gets automatically installed when you right click on a folder and go to sharing then hit create share. Then its a quick jump to set up the user or group the share is for. there is one config file that i think you need to change but samba prompts you as to which one to change. then make sure firewall is open for the windows pc ie.. trust its IP address for inbound and outbound same goes for the firewall on the windows machine naturally. then its as simple as popping in the unc location from your windows machine ie \\server\share or use \\server_ip\share formats then make sure to use your linux box's username you set up prevoiusly on the share window. You can complicate things by adding additional users and setting privs but i have no idea how they work yet. let me know if you need any other info and i can try to help. there is one other thing that i remember running in to. is the usb drive NTFS? if it is theres another program that you need to run to get ntfs to run with read write access from linux and for the share...

---

### Post by jerome1232 on 2008-08-15
Okay will samba is pretty easy once you get the hang of it.
```
sudo apt-get install samba
sudo smbpasswd -a <user>
```

Now logout, then log back in. lets say your drive is /media/disk
pop open nautilus browse to /media right click disk click share. Now it's shared you should be able to walk over to your windows box and see it. If not turn off the firewalls on the windows machine for now and try again.

If that doesn't' work you may be in the wrong workgroup, what version of windows is this?

see if you can post the output of smbtree from the ubuntu box
```
smbtree
```

---

