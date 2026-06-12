---
title: "How to make my server accesible from outside"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by jordi_rc on 2007-02-26
Hello to all

I come for another thread and started this because I am trying to make my home server and I configured my static ip as it is told in this thread:

[http://ubuntuforums.org/showthread.php?p=2216104#post2216104](http://ubuntuforums.org/showthread.php?p=2216104#post2216104)

BUT when I type the static IP my isp gave me, I visit my router, not the web page running on my server machine.

I don't know why.
In my router there's an option that maybe I must use, that says it is for assign a public ip to a device. In the explanations it says:

> 

Assign the public IP address of a connection to a LAN device

This page allows you to assign the public IP address of your Internet Connection(s) to a specific device on your local network...

You might want to do this if:

* You encounter issues with some applications through the Network Address Translation engine of your SpeedTouch.
[B]* This device is running server applications (web server, ...) and you want it to be accessible from the internet.
[/B]* This device has to be considered as the unique entry to your local network (DMZ).



Should I do that? Or will break something?
Or should I use as static ip in the network configuration the ip my isp gave me (starting in 85.) instead of the ip the router gives me (192.168.0.129)? 

What should I do?

Thanks for any info.

Jordi

---

### Post by pirothezero on 2007-02-26
first make sure the router has the ports being forwarded, and then you are going to want to change the port on the webserver more then likely so you can do [http://ip:port](http://ip:port) in the browser. Thats how a friend of mine has http file server installed on his server next door ( we share the same connection).

That way we can use [http://wanip:500](http://wanip:500) and get in or use the dyndns hostname that we have setup from the outside as well.

---

### Post by jordi_rc on 2007-02-26
Hello pirozethero

I had my Xubuntu machine with DHCP. As my isp gave me a static ip, I used ifconfig to get the ip, gateway and subnet mask values, and typed in the graphical UI as explained in:

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html)

(This is my first doubt. Why I used an ip assigned by the router (192.168.0.129) instead of the static ip that my isp gave me (starting in 85.)????)

All was fine, I do ping and can navigate.
Then, I forward ports 80 and 443 to Apache, and asigned it to my Xubuntu PC as shown in:

[http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/Speedtouch530v6/Apache.htm](http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/Speedtouch530v6/Apache.htm)


So... now what? I can't visit my server from the othe computer. When I type my static ip (85.etc), I go to the router page, not the server.

Why? What must I do now????? :confused: :confused: :confused: 

Jordi

---

### Post by Floppyjoe on 2007-02-26
Possibly disable remote management in you routers configuration or change the port for remote management to something else if you really need this.

---

### Post by jordi_rc on 2007-02-26
Thanks, but...

What is remote management? Eh? What?

I just want to be able to visit my server...

Do I did it the right way until now or I missed something?

By the way, I have noticed the option to identify the static ip with the Xubuntu has disappeared, so I think it must be another way.

Jordi

---

### Post by Floppyjoe on 2007-02-26
If you connect to your Isp by pppoe then they probably issue your Static Ip to your router when you connect. The router has the option of remote management that allows you to connect to your routers configuration utility from remote locations. If the port your remote management is using is the same as the port you are trying to forward then there may be a problem there. The router assigns Ip addresses to the different computers on the network. If your router has the ability to assign static dhcp addresses then this would be good because you can forward the ports(80-443) to that static dhcp ip address that your server is using.

---

### Post by jordi_rc on 2007-02-27
Hi thanks but the port is not blocked, as I can enter the xampp page using the private ip:
192.168.0.129:80
But if I type:
85.<the rest of my public static ip>:80 
then I enter the router configuration page.

Any ideas?

Jordi

---

### Post by az on 2007-02-27
First off, here is a great tutorial on networking:
[http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm)


> **jordi_rc said:**
> Hello pirozethero

(This is my first doubt. Why I used an ip assigned by the router (192.168.0.129) instead of the static ip that my isp gave me (starting in 85.)????)

All was fine, I do ping and can navigate.
Then, I forward ports 80 and 443 to Apache, and asigned it to my Xubuntu PC as shown in:

[http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/Speedtouch530v6/Apache.htm](http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/Speedtouch530v6/Apache.htm)


So... now what? I can't visit my server from the othe computer. When I type my static ip (85.etc), I go to the router page, not the server.

Why? What must I do now????? :confused: :confused: :confused: 

Jordi

The router should have two network addresses.  The router is joining two networks - that's what a router does.  The outside address should be the static IP you got from your ISP (85.xx.xx.xx).  The inside address (Your home network - LAN) should be a 192.168.0.xxx)  Now, you need to tell the router to forward the requests to port 80 on the outside address to the port 80 of the web server you have on your inside network.


> **jordi_rc said:**
> Hi thanks but the port is not blocked, as I can enter the xampp page using the private ip:
192.168.0.129:80
But if I type:
85.<the rest of my public static ip>:80 
then I enter the router configuration page.

Any ideas?

Jordi

That means three things:
1.  Your webserver is working fine on 192.168.0.129
2.  Your router is handling requests on 85.xx.xx.xx and it is working fine
3.  Your router is not forwarding the call from 85.xx.xx.xx to 192.168.0.129

You only need to fix number three.

---

### Post by 7h35ur930n on 2007-02-27
the outside address will be static that you got from your isp, the internal address is assigned static in network menu which will be assigned by you. try giving your webserver a static ip internal and putting your web server in the DMZ of the router which will be the static ip address you give it. this will make the websrver accessable to the outside world. if you want help msn at [email]djdevian@btinternet.com[/email] i just recently setup an ubuntu 6.10 webserver with php, mysql and ssl. its really easy when you get the right information.

---

### Post by jordi_rc on 2007-02-27
This is a resume of the situation:

The router is in fact a modem/router. I can connect to internet even
if the other computer is turned off, and I have no other device to
navigate.

To know if my router ports were blocked, I modified httpd.conf in
Apache and restarted it.
I changed the line:
-- 
Listen 80
-- 
To port 8000, and I guessed this:
Listen 192.168.0.129:8000 --- I can enter the Xampp page from the
other pc. Por 80 can't now.
Listen 192.168.0.129:80     --- I can  enter the Xampp page using port
80 now, so port 80 IS NOT blocked.
Listen 85.<plus the restof my ip>:8000 -- Xampp can't be started
Listen 85.<plus the rest of my static ip>:80 --- Xampp can't be
started too

I take all back to "Listen 80" as the port is not the problem.
When I type in the browser this:
85.<plus the restof my ip>:80 -- I visit my router configuration type
192.168.0.129:80 -- I visit the Xampp page (my website for now)

I wish I could type my static ip 85.<plus the restof my ip>:80 and
visit my website, but for some reason I can't.
The port works fine, not blocked, as no matter I change it to another,
and restart Apache, I get the same.

I think there is some place that identifies the router with my public
static ip.

-----------
I ping my windows machine with this: ping -c3 192.168.0.128
And i get all this stuff:
PING 192.168.0.128 (192.168.0.128) 56(84) bytes of data.
64 bytes from 192.168.0.128: icmp_seq=1 ttl=64 time=1.53 ms
64 bytes from 192.168.0.128: icmp_seq=2 ttl=64 time=0.944 ms
64 bytes from 192.168.0.128: icmp_seq=3 ttl=64 time=1.10 ms

--- 192.168.0.128 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.944/1.195/1.535/0.250 ms
-----------
About the DMZ... I think I don't understand
all, but tell me if I do:
1) Maybe I must have a router with 2 ethernet ports.
2) If not, I could use DMZ for the moment, so I must activate the
option in the router "Assign public ip to a device", but if I do, I
must have my server all day running or I won't be able to use internet
in the other PC.

