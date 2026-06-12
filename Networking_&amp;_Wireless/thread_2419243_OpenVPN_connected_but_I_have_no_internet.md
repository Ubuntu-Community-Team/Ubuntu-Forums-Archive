---
title: "OpenVPN connected but I have no internet"
date: 2019-05-18
forum: Networking &amp; Wireless
---

### Post by luks911 on 2019-05-18
Hello,

I'm sorry for my rustic English... I don't know much about networks and I couldn't find a solution form my problem: I have to connect to an OpenVPN server to work from my home. The company gave me the server configuration, keys and certificates and it works. I can connect to my office network throw the VPN, but when it is connected I can't browse on the internet. Looking for a solution, I read that I have to check the option "Use this connection only for resources on its network" in the IPv4 tab of the VPN configuration in network-manager. When I do this, I can browse on the internet but I can't connect to my company's network :(

Also, I installed a OpenVPN client in my android phone which allow me connect to the company network and access to the internet at the same time. So the problem might be in some configuration of the client in my notebook.

Any help will be grateful and please let me know if you need more information.

Thanks in advance

---

### Post by Okeur on 2019-05-18
Hello,

Could you post the openvpn file (without of course private info...) ?
Also give the output of route -n when you are both connected and not connected to the VPN

---

### Post by luks911 on 2019-05-18
Hello,

This is the ovpn file, I replace here the server address, which in the file is the same that the name of the folder containing ca.crt, user.crt, user.key and security.key.
```

client
remote server_address 52728
dev tun
comp-lzo
nobind
auth-nocache
script-security 2
ca folder/ca.crt
cert folder/user.crt
key folder/user.key
tls-auth folder/security.key 1
ns-cert-type server
persist-key
persist-tun
resolv-retry infinite
verb 3
```

and route -n not connected to the VPN
```

 ~ &#57520; route -n
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp4s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp4s0
 ~ &#57520; 

```

route -n connected to the VPN
```

 ~ &#57520; route -n
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
0.0.0.0         172.26.73.206   0.0.0.0         UG    50     0        0 tun0
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp4s0
10.2.3.0        172.26.73.206   255.255.255.0   UG    50     0        0 tun0
10.200.1.0      172.26.73.206   255.255.255.0   UG    50     0        0 tun0
10.201.1.0      172.26.73.206   255.255.255.0   UG    50     0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp4s0
172.26.72.0     172.26.73.206   255.255.248.0   UG    50     0        0 tun0
172.26.73.1     172.26.73.206   255.255.255.255 UGH   50     0        0 tun0
172.26.73.206   0.0.0.0         255.255.255.255 UH    50     0        0 tun0
172.26.112.0    172.26.73.206   255.255.240.0   UG    50     0        0 tun0
172.26.192.0    172.26.73.206   255.255.224.0   UG    50     0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp4s0
192.168.1.1     0.0.0.0         255.255.255.255 UH    600    0        0 wlp4s0
200.47.118.116  172.26.73.206   255.255.255.255 UGH   50     0        0 tun0
200.47.118.194  192.168.1.1     255.255.255.255 UGH   600    0        0 wlp4s0
 ~ &#57520; 

```

and, I don't know if it helps, but route -n with "Use this connection only for resources on its network" checked
```
route -n
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp4s0
10.2.3.0        172.26.73.206   255.255.255.0   UG    50     0        0 tun0
10.200.1.0      172.26.73.206   255.255.255.0   UG    50     0        0 tun0
10.201.1.0      172.26.73.206   255.255.255.0   UG    50     0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp4s0
172.26.72.0     172.26.73.206   255.255.248.0   UG    50     0        0 tun0
172.26.73.1     172.26.73.206   255.255.255.255 UGH   50     0        0 tun0
172.26.73.206   0.0.0.0         255.255.255.255 UH    50     0        0 tun0
172.26.112.0    172.26.73.206   255.255.240.0   UG    50     0        0 tun0
172.26.192.0    172.26.73.206   255.255.224.0   UG    50     0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp4s0
192.168.1.1     0.0.0.0         255.255.255.255 UH    600    0        0 wlp4s0
200.47.118.116  172.26.73.206   255.255.255.255 UGH   50     0        0 tun0
200.47.118.194  192.168.1.1     255.255.255.255 UGH   600    0        0 wlp4s0
 ~ &#57520; 

```

Thanks :-)

---

### Post by luks911 on 2019-05-26
Well, I tried the same vpn in a laptop with Linux Mint, based on 16.04, and with the option "Use this connection only for resources on its network" I can access to the company network and browse the internet at the same time. So, what configuration I should look for and copy or try to imitate to do the same in my Ubuntu 18.10?

---

