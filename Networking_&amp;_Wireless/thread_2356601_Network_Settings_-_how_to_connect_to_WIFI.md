---
title: "Network Settings - how to connect to WIFI ?"
date: 2017-03-24
forum: Networking &amp; Wireless
---

### Post by miquael on 2017-03-24
I'm new to Ubuntu and Linux.  I'm booting my custom PC with an Ubuntu USB to see if it will work with WIFI network.  I had installed Mint previously, but there was no network connection, so am trying Ubuntu.  If it works off USB, then I will install it.

But I do not understand the network settings panel.  What is SSDI,etc?  See image below.  

I have an OSX laptop that connects to my WIFI, but the network settings on OSX looks different.  How do I set up Ubuntu to connect with WIFI?

 [ATTACH=CONFIG]274297[/ATTACH]

---

### Post by miquael on 2017-03-25
anyone know ?

---

### Post by wildmanne39 on 2017-03-25
Click on the wireless script in my signature and follow the directions for running it and posting the link created to pastebin here, which is where the file will be posted.

---

### Post by miquael on 2017-03-26
okay, thanks @wildmanne39 - i'll try that (tomorrow, as it is late now) ...

meanwhile, here is an image.  i think the network hardware may not be working?  does it need to be switched on somehow?

[ATTACH=CONFIG]274309[/ATTACH]

---

### Post by wildmanne39 on 2017-03-26
That only shows it is not enabled, we need to see the info I asked for to find out why.
Thanks

---

### Post by miquael on 2017-04-03
Hi @wildmanne39 - sorry this took so long (had a busy week, and had to haul my system out to get a wire connection).  I followed all the instructions, and here is the pastebin: [http://paste.ubuntu.com/24310494/](http://paste.ubuntu.com/24310494/)

Any insights?

---

### Post by wildmanne39 on 2017-04-03
You installed the b43 driver so you need to remove it first then install the wl driver like this:
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe -r b43
sudo modprobe -v wl
```
unless you made the usb drive persistent once you reboot the changes will be lost.
Thanks

---

