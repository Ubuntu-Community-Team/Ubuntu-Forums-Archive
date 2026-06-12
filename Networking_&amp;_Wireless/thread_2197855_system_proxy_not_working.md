---
title: "system proxy not working"
date: 2014-01-05
forum: Networking &amp; Wireless
---

### Post by ertyugttt on 2014-01-05
hi im using ubuntu 12.04 and am setting my system proxy from terminal woth commands

gsettings set org.gnome.system.proxy.socks host '127.0.0.1'
gsettings set org.gnome.system.proxy.socks port 9050
gsettings set org.gnome.system.proxy mode 'manual'

this works when i open a browser but when i check my ip from terminal with commands

wget -qO- [http://ipecho.net/plain](http://ipecho.net/plain)

it gives me my normal ip address therefore the proxy isnot set system wide!
does anyne know of a way to route all system traffic thrpugh a proxy? in this case tor

thanks

---

