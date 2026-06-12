---
title: "OpenVPN Acess Sever Client not working"
date: 2014-10-03
forum: Networking &amp; Wireless
---

### Post by meetdilip on 2014-10-03
I have setup OpenVPN Access Server on my VPS and got the server working. Followed these instructions then

> **_Ubuntu/Debian_:**
[B][FONT=courier new]
apt-get install openvpn[/FONT][/B]
 
Once the openvpn package is fetched from the Internet and installed, run the client with the [FONT=courier new]**--version**[/FONT] argument to make sure that it is version 2.1:
**[FONT=courier new]openvpn --version[/FONT]**
 [FONT=courier new]OpenVPN 2.1_rc15e x86_64-unknown-linux-gnu [...]
[...][/FONT]
 [B][FONT=courier new]
[/FONT][/B]

This is the output 

> $ openvpn --version
OpenVPN 2.3.2 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Feb  4 2014

So I have installed Openvpn client as mentioned [here ]("http://openvpn.net/index.php/access-server/docs/admin-guides/182-how-to-connect-to-access-server-with-linux-clients.html")

Could you please help me connect to my VPN as and when I need to use it please ?

---

### Post by bashiergui on 2014-10-05
Did you try this?
[http://openvpn.net/index.php/access-server/docs/admin-guides/397-how-to-connect-to-a-vpn-server-with-the-openvpn-client.html](http://openvpn.net/index.php/access-server/docs/admin-guides/397-how-to-connect-to-a-vpn-server-with-the-openvpn-client.html)

---

### Post by meetdilip on 2014-10-05
> **bashiergui said:**
> Did you try this?
[http://openvpn.net/index.php/access-server/docs/admin-guides/397-how-to-connect-to-a-vpn-server-with-the-openvpn-client.html](http://openvpn.net/index.php/access-server/docs/admin-guides/397-how-to-connect-to-a-vpn-server-with-the-openvpn-client.html)

That is my question actually. How to get the the destkop client on Ubuntu ?

---

### Post by bashiergui on 2014-10-05
> **meetdilip said:**
> That is my question actually. How to get the the destkop client on Ubuntu ?
Aha. Here you go. This link is from 2011 but should still be basically the same: [http://www.linux.com/learn/tutorials/459675:configure-linux-clients-to-connect-to-openvpn-server](http://www.linux.com/learn/tutorials/459675:configure-linux-clients-to-connect-to-openvpn-server)

---

### Post by weatherman2 on 2014-10-05
For a start, you can install the OpenVPN client from a terminal window:

```

sudo apt-get update
sudo apt-get install openvpn network-manager-openvpn

```

---

### Post by meetdilip on 2014-10-05
> **weatherman2 said:**
> For a start, you can install the OpenVPN client from a terminal window:

```

sudo apt-get update
sudo apt-get install openvpn network-manager-openvpn

```

Thanks a lot. I am able to install it. But how to run it. I use Gnome Flashback as desktop environment.

---

### Post by meetdilip on 2014-10-05
I tried to configure VPN through network settings and it won't save no matter I give 192.168.1.1 which is my router gateway or my VPS IP.

---

### Post by weatherman2 on 2014-10-05
What kind of OpenVPN connection are you trying to create in Network Manager?  If you create a "Password" type you still need a Certificate Authority (CA) Certificate - otherwise, you won't be allowed to save the configuration.  Have you created a CA on for your server?

If you won't use any certificates at all, it's pretty pointless to use OpenVPN - you might as well use something much less secure like PPTP.

---

### Post by meetdilip on 2014-10-05
Thanks both of you. I will check and revert.

---

