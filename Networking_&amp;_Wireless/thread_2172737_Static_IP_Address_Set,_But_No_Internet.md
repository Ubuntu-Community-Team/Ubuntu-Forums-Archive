---
title: "Static IP Address Set, But No Internet"
date: 2013-09-06
forum: Networking &amp; Wireless
---

### Post by jakeclarkphoto on 2013-09-06
Hey everyone,

I teach at a university in Korea, and I've just moved into campus housing. I've been trying to connect to the LAN here with the IP information I was given today, but I haven't had any success despite inputting the information in "IPv4 Settings" using the GUI and restarting my computer several times.

I guess I'm connected to a central router, since I'm connected directly to the ethernet wall jack with an ethernet cable.

I've tried some fixes I've read about on the forums here - like setting the "IPv6 Settings" to "Ignore," and fiddling with the "/etc/network/interfaces" (which I eventually fiddled back to its original state... I think) - but nothing has done the trick.

I've pinged my gateway address and gotten: "PING xxx.xxx.xxx.xx (xxx.xxx.xxx.xx) 56(84) bytes of data."
And several lines that looked like:               "64 bytes from xxx.xxx.xxx.xx: icmp_req=1 ttl=255 time=0.549 ms"
And my ping statistics were:                       "10 packets transmitted, 10 received, 0% packet loss, time 9000m"

I've pinged [www.google.com]("http://www.google.com") and gotten: "PING [www.google.com]("http://www.google.com") (74.125.235.114) 56(84) bytes of data."
And several lines that looked like:          "64 bytes from nrt19s02-in-f18.1e100.net (74.125.235.114): icmp_req=1 ttl=48 time=96.2 ms"

I'm running Ubuntu 12.04, using MATE as my GUI. Does anyone know what my problem could be?

---

### Post by steeldriver on 2013-09-06
Hello and welcome to the forum

If you can ping [www.google.com]("http://www.google.com") both by IP and name, then you are basically connected to the internet, so your IPv4 settings are all OK I think - the only thing I can think of is that your university / residence requires you to use a proxy for internet browsing, or requires you to sign in via a 'captive portal' using your university account credentials.

---

### Post by varunendra on 2013-09-06
Hi, and Welcome to the fourms ! :)

> **jakeclarkphoto said:**
> 
I've pinged the gateway address and gotten: "PING 203.253.171.10 (203.253.171.10) 56(84) bytes of data."
And several lines that looked like:               "**64 bytes from 203.253.171.10: icmp_req=1 ttl=255 time=0.549 ms**"
And my ping statistics were:                       "**[COLOR="#006400"]10 packets transmitted, 10 received, 0% packet loss,[/COLOR] time [COLOR="#FF0000"]9000m[/COLOR]**"

I've pinged [www.google.com]("http://www.google.com") and gotten: "PING [www.google.com]("http://www.google.com") (74.125.235.114) 56(84) bytes of data."
And several lines that looked like:          "**[COLOR="#006400"]64 bytes from nrt19s02-in-f18.1e100.net (74.125.235.114): icmp_req=1 ttl=48 time=96.2 ms[/COLOR]**"

Everything above suggests that you are properly connected to the gateway as well as internet and so should be able to browse. Although the average response time from gateway is a bit long, the response time from google was perfectly ok.

Try changing your DNS to Google's open DNS servers - "8.8.8.8, 8.8.4.4" and see if you can browse.

---

### Post by jakeclarkphoto on 2013-09-06
> **varunendra said:**
> Hi, and Welcome to the fourms ! :)



Everything above suggests that you are properly connected to the gateway as well as internet and so should be able to browse. Although the average response time from gateway is a bit long, the response time from google was perfectly ok.

Try changing your DNS to Google's open DNS servers - "8.8.8.8, 8.8.4.4" and see if you can browse.


I tried those DNS servers, but still no success. And if my university requires me to login via a proxy or capitive portal, I was not informed of this necessity.

---

### Post by chili555 on 2013-09-06
Please tell us how you are not connected. As we've seen, you can ping the gateway and Google by name suggesting that you have a connection and that DNS is working. Is it when you open Firefox and look for a website, say [http://www.google.com](http://www.google.com), for example, that things go wrong? In Firefox >Edit > Preferences > Advanced > Network, what are the settings? Here are mine, for comparison.

---

### Post by jakeclarkphoto on 2013-09-07
> **chili555 said:**
> Please tell us how you are not connected. As we've seen, you can ping the gateway and Google by name suggesting that you have a connection and that DNS is working. Is it when you open Firefox and look for a website, say [http://www.google.com](http://www.google.com), for example, that things go wrong? In Firefox >Edit > Preferences > Advanced > Network, what are the settings? Here are mine, for comparison.

Yes, I guess I should have specified that: My problem is that I can't access web pages with Firefox or Chrome. 

Here are screenshots of the messages I get from Firefox and Chrome when I try to load a web page, and each browser's proxy settings. Chrome wouldn't allow me to access its proxy settings, so I took a screenshot of the message it gave me when I tried.

---

### Post by SeijiSensei on 2013-09-07
Can you connect to Google?  We already know you can ping it.  Can you connect to [https://www.google.com/](https://www.google.com/) but not [http://www.google.com/](http://www.google.com/)?  If so, it's likely your university is using a transparent proxy that is filtering HTTP content.

Did you read any and all rules from the university governing Internet usage?

---

### Post by chili555 on 2013-09-07
Fascinating.

Please run and post:```
ping -c3 www.espn.com
wget www.espn.com
sudo ufw status
```If ufw is active, temporarily turn it off:```
sudo ufw disable
firefox www.google.com
```Any improvement?

Obviously, if shutting down the firewall ufw helps, we need to do some reconfiguration.

---

### Post by jakeclarkphoto on 2013-09-07
Huh, well... my bad, guys. I kept trying to access web pages with Chrome as I continued to fiddle with my network settings and I noticed that I was getting a different message telling me I couldn't connect - a message written in Korean. At the bottom of the message was a button for me to click on, and my Korean skills aren't great, but some process ran and completed, and now I can access web pages. I apologize for the false alarm, guys - it looks like all I had to do was click on that button. I didn't even realize it was a button the first few times I saw it. Thanks all y'all for trying to help me out.

---

### Post by chili555 on 2013-09-07
No worries at all! I suspect it may be similar to the button as I saw at the doctor's office the other day; something like, "...by clicking this button, I accept the terms and conditions required for access to the guest network." 

Glad it's working.

---

