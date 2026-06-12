---
title: "no internet  - network configuration query"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by Old Jimma on 2009-08-09
Hi Ubuntu Community:

I'm running Hardy Herron LTS.

Somehow my machine lost the ability to access the internet. I have no idea how this happened.

:(

Could someone please provide advise on how to regain internet access? Perhaps this requires configuring how my machine accesses my home network...

My network looks like this: cable modem > router/switch > computers.

One of the machines I have is and XP machine and has not lost the ability to access the internet.

I will be grateful for your replies... I'll only be able to access your replies one time per day on the XP machine (it belongs to my son!).

Thank you!
Phil Smith
Duluth, GA

---

### Post by powel212 on 2009-08-09
If it were me. I would check all my wires were plugged in. Then I would check them again. Then I would pop a live disk in the computer with no internet access and boot from it. If we can access the internet from the live cd then we know the problem is not hardware or wiring. 

Are you using PPPoe or dial up of any kind?

In answer to your question. Samba, (home networking), should have no affect on accessing the internet. But a firewall certainly could. If you have recently installed a firewall, try disabling it and see if that helps.

Powel

---

### Post by pedro3005 on 2009-08-09
Could you post the output of 'ifconfig' (run on a terminal)?

---

### Post by Old Jimma on 2009-08-09
Hi Powel212 and Pedro3005:

Thanks for your replies. Here are point-by-point replies to your queries:

**For Powel212**
[LIST]
[*]I checked the wire connections used by my Ubuntu machine with my son's XP machine... the XP machine can access the internet using the wire connections used by the Ubuntu machine.
[*]Not sure what PPPoe is.  I use a cable modem.
[*]I used synaptic to check that firestarter is not installed. This confirmed that firestarter is not installed.
[*] I got a live CD for Hardy LTS... I cannot access the internet with the live CD.
[/LIST]

**For Pedro3005**
Here are the results from the ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:15:f2:9c:e3:63  
          inet6 addr: fe80::215:f2ff:fe9c:e363/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2742 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:178853 (174.6 KB)  TX bytes:6909 (6.7 KB)
          Interrupt:21 Base address:0xa000 

eth0:avahi Link encap:Ethernet  HWaddr 00:15:f2:9c:e3:63  
          inet addr:169.254.9.73  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:170352 (166.3 KB)  TX bytes:170352 (166.3 KB)

Thank you for your replies and help!

All the best,
Phil Smith
Duluth, GA

---

### Post by Michael Dooley on 2009-08-10
Phil:

It looks like you're connected via cable modem to me. However, I just subscribed to comcast last Friday so am almost a complete newbie on network matters. Here is/are the results of the ifconfig command on my main computer (if it will help):

```
eth0      Link encap:Ethernet  HWaddr 00:50:8d:85:29:07  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe85:2907/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:250989 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216667 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:285510157 (272.2 MB)  TX bytes:89618644 (85.4 MB)
          Interrupt:18 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1856 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92800 (90.6 KB)  TX bytes:92800 (90.6 KB)


```

Hopefully someone who knows more than I do will chime in. Good luck Phil.

---

### Post by powel212 on 2009-08-10
If all the wires are plugged in and the live disk also couldn't get access then I am guessing that you may have a kind of dial up cable modem. You can check on your windows box if it is using a user name and password to make its connection to the internet. this is very common. Attached is a pic of where you input the user id and password. Right click on the network icon top right selct edit connection and then dsl and them add. Here you can enter your user name and password. 

However if you find you do not have a user name and password then I would suggest giving your isp a call and see if they can give you an answer.

I hope that helps.

Powel

---

### Post by mapes12 on 2009-08-10
> eth0:avahi Link encap:Ethernet HWaddr 00:15:f2:9c:e3:63
inet addr:**169.254.9.73** Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:21 Base address:0xa000 The number I've highlighted is a none standard private IP address. On your windoze machine Start>Run>cmd>ipconfig and post back the output please.

---

### Post by Old Jimma on 2009-08-10
Hi Mappes:

For my windows machine, the ip address is: 97.80.173.27

Wow! This is a really non-standard IP address.

Phil

ps I have cable modem.

---

### Post by TheForumTroll on 2009-08-10
Well, Im not much of a GUI user for configuring Ubuntu, but if you don't mind using a console, maybe [this post could help you out]("http://ubuntuforums.org/showpost.php?p=7739794&postcount=6").

---

### Post by dj-toonz on 2009-08-10
have you been able to use the Internet in 8.04 before with the same setup i.e the router in place connected to the cable modem? when I first started out with a cable modem I had to release 1 of the machines IP addresses to access the net from any of the other machines as the ISP would only allow 1 machine to access the internet at the time & you had to resister the mac address on the system. That look's like what's happering in your case.  what I would try to do is

1) power down both of the machines
2) power down the Cable modem for about an hour so it release's the IP address (is it a dchp or static ip address)
3) connect the cable modem to the Wan port on the cable modem
4) connect both of the machines to the router
5) power up the cable modem first & let it sync with the ISP
6) power up the router & then the 8.04 Machine & see if you can access the routers config page to see if it's been synced a IP address 
7) then power up windows xp Machine & see if you can connect

