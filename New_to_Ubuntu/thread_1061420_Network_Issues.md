---
title: "Network Issues"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by stroudma on 2009-02-05
For about 2 weeks now my desktop has intermittently not connected to the internet.  Sometimes it will and sometimes it wont.  Turning it off and turning it back on almost always solves the problem but i'm getting very tired of this solution. 

during sessions when it does not connect to the internet it will still read a wired connection in Network Configuration.  Everything is left on default setting or auto-configuration as far as IP and DNS addresses and such

It ran off a wired connection (from a wireless router) for about a year no problem, then it started acting up, i got another router 2 days ago and got it back up and running but it is doing the exact same thing all over again

When it will connect to the internet it will stay connected until i turn it off and vice versa

I've tried google to no avail. Although, to be honest I dont know if i would be able to recognize the solution if i had found it.  

Does anyone have any ideas?

---

### Post by abyssius on 2009-02-05
> **stroudma said:**
> For about 2 weeks now my desktop has intermittently not connected to the internet.  Sometimes it will and sometimes it wont.  Turning it off and turning it back on almost always solves the problem but i'm getting very tired of this solution. 

during sessions when it does not connect to the internet it will still read a wired connection in Network Configuration.  Everything is left on default setting or auto-configuration as far as IP and DNS addresses and such

It ran off a wired connection (from a wireless router) for about a year no problem, then it started acting up, i got another router 2 days ago and got it back up and running but it is doing the exact same thing all over again

When it will connect to the internet it will stay connected until i turn it off and vice versa

I've tried google to no avail. Although, to be honest I dont know if i would be able to recognize the solution if i had found it.  

Does anyone have any ideas?

Stroudma

If you really want help resolving this issue, it's up to you to provide enough information for someone to respond to. You've not said whether your problem is with a wired or wireless connection. You've not identified ANY of your hardware. You've not even stated what version of Ubuntu you are currently using.

The people that volunteer to provide help on this forum will be less inclined to do so, if they have to extract every bit of information one post at a time.

For a start, you could identify if your problem is wired or wireless. I'd guess it's wireless, but no-one wants to guess basic information. Next, you could share what version of Ubuntu you are using. Some more meaningful information would be the model of the wireless adapter you're using. Even better, you could post the output of the following command:
```
ifconfig -a
```
With this information provided, I'm sure you'll receive a meaningful response.

---

### Post by stroudma on 2009-02-06
sorry, i was trying to keep my post length down

i am using a wired connection from a netgear router, the router is also providing wireless too two laptops and a PS3, none of them ever have problems connecting to the internet (I am assuming it is not the router because this my initial assumption as well, so i upped and bought a new one too no avail), the exact router model is... Netgear Wireless G-Router WGR614

My ISP is Comcast

i am using intrepid ibex

the desktop itself is a custom build, asus motherboard, Q6600 processor, nvidia GT8800 graphics card, samsung formula one harddrive, 4gb mushkin ram and mushkin power supply... used to be a dual boot, but i took out the vista partition bout 8 months ago

