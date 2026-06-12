---
title: "Script to find my public ip address?"
date: 2017-09-11
forum: Networking &amp; Wireless
---

### Post by 1clue on 2017-09-11
Hi,

I'm trying to work around my router's inability to do ddns with my dns provider. I have a script which can login to the dns provider and set the ip address, but I don't have a way to find out my public ip address from the linux box.

The dns provider is zoneedit, and I'm using the zoneclient.py script found here: [http://zoneclient.sourceforge.net/](http://zoneclient.sourceforge.net/) and the router is a tplink ad7200.

When I run the command without the part about logging into my local router, my public DNS entry gets changed to my linux box's 192.168 address, which I definitely don't want.

So the script also has a way to set the ip manually, so if I can get the external ip address by some other script I can make this work.

Thanks.

---

### Post by ajgreeny on 2017-09-11
Try command ```
curl ifconfig.me
``` in your script; that shows your public IP but I will let you sort out how to use it.

---

