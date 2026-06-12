---
title: "Access to Poker site"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Achilles124 on 2009-02-05
I cannot connect to the poker site of [www.888.com](www.888.com). I get the errormessage:

Attempts to connect were unsuccessful. Do you wish to continue trying to connect?

[http://www.flickr.com/photos/11774983@N02/3255710876/sizes/o/](http://www.flickr.com/photos/11774983@N02/3255710876/sizes/o/)

I have ufw installed. How can I connect to this site?

---

### Post by hyper_ch on 2009-02-05
*edit*

---

### Post by RobsterUK on 2009-02-05
Just having a look at your screen shot there, is that running from a web  browser or is it a bit of software you've downloaded from 888?

---

### Post by Achilles124 on 2009-02-05
it runs from my browser, Mozilla Firefox.

---

### Post by Achilles124 on 2009-02-05
Hyper_ch, what kind of answer is that?

---

### Post by handydan918 on 2009-02-05
Attempting to connect to this site gives the pop-up you show in your screenie. The file they are trying to fool you into installing is a .exe. It could be anything, and it probably ain't good. If you really want to borrow trouble, press on, and try installing this junk in wine.

---

### Post by Achilles124 on 2009-02-05
No, handydan, I have played this game lots of years in my Microsoft-years. They make money from people making bets on the internet. So, they cannot afford to deliver junk to the people. My problem is when I want to play this software in the java-form. so, without installing the software. 

How can I check what happens when I want to play this game. Something must refuse the internetconnection. Where can I check that?

---

### Post by RobsterUK on 2009-02-05
Looking a little further I see the default is to get you to install a windows .exe but there is also a browser based option which it looks like you're using.

That being the case it seems likely that its a server end problem. Unfortunately there's no way to replicate your problem without signing up to the site, which I think I'd be foolish to do (no offence)

EDIT: The site is Flash based so you might want to check you have the latest version of Flash installed (currently 10)

---

### Post by Achilles124 on 2009-02-06
I am a bit embarrassed after finding the answer myself. What I did was to click on the button login. That is what I used to do on my windows computer. But since I work from a different computer now, I have to register first.#-o

For other pokerenthusiasts like me, a Linux site about Poker:
[http://www.linuxpoker.net/](http://www.linuxpoker.net/)

Thanks for your answers, you all.

---

### Post by m0nstersnatch on 2011-09-12
unfortunately it did not work for me. according to the customer help from 888poker.com I will need following ports open in order for the No Download version to work: 21, 25, 110, 80, 443, 8080, 8081, 8084, and 8085.
Now the problem is the ports are not open on my Ubuntu installation:
```
netstat -an | grep "LISTEN "tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN
```
```
telnet localhost 8084
Trying ::1...
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```
```
sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 8084 -j ACCEPT
```

Has anyone a suggestion ?! Thanks

---

### Post by m0nstersnatch on 2012-02-27
..as of 11.10 oneiric the web version works. 
i have updated wine to version 1.2.3 and now even the application opens (yay!), i can log in, but no amount ($) is shown anywhere, which basically means still no 888 poker under wine. at least i can use the web version from time to time.

---

