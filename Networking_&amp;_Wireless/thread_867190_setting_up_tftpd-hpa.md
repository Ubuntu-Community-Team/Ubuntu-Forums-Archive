---
title: "setting up tftpd-hpa"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by Leebria on 2008-07-22
Hello, I have installed tftpd-hpa on my server and am having a problem with clients establishing a connection. I have gotten all my server side apps working except for tftp functionality. When I try to initialize a tftp sessionfrom my switch using:
 
        copy startup-config tftp 2001::dead:beef st.conf

I get an error saying "Error in sending rq message. Exceeded 5 retransmits." 

My /etc/inetd.conf looks like:

        tftp dgram udp6 nowait tftpd /usr/sbin/tcpd /usr/sbin/in.tftpd /srv/tftp

The tftp daemon is running and I have my switch set to tftp client mode. Any thoughts?

---

### Post by Leebria on 2008-07-22
It would appear the daemon I'm running is only for IPv4. Does anyone have suggestions for an IPv6 tftp server?

---

### Post by tybalt on 2008-10-03
My suggestion is you create 2 different lines in the inetd.config file. one should include the udp6 (as per your current config) and the other one with udp4. This way, you start 2 differetn tftp servers on the 2 different IP versions.

My inetd.config file claims "wait" for tftp, in opposition to yours...

hope this helps.

---