Maybe I must try, because I plan to change my router in some time, and
buy a good one with 2 ethernet ports at least and some support for
wifi for another laptop I have.

I said my provider I wanted a router with 2 ethernet ports, but they
sent me  one with 1 ethernet and 1 usb, and I heard many times usb is
a problem for all this. But they are a pain!
----
In the ubuntu forum you said me to configure Network GUI tool with
the values I get with ifconfig command.
In the tab DNS I have the router ip (192.168.0.1), as seems the router
gets the dns. Is this right?
-- 
Well, I hope not to bore you all,
please give any advice.

And many thanks to all people helping!

Jordi

---

### Post by az on 2007-02-27
> **jordi_rc said:**
> This is a resume of the situation:

The router is in fact a modem/router. I can connect to internet even
if the other computer is turned off, and I have no other device to
navigate.
...
I wish I could type my static ip 85.<plus the restof my ip>:80 and
visit my website, but for some reason I can't.
The port works fine, not blocked, as no matter I change it to another,
and restart Apache, I get the same.

All you need to do is tell your router to forward port 80 from the internet to your 192.168.0.129 machine on your lan.


> **jordi_rc said:**
> 
I think there is some place that identifies the router with my public
static ip.


Your router does need to use the static ip.  There is no other way for it to work.

---

### Post by jordi_rc on 2007-02-27
7h35ur930n !!

