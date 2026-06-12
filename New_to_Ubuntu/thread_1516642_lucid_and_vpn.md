---
title: "lucid and vpn"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by emarkd on 2010-06-24
Any 10.04 + vpn users that may be able to help?  I'm trying to set up my VyprVPN connection.  I followed these instructions:

[URL="https://www.goldenfrog.com/vyprvpn/setup/linux-open"]
https://www.goldenfrog.com/vyprvpn/setup/linux-open[/URL]

When I first completed the setup and tried to connect, I got the "invalid vpn secrets" error.  I rebooted and now I get no error at all.  The wireless icon "pulses" for a few seconds after I select vpn, then stops.  No notifications.

I know my account is good because I tried it from a windows box at work.  Any ideas?

Thanks!
-Mark

---

### Post by emarkd on 2010-06-24
anybody?

---

### Post by emarkd on 2010-06-24
Here's the syslog tail:

```
Jun 24 22:35:40 stratos nm-openvpn[2915]: UDPv4 link local: [undef]
Jun 24 22:35:40 stratos nm-openvpn[2915]: UDPv4 link remote: [AF_INET]216.168.2.17:1194
Jun 24 22:35:45 stratos nm-openvpn[2915]: [us1.vpn.giganews.com] Peer Connection Initiated with [AF_INET]216.168.2.17:1194
Jun 24 22:35:47 stratos nm-openvpn[2915]: AUTH: Received AUTH_FAILED control message
Jun 24 22:35:47 stratos nm-openvpn[2915]: SIGTERM[soft,auth-failure] received, process exiting
Jun 24 22:35:47 stratos NetworkManager: <info>  VPN plugin failed: 0
Jun 24 22:35:47 stratos NetworkManager: <info>  VPN plugin state changed: 6
Jun 24 22:35:47 stratos NetworkManager: <info>  VPN plugin state change reason: 10
Jun 24 22:35:47 stratos NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Jun 24 22:35:47 stratos NetworkManager: <info>  Policy set 'Coppermine' (eth1) as default for routing and DNS.

```

I see the auth_failed message there, but I swear my credentials are set up correctly in the config gui.  I can reboot this thing into windows and log in using the same credentials.

This sucks...

---

### Post by emarkd on 2010-06-25
Ok, so I decided to try it from the command line to see if I could get some more information, but I'm getting a different error here.  Here's the program output:

```
Fri Jun 25 09:27:36 2010 OpenVPN 2.1.0 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jan 26 2010
Fri Jun 25 09:27:42 2010 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Fri Jun 25 09:27:42 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Fri Jun 25 09:27:42 2010 LZO compression initialized
Fri Jun 25 09:27:42 2010 Control Channel MTU parms [ L:1576 D:140 EF:40 EB:0 ET:0 EL:0 ]
Fri Jun 25 09:27:42 2010 Data Channel MTU parms [ L:1576 D:1450 EF:44 EB:135 ET:32 EL:0 AF:3/1 ]
Fri Jun 25 09:27:42 2010 Local Options hash (VER=V4): '31fdf004'
Fri Jun 25 09:27:42 2010 Expected Remote Options hash (VER=V4): '3e6d1056'
Fri Jun 25 09:27:42 2010 Attempting to establish TCP connection with [AF_INET]216.168.3.17:1194 [nonblock]
Fri Jun 25 09:27:52 2010 TCP: connect to [AF_INET]216.168.3.17:1194 failed, will try again in 5 seconds: Connection timed out
Fri Jun 25 09:28:07 2010 TCP: connect to [AF_INET]216.168.3.17:1194 failed, will try again in 5 seconds: Connection timed out
Fri Jun 25 09:28:22 2010 TCP: connect to [AF_INET]216.168.3.17:1194 failed, will try again in 5 seconds: Connection timed out
Fri Jun 25 09:28:37 2010 TCP: connect to [AF_INET]216.168.3.17:1194 failed, will try again in 5 seconds: Connection timed out
Fri Jun 25 09:28:42 2010 SIGINT[hard,init_instance] received, process exiting
```

And it just repeats.  I understand the message but I don't know why it's happening.  I tried pinging the server and it responds very quickly.  I guess something's messed up in my config file.

I don't care how I connect, I just want to connect.  Any ideas?

---

### Post by tarps87 on 2010-06-25
I have never tried using vpn but is sounds like there are issues with the login details side of the config, this thread may help:
[http://ubuntuforums.org/showthread.php?t=1193786](http://ubuntuforums.org/showthread.php?t=1193786)

Are you behind a firewall or proxy?

---

### Post by clekstro on 2010-06-28
Hey there,
am having similar problems, but unsure as to the cause.  I am running the Lucid Netbook Edition on an eee pc 1001p, and before I setup full disk encryption the VPN was working just as promised.

I am familiar w/VyprVPN and got it to work by using the PPTP plugin instead of OpenVPN.  It had always worked immediately.  Now I'm stuck reading through the forums just like you.

I don't get any error messages when it fails either: it just gives me a blinking wireless icon and then suddenly stops...

I'll post any solutions if I find them...

EDIT: I sent in an email request @ Golden Frog's support site.  Hopefully they'll respond and I can post the results here.

---

### Post by clekstro on 2010-07-08
I'm still not having luck with OpenVPN -- neither on Windows 7 nor on Ubuntu.  I'm getting the following terminal error:

```
Output of: sudo openvpn --config /etc/openvpn/eu1.vpn.goldenfrog.com.ovpn


Fri Jul  9 01:21:41 2010 Cannot load CA certificate file ca.vyprvpn.com.crt path (null) (SSL_CTX_load_verify_locations): error:02001002:system library:fopen:No such file or directory: error:2006D080:BIO routines:BIO_new_file:no such file: error:0B084002:x509 certificate routines:X509_load_cert_crl_file:system lib
Fri Jul  9 01:21:41 2010 Exiting

```

On Windows, it just asks 3 times for the user data and then fails.  On the bright side, the PPTP connection is now working with a different vpn address.

Instead of using "us1.vyprvpn.com" or "us1.vpn.goldenfrog.com"
use **"***.vpn.giganews.com."**  That's working for me now in the short term, though pptp is less secure...

---

### Post by karen007 on 2010-11-01
You should contact their support if you still encounter problems with the setup. 
I use another VPN service called ibVPN and is as good as vyprVPN but is cheaper and has more servers for different countries.
[http://www.ibvpn.com](http://www.ibvpn.com)

---

### Post by hamil on 2011-02-05
The Giganews Diamond subscribers only have VyprVPN basic, not Pro. With VyprVPN basic, they do not offer Open VPN solutions. Solution is to NOT follow their own setup instructions, and rather set it up as PPTP.

---

