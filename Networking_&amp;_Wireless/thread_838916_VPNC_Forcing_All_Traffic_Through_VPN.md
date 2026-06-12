---
title: "VPNC Forcing All Traffic Through VPN?"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by RROY on 2008-06-23
I am having an issue when I connect to my work Cisco VPN through VPNC.

The problem is when the VPN is up, all network traffic seems to get routed through the VPN, and I lose most internet connectivity, because the VPN is setup for internal work network access.

Is there something I can do to tell VPNC to only use the routes that the VPN is supposed to manage?  If so, how do I know which routes the VPN is managing?

---

### Post by SpaceTeddy on 2008-06-24
as far as i am informed about the Cisco VPN, it is build upon IPSEC, which will always direct you entirely over the VPN once you are connected. 
Afaik, there is no way (unless you wish you modify your routes after the connection has come up) to stop this. One of the reasons i tried this one, and then left it alone. OpenVPN is way more flexible and can do partial redirects.

So, i guess the answer to your question is a definitely maybe. You'll need to modify your router accordingly - manually. If you can give me the output of 
```
route -n
```
once when you are connected and once when you are not, i might be able to to see something. But don't count on it... :(

Hope this helps :)

---

### Post by RROY on 2008-06-24
Here are the results you asked for:

With VPN On:```

~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.xxx.xxx 192.168.0.1     255.255.255.255 UGH   0      0        0 ath0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 tun0
```
The xxx.xxx.xxx.xxx is my VPN Gateway.


With VPN Off:```
~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 ath0
```


It appears to be removing the Gateway and Gateway Flag from the 0.0.0.0 entry.  Is there a way to resolve this?

---

### Post by SpaceTeddy on 2008-06-24
ok, that is a full redirect of everything... here are the commands you can try to force the redirect to be dropped while the vpn stays up.

```
sudo route del -net 0.0.0.0 netmask 0.0.0.0
sudo route add default gw 192.168.0.1
```
these will take out the vpn redirection... now, what you need is forward the work network through the vpn. For that you need to know what networks are inside your work. This can be one or multiple. If you are running a rather "normal" internal network, i think these routes should be sufficient:
```
sudo route add -net 192.168.0.0 netmask 255.255.0.0 dev tun0
sudo route add -net 10.0.0.0 netmask 255.0.0.0 dev tun0
```

tell me how it works :)

---

### Post by RROY on 2008-06-24
Tried the first step, still no internet:

```

~$ sudo route del -net 0.0.0.0 netmask 0.0.0.0
~$ sudo route add default gw 192.168.0.1
~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
x.x.x.x         192.168.0.1     255.255.255.255 UGH   0      0        0 ath0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 ath0
~$ ping google.com
ping: unknown host google.com

```

I could still connect to work's network...

---

### Post by SpaceTeddy on 2008-06-24
did you check your /etc/resolv.conf if your nameserver was still reachable ? it could be that vpnc rewrites the dns to match it with the ones from work - which won't work anymore if you delete the standard route :)

i'll need sleep now, so i won't answer for the next 10 hours or so

cheers :)

---

### Post by RROY on 2008-06-24
My nameserver is my gateway 192.168.0.1 and is still reachable.

I tried to ping by IP...no response.

Tried a tracert and it never got any responses either...

I loaded the resolv.conf after I connected to the VPN, and Network Manager changed my nameservers automatically...removing my default one...

Thanks for all the help...I'm gonna install the Cisco client, VPNC is being a pain...it was nice having it integrated into the network manager though...oh well...

---

### Post by RROY on 2008-06-24
I just found that if I use the shell vpnc-connect command everything works fine.

It adds an entire proper routing table and leaves me able to connect to the internet.

Now to figure out why the network manager vpnc doesn't run vpnc-connect properly...

---

### Post by RROY on 2008-06-24
Found out what the problem is:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/207506](https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/207506)

It looks like the Network-Manager-VPNC plugin uses it's own script...and it's fubar'd when it comes to managing routing tables it seems...

I've switched to kvpnc as a tray item...too bad though...network manager would have been awesome if only it's vpnc plugin actually worked.

---

### Post by ixxalnxxi on 2013-04-04
2013 and this post helped me after a month of thinking ovpn had a bug.

---

### Post by thijsvanulden on 2014-01-03
> **ixxalnxxi said:**
> 2013 and this post helped me after a month of thinking ovpn had a bug.

And again, many months later, this is still a problem.

---

