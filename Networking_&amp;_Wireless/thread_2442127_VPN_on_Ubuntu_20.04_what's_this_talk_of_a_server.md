---
title: "VPN on Ubuntu 20.04: what's this talk of a server?"
date: 2020-04-30
forum: Networking &amp; Wireless
---

### Post by stuseem on 2020-04-30
Hi all,

Ive recently moved from Windows 10 to Ubunutu and I am bloody loving it!

On Win10 I used a VPN (Hotspot Shield) and it was just downloaded, installed and used easily via a GUI.

I want to install and use similar on Ubunutu, and ive read that WireGuard VPN is already in Ubunutu 20.04?

Anyway I been looking at the instructions to use it:

[https://linuxconfig.org/how-to-create-a-vpn-on-ubuntu-20-04-using-wireguard](https://linuxconfig.org/how-to-create-a-vpn-on-ubuntu-20-04-using-wireguard)

[https://www.cyberciti.biz/faq/ubuntu-20-04-set-up-wireguard-vpn-server/](https://www.cyberciti.biz/faq/ubuntu-20-04-set-up-wireguard-vpn-server/)

What is all this reference to a server? Why do I need to set up a server?

How comes its so uch more difficult to setting on up in Windows 10?

Thanks!

---

### Post by TheFu on 2020-04-30
a) Linux people tend to be more technical and WANT complete control over everything on the system.
b) VPNs have a client and a server.  Since Linux people want to control stuff, we often run our own servers. This is not mandatory, but with any VPN solution, there is a client, usually you, and a server, usually a paid service.
c) You cannot just pick to use any VPN software that you like and expect your VPN provider (hotspot shield?) to support it.  Different VPN software only works with the servers that match.  If Hotspot Shield supports wireguard, great!  But they probably support OpenVPN.

There are 2 major purposes for a VPN-server at home and a VPN-server on the internet, somewhere. 

