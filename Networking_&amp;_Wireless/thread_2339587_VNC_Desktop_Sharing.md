---
title: "VNC Desktop Sharing"
date: 2016-10-10
forum: Networking &amp; Wireless
---

### Post by davidallan on 2016-10-10
Hi,

Hoping someone can help...

I'm trying to setup desktop sharing, just on local LAN at the moment. I did have this working last week but something has stopped working...

I've enabled the desktop sharing, changed the dconf setting for encryption and i've disabled my ufw firewall temporarily.

From the client i get 'unable to connect to VNC server'.

If i run the vino-server on the host it says its already running. I've purged and reinstalled , rebooted etc....


Can anyone help?

---

### Post by steeldriver on 2016-10-10
Is networking between the two machines working otherwise e.g. can you ping the remote machine from the local machine?

What is the output of 

```

sudo netstat -nlp | grep vino

```

on the target machine?

---

### Post by davidallan on 2016-10-11
sudo netstat -nlp | grep vino

tcp6       0      0 :::5900                 :::*                    LISTEN      2474/vino-server

---

### Post by davidallan on 2016-10-11
if i kill the process and run it up from terminal it starts listening on ipv4 but still wont connect.

dna@DNAPC:/usr/lib/vino$ ./vino-server 
11/10/2016 09:36:53 Autoprobing TCP port in (all) network interface
11/10/2016 09:36:53 Listening IPv6://[::]:5900
11/10/2016 09:36:53 Listening IPv4://0.0.0.0:5900
11/10/2016 09:36:53 Autoprobing selected port 5900
11/10/2016 09:36:53 Advertising security type: 'TLS' (18)
11/10/2016 09:36:53 Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
11/10/2016 09:36:53 Listening IPv6://[::]:5900
11/10/2016 09:36:53 Listening IPv4://0.0.0.0:5900
11/10/2016 09:36:53 Clearing securityTypes
11/10/2016 09:36:53 Advertising security type: 'TLS' (18)
11/10/2016 09:36:53 Clearing securityTypes
11/10/2016 09:36:53 Advertising security type: 'TLS' (18)
11/10/2016 09:36:53 Advertising authentication type: 'No Authentication' (1)
11/10/2016 09:36:53 Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
11/10/2016 09:36:53 Listening IPv6://[::]:5900
11/10/2016 09:36:53 Listening IPv4://0.0.0.0:5900
11/10/2016 09:36:53 Clearing securityTypes
11/10/2016 09:36:53 Clearing authTypes
11/10/2016 09:36:53 Advertising security type: 'TLS' (18)
11/10/2016 09:36:53 Advertising authentication type: 'VNC Authentication' (2)
11/10/2016 09:36:53 Clearing securityTypes
11/10/2016 09:36:53 Clearing authTypes
11/10/2016 09:36:53 Advertising security type: 'TLS' (18)
11/10/2016 09:36:53 Advertising authentication type: 'VNC Authentication' (2)
11/10/2016 09:36:53 Advertising security type: 'VNC Authentication' (2)



tcp        0      0 127.0.0.1:5900          0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::5900                 :::*                    LISTEN      3846/vino-server

---

### Post by steeldriver on 2016-10-11
It looks like the IPv4 is only listening on the loopback interface (127.0.0.1:5900 - although I'm confused why the log output says 'Listening IPv4://0.0.0.0:5900') - is that intentional (it's a good thing to do for security, but implies that you're going to use SSH tunneling)?

---

### Post by davidallan on 2016-10-11
sorry im not sure why it posted a repeat of my last message :confused:

anyway, i modified the interface for use and this corrected the lookback and now shows my local IP. still cant connect tho...  0.0.0.0 means any address can connect right?

i did have this working over ssh but now nothing at all will connect to it via vnc

---

### Post by davidallan on 2016-10-11
so now i have this...


$ netstat -alpn | grep :5900
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 192.168.1.80:5900       0.0.0.0:*               LISTEN      -               
tcp        0      0 10.0.0.10:5900          0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:5900          0.0.0.0:*               LISTEN      -               
tcp        1      0 192.168.1.80:5900       10.10.10.198:43688      CLOSE_WAIT  -               
tcp        0      0 192.168.1.80:5900       10.10.10.196:58900      ESTABLISHED -               
tcp        1      0 192.168.1.80:5900       192.168.1.123:52912     CLOSE_WAIT  -               
tcp        1      0 192.168.1.80:5900       10.10.10.198:43698      CLOSE_WAIT  -               
tcp        1      0 192.168.1.80:5900       10.10.10.198:43702      CLOSE_WAIT  -               
tcp6       0      0 fe80::e31c:750f:83:5900 :::*                    LISTEN

---

