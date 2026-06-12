---
title: "ProXPN via OpenVPN bash script"
date: 2014-04-27
forum: Networking &amp; Wireless
---

### Post by alexandra2 on 2014-04-27
I am able to connect to ProXPN's VPN using the command:

```
sudo openvpn --config proxpn.ovpn
```

I want to make an executable shortcut for this. I have made a .sh and a corresponding .desktop file, with the contents:

```
#!/bin/bash         

sudo openvpn --config proxpn.ovpn
```

and

```
[Desktop Entry]
Name=connectproxpn
#Comment=kgs go server
Exec=sh /home/myusername/Documents/Scripts/connectproxpn.sh
Terminal=true
Type=Application
StartupNotify=true
```

I would have thought it would be straightfoward to run this, but I get the error: 

```
Options error: In [CMD-LINE]:1: Error opening configuration file: proxpn.ovpn
Use --help for more information.
```

I am new to scripting an STUMPED. Can anyone help me get a working script, so I can connect to this VPN with a click? I'm not too concerned with entering the credentials at this point, as long as I can get the basic connection working in this script.

Thanks,
Alexandra

Ubuntu 14.04

---

