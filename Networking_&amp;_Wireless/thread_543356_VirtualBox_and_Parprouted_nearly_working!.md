---
title: "VirtualBox and Parprouted nearly working!"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by Tangee on 2007-09-05
Hey,

I have been trying to get networking working on VirtualBox and came across a thread that told me to use parprouted, so I did!

And lo and behold I can ping the network...kind of...

I can actually only ping the IP addresses of my host's eth1 and tap1 interfaces, but its a start...

I have set up the eth0 interface on the guest machine with a static IP, and added a route default gw to my router, but I cannot ping anything other than my host interfaces...not even the router.

any suggestions?

thanks in advance...

---

### Post by Tangee on 2007-09-05
on a second note (and less important than the first for those who like to prioritise), if I change vbox to use nat instead I get a 10. . .  address, and cannot ping internet IP's or addresses, but can seemingly apt-get from repos...

i am somewhat confuzzled!

---

### Post by Tangee on 2007-09-06
*shameless bump*

---

### Post by dominicedmonds on 2007-11-06
***Successful wireless networking with VirtualBox***
Hmmm, I feel slightly guilty :-s at not having shared this work (mostly done by my pal CPL)

Dell Latitude D810
Kubuntu Feisty Fawn
VirtualBox 1.5.0
parprouted 0.63-2


I have a local script vboxnetp which I have annotated:


```
#!/bin/sh

# Start/stop arp-based proxying to a tuntap network device
# Required for VirtualBox guests that use HIN over wireless
# (The oft-touted bridging route works over host's wired ethernet
# but won't work if host uses a wireless nic. (Something to do with
# multiple MAC addresses?)

# TODO: Handle multiple tapX interfaces, for multiple VMs?
#       Merge with bridging script and give choice of method? (auto-detect wlan...?)
#       Allow passing of NETDEV via command line, overriding hard-coded default?

TAPDEV=tap0             # Tap device, for virtual NIC
NETDEV=eth1             # Network device for host's connection to LAN and Internet (wlan0, eth0 etc.)
TAPUSER=dominic         # User as whom VBox will be running (we really should not need this???)
TUNPROG=/usr/sbin/tunctl
PARPPROG=/usr/local/sbin/parprouted
DEBUG=-d
 # -d turns on parprouted debug output to terminal (i.e. runs in foreground)

#==========================
case "$1" in
start)

# Remove existing
echo Unlinking any existing $TAPDEV ... ; /sbin/ip link set $TAPDEV down
echo Deleting any existing $TAPDEV ...  ; $TUNPROG -d $TAPDEV

# Create new (does -u userid matter?)
echo Creating new $TAPDEV ... ; $TUNPROG -u $TAPUSER -t $TAPDEV

echo Linking new $TAPDEV ... ; /sbin/ip link set $TAPDEV up # Enable the i/face
echo sleep 1 ... ; sleep 1 # Fudge?
echo adding $TAPDEV 172.16... ; /sbin/ip addr add 172.16.16.16/32 dev $TAPDEV  # Looks odd but address is arbitrary, so this works

#/sbin/ip addr add 192.168.1.18/32 dev $TAPDEV  # In an effort to get dhcrelay to relay anything....

# Change permissions on /dev/net/tun (660 and chown or chgrp is better??)
# Why is this necessary? Why does the -u switch above not suffice?
# AND WHY DOES IT SOMETIMES NOT WORK???? (Timing?? Added a few second sleep to test this theory)
echo sleep 3 ...  ; sleep 3
echo chmod 0666 /dev/net/tun ; chmod 0666 /dev/net/tun # FIXME! Ugh, we should not have to create this world read/writable

#echo 1 >/proc/sys/net/ipv4/conf/tap0/proxy_arp # Investigate -- could be useful but does not work as expected
echo Enabling IPv4 forwarding ...  ; echo 1 >/proc/sys/net/ipv4/ip_forward                 # Enable ipv4 packet forwarding on the host
# Start parprouted (arp-based proxy)
echo sleep 3 ... ; sleep 3
echo Setting up wireless bridge with cmd $PARPPROG $DEBUG $NETDEV $TAPDEV ...
$PARPPROG $DEBUG $NETDEV $TAPDEV

ifconfig # Feedback for user
route -n
;;

#==========================
stop)
killall parprouted
/sbin/ip link set $TAPDEV down
$TUNPROG -d $TAPDEV
;;

#==========================
status)
if ps ax | grep "parprouted" | grep -qv "grep"; then
        echo "parprouted is running..." ;
else
        echo "parprouted is NOT running" ;
fi
;;


*)
        echo -e "USAGE: $0 {start|stop:status}\nEdit script to specify host LAN interface, user, tap device etc."
        echo
        ;;
esac

exit 0
```

***Host and Guest IP Addresses***
I am running Windows XP as a guest with a fixed IP address on the same subnet as the Host. I.e.: my Linux Gutsy Gibbon host has an IP of 192.168.1.145 on eth1 (the wireless interface) and the VirtualBox Windows XP Guest has an IP of 192.168.1.146 on its virtual NIC.

And this all works fine and big thanks to help from my pal CPL.

---

### Post by Wutzl on 2007-11-08
Hi,

thanks so much for your work - I've been trying for weeks now to get my virtualbox online through my wifi card - now there's new hope!

I have one question though - wifi users tend to be on different networks all the time - so the static IP setup isn't really what most people will need.
I can't really follow what your script is doing (and thus don't know how to go about adjusting it) - is there any chance you could adjust it to use DHCP from the wifi router instead of requiring a fixed IP setup?

Thanks,

Chris

---

### Post by dominicedmonds on 2007-11-08
Hi Wutzl
DHCP would be great wouldn't it? But that is more work for another day. I am sure that it would be possible given that we have come this far. It is a bore to have to modify both IP addresses when you are 'on the road'; the workaround is most proobably in tweaking the VirtualBox HIN dialog. I will look at it some time.
Dominic

---

### Post by LazarusHC on 2007-11-11
I've got a wireless network, and this isn't working for me.  I really have no idea why.  I'm not getting nay errors, and everything seems to go smoothly, but when I boot up the guest machine it simply doesn't connect.  

Any help would be appreciated!

---

### Post by LazarusHC on 2007-11-12
Never mind.  I got it working.  However... I'm not really sure how.  I didn't change anything; I simply woke up today and decided to try it one more time before I went looking again and... it just worked.   Bizare...

---

