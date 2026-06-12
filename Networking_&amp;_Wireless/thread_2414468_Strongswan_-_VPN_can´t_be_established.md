---
title: "Strongswan - VPN can´t be established"
date: 2019-03-11
forum: Networking &amp; Wireless
---

### Post by sysukbes on 2019-03-11
Hello, after a Strongswan Upgrade from 4.5.3 to 5.3.5 a lot of our Tunnels couldn´t be established. 
Here is one Example....


This is our Configuration : 
conn VPN-Tunnel-Name                                                                               
        type                   = tunnel                                                                             
        left                   = x.x.x.x                                                                    
        leftsubnet             = x.x.x.x/32                                                                      
        leftsourceip           = x.x.x.x                                                                         
        right                  = x.x.x.x                                                                  
        rightsubnet            = x.x.x.x/32                                                                    
        esp                    = aes256-sha1-modp1536                                                               
        ike                    = aes256-sha1-modp1536                                                               
        ikelifetime            = 86400s                                                                             
        keylife                = 28800s                  
        Keyexchange      =ikev1
        compress          =no                                           
        authby                 = secret                                                                             
        dpdaction              = restart                                                                            
        auto                   = start          

Log: 

initiating Main Mode IKE_SA VPN-Tunnel-Name[5748] to Customer Public IP
generating ID_PROT request 0 [ SA V V V V ]
sending packet: from Our Public IP[500] to Customer Public IP[500] (228 bytes)
received packet: from Customer Public IP[500] to Our Public IP[500] (120 bytes)
parsed ID_PROT response 0 [ SA V V ]
received XAuth vendor ID
received DPD vendor ID
generating ID_PROT request 0 [ KE No ]
sending packet: from Our Public IP[500] to Customer Public IP[500] (260 bytes)
received packet: from Customer Public IP[500] to Our Public IP[500] (236 bytes)
parsed ID_PROT response 0 [ KE No ]
generating ID_PROT request 0 [ ID HASH N(INITIAL_CONTACT) ]
sending packet: from Our Public IP[500] to Customer Public IP[500] (108 bytes)
received packet: from Customer Public IP[500] to Our Public IP[500] (76 bytes)
parsed ID_PROT response 0 [ ID HASH ]
IKE_SA VPN-Tunnel-Name[5748] established between Our Public IP[Our Public IP]...Customer Public IP[Customer Public IP]
scheduling reauthentication in 85690s
maximum IKE_SA lifetime 86230s
generating TRANSACTION request 3496621978 [ HASH CPRQ(ADDR DNS) ]
sending packet: from Our Public IP[500] to Customer Public IP[500] (76 bytes)
received packet: from Customer Public IP[500] to Our Public IP[500] (92 bytes)
parsed INFORMATIONAL_V1 request 2359048341 [ HASH N(INVAL_SYN) ]
received INVALID_SYNTAX error notify
received packet: from Customer Public IP[500] to Our Public IP[500] (92 bytes)
parsed INFORMATIONAL_V1 request 3016136106 [ HASH D ]
received DELETE for IKE_SA VPN-Tunnel-Name[5748]
deleting IKE_SA VPN-Tunnel-Name[5748] between Our Public IP[Our Public IP]...Customer Public IP[Customer Public IP]
initiating Main Mode IKE_SA VPN-Tunnel-Name[5750] to Customer Public IP
generating ID_PROT request 0 [ SA V V V V ]
sending packet: from Our Public IP[500] to Customer Public IP[500] (228 bytes)
connection 'VPN-Tunnel-Name' established successfully





Thanks in advance for all your help.

---

