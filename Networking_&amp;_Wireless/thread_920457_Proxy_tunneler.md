---
title: "Proxy tunneler"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by Dark_Fire on 2008-09-15
Hey,

Well I am finally uninstalling Windows on my laptop, (meaning ill have 4 Linux PC's... :P) the main thing I used my laptop for was connecting to the internet. I also used a proxy tunneler callex "xera HTTP Proxy Tunnel".

What can I use to tunnel my internet?

Thanks...

---

### Post by qstraza on 2008-09-15
tor maybe?

---

### Post by NoReflex on 2008-09-15
I don't know what exactly do you mean by tunnel your Internet but if you want to relay your traffic or to bypass some security settings you could use a SSH server (I used open-ssh on a friend's computer and putty as a client on my PC).

If that's what you want let me know and I'll elaborate.

Best wishes,
NoReflex

---

### Post by Dark_Fire on 2008-09-15
Well yea, like when you tunnel something through one port...

I tried a few things now... no sucsess. I thought maybe if I give the config files of the other programe, you could make something out.

Note, I changed the IP's and Domains for security measures...

proxy.txt:
```
CONNECT {0}/test.example.co.za:{1} HTTP/1.1
Proxy-Connection: Keep-Alive
Accept-Encoding: identity;q=1.0, *;q=0
Cache-Control: no-cache no-store no-transform
Accept: text/html; text/plain; */*


```
Config.ini:
```
[HttpProxyTunnel]

; this is the port xera HTTP Proxy Tunnel will listen for connections on
ProxyPort = 777

; Remote Address of HTTP Proxy Server
RemoteIP = 162.168.0.99
RemotePort = 8080

; if web Request Declares host, connect to it
ConnectToHost = true
; Connect to host on the following default port. 80 or 8080
DefaultHostPort = 80

; Network Activity
Bytes_rx=1522971639

```

So umm yea...

---

### Post by Dark_Fire on 2008-09-15
NoReflex, you have any ideas? You think its possible?

If you want I could send you The windows programme as well?

Thanks so much for your help and quick replies. :)

---

### Post by NoReflex on 2008-09-16
Hello again!

Yes, I think it's possible. I used it to bypass proxy limitations at my university campus. They had a proxy (port 3128) that accepted traffic only on port 80 and 443. What I did was to install a ssh server on my friend's router (Asus WL-700G - which runs Linux) and configured it to listen for connections on port 443.
On my notebook I used putty (you can use any other ssh client) and added SSH tunnel on port 8080 (you can use any other port : 1080 etc.) and connected to my friend's router. 
Now you must setup the programs you want to use the tunnel with the following proxy information : 
```
hostname : localhost (or 127.0.0.1)
port : 8080 (or whatever you chose previously)
```
You can use this with Firefox (or whichever browser you use), uTorrent (or other bittorrent clients), basically any other proxy-aware program.
If a program doesn't have a proxy configuration option you can try to "socksify" it. On Windows I used SocksCap or FreeCap. I haven't searched for but I'm sure there are Linux equivalents.
You must be carefull though because the DNS requests won't be tunneled (as far as I know you can't tunnel UDP - if I'm wrong please correct me).

I hope this helps you!

Best wishes,
NoReflex

---

### Post by kjetilbmoe on 2008-12-03
> **NoReflex said:**
> Hello again!

Yes, I think it's possible. I used it to bypass proxy limitations at my university campus. They had a proxy (port 3128) that accepted traffic only on port 80 and 443. What I did was to install a ssh server on my friend's router (Asus WL-700G - which runs Linux) and configured it to listen for connections on port 443.
On my notebook I used putty (you can use any other ssh client) and added SSH tunnel on port 8080 (you can use any other port : 1080 etc.) and connected to my friend's router. 
Now you must setup the programs you want to use the tunnel with the following proxy information : 
```
hostname : localhost (or 127.0.0.1)
port : 8080 (or whatever you chose previously)
```
You can use this with Firefox (or whichever browser you use), uTorrent (or other bittorrent clients), basically any other proxy-aware program.
If a program doesn't have a proxy configuration option you can try to "socksify" it. On Windows I used SocksCap or FreeCap. I haven't searched for but I'm sure there are Linux equivalents.
You must be carefull though because the DNS requests won't be tunneled (as far as I know you can't tunnel UDP - if I'm wrong please correct me).

I hope this helps you!

Best wishes,
NoReflex
Hi there.
Sounds like a good trick, I have been using putty tunnelig for other apps and services before. But I just don't get it - what port or host do you enter? If I enter only ":" then it won't work.

---

### Post by kjetilbmoe on 2008-12-05
How to make a SSH tunnel with putty:

[LIST=1]
[*]Configure your you router or firewall to accept port 443 and route this to your openssh listening server. Note that you can choose whatever port you'd like, but the port 443 is usually allowed in any narrow minded network. And you don't want to use port 80, becuase that's for your web server. Well, if you don't have a webserver, feel free to use that port too. (I set up my own router to accept two different [*outside*] ports - both the 443 and another *secret* one - and route them [*internally*] to my ssh listening port) :D
[*]Load you fav putty preset, or start a new one.
[*]Go to Connection > SSH > Tunnels. Here add a port number of choice. Tick *Dynamic*, and you're good to go.
[*]Klikk *Open*
[/LIST]

Now you may access the world wide web (or whatever) having your remote computer as proxy. In Firefox, add a SOCKS proxy with hostname "localhost", the port number you just chose, and tick "SOCKS 5". Works like a dream. You might want to add "Switchproxy" add-in for firefox to easily switch between multiple proxies.

;)

(Edit: if you cannot reroute the ports internally, you must add listening port 443 in you ssh config. Do: "sudo nano /etc/ssh/sshd_config" and add the port(s) you want, and restart "sudo /etc/init.d/ssh restart")

---

