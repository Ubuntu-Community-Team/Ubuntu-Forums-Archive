---
title: "Check me - WD cloud and Ubuntu access"
date: 2021-01-28
forum: Networking &amp; Wireless
---

### Post by uacnt83982803 on 2021-01-28
Considering pulling the trigger on a WD Mycloud NAS.  Reasoning is, I want to own my backups not rely on someone else to host them or secure them.

Before I go this route, I just want to be sure that I'll be able to do the following:
1. Connect to it and read/write via Ubuntu 20.04LTS within my own network
2. Connect to it and read/write using ES File Explorer on Android (over the internet, not using wifi)
3. Connect to it and use Plex on my Android, etc. to view photos and videos

I realize this probably covers multiple forum topics but it seemed like this is the best place to ask.  I'm trying to separate myself from the big cloud photo hosting providers.

Thanks a bunch, in advance.

---

### Post by TheFu on 2021-01-28
Bad idea trusting an 3rd party to bypass your firewall.  WD as a history of poorly secured stuff like this.ventally, they patch the reported problem, sometimes after the exploit i public for years.

For remote access to your LAN over the internet, there are 2 generally secure solutions. Everything that doesn't use these are to be suspect:
[LIST]
[*]Run a full vpn that you host on yor LAN - wiregard or openvpn are the options.
[*]Run an ssh server that only accepts ssh-keys over the internet (never passwords), blocks all internet IPs that aren't in your whitelist, and blocks brute force login attempts.
[/LIST]

ssh is easier to setup, but harder to use on portable devices.
VPNs are harder to setup, but easier to use, especially from android/ios.  Go with wireguard. It is much easier than openvpn and only slightly harder than normal ssh.  After setup, you'll have ecre, fll, connectivity to your LAN from anywhere, any device. That means you don't need a plex account to access your plex content from anywhere.

I use both ssh and openvpn into my home.

---

### Post by uacnt83982803 on 2021-01-28
Agreed on avoiding 3rd party access through the firewall.  Does hosting a wireguard VPN require a server-grade Ubuntu setup?  Maybe I'd better list what I want to do in order of priority:

1. [Most important] Have a file server that I can store important data on (besides my current geographically-separated hardware backups - I just want something that's easier/faster and inside my house as a compliment to what I'm already doing)

2. [Important] Mainly because it would permit me to get rid of my A***** account (I don't buy from them any more, and only use it for photo storage and watching shows via Firestick and tablets

3. [Nice-to-have] Be able to access the contents of this storage via my phone

Appreciate the help!

---

### Post by TheFu on 2021-01-28
> **uacnt83982803 said:**
>    Does hosting a wireguard VPN require a server-grade Ubuntu setup?   


Nope. Almost any Linux install can do it.

There aren't any great differences between a server and a desktop ... well ... except a GUI doesn't exit on a server install, so none of the GUI things are installed on a server.  [LIST]
[*][https://www.howtoforge.com/how-to-set-up-wireguard-vpn-on-ubuntu-20-04/](https://www.howtoforge.com/how-to-set-up-wireguard-vpn-on-ubuntu-20-04/) seems reasonable. 
[*][https://www.cyberciti.biz/faq/ubuntu-20-04-set-up-wireguard-vpn-server/](https://www.cyberciti.biz/faq/ubuntu-20-04-set-up-wireguard-vpn-server/)
[/LIST]
I consider either of those sites as reputable. Usually, i'd want to see "ubuntu" in the domain name somewhere for guides.  And always seek how-to guides at help.ubuntu.com first.

---

