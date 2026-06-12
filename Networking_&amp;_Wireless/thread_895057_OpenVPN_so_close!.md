---
title: "OpenVPN so close!"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by renegadeandy on 2008-08-19
Hey!

I am happy as I have finally nearlly setup an openvpn server on my ubuntu box in my house over ssh, and am trying to connect to it from my halls in university.

I have added the line to allow me to route all traffic on my windows machine @ uni through the vpn to the server.conf file, and added the following line to tell the iptables to then forward all this traffic to eth0:

```

iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE

```

The guide i followed was Routing all local traffic on : [http://openvpn.net/index.php/documentation/howto.html](http://openvpn.net/index.php/documentation/howto.html)

Anyways, when i connect - It connects successfully, however the ssh window which i have open which is displaying the unbuntu server side output on it shows the following error, a lot:

Wed Aug 20 01:45:15 2008 valleyattack.gam_e.host/194.66.200.1:51818 MULTI: bad source address from client [172.29.14.58], packet dropped

172.29.14.58 is the ip issued from my temporary residence - my ip for vpn is 10.8.0.6 and the tunl interface on the server is 10.8.0.1

It seems that my windows box configuration still is not right - what do i need to do in order for it to work!

I am sure this is why my vpn is not wrking - and why i am not getting any packets back from the server of the vpn! Why would this be happening? Could the uni be blocking the incoming traffic on that port?? How would I change the port, i specified it to be udp 1863 which allows the connection to take place but where else would i change anything to make this work!!!!!:confused:

Please help!

Andy

---

### Post by renegadeandy on 2008-08-20
Anybody got any support for me|?

---

### Post by renegadeandy on 2008-08-20
so has nobody got any help!?

---

### Post by renegadeandy on 2008-08-21
<bump> Need help!?

---

### Post by dmizer on 2008-08-21
On your Ubuntu machine, what is the output of:
```
cat /proc/sys/net/ipv4/ip_forward
```

If the output is 0, please run this command:
```
echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
```

Don't know anything about setting up windows for ssh vpn.

---

### Post by renegadeandy on 2008-08-21
Hey!

Right, the output was 0;

it now outputs 1.

Shall i try again?!

---

### Post by renegadeandy on 2008-08-21
Ok well i did try it again, the result was the same. I Can connect fine - and I can ping the tunl interface on the server .

On the windows client, it gets :

ip = 10.8.0.10
and claims the gateway of the tun adapter to be = 10.8.0.9

shoouldnt that be 10.8.0.1 for the tun adapater on the ubuntu box?

As before the following error is reported millions of times on the ssh debug output for the server :

Thu Aug 21 11:37:23 2008 valleyattack_hgame-host.org/195.212.29.83:56828 MULTI: bad source address from client [9.20.224.74], packet dropped

Thanks for your continued support!

---

### Post by dmizer on 2008-08-21
Have you seen this? [https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

Also, have you enabled the root account on your Ubuntu server?

---

### Post by renegadeandy on 2008-08-21
i dont thikn i have enabled the root account. how do i do this!?

The ssh vpn could be useful although i have not really looked into it - would prefer to get this working!

---

### Post by dmizer on 2008-08-21
Perhaps this will help then: [http://gentoo-wiki.com/HOWTO_OpenVPN_Linux_Server_Windows_Client](http://gentoo-wiki.com/HOWTO_OpenVPN_Linux_Server_Windows_Client)

---

### Post by renegadeandy on 2008-08-21
hmm, ive looked through it - It covers all of what I have done = but not solve the problem!?

Thanks for your continued support, hope i can get this working soon!

---

### Post by renegadeandy on 2008-08-21
anybody!?!?!

---

### Post by SpaceTeddy on 2008-08-22
Ok - restart. I am not sure i entirely understand your setup. Can you please explain how the machines are connected to each other, what subnets they have and can you post your server config and a sample client config. I'd also like it know what access you want from where and if you have working dns server internally that need to be addressed for internal name resolution. 
From the looks of it, you are missing a routing entry at your default gateway of your internal network, or your masquerading is wrong - both are easy errors to fix, but since i do know nothing of you setup i cannot help... so please provide the requested info.

hope we can figure this out :)

---

### Post by renegadeandy on 2008-08-22
I did it!

Im not sure what fix made it work, couldve been ip forwarding, but i think i was missing one line with deleting old routes in the client side config!

Now all my traffic goes through the vpn awesome!

---

### Post by sickanimations on 2008-10-15
Please, please tell mee what the solution was... I've got a similar problem.

Previously I had OpenVPN working perfectly from a WinXP server. I transferred the .conf and updated IPs, static routes, etc. 

OpenVPN Clients can connect to the server but can't access the internet or hosts on the server subnet. :(

Trying that ip_forward thing now. Will report back :)

Cheers.

[UPDATE]

Yes! It's ip_forward.

For one reason or another OpenVPN have neglected it in their how-to guide, even though it's EXTREMELY IMPORTANT! Not only for gateway functionality but even for cross-subnet access. 

Anyway, I used
**sysctl net.ipv4.ip_forward**
to check whether ip_forward was enabled. It wasn't.

then
**sysctl -w net.ipv4.ip_forward=1**
To enable it.

I had to reboot - probably could have just restarted networkmanager daemon.

SWEET JESUS IT WORKS!

---

### Post by DrJohn999 on 2008-10-16
Dell Lat D-610, Hardy, wireless, NetworkManager, OpenVPN: same problem -- can connect to OpenVPN server (Hardy), connect to LAN machines, get to the web from within a remote session, etc. but when OpenVPN is active cannot connect to web from the client laptop. With Firefox trying to connect, as soon as I disconnect OpenVPN it starts to receive data from the web.

Enabling IPV4.ip_forward does not work for me, and ip_forward resets to 0 on reboot anyway.

The laptop is dual boot with WinXP Pro, and this problem does not exist running WinXP and OpenVPN client.

OpenVPN Client is managed by NetworkManager. Gconf-editor shows the following values under /system/networking/vpn_connections/CSI@32@OpenVPN:

```

connection type x509
dev tun
remote <my-openvpn-server>
port 1194
proto udp
servercert-insecure no
ca <path-to-my-ca>
cert <path-to-my-cert>
key <path-to-my-key>
comp-lzo yes
shared-key
local-ip
remote-ip
username
ta <path-to-ta>
ta-dir 1

```

The WinXP client.ovpn file settings are:
```

client

dev tun

proto udp

remote <my-openvpn-server> 1194

resolv-retry infinite

nobind

persist-key

persist-tun

ca ../keys/ca.crt

cert ../keys/cert.crt

key ../keys/key.key

ns-cert-type server

tls-auth ../keys/ta.key 1

comp-lzo

verb 3

mute 20

```

Any ideas on how to enable internet access while connected thru OpenVPN on this Hardy machine?

Thanks,

DJ

---

### Post by kevdog on 2008-10-21
Can you post the server config files?

---

### Post by SpaceTeddy on 2008-10-21
network manager is stupid when it comes to openvpn. It automaticially sets the "redirect-gateway" on the client side this sending EVERYTHING over the VPN. If you vpn is not configures for that (i.e. you do not push the correct DNS servers, you do not have ip_forwarding enabled on your server and may need NAT for the packets to find their way back) it is normal that your internet just dies. 

What i suggest is that you connect manually to the vpn server to debug the problem without using network manager. Once you manager to get it working via the command line, you can go ahead and try again with nm (with better understanding what should be happening and what nm is actually doing).

to connect manually you will need to call the client.conf via openvpn - this should get your started:
```
sudo openvpn --config $PATH_TO_CONF_FILE$
```
after that is done, check your network configuration and see if the internet still works and if access to the VPN works as needed.

Sorry for being short and cryptic - but i hope it helps anyway :)