this is the output to... ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:1d:60:c7:be:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:1e:8c:0a:ce:f6  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe0a:cef6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8484351 errors:0 dropped:570 overruns:0 frame:0
          TX packets:7181287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3778856073 (3.7 GB)  TX bytes:2283861778 (2.2 GB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29856 (29.8 KB)  TX bytes:29856 (29.8 KB)

pan0      Link encap:Ethernet  HWaddr 16:cf:81:40:e3:9a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



i love linux and have been trying to advocate it too my friends for a while now, and this forum is the only reason i can even use it in the first place, you guys have been nothing but helpful the whole time in my switch to linux, i've even been planning on getting a linux netbook within the next two weeks... basically, thanks in advance... if you need any other information i will try to be as prompt as possible in getting back to you, just hope someone has a clue whats going on

---

### Post by Quagga7 on 2009-02-08
Hey guys i have trouble with my computer, i can connect my comcast internet on my laptop it has windows xp installed into it but on my desktop i cant because i have ubuntu. when i connected it on my ubuntu it says looking for area connections then it says that their is no connection. Can anyone help me solve this? 



THANKS

---

### Post by superprash2003 on 2009-02-08
is this a wireless connection?? post output of ifconfig from the terminal

---

### Post by HermanAB on 2009-02-08
Uhm, Quagga7, please start your own thread, don't confuse things by hijacking an existing thread.

Stroudma:
In order to get a network connection to work, you need a number of things:
[LIST]
[*]IP Address
[*]Subnet mask
[*]Default Route
[*]DNS IP address
[/LIST]

These settings are usually negotiated between the DHCP client on your machine and the DHCP server on your Netgear router.

On Linux, you can schkrew things up if you would play around and install your own DHCP server.  So, check your running services and if you have a DHCP SERVER running, disable it.

To confirm that you have all the required settings, you can do this:
$ sudo route  (look for the default gateway address of your Netgear router)
$ sudo ifconfig (look for the IP address and netmask)
$ sudo cat /etc/resolv.conf (look for the DNS addresses - probably the Netgear address as well, otherwise your ISP DNS)

If things are not right, then you can manually run dhclient to fix things up:
$ sudo dhclient eth0

Otherwise, you can manually restart networking:
$ sudo service network restart

You should not need to reboot, UNLESS it is a WiFi connection.  WiFi adaptors have a dinky little ARM processor inside which needs to start up properly in order to work.  Frequently the only way to get a bad WiFi adaptor to work, is by cycling power on your machine.  There is no solution to this problem, except to buy a new adaptor.

Hope that helps!

Cheers,

Herman

---

### Post by Quagga7 on 2009-02-08
no its not wireless i want to connect just the ethernet cable so i can connecteed to the internet

---

### Post by bgates on 2009-02-08
There are two network interface cards, you might try disabling the one that's not being used, eth0.

eth1 looks ok, but maybe you could compare the settings to one or both of the working laptops.  If they run Ubuntu (or some linux) do ifconfig -a, if they run Windows go to Start > Run and type cmd, then at the prompt type ipconfig /all and hit enter.  If Linux then this:

inet addr:192.168.1.6 Bcast:192.168.1.255 Mask:255.255.255.0

Should all be the same on the laptops *except* the very last number after the last period in the inet addr.  I. e., it's a 6 here, that should be different on each machine.  The 1 before the 6 needs to be the same on each machine.  

If Windows, that setting will be called IP Address, but the same holds, the last segment needs to be different and all other segments need to be the same.  Mask will be called Subnet Mask and should be the same on all machines.  Windows will not have Bcast, but it will have Gateway which should be (almost but not quite certainly) 192.168.1.1 on all Windows machines.

If Netgear router is using default settings, and all machines are in agreement that Netgear router is DHCP server and they themselves are DHCP clients and there are no addressing conflicts, this will all be true, so we can rule all that out.  If that is the case, perhaps something is playing up between the two ethernet cards, or there is software that is trying to take over the configuration for some reason.  It is also a possibility there is a hardware fault in the ethernet card, ethernet cable, or the particular port on the Netgear that the desktop is plugged into.  So swapping cable and plugging it into a different port are more things to try.

---

### Post by Quagga7 on 2009-02-08
its just say that the connection is disconnected

---

### Post by superprash2003 on 2009-02-10
@quagga
   please check your LAN cables.. do you see a light on your router?.

---

### Post by Scunnered on 2009-02-10
stroudma

Like you I experience times when my internet connection will not install. What I find is that there is a request for my password for the WPA & WPA2 Personal.  Normally I*enter my password and all is well. This password is the one that you and your ISP work with rather than your usual logon one. In the event that the request is made a second time I cancel the request and totally shut down the system.

Do not assume that System > Shut Down > Restart will work as it has never done so for me.  A full shut down and give it a few seconds to settle before start up will normally work.  The worst I have had has been having to repeat this a second time.  As a rule this will work for a great number of days before a request to confirm the password.  

I have not kept a log of the times between such requests but I can recall a period in excess of 21 days.  This is my experience in the UK with Virgin Media and I hope that it will assist you.

---

### Post by Quagga7 on 2009-02-14
I hava problem i had to completely reinstall ubuntu
an it finally gave a conncetion! but i try to connect to the internet but it gave mi this message


"Your operating system is not supported by Comcast's Installation Wizard......"

---

