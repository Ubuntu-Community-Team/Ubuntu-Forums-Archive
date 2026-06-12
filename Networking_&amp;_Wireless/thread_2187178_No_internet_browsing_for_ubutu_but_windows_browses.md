---
title: "No internet browsing for ubutu but windows browses normally (dual boot)"
date: 2013-11-11
forum: Networking &amp; Wireless
---

### Post by mummak on 2013-11-11
Hey all.

I use a dual boot system, and what happens is windows gets connection and can browse normally, using google chrome.
Ubuntu gets connected, but I cant browse anything at all. I use chromium and firefox, none of them works, both display website is unavaillable.

This started to happen since I arrived here in Rwanda. I was in South Africa b4 and all was working well. I have not tried to connect to any other access points apart from this access point mentioned below.

The router is a ZTE OX253P
I can get inside it via windows, but not via ubuntu.
In ubuntu, if I try to access it, chromium does not work at all, and firefox asks for password and user, which I fill in but it keeps loading for ever.

My network interface card is broadcom 803.22 g

Since I started using ubuntu I never went back to windows (salve on occasion like this) and using ubuntu for internet browsing is really important for me (safety and comfort reasons)...so,
can anyone help me? anyone have any idea on how to fix this?

thank you very much in advance

---

### Post by phaenze on 2013-11-11
Hi,

