---
title: "D-link 524"
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by jeremyk on 2005-11-26
Hi,

I am presently connected to internet using a wired ethernet with pppoe. 

Since I want to share my connection with a computer having a WIFI card, I bougt a router D-link DI 524. The WIFI card is supported by ubuntu (RT2500 based WIFI card). 

However I have absolutely no idea how to manage the whole stuff. Can someone give me a step by step procedure?

Who is supposed to call the ISP (router, wired ethernet, WIFI, any of the computers??)? How do I configure my wired ethernet through the router (IP, gateway, name resolution ...)? 

Many thanks in advance. 

:confused:

---

### Post by mips on 2005-11-26
Who is your ISP ? Please provide a link.

I would suggest you first get the router up and running to get your wired connection going and then worry about the wireless.

What are youre current network setting LAN & WAN side of things, please post all details here.

---

### Post by jeremyk on 2005-11-26
First, thanks for helping.

I have a network card (intel 82801CAM) that I connect to a adsl speedtouch alcatel 500 series. I used the script pppoeconf to configure my connection. 

Before I go ahead, let me please tell you more about my situation. My computer is a laptop (which is also equipped with a WIFI card (Prism 2.5 Wavelan chipset)). So in fact, to be more precise I would like first to configure the internet connection of my laptop through the router (using any of the interfaces eth0 (wifi) or eth1 (wired)) and then to configure the connection of my second computer. This second computer will be used by my children. For practical reasons, the router must be located in the room, where I work with my laptop and the second computer in an other room.  Therefore the second computer will necessarily use the WIFI. Sorry for being so bothering, but I mention all this just because I also use my laptop outside home from time to time and I need to be able to have a dynamic IP in other networks. As I said, I have absolutely no experience about this kind of stuff.

Many thanks to you in advance for your help.

---

### Post by jeremyk on 2005-11-26
Sorry my ISP is bezeint from Israel. The site is in Hebrew. So I give here the content of my resolv.conf file:

nameserver 192.115.106.35
nameserver 62.219.186.7

Do you need further information?

---

### Post by mips on 2005-11-26
Here is what we will do:

1. Configure the router.
2. Get the laptop online via a wired connection.
3. Get the laptop online via a wireless connection.
4. Get your childrens PC online.

Are you using Ubuntu on both the laptop and PC ?

Give me the link to the bezeint website, i'll see what I can figure out.

We need the following information from your ISP:
Encapsulation type (PPPoE, PPPoA etc)
VPI
VCI
DNS Servers
You need to have your username & password ready.

---

