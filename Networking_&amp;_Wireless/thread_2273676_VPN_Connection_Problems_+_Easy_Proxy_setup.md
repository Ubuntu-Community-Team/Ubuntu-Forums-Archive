---
title: "VPN Connection Problems + Easy Proxy setup ?"
date: 2015-04-14
forum: Networking &amp; Wireless
---

### Post by Sbo0Tr on 2015-04-14
So Im in need to setup a FREE Vpn and if I can setup more than one then I would like to do that is well. I've seen the free vpn sites like , VPN Book and VPNME but the setup never seems to work for me. I also was told to try setting up a proxy after setting up my vpn to ensure max security. I haven't found a way to setup a free proxy. Im asking for help with setting up a free proxy and fixing my VPN problems.

```

shadergaming@Shader:~/Desktop$ sudo openvpn vpnme_us1_udp1194.ovpn
Tue Apr 14 16:46:11 2015 OpenVPN 2.3.2 i686-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Dec  1 2014
Enter Auth Username:us_open
Enter Auth Password:
Tue Apr 14 16:46:49 2015 Socket Buffers: R=[163840->131072] S=[163840->131072]
Tue Apr 14 16:46:49 2015 UDPv4 link local: [undef]
Tue Apr 14 16:46:49 2015 UDPv4 link remote: [AF_INET]104.223.1.248:1194
Tue Apr 14 16:47:50 2015 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Tue Apr 14 16:47:50 2015 TLS Error: TLS handshake failed
Tue Apr 14 16:47:50 2015 SIGUSR1[soft,tls-error] received, process restarting
Tue Apr 14 16:47:50 2015 Restart pause, 2 second(s)
Tue Apr 14 16:47:52 2015 Socket Buffers: R=[163840->131072] S=[163840->131072]
Tue Apr 14 16:47:52 2015 UDPv4 link local: [undef]
Tue Apr 14 16:47:52 2015 UDPv4 link remote: [AF_INET]104.223.1.248:1194
Tue Apr 14 16:48:52 2015 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Tue Apr 14 16:48:52 2015 TLS Error: TLS handshake failed
Tue Apr 14 16:48:52 2015 SIGUSR1[soft,tls-error] received, process restarting
Tue Apr 14 16:48:52 2015 Restart pause, 2 second(s)
Tue Apr 14 16:48:54 2015 Socket Buffers: R=[163840->131072] S=[163840->131072]
Tue Apr 14 16:48:54 2015 UDPv4 link local: [undef]
Tue Apr 14 16:48:54 2015 UDPv4 link remote: [AF_INET]104.223.1.248:1194
Tue Apr 14 16:49:54 2015 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Tue Apr 14 16:49:54 2015 TLS Error: TLS handshake failed
Tue Apr 14 16:49:54 2015 SIGUSR1[soft,tls-error] received, process restarting
Tue Apr 14 16:49:54 2015 Restart pause, 2 second(s)
Tue Apr 14 16:49:56 2015 Socket Buffers: R=[163840->131072] S=[163840->131072]
Tue Apr 14 16:49:56 2015 UDPv4 link local: [undef]
Tue Apr 14 16:49:56 2015 UDPv4 link remote: [AF_INET]104.223.1.248:1194 
```

That is whats happening currently when trying to run the cmd "sudo openvpn filename.opvn" It has errors. I want to be able to maybe have a .sh file that will start the vpn when my computer boots. Thank You guys!


I haven't tried setting up a proxy so any link to a tutorial would help. Thank you.

---

### Post by michi1983 on 2015-04-15
Well, it looks like that this is an issue on the server side. In line 7 of your code it says that you get an IP address from the server which means you can communicate with the server. But for some reason it refuses the TLS handshake which means that somewhere something is blocked, maybe from a firewall. 
It's described [here ]("http://openvpn.net/index.php/open-source/faq/79-client/253-tls-error-tls-key-negotiation-failed-to-occur-within-60-seconds-check-your-network-connectivity.html")as well.

Can you please type this in your terminal and post the output here in your next comment:
```
sudo ufw status 
```
```
sudo iptables -L
```

---

### Post by Sbo0Tr on 2015-04-15
shadergaming@Shader:~$ sudo ufw status
[sudo] password for shadergaming: 
Status: inactive
shadergaming@Shader:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
shadergaming@Shader:~$

---

### Post by michi1983 on 2015-04-15
okay so the problem is not on your side I guess.
do you have a way to check if the connection works with another client, maybe windows or osx to see if its ubuntu related?

---

### Post by Sbo0Tr on 2015-04-15
I only have access to Ubuntu , lol thats my problem. Will a proxy be able to mask my IP as well ?

---

### Post by Sbo0Tr on 2015-04-15
Ok so I tried vpnbook , and it seems to be working. Is there a way I can make my computer start the vpn whenever I boot up ?

Maybe .sh file ? I don't know how to do this but yeah

The Cmd is:
 - cd Desktop
 - cd vpn
 - sudo openvpn vpnbook-euro1-tcp80.ovpn

---

### Post by michi1983 on 2015-04-15
sure, create a file e.g. openvpn with the content:
```

#!/bin/sh
sudo openvpn /home/$username/Desktop/vpnbook-euro1-tcp80.ovpn

```

Save it in /etc/init.d/ and make it executable with:
```
sudo chmod +x /etc/init.d/openvpn
```

If it doesn't start make a symlink:
```

sudo ln -s /etc/init.d/openvpn /etc/rc.d/

```

---

### Post by Sbo0Tr on 2015-04-15
With this
#!/bin/sh
sudo openvpn /home/$username/Desktop/vpnbook-euro1-tcp80.ovpn
password #I can add tht there right ? The password

Then save it as like myvpn.sh and it will run on startup ?

---

### Post by michi1983 on 2015-04-15
sorry my fault, forget the sudo. just your normal command without sudo. and then change permissions with
```
sudo chmod 755 /etc/init.d/openvpn
```

no need for .sh extension

---

### Post by Sbo0Tr on 2015-04-15
Im sorry , Im a bit lost!

---

### Post by michi1983 on 2015-04-15
create a file and name it e.g. openvpn with the content
```

#!/bin/sh
openvpn /home/$username/Desktop/vpn/vpnbook-euro1-tcp80.ovpn

```
Save it in /etc/init.d/ and make it executable with:
```

sudo chmod +x /etc/init.d/openvpn

```
If it doesn't start make a symlink:
```

sudo ln -s /etc/init.d/openvpn /etc/rc.d/

```

---

