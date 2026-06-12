---
title: "Network Proxy script"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by solracarevir on 2007-01-03
Hi, I use my laptop on both my home and my work, no issues there, the problem is that on my work we have a network proxy and i have to switch my proxy settings on my preferences and in synaptics. Im planning writing a script wich ask averytime i boot, if im from work or at home, and then it changes automaticly both proxy settings,but i need to know, were ubuntu store those settings? or even better, is there any application right now that changes that for me? Im trying to make it as simple as posible, any insight would help me a lot. if i managed to make it, i will post it for all of you who are on the same situation.

Regards!

---

### Post by koenn on 2007-01-03
firefox proxy settings are in the .mozilla folder in your home dir, in
.mozilla/firefox/(somerandomfolder)/prefs.js

the look like this, buit can change depending on what youve set in preferences :
```
user_pref("network.proxy.http", "  blablabla ");
user_pref("network.proxy.http_port", 8080);
user_pref("network.proxy.no_proxies_on", "localhost, 127.0.0.1,");
user_pref("network.proxy.type", 1);
```

synaptic proxyis defined in /etc/apt/apt.conf, and looks like this:
```
Acquire::http::Proxy "http://serveraddress:proxyport";
```

I suppose you could keep two versions (with and without proxy) and have a script that puts the correct version in place, or have a script that does a "find and replace" action inside the files, or a script that writes into the file to set the proxy and restores a copy if you don't need the proxy. 
Have fun.

---

### Post by solracarevir on 2007-01-03
thanks for the info! the only one still missing is the one of the "Network Proxy" setting inside System/preferences menu which i think is the key /system/http_proxy/use_http_proxy... but im not sure, i'll try to start working on it later during the night, thanks!:D

---

### Post by 454redhawk on 2007-01-03
The firefox extension "switch proxy" might be eaiser. A single click to change to ANY proxy.

---

### Post by solracarevir on 2007-01-04
it would work, but it also changes the ubuntu proxys? or only the firefox proxy?

---

### Post by jamin100 on 2007-12-06
Did you ever finish this script?

I would love to have a copy if you did because i'm in the same boat :)

---

