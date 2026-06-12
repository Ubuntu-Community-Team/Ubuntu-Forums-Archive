---
title: "Broadband ADSL problem"
date: 2005-10-05
forum: Networking &amp; Wireless
---

### Post by swong1 on 2005-10-05
This is a continuation from a previous thread [http://ubuntuforums.org/showthread.php?t=69247](http://ubuntuforums.org/showthread.php?t=69247).
I recently installed broadband at my home. The modem/router is connected directly to my ethernet port. It works in Windows XP, but not in Ubuntu. Here is what I have done so far:
1. *sudo pppoeconf*. Go through the setup process.
2. *sudo pon dsl-provider*.
3. Added a line "*prepend domain-name-servers xxx.xxx.xxx.xxx;*" to the file /etc/dhcp3/dhclient.conf, where xxx.xxx.xxx.xxx is the primary DNS address of my isp. This adds the DNS address to the file /etc/resolv.conf. Previously, I added the DNS address to the file /etc/resolv.conf by editing the file, but for some reason, it kept reverting back to the old file everytime I start a new connection.
4. Open firefox. Type "about:config" in the address bar, type "ipv6" in the new search bar, set the "disable-ipv6" from "false" to "true".
It is still not working. The network connection icon shows that the connection is on, but I couldn't connect to the internet. Here is a summary of some of the error messages I got:
1. *ping -c 3 [www.google.com](www.google.com)*:
> unknown host [www.google.com](www.google.com)
2. *plog*:
> local host pppd [8025]: using interface ppp0
local host pppd [8025]: connect: ppp0 <--> eth0
local host pppd [8025]: couldn't increase MTU to 1500
local host pppd [8025]: couldn't increase MRU to 1500
local host pppd [8025]: remote message: unable to authenticate
local host pppd [8025]: PAP authentication failed
local host pppd [8025]: connection terminated
3. *ifconfig eth0*:
> Link encap: Ethernet            HWaddr 00:12:3F:d6:C8:28
inet addr: 192.168.1.2          Bcast: 192.168.1.255         Mask:255.255.255.0
BROADCAST MULTICAST        MTU:1500                Metric:1
RX packets:27    errors:0    dropped:0     overruns:0     frame:0
TX packets:66    errros:0    dropped:0     overruns:0     frame:0
collisions:0         txqueuelen:1000
RX bytes: 1768 (1.7KiB)       TX bytes: 4604 (4.4KiB)
Interrupt:18
Incidently, 192.168.1.2 is not the DNS address of my isp.
4. *ifup eth0*:
> interface eth0 already configured.
5. *ifdown eth0*:
> sit0: unknown hardware address type 776
Listening on LPF/eth0/00:12:3f:d6:cb:28
Sending on  LPF/eth0/00:12:3f:d6:cb:28
Sending on Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
6. *dmesg*
> b44: eth0: transmit timed out, resetting
b44: eth0: Link is down
eth0: no IPv6 routers present
b44: eth0: Link is up at 100Mbps, full duplex
b44: eth0: Flow control is on for TX and on for RX
Please help me make sense of these messages. What is the problem? Is it because of the modem? Do I need to download a driver? Did I not enter the right password during *pppoeconf* configuration? I downloaded a soft modem ([http://ubuntuforums.org/showthread.php?t=50810](http://ubuntuforums.org/showthread.php?t=50810)) for the dialup not long ago, is it interfering with the broadband connection? Thanks!

---

### Post by swong1 on 2005-10-06
Any help would be much appreciated. Thanks!

---

### Post by GTvulse on 2005-10-06
```
local host pppd [8025]: using interface ppp0
local host pppd [8025]: connect: ppp0 <--> eth0
local host pppd [8025]: couldn't increase MTU to 1500
local host pppd [8025]: couldn't increase MRU to 1500
local host pppd [8025]: remote message: unable to authenticate
local host pppd [8025]: PAP authentication failed
local host pppd [8025]: connection terminated
```

Did you add your identification info, username and password, to /etc/ppp/pap.secrets?

You are not logging in because because you are **not** logging in as the above shows... :-)

---

### Post by swong1 on 2005-10-07
[QUOTE=dradul]```
local host pppd [8025]: using interface ppp0
local host pppd [8025]: connect: ppp0 <--> eth0
local host pppd [8025]: couldn't increase MTU to 1500
local host pppd [8025]: couldn't increase MRU to 1500
local host pppd [8025]: remote message: unable to authenticate
local host pppd [8025]: PAP authentication failed
local host pppd [8025]: connection terminated
```

Did you add your identification info, username and password, to /etc/ppp/pap.secrets?

You are not logging in because because you are **not** logging in as the above shows... :-)[/QUOTE]

Thanks Dradul, for your tip. I checked the file, the correct username and password are present.  Any other ideas?:(

---

### Post by GTvulse on 2005-10-07
Well, I'm as befuddled as you are. :-( I wonder if hardwiring the MTU and MRU to a lower value (1492 is recommended for pppoe) could help; your ISP may be at fault in this trouble of yours....

---

### Post by swong1 on 2005-10-08
[QUOTE=dradul]Well, I'm as befuddled as you are. :-( I wonder if hardwiring the MTU and MRU to a lower value (1492 is recommended for pppoe) could help; your ISP may be at fault in this trouble of yours....[/QUOTE]

How do I hardwire the MTU and MRU to a lower value? Do I need to dismantle the modem? I will also try to contact my isp and see if they could help. Thanks!

---

### Post by GTvulse on 2005-10-08
You don't need to hack your modem ;-) You set up a couple of settings in your /etc/ppp/peers/<your_isp> file, namely add:
```

mru 1492
mtu 1492

```
or modify them if they are already there. Read the pppd(1) man page[1] for all the gory details. 

By the way, perhaps [this thread ]("http://ubuntuforums.org/showthread.php?p=393920")may give you a clue on how to solve your problem (check [the bugzilla entry]("https://bugzilla.ubuntu.com/show_bug.cgi?id=10334") mentioned there too).

[1] ```
man pppd
``` in a terminal window.

---

### Post by mips on 2005-10-08
I read your previous post as well and I still dont know whether you have a router or a modem but it sounds like a router.

If it is in fact a router why would you want to load PPPoE on your OS ???
How is it configured in Windows ???

If it is a router I would go into it's setup, ensure it is taken out of bridged mode and then simply configure your TCP/IP settings for your Ethernet card to use DHCP and auto DNS. Simple as that.

Can you give us a link/URL to the supplier of this router/modem ???

---

### Post by GTvulse on 2005-10-08
[quote=mips]If it is in fact a router why would you want to load PPPoE on your OS ???
How is it configured in Windows ???

If it is a router I would go into it's setup, ensure it is taken out of bridged mode and then simply configure your TCP/IP settings for your Ethernet card to use DHCP and auto DNS. Simple as that.[/quote]
There is a tendency among ISPs to give locked down xDSL bridges (there is no such things as an aDSL modem or an aDSL router), in [RFC 1483]("http://www.faqs.org/rfcs/rfc1483.html") bridged mode. That way the device makes a **physical link** to the ISPs network on start up but no **data link** (PPPoE, PPPoATM, whatever), The creation of a data link is left to software running in the OS.

As you don't have the administration username and password to the aDSL bridge, you can't take advantage of its capabilities to use NAT, firewalling nor create data links automatically (that is, log in automatically to the ISPs network).

---

### Post by mips on 2005-10-08
[QUOTE=dradul]There is a tendency among ISPs to give locked down xDSL bridges (there is no such things as an aDSL modem or an aDSL router), in [RFC 1483]("http://www.faqs.org/rfcs/rfc1483.html") bridged mode. That way the device makes a **physical link** to the ISPs network on start up but no **data link** (PPPoE, PPPoATM, whatever), The creation of a data link is left to software running in the OS.

As you don't have the administration username and password to the aDSL bridge, you can't take advantage of its capabilities to use NAT, firewalling nor create data links automatically (that is, log in automatically to the ISPs network).[/QUOTE]

That tendancy depends pretty much on where in the world you live. In his original post he specified that the bottom of the device states modem/router. Modem/Router are terms generally used by the public, the majority of the public dont study RFC's and use the correct terminology.

I'm just trying to establish what type of device swong1 has, nothing more nothing less....


[COLOR="Red"]swong1:[/COLOR]  Who is your ISP ???

---

### Post by swong1 on 2005-10-09
[QUOTE=mips]That tendancy depends pretty much on where in the world you live. In his original post he specified that the bottom of the device states modem/router. Modem/Router are terms generally used by the public, the majority of the public dont study RFC's and use the correct terminology.

I'm just trying to establish what type of device swong1 has, nothing more nothing less....


[COLOR="Red"]swong1:[/COLOR]  Who is your ISP ???[/QUOTE]

Hi dradul, mips,

Thanks very much for your replies. As mips guessed, I am not physically in the U.S. I am in Malaysia, my isp (you probably haven't heard of) is tmnet. The 'modem' (so it says on the package: ADSL modem) they provided me is a ZXDSL 831 ([http://www.zte.com.cn/English/03product/open1.jsp?ID=936](http://www.zte.com.cn/English/03product/open1.jsp?ID=936)). It is embarassing, but I really don't know the difference between a modem, bridge and router. I only know what a modem does.

I added the lines:
mtu 1492
mru 1492
to the file /etc/ppp/peers/dsl-provider. Still no luck:( 

Under Windows XP, the only thing we need to do is provide the username and password.

---

### Post by mips on 2005-10-09
[QUOTE=swong1]Hi dradul, mips,

Thanks very much for your replies. As mips guessed, I am not physically in the U.S. I am in Malaysia, my isp (you probably haven't heard of) is tmnet. The 'modem' (so it says on the package: ADSL modem) they provided me is a ZXDSL 831 ([http://www.zte.com.cn/English/03product/open1.jsp?ID=936)](http://www.zte.com.cn/English/03product/open1.jsp?ID=936)). It is embarassing, but I really don't know the difference between a modem, bridge and router. I only know what a modem does.

I added the lines:
mtu 1492
mru 1492
to the file /etc/ppp/peers/dsl-provider. Still no luck:( 

Under Windows XP, the only thing we need to do is provide the username and password.[/QUOTE]

The link provided does not seem to work, right now anyway.

I Googled the 'ZXDSL 831' and found a lot of hits. Looks like it is manufactured by   [www.zte.com.cn](www.zte.com.cn)

It looks like you are in luck as you should be able to configure it for PPPoE, DHCP, DNS etc from the links I saw.

I will carry on looking to see if I can find a configuration manual. Most of these devices alow you to do a 'reset to factory defaults', connect to it, do the config and hopefully problem solved. Will keep you posted.

[http://www.zte.com.cn/English/03product/open1.jsp?ID=936](http://www.zte.com.cn/English/03product/open1.jsp?ID=936)
[http://www.chipweb.de/dsl/index.php?menu=2&id2=107](http://www.chipweb.de/dsl/index.php?menu=2&id2=107)
[http://www.portforward.com/zte/ZXDSL831.htm](http://www.portforward.com/zte/ZXDSL831.htm)

Cheers
mips

---

### Post by mips on 2005-10-09
swong1,

You can download the manual here:
[http://ensupport.zte.com.cn/ensupport/WebForm/unlogin/adsl/adslBook.aspx?count=Y](http://ensupport.zte.com.cn/ensupport/WebForm/unlogin/adsl/adslBook.aspx?count=Y)

This site might require MS Internet Explorer as it does not seem to work with my FireFox browser.

There are two versions of the manual, I think you will only require the one for Malaysia but get both just in case one is better than the other.

The following site explains how to get into the router:
[http://www.portforward.com/english/routers/port_forwarding/ZTE/ZXDSL831/default.htm](http://www.portforward.com/english/routers/port_forwarding/ZTE/ZXDSL831/default.htm)

---

### Post by lordnikotine on 2005-10-09
mips,

i also have the same problem/same hardware/differrent location.....
i cant connect to the internet with Ubuntu but i am now connected to the internet with a M$ PC... i am trying to change my OS right now but i cant connect to the internet with the Ubuntu OS....

could you help me... any step-by-step guide, from the first thing to do... i already finished installing Ubuntu, checked that the eth0 is active....

thanks!

BTW: im noob in NETWORKING and LINUX...:(

---

### Post by mips on 2005-10-09
swong1,

There is light at the end of the tunnel ;)

Scroll down to the 5th posts on the link below:
[http://forum.lowyat.net/index.php?showtopic=61699](http://forum.lowyat.net/index.php?showtopic=61699)

Please note the last post on the link below:
[http://mybug.hostsync.net/search.php?search_author=jsthean&sid=2d58e42a4feabc3a17b385557edb5832](http://mybug.hostsync.net/search.php?search_author=jsthean&sid=2d58e42a4feabc3a17b385557edb5832)

> Hi all,
The VPI/VCI values for streamyx is 0/35. It's the same everywhere in Malaysia for Streamyx EXCEPT for Putrajaya. They're using Siemens DSLAM there and the VPI/VCI for home/SOHO is 130/32.


The link below will also be of assistance:
[http://www.dslreports.com/forum/remark,11656435~mode=flat](http://www.dslreports.com/forum/remark,11656435~mode=flat)

Once you have done all the above all you have to do is configure your Network Cards TCP/IP settings for DHCP & DNS. No need to run any PPPoE clients etc !!!

Hope this helps and let us know how it goes.
More infos here  [http://www.dslreports.com/nsearch?boardlist=216&cat=remark&advanced=1&216=1&p=10&o=r&q=zte](http://www.dslreports.com/nsearch?boardlist=216&cat=remark&advanced=1&216=1&p=10&o=r&q=zte)

---

### Post by mips on 2005-10-09
[QUOTE=lordnikotine]mips,

i also have the same problem/same hardware/differrent location.....
i cant connect to the internet with Ubuntu but i am now connected to the internet with a M$ PC... i am trying to change my OS right now but i cant connect to the internet with the Ubuntu OS....

could you help me... any step-by-step guide, from the first thing to do... i already finished installing Ubuntu, checked that the eth0 is active....

thanks!

BTW: im noob in NETWORKING and LINUX...:([/QUOTE]


lordnikotine,

Who is your ISP ?  Please provide link/URL !!!
What service are you using ?  Please provide link/URL !!!


The same procedure as above would apply to you only thing is the parameters will most likely change.

So we need to find the default username/password, Encapsulation type, VPI/VCI and DNS information for your ISP/Telco.

---

### Post by swong1 on 2005-10-10
[QUOTE=mips]The link provided does not seem to work, right now anyway.

I Googled the 'ZXDSL 831' and found a lot of hits. Looks like it is manufactured by   [www.zte.com.cn](www.zte.com.cn)

It looks like you are in luck as you should be able to configure it for PPPoE, DHCP, DNS etc from the links I saw.

I will carry on looking to see if I can find a configuration manual. Most of these devices alow you to do a 'reset to factory defaults', connect to it, do the config and hopefully problem solved. Will keep you posted.

[http://www.zte.com.cn/English/03product/open1.jsp?ID=936](http://www.zte.com.cn/English/03product/open1.jsp?ID=936)
[http://www.chipweb.de/dsl/index.php?menu=2&id2=107](http://www.chipweb.de/dsl/index.php?menu=2&id2=107)
[http://www.portforward.com/zte/ZXDSL831.htm](http://www.portforward.com/zte/ZXDSL831.htm)

Cheers
mips[/QUOTE]

Silly me, I accidently put the bracket within the url quotation, that's why the link wasn't working. It has now been corrected. The link is the same as the first one you provided. The website originates from China, loading may be slow.

> There is light at the end of the tunnel

Scroll down to the 5th posts on the link below:
[http://forum.lowyat.net/index.php?showtopic=61699](http://forum.lowyat.net/index.php?showtopic=61699)

Please note the last post on the link below:
[http://mybug.hostsync.net/search.php...b385557edb5832](http://mybug.hostsync.net/search.php...b385557edb5832)

Quote:
Hi all,
The VPI/VCI values for streamyx is 0/35. It's the same everywhere in Malaysia for Streamyx EXCEPT for Putrajaya. They're using Siemens DSLAM there and the VPI/VCI for home/SOHO is 130/32.


The link below will also be of assistance:
[http://www.dslreports.com/forum/rema...6435~mode=flat](http://www.dslreports.com/forum/rema...6435~mode=flat)

Once you have done all the above all you have to do is configure your Network Cards TCP/IP settings for DHCP & DNS. No need to run any PPPoE clients etc !!!

Hope this helps and let us know how it goes.
More infos here [http://www.dslreports.com/nsearch?bo...p=10&o=r&q=zte](http://www.dslreports.com/nsearch?bo...p=10&o=r&q=zte)


Wow! Thanks for digging up so much reading material. The websites you provided seems to describe a method of converting the zte zxdsl 831 modem into a router. I don't know if this solves the problem since I can connect to the internet without any modification under Windows. But I will try the hack and see if it solves the problem in Ubuntu.

Okay, here's what I did. I followed the process described in the thread [http://forum.lowyat.net/index.php?showtopic=61699](http://forum.lowyat.net/index.php?showtopic=61699). The settings I chose are:

VPI = 0. 
VCI = 35.
Protocol : PPPoE (disable Bridging).
WAN IP settings : obtain IP address automatically
                      : Enable NAT
LAN IP settings : Primary IP address : 192.168.1.1
                       Subnet Mask         : 255.255.255.0
                       Host Name            : ZXDSL831
                       Domain Name         : home
                       DHCP server          : disabled

I then went to the Local Area Connection TCP/IP properties (in Windows) and set the addresses as follows:

IP address: 192.168.1.2
Subnet Mask : 255.255.255.0
Default Gateway : 192.168.1.1

Preferred DNS server : 202.188.0.133
Alternate DNS server : 202.188.1.5

I followed the instructions in the thread as closely as possible. As I do not understand what exactly I am doing, some of the settings could be in conflict with each other. For example, in WAN settings, ip address is obtained automatically, but in LAN, DHCP is disabled.

I rebooted into Ubuntu. Tried both static and DHCP, with and without pon dsl-provider, nothing works.:(

---

### Post by mips on 2005-10-10
swong1,

Did you apply/save the changes & reboot the router ?

What you did seems more or less correct. What we are trying to do is to let the router handle the PPPoE stuff & login to the net automatically. That way you dont need any PPPoE stuf + Login on the PC. It is then transparrent and it makes it very easy to connect a PC. With an optional switch/hub you can then connect multiple PC's at once with any OS you want and it just needs an IP address/DNS/Default Gateway to work.

Can I suggest you join that forum + the other one with a procedure. Ask the local people in your country for help as it is very hard for me to tell you what to do because I'm not familair with your hardware or ISP settings. I'm sure people on those boards will be able to help you get it right. Please also read through all the posts as some later posts mention people with problems & solutions.

Check the routers log and see if it is indeed establishing a connection with your ISP and obtaining an IP address or failing.

I would suggest first testing with windows as I find it easier to change things. Your PC settings seem correct but try them in windows. Can you ping the default gateway ?

I have PM'ed you with my email address. I want you to mail me  screenshots of every single setup tab on your router. It would make it easier for me as I then actually have something to look at.

Try contacting your ISP and explain to them that you want to convert from bridged to router mode. Maybe, just maybe someone at the ISP has done it before.

Waiting to hear from you.

---

### Post by swong1 on 2005-10-10
Dear mips,

Thanks for your suggestions. You have provided tremendous amount of help. I will certainly follow up on some of the local threads. I have also sent you the screenshots. Yes, I did save the settings. I will post my findings if I'm successful.

---

### Post by mips on 2005-10-10
Hi swong1,

I just checked my mail and have not received anything yet. Will check again later and let you know if i received it.

cheers
mips

---

### Post by mips on 2005-10-11
swong1,

I have received no mail from you. Will PM you.

Cheers
mips

---

### Post by swong1 on 2005-10-11
Dear mips,

I have emailed you the screenshots you requested. Hope it doesn't contain any huge conflicts. I am happy to announce that I finally figured out (sort of) what is wrong with my connection.  Due to the perculiarity of the isp, they appended the username with an extension, that is why they weren't able to authenticate. I only noticed it just now.  #-o  Thank you (and sanjose, dradul) for all your help.[-o< 

I do have a question though. *ifconfig* gives the following output

> eth0      Link encap:Ethernet  HWaddr 00:12:3F:D6:CB:28
          inet6 addr: fe80::212:3fff:fed6:cb28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1425359 (1.3 MiB)  TX bytes:444454 (434.0 KiB)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4089 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4089 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:326061 (318.4 KiB)  TX bytes:326061 (318.4 KiB)

ppp1      Link encap:Point-to-Point Protocol
          inet addr:218.111.163.250  P-t-P:219.93.218.177  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:1277276 (1.2 MiB)  TX bytes:222283 (217.0 KiB)



The output for eth0 is still the same as before, the only difference is, previously absent ppp1 (ppp0 was configured for dialup) is now added to the list of network connections. Previously, I had ppp0, eth0 (ethernet) and eth1 (wireless). Is this normal?

By the way, DHCP seems to work just fine. I don't have to specify ip address, subnet mask and gateway.

---

### Post by adwait on 2005-10-11
Yes, you are using PPPoE to connect to your ADSL provider.....

---

### Post by mips on 2005-10-11
I was looking at your config and noticed that your username was not a appended by @domain.net or whatever as in my country. I thought nah, just because they do it here does not mean they do it there. They use the extension in order for the BRAS to distingius traffic for different ISP's & package types etc.

To be honest I'm not sure about the PPP1 interface but I think it is OK. Unfortunately I cannot check on my PC as my ADSL router was struck by lightning 2weeks ago and I sent it in for replacement. I can check for you later when I get my new ADSL router if that is OK.


So does this mean everything is working on Ubuntu & Windoze ???



[quote=swong1]Dear mips,

I have emailed you the screenshots you requested. Hope it doesn't contain any huge conflicts. I am happy to announce that I finally figured out (sort of) what is wrong with my connection. Due to the perculiarity of the isp, they appended the username with an extension, that is why they weren't able to authenticate. I only notice it just now. #-o  Thank you (and sanjose, dradul) for all your help.[-o< 

I do have a question though. *ifconfig* gives the following output



The output for eth0 is still the same as before, the only difference is, previously absent ppp1 (ppp0 was configured for dialup) is now added to the list of network connections. Previously, I had ppp0, eth0 (ethernet) and eth1 (wireless). Is this normal?

By the way, DHCP seems to work just fine. I don't have to specify ip address, subnet mask and gateway.[/quote]

---

### Post by swong1 on 2005-10-11
> So does this mean everything is working on Ubuntu & Windoze ???

Yes! Everything seems to be working. Until next time.....

Thanks again. Sorry about your fried router, mips.

Thanks adwait.

---

