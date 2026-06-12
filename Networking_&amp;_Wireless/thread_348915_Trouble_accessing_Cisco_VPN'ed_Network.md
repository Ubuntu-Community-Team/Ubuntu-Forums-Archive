---
title: "Trouble accessing Cisco VPN'ed Network"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by iver2435 on 2007-01-29
Hello,

      I am a college student and I have Ubuntu 6.10 loaded up on my Dell laptop.  Everything works great EXCEPT the wireless connection at my school.  The wireless network is accessed via the Cisco VPN Client, which I have downloaded and installed with no problems or issues.

     The problem comes in when I actually try to USE the client.  I type:

```
sudo vpnclient connect <profilename>
```

     And from there is displays the copyright information, blah blah blah, and it gets to the part where it says "Connecting to <IP Address of VPN Gateway>" and then it errors out.  It says something like (I'm paraphrasing): "Could not send packet, network unreachable."

Now, everything I've ever known about VPNs tells me that I need to already have a connection via a "insecure" connection and then the VPN is "tunneled" through the insure connection.  The problem with my school is that they don't broadcast any ESSIDs and they won't tell anyone what they are, so I can't connect to an "insecure" network to send the packet.  I'll be honest....I have ABSOLUTELY no idea how Cisco's VPN client works to establish a connection, maybe they have some other special way I don't know about...

Anything and everything Linux is "unsupported" here on campus, but they assure me that the Cisco VPN Concentrators they have are compatible and that several people around campus are known to use the Linux Cisco VPN client to connect.

I will update this post later with the text of the profile I am using to connect, but in the meantime, I'm hoping that the brilliant people that troll these forums will stop and give me a leg up.  Thanks and look forward to your replies...

---

### Post by joris1977 on 2007-01-29
Don´t think i can help you but this howto might be helpfull: 

[http://www.ubuntuforums.org/showthread.php?t=298181&highlight=cisco+vpn](http://www.ubuntuforums.org/showthread.php?t=298181&highlight=cisco+vpn)

---

### Post by netztier on 2007-01-29
> **iver2435 said:**
> The wireless network is accessed via the Cisco VPN Client, which I have downloaded and installed with no problems or issues.

It's the wireless network acting as "carrier" to the (Cisco) VPN Concentrators. So you access your campus network (where your servers, proxies, printers etc are) through a VPN tunnel across/over the wireless network. 

This is a commonly used setup to get a good level of security on a large scale wireless network, where modern and legacy hardware must coexist. Legacy WLAN chipsets are often not able to use modern day encryption standards required by WPA2 and the like, so encryption and access control have to move to an upper layers: VPN or SSL.

> **iver2435 said:**
>  It says something like (I'm paraphrasing): "Could not send packet, network unreachable." 

That says it all. Your VPN profile for the VPN client specifies an IP address and/or hostname of the VPN concentrator - and now the client says it can't reach it.

> **iver2435 said:**
>  Now, everything I've ever known about VPNs tells me that I need to already have a connection via a "insecure" connection and then the VPN is "tunneled" through the insure connection. 

This is basically correct, but actually the VPN client *builds* the tunnel, which is transported by the unsecured network. Once the tunnel is up, it's the connections you are actually using that are sent through the *through* the encrypted tunnel.

> **iver2435 said:**
>  The problem with my school is that they don't broadcast any ESSIDs and they won't tell anyone what they are, so I can't connect to an "insecure" network to send the packet. 

Not broadcasting the ESSID does not offer any security advantage. Launch kismet, netstumbler, wellenreiter or any wireless sniffing tool of your choice near some active WLAN client and you'll know the ESSID instantly. There's no benefit from not broadcasting it. In a setup as you describe it, security should be achieved by reducing the reachable services to "VPN protocols only" and these "only to/from the VPN concentrator". Any other traffic entering or leaving the unsecured network should be denied.

If they're not telling anyone the ESSID - and they're not broadcastig it, how the heck do the other client systems know what the actual ESSID is? Do they have to enter it manually, or do they all sniff the air to find it out? I have made the experience that Windows XP is not really good handling multiple ESSIDs in the air if one of them is non-broadcasting while others are, therefore I generally advise not to hide ESSIDs

> **iver2435 said:**
>  I'll be honest....I have ABSOLUTELY no idea how Cisco's VPN client works to establish a connection, maybe they have some other special way I don't know about...

Not (yet) being an expert in that area, I can still tell that there's no black magic to it. The profile contains the address/names of the VPN concentrators and the authentication settings and pointers to certificate files etc. That's it. It supports the common features used for NAT-traversal and the like. Nothing really special.

> **iver2435 said:**
> 
I will update this post later with the text of the profile I am using to connect, but in the meantime, I'm hoping that the brilliant people that troll these forums will stop and give me a leg up.  Thanks and look forward to your replies...

You'll have to work through the lower ISO/OSI layers:
[LIST]
[*] verify that your WLAN card is working correctly; pick some other wireless network and connect to it, to see that it works (which you already did, as indicated in your post).
[*] get access to that campus wireless network. Make sure you get to know the ESSID and if applicable also the encryption method and keys or username/passwords.
[*] check if your NIC has a correct IP address for this network. Ask if IP addresses are assigned dynamically with DHCP or statically. You might have to give them the MAC address of your NIC for that.
[/LIST]

Hope there's some breadcrumbs of useful information in this post.

best regards

Marc

---

