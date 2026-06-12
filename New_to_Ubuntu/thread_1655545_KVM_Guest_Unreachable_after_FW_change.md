---
title: "KVM Guest Unreachable after FW change"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by 2mozzie on 2010-12-29
Hello, I'm a relative beginner (not that technical).

I updated the ferm.conf file to restrict access to certain ports and after reloading with $sudo ferm /etc/ferm/ferm.conf on the host server I can no longer ping or ssh my VM (sitting on KVM) from the outside world (or even from the host itself). 

Interestingly when I added the VNC access on port 5901 that started working!

Here's the updated ferm.conf file....not sure what I removed that caused the problem!

paul@cloud:~$ cat /etc/ferm/ferm.conf
#
# -*- shell-script -*-
#
#  Configuration file for ferm(1).
#

table filter {
    chain INPUT {
        policy DROP;

        # connection tracking
        mod state state INVALID DROP;
        mod state state (ESTABLISHED RELATED) ACCEPT;

        # allow local packages
        interface lo ACCEPT;

        # respond to ping
        proto icmp ACCEPT;

        # allow IPsec
        #proto udp dport 500 ACCEPT;
        #proto (esp ah) ACCEPT;

        # allow FTP connections
        proto tcp dport ftp ACCEPT;

        # allow SSL
        proto tcp dport 443 ACCEPT;

        # allow HTTP
        proto tcp dport 80 ACCEPT;

        # allow FTP
        proto tcp dport 21 ACCEPT;

        # allow SMTP access
        proto tcp dport 25 ACCEPT;

        # allow RPS
        proto tcp dport 9444 ACCEPT;

        # allow access to Webmin
        proto tcp dport 10000 ACCEPT;

        # allow SSH connections
        proto tcp dport ssh ACCEPT;

        # Allow VNC Access
        proto tcp dport 5901 ACCEPT;

        # Allow http 8080
        proto tcp dport 8080 ACCEPT;

    }
    chain OUTPUT {
        policy ACCEPT;

        # connection tracking
        #mod state state INVALID DROP;
        mod state state (ESTABLISHED RELATED) ACCEPT;
    }
    chain FORWARD {
        policy DROP;

        # connection tracking
        #mod state state INVALID DROP;
        #mod state state (ESTABLISHED RELATED) ACCEPT;
    }
}

# IPv6:
#domain ip6 {
#    table filter {
#        chain INPUT {
#            policy ACCEPT;
#            # ...
#        }
#        # ...
#    }
#}
paul@cloud:~$

The host is running 10.04 with KVM, LAMP and SSH installed. The VM is also 10.04

I have also installed Cloudmin for VM management (which is working well).

Any help would be great.

Regards
Paul.

---

