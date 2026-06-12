---
title: "I'm having a problem with nftables and Glassfish"
date: 2017-12-17
forum: Networking &amp; Wireless
---

### Post by sfigueroab on 2017-12-17
Hi everyone, it's my first time posting here, I will admit that I lurked through the forum for meny years looking for answers but this is the first time that Google or this forum doesn't have an answer for this problem.

I have a Ubuntu server 16.04 as a home / development server.
IPtables is compleatly uninstalled and replaced with nftables, this is my configuration:

```


table ip filter {
        chain input {
                type filter hook input priority 0; policy drop;




        #       Acepta loop
                iif lo accept


        #       Trafico establecido-orginado
                ct state established,related accept


        #       Entrante nuevo
                tcp dport {80, 443, 8443, 61666} ct state new accept
                udp dport {61666} ct state new accept


        #       Solo desde LAN
                tcp dport {3500, 139, 445,  8200, 9091} meta iif enp1s0 ct state new accept
                udp dport {67, 137, 138, 1900} meta iif enp1s0 ct state new accept


        #       Glassfish
                tcp dport {4848, 8080, 8181, 8686, 7676, 3700, 3820, 3920} accept


        #       Ping desde LAN
                ip protocol icmp meta iif enp1s0 accept


        }
        chain output {
                type filter hook output priority 0; policy drop;


        #       Loopback
                oif lo accept


        #       Permite trafico saliente ya establecido o relacionado
                ct state established,related accept


        #       PING
                ip protocol icmp accept


        #       Torrent
                udp sport {61666} ct state new accept


        #       DHCP-WAN
                udp sport {68} udp dport {67} ct state new meta oif enx000ec6d9d549 accept


        #       DNS-WAN
                udp dport {53} ct state new meta oif enx000ec6d9d549 accept


        #       NTP-WAN
                udp dport {123} ct state new meta oif enx000ec6d9d549 accept



        #       Navegacion por WAN
                tcp dport {80,443} ct state new meta oif enx000ec6d9d549 accept


        #       Descubrimeinto host NMB desde LAN
                udp sport {137,138} udp dport {137,138} meta oif enp1s0 accept


        #       Usuario de sistema
                meta skuid debian-transmission accept
                


        #       Vuelta minidlna
                udp sport {1900} meta oif enp1s0 accept


       
 }



        chain forward {
                type filter hook forward priority 0; policy drop;


        #       permite atravesar TCP-UDP-PING por WAN
                ip protocol {tcp,udp,icmp} meta oif enx000ec6d9d549 accept


        #       Permite trafico racionado de vuelta
                ct state established,related meta iif enx000ec6d9d549 accept


        #       Puerto camara forward prueba
                ip daddr 192.168.50.190 tcp dport {554, 8000} meta iif enx000ec6d9d549 accept
                ip daddr 192.168.50.1 tcp dport {1194} meta iif enx000ec6d9d549 accept
       
        }


}


table ip nat {
        chain prerouting {
                type nat hook prerouting priority 0; policy accept;


        #       Traduccion de destino Destination NAT
                tcp dport {554, 8000} meta iif enx000ec6d9d549 dnat 192.168.50.190
                tcp dport {1194} meta iif enx000ec6d9d549 dnat 192.168.50.1
               
                 }

        chain postrouting {
                type nat hook postrouting priority 100; policy accept;


                masquerade


        }
}








```


Now the problem is when i wnat to connect to the glassfish v5 engine through the "asadmin" client or the web administrator (4848 port), by both ways the response is always the same, it can't reach the server.
The only way to make it work is to stop the nftables service, running out of internet in the process beacuase of the massquerading function.

I really hope some of you have an idea of what is the problem here, I know it is something related with the firewall but even putting an accepting policy on everything, nothing happened.

I'm sorry if I made some spelling mistakes or grammatical errors, I don't use english very much.

---

### Post by sfigueroab on 2017-12-26
I'm making a bump, if anyone have a hint of what may be the answer it would be awesome.

---

