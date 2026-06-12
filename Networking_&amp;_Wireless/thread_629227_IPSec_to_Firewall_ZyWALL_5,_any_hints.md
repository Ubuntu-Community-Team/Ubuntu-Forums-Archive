---
title: "IPSec to Firewall ZyWALL 5, any hints ?"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by ribico on 2007-12-02
Dear IPsec guru..
since days I am wondering how to configure a tunnel to my company network via IPsec to a ZyWALL firewall.
Now I understand why it is so secure.: even if you know all the parameters you cannot get it work !! :confused:

I attach two screenshots made from the administrator showing the complete configuration of the firewall.

After googoling a lot, I tried the racoon way, both using racoon directly and through Kvpnc.
As you may see from the screenshots local ID and Peer ID are used, and I did not find a way to instruct Kvpnc about that.

So I decided to go for racoon direct mode.

Here is my /etc/racoon/racoon.conf
----------------
path pre_shared_key "/etc/racoon/psk.txt";

remote AAA.BBB.CCC:DDD {
    exchange_mode aggressive;
    my_identifier user_fqdn "vpn@aaaa.com";
    peers_identifier address 10.11.10.201;
    proposal {
        encryption_algorithm aes;
        hash_algorithm sha1;
        authentication_method pre_shared_key;
        dh_group modp1024;
    }

    # Verifica l'identita' del peer su /etc/racoon/psk.txt con l'indirizzo IP.
    peers_identifier address "AAA.BBB.CCC.DDD";
    verify_identifier on;

    # Aspetta il remoto, aggiungi la policy appena si presenta.
    passive on;
    generate_policy on;

    xauth_login "pippo";
}

sainfo address 192.168.0.0/24 any address 10.11.0.0/24 any {
    encryption_algorithm aes;
    authentication_algorithm hmac_sha1;
    compression_algorithm deflate;
}
-----------------------------------



my /etc/racoon/psk.txt
-----------------------------------
AAA.BBB.CCC.DDD  passphrase
pippo  pluto
-----------------------------------


after starting racoon (sudo racoon -F -f /etc/racoon/racoon.conf) i get:

------------------------------------
gabriele@gigi:~$ sudo racoon -F -f /etc/racoon/racoon.conf
Foreground mode.
2007-12-02 11:57:16: INFO: @(#)ipsec-tools 0.6.6 ([http://ipsec-tools.sourceforge.net](http://ipsec-tools.sourceforge.net))
2007-12-02 11:57:16: INFO: @(#)This product linked OpenSSL 0.9.8e 23 Feb 2007 ([http://www.openssl.org/](http://www.openssl.org/))
2007-12-02 11:57:16: INFO: 127.0.0.1[500] used as isakmp port (fd=6)
2007-12-02 11:57:16: INFO: 127.0.0.1[500] used for NAT-T
2007-12-02 11:57:16: INFO: AAA.BBB.CCC.DDD[500] used as isakmp port (fd=7)
2007-12-02 11:57:16: INFO: AAA.BBB.CCC.DDD[500] used for NAT-T
2007-12-02 11:57:16: INFO: 192.168.0.2[500] used as isakmp port (fd=8)
2007-12-02 11:57:16: INFO: 192.168.0.2[500] used for NAT-T
2007-12-02 11:57:16: INFO: ::1[500] used as isakmp port (fd=9)
2007-12-02 11:57:16: INFO: fe80::20e:35ff:fec7:ff56%eth1[500] used as isakmp port (fd=10)
-----------------------------------


when i ping to a remote network address i get from racoon:
------------------------------------
2007-12-02 11:57:34: ERROR: failed to get sainfo.
------------------------------------

Could you suggest me anything ?
My system administrator is not a linux expert.. he managed that from windows using TheGreenBow VPN client..

thanks.

---

