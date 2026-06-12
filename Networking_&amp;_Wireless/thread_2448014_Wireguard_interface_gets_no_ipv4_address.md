---
title: "Wireguard interface gets no ipv4 address"
date: 2020-07-30
forum: Networking &amp; Wireless
---

### Post by cpunk on 2020-07-30
Wireguard has been working fine on this Kubuntu 20.04 install for a while. Now for some reason when I try to bring up a new interface with wg-quick, it gets no IP address assigned. Is anyone else seeing this when trying to create a new Wireguard interface?

Here's the ifconfig after it's brought up:
```
[FONT=monospace][COLOR=#000000]wg1: flags=209<UP,POINTOPOINT,RUNNING,NOARP>  mtu 1420[/COLOR]
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 1000  (UNSPEC)
        RX packets 3  bytes 156 (156.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 25  bytes 22144 (22.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/FONT]
```
There should be an IPv4 address, but there's none. 

wg show output:
```
[FONT=monospace][COLOR=#54FF54]**interface**[/COLOR][COLOR=#000000]: [/COLOR][COLOR=#18B218]wg0[/COLOR]
  [COLOR=#000000]**public key**[/COLOR][COLOR=#000000]: <redacted> [/COLOR]
  [COLOR=#000000]**private key**[/COLOR][COLOR=#000000]: (hidden)[/COLOR]
  [COLOR=#000000]**listening port**[/COLOR][COLOR=#000000]: 44429[/COLOR]
  [COLOR=#000000]**fwmark**[/COLOR][COLOR=#000000]: 0xca6c[/COLOR]

[COLOR=#FFFF54]**peer**[/COLOR][COLOR=#000000]: <redacted>[/COLOR]
  [COLOR=#000000]**endpoint**[/COLOR][COLOR=#000000]: 192.168.11.88:51820[/COLOR]
  [COLOR=#000000]**allowed ips**[/COLOR][COLOR=#000000]: 0.0.0.0[/COLOR][COLOR=#18B2B2]/[/COLOR][COLOR=#000000]0, ::[/COLOR][COLOR=#18B2B2]/[/COLOR][COLOR=#000000]0[/COLOR]
  [COLOR=#000000]**latest handshake**[/COLOR][COLOR=#000000]: 26 [/COLOR][COLOR=#18B2B2]seconds[/COLOR][COLOR=#000000] ago[/COLOR]
  [COLOR=#000000]**transfer**[/COLOR][COLOR=#000000]: 156 [/COLOR][COLOR=#18B2B2]B[/COLOR][COLOR=#000000] received, 21.62 [/COLOR][COLOR=#18B2B2]KiB[/COLOR][COLOR=#000000] sent[/COLOR][/FONT]
```

Here's the config file:
```
[FONT=monospace][COLOR=#000000][Interface][/COLOR]
Address = 10.0.0.2/32
PrivateKey = <redacted> 
DNS = 8.8.8.8

[Peer]
PublicKey = <redacted> 
AllowedIPs = 0.0.0.0/0,::0/0
Endpoint = 192.168.11.88:51820[/FONT]
```

Right now I'm doing this just to test performance on a router that's acting as wg server. So I have it on a private network. There is some L2 traffic moving since I can see the handshake on the wg server and a few bytes moving. 

I had another interface on this PC that was set up earlier, associated with a different endpoint, and it was still functioning fine. I could bring it up with "wg-quick up wg0" and it has the IP assigned and connectivity is working. 

Thinking it was just a problem with interface creation I've tried the following:

[LIST=1]
[*]Create the interface through the connections GUI in system settings. Same behavior. The IP is visible in the output of "[COLOR=#000000]nmcli -s c show wg1" and in /etc/NetworkManager/system-connections/wg1.nmconnection. Interestingly, the interface gets a link-local ipv6 address in this config, since ipv6 address mode is required (and disabled is not available in the GUI). Setting it to ignore gives a link-local that does respond to a ping. Still no ipv4. [/COLOR]
[*][COLOR=#000000]Create the interface through nmcli. Same as above, the IP is in the stored configuration. [/COLOR]
[*][COLOR=#000000]Next [/COLOR]I removed all the Wireguard interfaces (including the working one), restarted, and then tried to set up only the previously-working interface wg0, with the same config file that was used previously (a 3 or so of months ago). That interface now has the same problem.
[*]Thinking it could be caused by an update, I reverted the wireguard and wireguard-tools to the 20.04 release versions ([COLOR=#000000]apt-get install wireguard=1.0.20200319-1ubuntu1 wireguard-tools=1.0.20200319-1ubuntu1). Then I tried to wg-quick up that previously-working wg0.conf file. Same behavior. I upgraded back to current. [/COLOR]
[/LIST]
[COLOR=#000000]
Any ideas about what might be happening? Can anyone else reproduce this? 
Thanks for any ideas![/COLOR]

---

### Post by cpunk on 2020-08-03
FWIW I dropped back to release 20.04, then applied updates in batches, restarting and testing along the way. The problem has not recurred.

---

