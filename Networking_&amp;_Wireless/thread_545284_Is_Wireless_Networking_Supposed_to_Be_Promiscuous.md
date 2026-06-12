---
title: "Is Wireless Networking Supposed to Be Promiscuous?"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by porcorosso on 2007-09-07
I searched for information on this but didn't find anything useful.

The Intel Pro 2200 BG wireless device in this Dell notebook worked right off the bat. It works just a little too well. I imagine I have to tell it to stop hooking up with every sailor on the block, but I don't know how to go about that.

I have used it with network-manager, network-manager with pam-keyring, and wicd. It behaves the same in every case. I can set it up to connect automatically to my WPA2-encrypted wireless router. But on occasion, it goes ahead and grabs a DHCP address from my neighbor's unencrypted Netgear router. I've checked, and it is not set to connect automatically to any other wireless network -- not deliberately anyway.

Someone want to whack me with a clue-by-four? I can find nothing in wicd's interface that seems like it will keep this adapter from connecting on occasion to that pesky unencrypted network.

An additional question I have concerns a feature which the gnome-network-manager provided in a dropdown when you clicked on the network tray icon -- the Enable Wireless selection. When I'm in some locations I'd prefer just to disable wireless. I don't see an obvious  solution for this in wicd. Can anyone help me on this?

Thanks!

---

### Post by spd106 on 2007-09-07
Network Manager will not connect to any new networks unless told to, it's default action is to attempt to connect to those networks it has been previously connected. The list of networks is stored in gconf. So you'll probably have to edit it to remove your neighbour's network.

See [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) for more details.

Sorry I've no idea about Wicd, never used it. There are many other people around this forum that have. So I'm sure someone can help.

---

### Post by porcorosso on 2007-09-07
Thanks for that info. I'll check into this.

When I first installed Ubuntu the only network available (because I hadn't put the WPA2 key in yet and didn't have Ethernet cable attached) was that danged unsecured Netgear router. I guess Ubuntu grabbed the only network connection it could find, because it certainly didn't ask me. So that network, I guess, got added as an "approved" network in the configuration file.

Now that I know where it is, I should be able to correct it. Will try this in a little while. Booted up in Vista right now.

Thank you.

---

### Post by porcorosso on 2007-09-07
I don't know. I go into gconf-editor and see nothing about the unsecured network.

On the other hand, I had -- since the last time this unwanted connection was made -- used Synaptic to "remove completely" Wicd (which I was using for management of connections). I reinstalled it. I supposed that using the "remove completely" option may have removed the configuration information for the unwanted connection. On the other hand, it didn't remove the WPA key for the connection I do want.

Frankly, I'm confused.

I'll watch and work on this if it reappears.

Thank you again for the info.

----EDIT----

Well, the connection to the unwanted unsecured network occurred again. As I said, I had checked in gconf and found absolutely nothing about that network -- which makes sense, really, since without encryption on it there's nothing (other than SSID) to differentiate one network from another. I went back to network-manager and got the same thing happening.

Looks to me like Ubuntu hooks up to the most available wireless network in the neighborhood.

But I did beat it. I reinstalled Wicd (for convenience), and I used Firestarter to set an iptables policy to NOT allow outbound to the IP addy of that blasted router. That took care of the problem.

I've got to hope there's something better built in to the system, though. Even Windows can be told to connect only to known, secured networks.

---

