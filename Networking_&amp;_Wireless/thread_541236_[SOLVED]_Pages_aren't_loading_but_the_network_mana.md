---
title: "[SOLVED] Pages aren't loading but the network manager says all good."
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by staticvoid on 2007-09-02
Hi,
Seeing as this is my first post I would like to offer everyone some popcorn :popcorn: enjoy :)
ok, to business...

During my Ubuntu installation my wireless network was detected,  and passed the test (I do not have WEP authentication, it's an open network). But when I try to download updates or surf the web my network times out. It says "connected" but it doesn't work. 
 
1. It may be a hardware problem, I was having similar problems in windows.
2. It may be the router.
3. It may be silly me.

It's maddening that 1. everyone else in my house gets wireless,2. my network manager says its connected, 3.when I get nearer to the wireless router my signal is higher, and all this to say: I cannot load a single site.

With opensuse under KDE and Konquerer it would load sites very very slow, and sometimes not at all. HUH?? :confused:

sincerely,
staticvoid

p.s. What are the causes to network time outs? Perhaps some general networking information would help? Some one to translate loopback lo DHCP network timeout WEP IPv6 into english?

---

### Post by eggdeng on 2007-09-02
Assuming your router is using DHCP, the first thing to do is check if you are getting an IP address from the router. You can do this by typing ```
ifconfig
``` in a terminal. If you are getting an IP, see if you can ping the router. ```
ping IP_of_router
``` If you don't know the router's IP, check the documentation that came with it. If all goes well up to here, it may be a DNS problem. Instructions on how to fix it and lots of other useful info at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

---

### Post by broinjc on 2007-09-03
.

---

### Post by staticvoid on 2007-09-03
Thank you for the information,

I executed the ifconfig command and I did not get any IP address. at least, I don't think so. :( The output was a little confusing. I am no expert. Basically what I got from it was this:

eth1 says everything (packets, errors, collisions, carrier, TX bytes) is 0 the "HWaddr" says 08:00:46:CC:28:6F

lo says "UP LOOPBACK RUNNING" and "MTU:16436" What is MTU? the diff between these to is that the RX bytes and the TX bytes have values (6923)

What is lo? my mask is set to 255.0.0.0 and my "inet addr" has a value there as well. What does this all mean?

I have a "manual network configuration" now and I have tried "roaming mode" and also "WLAN_C3" (the name of my network, it says "48%") But it won't connect. I mean, it does not say it won't connect but, it doesn't.

SO. I went to the help page you gave me, I entered "sudo pccardctl ident" and got "Socket 0: no product info available". So is my wireless card unsupported? I did "gksudo gedit /etc/pcmcia/config.opts" to enter in my card information. I do not know my card information. I will research that... For now I need an English interpretation of my output :/

sincerly,
staticvoid

---

### Post by eggdeng on 2007-09-03
You are confused! To start with, don't worry what everything means for the moment, most of it is pretty much gibberish anyway. 
It sounds as if your wireless card is working but you have not configured your network. 
The first thing you need to know is whether your network uses static IPs (you specify an IP address from a given range for each machine) or DCHP, (your router decides which IP to hand out to any machine that connects to it . An IP address is basically a string of digits which uniquely identifies a machine on a network). You should be able to find out this information by checking the configuration on any machine which has a working connection to the network and / or checking against the router documentation.
The next important thing you need to know is the name of your network or ESSID. 
You will also need to know the interface name of your wireless card (probably eth1 but check in System->Administration->Networking).

---

### Post by staticvoid on 2007-09-03
Hi, yes I am deffinately confused,
My network gives me an IP address automatically. It has DCHP. The interface name of my wireless card is eth1. I put in my ESSID correctly (WLAN_C3) and since it s an open network I did not assign any WEP key. 
My last post described my situation when it was not connected (oops, my bad). 
It now says "connected" (as It has been before in windows and with openSUSE).

1. I can install programs from the internet through "Add/Remove Programs..." It connects to blablabla.es and says "downloading". Somehow...

2. But, I cannot connect to the internet though. No jolly google page in fireox for me, nope. Just a VERY long wait and then a "timed out" notification.

3. All the other computers with wireless are using the same configuration in my workspace and get internet.

So. Why is it timeing out??? If I it was not configured it would say "Cannot load page" not "timed out", right? And it is configured because somehow, some way, Ubuntu can get download programs and realize that it needs to be updated (I cannot install those updates though) Why in the world would it recognize 116 updates for my system and not be able to download a singal one of them?

I would still like to know what lo and MTU is... Yes, I know what an IP address is ;) 

