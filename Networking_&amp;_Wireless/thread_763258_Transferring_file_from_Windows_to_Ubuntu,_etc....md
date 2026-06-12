---
title: "Transferring file from Windows to Ubuntu, etc...?"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by maxpayne on 2008-04-22
I have a Macbook with the latest version of Ubuntu on it.  I had Leopard before but i decided to experiment with Ubuntu.  I lost my Leopard disk and downloaded it from the internet to a Windows Vista machine.  I need to transfer the .iso file from the windows machine to my Ubuntu Macbook over my wireless network.  My Macbook doesn't have DL dvd capabilities and neither does my pc.  Once transferred to Ubuntu I need to know how to mount the disk? or whatever it takes to boot it and install it.

I need the software on Leopard thus I need to install it.  I would HIGHLY appreciate a walk-through because I don't sh*t about Ubuntu.

Many thanks!

---

### Post by SpaceTeddy on 2008-04-23
bluntly put - it's impossible !
you will need to burn the DVD if you want to install leopard. 

As for the transferting - use ssh. install the openssh-server on the ubuntu with this command
```
sudo apt-get install openssh-server
```

then go and download the winscp software for windows [[COLOR="Blue"]here[/COLOR]]("http://winscp.net/eng/download.php").

use this to connect to your mac, browse into your home folder, and upload the iso.
AS for mounting it, i use gmount-iso from the repositories to mount iso images - but if you want to install, this will not help you... sorry

---

