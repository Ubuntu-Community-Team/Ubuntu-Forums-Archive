---
title: "Need help figuring out my connection issues, please..."
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by norfair on 2008-04-25
First off, I'm completely new to Ubuntu (and Linux in general) and am using the Gutsy version currently and have internet access via cable internet and an ethernet cable modem. I am having problems getting online with my new computer (Shuttle KPC with Ubuntu preinstalled) in that I was able to successfully complete the registration process by typing in the web address my ISP gave me to configure my online account, but can't go anywhere else. 

Every site I try comes back with "Server not found." I'm not savvy when it comes to networking, so I don't know what I should be looking for, but I currently have my connection set as a "wired connection" and address set as "dhcp." My cable modem is hooked directly up to my computer, so I didn't enable "roaming mode" assuming that was for wirelessly accessing the internet. 

Trying every setting I could, I consulted the Ubuntu Help section and tried their "ifup" Terminal command trick. I got the message they displayed on their help page, which led me to believe that would fix my problem. But I still get the "Server not found" message everytime. I've also never recieved the message "Connection Established" as mentioned on Ubuntu's Help guide under "Connect to a network." 

Can anyone offer some assistance, please?

---

### Post by superprash2003 on 2008-04-25
if you are able to access your ISP webpage and not any other webpage.. it could be a DNS problem.. try changing your DNS to opendns 208.67.222.222 and 208.67.220.220 .. here's how you do it [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by norfair on 2008-04-25
> **superprash2003 said:**
> if you are able to access your ISP webpage and not any other webpage.. it could be a DNS problem.. try changing your DNS to opendns 208.67.222.222 and 208.67.220.220 .. here's how you do it [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

Thanks for the suggestion. However, it didn't work for me. I followed the directions and all that, but nothing happened. I really can only connect to my internet service providers registration page - that's it. It's the only sign of life on the internet I've seen. I know I was truly connected as the first email address/account I entered was rejected as already being used. The next one I entered was okay. I don't know. 

This will really make me sound stupid (too late, I know), but what kind of information does one need to enter when setting up a connection and configuring an network connection? I assumed things would somewhat configure themselves, especially seeing as how I was able to seemingly set up my account. For example, under "connection settings" how do I know if I need it set to static, dhcp, or local zeroconf? Or should the host name be something other than "ubuntu"? Under DNS servers I have to address(?) listed, but how do I know that they are correct? Same thing with the Hosts tab. How do I know if any of that needs changing? 

I hate asking such basic questions, but I really have searched here there and everywhere for solutions. I've been on this project of getting my internet connection up and running since 2:30p today! I need to get the connection up so I can get somethings modified to work and test out my new computer so I know whether or not to keep it! I really like Ubuntu and want to stick with it.

---

### Post by wilsonmuse on 2008-04-25
I'm on a cable modem connection and these are my settings:

in System > Administration > Network > Wired Connection > Properties, Roaming mode is enabled. You may have to reboot after changing this setting (a bug in network manager?) but after reboot it should work.

If that doesn't work try this in the terminal:

```

ifconfig

```

get the name of your NIC. Probably eth0 or similar.

```

sudo dhclient eth0

```

and if you get no errors and still can't surf or if you do get errors post the results of these commands

---

### Post by norfair on 2008-04-25
> **wilsonmuse said:**
> I'm on a cable modem connection and these are my settings:

in System > Administration > Network > Wired Connection > Properties, Roaming mode is enabled. You may have to reboot after changing this setting (a bug in network manager?) but after reboot it should work.

Nope that didn't work. That was the default setting too, as in, that's where it was at when I plugged in my modem and so forth. I manually configured it for some reason thinking romaing mode was for wireless access only.

[QUOTE=wilsonmuse]If that doesn't work try this in the terminal:

```

ifconfig

```

get the name of your NIC. Probably eth0 or similar.[/QUOTE]

