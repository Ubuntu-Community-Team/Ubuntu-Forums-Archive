---
title: "VPN problems"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by tomski on 2007-01-25
Hi people,

I am try to figure out how to get my vpn connection to go through my linux firewall & am getting stuck on how i can conquer this.

here is my setup/plan

DSL line
      |
ADSL Router (netgear DG834G - natted, sharing to 3 other clients on 192.168.0.0/24) 
      |
      | 
192.168.0.10/24 (WAN/eth0)
Linux firewall/gateway (Dapper lts/shorewall
(2 interface setup, not bridged, natted, more details here [http://www.ubuntuforums.org/showthread.php?t=152101](http://www.ubuntuforums.org/showthread.php?t=152101))
192.168.1.1/24 (LAN/eth1)
      |
      |
Netgear 8 port switch
      |
      /\
     |  |
     | Web server 192.168.1.2/24
     |
Dual booted pc edgy eft / windows xp 192.168.1.10/24 (netscreen-remote vpn client)


If i remove the linux firewall out of the the setup i can connect fine to the office so guess 
that it is this that is stopping me connecting or mangling the packets.

The nescreen-reomte client uses the following settings:

Connection Security = secure

Remote party identity & addressing:
id type = ip subnet (xxx.xxx.xxx.xxx/24)
port = all
protocol = all
connect using = secure gateway tunnel
ID Type = IP address xxx.xxx.xxx.xxx (some public IP)

My Indentity:
ID type = email address (must be valid & known to the server)

Security policy = aggressive

Authentication (phase 1, proposal 1):
Authentication Method = Pre shared Key

Encryption & data integrity algorithims:
enrcryption alg = triple des
Hash alg = sha-1
Key group = diffie hellman group 2

Key exchange (phase 2, proposal 1):
IPSEC protocols
sa life = 3600 sec
compresion = none

Encapsulation protocol (esp):
Encrypt alg = triple des
Hash alg = sha-1
Encapsulation = tunnel

these settings plus the key & valid known mail address will get me to my pc in the office & nothing else (this is all i need!).

I think i have 2 choices:
1) setup the linux firewall in bridged mode ( i need more help with this as previous attempts have failed!!)
2) connect a second net card in my desktop pc direct to the adsl router & have a persistant route added so all vpn traffic goes out this net card (not much to learn from this & too defeatist for me)

I have followed many how to's for bridged firewall/gateways & vpn setup's but always seem to get it wrong or just dont know what howto i need to follow!
Do i need a client/server to connect to the office on my linux firewall & then connect to that from the client on my desktop pc? or can i have the linux firewall pass all traffic through for vpn access to my desktop pc? if so how do i do this? 

If you have any ideas or pointers please reply

---

### Post by Phulerock on 2007-03-22
Did you allow port 500 and protocol 50 in your shorewall ?

I thinks this point make you cant connect IPSEC to remote subnet. Let try it

---

### Post by tomski on 2007-04-25
yeah i got ports 500 ipsec & 50 dnat to my local IP

---

