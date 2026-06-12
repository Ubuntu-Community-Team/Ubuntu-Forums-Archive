---
title: "VPN connection to Juniper Netscreen Firewall through Racoon"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by bence8810 on 2007-05-12
Hi

I am trying to connect to our corporate VPN, but before even attempting to connect to the actual box, I set up another netscreen for testing purposes; however, I am unable to connect to this unit somehow.
The reason for the test is that I dont have access to the Corp firewall to see the logs, and I dont want to piss our IT off with attacking "seemingly" their system.

I have followed the following tutorial for the netscreen setup:

[http://www.bluetrait.com/archive/2006/09/01/setting-up-a-dial-up-vpn-to-connect-to-a-netscreen/](http://www.bluetrait.com/archive/2006/09/01/setting-up-a-dial-up-vpn-to-connect-to-a-netscreen/)

(I followed the first part only, to set up the firewall)

Then I followed this to set up racoon:

[http://www.bluetrait.com/archive/2006/09/27/racoon-to-netscreen-vpn-dialup/](http://www.bluetrait.com/archive/2006/09/27/racoon-to-netscreen-vpn-dialup/)

All went well, except I am unable to make any kind of connection, and I am sure the problem is with me, as I am new to linux, and specially to VPNs.

Here I paste the related config file from the netscreen (with forged information)

```
set user "bfrank.user" uid 1
set user "bfrank.user" ike-id fqdn "bfrank.user" share-limit 1
set user "bfrank.user" type  ike
set user "bfrank.user" "enable"
set ike gateway "bfrank.userP1" dialup "bfrank.user" Aggr outgoing-interface "untrust" preshare "scrambled_passcode" proposal "pre-g2-des-md5"
set ike gateway "bfrank.userP1" cert peer-ca all
unset ike gateway "bfrank.userP1" nat-traversal
set ike respond-bad-spi 1
set vpn "bfrank.userP2" gateway "bfrank.userP1" replay tunnel idletime 0 proposal "g2-esp-des-md5" 
set pki authority default scep mode "auto"
set pki x509 default cert-path partial
set url protocol sc-cpa
exit
set policy id 1 from "Trust" to "Untrust"  "Any" "Any" "ANY" permit 
set policy id 2 name "bfrank.user" from "Untrust" to "Trust"  "Any" "Dial-Up VPN" "ANY" tunnel vpn "bfrank.userP2" id 1 
set global-pro policy-manager primary outgoing-interface untrust
set global-pro policy-manager secondary outgoing-interface untrust
```

Here I paste my /etc/racoon/racoon.conf

```
path pre_shared_key "/etc/racoon/psk.txt";
path certificate "/etc/ipsec.conf";

padding
{
    maximum_length 20;      # maximum padding length.
    randomize off;          # enable randomize length.
    strict_check off;       # enable strict check.
    exclusive_tail off;     # extract last one octet.
}

# Specification of default various timer.
timer
{
    # These value can be changed per remote node.
    counter 5;              # maximum trying count to send.
    interval 20 sec;        # maximum interval to resend.
    persend 1;              # the number of packets per a send.

    # timer for waiting to complete each phase.
    phase1 30 sec;
    phase2 30 sec;
}

remote  VPN-PUBLIC-IP {
  exchange_mode aggressive;
  doi ipsec_doi;
  situation identity_only;
  my_identifier fqdn "bfrank.user";
  peers_identifier address;
  verify_identifier off;
  lifetime time 28800 seconds;
  initial_contact on;
  passive off;
  proposal_check obey;
  support_mip6 on;
  generate_policy off;
  nonce_size 16;
  proposal {
    encryption_algorithm des;
    hash_algorithm md5;
    authentication_method pre_shared_key;
    dh_group modp1024;
  }
}

sainfo address CLIENT-INTERNAL-IP any address VPN-INTERNAL-NETWORK/24 any {
  pfs_group modp1024;
  lifetime time 3600 seconds;
  encryption_algorithm des;
  authentication_algorithm hmac_md5;
  compression_algorithm deflate;
}

listen {
  isakmp CLIENT-INTERNAL-IP;
}

log debug2;

```

This is my /etc/racoon/psk.txt

```
VPN-PUBLIC-IP    SCRAMBLED-PASSCODE

```

And here is my /etc/ipsec.conf

```
#!/usr/sbin/setkey -f
#nat_traversal=yes
flush;
spdflush;
#out
spdadd CLIENT-INTERNAL-IP VPN-INTERNAL-NETWORK/24 any
    -P out ipsec esp/tunnel/CLIENT_IP-VPN_PUBLIC_IP/require;
#in

spdadd VPN_INTERNAL_NETWORK/24 CLIENT_INTERNAL_IP any
    -P in ipsec esp/tunnel/VPN_PUBLIC_IP-CLIENT_INTERNAL_IP/require; 

```

The issue is I don't even know how to initiate the connection, but what I read on google is that I only need to ping the remote network, which I did, and nothing happens, nothing shows up in the syslog. Then I figured I start racoon /usr/sbin/racoon and then I have the following in my syslog

```
May 11 17:19:57 bfrank-laptop racoon: INFO: @(#)ipsec-tools 0.6.6 (http://ipsec-tools.sourceforge.net) 
May 11 17:19:57 bfrank-laptop racoon: INFO: @(#)This product linked OpenSSL 0.9.8c 05 Sep 2006 (http://www.openssl.org/) 
May 11 17:19:57 bfrank-laptop racoon: WARNING: /etc/racoon/racoon.conf:36: "support_mip6" it is obsoleted.  use "support_proxy". 
May 11 17:19:57 bfrank-laptop racoon: DEBUG2: parse successed. 
May 11 17:19:57 bfrank-laptop racoon: DEBUG: open /var/run/racoon/racoon.sock as racoon management. 
May 11 17:19:57 bfrank-laptop racoon: INFO: CLIENT_INTERNAL_IP[500] used as isakmp port (fd=7) 
May 11 17:19:57 bfrank-laptop racoon: INFO: CLIENT_INTERNAL_IP[500] used for NAT-T 
May 11 17:19:57 bfrank-laptop racoon: DEBUG: get pfkey X_SPDDUMP message 
May 11 17:19:57 bfrank-laptop racoon: DEBUG2:  02120200 02000000 00000000 99420000 
May 11 17:19:57 bfrank-laptop racoon: DEBUG: pfkey X_SPDDUMP failed: No such file or directory
```

There should be more lines at least what I found on google indicates that to me. 

Also on the firewall side, I dont see any connection coming in, no requests, no failures. That firewall has a static IP, and all ports are open towards it, but it sits behind a small Cisco 806. 

This is what I get once I start racoon and check "lsof -i"

```
racoon    17086   root    7u  IPv4  61592       UDP bfrank-laptop.local:isakmp 
```

At this point I feel like dead in the water, and dont know where to start. Any suggestions are welcome,

Thanks

Ben

---

### Post by bence8810 on 2007-05-13
Hi

Meantime I tried it from another laptop, with Debian installed, and the outcome is the same, so for sure there is a problem on my end.

How should racoon initiate the connection? I just start it with /etc/init.d/racoon start

and then I see the few lines in the syslog, but no further errors, nor any progress. I also tried to ping an IP on the remote VPN network, but that either didnt create any logs, errors in the Syslog.

Am I doing something wrong?

Thanks

Ben

---

### Post by bence8810 on 2007-05-20
Hi Folks,

I have gotten further. I am able to connect to the test Netscreen. The problem was that I didnt run the following on the client PC:

```
setkey -f /etc/ipsec-tools.conf
```

Once I have done that, things went smooth. I am able to connect by pinging the remote host.

Now, I am at Phase2. I need to try to connect to the Production Netscreen but to that box I have no access to, and wouldnt like to spill errors left and right.

The only thing I am missing is the pre-shared key from that box. I have its config file, which has the key in an encrypted format with two "==" signs at the end. Can I somehow use that key in the /etc/racoon/psk.txt file? Or can I somehow decrypt it to the original phrase?

Thanks

Ben

---

