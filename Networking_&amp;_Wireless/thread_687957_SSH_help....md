---
title: "SSH help..."
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by Saponsky09 on 2008-02-04
I'm trying to connect remotely from my university using ssh.  The problem is that i don't know the external IP address of the machine I want to connect to (my Desktop PC).  All I get is always my network address.  I need help to find the correct IP.
  My home network (where resides the PC I want to connect to) is set this way:
I connect to the Internet using DSL so it goes... ISP -> SpeedTouch Router -> Linksys Router -> My Laptop + My Desktop PC (target)
If i do ifconfig all i get is my internal addresses.  I also tried a web page like whatismyip.com but it tells my ISP's IP, I don't know how to connect to my PC.  As you noticed I don't know too much about IP addressing so please if you could explain how to solve my problem I would appreciate a lot. Tanx in advance.

---

### Post by stalker145 on 2008-02-04
> **Saponsky09 said:**
> I'm trying to connect remotely from my university using ssh.  The problem is that i don't know the external IP address of the machine I want to connect to (my Desktop PC).  All I get is always my network address.  I need help to find the correct IP.
  My home network (where resides the PC I want to connect to) is set this way:
I connect to the Internet using DSL so it goes... ISP -> SpeedTouch Router -> Linksys Router -> My Laptop + My Desktop PC (target)
If i do ifconfig all i get is my internal addresses.  I also tried a web page like whatismyip.com but it tells my ISP's IP, I don't know how to connect to my PC.  As you noticed I don't know too much about IP addressing so please if you could explain how to solve my problem I would appreciate a lot. Tanx in advance.

Have you tried using the IP you got from whatismyip? That is actually the one you'll be using. Also you will need to forward port 22 on your router to your desktop.

---

### Post by Saponsky09 on 2008-02-04
Hmmm.. how do I forward my router to port 22 ?

---

### Post by jmar71n on 2008-02-04
First you will need to set up a static ip address on your home computer you want to connect to,
likely to be something starting with 192.168.............

Then have a look at 

[http://portforward.com/english/routers/port_forwarding/routerindex.htm]("http://portforward.com/english/routers/port_forwarding/routerindex.htm")

Select your router then SSH and it will show you a guide how to set up port forwarding.

Then you will be able to connect to that computer using the external ip address.

Another thing to note is that you external ip address is likely to be dynamic, meaning it will change every time your modem reconnects. To get round this problem set up a free account at [https://www.dyndns.com/services/dns/dyndns/]("https://www.dyndns.com/services/dns/dyndns/"), and most linksys routers can act as a update client so you can enter your dyndns details in there, if not you will have to install one on the computer you want to connect to.

that way instead of entering your external ip address in the terminal to connect by ssh, you could enter eg; [email]yourservername@dyndns.org[/email].

---

### Post by Saponsky09 on 2008-02-04
Thank you very much for the links, I completely understood what my problem was.  I still can't connect to my PC via SSH.  I set up the Linksys router to port forward for the SSH application but, I still can't connect to my PC, I do ssh 'my ip' and the program just stays waiting for the connection...
could it be something related to set up the SpeedTouch router to port forward too?  This router has username and password restrictions and I can' t set it up like I did with the Linksys, any idea?

---

### Post by jmar71n on 2008-02-05
hi Saponsky09, are you sure the SpeedTouch part of your network is a router and not a modem.

If its a router as you said, with a built in modem you will have to set up port forwarding and that as well as the linksys router.
If it's just a modem, all connections will be passed to the linksys router, and no further setup would be required.

Also if your at a University, i know i have to apply to have a non standard ports opened. My Uni allows us to register 10 outgoing ports, so maybe your connection attempts are being blocked there.

---

### Post by Saponsky09 on 2008-02-05
yes, it is a router with a built in modem, the problem is as i said, that it is password potected so i can't set it up to port forward.  I'll try to contact my ISP to see what can i do to set it up to port forward.  If not I'll try some other methods (not convenient to my ISP)  and see if can get into the router settings. Anyways tanx a lot for your help, it solved most of my problem and I get to know the cause.

---

### Post by ruy_lopez on 2008-02-05
If you google "noip", you can set up a domain name that will always map to your routers ip address. Follow the instructions for installing the software that updates the dynamic domain name. Then all you do is: ssh [email]username@domain_created.noip[/email]

You have to enable fort forwarding for your home router.

Also, make sure you create a really difficult ssh password. Otherwise, in no time you'll have Koreans trying to brute force their way into your home system.

(no offence intended towards Koreans. But when I had my ssh port forwarded, the attacks all traced to Korean ips. Maybe they were zombies!)

---

### Post by Herman on 2008-02-05
The way I keep track of my external IP address of my home LAN is by having one of my home machines sent out an email every few hours. All emails contain the originating IP address in the message source. Probably the dyndns idea is easier and more convenient for most people, but my way works well enough for me.

I connect to the Internet using ADSL too, mine goes... ISP -> SpeedTouch 530 Router -> D-Link Router -> My Laptop + My Desktop PC (targets).

To access my speedtouch 530 broadband modem-router's console, I just open Firefox and type '10.0.0.138' into the address bar. It's a good idea to bookmark that page for future convenience.
Then I type in my username and password for the speedtouch broadband modem-router. I you don't have a username and password set you should set them for security reasons.
Then I click 'Advanced'-->'NAPT', and select the NAPT Entries tab.
Click 'New', and set up connection between my Speedtouch 530 and my D-Link router.
At that point you just need to know the IP address for the router and what port numbers you forwarded from the router. 

In my case I have forwarded a different port number from my router for each PC in my LAN. I just forward each of those port numbers straight through my Thompson Speedtouch modem. 
The IP address of the router is shown in my router's settings console which is accessible in a similar manner as the Thompson Speedtouch console, (by typing an IP number for it into my web browser.

It's usually a good idea to obtain the documentation for each piece of equipment you have by searching for it in Google, you can usually find a .pdf file or something you can download which can be very helpful. I found .pdf files in the CD-ROMs that came with my hardware and I copied those into my computer so I can refer to them easily anytime.

I hope that helps,
Regards, Herman :)

---

### Post by Herman on 2008-02-05
If you have lost your password for your Thompson Speedtouch modem you ca reset the whole modem by pressing the on/off switch for a certain number of seconds until certain lights start blinking and releasing it then pressing it again. I'm in the wrong computer at the moment so I don't have the exact instructions, but they're in the documentation.

---

