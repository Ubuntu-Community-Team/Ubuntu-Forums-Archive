---
title: "Pptp stopped working after upgrade to 17.10"
date: 2018-01-02
forum: Networking &amp; Wireless
---

### Post by radoslav2 on 2018-01-02
Hello
After I made an upgrade from Ubuntu mate 16.10 to 17.10 my vpn connection stopped working.
My current configuration is:
cat /etc/ppp/options.pptp
```

 ###############################################################################
# $Id: options.pptp,v 1.4 2012/08/30 21:34:13 quozl Exp $
#
# Sample PPTP PPP options file /etc/ppp/options.pptp
# Options used by PPP when a connection is made by a PPTP client.
# This file can be referred to by an /etc/ppp/peers file for the tunnel.
# Changes are effective on the next connection.  See "man pppd".
#
# You are expected to change this file to suit your system.  As
# packaged, it requires PPP 2.4.2 or later from http://ppp.samba.org/
# and the kernel MPPE module available from the CVS repository also on
# http://ppp.samba.org/, which is packaged for DKMS as kernel_ppp_mppe.
###############################################################################


# Lock the port
lock


# Authentication
# We don't need the tunnel server to authenticate itself
noauth


# We won't do PAP, EAP, CHAP, or MSCHAP, but we will accept MSCHAP-V2
# (you may need to remove these refusals if the server is not using MPPE)
refuse-pap
refuse-eap
refuse-chap
refuse-mschap


# Compression
# Turn off compression protocols we know won't be used
nobsdcomp
nodeflate


# Encryption
# (There have been multiple versions of PPP with encryption support,
# choose which of the following sections you will use.  Note that MPPE
# requires the use of MSCHAP-V2 during authentication)
#
# Note that using PPTP with MPPE and MSCHAP-V2 should be considered
# insecure:
# http://marc.info/?l=pptpclient-devel&m=134372640219039&w=2
# https://github.com/moxie0/chapcrack/blob/master/README.md
# http://technet.microsoft.com/en-us/security/advisory/2743314


# http://ppp.samba.org/ the PPP project version of PPP by Paul Mackarras
# ppp-2.4.2 or later with MPPE only, kernel module ppp_mppe.o
# If the kernel is booted in FIPS mode (fips=1), the ppp_mppe.ko module
# is not allowed and PPTP-MPPE is not available.
# {{{
# Require MPPE 128-bit encryption
#require-mppe-128
# }}}


# http://mppe-mppc.alphacron.de/ fork from PPP project by Jan Dubiec
# ppp-2.4.2 or later with MPPE and MPPC, kernel module ppp_mppe_mppc.o
# {{{
# Require MPPE 128-bit encryption
#mppe required,stateless
# }}}



```
cat /etc/ppp/peers/tunnel_file
 
```

pty "pptp prodanov.biz --nolaunchpppd"
    name domain.biz\\user
    remotename PPTP
    require-mppe-128
    file /etc/ppp/options.pptp
    maxfail 0
    persist
    mtu 1392  
    ipparam tunnel_file

```

cat /etc/ppp/ip-up.d/tunnel_file
```

!/bin/sh


    route add -net 192.168.88.0 netmask 255.255.255.0 dev ppp0

```


Here are the logs:
tail -f /var/log/syslog | grep pppd

```

Jan  2 21:55:42 rpr-HP-ProBook-430-G4 pppd[2316]: pppd 2.4.7 started by root, uid 0
Jan  2 21:55:42 rpr-HP-ProBook-430-G4 pppd[2316]: Using interface ppp0
Jan  2 21:55:42 rpr-HP-ProBook-430-G4 pppd[2316]: Connect: ppp0 <--> /dev/pts/5
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pppd[2316]: LCP: timeout sending Config-Requests
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pppd[2316]: Connection terminated.
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pppd[2316]: Modem hangup
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pptp[2320]: anon warn[decaps_hdlc:pptp_gre.c:238]: pppd may have shutdown, see pppd log
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pppd[2316]: Using interface ppp0
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pppd[2316]: Connect: ppp0 <--> /dev/pts/6

```


tail -f /var/log/syslog | grep pptp

