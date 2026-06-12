---
title: "Auto restart openVPN if stopped - Cron help ?"
date: 2019-03-12
forum: Networking &amp; Wireless
---

### Post by neilanthonystuckey on 2019-03-12
Hello thanks for your time first of all.  I recently overhauled my home network and server.  I have never had this issue before but for some reason on this new server build i have an issue with openVPN disconnecting.  About once  a week ill check my connection info with ip route and sure enough my local ip shows instead of the  openVPN ip's.  I  manually start the vpn from cli and its good for about another week.  Would any of you linux/Ubuntu experts have a clever way to check and see if tun0 is present and if not restart the open vpn service maybe once a day ? I am using Ubuntu Server 16.04.6 64 bit with the latest patches installed.

---

### Post by SeijiSensei on 2019-03-12
First, let's see the configuration file for the connection.  In particular, do you have these directives?

```

ping 15
ping-restart 45
persist-tun
persist-key

```

See "[man openvpn]("https://linux.die.net/man/8/openvpn")" for an explanation of these directives.

---

### Post by neilanthonystuckey on 2019-03-12
Thanks SeijiSensei for the reply. As for my .ovpn file

No - ping 15
No - ping-restart 45
Yes - persist-tun
Yes - persist-key

---

### Post by neilanthonystuckey on 2019-03-12
Here is the full config file. 

client
dev tun
proto udp
remote sweden.privateinternetaccess.com 1198
resolv-retry infinite
nobind
persist-key
persist-tun
cipher aes-128-cbc
auth sha1
tls-client
remote-cert-tls server
crl-verify /etc/openvpn/crl.pem
ca /etc/openvpn/ca.crt
auth-user-pass /etc/openvpn/auth.txt
verb 1
reneg-sec 0
--comp-lzo adaptive

---

### Post by SeijiSensei on 2019-03-13
Try adding the ping directives.  Their purpose is to keep up the connection when it idles.  There's also the "keepalive" directive which I haven't used.

In answer to your question, you can try something like this:

```

#!/bin/bash

# openvpn restart if down
# save as /usr/local/sbin/openvpn-restart

TEST=$(ps aux | grep openvpn)

if [ "$TEST" = ""  ] 
then
     systemctl restart openvpn
fi

```

and a corresponding entry in /etc/crontab

```

* * * * * root sh /usr/local/sbin/openvpn-restart

```

that runs the script once each minute.

But I'd try things like ping-restart and keepalive first before going to all this rigamarole.

---

### Post by neilanthonystuckey on 2019-03-13
Agreed. I applied those to my config we shall see.

---

