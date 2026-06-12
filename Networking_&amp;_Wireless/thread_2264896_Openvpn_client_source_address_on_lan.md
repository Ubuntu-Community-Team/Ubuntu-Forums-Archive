---
title: "Openvpn client source address on lan"
date: 2015-02-11
forum: Networking &amp; Wireless
---

### Post by chris143 on 2015-02-11
I'm wanting my openvpn clients to keep their virtual IP  address  assigned by the openvpn server when connecting to other  resources over  the LAN on the openvpn server's network (As well as the  internet via  the openvpn server's network, the router should see the  virtual address  as the source address so I can handle the traffic  separately from  other LAN devices (force an different ext address))

  Currently when doing this the other devices on the LAN report the   openvpn server's address instead of the virtual address they're   assigned.
  
I.E.

  ```

Server 172.19.195.18
Client 172.19.197.6
FTP 172.19.195.13

```

If I'm connected to openvpn as the client (172.19.197.6) and I make a  connection to the FTP @ 172.19.195.13 it says I'm connecting from  172.19.195.18(Openvpn Server) I want the client to keep it's address (  172.19.197.6, and I want the FTP server/device to report the client is  connecting from there rather then the Openvpn server).
  
I've looked into [Routed Lans]("https://community.openvpn.net/openvpn/wiki/RoutedLans"),
  And attempted integrating this but it doesn't seem to help in my situation.

  Any advice/direction or help would be greatly appreciated, 
So far I  know that the directive "push redirect-gateway def1" should probably be  removed and I should not be using NAT via iptables to handle the traffic  or at least this is what I think from what I've read now.


  **server configuration**
  ```
dev tun
proto tcp-server
port 1095

ca /etc/openvpn/ca.crt
cert /etc/openvpn/server.crt
key /etc/openvpn/server.key
dh /etc/openvpn/dh1024.pem
tls-auth /etc/openvpn/ta.key 0

client-cert-not-required
username-as-common-name

server 172.19.197.0 255.255.255.0

client-to-client
client-config-dir /etc/openvpn/ccd/


route 172.19.197.0 255.255.255.0
push "route 172.19.197.0 255.255.255.0"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"

push "redirect-gateway def1"

log-append /var/log/openvpn/server.log
tmp-dir /tmp

plugin /usr/local/lib/openvpn/openvpn-otp.so

```  **client configuration**
  ```
remote XXX 1095
ca [inline]
tls-auth [inline] 1

client
dev tun
tls-client
proto tcp-client
route-method exe
route-delay 2
resolv-retry infinite
nobind
persist-key
persist-tun
auth-user-pass
auth-nocache
reneg-sec 0
verb 3

```  **ccd configuration**
  ```
iroute 172.19.197.0 255.255.255.0

```

---

### Post by SeijiSensei on 2015-02-11
If you use NAT, then you will never see the originating address.

Show us the results of the command "route -n" on the various machines with the VPN activated

---

