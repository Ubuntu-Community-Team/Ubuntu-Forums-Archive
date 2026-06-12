---
title: "i am having issues using the network manager applet to setup an openvpn connection"
date: 2018-07-18
forum: Networking &amp; Wireless
---

### Post by technomooney on 2018-07-18
i have looked this up and all most all the posts and information shows different windows than what i am getting a window that looks like this after selecting the import a saved VPN configuration and selecting the *.ovpn file: [https://imgur.com/3hDljrU](https://imgur.com/3hDljrU)  i can not for the life of me get figure out what to do about this. 

i am only attempting to do this because the vpn application the service provides me uses gksudo for the privilege escalation and 18.04 has deprecated that package and i don't want to go through the process of setting it back up because it is an old software and to  get the pkexec working with the application so i don't have to have an annoying terminal in the background is something i don't want to learn as it is more annoying and a lot of research to do.

i'm running xubuntu 18.04 x64

i'll edit with whatever other info you need to help just let me know

---

### Post by kazakore on 2018-07-20
Personally I use Wireguard protocol  but below are the instructions from my VPN provider. Deleted vendor specific bits. Hope it helps....[B]


Ubuntu 16.04 or newer using Network-manager[/B]
  
[LIST=1]
[*]Open a terminal and issue "sudo apt-get install openvpn network-manager-openvpn network-manager-openvpn-gnome" 
[*]**Download** to save the configuration file. 
[*]**Network manager does not like inline crl**, so  please open the downloaded configuration file in an editor and remove  the inline crl, remove "<crl-verify>"  and everything after to   "</crl-verify>" (including that line)   and then save it. 
[*]Click on the Network icon 
[*]Click on VPN-Connections -> **Configure VPN** 
[*]Click on **Add** 
[*]Select **Import a saved vpn configuration** 
[*]navigate to where you saved the downloaded file, select it and then click **open** 
[*]**Enter your XXXX account number as in the User name field** and enter "**??**" in the password field 
[*]Click on **Save** 
[*]sudo nano -w /etc/NetworkManager/NetworkManager.conf and change "dns=dnsmasq" to "#dns=dnsmasq" and save. 
[*]Issue "sudo service network-manager restart" in a terminal 
[*]Click on Network icon -> VPN Connections -> YourVPN_** where ** is the country you selected  to connect. 
[/LIST]

---

