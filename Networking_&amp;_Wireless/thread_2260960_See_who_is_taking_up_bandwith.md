---
title: "See who is taking up bandwith?"
date: 2015-01-15
forum: Networking &amp; Wireless
---

### Post by haxerius on 2015-01-15
Hi, i live in a shared living and someone is taking up bandwith. Is there any way of see
1.who is taking up?
2.how much he is taking up?
3. and possible kicking him from the network or ping him down? 

if the third option requires brute illegal action please leave it blank.

---

### Post by newbie-user on 2015-01-15
If you have access to the router, see if it has any bandwidth monitoring tools.

---

### Post by haxerius on 2015-01-15
no can do, dont have permission for the router.

---

### Post by Frogs Hair on 2015-01-15
See the tcptrack option at the link.

[http://askubuntu.com/questions/257263/how-to-display-network-traffic-in-terminal](http://askubuntu.com/questions/257263/how-to-display-network-traffic-in-terminal)

---

### Post by haxerius on 2015-01-15
how does tcptrack work? cant see anything

used fing on my ihphone i now have ip adress of all devices on the network how can i find out whom is lagging the connection?

---

### Post by Frogs Hair on 2015-01-15
If not installed : ```
sudo apt-get install tcptrack 
```The  command I think you are looking for is as follows. ```
sudo tcpdump
```
See the first link for various command examples

[http://sickbits.net/tcptrack-simple-tcp-connection-monitor/](http://sickbits.net/tcptrack-simple-tcp-connection-monitor/)

[http://linux.die.net/man/1/tcptrack](http://linux.die.net/man/1/tcptrack)

---

### Post by haxerius on 2015-01-15
listening on eth0 .. im on wifi. 

Are you really forum moderator? 

How come a free ios app was more efficent than linux open source... think i tried maybe 15 different programs for linux befor using fring on my iphone and it even listed my neighbors samsung phone...

---

### Post by QIII on 2015-01-15
> **haxerius said:**
> listening on eth0 .. im on wifi. 

A tidbit of information we didn't know.

> Are you really forum moderator? 

Yes he is.  Why do you ask?

---

