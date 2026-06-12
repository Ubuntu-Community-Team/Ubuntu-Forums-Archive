---
title: "vpn doesn't work"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by Cape on 2008-12-31
I'm trying to connect to my university's network via a vpn connection. I installed the network-manager-pptp package from the repositories as they use pptp. However, I cannot seem to connect. Each time I try through the network manager it either says the connection failed, or that it could not initialise the pptp process. The instructions my university provides covers Windows 2000/XP/Vista and OSX and are available here:

[http://www.york.ac.uk/services/cserv/net/vpn/]("http://www.york.ac.uk/services/cserv/net/vpn/")

I've also included an image of how I've configured the network manager GUI (with my username, and password length obscured). I know the password and username are correct as I can connect with my windows laptop.

Can anyone help?

---

### Post by pytheas22 on 2008-12-31
Do you have better luck if you connect using the command-line pptp client?  There are instructions [here]("http://www.cyberciti.biz/tips/howto-configure-ubuntu-fedora-linux-pptp-client.html").

Also, make sure that the pptp-linux package is installed:

```
sudo apt-get install pptp-linux
```

It should have been installed when you added the package to Network Manager, but I've had issues in the past with the NM GUI for openVPN being installed, but not the underlying openVPN framework, which caused the GUI to do nothing.

---

