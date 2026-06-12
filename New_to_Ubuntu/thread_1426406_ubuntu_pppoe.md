---
title: "ubuntu pppoe"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by aloprot on 2010-03-10
i installed my pppoe connection using sudo pppoeconf and it worked like a charm for one week and when restarting it would automatically login. now i turned on the machine and it would't automatically load so i sudo pppoeconf again, works for 4 minutes or so and then nothing..if i type sudo pppoeconf it works again.why is this and what can i do to run my internet connection without this frustrating problem?
It's not from my isp, I have checked and in windows the connection works like a charm.

In the terminal when i hit plog i get a strange message like
modem hangup/connection terminated/serial link appears to be disconnected/connect time 3.5 minutes.

---

### Post by aloprot on 2010-03-10
Can someone please help me?

---

### Post by aloprot on 2010-03-10
bump*:popcorn:

---

### Post by TheLions on 2010-03-10
try installing gnome-ppp and setup everything from there:
sudo apt-get install gnome-ppp

---

### Post by rrinjapan on 2010-03-11
Aloprot,

I've had the same problem and I find that it usually happens if I've tried to connect to another pppoe network at work on my netbook. After I do that, nothing really works or it works just before I give up ... I don't have any answers for you at this time but that seems to be the cause of it for me.

RR

---

### Post by aloprot on 2010-03-11
Hello again, after 20 sudo pppoeconf commands I can not keep my internet connection stable. It goes of 1 or 2 minutes, and if i type plog it says something like"serial link appears to be disconnected, connection terminated, modem hangup(i don't have a modem...why is that showing there?)I have a fiber optic connection and I connect using a lan cable with both username and password provided by my isp. What can I do to fix this problem?. I'm desperated....can't do nothing on ubuntu because of the internet.
Please help me, the folks on irc could not help me because I only can write the question, and boom my internet connection is down.

---

### Post by isee on 2010-03-11
Hi aloprot!

I don't know if this will help but I created a DSL connection using the NetworkManager Applet icon. I've never heard of the sudo pppoeconf command (not that I know any commands, I'm still noob).

This is the thread I was working in: [http://ubuntuforums.org/showthread.php?t=1427279&page=2](http://ubuntuforums.org/showthread.php?t=1427279&page=2)

I have an Auto eth0 connection for when I connect via my DLink (my Wired connection), and DSL connection 1 for when I disconnect my DLink and connect directly to my ISP's modem.  I don't set either of them to automatically connect.  I don't like my computer logging on to the internet just because I've turned it on,

My wireless through my DLink drops the connection periodically, but other than that it is stable.

Are you sure you don't have an ISP modem/cable-box?  My ISP modem provides my TV as well as my internet and telephone call display (thru my TV).

Cheers and good luck!

---

### Post by aloprot on 2010-03-11
The same connection under windows is working like a charm..it's not my isp that's for shure.

---

### Post by aloprot on 2010-03-11
I have tried using network connections and thicked autostart so everytime it should login with my username and password...but this has't changed anything.

---

### Post by aloprot on 2010-03-11
No one can help me?

---

### Post by aloprot on 2010-03-11
Please?I'm the single ubuntu user who uses pppoe in the world?>

---

### Post by isee on 2010-03-11
I have two ways to connect via PPPoE.

My DLink router stores my username and password to connect via PPPoE to my ISP.  I connect to my router using Auto eth0.

If I unplug my router and plug my PC directly in, I had to create a DSL connection in my Network Manager which uses a PPPoE connection.

So either way I have pppoe.

Wish I could help more.

---

### Post by aloprot on 2010-03-11
[http://serverfault.com/questions/3097/ubuntu-pppoe-connection-timeout](http://serverfault.com/questions/3097/ubuntu-pppoe-connection-timeout)


I get the same output in my terminal.

---

### Post by aloprot on 2010-03-11
bump*

---

### Post by aloprot on 2010-03-11
*bump

---

