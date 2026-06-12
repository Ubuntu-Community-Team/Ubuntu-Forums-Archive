---
title: "VPN How To Kubuntu - Junipter SSG 5"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by Tie_Domi on 2007-09-23
I recently went through a Remote VPN install for my Kubuntu Laptop and my Junipter (Netscreen (put in for google index)) SSG 5 Remote Dial-up VPN.

This is how I did it.

Please do not start asking questions because I prob will not answer them.

So before I start here are some links that helped me out

[http://www.bluetrait.com/archive/2006/09/27/racoon-to-netscreen-vpn-dialup/](http://www.bluetrait.com/archive/2006/09/27/racoon-to-netscreen-vpn-dialup/)
[http://www.prolixium.com/netscreenlinux](http://www.prolixium.com/netscreenlinux)
[http://www.bluetrait.com/archive/2006/09/01/setting-up-a-dial-up-vpn-to-connect-to-a-netscreen/](http://www.bluetrait.com/archive/2006/09/01/setting-up-a-dial-up-vpn-to-connect-to-a-netscreen/)

The last link shows you how to setup your firewall. However note when you are setting up your SSG firewall you MUST enable proxy-ID. You set it to 

Local IP / NetMask <Local Network> / <slash subnet mask>
Remote IP / NetMask 255.255.255.255 / 32

Ok now on to Ubuntu.

Run the following commands

sudo apt-get install racoon apg
nano /etc/racoon/racoon.conf

copy this config and modify to meet your requirements:

path certificate "/etc/ipsec.conf";
log notify;
path pre_shared_key "/etc/racoon/psk.txt";
listen
{
  isakmp <your ipaddress>[500];
  isakmp_natt <your ipaddress>[4500];
}

timer
{
  natt_keepalive 10 sec;
}

remote <remote IP> {
  exchange_mode aggressive;
  nat_traversal on;
  my_identifier fqdn "<your username you set in the SSG firewall>";
  peers_identifier address;
  verify_identifier off;
  lifetime time 28800 seconds;
  initial_contact on;
  passive off;
  proposal_check obey;
  generate_policy off;
   proposal {
    # for phase 1
    encryption_algorithm aes;
    hash_algorithm md5;
    dh_group 2;
    authentication_method pre_shared_key;
  }
proposal_check obey;
}

sainfo address <your ipaddress>/32 any subnet <remote subnet>/<your slash subnet> any {
  pfs_group 2;
  lifetime time 3600 seconds;
  encryption_algorithm aes;
  authentication_algorithm hmac_md5;
  compression_algorithm deflate;
}


************* NOTE I could not get SHA1 working with my firewall. Not sure why but when I used it it caused negotiation errors.

Now create your pre-shared key file.

apg -m 64 -a 1 -n 1 -M nlc
*Copy output into psk file

sudo nano /etc/racoon/psk.txt

# IPv4/v6 addresses
# USER_FQDN
# FQDN
<remote IP address>      PRESHAREDKEY

sudo chmod 400 /etc/racoon/psk.txt 

Now create your /etc/ipsec.conf file 

sudo nano /etc/ipsec.conf

#!/usr/sbin/setkey -f
#nat_traversal=yes
flush;
spdflush;
#out
spdadd <local ipaddress>/32 <remote network>/24 any
    -P out ipsec esp/tunnel/<local ipaddress>-<remote gateway>/require;
#in

spdadd <remote network>/<remote subnet> <local ipaddress>/32 any
    -P in ipsec esp/tunnel/<remote gateway>-<local ipaddress>/require;

Now you should be ready to go. Just restart racoon with sudo /etc/init.d/racoon restart

However I removed this so I created this script.

sudo nano /$HOME/racoonstart.sh

#/usr/bash
sudo setkey -f /etc/ipsec.conf
sudo racoon -f /etc/racoon/racoon.conf
ping -c 5 <ip address at remote network>

chmod 700 /$HOME/racoonstart.sh

Please note this is not the most secure setup. However for access to my home network a PSK VPN is perfect for me. Please also note that I have taken further precautions on my system to further protect it (ie harden it, firewall, snort, etc. etc, I suggest you do the same)

---

