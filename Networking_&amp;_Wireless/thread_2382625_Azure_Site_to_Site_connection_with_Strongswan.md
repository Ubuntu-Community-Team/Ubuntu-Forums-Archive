---
title: "Azure Site to Site connection with Strongswan"
date: 2018-01-15
forum: Networking &amp; Wireless
---

### Post by albini77 on 2018-01-15
Hello all,

I am trying to configure a S2S lab all in Azure between a VM running Strongswan (U5.3.5/K4.4.0-22-generic) doing the Local Network role and an Azure Gateway on the other side, using dynamic routing. I am following this article: [https://tscr.io/2018/01/03/azure-routed-vpn-with-strongswan-on-linux/](https://tscr.io/2018/01/03/azure-routed-vpn-with-strongswan-on-linux/)

My setup would be:

- Azure GW PIP 52.178.32.77
- Azure Vnet Address Space 10.20.30.0/24
- StrongSwan PIP 52.166.60.183 
- StrongSwan Vnet Addres Space 192.168.30.0/24
- StrongSwan Local IP 192.168.30.4


The issue is that the connection remains in connecting and in the /var/log/syslog log i see that the connection "flows" between the Azure Gateway PIP 52.178.32.77 and the private IP of the Strongswan 192.168.30.4 instead its public, see below:

*Jan 15 06:25:45 gw-onprem-swam charon: 13[NET] sending packet: from **192.168.30.4**[500] to **52.178.32.77**[500] (36 bytes)*
*Jan 15 06:26:09 gw-onprem-swam charon: 06[NET] received packet: from **52.178.32.77**[500] to **192.168.30.4**[500] (620 bytes)*
*Jan 15 06:26:09 gw-onprem-swam charon: 06[ENC] parsed IKE_SA_INIT request 0 [ SA KE No N(NATD_S_IP) N(NATD_D_IP) V V V V ]*
*Jan 15 06:26:09 gw-onprem-swam charon: 06[IKE] no IKE config found for 192.168.30.4...52.178.32.77, sending NO_PROPOSAL_CHOSEN*
*Jan 15 06:26:09 gw-onprem-swam charon: 06[ENC] generating IKE_SA_INIT response 0 [ N(NO_PROP) ]*


Output from "ipsec status azure", no SA's :(

*Routed Connections:*
*       azure{1}:  ROUTED, TUNNEL, reqid 1*
*       azure{1}:   192.168.30.0/24 === 10.20.30.0/24*
*Security Associations (**0 up**, 0 connecting):*
*  no match*


This is my /etc/ipsec.conf

*# ipsec.conf - strongSwan IPsec configuration file*
*config setup*
*conn azure*
*        leftupdown=/usr/local/sbin/ipsec-notify.sh # Script to create a VTI and configure the necessary routing when doing "ipsec up azure" (and remove changes when doing "ipsec down azure"*
*        authby=secret*
*        type=tunnel*
*        left=52.166.60.183 # My Public IP address*
*        leftsubnet=192.168.30.0/24 # My IP address space / protected network(s)*
*        right=52.178.32.77 #Azure Dynamic Gateway*
*        rightsubnet=10.20.30.0/24 #Azure Vnet prefixes*
*        auto=route*
*        keyexchange=ikev2 # Mandatory for Dynamic / Route-based gateway*


And this is my /usr/loca/sbin/ipsec-notify.sh

*#!/bin/bash*
*set -o nounset*
*set -o errexit*

*VTI_IF="vti${PLUTO_UNIQUEID}"*

*case "${PLUTO_VERB}" in*
*    up-client)*
*        ip tunnel add "${VTI_IF}" local "${PLUTO_ME}" remote "${PLUTO_PEER}" mode vti \*
*            okey "${PLUTO_MARK_OUT%%/*}" ikey "${PLUTO_MARK_IN%%/*}"*
*        ip link set "${VTI_IF}" up*
*        ip route add 10.20.30.0/24 dev "${VTI_IF}"*
*        sysctl -w "net.ipv4.conf.${VTI_IF}.disable_policy=1"*
*        ;;*
*    down-client)*
*        ip tunnel del "${VTI_IF}"*
*        ;;*
*esac*


Any suggestion? Many thanks :)

---

