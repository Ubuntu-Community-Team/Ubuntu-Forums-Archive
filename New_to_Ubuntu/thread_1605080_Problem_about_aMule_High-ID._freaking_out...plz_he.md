---
title: "Problem about aMule High-ID. freaking out...plz help...."
date: 2010-10-24
forum: New to Ubuntu
---

### Post by zeuso0 on 2010-10-24
My ubuntu is 9.04.No extra firewall installed. Want to turn low-id to High-id. So I did the following steps.1&#12290;in Amule preference-&#12299;connection set TCP port 4662&#65292;UDP 4672&#12290;download 200kb/s&#65292;upload 100kb/s.  Slot Allocation 2kb/s(I didn't change this&#65289;.Also marked Enable UPnp default:500002&#12290;I enter the router&#12290;Did the following three settings on port forwardin&#65306;   1) aMule  4662 to 4662 TCP  My_IP    enable   2)aMule  4672 to 4672 UDP  My_IP    enable      3) aMule  4665 to 4665 UDP  My_IP    enable     I also enabled DHCP in the router&#65292;3&#12290;aMule infomation after connected (with low-id appeared) &#65306;   aMule log: warning:Low-ID  Most likely is because you're behind a firewall or router  (don't understand, I didn't install firewall,n I thought I've done the port mapping&#65289;   ed2k info: status&#65306;connect;  IP:Port   Server  ID  *** LowID    kap info: Kademlia &#29366;&#24577;&#65306;running&#65307;   status:connected&#65307;               Connection State: Firewalled( didn't get this either. Does ubuntu has a default firewall?)Firewalled State: No buddy**********have spent the whole day on it but still couldn't figure it out.can anybody help me out here??Thank you!

---

