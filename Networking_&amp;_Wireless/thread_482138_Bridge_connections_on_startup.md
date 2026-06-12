---
title: "Bridge connections on startup"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by KitChy on 2007-06-23
So I'm able to bridge my two wired connections (eth0 + eth1) using brctl and ifconfig but I want to know if there's a way to bridge the two connections on start up?

---

### Post by harty83 on 2007-06-23
This is a script developed to be used by openvpn to bridge a connection on startup.  You may be able to modify it to be used for your needs.

```
#!/bin/bash  
# Create global variables   
# Define Bridge Interface 
br="br0" 
# Define list of TAP interfaces to be bridged, 
# for example tap="tap0 tap1 tap2". 
tap="tap0" 
# Define physical ethernet interface to be bridged 
# with TAP interface(s) above. 
eth="eth2" 
eth_ip="10.8.6.50" 
eth_netmask="255.255.255.0" 
eth_broadcast="10.8.6.255" 
gw="10.8.6.1"   

start_bridge () {   
#################################   
# Set up Ethernet bridge on Linux   
# Requires: bridge-utils   
#################################    
for t in $tap; do
     openvpn --mktun --dev $t   
done    
for t in $tap; do
     ifconfig $t 0.0.0.0 promisc up   
done

ifconfig $eth 0.0.0.0 promisc up

brctl addbr $br 
brctl addif $br $eth
for t in $tap; do
     brctl addif $br $t   
done    
ifconfig $br $eth_ip netmask $eth_netmask broadcast $eth_broadcast up   
route add default gw $gw $br
} 

stop_bridge () {   
####################################   
# Tear Down Ethernet bridge on Linux   
####################################    
ifconfig $br down
brctl delbr $br    
for t in $tap; do
     openvpn --rmtun --dev $t   
done   

ifconfig $eth $eth_ip netmask $eth_netmask broadcast $eth_broadcast up   
route add default gw $gw $eth
}  
case "$1" in 
start)   
echo -n "Starting Bridge"   
start_bridge   
;; 
stop)   
echo -n "Stopping Bridge"   
stop_bridge   
;; 
restart)   
stop_bridge   
sleep 2   
start_bridge   
;; 
*)   
echo "Usage: $0 {start|stop|restart}" >&2   
exit 1   
;; 
esac  
```

After you think you have it modified to work on your system, put it in the /etc/init.d/ folder then run 

```
sudo chmod +x /etc/init.d/filename
sudo update-rc.d filename defaults
```

That should make it start when you boot up.

---

### Post by KitChy on 2007-06-23
Thanks for the script, it worked great after some editing! 

In case someone has come here searching for a similar solution and doesn't fancy editing the script themselves here's mine, it assumes you are bridging two NIC's (eth0 and eth1) together, and that the bridge has the IP 192.168.0.1

```

#!/bin/bash  
# Create global variables   
# Define Bridge Interface 
br="br0" 
# Define list of TAP interfaces to be bridged, 
# for example tap="tap0 tap1 tap2". 
#tap="tap 0" 
# Define physical ethernet interface to be bridged 
# with TAP interface(s) above. 
eth0="eth0" 
eth1="eth1"
eth_ip="192.168.0.1" 
eth_netmask="255.255.255.0" 
gw=""   

start_bridge () {   
#################################   
# Set up Ethernet bridge on Linux   
# Requires: bridge-utils   
#################################    


brctl addbr $br 
brctl addif $br $eth0
brctl addif $br $eth1  
ifconfig $eth0 0.0.0.0
ifconfig $eth1 0.0.0.0  
ifconfig $br $eth_ip netmask $eth_netmask up   
#route add default gw $gw $br
} 

stop_bridge () {   
####################################   
# Tear Down Ethernet bridge on Linux   
####################################    
ifconfig $br down
brctl delbr $br    

}  
case "$1" in 
start)   
echo -n "Starting Bridge"   
start_bridge   
;; 
stop)   
echo -n "Stopping Bridge"   
stop_bridge   
;; 
restart)   
stop_bridge   
sleep 2   
start_bridge   
;; 
*)   
echo "Usage: $0 {start|stop|restart}" >&2   
exit 1   
;; 
esac

```

---

