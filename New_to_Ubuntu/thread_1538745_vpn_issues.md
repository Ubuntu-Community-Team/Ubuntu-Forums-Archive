---
title: "vpn issues"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by lazurrpewpew on 2010-07-25
I'm trying to setup a VPN with my uni while I'm abroad and I'm running into some issues. My uni uses Cisco Anyconnect, so I downloaded the Openconnect package. I also have my school's vpn config file. I try to connect by typing in the terminal (I think I read these instructions somewhere...)

```
sudo openconnect --script /etc/vpnc/myvpnfile.pcf https://vpn.school.edu
```

I get prompted for my username and password, I type them in, and then I get 

```

CSTP connected. DPD 30, Keepalive 20
sh: /etc/vpnc/myvpnfile.pcf: Permission denied
Failed to spawn script '/etc/vpnc/myvpnfile.pcf': Success
Connected tun1 as 18.101.24.250, using SSL + deflate
Established DTLS connection

```

Then the terminal just hangs there. I know I haven't actually established a VPN connection because I still can't use our Matlab licenses or access sites that aren't available in Europe (Pandora, for example.) I'm pretty clueless about setting up VPNs, so I really don't know what's going wrong or if there is a better/easier way. Any help is appreciate, thanks!

---

### Post by yeats on 2010-07-25
You might try vpnc, which is designed for Cisco VPNs.  You'll need the following information:


IPSec gateway 
IPSec ID 
IPSec secret 
Xauth username 
Xauth password

This is how I connect to my work VPN.

---

### Post by dwmw2 on 2010-07-26
It looks like you've successfully connected to the VPN; it's just that you haven't set up the routing so your system isn't **using** it.

The script is supposed to set up the routing for you, but you've given it the wrong script. It's supposed to be /etc/vpnc/vpnc-script (or wherever Ubuntu puts that). You could also use the NetworkManager-openconnect plugin and connect using the GUI.

You don't need the PCF file. That just contains the VPN configuration, and the only important part of that is the [https://vpn.school.edu/](https://vpn.school.edu/) URL which you already know.

This isn't the best place to ask questions; the openconnect-devel mailing list would be better. I only saw this here by chance.

---

### Post by lazurrpewpew on 2010-08-18
It works and dwmw2 is right.

All I had to do after selecting the connection type as Cisco AnyConnect Compatible VPN was
1. Set Gateway as school.vpn.edu
2. Enter my school username in Username
3. Leave everything else as default
4. Connect!

In retrospect this all seems fairly obvious :).

---

