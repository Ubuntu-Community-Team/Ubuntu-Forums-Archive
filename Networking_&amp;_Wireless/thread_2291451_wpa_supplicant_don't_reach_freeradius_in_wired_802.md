---
title: "wpa_supplicant don't reach freeradius in wired 802.1x EAP-TLS"
date: 2015-08-20
forum: Networking &amp; Wireless
---

### Post by julie2 on 2015-08-20
Hi everybody! ):P  

I want to make setup a 802.1x EAP-TLS connexion with freeradius, wpa_supplicant and a Cisco Switch

My network : supplicant eth0-----f1/1 SWITCH f1/0-----eth1 Freeradius 

 the Switch is an emulated Switch with GNS3 (IOS Cisco c3700/3725) 
freeradius is on a vm (virtualbox, ubuntu-server 14.04) 
the supplicant is my computer (ubuntu desktop 14.04, with wpa_supplicant)  

So I run "freeradius -X" on the vm and "wpa_supplicant -Dwired -ieth0 -c/etc/wpa_supplicant/wpa_supplicant.conf -ddd" 
 Here the problem with wpa_supplicant : 
```

...
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
TX EAPOL: dst=01:80:c2:00:00:03
TX EAPOL - hexdump(len=4): 02 01 00 00
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
TX EAPOL: dst=01:80:c2:00:00:03
TX EAPOL - hexdump(len=4): 02 01 00 00
EAPOL: idleWhile --> 0
EAP: EAP entering state FAILURE
CTRL-EVENT-EAP-FAILURE EAP authentication failed
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state FAIL
EAPOL: SUPP_PAE entering state HELD
EAPOL: Supplicant port status: Unauthorized
EAPOL: SUPP_BE entering state IDLE
EAPOL authentication completed unsuccessfully
...

```
I don't know if something in this output means that the switch is responding or not... :| 
Are these normal? : startWhen --> 0 and idleWhile --> 0 ?
I see nothing on the freeradius side, it's waiting ("Ready to process requests." and no more output)
My wpa_supplicant configuration :
 ```

    ctrl_interface=/var/run/wpa_supplicant
    eapol_version=2
    ap_scan=0
    fast_reauth=1
    network={
        ssid=""
        key_mgmt=IEEE8021X
        eap=TLS

        ca_cert="/xxx/cacert.pem"
        client_cert="/xxx/client_cert.pem"
        private_key="/xxx/client_key.pem"
        private_key_passwd=""
    }

```

  My Freeradius configuration : 
```
 
/eap.conf :
    default_eap_type = tls
    tls {
        private_key_password = (rien)
        private_key_file = ${certdir}/server_key.pem    
        certificate_file = ${certdir}/server_cert.pem
        CA_file = ${certdir}/cacert.pem
        dh_file = ${certdir}/dh
        random_file = ${certdir}/random
    }    
/client.conf :
    client 192.168.2.1/24 {
        secret = pass
        shortname = R2
        nastype = cisco
    }
/users :
    admin    Cleartext-Password := "pass"
            Service-Type = NAS-Prompt-User,
            Cisco-AVPair = "shell:priv-lvl=15"

``` 

 I create a vlan for this part : SWITCH f1/0-----eth1 Freeradius, from the switch I can ping the VM and from the VM ping the vlan IP
My Cisco configuration : 
```
 
Current configuration : 1778 bytes
    !
    version 12.4
    service timestamps debug datetime msec
    service timestamps log datetime msec
    no service password-encryption
    !
    hostname R2
    !
    boot-start-marker
    boot-end-marker
    !
    logging console notifications
    !
    aaa new-model
    !
    !
    aaa authentication login default group radius
    aaa authentication dot1x default group radius
    aaa authorization network default group radius 
    !
    aaa session-id common
    memory-size iomem 5
    no ip icmp rate-limit unreachable
    ip cef    
    !         
    !         
    !         
    !         
    no ip domain lookup
    ip auth-proxy max-nodata-conns 3
    ip admission max-nodata-conns 3
    !         
    ...       
    dot1x system-auth-control
    username admin privilege 15 password 0 cisco123!
    !         
    !         
    ip tcp synwait-time 5
    !         
    ...   
    interface FastEthernet1/0
     switchport access vlan 2
    !         
    interface FastEthernet1/1
     dot1x port-control auto
    !  
    ...       
    interface Vlan1
     no ip address
    !         
    interface Vlan2
     ip address 192.168.2.1 255.255.255.0
    !         
    ip forward-protocol nd
    !         
    !         
    no ip http server
    no ip http secure-server
    !         
    !         
    !         
    radius-server host 192.168.2.5 auth-port 1812 acct-port 1813 key pass
    !         
    control-plane
    !         
    ...       
    !         
    line con 0
     exec-timeout 0 0
     privilege level 15
     logging synchronous
    line aux 0
     exec-timeout 0 0
     privilege level 15
     logging synchronous
    line vty 0 4
    !         
    !         
    end

```       

Thank's a lot for your help!

:)      J.

---