```

Jan  2 21:55:42 rpr-HP-ProBook-430-G4 pptp[2320]: anon log[main:pptp.c:353]: The synchronous pptp option is NOT activated
Jan  2 21:55:42 rpr-HP-ProBook-430-G4 pptp[2334]: anon log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan  2 21:55:42 rpr-HP-ProBook-430-G4 pptp[2334]: anon log[ctrlp_disp:pptp_ctrl.c:781]: Received Start Control Connection Reply
Jan  2 21:55:42 rpr-HP-ProBook-430-G4 pptp[2334]: anon log[ctrlp_disp:pptp_ctrl.c:815]: Client connection established.
Jan  2 21:55:43 rpr-HP-ProBook-430-G4 pptp[2334]: anon log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan  2 21:55:43 rpr-HP-ProBook-430-G4 pptp[2334]: anon log[ctrlp_disp:pptp_ctrl.c:900]: Received Outgoing Call Reply.
Jan  2 21:55:43 rpr-HP-ProBook-430-G4 pptp[2334]: anon log[ctrlp_disp:pptp_ctrl.c:939]: Outgoing call established (call ID 48985, peer's call ID 1244).
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pptp[2320]: anon warn[decaps_hdlc:pptp_gre.c:226]: short read (-1): Input/output error
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pptp[2320]: anon warn[decaps_hdlc:pptp_gre.c:238]: pppd may have shutdown, see pppd log
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pptp[2334]: anon log[callmgr_main:pptp_callmgr.c:245]: Closing connection (unhandled)
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pptp[2334]: anon log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 12 'Call-Clear-Request'
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pptp[2334]: anon log[call_callback:pptp_callmgr.c:84]: Closing connection (call state)
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pptp[2343]: anon log[main:pptp.c:353]: The synchronous pptp option is NOT activated
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pptp[2356]: anon log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pptp[2356]: anon log[ctrlp_disp:pptp_ctrl.c:781]: Received Start Control Connection Reply
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pptp[2356]: anon log[ctrlp_disp:pptp_ctrl.c:815]: Client connection established.
Jan  2 21:56:14 rpr-HP-ProBook-430-G4 pptp[2356]: anon log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan  2 21:56:14 rpr-HP-ProBook-430-G4 pptp[2356]: anon log[ctrlp_disp:pptp_ctrl.c:900]: Received Outgoing Call Reply.
Jan  2 21:56:14 rpr-HP-ProBook-430-G4 pptp[2356]: anon log[ctrlp_disp:pptp_ctrl.c:939]: Outgoing call established (call ID 18349, peer's call ID 1245).

```

tail -f /var/log/ppp-connect-errors
```

anon fatal[open_callmgr:pptp.c:525]: Call manager exited with error 256
anon warn[open_unixsock:pptp_callmgr.c:383]: bind: Address already in use
anon fatal[callmgr_main:pptp_callmgr.c:136]: Could not open unix socket for 84.22.27.96
anon fatal[open_callmgr:pptp.c:525]: Call manager exited with error 256
anon warn[open_unixsock:pptp_callmgr.c:383]: bind: Address already in use
anon fatal[callmgr_main:pptp_callmgr.c:136]: Could not open unix socket for 84.22.27.96
anon fatal[open_callmgr:pptp.c:525]: Call manager exited with error 256
anon warn[open_unixsock:pptp_callmgr.c:383]: bind: Address already in use
anon fatal[callmgr_main:pptp_callmgr.c:136]: Could not open unix socket for 84.22.27.96
anon fatal[open_callmgr:pptp.c:525]: Call manager exited with error 256

```

The same log when connection was working:
tail -f /var/log/ppp-connect-errors
```

anon warn[open_unixsock:pptp_callmgr.c:374]: Call manager for 84.22.27.96 is already running.
anon fatal[callmgr_main:pptp_callmgr.c:136]: Could not open unix socket for 84.22.27.96
anon fatal[open_callmgr:pptp.c:526]: Call manager exited with error 256
anon warn[open_unixsock:pptp_callmgr.c:374]: Call manager for 84.22.27.96 is already running.
anon fatal[callmgr_main:pptp_callmgr.c:136]: Could not open unix socket for 84.22.27.96
anon fatal[open_callmgr:pptp.c:526]: Call manager exited with error 256



```

I think this line is the error but i don't know it means:
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pptp[2320]: anon warn[decaps_hdlc:pptp_gre.c:226]: short read (-1): Input/output error
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pptp[2320]: anon warn[decaps_hdlc:pptp_gre.c:238]: pppd may have shutdown, see pppd log
Jan  2 21:56:13 rpr-HP-ProBook-430-G4 pptp[2334]: anon log[callmgr_main:pptp_callmgr.c:245]: Closing connection (unhandled)


Any help will be  appreciated.
Thank you

---

### Post by radoslav2 on 2018-01-02
I found that firewall ufw blocks connection. But i don't know how to add rule to pass only vpn traffic.

---