Still very much confused,
staticvoid

---

### Post by staticvoid on 2007-09-03
Oh, and I ran ifconfig and it recognized eth1 this time and gave me an IP address. So it is connected.

staticvoid

p.s. I have pinged the IP address before when it was not working and I get results. I will try again though...  :/

---

### Post by eggdeng on 2007-09-04
lo is the interface which represents the loopback address (127.0.0.1). It's basically a connection which is used to check if your networking (TCP/IP stack) is configured correctly. If your machine can talk to itself over this connection ie if you get a response from ```
ping 127.0.0.1
```, then your network interface is installed OK.
Next step is to check if there is communication between the network interface and the the router. To this end, you want to ping the router. ```
ping XXX.XXX.XXX.XXX 
```where  XXX.XXX.XXX.XXX is the router's IP address. If you get a response, try to ping an external IP address, if possible, your ISP's DNS address or else just ping my website at 81.172.50.71
If you are getting responses on all these, then despite appearances you are connected to the internet, just not to the Web. The problem is that you are not connecting to a DNS server. (This is a server which translates IPs into hostnames, ie the above IP into [www.eggdeng.com](www.eggdeng.com)). If this is the case, follow the steps described at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59-2]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59-2") section headed DNS.
If you really need to know what MTU is, try [http://en.wikipedia.org/wiki/Maximum_transmission_unit](http://en.wikipedia.org/wiki/Maximum_transmission_unit)

---

### Post by staticvoid on 2007-09-04
:) Yay! It must be a DNS problem. I pinged everything (plus the IP for your site, thank you) and got responces. So I went to follow the steps you said and still have questions.

This is a sample of what should apear in the file: /etc/resolv.conf

  search telus.net
  nameserver 209.53.4.130
  nameserver 209.53.4.150

What does "search" refer to? I do not get it when I check *my *resolv.conf file, just the two nameserver results. 

**When I edit this file that says "do not edit!" should I first turn off my wireless?** help.ubuntu says:

*For a Win 2000/xp box click Start>Run...type cmd click ok. type ipconfig /all. In the sample above, replace telus.net with what's next to the field "Connection-Specific DNS suffix". For name server look next to the line "DNS servers".*

Should I **add **the *search *to my file if I see the "Connection-Specific DNS suffix" field? Ok, thanks again. Hope I can get it up and running soon.

Staticvoid

p.s. Nice site by the way :) Very organized layout. Just curious: What does "eggdeng" mean?

---

### Post by staticvoid on 2007-09-04
.

---

### Post by eggdeng on 2007-09-04
Any /etc/resolv.config files I have seen have just had the bare nameserver entries. Mine simply reads

```
nameserver 62.42.230.24
nameserver 192.168.1.254
```

Bit strange you are warned not to edit the file though.Try entering the appropriate values on the DNS tab in System->Administration->Networking. Click OK and then restart your network. ```
sudo /etc/init.d/networking restart
```
Thanks for checking out the site, glad you liked it. As for eggdeng, it's just the way some of the non-native speakers around here pronounce my name.

---

### Post by staticvoid on 2007-09-05
Hi, so...
boohoo... it's a hardware problem. everything is perfect. DNS, DHCP, etc. I should've guessed from the start. No internal wireless for me I guess. busted. Anyway, I now have a bulky card sticking out of my computer and I am writing this post in a firefox browser provided by Ubunutu :) Anyway, I learned a TON out of this. Thank you again and again. If some one is searching the forums they will find this to be a nice step by step guide (with brief interuptions by yours truly). Ok, gtg.

Staticvoid

---

### Post by PeterF on 2007-09-05
When I activated my wireless card I had something similar, somehow the firewall didn't let Internet traffic trough. After disabling the firewall (I used Firestarter for that) and enabling it when the wireless connection was active everything worked. I don't know if it's a bug but i can't reproduce the behavior again.

---

### Post by staticvoid on 2007-09-09
Hmm... I'll try that :) I need a firewall anyway.

SV

---

