---
title: "firewalld port forwarding not working with dansguardian"
date: 2016-02-14
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2016-02-14
I do not like ufw so I uninstalled it for firewalld. I have tried both
firewall-cmd --zone=home --list-all
home (active)
  interfaces: wlp4s0
  sources: 
  services: dhcpv6-client https mdns nfs samba samba-client squid ssh telnet
  ports: 8118/tcp 8080/tcp
  masquerade: no
  forward-ports: port=80:proto=tcp:toport=8080:toaddr=
  icmp-blocks: 
  rich rules: 
	
root@bermudezl:/etc/dansguardian/lists# firewall-cmd --zone=home --list-all
home (active)
  interfaces: wlp4s0
  sources: 
  services: dhcpv6-client https mdns nfs samba samba-client squid ssh telnet
  ports: 8118/tcp 8080/tcp
  masquerade: no
  forward-ports: port=80:proto=tcp:toport=8080:toaddr=1.2.3.4
  icmp-blocks: 
  rich rules: 

but unless I set the proxy setting in firefox nothing happens I was hopping to forward port 80 to 8080 so that I would not have to set the proxy settings in firefox.

---

