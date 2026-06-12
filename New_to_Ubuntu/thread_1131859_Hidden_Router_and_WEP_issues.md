---
title: "Hidden Router and WEP issues"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by fiona-conn on 2009-04-21
Okay, so, I have a Netgear wireless router. I access the wireless via my laptop, which has Windows Vista, and Ubuntu (Intrepid) on it. 

Last night, after much thinking about it 'cause I was concerned, I decided to try securing the router because it was visible to pretty much everyone in the neighbourhood (though mind, so are their routers...) I did the usual stuff -- was able to access the router page via 192.168.0.1 and then turned off broadcasting and applied WEP security. 

This was all fine once I had my Vista connection set up to work with it, as well as the other computers in the house. However, when I tried to use Ubuntu, I couldn't connect, despite fixing the Network Connections so that it would provide the correct WEP code. 

Things got more complicated when I realized that disconnecting the internet from our computers would result in us being unable to access it, period. 

So, I turned WEP OFF and restored the settings to broadcasting. This was fine on the Windows computers. 

However, on Ubuntu, I am *still* having problems: Ubuntu seems to believe the router is STILL hidden and won't detect it. I've tried deleting the connection and reconfiguring it in the connections manager, but alas, it won't work. When I ask it to connect, it just sort of... talks to the router for about 2-5 minutes, and then refuses a connection. (Though, weirdly enough, it works when I plug in the ethernet cable. It's just the wireless it doesn't like. Auto-etho works.)

It was working absolutely FINE before any of this happened! So I'm not sure why it's being difficult.

Any advice would be really appreciated.

Thanks, folks.

~Fiona

---

### Post by LowSky on 2009-04-21
go to the network app on the panel

right clcik to edit connections, delete all current known connections., now disable wireless, and the reinable it should start re-looking for availbe networks

Also using the option to configure a network you can set up hidden wireless networks

---

