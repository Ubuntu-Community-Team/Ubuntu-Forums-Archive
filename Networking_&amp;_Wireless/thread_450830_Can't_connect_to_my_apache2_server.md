---
title: "Can't connect to my apache2 server"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by spock84 on 2007-05-21
'netstat -tap' tells me apache is running and listening to the configured port and it works fine when I connect on localhost or 10.0.0.20, my lan ip, but not through the public ip. So I'm thinking it's a routing problem, but I don't really know much about routing and can't make any sense of it.

I've tried changing the port in the ports.conf file (as the router web interface listens on port 80), but none of them work, even though I'm reasonably sure I've forwarded the port correctly, just as I have forwarded ports successfully for torrent apps and such.

What could the problem be?

---

### Post by tomroffe on 2007-05-21
to clarify to say you have forwarded port 80 tcp to you internal ip 10.0.0.20 but your router listens on port 80. what router do you have?

---

### Post by spock84 on 2007-05-21
The router is a Thomson SpeedTouch, which has a web interface where you can change various settings, forward ports etc. which you connect to on port 80 through a web browser. Therefore I figured I'd use some other port for my server and none of the ports I've tried so far work.

---

### Post by tomroffe on 2007-05-21
sounds like your router is not forwarding traffic from port 80 on your external IP to your internet server correctly. on 10.0.0.2:80. check your routers docs and support to see if this is possible to forward port 80.

btw. if you configure your router to only listen for and forward traffic to your your server 10.0.0.2 on a port other then port 80 then you will have to explicitly state the port number in the url in your browser when trying to connect. e.g. [http://externaldomianorip:8080](http://externaldomianorip:8080)

---

### Post by spock84 on 2007-05-21
Well, I figured that I'd rather not use port 80, as I can't be bothered to mess around with telnet sessions and crap (there's no option to change this port in the web interface). And I know I have to state the port explicitly in the browser, and it just isn't working.

---

### Post by spock84 on 2007-05-22
Anyone?

---

