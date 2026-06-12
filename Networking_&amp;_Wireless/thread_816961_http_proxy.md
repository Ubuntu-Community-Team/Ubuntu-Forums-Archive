---
title: "http proxy?"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by ianq on 2008-06-03
So, my parents summoned me and I had to fly to Europe. Now I'm stuck here not being able to watch my The Office episodes or listen to my Pandora stations, a fact which I find aggravating. Since I have a server sitting in my basement in the US that I can control via SSH, I thought why not set up an http proxy so I can connect through my home network in the States to my important websites?

Can anybody point me in the right directions with some tips on the matter?

---

### Post by gvartser on 2008-08-08
One way of doing it is to create a socks proxy from your ssh connection and then use this proxy in your Firefox browser.


1) Connect to your home node using the following ssh syntax:
```
ssh <username>@<home_ip> -D 127.0.0.1:7884
```

2) Configure your browser to use a SOCKS proxy: 
   -> FireFox: Edit -> Preferences ->  Network -> Settings
   -> Add: IP:127.0.0.1, Port:7884

3) Surf..

A tip is to install Firefox addon "FoxyProxy", this allows you to setup rules on which proxy to use depending on website.

Best regz,
/g

---

