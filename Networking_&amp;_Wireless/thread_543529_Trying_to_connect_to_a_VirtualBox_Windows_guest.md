---
title: "Trying to connect to a VirtualBox Windows guest"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by alperenkose on 2007-09-05
Hi all,

I have an absurd problem at least according me
I have a laptop running Ubuntu Feisty Fawn, and I installed VirtualBox on it to run windows Xp pro. I setup the virtual machine to use host networking so i use the following script to connect Windows to the local network.
```
# Set up variables here: 
DESC="Virtualbox IP tunnel" 
VBOXUSER=alp # this should be your username, can use 'root' if you want it for everyone 
PATH=/sbin:/bin:/usr/sbin:/usr/bin 
TUNDEVICE=tap1 # Arbitrary, but must match device used in virtualbox network device setting 
LANDEVICE=eth1 # Adjust to match your WiFi device - may be ath0 etc. 
IPADDR=192.168.1.60 # pick something from an unused subnet 

case "$1" in 
 start|restart|force-reload) 
	echo -n "Starting $DESC: " 
	chown root:vboxusers /dev/net/tun 
	tunctl -t $TUNDEVICE -u $VBOXUSER 
	ip link set $TUNDEVICE up 
	ip addr add $IPADDR dev $TUNDEVICE 
	iptables -t nat -P POSTROUTING DROP 
	iptables -t nat -A POSTROUTING -o $LANDEVICE -j MASQUERADE 
	echo 1 > /proc/sys/net/ipv4/ip_forward 
	echo 1 > /proc/sys/net/ipv4/conf/$TUNDEVICE/proxy_arp 
	parprouted $LANDEVICE $TUNDEVICE 
	;; 
 stop) 
	echo -n "Stopping $DESC: " 
	iptables --table nat -F 
	ip link set $TUNDEVICE down 
	;; 
 *) 
	N=/etc/init.d/$NAME 
	echo "Usage: $N start|stop" >&2 
	exit 1 
	;; 
esac 
exit 0
```
But of course that is not enough, I assigned a static ip to Windows which is "192.168.1.61" .
And now I am able to connect to internet and can access to other computers on LAN in Windows. But the problem is I can NOT access Windows from other computers and i can not ping "192.168.1.61". It says:
> ping: sendmsg: Operation not permitted
So I am not able to connect to Windows through rdp with the following command, after waiting for some it ends up with connection timed out!
```
alp@alp-laptop:~/Desktop$ rdesktop -rsound:remote -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Shell\WinShellEx\WinShellEx.exe" -c "c:\seamlessrdp" 192.168.1.61:3389 -u "remoteUser" -p password -N
Autoselected keyboard map en-us
ERROR: connect: Connection timed out
```
I also tried to connect 192.168.1.60 using rdesktop but it doesn't work either!
But I can ping 192.168.1.60 from other computers...
So Can anyone help me?... I am desperate... :confused: 
Please...

---

### Post by alperenkose on 2007-09-05
Please, doesn't anyone has an IDEA at least???
](*,)

---

