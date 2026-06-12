---
title: "UBUNTU 14 freeradius/daloradius error"
date: 2015-02-04
forum: Networking &amp; Wireless
---

### Post by k.trasschaert on 2015-02-04
Hi All, 

I just install a clean ubuntu and installed freeradius and daloradius from that tutorial. : [https://help.ubuntu.com/community/CategoryNetworking/daloRADIUS](https://help.ubuntu.com/community/CategoryNetworking/daloRADIUS)

I can reach the daloradius interface, create a user, but when i do a radtest i get a error .

i think the problem is from some "right" to allow freeradius to start.
here are the logs of : sudo freeradius -XXX

```
Wed Feb  4 16:54:06 2015 : Debug:       key = "%{User-Name}"Wed Feb  4 16:54:06 2015 : Debug:       relaxed = no
Wed Feb  4 16:54:06 2015 : Debug:   }
Wed Feb  4 16:54:06 2015 : Debug:  Module: Checking session {...} for more modules to load
Wed Feb  4 16:54:06 2015 : Debug:  Module: Checking post-proxy {...} for more modules to load
Wed Feb  4 16:54:06 2015 : Debug:  Module: Checking post-auth {...} for more modules to load
Wed Feb  4 16:54:06 2015 : Debug:  Module: Instantiating module "attr_filter.access_reject" from file /etc/freeradius/modules/attr_filter
Wed Feb  4 16:54:06 2015 : Debug:   attr_filter attr_filter.access_reject {
Wed Feb  4 16:54:06 2015 : Debug:       attrsfile = "/etc/freeradius/attrs.access_reject"
Wed Feb  4 16:54:06 2015 : Debug:       key = "%{User-Name}"
Wed Feb  4 16:54:06 2015 : Debug:       relaxed = no
Wed Feb  4 16:54:06 2015 : Debug:   }
Wed Feb  4 16:54:06 2015 : Debug:  } # modules
Wed Feb  4 16:54:06 2015 : Debug: } # server
Wed Feb  4 16:54:06 2015 : Debug: server inner-tunnel { # from file /etc/freeradius/sites-enabled/inner-tunnel
Wed Feb  4 16:54:06 2015 : Debug:  modules {
Wed Feb  4 16:54:06 2015 : Debug:  Module: Checking authenticate {...} for more modules to load
Wed Feb  4 16:54:06 2015 : Debug:  Module: Checking authorize {...} for more modules to load
Wed Feb  4 16:54:06 2015 : Debug:  Module: Checking session {...} for more modules to load
Wed Feb  4 16:54:06 2015 : Debug:  Module: Checking post-proxy {...} for more modules to load
Wed Feb  4 16:54:06 2015 : Debug:  Module: Checking post-auth {...} for more modules to load
Wed Feb  4 16:54:06 2015 : Debug:  } # modules
Wed Feb  4 16:54:06 2015 : Debug: } # server
Wed Feb  4 16:54:06 2015 : Debug: radiusd: #### Opening IP addresses and Ports ####
Wed Feb  4 16:54:06 2015 : Debug: listen {
Wed Feb  4 16:54:06 2015 : Debug:       type = "auth"
Wed Feb  4 16:54:06 2015 : Debug:       ipaddr = *
Wed Feb  4 16:54:06 2015 : Debug:       port = 0
Wed Feb  4 16:54:06 2015 : Error: Failed binding to authentication address * port 1812: Address already in use
Wed Feb  4 16:54:06 2015 : Error: /etc/freeradius/radiusd.conf[240]: Error binding to port for 0.0.0.0 port 1812



```

Here are the result of 
```
$ sudo /etc/init.d/freeradius stop * Stopping FreeRADIUS daemon freeradius                                                                                                                   
* /var/run/freeradius/freeradius.pid not found...                                                                                                 [ OK ]
administrator@RADIUS-Server:~$ sudo /etc/init.d/freeradius start
 * Starting FreeRADIUS daemon freeradius                                                                                                           [ OK ]
administrator@RADIUS-Server:~$



```

```
$ sudo radtest "Karl" "inventive" 10.9.8.208 0 test123Sending Access-Request of id 89 to 10.9.8.208 port 1812
        User-Name = "Karl"
        User-Password = "inventive"
        NAS-IP-Address = 127.0.1.1
        NAS-Port = 0
        Message-Authenticator = 0x00000000000000000000000000000000
Sending Access-Request of id 89 to 10.9.8.208 port 1812
        User-Name = "Karl"
        User-Password = "inventive"
        NAS-IP-Address = 127.0.1.1
        NAS-Port = 0
        Message-Authenticator = 0x00000000000000000000000000000000
Sending Access-Request of id 89 to 10.9.8.208 port 1812
        User-Name = "Karl"
        User-Password = "inventive"
        NAS-IP-Address = 127.0.1.1
        NAS-Port = 0
        Message-Authenticator = 0x00000000000000000000000000000000
radclient: no response from server for ID 89 socket 3
administrator@RADIUS-Server:~$



```

---