I have a paid VPN provider. They support openVPN and have an installer for Linux or I can setup an openvpn client following their how-to guide. They have exit nodes in about 30 countries, which means I can appear to be in those other countries by the exit node selected. They do not support wireguard, because wireguard is not production ready at this point.  
Learn more about wireguard: [https://arstechnica.com/gadgets/2018/08/wireguard-vpn-review-fast-connections-amaze-but-windows-support-needs-to-happen/](https://arstechnica.com/gadgets/2018/08/wireguard-vpn-review-fast-connections-amaze-but-windows-support-needs-to-happen/)

I also run a VPN server at home so that secure access to my LAN is possible when I'm away - anywhere - in the world.  I use openvpn for this. I looked at wireguard, but decided I would wait until it matured a little more and clear instructions were available to handle some more complex routing needs and hundreds of users.  The instructions I've seen for wireguard are for single-user setups.

I don't know anything about Win10, except I didn't like or agree to the EULA and never intend to let that OS on my networks.

---

### Post by The Cog on 2020-04-30
> Why do I need to set up a server?
You don't need to set up a server if you don't want to. You can use a public server (as you have been doing). There are plenty of public servers around. Many support wireguard these days.

> What is all this reference to a server? 
By server, they are referring to an arrangement where a permanently-on machine provides a service to many users who connect to it when they want the service and disconnect when they have finished. 
I gather you have been using a server provided by Hotspot Shield: [https://en.wikipedia.org/wiki/Hotspot_Shield](https://en.wikipedia.org/wiki/Hotspot_Shield)

> Why do I need to set up a server?
You don't need to set up a server if you don't want to. You can use a public server (as you have been doing). There are plenty of public servers around. Many support wireguard these days.

I disagree with TheFu that "VPNs have a client and a server". Some VPNs are always set up so that one end , the "client" has to call the "server" not the other way round, but not all. Wireguard can be configured in a symmetrical way for connections such as connecting company offices together over the internet while keeping their data private - the real meaning of "Virtual Private Network". Some of my computers run a VPN between each other over my WiFi network at home. I know someone who uses wireguard between his permanent home and his holiday home - uses it to check thermostats, security cameras etc.

I actually do have my own server, a machine rented somewhere in cloudy-land. I use it because my poxy ISP couldn't organise a booze-up in a brewery let alone an IPv6 network. So my IPv6 connection to the world is via my own little VPN. And since I've been to that trouble, I send my IPv4 traffic that way too (including DNS queries) just to annoy them. 

> How comes its so uch more difficult to setting on up in Windows 10?
Because you are reading how to set up the VPN from scratch. If you subscribe to a public VPN provider, they provide an easy tool - for instance [https://mullvad.net/en/help/install-mullvad-app-linux/](https://mullvad.net/en/help/install-mullvad-app-linux/) (I don't use them, it's just an example of "download it, run the installer, use it."). They have done all the config work for you, just like Hotspot Shield did for you.

---

### Post by stuseem on 2020-05-01
Thanks for the replies guys. Really appreciate the tie and detail!

Hope you don't mind the extra questions: 

> [COLOR=#000000]You don't need to set up a server if you don't want to. You can use a public server (as you have been doing). There are plenty of public servers around. Many support wireguard these days.[/COLOR][COLOR=#000000]

[/COLOR]In this sentance what is meant by "many support wireguard" ? Can I only use VPNs that support wireguard as that is already in Ubuntu 20.04? If I installed this would it autoatically connect to wireguard: [https://windscribe.com/guides/linux](https://windscribe.com/guides/linux)? 

If I followed instructions on this page would it not provide e with a VPN to use? [https://www.wireguard.com/install/](https://www.wireguard.com/install/)



Thanks.

---

### Post by TheFu on 2020-05-01
The client and the server must use the same sort of software - openvpn or wireguard or one of the 20 other less-used VPN tools.

Your client uses 1 or both of those, depending on the different services involved, just not at the same time .... well, unless you are an expert and like a routing challenge by having 2 VPNs active concurrently.

If you are paying for a VPN service, their documentation is the best hope you have for which underlying VPN software is being used.  The point-n-click VPN setup method that is pretty easy in Ubuntu to use would be to get an ovpn file from your VPN service and use that. Probably in the network-manager screens.  IDK. I setup my VPN connections from a shell command since most of my systems don't have any GUI or any network-manager files.

---

### Post by The Cog on 2020-05-01
> 
In this sentance what is meant by "many support wireguard" ? Can I only use VPNs that support wireguard as that is already in Ubuntu 20.04? If I installed this would it autoatically connect to wireguard: [https://windscribe.com/guides/linux?](https://windscribe.com/guides/linux?) 
I've never heard of windscribe, and their web site doesn't clearly say what it is, though I suspect they are another public VPN server, like the others we have already mentioned.
You don't have to use wireguard as your VPN protocol. The two common ones are OpenVPN (the most popular, been around for years, well established, hard to configure) and wireguard (the newcomer, support recently built into the Linux kernel, delightfully easy to configure). Almost every public VPN server supports OpenVPN, and many are starting to support wireguard - you choose which you want to use and download their installer that sets it all up for you. Having chosen your VPN service provider, if they offer the choice then I would recommend wireguard but they both work.

---

### Post by stuseem on 2020-05-01
lovely. thanks for your help guys!

ill give it a go. might have to ask a few questions down the line, but hopefully not!

---

### Post by stuseem on 2020-05-08
Hi all,

So I just installed Windscribe and use it with by following the instructions on this page: [https://windscribe.com/guides/linux?](https://windscribe.com/guides/linux?)

I didnt have to do anything with WireGuard thats already in Ubuntu, and I dont have to do anything with it when I use Windscribe. But you said it has to supportWireGuard?

Have I done it all right?

---

### Post by slickymaster on 2020-05-08
*Thread moved to **Networking & Wireless**.*

---

### Post by TheFu on 2020-05-08
> Note: Windscribe for Linux is still in beta. If you encounter bugs please send us a debug log and open a support ticket. 
is from their site and is VERY telling.  For getting cat videos, fine. For company secrets staying safe?  Not so much.

On the "features" page, is has this:
> Generate OpenVPN, IKEv2 and SOCKS configs for all your devices
Which is pretty clear that they use OpenVPN, as we mentioned multiple times.  Many openvpn services claim 256 AES, but don't actually enable that by default for assorted reasons.  With my paid VPN provider, 128 AES was the default. To force 256AES required multiple, manual, steps. I

 didn't dig into the deeper capabilities or config files for Windscribe.  There will be an ovpn text config file somewhere on your client. Inside it, will clearly say which encryption is being used. They seem to offer a number of different methods, each has a specific use-case. Picking the wrong feature to use and you could end up with cat-video safety when you really need NSA/FBI safety.  Not all types of VPN interfaces are equal.  For example, browser-based VPNs have all sorts of caveats for use if you don't want to leak information through streaming or DNS.  Almost always, the rule is the harder it is to configure, the more secure it is AND the more likely someone will make a mistake in that configuration on the server-side.

---

### Post by TheFu on 2020-07-17
Turns out that some VPN providers who claim they don't log anything have been ... er .... logging stuff.  AND they left the log files on a public server that anyone could access.

[https://www.theregister.com/2020/07/17/ufo_vpn_database/](https://www.theregister.com/2020/07/17/ufo_vpn_database/)

> A string of "zero logging" VPN providers have some explaining to do after more than a terabyte of user logs were found on their servers unprotected and facing the public internet.


Whenever it comes to VPNs, we always talk about the amount of trust for that VPN provider.  What the article above proves is that certain companies appear to have an ability to lie about things with little or no legal repercussions.  Would other companies in that same country have a similar ability?  IDK, but something to be considered when choosing a VPN, most definitely.

---

