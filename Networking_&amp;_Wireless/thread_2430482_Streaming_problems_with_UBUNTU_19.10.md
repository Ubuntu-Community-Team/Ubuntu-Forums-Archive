---
title: "Streaming problems with UBUNTU 19.10"
date: 2019-11-02
forum: Networking &amp; Wireless
---

### Post by Davethehedgehog on 2019-11-02
I like to stream music from my desktop to my SONOS sound system and also to stream video and pictures to my Panasonic TV. This ceased to be possible with Ubuntu versions 17.04, 17.10, 18.04, 18.10 but with the installation of 19.04 functionality was restored. However, with the 19.10 upgrade things aren’t working anymore. I checked the SAMBA config file and that seems the same as 19.04. I have switched on the new sharing settings in Settings.
I would appreciate any other suggestions!

---

### Post by Davethehedgehog on 2019-11-22
Eureka!!!
It's a firewall problem. Switch off the firewall and everything works.
This prompts the question, however, if I want to use a firewall and still want to access the home (windows) network and use streaming facilities, what rule should I set in ufw?

---

### Post by SeijiSensei on 2019-11-22
I write my own firewall rules and don't use ufw, so I can't answer your question exactly, but you need to permit access to ports 137-139 on the server.

---

### Post by uRock on 2019-11-22
If you install GUFW, then you can use it to allow certain services per port and what source IPs you want to allow.

You can also enter rules using commands, such as the following,
```
sudo ufw allow 22
```
That command allows all to access the port. Edit the port numbers to match the services you need. 

This link has examples if you're looking to only allow your local subnet to connect. [https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands](https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands)

---

### Post by Davethehedgehog on 2020-04-03
Thanks for the suggestions. GUFW makes it clear which ports are required.

---

### Post by Davethehedgehog on 2020-04-03
A related problem. I have a new computer withe two hard drives - a smallish SSD for system files and regularly accessed documents and a conventional larger hard drive for storage of (mainly) media files. Ubuntu 19.10 came with a sharing/streaming option which I can use successfully for files on the SSD, but not for files on the storage drive, even though I have added the relevant folders to the list to be shared. These folders are all showing as shared and the storage drive is mounted, but I can't see them on either of my smart TVs.
Anyone got any ideas?

---

