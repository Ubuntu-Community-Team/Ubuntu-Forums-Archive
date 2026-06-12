---
title: "leads to setting up a internet connection for a PS3 with some restrictions"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by kdrakon on 2008-04-30
Ok, this is my situation and if anyone has any suggestions, I am more than willing to hear them...

I am currently situated on a university residence with a caching-proxy that routes mainly HTTP common ports.  I have to specify and use this proxy for all normal internet usage (browsing, OS updates, etc.). It requires the authentication of my student id and password, so any platform that does not expect this I assume ignores it.  
The following have not worked and to my knowledge are blocked => FTP, port 8080, and most other ports since bittorrent does not work.

My question is, is it possible for me to setup an internal network on my ubuntu system to re-route traffic from/to a Playstation 3 (or any gaming console i suppose) through this proxy so that I may connect to the Playstation network for online play?

I borrowed a router (belkin Wireless G Router) and tried using that.  The uni network uses MAC address filtering, but that was alleviated through the use of address cloning on the router.  I was able to get an internet connection by specifying the proxy address on the PS3 in the following format:
```
userID:password@proxyaddress:3128
```
This succeeded, but I was ONLY capable of internet access through the internal PS3 browser (which weirdly still asked me to authenticate myself to the proxy) and through the firmware update application (which did not request authentication).
I was NOT able to connect to the Playstation Network, and received what looked like a timeout due to no connectivity.  My guess is the PSN is either using a port I cannot gain access to OR the system reached a point where the proxy was requesting authentication again and the PS3 was not handling that.
I tested both through Ethernet cable and wireless to no avail.  I gave up on this idea after a few months of playing around.

After searching around, I came across some ideas using iptables and squid.  After more research, I am still a little blurry on how I can use these tools to solve this problem.  However, if it is possible with them or anything else, I would appreciate an explanation under my circumstances.

Thank you for any input.

---

### Post by nixscripter on 2008-05-01
If the message you get is "connection timed out", instead of something like "protocol violation", then the port is probably being blocked.

The only way I know of around a blocked port is, in effect a VPN. If ssh is not blocked (port 22), then you can do it with a friendly server "on the outside" and the ssh client. However, it's a bit of a mess.

---

### Post by kdrakon on 2008-05-01
port 22 is fully available, but how exactly does the PS3 connect to the internet?  Do you mean:

```
PS3 => ubuntu laptop => ssh to outside pc => internet
```

if so, what kind of server is running on the ubuntu laptop for connectivity to the PS3, and what kind of configuration must be done on the outside pc to allow traffic from the "internet" to be tunnelled through ssh?

thank you very much for your earlier reply!

---

### Post by nixscripter on 2008-05-03
Your diagram is exactly what I mean. Specifically, PS3 will connect to the Ubuntu laptop, as if it is the game server. The Ubuntu laptop will listen on the PS3 gaming port, and forward all data to the outside PC, who forwards it to the PS3 game servers. Amazingly, if the internet PC is running ssh with port forwarding enabled (it is by default), this can be done with a single command on the local PC: ```
ssh -L ps3gameport:ps3gameserver:ps3gameport user@inetpc
``` If you connect succesfully, as long as the connection is maintained, the traffic will be forwarded. By default, it will give you a login shell and sit there. See the ssh manual page for other options that make the backgrounding easier.

Note also you may need to run the command as root if the port is priviledged (i.e. less than 1024), but that shouldn't be a problem.

Hope this helps.

---

### Post by kdrakon on 2008-05-03
thanks nixscripter, ill see what i can do

---

