---
title: "Wireless Router Construction?"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by NonPermissive on 2008-05-18
I have an old Dell Optiplex beside me here, and I want to set it up as a router, connecting to the internet via a WEP-encrypted wireless connection, and serving three other devices via ethernet. How would I go about doing that? It's been very hard for me to find a tutorial, and if anyone could link me to a good, simple one, I'd be grateful. I don't want to have to configure it every time it boots, I want it to be able to connect to my network automatically on startup.

As an aside, I also wouldn't mind using the hard drive in it as NAS, even putting new disks in it for additional storage.

---

### Post by SpaceTeddy on 2008-05-18
i've written down this step-by-step [[COLOR="Blue"]tutorial[/COLOR]]("http://ubuntuforums.org/showthread.php?t=713874") some time back which explains how to setup an ubuntu box as a router/firewall. That should do the trick for you :)

if any question are left after that, just ask :)

as for the NAS - that would require a Samba server. Should not be too hard, but i don't have a tutorial at hand for that - sorry :(

---

### Post by NonPermissive on 2008-05-18
> now, to configure eth0, you will need add a few lines to the file. Also, this configuration ONLY works on ethernet cards, NOT on wireless.
It says it won't work with a wireless connection, but it's going to use wireless to hook up to the network.

Also, I thought Samba was just for Windows compatibility?

---

### Post by SpaceTeddy on 2008-05-18
what exactly is saying that it will not work with a wireless connection ? i am a bit confused about that. Can you please explain that ?

regarding samba - samba is a tool to create windows shares on ubuntu. Since both, ubuntu and windows can access those shares, it would make sense to use samba for it as it means that anyone can write to the drives in the computer - exactly what a NAS does :)

---

### Post by Der_Idiot on 2008-05-18
I'm doing simmilar; setting up ubuntu as a wired and wireless router to the internet.

Server will be DNS/DHCP/Wins/Samba data server (1.5tb storage)/apache/etc.

Good to see a guide up, I'm still moving data off ntfs partitions and formatting them to ext3. 300 gigs takes a long time :mad:

---

### Post by NonPermissive on 2008-05-18
Looking over that guide again, it seems that it is specific to a router connecting to the Internet via Ethernet. I imagine there wouldn't be much change with a Wifi connection, but I'm wondering what I would have to add to /etc/rc.local to make it connect to the WiFi automatically.
I guess my real question is, what exactly is the syntax for iwconfig, when using WEP?

---

### Post by SpaceTeddy on 2008-05-19
you can either do the connection via the /etc/network/interfaces files, where all your parameters for the network cards are specified. but im am not too sure about that either. 

Just had a look at the sticky posts in the forum, and guess what the first one is :) [[COLOR="Blue"]How To: Manual Network Configuration without the need for Network Manager[/COLOR]]("http://ubuntuforums.org/showthread.php?t=684495")
that should explain how you can manually connect to a wifi network :) Also, i've checked, WEP is convered :)

Also, as a quick answer, the command would be
```
sudo iwconfig %device essid %network key s:%key
```
where 
 - %device is your network card (as specified by iwconfig)
 - %network is the name of your wireless network
 - %key is your WEP key IN ASCII

hope it helps :)

---

### Post by NonPermissive on 2008-05-19
Yeah, thanks man. One more thing, I plan to make this a headless machine, would you recommend installing Xubuntu on it and then taking off every display related thing, or just using Ubuntu Server? I'm comfortable with the command line, I'm just thinking about the time it would take me.

---

### Post by SpaceTeddy on 2008-05-19
i prefer installing as little as possible and then only adding whatever i need. Uninstalling usually leaves leftovers that i am never sure if i can remove them or not. Also, they generate more updates notifications. So i would go for the ubuntu-server without any overhead at all.

So, i'd install it, make sure the ssh-server is on, and then just stuff it in a corner and let it run. If ever anything fails, you always have ssh to fix it :)

That's how i do it, anyways :)

---

### Post by NonPermissive on 2008-05-19
Good to know, I already have a Hardy Server image, didn't want to have to download another Xubuntu image. Thanks again man.

---

