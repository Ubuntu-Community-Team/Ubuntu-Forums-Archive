---
title: "Certificate based OpenVPN client"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by Springs on 2008-09-22
I have looked around and I am sure someone will give me a link that has what I am looking for...

Anyways.

I have an Untangle server that I need to connect to via OpenVPN. I have the config file and the certificates on a Windows Laptop and works great. I can connect and transfer files without loosing my connection to local resources of hanging up skype.

In Ubuntu at home I have tried setting up network manager by importing the OVPN file and the certs. Can't seem to get it to work.

Anyone have a real good tutorial or how to they could point me too?

Thanks for any help.

---

### Post by thefunnyman on 2008-09-23
> **Springs said:**
> I have looked around and I am sure someone will give me a link that has what I am looking for...

Anyways.

I have an Untangle server that I need to connect to via OpenVPN. I have the config file and the certificates on a Windows Laptop and works great. I can connect and transfer files without loosing my connection to local resources of hanging up skype.

In Ubuntu at home I have tried setting up network manager by importing the OVPN file and the certs. Can't seem to get it to work.

Anyone have a real good tutorial or how to they could point me too?

Thanks for any help.

I tried to use the network manager openvpn gui just recently and could connect to my vpn server, but lost all internet access after connecting.  I found that just installing openvpn 

```

sudo apt-get install openvpn openssl

```

and putting the config and key files in the /etc/openvpn directory worked just fine, now it just connects everytime on startup without me having to do anything.  Just make sure that you specify in the config file the full absolute path to the location of your key files to avoid any confusion.  That is the route I would recommend taking.

Hope this helps.

thefunnyman

---

