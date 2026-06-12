---
title: "Gencontrol (remote assist) for Ubuntu?"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by syk69 on 2008-09-25
Hi, at work we use gencontrol to remote assist users with their computer problems. Nothing is needed to be installed on users computer. It's only an .exe file and you can administer the machine remotely. Is there any vnc like software for ubuntu that you don't have to install software on the remote end? Thanks!

---

### Post by superprash2003 on 2008-09-25
well, ubuntu comes with remotedesktop by default.. system->preferences->remote desktop .. all you need to do is enable it.. and open the required port.

---

### Post by syk69 on 2008-09-25
> **superprash2003 said:**
> well, ubuntu comes with remotedesktop by default.. system->preferences->remote desktop .. all you need to do is enable it.. and open the required port.

that lets others remote to my desktop. not looking for that. i want to remote desktop vnc like to others desktop to administer their computers without having them logoff their windowsxp machine. thanks though!

---

### Post by superprash2003 on 2008-09-26
you want to remote control a windows machine from ubuntu where the windows machine has a vnc client.. right?? is this on a LAN?

---

### Post by syk69 on 2008-10-01
> **superprash2003 said:**
> you want to remote control a windows machine from ubuntu where the windows machine has a vnc client.. right?? is this on a LAN?

yes, we usually use a program called gencontrol which is great because you take over the users computer even if they are logged in so we can help them. with this program we don't have to install a vnc client in the remote machine. somehow the program adds a temp directory and does it hidden without the user knowing. 

yes its on a LAN. just looking for some app similar to it using ubuntu 8.04.1.

gencontrol is open source so if anyone can even make it for ubuntu would be greatly appreciated. it can be found here [http://www.gensortium.com/products/gencontrol.html](http://www.gensortium.com/products/gencontrol.html)

---

### Post by Zulu-Zeffir on 2009-07-01
I know this post is quite dated, but I'm also interested in an essentially push deploy vnc solution like Gencontrol for Ubuntu.  Currently I can run gencontrol within wine but it does not seem to be able to see hosts on the lan.  Perhaps something pertaining to DNS, although even if it could see the rest of the lan I'm not sure if it would even function to connect.  My ubuntu box from which I'm attempting this is jointed to an AD domain and authenticating well with single sign on (e.g. I can browse network shares etc with my ad user credentials).

---

