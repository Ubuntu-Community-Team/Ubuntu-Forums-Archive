---
title: "Remote Desktop Access?"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by Unanimated on 2009-10-20
I can't figure out how to configure my remote desktop to accept connections anywhere from the Internet. It said that anyone could reach my computer after putting in the IP address and putting in the correct password, but then I closed and opened the menu again and that had changed back to being only reachable over the local network. How can I make the remote desktop settings accept connections from anywhere in the Internet, and then make it stay like that?

---

### Post by spiderbatdad on 2009-10-20
There is a guide here: [http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop](http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop) and there are many others. The priciples are the same. Make sure your firewall, ufw for instance, is allowing 5900, and make sure your router forwards 5900 to the machine's lan ip. It is best to set a static ip for your machine in /etc/network/interfaces, because your router might assign a different # each time you boot.

---

### Post by stinger30au on 2009-10-20
theres a few pieces of s/w you may be interedted in

first off is freeNX

[http://freenx.berlios.de/](http://freenx.berlios.de/)

there is also one at launchpad

i have done a quick google for it but cant find it

it allows remote access to a freinds pc over the net to assist them

---

### Post by Unanimated on 2009-10-25
> **spiderbatdad said:**
> There is a guide here: [http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop](http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop) and there are many others. The priciples are the same. Make sure your firewall, ufw for instance, is allowing 5900, and make sure your router forwards 5900 to the machine's lan ip. It is best to set a static ip for your machine in /etc/network/interfaces, because your router might assign a different # each time you boot.
I installed Firestarter and configured it to accept everything from port 5900 (I have a password enabled in Remote Desktop preferences), but it's still only reachable over the local network. How do I set a static IP in /etc/network/interfaces?

---

### Post by Unanimated on 2009-11-16
bump

---