I have a couple of questions.
1. When start Firefox under Ubuntu and try to get to a site on the internet (e.g. google.com), are you given a login page to access the wireless network? (I'm presuming from your email that you are using a wifi connection)?
2. Are you using DHCP to get an ip address under both Windows and Ubuntu? If so, check that DHCP under Ubuntu is set up the same as Windows.
3. Under "Connection Information" under Network Manager, what is your ip, default gateway and DNS?

You can try to see if your network is working correctly under Ubuntu. Open a terminal and try the following commands. Note where it fails:
1. **ping 127.0.0.1**
2. **ping localhost**
3. Ping your network address as shown in question 3 - e.g. **ping 192.168.0.2** (replace the ip address with yours)
4. Ping your default gateway as shown in question 3 - e.g. **ping 192.168.0.1** (replace the ip address with yours)
5. Ping you primary DNS server as shown in question 3 - e.g. **ping 208.67.222.123** (replace the ip address with yours)
6. Ping your secondary DNS server as shown in question 3 - e.g. **ping 208.67.220.123** (replace the ip address with yours)
7. **ping 173.194.43.102** (This is a google.com address.)
8. **ping google.com**

Let me know if it failed at one of the above steps - and where.

Peace,
Paul :cool:

---

### Post by mummak on 2013-11-13
Hi Paul! Thank you much for replying!


Yes, I am trying to get a wifi connection. It is the open wifi of the NGO where I am stayin. Yesterday I got the chance to connect the cable to it and it did not work either :/


As for your questions, here we go:


1. When I start FIREFOX it does not ask for any password. Instead, it keeps tryng to load for long time then displays:


Server not found
Firefox can't find the server at [www.google.com](www.google.com)


2. I have no idea if I am using DHCP, but I will try to check this. How do I get both settled the same way?


3. See picture below, here's all my connection info:

[http://helpmiii.blogspot.com/](http://helpmiii.blogspot.com/)


As for the other questions:


**1. ping 127.0.0.1 [COLOR=#ff0000]> seems to be normal, here is the output:[/COLOR]**


PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_req=1 ttl=64 time=0.059 ms
64 bytes from 127.0.0.1: icmp_req=2 ttl=64 time=0.052 ms
64 bytes from 127.0.0.1: icmp_req=3 ttl=64 time=0.056 ms
64 bytes from 127.0.0.1: icmp_req=4 ttl=64 time=0.064 ms
64 bytes from 127.0.0.1: icmp_req=5 ttl=64 time=0.056 ms
64 bytes from 127.0.0.1: icmp_req=6 ttl=64 time=0.057 ms
64 bytes from 127.0.0.1: icmp_req=7 ttl=64 time=0.052 ms
^C
--- 127.0.0.1 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 5998ms
rtt min/avg/max/mdev = 0.052/0.056/0.064/0.008 ms






**2. ping localhost**


PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.045 ms
64 bytes from localhost (127.0.0.1): icmp_req=2 ttl=64 time=0.048 ms
64 bytes from localhost (127.0.0.1): icmp_req=3 ttl=64 time=0.057 ms
^C
--- localhost ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.045/0.050/0.057/0.005 ms


**3. Ping your network address as shown in question 3 - e.g. ping 192.168.0.2 (replace the ip address**
**with yours)**


PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=254 time=1.36 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=254 time=1.39 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=254 time=1.43 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=254 time=1.49 ms
^C
--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 1.364/1.420/1.496/0.056 ms




**4. Ping your default gateway as shown in question 3 - e.g. ping 192.168.0.1 (replace the ip address**
**with yours)**


PING 192.168.1.4 (192.168.1.4) 56(84) bytes of data.
64 bytes from 192.168.1.4: icmp_req=1 ttl=64 time=0.053 ms
64 bytes from 192.168.1.4: icmp_req=2 ttl=64 time=0.050 ms
64 bytes from 192.168.1.4: icmp_req=3 ttl=64 time=0.057 ms
^C
--- 192.168.1.4 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.050/0.053/0.057/0.006 ms




**5. Ping you primary DNS server as shown in question 3 - e.g. ping 208.67.222.123 (replace the ip**
**address with yours) [COLOR=#ff0000]> this kept forever until I stopped it[/COLOR]**


moreon@8D:~$ ping 192.168.1.255
Do you want to ping broadcast? Then -b
moreon@8D:~$ ping -b 192.168.1.255
WARNING: pinging broadcast address
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.
^C
--- 192.168.1.255 ping statistics ---
94 packets transmitted, 0 received, 100% packet loss, time 93137ms






**6. Ping your secondary DNS server as shown in question 3 - e.g. ping 208.67.220.123 (replace the**
**ip address with yours)**


it has the same ip address of the router, 192.168.1.1


**7. ping 173.194.43.102 (This is a google.com address.)**


PING 173.194.43.102 (173.194.43.102) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=1 Destination Host Unreachable
From 192.168.1.1 icmp_seq=2 Destination Host Unreachable
From 192.168.1.1 icmp_seq=3 Destination Host Unreachable
From 192.168.1.1 icmp_seq=4 Destination Host Unreachable
From 192.168.1.1 icmp_seq=5 Destination Host Unreachable
From 192.168.1.1 icmp_seq=6 Destination Host Unreachable
From 192.168.1.1 icmp_seq=7 Destination Host Unreachable
From 192.168.1.1 icmp_seq=8 Destination Host Unreachable
^C
--- 173.194.43.102 ping statistics ---
8 packets transmitted, 0 received, +8 errors, 100% packet loss, time 7010ms


**8. ping google.com > [COLOR=#ff0000]took very long time[/COLOR]**


ping: unknown host google.com



**#############################################################**


So, I am not an internet expert. But my guess, so far, from all the information you gave me is that I can connect to the router and access point but not to any website on the internet..


Curiously, sometimes browsing in ubuntu WORKED AFTER i turned windows on, surfed in windows for a while, and then reboot into ubuntu. That s so awkward..:/


Thank you again!
Bests,
Gus

---

### Post by phaenze on 2013-11-13
Hi Gus,

Try ping the address 10.0.3.176 (i.e. **ping 10.0.3.176**). That's the ip address of the router on the wan side. This will let us know whether you are able to get out of the subnet.

Looking over your notes, I wanted to clarify your various addresses:
1. Machine address: 192.168.1.4
2. Default gateway: 192.168.1.1
3. Primary DNS: 192.168.1.1

The address 192.168.1.255 is not a valid address for your subnet.

So let's try something a little different:
[LIST=1]
[*]Boot into ubuntu.
[*]Release and renew your IP address by running the following: **sudo dhclient -r** and then **sudo dhclient**.
[*]**ping 192.168.1.1**
[*]**ping 10.0.3.176**
[*]**ping 91.189.94.156** (This is an address for ubuntu.com)
[/LIST]

Let me know if and where it fails.

Peace,
Paul :cool:

---

### Post by mummak on 2013-11-14
Hi Paul! thank you again for answering and the clarifications about the ip addresses.

Well, here is the result to the commands:

**moreon@8D:~$ ping 10.0.3.176**
PING 10.0.3.176 (10.0.3.176) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=1 Destination Host Unreachable
From 192.168.1.1 icmp_seq=2 Destination Host Unreachable
^C
--- 10.0.3.176 ping statistics ---
2 packets transmitted, 0 received, +2 errors, 100% packet loss, time 1001ms


**moreon@8D:~$ sudo dhclient -r**
[sudo] password for moreon: 
**moreon@8D:~$ sudo dhclient**
**moreon@8D:~$ ping 192.168.1.1[COLOR=#ff0000] > SINCE this did not work, I supposed none of the other would, anyway...[/COLOR]**
connect: Network is unreachable
**moreon@8D:~$ ping 10.0.3.176**
connect: Network is unreachable
**moreon@8D:~$ ping 91.189.94.156**
connect: Network is unreachable
moreon@8D:~$ 


[B]###################################################

It seems I cannot connect to the router itself. Weird. Btw, I am now using ubuntu, but from my phone as an AP..it connects normally..

Peace to you too!
Gus[/B]

---

### Post by phaenze on 2013-11-14
After you did the sudo dhclient, did you check to see if you had received an IP address? Also, I forgot to ask what version of Ubuntu you were using. There's a bug in 13.10 that it won't properly reconnect after a suspend. You may want to try the command sudo restart network-manager and see if that knocks anything loose. 

Unfortunately, I'm on the road, so won't be able to contact you until Monday. Sorry that you are having problems.

Paul

---

### Post by mummak on 2013-11-16
Hi Paul!


Thank you again for your support. Dont worry about being away, have a nice weekend on the road!


My ubuntu is Release 12.04 (precise) 32-bit


I have checked the ip addresss, it seems normal.
Looking at these pictures:
[http://helpmiii.blogspot.com]("http://helpmiii.blogspot.com/")
> the flow of data is extremely low, around 0,3 kb/s

I tried your commands, they did not work.

Then I tried:

sudo dhclient -x
sudo dhclient -r
sudo dhclient

Did not work either.
Then went off to sleep, and after 2 hours woke up.

just a curiosity, I am now using ubuntu with the AP and it is working, but this is just...random...if I boot it wont work anymore I guess

btw, I also have n android phone that cannot surf on the same wifi.


Bests!
Gus

---

### Post by phaenze on 2013-11-20
Sorry, but I'm out of ideas. My guess is that there is something with the firmware on the router/access point. When I have had this weird stuff happen in the past, I was able to surf once I restarted the router/access point. I was also able to replace the router at a friends house, flash it with dd-wrt and never saw the issue arise again.

Peace,
Paul :cool:

---

### Post by mummak on 2013-11-23
Hi Paul!

I believe you are right...anyway, I am now getting internet in Ubuntu. But not normally. I have to boot into ubuntu, and the around 30 min later the internet wifi works. Odd..

I will see what I can do towards the firmware and router ap..
And thank you for all help!

Bests
Gus

---

