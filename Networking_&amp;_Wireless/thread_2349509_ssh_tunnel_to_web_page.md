---
title: "ssh tunnel to web page"
date: 2017-01-15
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2017-01-15
Folks,

I run a laptop with 16:04 installed. I manage two friends machines remotely using ssh.

One of the machines is a R-Pi running 16:04 Mate - now for some reason accessing tightvnc via an ssh tunnel gives me a grey screen (previously worked), followed numerous possible fixes to no avail.

Is there any way I can use an ssh tunnel to access the web server on their modem? This was easy when VNC worked.

Geffers

---

### Post by TheFu on 2017-01-16
Gray screen often means there root window (X/Windows) is working, just no DE.  Try right clicking anywhere on the desktop and waiting for the menu to come up. Might take 10-30 seconds for the menu to be displayed.

Lacking any more facts, that's my only guess.

Can't you manage the systems over ssh without a GUI?

---

### Post by Geoff_Lane on 2017-01-16
> **TheFu said:**
> Gray screen often means there root window (X/Windows) is working, just no DE.  Try right clicking anywhere on the desktop and waiting for the menu to come up. Might take 10-30 seconds for the menu to be displayed.

Lacking any more facts, that's my only guess.

Can't you manage the systems over ssh without a GUI?

Most things I can manage but I need to access the modem logs, not quite sure how I can do that without opening up the modem to internet access which I don't really want to do.

Actually, might try VPN.

Geffers

---

### Post by TheFu on 2017-01-16
Logs are usually in /var/log/ ... with all the other system logs. Don't see what internet access has to do with any log files being "open" . Maybe I'm just being dumb?  

Ssh is a secure protocol - much better than pretty much any others. ssh is trivial to setup (sounds like you already have it working). 

Configuring openVPN correctly is about 10x harder.  Any other VPN probably isn't worth running. Don't use a pptp-based VPN. That protocol has been hacked for about 13 yrs. it is possible to watch that, so-called, encrypted (cough) traffic at wire-speed these days.

---

### Post by The Cog on 2017-01-16
I think he wants to open a browser on the remote host, and browse to the router management URL. The usual way would be to open a remote GUI to the remote PC, e.g. VNC.

You could use ssh with X tunnelling and launch firefox from the command line. The browser will be running on the remote PC, but its output will then be tunnelled to your local screen. It may be sluggish, but should work.
Log into the remote PC with ssh, adding the **-X** option. Then run the command **firefox** (or whatever browser you use).

EDIT
Actually here's another way: Tunnel http over the SSH connection, so that your anything connecting to (say) port 8888 on your PC gets forwarded to port 80 on the remote PC's modem.
Assumptions: 
Remote modem is 192.168.0.1
you want to browse to modem port 80
You will forward your local PC port 8888 to 192.168.0.1 port 88

The option to add to the ssh connection command (in addition to all the other options like username and destination address) is:
```
-L:127.0.0.1:8888:192.168.0.1:80
```
Then while ssh is still connected, open your local browser and connect to [http://127.0.0.1:8888/](http://127.0.0.1:8888/) - this should get forwarded to the modem

---

### Post by TheFu on 2017-01-16
I wouldn't do it that way.  Remote X is terrible and if the router/modem uses a web interface, you can have ssh provide a SOCKS proxy to it.  Changing firefox between SOCKS and no proxy is a hassle if you want to use the same profile.   

Chromium-browser accepts an option on the cmd line at startup for this. The script I use is this:
```
#!/bin/bash

# Only start SOCKS proxy if necessary
if  [ $(ps -eaf |grep ssh |grep -c 64000) = 0 ] ; then
   # Setup SOCKS proxy through home server
   echo "Starting ssh SOCKS Proxy"
   ssh -f -D 64000 gw-linux.my-domain.com -NT 
fi 

# Star private firejail with chromium, going through 
# just setup SOCKS proxy
echo "Starting Firejail chromium with private & proxy "
export http_proxy="socks5://localhost:64000"; 
firejail --private chromium-browser \
         --proxy-server="socks5://localhost:64000" &

```

All http and https traffic goes to my gw-linux machine before going anywhere else.
DNS is leaked to whatever DNS server is configured - ssh is tcp and DNS is UDP. SOCKS doesn't proxy DNS. Just the way it is.

OTOH, if the remote system (your laptop when away from the "home network") has the LAN hosts in the /etc/hosts file, then no DNS leaks happen and access to the LAN-side interfaces works.  It will also make all web surfing appear to come from your "home network", which can be handy for a number of reasons.  Been using this method for a few years to have access to media on my internal Plex media server, for example.

I always use this in coffee and cafes and pizza places and hotels to surf securely, assuming a full desktop isn't needed to have complete access to my normal desktop. If that is the situation, as for international travel, then I'd use x2go.  Much faster than VNC/RDP and authentication is by ssh-keys. Plus data doesn't leave the secured LAN this way. It is never on a laptop, so if the laptop is lost or stolen, not much is really lost, just HW.  Of course, there are lots of other security things necessary for any portable device.

ssh -X (for remove X/Windows) really only makes sense on a 100Mbps connection or better.

firejail is completely optional.

Anyway, that's how I do it. May not fit for the OP.

DO has a how-to [https://www.digitalocean.com/community/tutorials/how-to-route-web-traffic-securely-without-a-vpn-using-a-socks-tunnel](https://www.digitalocean.com/community/tutorials/how-to-route-web-traffic-securely-without-a-vpn-using-a-socks-tunnel) - I wouldn't touch the port 22 setting on the server-side. Let the router do port translation for you and setup a ~/.ssh/config file to put the port and userid and whatever else is needed inside for the connection. Make life easier.  Also, my script checks to see if the proxy was already running first. Sometimes I forget.

---

### Post by Geoff_Lane on 2017-01-18
> **The Cog said:**
> I think he wants to open a browser on the remote host, and browse to the router management URL. The usual way would be to open a remote GUI to the remote PC, e.g. VNC.

You could use ssh with X tunnelling and launch firefox from the command line. The browser will be running on the remote PC, but its output will then be tunnelled to your local screen. It may be sluggish, but should work.
Log into the remote PC with ssh, adding the **-X** option. Then run the command **firefox** (or whatever browser you use).

EDIT
Actually here's another way: Tunnel http over the SSH connection, so that your anything connecting to (say) port 8888 on your PC gets forwarded to port 80 on the remote PC's modem.
Assumptions: 
Remote modem is 192.168.0.1
you want to browse to modem port 80
You will forward your local PC port 8888 to 192.168.0.1 port 88

The option to add to the ssh connection command (in addition to all the other options like username and destination address) is:
```
-L:127.0.0.1:8888:192.168.0.1:80
```
Then while ssh is still connected, open your local browser and connect to [http://127.0.0.1:8888/](http://127.0.0.1:8888/) - this should get forwarded to the modem

Tried that, looked promising - the colon after L I think was an error and changed 192.168.0.1 to 192.168.1.254 but the web page said 403 FORBIDDEN

Geffers.

---

