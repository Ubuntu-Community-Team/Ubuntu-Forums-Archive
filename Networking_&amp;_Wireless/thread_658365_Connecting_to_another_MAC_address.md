---
title: "Connecting to another MAC address"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by jackhill on 2008-01-04
I am a total newcomer to anything like this so i hope i have come to the right place for help!

I want to connect to another PC via the web. We have the IP and MAC addresses but have no idea what to do with them. How can i use this info to connect to the remote PC? 

From a security point of view, if someone else had my IP and Mac address, what information could they get from it/my machine?

---

### Post by zyghom on 2008-01-04
> **jackhill said:**
> I want to connect to another PC via the web. W/my machine?

excuse me ? try again with the question please as no idea what you want from web towards connection of 2 pc

---

### Post by jackhill on 2008-01-04
i have a pc at my home and my girlfriend has one at hers. we want to be able to log on to each others. i am told we could do this over the 'net if we have the IP and MAC addresses but i cannot find any decent instructions on how to do it. we both have wireless routers. does this make more sense?

---

### Post by zyghom on 2008-01-04
yeap, now I got it
but it has nothing to do with web
fist: are your IP fixed ?
second: start googling for VPN - that should be good direction

---

### Post by Predator[23rd] on 2008-01-04
> **jackhill said:**
> i have a pc at my home and my girlfriend has one at hers. we want to be able to log on to each others. i am told we could do this over the 'net if we have the IP and MAC addresses but i cannot find any decent instructions on how to do it. we both have wireless routers. does this make more sense?

First, you don't need the MAC address.

Second, what do you mean by "log on"? There are a few possible ways to connect, depending on what your ultimate goal is ...

---

### Post by jackhill on 2008-01-04
"log on" as in connect to the other machine access its files etc. i am also worried that with a wireless router, neighbours can access my data.

---

### Post by zyghom on 2008-01-05
> **jackhill said:**
> i am also worried that with a wireless router, neighbours can access my data.

wireless should be protected by WPA2 in best case
and then nobody will access your pc

---

### Post by Predator[23rd] on 2008-01-05
> **zyghom said:**
> wireless should be protected by WPA2 in best case
and then nobody will access your pc

actually I would say:

WPA2 in the worst case AND then it will be difficult (but still possible) to access your wireless network.

to "secure" a wireless network you should regularly change encryption and authentication passwords. SSID should always be hidden. MAC based ACL is also a must have. all this will make it very difficult and practically impracticable (but still not impossible) to access a wireless LAN.

back to "logon":

for a simple and easy way to access files on a remote computer install a SSH server and logon via SSH (e.g. SFTP for file transfers, FILEZILLA is a nice client for this).

if you want to transfer to desktop form the remote computer to your local computer (picture-in-picture so to speek) you possible want to use a VNC (virtual network computing) server. But with VNC you have to make sure to have a secure connection since VNC clients themself usually do not encrypt their communication. A possible solution here is tunneling.

---

