---
title: "l2tp/ipsec vpn client using x509 certificates"
date: 2014-08-22
forum: Networking &amp; Wireless
---

### Post by lee-musgrave on 2014-08-22
Hi, 
i'm going mad trying to get Ubuntu 14.04 client  machines to connect to my vpn server. I've tried following various tutorials/instructions, most of which are confusing, and some of which are downright contradictory, and I've lost count of the number of times I've now installed/removed/re-installed x2ltpd, openswan and l2tp-ipsec-vpn 

i know the vpn server works, and i can connect perfectly fine (and simply) from windows clients. all certificates were created by me, and i can easily split any of the .p12 files into separate pem files as required.

below is the configuration of the vpn server (vyatta - debian based open-source router/firewall) and below that is how I've got the windows client working (included so you can see exactly how i need to connect). 

can someone please let me know exactly how to create this vpn client in Ubuntu

 
vyatta vpn server configuration:

vpn {
 ipsec {
  ipsec-interfaces {
   interface eth0
  }
  logging {
   log-modes all
  }
  nat-networks {
   allowed-network 0.0.0.0/0 {
    exclude 192.168.40.0/24
   }
  }
  nat-traversal enable
 }
 l2tp {
  remote-access {
   authentication {
    local-users {
     username lee {
      static-ip 192.168.40.151
     }
    }
    mode local
   }
   client-ip-pool {
    start 192.168.40.11
    stop 192.168.40.200
   }
   ipsec-settings {
    authentication {
     mode x509
     x509 {
      ca-cert-file /config/auth/SCL_CA.crt
      server-cert-file /config/auth/l2tp_vpn.crt
      server-key-file /config/auth/l2tp_vpn.pem
     }
    }
    ike-lifetime 3600
   }
   outside-address 192.168.2.25 (149.6.10.235)
   outside-nexthop 192.168.2.1  (149.6.10.233)
  }
 }
}
 
 
how i created a working vpn client on windows:
in certificates mmc:
 computer account - local computer
  personal  -- install the user certificate (.p12 file)
  trusted root certification authority -- install the CA certificate (.crt file) - 
   (same file as the certificate authority certificate on vpn server above)
create new connection following wizard in network & sharing center, vpn connection - enter server ip address (192.168.2.25)
open up network adapter properties - security - select lt2p/ipsec
 under advanced settings - select use certificate for authentication,
  verify the name and usage attribues of the server's certificate is ticked
 authentication :
  EAP - deselected
  allow these protocols - selected
   PAP - unselected
   CHAP and MS-CHAP v2 selected
     -automatically use my windows logon name and password unchecked.

---

