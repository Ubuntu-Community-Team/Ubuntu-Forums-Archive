---
title: "DG834G - AOL -  Ubuntu"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by Sussex on 2011-08-19
[FONT=Times New Roman][SIZE=3]**Background**[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I’ve been happily using a DG834G, AOL, Ubuntu; we changed our line provider but kept AOL; I now find cannot access the internet (DNS error). [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]After telling me that they do not support Linux, AOL helpline not particularly helpful, they told me to reset the router; and putting in new settings and to call Netgear - Netgear particularly un-obliging and would not give me the settings as they did not support the router! [/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]**Q.** Can someone tell what settings I need to use, and how I go about solving the problem (the complete amateur/kiddies version please). – Alternatively point me to an older post with the answer.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Thanks [/FONT][/SIZE]
 
 
[SIZE=3][FONT=Times New Roman]Sussex [/FONT][/SIZE]

---

### Post by coffeecat on 2011-08-19
Welcome to the forum.

I am tempted to advise you to find another ISP, particularly if the AOL unhelpline told you to reset the router. Among other things this blanks out the dsl username and password fields which means you won't be able to connect to any adsl service until they are filled in again.

We need the answers to a few questions.

1 - What country are you in?

2 - You changed your line provider. From whom to whom? In the UK if you change from BT to TalkTalk, for example, nothing is physically done to your line. I'm surprised the Internet failed coincident with this.

3 - Do you have your AOL adsl internet username and password? (Don't post them!) This will be in your internet connections details in your account page in the AOL website (if you can get into it). Alternatively, you can ask AOL, and pray that you speak to someone with their brain in gear. The username looks vaguely like an email address with '@' in it.

4 - Do you know your Netgear router login details - username and password? These are different from the above. If you never reset them, or if you have now reset the router, they'll be the default ones, and we can come back to that.

5 - What is the exact DNS error you got? Where did you see it?

By the way, I don't think Netgear were being deliberately unobliging. They cannot tell you what to do without the adsl username and password which you have to get from AOL.

---

### Post by Sussex on 2011-08-19
Thanks for getting back to me. 

We need the answers to a few questions.

1 - What country are you in? [COLOR=red]**UK**[/COLOR]

2 - You changed your line provider. From whom to whom? In the UK if you change from BT to TalkTalk, for example, nothing is physically done to your line. I'm surprised the Internet failed coincident with this. [COLOR=red]**BT to AOL **[/COLOR]

3 - Do you have your AOL adsl internet username and password? (Don't post them!) This will be in your internet connections details in your account page in the AOL website (if you can get into it). Alternatively, you can ask AOL, and pray that you speak to someone with their brain in gear. The username looks vaguely like an email address with '@' in it. [B][COLOR=red]Yes 
[/COLOR][/B]
4 - Do you know your Netgear router login details - username and password? These are different from the above. If you never reset them, or if you have now reset the router, they'll be the default ones, and we can come back to that. [B][COLOR=red]Sorry Nope[/COLOR]

[/B]5 - What is the exact DNS error you got? Where did you see it? [COLOR=red][B]The DNS error comes up when I start up either google or firefox, I cannot remember exactly but something along the lines of unable to connect to DNS server.
[/B][/COLOR]
[COLOR=red][/COLOR] 
[COLOR=red][B]Thanks
[/B][/COLOR]

---

### Post by Matt__ on 2011-08-19
[COLOR=Red]//EDIT: you changed line provider? to who? as far as I know you CANT do that with aol, it must be BT..something to do with pppoe I think.[/COLOR]

The following settings need to be used in the UK
access this by typing 192.168.0.1 into your browser address bar
put in your router user name and pass (default username is admin (or administrator)  and default password is password):


_BASIC SETTINGS_
encapsualtion = PPPoE
login = <yourphonenumber>@dialbb.com
password = your master screen name password [COLOR=Navy](caveat: sometimes this fails...you will need to ask for a new setup pass from aol..and wait a couple of hours before they reset it)[/COLOR]
dynamic ip
auto dhcp
enable NAT

_ADSL settings_
multiplex = LLC based
vpi = 0
vci = 38

_Wireless settings_
region = europe
channel = Aol insist that you use channel 11 preferably or 7...why I dont know..I didnt and still the router worked.
enable access point and broadcast of ssid.
mode g & b

start off with NO security to see if you can get it running. try to connect and be sure to check the auto connect box in ubuntu network manager.

once set up...reboot both router(hard reboot..turn off and unplug) and pc 

there is a reset pin hole on the back of the router if it really is required

good luck...I had all this set up for someone and ubuntu still wouldnt connect at first..nor windows as the exchange wasnt set to connect to anything.

Phone BT and get a line check too..just so you can reassure aol they are wrong when you need to call them...I think you can still do it automatically via dialling 50.

The best time to call AOL is in the evening, then you at least get native english speakers who wont lie to you like the poorly trained indian call centre do. 

Most important of all, keep on at them if you cant connect, it will no doubt be something theyre doing wrong at their end (the local exchange).

---

### Post by Sussex on 2011-08-19
Natty Narwhal and UK Beans, thanks I will give that a go.

---

### Post by coffeecat on 2011-08-19
> **Sussex said:**
>  [COLOR=red]**BT to AOL **[/COLOR]

I can't resist - the words frying-pan and fire spring to mind! :-s

Matt__ has given you everything you need. But a couple of thoughts.

AOL saying they don't "support" Linux - this is inexcusable in this context. The way you setup a router is identical in Windows, MacOS and Linux. The only difference is the browser you use; most Windows users will use Internet Explorer and Mac users Safari, but the procedure is the same.

I seriously suggest you think of finding another phone/internet provider. AOL usually comes about at or near the bottom in customer satisfaction surveys.

---

### Post by Matt__ on 2011-08-19
read the above edit, you CANT use anyone but BT as your line provider with aol. :(

I double checked their small print and even went as far to call them..BT only


@ coffeecat: try most providers and you will get the same response, I think Plusnet are an exception to this.
Crazy considering how many servers actually use linux and the increasing home linux userbase.

---

### Post by coffeecat on 2011-08-19
> **Matt__ said:**
> read the above edit, you CANT use anyone but BT as your line provider with aol. :(

I double checked their small print and even went as far to call them..BT only

That's extraordinary. Is there a reason for this? I'm with Zen (expensive but excellent) and I can migrate to them for phone as well if I want. BT wholesale will still maintain the line, of course, but that's virtually a separate company from the BT retail you and I deal with.

> **Matt__ said:**
> @ coffeecat: try most providers and you will get the same response, I think Plusnet are an exception to this.
Crazy considering how many servers actually use linux and the increasing home linux userbase. 

I know, but it's still no excuse. It's lowest common denominator customer support with ill-trained non-techies reading from scripts. Both my present ISP, Zen, and my previous (Eclipse) would give me the "Linux not officially supported" line, but as their technical support guys are real techies, I found I was able to have an intelligent conversation with them and tell them I was using Linux on the few occasions I needed to talk to them. Zen actually give you a choice of Linux or Windows servers for their virtual hosting service. Guess which is cheaper. :)

---

### Post by Sussex on 2011-08-19
> **Matt__ said:**
> [COLOR=Red]//EDIT: you changed line provider? to who? as far as I know you CANT do that with aol, it must be BT..something to do with pppoe I think.[/COLOR]

The following settings need to be used in the UK
access this by typing 192.168.0.1 into your browser address bar
put in your router user name and pass (default is username is admin (or administrator)  and default password is password):


_BASIC SETTINGS_
encapsualtion = PPPoE
login = <yourphonenumber>@dialbb.com
password = your master screen name password [COLOR=Navy](caveat: sometimes this fails...you will need to ask for a new setup pass from aol..and wait a couple of hours before they reset it)[/COLOR]
dynamic ip
auto dhcp
enable NAT

_ADSL settings_
multiplex = LLC based
vpi = 0
vci = 38

_Wireless settings_
region = europe
channel = Aol insist that you use channel 11 preferably or 7...why I dont know..I didnt and still the router worked.
enable access point and broadcast of ssid.
mode g & b

start off with NO security to see if you can get it running. try to connect and be sure to check the auto connect box in ubuntu network manager.

once set up...reboot both router(hard reboot..turn off and unplug) and pc 
.


Thanks Guys worked a treat!!

Sussex

---

