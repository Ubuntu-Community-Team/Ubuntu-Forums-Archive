---
title: "squid and static ip address"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-07-21
ok so each time i have to take down my network for the weather and then return on the router i get an new ip address for the computer but not squid server. I want the computer and squid static so that i dont have to go to each computer and reset it up. I have it on a computer let say the id address is 1.2.3.4 for that computer so the squid ip address is 1.2.3.4 3128. then i have to shutdown the router when i turn it on the ip address for the computer is 1.2.3.5 and squid has 1.2.3.4 3128 so squid it not accepting connections because the ip address do not match. how do i fix this? below is the only changes i have made to the squid config file.

on lines631-655 in config file

acl user src 1.2.3.0/24 
http_access allow user


#  TAG: http_access
#	Allowing or Denying access based on defined access lists
#
#	Access to the HTTP port:
#	http_access allow|deny [!]aclname ...
#
#	NOTE on default values:
#
#	If there are no "access" lines present, the default is to deny
#	the request.
#
#	If none of the "access" lines cause a match, the default is the
#	opposite of the last line in the list.  If the last line was
#	deny, the default is allow.  Conversely, if the last line
#	is allow, the default will be deny.  For these reasons, it is a
#	good idea to have an "deny all" or "allow all" entry at the end
#	of your access lists to avoid potential confusion.
#
#Default:
 http_access deny all

---

### Post by bodhi.zazen on 2010-07-21
> **lance bermudez said:**
> ok so each time i have to take down my network for the weather and then return on the router i get an new ip address for the computer but not squid server. I want the computer and squid static so that i dont have to go to each computer and reset it up. I have it on a computer let say the id address is 1.2.3.4 for that computer so the squid ip address is 1.2.3.4 3128. then i have to shutdown the router when i turn it on the ip address for the computer is 1.2.3.5 and squid has 1.2.3.4 3128 so squid it not accepting connections because the ip address do not match. how do i fix this? below is the only changes i have made to the squid config file.

on lines631-655 in config file

acl user src 1.2.3.0/24 
http_access allow user


#  TAG: http_access
#    Allowing or Denying access based on defined access lists
#
#    Access to the HTTP port:
#    http_access allow|deny [!]aclname ...
#
#    NOTE on default values:
#
#    If there are no "access" lines present, the default is to deny
#    the request.
#
#    If none of the "access" lines cause a match, the default is the
#    opposite of the last line in the list.  If the last line was
#    deny, the default is allow.  Conversely, if the last line
#    is allow, the default will be deny.  For these reasons, it is a
#    good idea to have an "deny all" or "allow all" entry at the end
#    of your access lists to avoid potential confusion.
#
#Default:
 http_access deny all

Depending on your router, either configure a static IP for your clinets (most do this via MAC address) or configure your clients with a static IP address.

You can configure a static IP either from network manager or on the server edit /etc/network/interfaces.

[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

---

### Post by lance bermudez on 2010-07-21
Thank you that fixed my problem.

---

### Post by alphacrucis2 on 2010-07-21
> **lance bermudez said:**
> Thank you that fixed my problem.

Just be careful that any manually assigned static address should be outside of the DHCP address pool unless you use the MAC address method of assigning the address on the router/DHCP server.

---

### Post by bodhi.zazen on 2010-07-21
> **lance bermudez said:**
> Thank you that fixed my problem.

Sweet =)

---

