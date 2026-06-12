---
title: "network settings?"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by muggins on 2006-09-20
Can not seem to connect to internet even though everything looks okay. Is there anything in network settings that I should tinker with ie. under the hosts tab? Also under the dns tab everything is blank is this normal? The wlan0 connection says it is active and have tried with wep on and off.

---

### Post by skymt on 2006-09-20
What's your setup like? What kind of WLAN router is it?

---

### Post by kroiz on 2006-09-20
do you have an IP? do "ifconfig" and post it here.
do have access to dns? do "ping www.google.com" and post it here.

---

### Post by muggins on 2006-09-21
> **skymt said:**
> What's your setup like? What kind of WLAN router is it?
  Thanks for the reply. My router is Trendnet TEW432BRP and wireless adapter is Trendnet424UB. Router is connected to adsl and when I am using xp on the wireless I get an excellent mbps rate most of the time. In Ubuntu under network settings wlan0 is active. Have yet to aquire an internet connection after 2 weeks of trying.

---

### Post by muggins on 2006-09-21
> **kroiz said:**
> do you have an IP? do "ifconfig" and post it here.
do have access to dns? do "ping www.google.com" and post it here.
  Thanks for reply. Did ifconfig and first 2 lines read.
   lo   Link encap:Local Loopback
        inet addr:127.0.0.1    mask:255.0.0.o

 wlan0  Link encap:Ethernet HWaddr 00:40:F4:E5:B3:7A
        inet6 addr:fe80:240:f4ff:fee5:b37a/64
    
    When I tried to ping google it said the address could not be found. Not really sure what you mean by access to dns. Under the dns tab in network settings everything is blank.

---

### Post by muggins on 2006-09-23
Still have no internet connection. I am not sure what to do at this point. This is a dual boot machine. I have excellent connection with xp. Is there any further settings I could try in network settings, I'm thinking of either the dns or hosts tabs.

---

### Post by kroiz on 2006-09-26
you do not have an IP, your DHCP on the router should have given you one.
can you ping you router? 
"ping 192.168.1.0"
notice you might have a different router IP.

maybe your wireless adapter is not installed?
please do iwconfig and paste it output here.

---

### Post by muggins on 2006-09-28
Yes I can ping my router using 192.168.1.1

---

### Post by kroiz on 2006-09-28
oh I think you need to enter the dns of your isp in the dns tab.
you can call your isp or usualy find it in their site or just google for it.

---

### Post by bigken on 2006-09-28
you may also need to type about:config in firefox address and ipv6 in the filter bar and change ipv6 from fales to true ;)

---

### Post by muggins on 2006-09-29
I have now changed ipv6 to true. Googled telus dns and put both values under dns tab in network settings. With dhcp enabled I tried mlb.com in firefox and no luck instantly. So I disenabled dhcp and went to static.
  ip address-192.168.1.1
  subnet mask-255.255.255.0
  gateway address-192.168.1.1
Again tried mlb.com and this time actually got the busy icon but after about 1 minute no luck. Do these settings look okay or am I out in left field? Thanks for all the input I am learning a lot in the process, feel like I am getting closer.

---

### Post by bigken on 2006-09-29
> **muggins said:**
> I have now changed ipv6 to true. Googled telus dns and put both values under dns tab in network settings. With dhcp enabled I tried mlb.com in firefox and no luck instantly. So I disenabled dhcp and went to static.
  ip address-192.168.1.1
  subnet mask-255.255.255.0
  gateway address-192.168.1.1
Again tried mlb.com and this time actually got the busy icon but after about 1 minute no luck. Do these settings look okay or am I out in left field? Thanks for all the input I am learning a lot in the process, feel like I am getting closer.

try 192.168.1.2 for your ip address ;)

---

### Post by muggins on 2006-09-30
> **bigken said:**
> try 192.168.1.2 for your ip address ;)
I tried 192.168.1.2 for the ip address and got the same result. Thanks for the suggestion.

---

### Post by kroiz on 2006-09-30
your IP and gateway have the same address.
maybe your gateway should be 192.168.1.0

this is realy taking time to set up isn't it. I wish some one who realy know something about networking could help you.
I am supprised you did not give up already.

It seems these forums are all filled with noobs like me.
I gues all the experts are doing something else.
You should try to get help on the IRC. but dont use the ubuntu channel because it is too fast. look for some general linux channel or networking.

keep us updated please.

---

### Post by Ferk on 2006-10-01
I have exactly the same problem...

I managed to overcome it making a simple script that pings all the adresses in sources.list

It seems that after a ping to the direction, the IP of that site resolves without issues and you dont get that f***ng 1.0.0.0 IP

however I still cant conect bittorrent, azureus nor amule.. nor some other apps..
And the need of the ping script makes installing uncomfortable

I hope we can find a better way

---

### Post by muggins on 2006-10-01
I am starting anew. I have enabled dhcp and turned off wep. In iwconfig I am not associated with my access point and this seems to be a sticking point. Tried to get an ip with wifi radar, no luck. Tried to connect to router using iwconfig command line, it wouldn't let me. What should I try now?

---

### Post by muggins on 2006-10-02
Is it safe to assume that if my wlan0 is active that the wireless usb adapter driver is working properly and I can eliminate it as the problem? Note: it works perfectly when I boot in xp.

---

### Post by kikos on 2006-10-02
You should try to set your wireless interface to static ip, dns, etc to see if that works.  Otherwise, your problem seems to be with dhcp.  dhclient is the program in linux that communicates with the router to get address information.

dhclient records the DHCP lease for each interface in var/lib/dhcp3/dhclient.leases and /var/lib/dhcp3/dhclient.YOUR_INTERFACE.leases

dhclient writes its log to /var/log/daemon.log which may be useful for debugging purposes.

Look in those files to see what's going on.

---

### Post by muggins on 2006-10-02
Thanks for reply kikos. I have tried using a static ip a few times but hasn't worked so far. When I typed in your commands I recieved either no such file or directory and permission denied.

---

### Post by Gotterdammerung on 2006-10-03
same stuff here... I've have never seen it happen in other distros. far to strange. :-k

---

### Post by Gotterdammerung on 2006-10-03
Check out this [thread]("http://www.ubuntuforums.org/showthread.php?t=269746&highlight=network").

---

### Post by muggins on 2006-10-04
> **Gotterdammerung said:**
> Check out this [thread]("http://www.ubuntuforums.org/showthread.php?t=269746&highlight=network").

I took a look at this thread and I am wondering how they did the apt-get upgrade? I am also wondering if reinstalling dapper might work and how I would do that.

---

### Post by muggins on 2006-10-05
iwlist wlan0 scan results:
     Address:00:40:F4:E4:2E:C2
     ESSID:"TRENDnet"
     Protocol:IEEE 802.11g
     Mode:Managed
     Frequency:2.412 GHz
     Encryption key:on

  Still have no connection.

---

