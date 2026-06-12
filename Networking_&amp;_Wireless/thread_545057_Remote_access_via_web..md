---
title: "Remote access via web."
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by dgrafix on 2007-09-07
Im looking for something like gotomypc that is secure and can be used from anywhere.

I like the look of gotomypc but it has subscription fees! (i dont mind paying once tho, but i dont want to subscribe for it) 

Anyone know of any other services that can run on a linux host that can allow me to view my desktop securely through a web browser? The problem with VNC is you need to install both SSH and VNC on the client machine, which kind of defeats the object.

---

### Post by ebozzz on 2007-09-28
Any luck with your search? I am looking for solution that would allow me to perform functions on my mother's computer. She always has questions that I find difficult to explain over the phone as she is hearing impaired. :(

---

### Post by dgrafix on 2007-09-28
I have found a very good comprimise using ssh/vnc/dynamicDNS after all:

I can now use a keyring USB drive armed with "putty" ssh and VNCviewer (windoze versions, so i can use anywhere), neither of which need 'installing' on windows and can run straight off the flashdisk.

Heres how i did it:

1- lock your router down for non-essential incomming traffic (the usual default) and then set it to use  "port forwarding" on Port 22 to the ip address of your linux box. Then install SSH server for linux, with a nice big password 'sentence' to protect it (L o n g ! with caps and numbers! - as this is your castle door!). 

2- get dynamic DNS, use [www.dyndns.org](www.dyndns.org) (free service) to constantly be updated by your router - as in your router (assuming it has a DDNS option)  sends its current isp IP number to the dyndns server (instructions on site) but **be sure to use a unique password for the dyndns.org website, DO NOT MAKE IT THE SAME AS  ANYTHING ELSE, ESPECIALLY YOUR SSH LOGIN!** the reason being is when your router sends out the IP details it sends login info for the dyndns server and it is not encrypted!

3- where ever you have internet access simply stick the keychain in, log into (for example) yourname.dyndns.org (which resolves you current IP) using the 'tunneling' settings in putty to forward the desired port. for example with VNC you would us the settings in tunneling:
5901
localhost:5900
Or any other ports you need to be securely tunneled.

4- load vnc viewer and log on to localhost:1 

its simple and sweet and gets the job done. Only problem is, the host pc needs to be loged in, and anyone at home can see what you are doing on the screen, but hey it works :)

---

### Post by dgrafix on 2007-09-28
. duplicate post :(

---

### Post by dgrafix on 2007-09-28
. Duplicate post :?

---

### Post by ebozzz on 2007-09-28
Nice! Thanks for the reply. I actually want Mom to see what I am doing. It may save me from having to answer questions as frequently. Or, not...... :)

---