### Post by mips on 2005-11-26
Which Speedtouch **Model** & **Version** do you have ?
[http://www.speedtouch.com/support.htm](http://www.speedtouch.com/support.htm), pick the correct one from the list or it should be written on the underside of the router.

---

### Post by jeremyk on 2005-11-26
I am using adsl.

The ISP web site is: [http://www.bezeqint.net/](http://www.bezeqint.net/)

I will try to get the information you need by calling them.

Cheers,

jeremyk.

---

### Post by jeremyk on 2005-11-26
I am using ubuntu breezy on both computers.

---

### Post by jeremyk on 2005-11-26
The adsl modem is Alcatel speedtouch 510

It uses pppoe.

---

### Post by mips on 2005-11-26
[QUOTE=jeremyk]The adsl modem is Alcatel speedtouch 510

It uses pppoe.[/QUOTE]

Which version ? There are versions 4, 5 & 6. Check the label at the bottom of the device.

After you have asked your ISP for all the info ask them if they can assist you to setup your speedtouch as a router so it logs in to the net by itself and you dont have to run PPPoE on the PC.

---

### Post by jeremyk on 2005-11-26
Sorry I could not determine the exact version of the modem, but the model is speedtouch 510. 

I called the ISP. They said the encapsulation mode is indeed pppoe, but could not understand what is VPI or VCI.

Cheers

---

### Post by mips on 2005-11-26
VPI=Virtual Path Identifier
VCI=Virtual Channel Identifier

There are many versions of the 510, I need the get the manual for the correct device from this website [http://www.speedtouch.com/support.htm](http://www.speedtouch.com/support.htm).

I'm sorry but without the above information I cannot help you.

Contact your ISP and ask them to assist you in setting up the the 510 for routed so you dont have to run any PPPoE software on your PC. This way the 510 would have the username&password for your adsl service and login automatically and stay permanently connected. You would only need to configure your PC/Wireless router for DHCP to get an IP address.

If you can get the above right then I can assist you further with the D-Link wireless router.

---

### Post by jeremyk on 2005-11-26
After checking more carefully, it turns out that the version is ST 510 4.2.3

My ISP does not support linux. However I saw on the web how they recommend to configure a similar router with exactly this modem on windows: by connecting on the browser to [http://192.168.0.1/](http://192.168.0.1/) and then follow the instructions they put on the web.

Therefore I tried the following:

sudo /etc/init.d/networking restart
firefox [http://192.168.0.1/](http://192.168.0.1/). However firefox tried during 10 minutes to connect to this address and finally I gave up.

Do you have any idea what should I do?

Cheers

---

### Post by jeremyk on 2005-11-26
I called the ISP again. The person who answered me did not know what are:

VPI=Virtual Path Identifier
VCI=Virtual Channel Identifier

Moreover, they do not provide support for linux, so they cannot help me in setting the adsl modem as a router.

Given this information, is it still possible for you to give me some assitance? 

Many thanks.

---

### Post by mips on 2005-11-26
I did some more searching on google and found this:

[http://www.petri.co.il/upgrade_from_alcatel_speedtouch_pro_to_510.htm](http://www.petri.co.il/upgrade_from_alcatel_speedtouch_pro_to_510.htm)
[http://www.petri.co.il/alcatel.htm](http://www.petri.co.il/alcatel.htm)
[http://www.isoc.org.il/~doron/PPPoE.html](http://www.isoc.org.il/~doron/PPPoE.html)

This tells us the VPI/VCI = 8/48

We know the encapsulation is PPPoE but which version of PPPoE, is it PPPoE LLC or PPPoE VC-Mux ??? I think it is PPPoE LLC.

Please confirm the PPPoE LLC and VPI/VCI = 8/48 with your ISP. If the person does not know what you are talking about ask to speak to someone else.

---

### Post by mips on 2005-11-26
[QUOTE=jeremyk]

Moreover, they do not provide support for linux, so they cannot help me in setting the adsl modem as a router.

Given this information, is it still possible for you to give me some assitance? 

Many thanks.[/QUOTE]

Configuring the Speedtouch 510 as a router has nothing to do with Linux, I would not even mention the word linux to them.

I can only try and assist but cannot promise anything.

---

### Post by mips on 2005-11-26
[QUOTE=jeremyk]After checking more carefully, it turns out that the version is ST 510 4.2.3

My ISP does not support linux. However I saw on the web how they recommend to configure a similar router with exactly this modem on windows: by connecting on the browser to [http://192.168.0.1/](http://192.168.0.1/) and then follow the instructions they put on the web.

Therefore I tried the following:

sudo /etc/init.d/networking restart
firefox [http://192.168.0.1/](http://192.168.0.1/). However firefox tried during 10 minutes to connect to this address and finally I gave up.

Do you have any idea what should I do?

Cheers[/QUOTE]

Try this address, 192.168.1.254

---

### Post by jeremyk on 2005-11-26
I tried:
[http://10.0.0.138/](http://10.0.0.138/)
[http://10.0.0.1/](http://10.0.0.1/)
[http://10.0.0.0/](http://10.0.0.0/)
[http://192.168.1.254](http://192.168.1.254)

None of them, worked. Is there any script to make the same task? Should I first reboot before I try to connect to the modem?

I called the ISP: they finally confirmed that VPI/VCI = 8/48

For setting the modem as a router, they ask some fees. So if you have some further idea, I would prefer to try this before.

Many thanks.

---

### Post by mips on 2005-11-26
I'm reading this manual, http://www.speedtouch.com/interface/R533/HTML/User's%20Guides/ST510v4/wwhelp/wwhimpl/js/html/wwhelp.htm?single=false&context=ug&topic=init
 and it does not look like the 510 can do what we want it to do. It seems like it will always require a PPPoE client on the pc which is very uncool and not good news for you.

How old is the D-Link device you purchased ? Can I possibly suggest you contact the supplier and ask him if you can exchange it for a D-Link DSL-G604T model instead if available in Israel and if it is compatible with bezeqint as router (not a modem). Possibly check the D-Link Israel site for more info.

[http://www.dlinkshop.co.il/Product.asp?Pid=DSLG604T&Cat2Cat1ID=146&Cat2ID=536](http://www.dlinkshop.co.il/Product.asp?Pid=DSLG604T&Cat2Cat1ID=146&Cat2ID=536)

---

### Post by jeremyk on 2005-11-26
I just bought the router. It is a D-link Di 524. Do you think this model is not the proper one in my situation?

---

### Post by mips on 2005-11-26
If you open a terminal and type **route -n** what output does it give ?

---

### Post by jeremyk on 2005-11-26
ifconfig
eth1      Link encap:Ethernet  HWaddr 00:09:6B:D0:90:D3
          inet6 addr: fe80::209:6bff:fed0:90d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48617 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:37302649 (35.5 MiB)  TX bytes:4996228 (4.7 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:679395 errors:0 dropped:0 overruns:0 frame:0
          TX packets:679395 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:52163612 (49.7 MiB)  TX bytes:52163612 (49.7 MiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:212.179.229.22  P-t-P:212.179.229.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:4853 errors:4946 dropped:0 overruns:0 frame:0
          TX packets:5075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:3639782 (3.4 MiB)  TX bytes:517239 (505.1 KiB)


route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
212.179.229.1   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         212.179.229.1   0.0.0.0         UG    0      0        0 ppp0

---

### Post by mips on 2005-11-26
Ok, that does not help as it does not use the 510 as a gateway.

In the meantime I found how this [http://www.dslreports.com/forum/remark,10372806~mode=flat](http://www.dslreports.com/forum/remark,10372806~mode=flat)
which explains how to configure an Alcatel for PPPoE authentication.

I'm gonna go sleep now. I'll carry on doing some more research tomorrow and hopefully we can find you a free solution.

---

### Post by jeremyk on 2005-11-26
Again many thanks and good night.

Cheers,
Jeremy.

---

### Post by mips on 2005-11-26
[QUOTE=jeremyk]I just bought the router. It is a D-link Di 524. Do you think this model is not the proper one in my situation?[/QUOTE]

It will work in conjunction with the Speedtouch 510 (That is if we get it to work the way we want it to).

The D-Link 524 is a wireless router only. It has no facility for ADSL wan, only a LAN ethernet port that you will have to connect to one of the LAN port on the Alcatel 510.

The DSL-G604T has a built in ADSL modem, router, wireless & firewall. It is like a combination of your Alcatel 510 & Dlink 524 in one box. It would be simpler to get the DSL-G604T to work i think.

---

### Post by mips on 2005-11-26
[QUOTE=jeremyk]I tried:
[http://10.0.0.138/](http://10.0.0.138/)
[http://10.0.0.1/](http://10.0.0.1/)
[http://10.0.0.0/](http://10.0.0.0/)
[http://192.168.1.254](http://192.168.1.254)

None of them, worked. Is there any script to make the same task? Should I first reboot before I try to connect to the modem?
[/QUOTE]

You need to configure your PC's LAN card for a Static IP address:

[http://www.dslreports.com/faq/6106](http://www.dslreports.com/faq/6106)
> How do I access the modem configuration page through my web browser? (#6106)	

      A: First, you must configure your TCP/IP connection to use your modem as the default gateway. The procedure for this varies slightly depending on the operating system you are using, but the settings you will need to use are as follows:

      IP Address (of your machine): 10.0.0.1
      Subnet Mask: 255.255.255.0
      Default Gateway: 10.0.0.138
      IMPORTANT: make note of the current settings before you change them because you will need to change them back in order to connect to the Internet again.

      Once you have done that, you may need to reboot your computer for the changes to take effect. Then you can type 10.0.0.138 in your web browser to access the modem configuration pages.

      **[COLOR="Red"]Note that you will not be able to connect to the Internet using your modem while doing this, so it is a good idea to have any material you need either printed out or saved to your computer since you will not be able to consult resources on the internet for assistance.[/COLOR]**


---

### Post by mips on 2005-11-26
This guide describes what needs to be done, [http://www.speedtouch.com/ST610%5CAppNotes/AppNote_RoutedPPPoE.pdf](http://www.speedtouch.com/ST610%5CAppNotes/AppNote_RoutedPPPoE.pdf)

---

### Post by jeremyk on 2005-11-27
Thanks to your assistance, I eventually managed to connect through the router using a wired ethernet. 

I will now deal with the wifi cards. If I encounter any problem, I will post in this thread a new question.

Again, many thanks.

Cheers,
Jeremy.

---

### Post by mips on 2005-11-27
What did you do/configured to get the wired connection up ?

---

### Post by jeremyk on 2005-11-27
Hi,

1. I rebooted the computer and instead of launching the connection by pon dsl-provider, I tried dhclient eth1. I got a IP from the modem. Then I finally could browse the modem at [http://10.0.0.138](http://10.0.0.138). I managed to use it as a router with pppoe. 

2. Then I connected the router D-link to the modem and to the computer. Also I tried dhclient eth1 and got an IP that allowed me to browse the router at [http://192.168.0.1](http://192.168.0.1). I defined the router as a pppoe connection engine. This did not work. 

3. I configured again the modem itself to work as bridged ethernet. In this configuration the pppoe script is executed by the router and every thing works.

4. I also managed to connect the web using the wifi of my laptop and it worked. I still have to try with the other computer. I will try it tonight.

I just noticed that the reinitialiazation of the networking services some times requires a reboot. That is /etc/init.d/networking restart is not always enough. Do you understand why this is case? Maybe there is some thing else to trigger for a complete reset. But what?

Thanks and cheers,
Jeremy.

---

### Post by mips on 2005-11-27
> 1. I rebooted the computer and instead of launching the connection by pon dsl-provider, I tried dhclient eth1. I got a IP from the modem. Then I finally could browse the modem at [http://10.0.0.138](http://10.0.0.138). I managed to use it as a router with pppoe. 

Could you browse the internet with these settings ?

> 2. Then I connected the router D-link to the modem and to the computer. Also I tried dhclient eth1 and got an IP that allowed me to browse the router at [http://192.168.0.1](http://192.168.0.1). I defined the router as a pppoe connection engine. This did not work.

Which router did you define as a pppoe engine, Alcatel or D-Link ?


> I just noticed that the reinitialiazation of the networking services some times requires a reboot. That is /etc/init.d/networking restart is not always enough. Do you understand why this is case? Maybe there is some thing else to trigger for a complete reset. But what?

No, not offhand.

So are you running any PPPoE on the PC's now or is the router handling that ? It sounds like the router from your description.

---

### Post by jeremyk on 2005-11-27
Hi,

1. When only the modem was on pppoe mode, I could browse the web without any problem.

2. When both the modem and the router were on pppoe mode, it did not work.

3. Presently, I am using the router on pppoe mode. It works and the route is:

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1

4. I also could connect to the router using the wifi of the second computer.

Cheers,
Jeremy.

---

### Post by mips on 2005-11-28
Cool, so everything is working.

Can I suggest you look at enabling some encryption on the wireless connections, WPA is the best to use and then there is WEP which is less secure.

---

### Post by jeremyk on 2005-11-28
Hi,

Thanks for your suggestion. This is interesting. However I have no idea about these encryption methods WPA and WEP. 

It would be great if you could explain me how to configure one of them.

By the way I posted a thread on the forum about another issue. I did not receive an answer yet. You may have some idea. On my second computer, I have a graphic card integrated to the mother card. The device is via VT8378 S3 unichrome. The resolution stucks at 800x600 after a lot of manipulation (dpkg-reconfigure xserver-xorg + correcting the frequencies in the xorg.conf file). Do you have any idea on the subject? 

Many thanks and cheers,
Jeremy.

---

### Post by mips on 2005-11-28
For the WEP & WPA stuff look at the tips & tricks forum as well as the wiki. You can also search for posts by Lambert.


Give me a link to that thread and post the required info below there and I will follow up there.
What brand & model monitor does the PC use. Might have to check up the Hor/Ver frequencies supported.

Post your xorg config file here.

---

### Post by jeremyk on 2005-11-28
Thanks again. I will give you a pointer to thread and my xorg file tonight or tomorrow morning. Right now I don't have access to the computer.

Cheers,
Jeremy.

---

### Post by jeremyk on 2005-11-29
Hi,

I you have time, please look at the thread I opened about the resolution problem:

[http://www.ubuntuforums.org/showthread.php?p=529242#post529242](http://www.ubuntuforums.org/showthread.php?p=529242#post529242)

By the way, I put a WEP key on my wireless connection. From time to time, the signal strength becomes zero and it takes time until it recovers a higgher level. Is this normal?

Many thanks,
Cheers,
Jeremy.

---

### Post by mips on 2005-11-29
> By the way, I put a WEP key on my wireless connection. From time to time, the signal strength becomes zero and it takes time until it recovers a higgher level. Is this normal?

No, it does not sound normal to me.

---

