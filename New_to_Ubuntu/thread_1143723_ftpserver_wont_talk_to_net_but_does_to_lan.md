---
title: "ftpserver wont talk to net but does to lan"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by stinger30au on 2009-04-30
im using ubuntu 9.04 and i have installed gadmin-proftp from synaptic

i have got it configured and i can ftp to it across my lan and it does exactly what i want


i have also configured my router, a billion 7402LM with port forwarding to the ip address of this machine forwarding port 21

i have checked my ip with

[http://www.whatsmyip.org/](http://www.whatsmyip.org/)

and i can not ping this ip address either

if i point my ftp client - filezilla to the ip address obtained from the web site it times out

if i go to another location and ping my ip it times out also

i have a static ip as well from my isp

what am i doing wrong???

---

### Post by halitech on 2009-04-30
maybe double check your router setup as something doesn't sound right. If  you can't ping it then its something on the router and not a firewall on your computer.

Maybe this will help:
[http://portforward.com/english/routers/port_forwarding/Billion/Bipac-7402GL/Bipac-7402GLindex.htm](http://portforward.com/english/routers/port_forwarding/Billion/Bipac-7402GL/Bipac-7402GLindex.htm)

---

### Post by alphacrucis2 on 2009-04-30
> **stinger30au said:**
> im using ubuntu 9.04 and i have installed gadmin-proftp from synaptic

i have got it configured and i can ftp to it across my lan and it does exactly what i want


i have also configured my router, a billion 7402LM with port forwarding to the ip address of this machine forwarding port 21

i have checked my ip with

[http://www.whatsmyip.org/](http://www.whatsmyip.org/)

and i can not ping this ip address either

if i point my ftp client - filezilla to the ip address obtained from the web site it times out

if i go to another location and ping my ip it times out also

i have a static ip as well from my isp

what am i doing wrong???

On the machine running the ftp server, what is the output of this command?

```
route
```

---

### Post by stinger30au on 2009-04-30
route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         home.gateway    0.0.0.0         UG    0      0        0 eth0

---

### Post by Kareeser on 2009-04-30
Alternatively, your ISP may prohibit the running of servers on its network and block port 21 on their side.

---

### Post by halitech on 2009-04-30
> **Kareeser said:**
> Alternatively, your ISP may prohibit the running of servers on its network and block port 21 on their side.

possible but that shouldnt prevent the router from being pinged.

---

### Post by alphacrucis2 on 2009-04-30
> **stinger30au said:**
> route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         home.gateway    0.0.0.0         UG    0      0        0 eth0

That looks ok. I just wondered if maybe your server didn't have a default gateway set up. Most likely problem is the port forwarding or firewall setup on your router. Ftp can actually be a bit tricky, as once the control port 21 is established the actual data transfers occur over a completely different session which is either opened from the server back to the client or the client to the server depending on whether active or passive transfer is specified.

---

### Post by stinger30au on 2009-04-30
> **alphacrucis2 said:**
> That looks ok. I just wondered if maybe your server didn't have a default gateway set up. Most likely problem is the port forwarding or firewall setup on your router. Ftp can actually be a bit tricky, as once the control port 21 is established the actual data transfers occur over a completely different session which is either opened from the server back to the client or the client to the server depending on whether active or passive transfer is specified.


default gateway ip might be it...
heres limited help with the program. i will look at its homepage tomorrow and see what i can find

there is an ip setting in the program that says

server address

it is currently 0.0.0.0  - default

theres another that says

server port:
nat router - nill


maybe in one or both of these i need to put the ip of my router?

---

### Post by stinger30au on 2009-05-02
i have done some asking round of some friends of mine and they told me to check if my isp has got the ftp ports blocked so you cant set up a ftp server at home.

i spoke to my isp today and they said no to this but they told me to check the router config.


[i have been hunting thru here for a config for my billion 7402LM]("http://www.portforward.com/english/routers/port_forwarding/routerindex.htm")

there is a few here but nothing exactly what i need

i have emailed billion tech support and asked for a manual in pdf format. i have misplaced mine.

but from what i gather from my friends there is two sections in my router config i need to tell it to enable the ftp server to talk to the net.

now i wait i guess for the manual to turn up and see if i can sort it out.

---

### Post by halitech on 2009-05-02
when you log into the router, do you have a link for Configuration? If you do, there should be an option for virtual server. Add the FTP server there. The settings for the 7402lm should be close to the 7402gl so you should be able to use those steps (I Hope)

[http://www.portforward.com/english/routers/port_forwarding/Billion/Bipac-7402GL/FTP.htm](http://www.portforward.com/english/routers/port_forwarding/Billion/Bipac-7402GL/FTP.htm)

---

### Post by stinger30au on 2009-05-02
> **halitech said:**
> when you log into the router, do you have a link for Configuration? If you do, there should be an option for virtual server. Add the FTP server there. The settings for the 7402lm should be close to the 7402gl so you should be able to use those steps (I Hope)

[http://www.portforward.com/english/routers/port_forwarding/Billion/Bipac-7402GL/FTP.htm](http://www.portforward.com/english/routers/port_forwarding/Billion/Bipac-7402GL/FTP.htm)


yes i have done this and still no go

theres so many options in the setup on this router its mind blowing.
hopefully when the manual arrives it will make my life easier

---

### Post by stinger30au on 2009-05-03
i have had another look at this

looks like in my router i have to forward BOTH port 21 and port 20

*NOW* i can actually ping my ip address

and now i have a new problem

i have restarted the pc a few times and i can not get gadminproftp server to active

the program starts up and all my seettings appear to be ok

if i hit the activate button... it does nothing

*sigh*

one step forward, two steps backwards!

---

### Post by stinger30au on 2009-05-03
more reading...

i have found out i have had to register here at [https://www.dyndns.com](https://www.dyndns.com)

create an account and give it your ip address and make up a domian

you can find you ip address here

[http://www.whatsmyip.org/](http://www.whatsmyip.org/)

my route has a config that says 

"DYNAMIC DNS"
in this window, select [www.dyndns.com]("http://www.dyndns.com")
also i had to put in my username and account

now what happens is, if i fireup my ftp cliend and put in my domain name that i made up, say "lets.get.it" it resolved the ip address

thats great, its a good start and thats whats supposed to happen

now if i could just get the server to talk to the net id be happy

to check if the net is seeing your ftp server correctly is here

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

more searching and i found this

[http://www.youtube.com/watch?v=NfvNifHKP3s](http://www.youtube.com/watch?v=NfvNifHKP3s)

---

### Post by stinger30au on 2009-05-03
> **Kareeser said:**
> Alternatively, your ISP may prohibit the running of servers on its network and block port 21 on their side.


i have spoke to my isp and they said they are not doing this


what if i change ports perhaps?

i might try this.... nothing else seems to work:confused:

---

### Post by stinger30au on 2009-05-03
more reading on the topic

[http://ubuntuforums.org/showthread.php?t=79588&page=2](http://ubuntuforums.org/showthread.php?t=79588&page=2)

[http://ubuntuforums.org/showthread.php?t=39566&highlight=proftp+nat](http://ubuntuforums.org/showthread.php?t=39566&highlight=proftp+nat)

---

### Post by stinger30au on 2009-05-04
handy command

sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 20 -j ACCEPT

this will open port 20


this will show you what ports are open on your o/s


netstat -an | grep "LISTEN "


if your router does not support DDNS use this s/w in ubuntu

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by stinger30au on 2009-05-05
the closest i can find to my 7402LM router manual is a 7402R2

[http://www.billion.com/_Internet/usermanual/7402R2UM10282005_203.pdf](http://www.billion.com/_Internet/usermanual/7402R2UM10282005_203.pdf)

---

### Post by scheuri on 2009-05-05
Hi there...just a few thoughts on my side.

Am I getting this right?:
You have an ADSL or Cable Connection from an ISP. You connect your LAN (Local Area Network between your private computers) with the internet using a router.

Now, first you need to try to make sure that the outside world is capable of getting to your router which has an IP address assigned by your provider. Lets say it is 10.0.0.1.
Now, it is very very likely that you CAN NOT ping or otherwise use that IP address because your router has some sort of firewall installed which denies ALL incoming traffic by default.
Pings are special (keyword is ICMP), they might never work, even if we manage to make ftp work in the end.

As a next step you need to open your firewall of your router to allow a certain port to accept traffic from outside. In your case it is port 21 (at least for now, I explain later on what I mean).
But you not only need to say this to your router, but also WHERE TO route this traffic to within your LAN when accepting that traffic (keyword is: NAT)
So actually TWO steps are necessary to do with your router:
- open the ports to make incoming traffic possible
- tell your router where (within your LAN) to pass that traffic to

I suggest you try to open up ssh first. That is port 22.
The reason I say this is, because ftp needs MORE ports than just port 21 depending if you use passive or active FTP.
SSH is easier to setup as a start and to learn what to configure with your router. You can disable that later on any time, but then you might know better how things work and start trying to make ftp work.

And yes, dyndns.org allows you to give your IP-address (outside, from your ISP) a name such as myhomeserver.dyndns.org and therefore easier to remember....
There are clients available for linux which you can install on your ftp server which will update the information on dyndny reagularly to make sure that the correct IP-address from your ISP is used with your name.

EDIT:
Since the FTP-server is working on LAN, there is nothing wrong (so far) with your linux-box...so no firewall there. 
If you have your router as gateway for your linux-box that is fine and exactly what you need. 

Hope I could help.
If all that was written before already...sorry...I failed to see it.
cheers
scheuri

---

### Post by stinger30au on 2009-05-05
FIXXED!!!!

after reading the manual i have found out i had to adjust the firewall settings 


i had to turn on in the firewall section port 20 & port 21

i pointed them back to my server ip of 192.168.1.1


works nicely!!!

and because i have setup the dyndns account i can give out a handy address rather then the ip

YOU RIPPA!!!

i knew the manual would tell all.

---

### Post by stinger30au on 2009-05-05
> **scheuri said:**
> 
Hope I could help.
If all that was written before already...sorry...I failed to see it.
cheers
scheuri


well its stopped working again in the middle of the night

my router is going silly. the fireware is not letting me route to 192.168.1.1
thats the ip of my server on the lan
the router keeps changing it to 192.168.1.0 for some unknown reason

---

### Post by scheuri on 2009-05-06
Does your server use a fixed IP adress or does it get it from the router (with DHCP)?
It could also be a problem with the router, but I do not know.

---

### Post by stinger30au on 2009-05-07
> **scheuri said:**
> Does your server use a fixed IP adress or does it get it from the router (with DHCP)?
It could also be a problem with the router, but I do not know.


i have at the moment got the server with a dynampic ip from the router


i have tried to set a static ip but everytime i do i lose net access all together from it


thanks for the suggestion though

i will look in to this deeper with a static ip

---

### Post by stinger30au on 2009-05-22
i finally got a reply back from billion.com

only took them 2 weeks or so

i had to change the netmask in the router to 255.255.255.255

this allows me to set a single ip address to router the ftp incoming/outgoing ports to

---