I have turned on msn on my Xubuntu and added your msn as friend.

If you can come and help me I will have it open.

See you

Jordi

---

### Post by jordi_rc on 2007-02-27
Hello Az,

I did all just as explained in
[http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/Speedtouch530v6/Apache.htm](http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/Speedtouch530v6/Apache.htm)

Is something there bad explained? I did just that way!

Thanks again

Jordi

---

### Post by jordi_rc on 2007-02-27
Hi to all

I must thank all people here.

And specially to 7h35ur930n, who just now helped me to see the problem.

So the server works fine !

The problem is that from inside my home, the router sends all visits to its configuration. But from outside, they can visit my server, not the router.

SO I am happy because server works, and static public ip and port forwadding too.

But how do I make my computers at home visit my server using my public static ip?
Or this is normal?

And for some reason, now visiting in the Xubuntu machine to "localhost" doesn't work. I must use 192.168.0.129

So the problem is this, The port forwading was ok.
Is this all normal? Or how to fix this, so I can visit using public ip?
Thanks again

Jordi

---

### Post by dzul1983 on 2007-03-03
do you mind telling me what you did to get it working? I'm trying to get this working too..

---

### Post by jordi_rc on 2007-03-03
Hi dzul1983

I suppose that you have a web server installed and running. If not, install Xampp.
[http://www.apachefriends.org/en/index.html](http://www.apachefriends.org/en/index.html)
That is not a secure web server but it is easy to install and test all this.

If you have a better version (more secure) of Apache or any other server, turn it on, so it runs, and do all the following.

You must do this:

1) Open a terminal and type: 

ifconfig

You will see a text similar to mine:
eth0      Link encap:Ethernet  HWaddr 00:01:80:63:67:AE
          inet addr:192.168.0.129  Bcast:192.168.0.255  Mask:255.255.255.0

the numbers may be different for you.
The number for "inet addr" is your local ip.
The number "Mask" is your subnet mask.

2) Use the command:

route -n

And you will see something like this:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

Just look the number in the last row in the column under gateway. In this case, 192.168.0.1
This is your gateway.

3) Write down in a paper those values. For me are:
ip:192.168.0.129
Subnet mask: 255.255.255.0
Gateway: 192.168.0.1
May be different for you

4) IF YOU HAVE STATIC IP:
Follow the instructions if you use Ubuntu of this page to fill these values in your graphical gui:
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html)

If you use Xubuntu like me, this is placed on Applications/Sistem/Network.

BUT you don't need to fill a name for host or domain, it is not necesary.

5) IF YOU DON'T HAVE STATIC IP: No idea how it works then. I have static ip. I suppose you should then use dyndns.org or similar. All said here is not valid then.

6) Forwar the ports so people can visit you.
Go to page:

[http://www.portforward.com/routers.htm](http://www.portforward.com/routers.htm)

Search for your router company and model. Then search for Apache if that is your web server.
Do what says there.
Proceed with care.
If you have some other computer using your router to send files or download something, like for example emule, close all programs like these, so it may hang your router menu. If something fails, disconnect, initialize router, and connect again.

7) Now if you have a domain name, and is set up well, people can visit you. If you don't have domain name yet, people can visit you using your static ip. THis is my case for now.


Do all this in order.
If you don't get all done, please tell well what you did.
If you have done well, your server will be seen from outside.
From inside your home, if you use your ip, you will not see your server. You will see your router's page. This is normal. Just use the local ip that you got with ifconfig to visit yourself.

Please tell me what you got, and if I can, I can help you to know if it works visiting your site.
My msn and email is [email]acero_64@yahoo.com[/email]. If the hour difference between our countries permits it, I can visit and tell you. If not, I will take a screenshot.

So long

Jordi

---

### Post by curtis on 2007-03-03
Your seeing your routers configuration page when you go to your wan ip because your router is listening on port 80 for your local network. Change the port for the router if there is a setting to do so, I know with Linksys and Netgear routers you can.

---

### Post by dzul1983 on 2007-03-03
got it working.. the port forwarding seems to have done the trick.. I was the only person to see the router config when typing in the URL.. curtis was right.. the router was also listening to port 80.. but on the LAN side.. I got someone to try it out from the outside.. and they said that it was working fine..

---

### Post by jordi_rc on 2007-03-04
Good that it worked dzul

In my router, as in many, I can't change the port were it listens, but as you say, that is only for your LAN, not from outside.

And that is fully normal.
I think it is better to just use local ip when you want to enter your server, and not change anything.

So long

Jordi

---

