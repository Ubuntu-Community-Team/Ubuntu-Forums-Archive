---
title: "Windows 10 Putty SSH Tunnel VNC To Ubuntu 14.04"
date: 2015-08-17
forum: Networking &amp; Wireless
---

### Post by Forbees on 2015-08-17
so i reinstalled windows 10 on my main computer and i cant get my SSH tunnel to VNC into my ubuntu media server (it's running desktop)

i can SSH into it no problem but i can't get putty configured right and i've tried a number of tutorials but have failed. everything worked fine before the windows reinstall but i have the putty settings saved so i'm probably forgetting to click a box or maybe my port is off by one digit.


on the "server" side in ubuntu i'm just using the ubuntu desktop sharing instead of having VNC installed. i forget the real name of the program... remna? either way i was physically at the ubuntu machine today and couldn't figure out how to confirm which port it was listening on, but from what i read in forums it should be 5900 or 5901.


so in putty i type the url for my ubuntu machine (it's in a different city, have a noip.me for it), then goto SSH Tunnel and put port 5900 and destination 192.168.1.4:5900 (the internal ip of the ubuntu machine)

SSH gets me in fine but vnc won't connect when i tell it to connect localhost. what did i miss?

---

### Post by weatherman2 on 2015-08-18
VNC by default listens on port 5900.  VNC is not encrypted, which is why people like to use ssh, because it is encrypted.

An ssh server listens on port 22 by defualt.

What you need to do is ssh in first to your server, then start a VNC server and route that through your ssh tunnel.  Then VNC in through the ssh tunnel.  There are tutorials on how to do it - google them.  You can't use Ubuntu's desktop sharing for this, though - you have to install and use a vnc server of some sort, I believe.  I've looked at doing this but never done it.  I use a VPN instead to connect to my home network; then I don't need ssh to connect securely, I just connect using vinagre into my server via VNC, as if I were on my local network.

---

### Post by Forbees on 2015-08-18
i'm already ssh'd in, and i did it with ubuntu's desktop sharing last week before i lost my putty config with no problems

---

### Post by steeldriver on 2015-08-18
Sure you can use the default desktop sharing application (vino-server) - although it is not enabled by default: you will need to open the Desktop Sharing dialog from the dash, or type

```

vino-preferences

```

in a terminal, and then check the boxes for "Allow others to view your desktop" and (if desired) "Allow others to control your desktop"

[ATTACH=CONFIG]263915[/ATTACH]

To connect from a Windows VNC client, you may also need to disable encryption: this is a fairly recent change (post 12.04 IIRC) and AFAIK cannot be done through the preferences GUI, only through gsettings or dconf e.g.

```

gsettings set org.gnome.Vino require-encryption 'false'

```

You can check the current status using

```

gsettings get org.gnome.Vino require-encryption

```

or (to see all the settings)

```

gsettings list-recursively org.gnome.Vino

```

You can check that Vino is using the default port 5900 using

```

sudo netstat -nlp | grep vino

```

On the client (PuTTY) side, I always specify the "Destination" using "localhost" rather than an explicit IP address 

```

L5900      localhost:5900

```

---

### Post by Forbees on 2015-08-18
> **steeldriver said:**
> 

On the client (PuTTY) side, I always specify the "Destination" using "localhost" rather than an explicit IP address 

```

L5900      localhost:5900

```

that did it. thank you so much

---

