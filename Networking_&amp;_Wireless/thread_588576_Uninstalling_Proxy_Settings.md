---
title: "Uninstalling Proxy Settings"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by philipwallbridge on 2007-10-23
I used to have to connect through a proxy server, so someone set up the computer to run through the proxy server.  Now I have a direct connection to the Internet, and firefox accesses the internet, but my update manager can't, either through the desktop interface, or the terminal.  I've reset the Network Proxy Preferences to Direct Internet Connection, but it hasn't helped, I think that my problem is deeper, Can anyone help me so that I can upgrade to Gutsy?

---

### Post by drlunanai on 2007-10-23
The same problem here.. was @ work today with my laptop and we have a proxy so I adjusted everything for that, and when I came home, I switched everything back to "Direct connection" and I can acces the internet, but can't update or use symantec package manager.. 

It want's to connect through the proxy with the settings that "don't exist".. how do I fix it?

---

### Post by drlunanai on 2007-10-24
Help, anyone? :(

---

### Post by staticsage on 2007-10-24
In Synaptic - Settings/Preferences/Network
Remove the proxy.

Please post back with your results.

---

### Post by drlunanai on 2007-10-24
Ok.. now I'm just ashamed of myself.. I'll go and spank myself.. I removed all the network proxy settings except that one.. 

Im still a n00b.. so sorry for being anoying..

---

### Post by staticsage on 2007-10-24
Hey, no worries! It happens to the best of us...

---

### Post by philipwallbridge on 2007-10-25
I'm sorry, but I've reset that to direct network connection and it still tries to update via the proxy server.  Any other ideas?  I may need to call up a file via the terminal and edit it perhaps?

---

### Post by staticsage on 2007-10-25
Try checking out System --> Preferences --> Network Proxy (I think that is where it is located, I'm not in front of my Ubuntu install right now)

For apt and synaptic you can also try checking this file manually: /etc/apt/apt.conf

```
sudo gedit /etc/apt/apt.conf
```

Look for a line that says something like

```
Acquire::http::Proxy "http://proxy:port"
```

and remove it.

---

### Post by philipwallbridge on 2007-10-25
Network Proxy shows direct internet connection.  My apt.conf is just a blank page, if you know what I should paste into it then please post it here.  The file at "gedit ~/.bashrc" doesn't contain any references to the proxy connection, if that helps.

---

### Post by philipwallbridge on 2007-10-26
Has anyone got any ideas at all?

---

