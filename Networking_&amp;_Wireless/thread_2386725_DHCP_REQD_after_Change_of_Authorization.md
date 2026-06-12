---
title: "DHCP_REQD after Change of Authorization"
date: 2018-03-09
forum: Networking &amp; Wireless
---

### Post by jupiterprop on 2018-03-09
Is there a way to configure dhclient and/or wpa_supplicant to re-issue a DHCP request after Deauth? I don't have control of my customer's WLC, so I need to work around this on my instrument.

Excerpt from the Cisco link ( [COLOR=#525252][FONT=inherit]https://quickview.cloudapps.cisco.com/quickview/bug/CSCuj45983 [/FONT][/COLOR]):
"When the WLC gets a CoA (Change of Authorization) RADIUS message (e.g. from ISE), the WLC will send a Deauth to the client, and move the client to DHCP_REQ state.  Unless "DHCP Required" is disabled on the WLAN, this means that the client will then be disconnected, unless it performs a new DHCP request.

With "debug client" in effect on the WLC, this message will be seen:

DHCP_REQD (7) DHCP Policy timeout. Number of DHCP request 0 from client" 

[https://quickview.cloudapps.cisco.com/quickview/bug/CSCuj45983](https://quickview.cloudapps.cisco.com/quickview/bug/CSCuj45983)

---

