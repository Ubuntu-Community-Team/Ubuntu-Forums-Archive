---
title: "How-to Setup Firewall for OpenVPN?"
date: 2022-09-17
forum: Networking &amp; Wireless
---

### Post by guillaumesoucy on 2022-09-17
Hello,  
  
 
  I have OpenVPN installed and working on a Ubuntu Server 20.04 that I will upgrade to 22.04 very soon. When connecting to it, clients are able to access other machines on the local network, the one where OpenVPN is running.  

  
 
  How-to setup the firewall to restrict the clients to only having access to internet, nor the local network and the gateway?
  
 
  I do know only a little bit on firewall setup. I did look on internet and I was able to find post mainly about peoples who want to block access to internet and make the local network host reachable by clients. This is the opposite of what I need.
  
 
  I do find a thread about what I'm looking to perform, after trying out it blocks the local network on the OpenVPN side but also blocks internet access.
  
 
  This is the post I've found. After having adjusted the syntax to match my configuration, it blocks as I say above the local network and the internet access on the OpenVPN server side. So I had to revert it.  
  
 
  [https://serverfault.com/questions/250927/how-do-i-block-access-to-lan-through-openvpn/250948#250948](https://serverfault.com/questions/250927/how-do-i-block-access-to-lan-through-openvpn/250948#250948)
  
 
  Is some information are missing or if you need more information, please let me know.
  
 
  Best regards,  
  
 
  Guillaume

---

