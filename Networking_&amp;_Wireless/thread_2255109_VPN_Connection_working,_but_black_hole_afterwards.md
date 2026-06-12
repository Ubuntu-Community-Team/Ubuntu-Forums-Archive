---
title: "VPN Connection working, but black hole afterwards"
date: 2014-12-02
forum: Networking &amp; Wireless
---

### Post by christophdb on 2014-12-02
Hi everybody,

please help me to find my error. I am totaly depressed because I have no idea why this is not working.

I want
OPENVPN-Client (Ubuntu Notebook with UMTS) --> Internet --> PFSense Firewall --> OpenVPN-Server (Ubuntu Server)

What is working:
-  I can establish a connection from the Client to the OpenVPN-Server. All  devices can ping each other. Even I can open local webpages or samba  shares on 192.168.5.205 or 192.168.5.4 (other server on the lan).
IP-Client: 10.8.0.6
IP-Server (tun0): 10.8.0.1
IP-Server (eth0): 192.168.5.205
IP-PFSense Gateway: 192.168.5.1

My Configurations:
/etc/openvpn/server.conf (reduced to the most important things)
dev tun
server 10.8.0.0 255.255.255.0
push "route 192.168.5.0 255.255.255.0"
push "redirect-gateway"

/etc/network/iptables
*nat
: POSTROUTING ACCEPT [0:0]
-A POSTROUTING -s 10.8.0.0/24 -d 192.168.5.0/24 -j SNAT --to-source 192.168.5.205
-A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MAQUERADE
COMMIT

I can confirm that all traffic is routed through the VPN. 

ip route show (on the server)
default via 192.168.5.1 dev eth0
10.8.0.0/24 via 10.8.0.2 dev tun0
10.8.0.2 dev tun0 proto kernel scope link src 10.8.0.1
192.168.5.0/24 dev eth0 proto kernel sceope link src 192.168.5.205

Problem 1:
- I can ping from the client [http://www.google.de](http://www.google.de) and it shows me the IP 173.194.39.23
- I can do traceroute [http://www.google.de](http://www.google.de) and it takes quite a long time:
1 10.8.0.1 80 ms
2 37.148.137.57 500ms
3 217.0.67.250 600ms
...
- But if i try to open [http://www.google.de](http://www.google.de) on the page it shows me a "timeout"
- I can see no blocked packages in my pfsense firewall from the source 10.8.*

Assumption 1:
can you confirm that I have internet access via openvpn. Otherwise it should not be possible to ping anything.
but where is the problem that I can not open url pages? Is the channel back blocked? How can I debug where the problem is?

Problem 2:
- I can open via openvpn all different clients in the lan (I can open 192.168.5.* via openvpn).
- But some pages are not shown correctly. For example If I open seafile via 192.168.5.205 from the LAN everything is perfect. 
-  If I open same page via openvpn it show me only half of the page and it  seems like the computer has huge problems to resolve the url.

Do you have any idea what the problem is? It is pfsense? Is it iptables?
Thanks for your help.

---

### Post by gordintoronto on 2014-12-02
Why do you want to surf the web over the VPN connection, when you have a native Internet connection?

Why do you connect to a Ubuntu Server, when pfSense has a perfectly good OpenVPN host -- which is closer (faster) to the Internet?

What do you really want to do on the remote network?

I connect to pfSense at my office, then use KRDC to remote-desktop into every computer on the LAN. (They mostly run Windows Pro, have static IP addresses provided by pfSense based on their MAC addresses, and unique remote desktop host ports, so I connect to 192.168.168.123:1234 for example. There's a bit of Xubuntu, running X11vnc.)

---

### Post by christophdb on 2014-12-03
Hi [**[COLOR=#000000]gordintoronto[/COLOR]**]("http://ubuntuforums.org/member.php?u=507940"),

here is some meet to the background of the question:
I am working on a general raspberry pi project to do two things:
1) secure internet connection for a mobile phone over a public wlan
2) synchronisation of files to seafile or contact/calender information via caldav and carddav through VPN. VPN because I don't want to open up the ports in general.
3) the solution should be router independent. That means no matter which router somebody has he only needs to open up a port for openvpn.

It is true that pfsense would be a much more logical solution for openvpn server but this should be a general solution. So somebody gets a raspberry pi with the preconfigures setup. then this somebody opens up port 1194 to the ip of the pi and then he can use his pi to secure his internet access and he can sync his data via vpn to some services on the pi. I am looking for a setup that needs as less as possible configuration on the router of this somebody. 

Now to the problem.
Do you think it is a problem with the firewall of the raspberry pi, pfsense or the client? Did I missed some iptables rules?

Thank you very much in advance for your help.
Best regards
Christoph

---

