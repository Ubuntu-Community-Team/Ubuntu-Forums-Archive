---
title: "iptables problem"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by lordpet on 2006-08-14
I recently upgraded from debian to dapper for my home network and everything is fine except for a slight problem with iptables / firestarter.
Things work fine on internet sharing except for the uploading of files via web forms.
I recently found this out developing a form uploader with progress bar and the upload speed starts ok but drops to tiny k per second.

I'm back on debian with my rc.firewall which works fine
> #!/bin/sh
WHITELIST=whitelist.txt
BLACKLIST=blacklist.txt
ALLOWED="20 21 22 25 80 443 10000"
EXT_IFACE=eth0

iptables        -F
for x in `grep -v ^# $WHITELIST | awk '{print $i}'`;do
echo "Allowing $x ..";
iptables -A INPUT -t filter -s $x -j ACCEPT
done
for x in `grep -v ^# $BLACKLIST| awk '{print $i}'`;do
echo "Disallowing $x ..";
iptables -A INPUT -t filter -s $x -j DROP
done
for port in $ALLOWED;do
echo "Accepting port $port ...";
iptables -A INPUT -t filter -p tcp --dport $port -j ACCEPT
done
iptables -A INPUT -t filter -p tcp --syn -j DROP
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o $EXT_IFACE -j MASQUERADE

Any solution would be appreciated. Seems to be the same on any 2.6 kernel
as I tried various distos over the weekend ranging from Redhat - Suse and it effects them all.:confused:

---

