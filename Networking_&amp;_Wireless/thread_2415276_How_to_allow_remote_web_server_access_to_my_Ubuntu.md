---
title: "How to allow remote web server access to my Ubuntu 18.04 when using NordVPN on Hyperv"
date: 2019-03-23
forum: Networking &amp; Wireless
---

### Post by brian_gillette on 2019-03-23
Hi all, hoping there are some network guru's here to help me figure out an issue with remote access to a web page i have running on Ubuntu18.04 when i'm using a vpn client.
I have ubuntu18.04 installed in a windows 10 Hyper-v and Ubuntu is setup with a static ip address of 192.168.0.95.  On Ubuntu i have NordVPN installed, as well as NOIP client "ddclient" and utorrent server running on port 8081. The Utorrent server has a web page you can get to in order to do application management of utorrent. I enable the vpn when needed, it is not setup to auto-start.  i have a NOIP account with the ddclient running on Ubuntu continually. It is working as expected to publish my web IP address to NOIP. It is working fine - when i do not have NordVPN enabled it is broadcasting my public IP address. When NordVPN is enabled it is broadcasting my NordVPN provided IP address correctly.  I have my router setup to forward port 8081 to my Ubuntu computer. I have the Ubuntu firewall set to allow traffic for port 8081.

With the NORVPN disabled i can get to the Utorrent application management page from my other computers in the house by opening [http://192.168.0.095:8081/gui/web/index.html]("http://192.168.0.195:8081/gui/web/index.html") just fine.   I can also open it remotely from those computers and outside my home LAN network by using my NOIP domain name, like : [http://brian.ddns.net:8081/gui/web/index.html](http://brian.ddns.net:8081/gui/web/index.html).

Initially when i enabled the NordVPN i am unable to access the the Utorrent application management page on port 8081 remotely from any of my other computers on my internal LAN. Nordvpn has a port whilelisting function that lest you whitelist a specific port, so i used it to whitelist port 8081 on the ubuntu comptuer.   That worked fine to allow my other computers on my home LAN to access the utorrent management page using the internal IP address of the Ubuntu computer ([http://192.168.0.95:8081/gui/web/index.html](http://192.168.0.95:8081/gui/web/index.html)), but i sill cannot access it externally from outside my home LAN via my NOIP domain name using [http://brian.ddns.net:8081/gui/web/index.html](http://brian.ddns.net:8081/gui/web/index.html)

Additionally, important to note, i have 2 NOIP domains - one that updates my public IP address from my ISP, and one that updates my VPN IP address provided by NordVPN when i'm using NordVPN. (so something like brian.ddns.net and brianvpn.ddns.net) I have tried using both, no go.
I'm sure i'm just overlooking some very basic concept of networking and VPN that i'm just ignorant of. was hoping if someone could tell me if this is possible to do, and some pointers on how to configure things if it is.

---