_____@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1B:46:B3:E6  
          inet addr:10.127.128.183  Bcast:10.127.131.255
          Mask:255.255.252.0
          inet6 addr: fe80::230:1bff:fe46:b3e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14299 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:708573 (691.9 KB)  TX bytes:7472 (7.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

[QUOTE=wilsonmuse]```

sudo dhclient eth0

```[/QUOTE]

______@ubuntu:~$ sudo dhclient eth0
[sudo] password for ______:
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:30:1b:46:b3:e6
Sending on   LPF/eth0/00:30:1b:46:b3:e6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 10.113.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.113.0.1
bound to 10.127.128.183 -- renewal in 1604 seconds.

[QUOTE=wilsonmuse]and if you get no errors and still can't surf or if you do get errors post the results of these commands[/QUOTE]

Well, this didn't work, unfortunately. Though, I do thank you for your suggestion. I've posted the details of terminal entries (which wasn't easy seeing as how one machine is Windows connected via DSL and the other internetless one is Ubuntu connected via cable). Anyway, I'm open to trying anything as I don't really know what the heck I'm doing or not doing wrong. Or what I'm doing period. 

Thanks again.

---

### Post by superprash2003 on 2008-04-26
have you used it with windows before? did you have to dial the connection using a dialer in windows?

---

### Post by norfair on 2008-04-26
> **superprash2003 said:**
> have you used it with windows before? did you have to dial the connection using a dialer in windows?

No, I've only used it with my new Ubuntu only computer. Also, it's a cable modem, so I don't think there's a dialer to deal with, correct? 

All I did was hook up the cable modem to my new computer, and tried going online. According to the info my ISP provided, the internet browser was supposed to pop up and direct me to their registration page. It never did that, so I searched and struggled to find a link to go there myself. For some reason, that link works - but no other link/web address will work. I keep getting the message, "server not found." Why could I access their page, but no one elses? It's just weird. I'm so confused!

---

### Post by norfair on 2008-04-26
Well, I still haven't gotten anywhere and have no clue what to do. However, I followed Ubuntu's documentation guide from my system (also found here: [https://help.ubuntu.com/7.10/internet/C/network-troubleshooting.html](https://help.ubuntu.com/7.10/internet/C/network-troubleshooting.html)), and have found out by following the instructions that I "have no connection" and "cannot reach a DNS server." 

While this is, I guess, good to know, the guide doesn't help in resolving these issues. I know I have a connection of sorts as I can go to, [https://signup.insightns.com](https://signup.insightns.com), and register my new account with my ISP (which I have successfully done - insofar as I can tell). But I simply can't go anywhere else. So, does anyone know how I can "reach a DNS server"? If that truly is what my problem is. 

Thanks. And sorry for my wordy posts. I just like to be descriptive as I can.

---

### Post by wilsonmuse on 2008-04-26
> **norfair said:**
> 
______@ubuntu:~$ sudo dhclient eth0
[sudo] password for ______:
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:30:1b:46:b3:e6
Sending on   LPF/eth0/00:30:1b:46:b3:e6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 10.113.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.113.0.1
bound to 10.127.128.183 -- renewal in 1604 seconds.


Ok this here says that you have a successful connection through your cable. What has happened is that they've got you on their internal network and not on the internet. Any IP that is 10.x.x.x is reserved for private address' on private networks. I'm thinking what is happening is that you are assigned to the private network until you register and then you are supposed to be reassigned to and internet IP address. The problem lyes with the cable company.

I would suggest that you call them and get them to tell you how to get through their system. Remember this though, these companies hire unskilled workers to man the support phones. If they give you trouble or try to give you crap, immediately ask to speak to a supervisor. If you call you either want to have a working internet connection when you hang up or they should be sending someone to your house. No other options. The fact that you're using Linux makes no difference. If it does to this company then they are absolute crap and you need to seriously think about switching company's.

---

### Post by norfair on 2008-04-26
> **wilsonmuse said:**
> Ok this here says that you have a successful connection through your cable. What has happened is that they've got you on their internal network and not on the internet. Any IP that is 10.x.x.x is reserved for private address' on private networks. I'm thinking what is happening is that you are assigned to the private network until you register and then you are supposed to be reassigned to and internet IP address. The problem lyes with the cable company.

I would suggest that you call them and get them to tell you how to get through their system. Remember this though, these companies hire unskilled workers to man the support phones. If they give you trouble or try to give you crap, immediately ask to speak to a supervisor. If you call you either want to have a working internet connection when you hang up or they should be sending someone to your house. No other options. The fact that you're using Linux makes no difference. If it does to this company then they are absolute crap and you need to seriously think about switching company's.

Thanks so much for your help! I'll do just that. I think their support line is open 24hrs, so hopefully I can get in touch with someone tonight. But you're right, it probably won't be a fun, smooth experience. Whatever happens, however, I'll post my findings. Thanks again!

---

### Post by norfair on 2008-04-26
Yay! I'm finally online. Thanks, [COLOR="Red"]wilsonmuse[/COLOR]! You were right, all it took was a call into my ISP and that was it! I told them what you told me, and though he worded things differently back to me, he got the jist of my issue and tweaked some things on his end and asked me to reboot - never even asking me what OS I was using. Suffice it to say, all is well for now (and forever I hope!). Anyway, thanks for the suggestion and push to go online. You're my new best friend!

---

### Post by wilsonmuse on 2008-04-26
Hahaha! That's great! Enjoy your internet! And enjoy Linux!

---

