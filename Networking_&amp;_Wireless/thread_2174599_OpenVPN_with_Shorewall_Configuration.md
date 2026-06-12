---
title: "OpenVPN with Shorewall Configuration"
date: 2013-09-15
forum: Networking &amp; Wireless
---

### Post by sjl127 on 2013-09-15
I am trying to learn.  

I have Shorewall running ok on my desktop.  It works.
And I also have privatetunnel.  It works when shorewall is off.  I can not get it to work with it on.  

```
#ZONE	INTERFACE	BROADCAST	OPTIONS

net	eth0		detect
net	wlan0		detect

```

```
#                                                                                                   
#Shorewall version 4 - Zones File                                                     
#                                                                                                   
#For information about this file, type "man shorewall-zones"               
#                                                                                                   
#The manpage is also online at                                                        
#http://www.shorewall.net/manpages/shorewall-zones.html               
#                                                                                                    
############################################# 
#ZONE	TYPE		OPTIONS		IN			OUT                  
#					         OPTIONS             OPTIONS              

fw	firewall                                                                                    

net     ipv4         
```


```
# Shorewall version 4 - Policy File
#
# For information about entries in this file, type "man shorewall-policy"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-policy.html
#
######################################################################
#SOURCE		DEST		POLICY		LOG		LIMIT:BURST
#					               		      LEVEL

$FW             net             ACCEPT
net             all             DROP            info
all             all             REJECT          info
```


```
# Shorewall version 4 - Rules File
#
# For information on the settings in this file, type "man shorewall-rules"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-rules.html
#
####################################################################
#ACTION		SOURCE	       DEST	PROTO	DEST	SOURCE	  ORIGINAL    RATE	USER/MARK
#							          PORT     PORT(S)	  DEST	      LIMIT        GROUP




```





Thanks, but I"m lost just because I don't understand the code.

---