### Post by zeuso0 on 2010-10-24
My ubuntu is 9.04.No extra firewall installed. Want to turn low-id to High-id. So I did the following steps.
***1&#12290;in Amule preference-&#12299;connection set TCP port 4662&#65292;UDP 4672&#12290;download 200kb/s&#65292;upload 100kb/s. Slot Allocation 2kb/s(I didn't change this&#65289;.Also marked Enable UPnp default:50000 
***2&#12290;I enter the router&#12290;Did the following three settings on port forwardin&#65306; 1) aMule 4662 to 4662 TCP My_IP enable 2)aMule 4672 to 4672 UDP My_IP enable 3) aMule 4665 to 4665 UDP My_IP enable I also enabled DHCP in the router
***3&#12290;aMule infomation after connected (with low-id appeared) &#65306; 
aMule log: warning:Low-ID Most likely is because you're behind a firewall or router (don't understand, I didn't install firewall,n I thought I've done the port mapping&#65289; ed2k info: status&#65306;connect; IP:Port Server ID *** Low-ID
kap info: Kademlia status&#65306;RUNNING&#65307; status:connected&#65307; 
Connection State:FIREWALLED ( didn't get this either. Does ubuntu has a default firewall?)
Firewalled State: No buddy**********have spent the whole day on it but still couldn't figure it out.can anybody help me out here??Thank you!

---

### Post by cariboo on 2010-10-24
Ubuntu does have a firewall installed by default, but it isn't enabled. To check the status of the firewall open a terminal and type:

```
sudo iptables -L
```

if the firewall is disabled, you should see several empty rules.

If the firewall is enabled, disable using the following command:

```
sudo ufw disable
```

to check if youhave port forwarding setup properly, use [canyouseeme]("http://www.canyouseeme.org/")

---

### Post by cariboo on 2010-10-24
Please  don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by zeuso0 on 2010-10-25
I am sorry,I am new to this forum.

I disabled the firewall but low-id still exists . it said"Your 4662 port is not reachable." what does that mean?

Thanks
Joe

---

### Post by zeuso0 on 2010-10-25
and I've tried to deleted the whole server lists in aMule and downloaded the latest one from [http://ed2k.2x4u.de/index.html](http://ed2k.2x4u.de/index.html). but "port 4662 not reachable" still exists.
I also have tried change TCP port to 4661 and correspondingly changed to forward port 4661 and port 4664,
but still didn't work.

HOW do I fix this problem ?? plz..

---

### Post by JustinR on 2010-10-25
> **zeuso0 said:**
> and I've tried to deleted the whole server lists in aMule and downloaded the latest one from [http://ed2k.2x4u.de/index.html](http://ed2k.2x4u.de/index.html). but "port 4662 not reachable" still exists.
I also have tried change TCP port to 4661 and correspondingly changed to forward port 4661 and port 4664,
but still didn't work.

HOW do I fix this problem ?? plz..

You could try launching it with administrative privileges - ALT + F2 and type: "gksudo amule"

---

### Post by zeuso0 on 2010-10-25
> **JustinR said:**
> You could try launching it with administrative privileges - ALT + F2 and type: "gksudo amule"

Thanks for the reply. 

I did as you said. but still "port 4662 is not reachable",  plus  my kad is not running now! :(

Joe

---

### Post by zeuso0 on 2010-10-25
Here is my aMule info.  and it keeps telling me port 4662 not reachable and it said something about UPNP, is there anything wrong with that??

*************************************************
2010-10-25 20:58:30: Starting aMule 2.2.4 using wxGTK2 v2.8.9
2010-10-25 20:58:30: Creditfile loaded, 8 clients are known
2010-10-25 20:58:30: Loading IP-filters 'ipfilter.dat' and 'ipfilter_static.dat'.
2010-10-25 20:58:30: Loaded 0 IP-ranges from '/home/zhou7/.aMule/ipfilter.dat'. 0 malformed lines were discarded.
2010-10-25 20:58:30: Loaded 0 IP-ranges from '/home/zhou7/.aMule/ipfilter_static.dat'. 0 malformed lines were discarded.
2010-10-25 20:58:30: External connections disabled in config file
2010-10-25 20:58:30: Created Server UDP-Socket at port 4665
2010-10-25 20:58:30: Created Client UDP-Socket at port 4672
2010-10-25 20:58:30: Universal Plug and Play: bound to 192.168.18.10:50000.
2010-10-25 20:58:30: Universal Plug and Play: Internet Gateway Device Detected.
2010-10-25 20:58:30: Universal Plug and Play: Uninteresting service detected: 'urn:schemas-upnp-org:service:WANEthernetLinkConfig:1'. Ignoring.
2010-10-25 20:58:30: Universal Plug and Play: WAN Service Detected: 'urn:schemas-upnp-org:service:WANIPConnection:1'.
2010-10-25 20:58:30: Universal Plug and Play: Successfully retrieved SCPD Document for service urn:schemas-upnp-org:service:WANIPConnection:1, absEventSubURL: [http://192.168.18.1:2869/WANIPConnEvtUrl](http://192.168.18.1:2869/WANIPConnEvtUrl).
2010-10-25 20:58:30: Universal Plug and Play: Successfully subscribed to service urn:schemas-upnp-org:service:WANIPConnection:1, absEventSubURL: [http://192.168.18.1:2869/WANIPConnEvtUrl](http://192.168.18.1:2869/WANIPConnEvtUrl).
2010-10-25 20:58:30: Universal Plug and Play: Uninteresting service detected: 'urn:schemas-upnp-org:service:WANCommonInterfaceConfig:1'. Ignoring.
2010-10-25 20:58:30: Universal Plug and Play: Uninteresting service detected: 'urn:schemas-upnp-org:service:Layer3Forwarding:1'. Ignoring.
2010-10-25 20:58:30: Universal Plug and Play: UPNP_EVENT_RECEIVED:
2010-10-25 20:58:30:     SID: uuid:237344f8-1dd2-11b2-a1f6-cac5da6c0966
2010-10-25 20:58:30:     Key: 0
2010-10-25 20:58:30:     Property list:
2010-10-25 20:58:30:         PossibleConnectionTypes='IP_Routed'
2010-10-25 20:58:30:         ConnectionStatus='Connected'
2010-10-25 20:58:30:         ExternalIPAddress='10.20.104.58'
2010-10-25 20:58:30:         PortMappingNumberOfEntries='0'
2010-10-25 20:58:30: Universal Plug and Play: Internet Gateway Device Detected.
2010-10-25 20:58:30: Universal Plug and Play: UPNP_EVENT_RECEIVED:
2010-10-25 20:58:30:     SID: uuid:237344f8-1dd2-11b2-a1f6-cac5da6c0966
2010-10-25 20:58:30:     Key: 1
2010-10-25 20:58:30:     Property list:
2010-10-25 20:58:30:         PortMappingNumberOfEntries='6'
2010-10-25 20:58:30: Universal Plug and Play: UPNP_EVENT_RECEIVED:
2010-10-25 20:58:30:     SID: uuid:237344f8-1dd2-11b2-a1f6-cac5da6c0966
2010-10-25 20:58:30:     Key: 2
2010-10-25 20:58:30:     Property list:
2010-10-25 20:58:30:         PortMappingNumberOfEntries='7'
2010-10-25 20:58:30: Universal Plug and Play: UPNP_EVENT_RECEIVED:
2010-10-25 20:58:30:     SID: uuid:237344f8-1dd2-11b2-a1f6-cac5da6c0966
2010-10-25 20:58:30:     Key: 3
2010-10-25 20:58:30:     Property list:
2010-10-25 20:58:30:         PortMappingNumberOfEntries='8'

2010-10-25 20:58:30:  - This is aMule 2.2.4 using wxGTK2 v2.8.9 based on eMule.
2010-10-25 20:58:30:    Running on Linux 2.6.28-19-generic i686
2010-10-25 20:58:30:  - Visit [http://www.amule.org](http://www.amule.org) to check if a new version is available.

2010-10-25 20:58:30: Loaded 248 flag bitmaps.
2010-10-25 20:58:30: Loading server.met file: /home/zhou7/.aMule/server.met
2010-10-25 20:58:31: 188 servers in server.met found
2010-10-25 20:58:31: No part files found
2010-10-25 20:58:31: Found 1 known shared file
2010-10-25 20:58:31: Connecting
2010-10-25 20:58:31: Connecting to [www.total.com](www.total.com)  (204.45.72.58 - 204.45.72.58:4232)
2010-10-25 20:58:31: ThreadScheduler: Completed task 'AICH Syncronizing', 0 tasks remaining.
2010-10-25 20:58:31: Connecting to UltraUploader (77.247.179.5 - 77.247.179.5:6231) using protocol obfuscation.
2010-10-25 20:58:31: Connected to [www.total.com](www.total.com)  (204.45.72.58:4232)
2010-10-25 20:58:32: You are using an outdated version of aMule!
2010-10-25 20:58:32: Your aMule version is 2.2.4 and the latest version is 2.2.6
2010-10-25 20:58:32: The latest version can always be found at [http://www.amule.org](http://www.amule.org)
2010-10-25 20:58:32: Connected to UltraUploader (77.247.179.5:6231)
2010-10-25 20:58:33: WARNING: [www.total.com](www.total.com)  (204.45.72.58:4232) - NG : Your 4662 port is not reachable. Please review your network config.
2010-10-25 20:58:33: Connection established on: [www.total.com](www.total.com)
2010-10-25 20:58:33: New clientid is 1454408
2010-10-25 20:58:33: WARNING: You have received Low-ID!
2010-10-25 20:58:33:     Most likely this is because you're behind a firewall or router.
2010-10-25 20:58:33:     For more information, please refer to [http://wiki.amule.org](http://wiki.amule.org)
2010-10-25 20:59:11: Only 0 Kad contacts available, nodes.dat not written
2010-10-25 20:59:21: The URL [http://emule-inside.net/nodes.dat](http://emule-inside.net/nodes.dat) returned: 410 - Error (6)!
2010-10-25 20:59:21: Failed to download the nodes list.
2010-10-25 21:04:41: Only 0 Kad contacts available, nodes.dat not written
2010-10-25 21:04:41: Read 166 Kad contacts
2010-10-25 21:05:14: Wrote 166 Kad contacts
2010-10-25 21:05:35: Connecting to Emule Server No1 (94.75.216.6 - 94.75.216.6:4666) using protocol obfuscation.
2010-10-25 21:05:35: Connected to Emule Server No1 (94.75.216.6:4666)
2010-10-25 21:05:37: WARNING: Emule Server No1 (94.75.216.6:4666) - NG : Your 4662 port is not reachable. Please review your network config.
2010-10-25 21:05:37: Connection established on: Emule Server No1
2010-10-25 21:05:37: New clientid is 12893598
2010-10-25 21:05:37: WARNING: You have received Low-ID!
2010-10-25 21:05:37:     Most likely this is because you're behind a firewall or router.
2010-10-25 21:05:37:     For more information, please refer to [http://wiki.amule.org](http://wiki.amule.org)

---

