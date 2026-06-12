---
title: "After 17.04 upgrade Windows Network not accessable"
date: 2017-04-17
forum: Networking &amp; Wireless
---

### Post by raccoonstrait on 2017-04-17
Hi,

Other issues now resolved, my next task is to access the rest of my Lan. When I open thunar and click on Network, and then Windows Network I get a message "Failed to open "Windows Network" and "Failed to retrieve share list from server: No such file or directory". The other devices on my Lan are raspberry Pi's running Debian. They were accessible prior to the upgrade, and now are not, nor are they even listed. 

One thing I have found is that connecting to my router, running Tomato, is very slow from this machine. It works better from one of my Pi's, which are slow in themselves.

Reading further I checked my iptables, but I do not know how to interpret them:

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            
INPUT_direct  all  --  anywhere             anywhere            
INPUT_ZONES_SOURCE  all  --  anywhere             anywhere            
INPUT_ZONES  all  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere             ctstate INVALID
REJECT     all  --  anywhere             anywhere             reject-with icmp-host-prohibited


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            
FORWARD_direct  all  --  anywhere             anywhere            
FORWARD_IN_ZONES_SOURCE  all  --  anywhere             anywhere            
FORWARD_IN_ZONES  all  --  anywhere             anywhere            
FORWARD_OUT_ZONES_SOURCE  all  --  anywhere             anywhere            
FORWARD_OUT_ZONES  all  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere             ctstate INVALID
REJECT     all  --  anywhere             anywhere             reject-with icmp-host-prohibited


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
OUTPUT_direct  all  --  anywhere             anywhere            


Chain FORWARD_IN_ZONES (1 references)
target     prot opt source               destination         
FWDI_public  all  --  anywhere             anywhere            [goto] 
FWDI_public  all  --  anywhere             anywhere            [goto] 
FWDI_public  all  --  anywhere             anywhere            [goto] 


Chain FORWARD_IN_ZONES_SOURCE (1 references)
target     prot opt source               destination         


Chain FORWARD_OUT_ZONES (1 references)
target     prot opt source               destination         
FWDO_public  all  --  anywhere             anywhere            [goto] 
FWDO_public  all  --  anywhere             anywhere            [goto] 
FWDO_public  all  --  anywhere             anywhere            [goto] 


Chain FORWARD_OUT_ZONES_SOURCE (1 references)
target     prot opt source               destination         


Chain FORWARD_direct (1 references)
target     prot opt source               destination         


Chain FWDI_public (3 references)
target     prot opt source               destination         
FWDI_public_log  all  --  anywhere             anywhere            
FWDI_public_deny  all  --  anywhere             anywhere            
FWDI_public_allow  all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            


Chain FWDI_public_allow (1 references)
target     prot opt source               destination         


Chain FWDI_public_deny (1 references)
target     prot opt source               destination         


Chain FWDI_public_log (1 references)
target     prot opt source               destination         


Chain FWDO_public (3 references)
target     prot opt source               destination         
FWDO_public_log  all  --  anywhere             anywhere            
FWDO_public_deny  all  --  anywhere             anywhere            
FWDO_public_allow  all  --  anywhere             anywhere            


Chain FWDO_public_allow (1 references)
target     prot opt source               destination         


Chain FWDO_public_deny (1 references)
target     prot opt source               destination         


Chain FWDO_public_log (1 references)
target     prot opt source               destination         


Chain INPUT_ZONES (1 references)
target     prot opt source               destination         
IN_public  all  --  anywhere             anywhere            [goto] 
IN_public  all  --  anywhere             anywhere            [goto] 
IN_public  all  --  anywhere             anywhere            [goto] 


Chain INPUT_ZONES_SOURCE (1 references)
target     prot opt source               destination         


Chain INPUT_direct (1 references)
target     prot opt source               destination         


Chain IN_public (3 references)
target     prot opt source               destination         
IN_public_log  all  --  anywhere             anywhere            
IN_public_deny  all  --  anywhere             anywhere            
IN_public_allow  all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            


Chain IN_public_allow (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh ctstate NEW
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https ctstate NEW
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             udp dpt:isakmp ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             udp dpt:ipsec-nat-t ctstate NEW
ACCEPT     ah   --  anywhere             anywhere             ctstate NEW
ACCEPT     esp  --  anywhere             anywhere             ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             udp dpt:netbios-ns ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             udp dpt:netbios-dgm ctstate NEW
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn ctstate NEW
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds ctstate NEW
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:51413 ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             udp dpt:51413 ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             udp dpt:bootps ctstate NEW


Chain IN_public_deny (1 references)
target     prot opt source               destination         


Chain IN_public_log (1 references)
target     prot opt source               destination         


Chain OUTPUT_direct (1 references)
target     prot opt source               destination         

```

Of interest is that I can ping all of the network devices, but cannot connect to them via Thunar.

This gets more interesting. I can connect to the units that are shared using smb://192.168.1.xx. But both Thunar and Nautilus return the error message "Failed to retrieve share list from server. No such file or directory."

Any ideas?

RaccoonStrait

---

