---
title: "How do I access a service running on my home server from outside my home network?"
date: 2023-10-29
forum: Networking &amp; Wireless
---

### Post by Grimly Fiendish on 2023-10-29
Hello friends,

How do I ensure I can access a chosen service exposing a single port running on my home server from outside my home network?

My server is a Raspberry Pi 4B running Ubuntu 23.04.

I have a paid-for ddns account with No-IP  (https//my-made-up-name.ddns.net)

I can ping my server from anywhere using the ddns address so I’m pretty sure that side of things is working

Ports 80 and 22 are open and functioning via port forwarding rules set up on my router.

I’m running ufw on the server, here are the firewall status/rules…

zack@pi:~$ sudo ufw status numbered
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] Samba                      ALLOW IN    Anywhere                  
[ 2] OpenSSH                    ALLOW IN    Anywhere                  
[ 3] Apache                     ALLOW IN    Anywhere                  
[ 4] 10000                      ALLOW IN    Anywhere                  
[ 5] 8080                       ALLOW IN    Anywhere                  
[ 6] Samba (v6)                 ALLOW IN    Anywhere (v6)             
[ 7] OpenSSH (v6)               ALLOW IN    Anywhere (v6)             
[ 8] Apache (v6)                ALLOW IN    Anywhere (v6)             
[ 9] 10000 (v6)                 ALLOW IN    Anywhere (v6)             
[10] 8080 (v6)                  ALLOW IN    Anywhere (v6)             

zack@pi:~$ 

Running on port 10000 is Webmin which I can access from anywhere (Linux, Windows, Android) I just go to https//my-made-up-name.ddns.net:10000 and it works perfectly.

Running on port 8080 is qBittorret which I can access and runs perfectly on my home network…

But when I try to access https:// my-made-up-name.ddns.net: 8080 

I get…

This site can’t be reached

totesrandomer.ddns.net unexpectedly closed the connection.

All I want to do is to be able to access https:// my-made-up-name.ddns.net: 8080 

Port forwarding is set up for ports 8080 and 10000

I suspect it’s something really simple/obvious but I’m not too up-to-speed on networking/ip stuff and this issue is really shredding my gourd. I will be eternally grateful for any pointers.

Thank you!

---

### Post by TheFu on 2023-10-30
This is generally a really bad idea.
Only allow access into your LAN using ssh or a VPN, nothing else.  The entire world will try to hack you already and allowing a webapp access into your LAN is a bad, bad, bad, idea without much more security than you seem to have.  For example, any internet-facing services need to be on different subnets with strong firewalls than other stuff inside you LAN.  So when those other computers (available over the internet) get hacked .... and they will ... your entire home network isn't trashed.  

Definitely, in no way, should Webmin be available over the internet.

Now, if you have ssh working and only allow ssh-keys or ssh-certs to be used for authentication, never, ever, passwords, then I can help you setup a SOCKS proxy to access internal websites over the internet through an ssh tunnel.  That's fine for Linux clients.

For non-Unix clients, it is usually easier to use wireguard VPN and run the wireguard VPN server inside a full VM or on dedicated hardware (never your router!) to provide remote access into the LAN.

Using a VPN and/or using ssh provide authenticated network access that just opening ports doesn't provide.  Please listen to these warnings. Please.

So, for port forwarding of ssh / VPN to work using a DNS name, you need to 
a) Buy a domain (or use a sub-domain from a free provider)
b) Have a DNS service listed as the authoritative DNS for that specific registered domain.  I've used No-IP for this long ago. Good service.
c) Have a static IP and an ISP that doesn't block all the standard inbound ports. Most residential ISPs will block 22, 25, 20, 80, 443, 8080, 465, 587, and perhaps others ... I had one ISP that blocked all inbound ports under 10000, by default. It screwed with my SIP server which needed 5060 for SIP traffic.
d) Setup your LAN systems to get connected via ssh/wireguard with static IPs on the LAN.  
e) In your WAN Router, setup port forwarding from your static Public IP(s)"Port, to the specific static LAN IP:Port

If you don't have static IPs on both the public IP and inside your LAN, things become much harder because routers work on IPs, not names.
You can have the router perform port translation too.   So I listen for ssh on :59078/tcp on the WAN side, but forward it to 192.168.86.34:22 on the LAN side. Not all routers support port translation, but many do. In this way, I can connect specifically to the LAN ssh port or to the internet ssh port and absolutely KNOW which is being used.

f) Only at this point does the on-system firewall matter. But everything above has to be working to get this far.  
g) Setup an automatic blocking tool so when the 100,000 daily attempts to get into your system happen, they only get 3 attempts and are blocked for a week.  Denyhosts or fail2ban can be configured that way. There are others tools too.  Right now, fail2ban has  5846 bans (for 7 days) on my VPN system.  Beware.  That doesn't count the huge areas of the internet that I don't allow to get far enough for fail2ban to even see. Certain countries allow lawlessness on the internet, so I block them with huge subnet blocks upstream.

Think of it as a direct connection from the remote system to the local service. If you can't trace the path, like running a thread through 7 needles, all lined up, then it won't work.

Did I mention that allowing anything other than VPN or ssh (never with passwords, always keys/certs) is required?  The internet is a dangerous place.

---

