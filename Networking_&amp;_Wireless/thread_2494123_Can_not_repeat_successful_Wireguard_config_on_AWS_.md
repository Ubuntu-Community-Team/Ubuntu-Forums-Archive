---
title: "Can not repeat successful Wireguard config on AWS or OCI"
date: 2024-01-05
forum: Networking &amp; Wireless
---

### Post by armars on 2024-01-05
Hi everyone
please help me to resolve this strange problem

about a year I am already successfully configured and using Ubuntu 22.04 on aws with Wireguard

configuration is very simple aws has 10.8.0.1 ip and win11 has 10.8.0.2 for wireguard.  I need access only this ips from each other (assume I need only ping 10.8.0.1 from 10.8.0.2 and backwards )
and this works on my aws without any problem. my aws has reserved public ip

here is configs of aws side
```

[Interface]
Address = 10.8.0.1/24
ListenPort = 51820
PrivateKey = aws-private-key


[Peer]
PublicKey = win11-public-key
AllowedIPs = 10.8.0.2/32

```

win11 config
```
[Interface]
PrivateKey = win11-private-key
Address = 10.8.0.2/32


[Peer]
PublicKey = aws[COLOR=#000000][FONT=&amp]-public-key[/FONT][/COLOR]
AllowedIPs = 10.8.0.1/24
Endpoint = aws-public-IP:51820
PersistentKeepalive = 60

```

also I opened 51820 port in aws web console
[[IMG]https://i.ibb.co/qC5vT0W/image-2024-01-06-062912728.png[/IMG]]("https://ibb.co/qC5vT0W")

[I used this tutorial]("https://www.digitalocean.com/community/tutorials/how-to-set-up-wireguard-on-ubuntu-22-04") without Step 4 and Step 5, because I don't need internet traffic routing IP forwarding
/etc/sysctl.conf on aws is all lines commented 

on aws side to initialize config used this commands
```
sudo systemctl enable wg-quick@wg0.service
sudo systemctl start wg-quick@wg0.service

```

here is also result of sudo systemctl status [EMAIL="wg-quick@wg0.servic"]wg-quick@wg0.servic[/EMAIL]e
```
ubuntu@ip-172-31-33-195:~$ sudo systemctl status wg-quick@wg0.service
&#9679; wg-quick@wg0.service - WireGuard via wg-quick(8) for wg0
     Loaded: loaded (/lib/systemd/system/wg-quick@.service; enabled; vendor preset: enabled)
     Active: active (exited) since Sat 2024-01-06 01:15:16 UTC; 1h 28min ago
       Docs: man:wg-quick(8)
             man:wg(8)
             https://www.wireguard.com/
             https://www.wireguard.com/quickstart/
             https://git.zx2c4.com/wireguard-tools/about/src/man/wg-quick.8
             https://git.zx2c4.com/wireguard-tools/about/src/man/wg.8
    Process: 376 ExecStart=/usr/bin/wg-quick up wg0 (code=exited, status=0/SUCCESS)
   Main PID: 376 (code=exited, status=0/SUCCESS)
        CPU: 78ms


Jan 06 01:15:15 ip-172-31-33-195 systemd[1]: Starting WireGuard via wg-quick(8) for wg0...
Jan 06 01:15:16 ip-172-31-33-195 wg-quick[376]: [#] ip link add wg0 type wireguard
Jan 06 01:15:16 ip-172-31-33-195 wg-quick[376]: [#] wg setconf wg0 /dev/fd/63
Jan 06 01:15:16 ip-172-31-33-195 wg-quick[376]: [#] ip -4 address add 10.8.0.1/24 dev wg0
Jan 06 01:15:16 ip-172-31-33-195 wg-quick[376]: [#] ip link set mtu 8921 up dev wg0
Jan 06 01:15:16 ip-172-31-33-195 systemd[1]: Finished WireGuard via wg-quick(8) for wg0.
ubuntu@ip-172-31-33-195:~$

```
and I repeat again everything works

------------------------------------

[B]now the problem
[/B]
I am tring to repeat this config on other aws instance with same verion of ubuntu
also I tried on oracle instance

and it does not work, windows dont connect to aws or oracle, but same windows succesfuly connects to my old aws


on new aws and oracle I did same steps to config 

here is windows log

[[IMG]https://i.ibb.co/J25QhGZ/image-2024-01-06-065310091.png[/IMG]]("https://ibb.co/J25QhGZ")

here is oracle sudo systemctl status [EMAIL="wg-quick@wg0.servic"]wg-quick@wg0.servic[/EMAIL]e```
ubuntu@instance-20240105-0446:~$ sudo systemctl status wg-quick@wg0.service
&#9679; wg-quick@wg0.service - WireGuard via wg-quick(8) for wg0
     Loaded: loaded (/lib/systemd/system/wg-quick@.service; enabled; vendor preset: enabled)
     Active: active (exited) since Sat 2024-01-06 01:12:57 UTC; 1h 44min ago
       Docs: man:wg-quick(8)
             man:wg(8)
             https://www.wireguard.com/
             https://www.wireguard.com/quickstart/
             https://git.zx2c4.com/wireguard-tools/about/src/man/wg-quick.8
             https://git.zx2c4.com/wireguard-tools/about/src/man/wg.8
    Process: 785 ExecStart=/usr/bin/wg-quick up wg0 (code=exited, status=0/SUCCESS)
   Main PID: 785 (code=exited, status=0/SUCCESS)
        CPU: 188ms


Jan 06 01:12:55 instance-20240105-0446 systemd[1]: Starting WireGuard via wg-quick(8) for wg0...
Jan 06 01:12:56 instance-20240105-0446 wg-quick[785]: [#] ip link add wg0 type wireguard
Jan 06 01:12:57 instance-20240105-0446 wg-quick[785]: [#] wg setconf wg0 /dev/fd/63
Jan 06 01:12:57 instance-20240105-0446 wg-quick[785]: [#] ip -4 address add 172.22.0.1/24 dev wg0
Jan 06 01:12:57 instance-20240105-0446 wg-quick[785]: [#] ip link set mtu 8920 up dev wg0
Jan 06 01:12:57 instance-20240105-0446 systemd[1]: Finished WireGuard via wg-quick(8) for wg0.
ubuntu@instance-20240105-0446:~$

```

in tutorial somebody commented this maybe problem is in this??
> [COLOR=#4D5B7C][FONT=Inter]Step 6 Setting up WireGuard Server is no longer working… it locks up Droplets on Digital Ocean, no matter the Ubuntu version. It seems that the ip rule subcommand that wg-quick runs is causing the issue:[/FONT][/COLOR]
[COLOR=#4D5B7C][FONT=Inter]sudo systemctl start [EMAIL="wg-quick@wg0.servic"]wg-quick@wg0.servic[/EMAIL]e[/FONT][/COLOR]
[COLOR=#4D5B7C][FONT=Inter]ip -4 rule add not fwmark 51820 table 51820[/FONT][/COLOR]


sorry for long topic i tried explain in details
I don't want use ready scripts from github because I need to learn

if you need more details please ask

thank you
 hope somebody will help me

---

