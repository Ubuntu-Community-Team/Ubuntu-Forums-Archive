---
title: "VPN in 8.10 is a Show Stopper - buggy, does not work"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by cwmoser on 2008-12-08
I was attempting to migrate from Ubuntu 8.04 to 8.10 but ran into a real Show Stopper -- VPN just does not work.  It worked very well in 8.04 using the Network Applet.  

I read posts that there are problems in gnome VPN and to try KVPN (KVpnc).  After trying to figure out KVpnc, I was finally able to establish the VPN to a Microsoft Server using the Terminal Server Client but the keyboard input fails at that point and I have to kill the VPN and Terminal process to get out of this hung up state.

Anyone have a fix for this?

Thanks

Carl

---

### Post by cwmoser on 2008-12-08
I found a new network-manager-pptp at:

[https://edge.launchpad.net/ubuntu/intrepid/+source/network-manager-pptp/0.7~~svn20081015t024626-0ubuntu1.8.10.1](https://edge.launchpad.net/ubuntu/intrepid/+source/network-manager-pptp/0.7~~svn20081015t024626-0ubuntu1.8.10.1)

How do you make this and install it?

I'm a little unclear on the process of installing packages like this.

Thanks

Carl

---

### Post by dukejib on 2008-12-24
@Carl

type this at Terminal

"sudo apt-get install network-manager-gnome network-manager-pptp"

then

"sudo NetworkManager restart"

This will install the proper application for your VPN.

You will see an icon on top right blink (Network Icon)

after this you can click on the Network Icon and configure your VPN.

Hope this helps.

---

### Post by cwmoser on 2008-12-25
Tried what you suggested but the nm-manager applet has no support for VPN.
It only shows a configuration for the IP address, DNS, etc.

Carl

---

### Post by waspbr on 2008-12-25
I use the cisco vpn client, it's not very difficult to install

---

