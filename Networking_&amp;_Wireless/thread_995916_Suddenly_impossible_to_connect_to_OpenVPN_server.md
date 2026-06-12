---
title: "Suddenly impossible to connect to OpenVPN server"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by primaxx on 2008-11-28
Hello forum,
I desperatly need some help now, after googling the web the whole day, without even being close to find a solution.

I have Ubuntu 8.10 running with the OpenVPN server (bridged), and everything ran smoothly for weeks, until suddenly nobody could connect anymore from last night.

The clients (XP/Vista) get's the TLS handshake timeout, while the server (constantly) reports```
Fri Nov 28 15:55:01 2008 Authenticate/Decrypt packet error: HMAC authentication failed
Fri Nov 28 15:55:01 2008 TLS Error: incoming packet authentication failed from xxx.xxx.xxx:(random portnmbr)
```

I found suggestions about this being an issue with the ta.key-file, but I have regenerated it (and also the rest of the keys and certificates) and redistributed them to the clients without being able to solve the problem.

My server.conf looks like this:```

port 1194
proto udp

dev tap0

ca /etc/openvpn/examples/easy-rsa/2.0/keys/ca.crt
cert /etc/openvpn/examples/easy-rsa/2.0/keys/server.crt
key /etc/openvpn/examples/easy-rsa/2.0/keys/server.key
 
dh /etc/openvpn/examples/easy-rsa/2.0/keys/dh1024.pem

ifconfig-pool-persist ipp.txt

server-bridge 192.168.200.200 255.255.255.0 192.168.200.210 192.168.200.255

client-to-client

keepalive 10 120

tls-auth ta.key 0

cipher AES-128-CBC   # AES
comp-lzo

persist-key
persist-tun

status openvpn-status.log

verb 3

# Forces client to have a linux account in order to connect
plugin /usr/lib/openvpn/openvpn-auth-pam.so login
```
Here is an example of one of my clients *.ovpn:```
client 
dev tap 
proto udp 
# change this to your server's address 
remote xxx.xxx.xxx 1194 
resolv-retry infinite 
nobind
persist-key 
persist-tun 
# Point the key and crt files to  
# the ones for this user 
tls-client
ca ca.crt 
cert someone.crt 
key someone.key 
#ensure that we are talking to a server 
ns-cert-type server
#confirm we are talking to the correct server 
tls-auth ta.key 1
# Select a cryptographic cipher. 
# If the cipher option is used on the server 
# then you must also specify it here. 
cipher AES-128-CBC 
# Enable compression on the VPN link. 
comp-lzo 
# enable user/pass authentication
auth-user-pass
```

If anyone has any idea of what my problems are, please let me know! (I really appreciate the help!)

Primaxx :confused: (Please forgive my lousy English...)

---

### Post by primaxx on 2008-11-29
*Bump*

---

### Post by jcoddington on 2008-12-08
Did you update your openvpn server?  I had the same problem when I updated my 8.04 server.  I even tried to take out TLS authentication on both the server and client but it didn't work.  I was planning on upgrading to 8.10 anyway so I just started over.

---

