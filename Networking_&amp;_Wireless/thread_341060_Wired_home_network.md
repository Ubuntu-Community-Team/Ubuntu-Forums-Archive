---
title: "Wired home network"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by Obor on 2007-01-18
I'm new to all this networking stuff so I'm not sure where to start.

I have 2 computers running edgy and both connected to my router (linksys wrt54g) using ethernet cables and sharing my broadband internet connection. 

Now what I want is to share certain folders between both PCs. I guess this is pretty simple to achieve but I can't seem to figure it out ](*,)  

So far I tried the SSHFS from [here]("https://help.ubuntu.com/community/SSHFS") but it kept giving me "remote host has disconnected" message and nothing happened.

Since its a wired connection between only 2 computers I don't even need encryption :confused:  I just want to share my files. What is the best way to achieve this? A link to some good guide or any pointers would be appreciated.

---

### Post by jd65pl on 2007-01-18
You will need ssh server running on the machine you are trying to access files from. It will also need to be turned on [see cmd 1.]. Its may be useful for you to download nmap [cmd 2.] and use it to scan the server machine for open ports. I use sshfs it is very good and I have found it to be very easy to setup and stable.

```
1. sudo sshd
2. sudo aptitude update
sudo aptitude install nmap
sudo aptitude install nmapfe <--- only if you want a gui to nmap

```

---

