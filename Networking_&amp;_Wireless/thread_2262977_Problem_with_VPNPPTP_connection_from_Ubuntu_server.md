---
title: "Problem with VPN/PPTP connection from Ubuntu server"
date: 2015-01-28
forum: Networking &amp; Wireless
---

### Post by alexsimon on 2015-01-28
We have a VPN setup.  I am able to connect to it from my local machine (a mac).  We need to build a script or process that can connect to this from a Linux based server however, so we set up a virtual box with an Ubuntu distro.  I am not able to connect to the VPN with either a regular OpenVPN connection or a PPTP connection despite trying all possible configurations and following every guide I could find (including the official ubuntu documentation).

The connection always fails, whether from the command line or the network settings drop down.  From command line I get a little bit more of an error which says that the connection timed out right after sending the configuration.  From the network settings drop down, the OpenVPN connection says 'Connection attempt timed out', for the PPTP connection it just says 'The VPN connection failed'.

What can I do to fix this or to get a more detailed error report?

---

### Post by alexsimon on 2015-01-28
Just for more info, here is what it gives me from the command line when I try to run pon:

using channel 8
Using interface ppp0
Connect: ppp0 <--> /dev/pts/6
Script pptp xxx.xxx.xxx.xxx --nolaunchpppd finished (pid 3132), status = 0x0
Modem hangup
Connection terminated.

---

### Post by alexsimon on 2015-01-28
Here is the result of running: sudo pppd call gdpvpn debug dump logfd 2 nodetach


debug debug        # (from command line)
nodetach        # (from command line)
logfd 2        # (from command line)
dump        # (from command line)
noauth        # (from /etc/ppp/peers/gdpvpn)
refuse-chap        # (from /etc/ppp/peers/gdpvpn)
refuse-mschap        # (from /etc/ppp/peers/gdpvpn)
refuse-eap        # (from /etc/ppp/peers/gdpvpn)
name xxx.xxx.xxx.xxx\\xxxxxxxxxxxx        # (from /etc/ppp/peers/gdpvpn)
remotename gdpvpn        # (from /etc/ppp/peers/gdpvpn)
        # (from /etc/ppp/peers/gdpvpn)
pty pptp xxx.xxx.xxx.xxx --nolaunchpppd        # (from /etc/ppp/peers/gdpvpn)
crtscts        # (from /etc/ppp/options)
        # (from /etc/ppp/options)
asyncmap 0        # (from /etc/ppp/options)
passive        # (from /etc/ppp/options)
silent        # (from /etc/ppp/options)
lcp-echo-failure 4        # (from /etc/ppp/options)
lcp-echo-interval 30        # (from /etc/ppp/options)
hide-password        # (from /etc/ppp/options)
ipparam gdpvpn        # (from /etc/ppp/peers/gdpvpn)
noproxyarp        # (from /etc/ppp/peers/gdpvpn)
nobsdcomp        # (from /etc/ppp/peers/gdpvpn)
nodeflate        # (from /etc/ppp/peers/gdpvpn)
require-mppe-128        # (from /etc/ppp/peers/gdpvpn)
noipx        # (from /etc/ppp/options)
using channel 11
Using interface ppp0
Connect: ppp0 <--> /dev/pts/6
Script pptp xxx.xxx.xxx.xxx --nolaunchpppd finished (pid 3340), status = 0x0
Modem hangup
Connection terminated.

---

### Post by alexsimon on 2015-01-29
No one has any ideas of what I could do to fix it?  Or what I could do to get more information out of the error reports?

---