If you still cant connect with Ubuntu 8.04 after doing all that but you can with the XP machine (then I haven't got a clue) sorry that's how I did it on mine when I was using Virgin Media a couple of years back 

Hope that helps

---

### Post by juanoleso on 2009-08-10
Connect an ethernet cable from the modem straight to the ubuntu box skipping the router/switch.  If you can access the internet then the router/switch is blocking your ubuntu box or not providing the necessary information for your ubuntu box to connect and you will have to configure your router/switch.  If not, then we know that ubuntu is not configured correctly.

---

### Post by TheForumTroll on 2009-08-10
Changing equipment that is connected directly to the internet may take up to an hour (or more) to work. Some ISPs only allow new MAC addresses to connect with these intervals. So if it do not work right away that might be the reason.

---

### Post by Old Jimma on 2009-08-12
juanoleso:

I have connected my machine directly to my modem, and it still does not work.

Should I reinstall Ubuntu? I tried a live CD, and it could not access the internet, either.

Phil

---

### Post by juanoleso on 2009-08-12
I couldn't say if reinstalling ubuntu will work or not...

It looks like you have tried a lot of this stuff, but I'll just put it out there again for posterity's sake...

Is the cable secure from the ubuntu machine to the router/switch?  Try swapping out the cable with the one on the XP machine.

Your ethernet card and your router/switch should both have blinking lights showing that information is flowing from the router/switch through the cord to the ethernet card (they will blink at about the same time to show packet exchange).  Try a different port on the router/switch, or, if you have an extra, try another ethernet card if those lights aren't blinking.

If you can't get the lights going, then you may have a hardware issue.

After making sure there is a connection, try pinging google: 

```
$ping www.google.com
```

try pinging the address of your son's computer (you can get it from the ipconfig command posted previously).

```
$ping 192.168.0.1
```

Can your router act as a gateway to your modem?  Modern routers should be able to do this and then be setup to act as a DHCP server to your machines (switches may not be able to do this).  If you can, setup your router to act as a gateway and a DHCP server (its going to be different for each router, most home routers have a simple http interface).

If your router can't do this, you may need to contact your ISP or find someone else on the forums who may have more experience.

Best of luck and I'll keep an eye on the thread if I can help anymore!

---

### Post by TheForumTroll on 2009-08-12
Did you try to configure it manually?

---

### Post by mapes12 on 2009-08-13
Those odd IP addresses still bother me. Have you consulted your router user manual to see how it assigns IP addresses. Mine are assigned automatically by DHCP that is set automatically within the router. Most routers assign class C private network addresses to machines _inside_ your LAN. These start with 192. You can check what IP address your ISP provider has allocated to you internet account _outside_ your LAN i.e. on the www by going here: [http://www.whatismyip.com/](http://www.whatismyip.com/) Once you have this info it may be worth a call to you ISP provider tech desk to ask how their configuration is supposed to work, or this info may be on their FAQ section of their website.

If your ISP has some odd IP configuration it could be you ran an installation disk on your XP machine that set up the addresses. That may be why your XP machine works but Ubu is having problems.

---

### Post by Old Jimma on 2009-08-15
Folks:

Here is what solved my problem:

When I replace my modem, I also hit the "reset" button on my router.

What a mistake... All of the DNS servers defined in the router got erased.

WHen I addressed my router and put the opendns server addresses, everything started to work again.

I gratefully thank all who worked hard on this problem. 

Sincerely,
Phil Smith
DUluth, GA

---

