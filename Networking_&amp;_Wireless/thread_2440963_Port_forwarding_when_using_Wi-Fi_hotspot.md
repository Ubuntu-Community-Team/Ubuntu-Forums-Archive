---
title: "Port forwarding when using Wi-Fi hotspot"
date: 2020-04-17
forum: Networking &amp; Wireless
---

### Post by tkeab on 2020-04-17
Hello,

I'd like to know how to do port forwarding when when using a Ubuntu 18.04 LTS desktop as a Wi-Fi hotspot. If using a typical, physical router, I can access to the router by typing its local IP address (e.g., [https://192.xxx.xxx.xxx](https://192.xxx.xxx.xxx)) on a web browser. Because I'm using the Wi-Fi hotspot function, however, it seems like I cannot access to the 'virtual' router. Then how can I do port forwarding?

I know I could use something like 'iptables' for port forwarding but the thing is a little tricky. My Ubuntu desktop is located in a local area network (LAN) at an institution, which has a global IP address (e.g., 210.xxx.xxx.xxx). So, my desktop has a local IP address (e.g., 192.xxx.xxx.xxx) within the LAN as well as another local IP address (e.g., 10.xxx.xxx.xxx) for the Wi-Fi hotspot's 'virtual' router mentioned above. I have all of these IP addresses but, because I cannot access the 'virtual' router, I don't know what to type in when using 'iptables'.

Basically I am trying to access to an IP camera over the Internet. So I know I need to port forward to the 554 port (RTSP) on the router.

Related to this, I'd like to know about UPnP, which seems to take care of the above task automatically, if someone knows about it.

Thanks in advance.

---

### Post by TheFu on 2020-04-17
UPnP is a security failure. Please don't use it.

iptables is how port forwarding is accomplished.  You'll need to learn it. There are 2 commands. I always have to look them up with google. If you want something easier, then use a router distro.

Also, please be certain to put some authentication **that isn't passwords** on the access for the ip camera.  Password-based authentication is a security failure. Use a private cert or some 2FA method.

Probably worth setting up port translation so the 554/tcp isn't used on the WAN, just the LAN.

---

### Post by tkeab on 2020-04-20
TheFu:

Thanks for the quick reply. And also thank for the warnings. I will be careful. 

Let me see if I correctly understand what you meant by saying "Probably worth setting up port translation so the 554/tcp isn't used on the WAN, just the LAN"?

1. A browser accesses the Internet with a domain name ([http://.](http://.)..).
2. The Internet returns the global IP address of the domain.
3. The browser accesses the domain with the global IP address. It can also specify a port number (say, 80).
4. The domain receives the port number (80) and translates it to a different port number (554, maybe?) at a specific local IP address.
5. The machine having the local IP address (and the one functioning as a Wi-Fi hotspot) further translates 554 to a specific port number of the IP camera I'm using.  

Am I missing any step?

Thanks in advance.

---

### Post by TheFu on 2020-04-20
No. The security profile and required mitigations greatly if you're going to allow a browser access.

A browser shouldn't have any direct access to the camera from the internet.  A tunnel using either a self-hosted VPN or ssh-SOCKS proxy should be used.  

With an ssh-proxy, only a high-port for ssh need be enabled.  All viewers should use ssh-keys to gain access to the internal LAN, and the internal webapp that can show the video/images or anything else.  Normal ssh security would be involved, but the camera and webapp wouldn't need anything special.  The same would apply if you setup a self-hosted VPN, though the VPN is harder to setup.

Regardless, don't use the normal ports for anything on the WAN interface.  Use strange, high, ports and have your router take those and forward to the static LAN ip and normal ports.  Cheap routers have been doing this for 15+ yrs.

This thread is an example of asking for the answer to a step in the solution, but the "best" solutions don't actually need the answer to the question.
If you search these forums for "ssh proxy tunnel" an example script that is run on the client should be found. All the needs to be setup for the ssh proxy to work is normal ssh connectivity and normal ssh security, both which are well-traveled.

---

