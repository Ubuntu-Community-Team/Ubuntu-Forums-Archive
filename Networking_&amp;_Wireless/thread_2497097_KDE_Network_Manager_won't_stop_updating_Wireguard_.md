---
title: "KDE Network Manager won't stop updating Wireguard configuration"
date: 2024-04-23
forum: Networking &amp; Wireless
---

### Post by jferments on 2024-04-23
I have Wireguard set up on Kubuntu 23.10. 

I have a manually created config file that I want to use that I put in /etc/wireguard/wg0.conf

I then want to bring up the wireguard interface wg0 with "sudo systemctl start wg-quick@wg0" 

Previously this was working, and then I made the mistake of trying to edit the network interface settings in KDE Network Manager (adding the private key to the wg0 interface). This made me unable to connect, and it would not let me remove the private key, so I tried removing the wg0 interface from network manager altogether. 

Now, even though the wg0 interface isn't there, KDE network manager is overwriting my /etc/wireguard/wg0.conf every time I try to start or restart wireguard service. I know that it is KDE because it exactly the settings that were listed in the network manager dialog (it is adding a listen port, changing IP addresses, setting "fwmark" and other things that I don't want it to change). If I delete the copy of wg0.conf that KDE network manager is creating, and rewrite the file manually, it just gets overwritten again. 

How can I make it where KDE network manager will never touch /etc/wireguard/wg0.conf again? Is there a configuration file that I can edit somewhere to remove this from the list of network interfaces it tampers with?

---

