---
title: "How to set up L2TP/IPsec VPN on Ubuntu 17.10"
date: 2018-03-16
forum: Networking &amp; Wireless
---

### Post by Penguin360 on 2018-03-16
I need to connect to my university's L2TP/IPsec VPN but I have tried a while in vain. Here is the instructions for setting up the VPN in Windows 10: [https://askit.ttu.edu/portal/app/portlets/results/view2.jsp?k2dockey=160112121042157](https://askit.ttu.edu/portal/app/portlets/results/view2.jsp?k2dockey=160112121042157)

I have installed network-manager-l2tp and network-manager-l2tp-gnome, and I can see the L2TP type of VPN from Network Manager, but after I enter all information, it will not connect. 

Can someone help me? I am basically using Ubuntu for my research but I still have to connect to my Windows computer via VPN.

Thanks in advance.

---

### Post by superlep on 2018-03-16
i resolve with strongSwan .

---

### Post by Penguin360 on 2018-03-16
> **superlep said:**
> i resolve with strongSwan .

I installed libreswan and strongswan, do I need to specify anything when I set up VPN?

---

### Post by Penguin360 on 2018-03-16
The screenshots show how I currently set up the VPN, but it does not work.

[ATTACH=CONFIG]278968[/ATTACH][ATTACH=CONFIG]278969[/ATTACH][ATTACH=CONFIG]278970[/ATTACH]

Can someone help?

---

### Post by dkosovic on 2018-03-17
For the NT Domain, you didn't enter [FONT=courier new]TTU[/FONT]

All of the proposals the TTU VPN server (vpn.ttu.edu) is offering contain weak algorithms, so newer versions of strongswan and libreswan need the phase 1 algorithms (ike) and phase 2 algorithms (esp) to be explicitly specified. See the network-manager-l2tp README.md file for details on VPN servers proposing weak algorithms :

[LIST]
[*][https://github.com/nm-l2tp/network-manager-l2tp#issue-with-vpn-servers-only-proposing-ipsec-ikev1-weak-legacy-algorithms](https://github.com/nm-l2tp/network-manager-l2tp#issue-with-vpn-servers-only-proposing-ipsec-ikev1-weak-legacy-algorithms) 
[/LIST]

The ike-scan.sh script mentioned in that section queries the VPN server for its proposals :

```

sudo ./ike-scan.sh vpn.ttu.edu | grep SA=
    SA=(Enc=3DES Hash=MD5 Group=2:modp1024 Auth=PSK LifeType=Seconds LifeDuration=28800)
    SA=(Enc=3DES Hash=SHA1 Group=2:modp1024 Auth=PSK LifeType=Seconds LifeDuration=28800)
    SA=(Enc=AES KeyLength=256 Hash=SHA1 Group=2:modp1024 Auth=PSK LifeType=Seconds LifeDuration=28800)
```

the proposal listed on the last line is the strongest, so I would recommend using that, so in the IPsec Options dialog box advanced section, enter the following:

[LIST]
[*]**Phase1 Algorithms:** aes-sha1-modp1024 
[*]**Phase2 Algorithms:** aes-sha1 
[/LIST]

With network-manager-l2tp and your VPN server, you might need to stop the system xl2tpd service, again see the README.md file for issue with not stopping the system xl2tpd:
[LIST]
[*][https://github.com/nm-l2tp/network-manager-l2tp#issue-with-not-stopping-system-xl2tpd-service](https://github.com/nm-l2tp/network-manager-l2tp#issue-with-not-stopping-system-xl2tpd-service) 
[/LIST]

---

### Post by Penguin360 on 2018-03-17
> **dkosovic said:**
> For the NT Domain, you didn't enter [FONT=courier new]TTU[/FONT]

All of the proposals the TTU VPN server (vpn.ttu.edu) is offering contain weak algorithms, so newer versions of strongswan and libreswan need the phase 1 algorithms (ike) and phase 2 algorithms (esp) to be explicitly specified. See the network-manager-l2tp README.md file for details on VPN servers proposing weak algorithms :

[LIST]
[*][https://github.com/nm-l2tp/network-manager-l2tp#issue-with-vpn-servers-only-proposing-ipsec-ikev1-weak-legacy-algorithms](https://github.com/nm-l2tp/network-manager-l2tp#issue-with-vpn-servers-only-proposing-ipsec-ikev1-weak-legacy-algorithms)
[/LIST]

The ike-scan.sh script mentioned in that section queries the VPN server for its proposals :

```

sudo ./ike-scan.sh vpn.ttu.edu | grep SA=
    SA=(Enc=3DES Hash=MD5 Group=2:modp1024 Auth=PSK LifeType=Seconds LifeDuration=28800)
    SA=(Enc=3DES Hash=SHA1 Group=2:modp1024 Auth=PSK LifeType=Seconds LifeDuration=28800)
    SA=(Enc=AES KeyLength=256 Hash=SHA1 Group=2:modp1024 Auth=PSK LifeType=Seconds LifeDuration=28800)
```

the proposal listed on the last line is the strongest, so I would recommend using that, so in the IPsec Options dialog box advanced section, enter the following:

[LIST]
[*]**Phase1 Algorithms:** aes-sha1-modp1024
[*]**Phase2 Algorithms:** aes-sha1
[/LIST]

With network-manager-l2tp and your VPN server, you might need to stop the system xl2tpd service, again see the README.md file for issue with not stopping the system xl2tpd:
[LIST]
[*][https://github.com/nm-l2tp/network-manager-l2tp#issue-with-not-stopping-system-xl2tpd-service](https://github.com/nm-l2tp/network-manager-l2tp#issue-with-not-stopping-system-xl2tpd-service)
[/LIST]


Thank you very much for your help. I disabled xl2tpd and changed both algorithms, but it didn't fix the problem. I am getting "activation of network connection failed" error 5 seconds after I tried to turn on VPN.

---

### Post by Penguin360 on 2018-03-20
Anyone please?

---

