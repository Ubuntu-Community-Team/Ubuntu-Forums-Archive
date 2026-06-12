---
title: "IPVanish OpenVPN personal setup guide for Ubuntu 16.10"
date: 2017-03-10
forum: Networking &amp; Wireless
---

### Post by ganesh66x on 2017-03-10
Hi, here below my complete guide for setting up IPVANISH VPN for UBUNTU 16.10.

I hope it will help for your 16.04 version as well...

The  Ubuntu set guide on the IPVanish website doesn't work and I discovered a  DNS Leak issue under their setup so ... I made my own guide below instead...

My guide below assumes :
-  your put your ipvanish .ovpn and certificate files in a folder named  "IPVanish-openvpn" created under the "Documents" folder - but of course  put your files where you want, just put your folder name below instead
-  you use the Belgian ipvanish server - but of course, use the Ipvanish  server your wants, just put your server name, gateway name and ovpn  files names below instead 

Please note that all the info I'v  summarised here, I found them here and there on other forums on the  web... I'm no IT programmer... even an Ubuntu noob... but a very  resourceful noob ... it took me a full day to make it work properly  so.... Enjoy ! :)

**_IPVANISH OPENVPN PERSONAL SETUP GUIDE FOR UBUNTU 16.10_**
 
**1.  _OPENVPN NETWORK MANAGER_**
 
_Terminal_ >
**sudo apt-get install network-manager-openvpn network-manager-openvpn-gnome**
**y**
**sudo systemctl restart network-manager**
 
 
**2. _IPVANISH CONFIGS FILES_**
 
Download them from here (certificate + servers you want) and place them in folder under **Documents/IPVanish-openvpn/**
[**[https://www.ipvanish.com/software/configs/](https://www.ipvanish.com/software/configs/)**]("https://www.ipvanish.com/software/configs/")
or use the wget below :

**1° _Certificate_**
 
_Terminal_ >
**cd Documents/IPVanish-openvpn/**
**wget [http://www.ipvanish.com/software/configs/ca.ipvanish.com.crt](http://www.ipvanish.com/software/configs/ca.ipvanish.com.crt)**
 
**2. _Servers_**
 
_Terminal_ >
**cd Documents/IPVanish-openvpn/**
**wget [http://www.ipvanish.com/software/configs/ipvanish-BE-Brussels-bru-b01.ovpn](http://www.ipvanish.com/software/configs/ipvanish-BE-Brussels-bru-b01.ovpn)**
 
 
**4.  _OPENVPN SETUP_**
 
_Network Connections_ > Edit Connections... > Add > OpenVPN > Create... >
1° General : all users may connect to this network
2° VPN >
- Connection name : ** ipvanish-BE-Brussels-bru-b01**
- Gateway : **bru-b01.ipvanish.com**
**- **Type** : password**
- User name : **[IPVanish username]**
- Password : store the password only for this user + **[IPVanish password]**
- CA Certificate : import certificate **ca.ipvanish.com.crt**
3° VPN > Advanced >
1] General >
- **Use custom gateway port : 1194 (or 443) **– optional !
**- Use LZO data compression**
- **Use a TCP connection – optional** !
**- Restrict tunnel TCP Maximum Segment Size (MSS)**
2] Security >
- Cipher : **AES-256-CBC**
- HMAC Authentification : **SHA-256**
4° IPv6 Settings :
- Method : **ignore**
 
 
**6.  AUTOLOGON**
 
_Network Connections_ > [your Wifi] > Edit > General >
**Automatically connect to VPN when using this connection : ****ipvanish-BE-Brussels-****bru-b****01**
 
 
**7.  IPVANISH OPENVPN SERVER CONNECTION**
 
_Network Connections_ > VPN Connections > **ipvanish-BE-Brussels-bru-b01**
 
 
 
**_8. DNS LEAK SETUP_**
 
1° i_pvanish-BE-Brussels-__bru-b__01__.ovpn_ > Open (edit) + *Add at the end of file* *these 3 lines* :
**script-security 2**
**up /etc/openvpn/update-resolv-conf**
**down /etc/openvpn/update-resolv-conf**
 
2° _Terminal_ >
**cd Documents/IPVanish-openvpn/**
**sudo openvpn --config ipvanish-BE-Brussels-bru-b01.ovpn**
Enter Auth Username : **[IPVanish username]**
Enter Auth Password : [B][IPVanish password]


Enjoy ! :o
[/B]

---