---

### Post by DrJohn999 on 2008-10-21
The above manual connection does work -- the laptop finds the internet; I can ssh to the server.

Here is the server config:
```

;local a.b.c.d
port 1194
proto udp
dev tun
;dev-node MyTap
ca /etc/openvpn/keys/ca.crt
cert /etc/openvpn/keys/server.crt
key /etc/openvpn/keys/server.key  # This file should be kept secret
dh /etc/openvpn/keys/dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
;server-bridge 10.8.0.4 255.255.255.0 10.8.0.50 10.8.0.100
#server's local subnets
push "route 192.168.2.0 255.255.255.0"
push "route 192.168.3.0 255.255.255.0"
;push "redirect-gateway"
;push "dhcp-option DNS 10.8.0.1"
;push "dhcp-option WINS 10.8.0.1"
;client-to-client
;duplicate-cn
keepalive 10 120
tls-auth /etc/openvpn/keys/ta.key 0 # This file is secret
;cipher BF-CBC        # Blowfish (default)
;cipher AES-128-CBC   # AES
;cipher DES-EDE3-CBC  # Triple-DES
comp-lzo
max-clients 4
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
log openvpn.log
verb 3
mute 20

```

and here is the laptop config used for the manual invoke:
```

client
dev tun
proto udp
resolv-retry infinite
nobind
remote <myserversfqdn> 1194
user nobody
group nobody
persist-key
persist-tun
ca ./keys/ca.crt
cert ./keys/dell-d610.crt
key ./keys/dell-d610.key
ns-cert-type server
tls-auth ./keys/ta.key 1
comp-lzo
verb 3
mute 20

```

When using NM, 'push redirect-gateway' at the server side does nothing. So, the question becomes how to make NetManager not force the gateway to redirect.

-- DJ

---

### Post by SpaceTeddy on 2008-10-21
good - in this case, you will need to go into the nm configration of your VPN and choose the Option TAB, there, check "only use VPN connection for these Addresses" and put in what ever you would normally push from the server.
in your case (according to your server conf) this should be:
> 192.168.2.0/24 192.168.3.0/24
then save and see if the vpn works correctly...

As i said, nm always sets the redirect-gateway by itself without listening to what openvpn acctually wants to do. So you have to reverse configure it (i.e. tell it NOT to set the redirect-gateway) this way. Please note that if you change the subnets that get pushed to your clients you also need to modify your nm configuration, as it will NOT pick up any pushed routes (silly, really... but that's how it works)

hope it works now :)

---

### Post by DrJohn999 on 2008-10-21
Perfect! Now it works. 

Thanks, SpaceTeddy and kevdog.

-- DJ

---

