---
title: "Installing a router"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by kebeat on 2009-02-05
Hi.
I can not install my Belkin Router. 
Modem alone works fine, but when I added the router, there is no more connection. How can I solve it?

---

### Post by gettinoriginal on 2009-02-05
Here ya go :p
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

---

### Post by newbee70 on 2009-02-05
> **kebeat said:**
> Hi.
I can not install my Belkin Router. 
Modem alone works fine, but when I added the router, there is no more connection. How can I solve it?

Have you set your router up yet?

type 192.168.1.1 into your browser window and hit enter.

that should connect you to your router.

<of course your router needs to be hooked up to your modem and to your computer.>

---

### Post by kebeat on 2009-02-06
> **newbee70 said:**
> Have you set your router up yet?

type 192.168.1.1 into your browser window and hit enter.

that should connect you to your router.

<of course your router needs to be hooked up to your modem and to your computer.>

Thanks. I tried what you write, but the problem remains. 
192.168.1.1 is not found. All cables are hooked up as you said. 
What do you suggest? 
Is it possible, that my router (Belkin Wireless G) is not compatible with Ubuntu? Does the Firestarter interfere with it?   
I have Ubuntu 8.10.

---

### Post by jimv on 2009-02-06
What's the output of this command (with the computer plugged into the router)?

```
ifconfig
```

---

### Post by kebeat on 2009-02-06
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:c8:95:9e  
          inet6 addr: fe80::20a:e4ff:fec8:959e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1157635 (1.1 MB)  TX bytes:197998 (197.9 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:84.0.63.249  P-t-P:145.236.238.182 Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1112469 (1.1 MB)  TX bytes:152710 (152.7 KB)

---

### Post by kebeat on 2009-02-06
The outcome of ifconfig is: 

eth0      Link encap:Ethernet  HWaddr 00:0a:e4:c8:95:9e  
          inet6 addr: fe80::20a:e4ff:fec8:959e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1157635 (1.1 MB)  TX bytes:197998 (197.9 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:84.0.63.249  P-t-P:145.236.238.182  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1112469 (1.1 MB)  TX bytes:152710 (152.7 KB)

What is the solution?

---

### Post by Kevbert on 2009-02-06
> **kebeat said:**
> Thanks. I tried what you write, but the problem remains. 
192.168.1.1 is not found. All cables are hooked up as you said. 
What do you suggest? 
Is it possible, that my router (Belkin Wireless G) is not compatible with Ubuntu? Does the Firestarter interfere with it?   
I have Ubuntu 8.10.
If that address doesn't work what do you get with [http://192.168.0.1](http://192.168.0.1) ?
What's the model of router ?

---

### Post by az on 2009-02-06
When you plug in the network cable between the router and the computer, does the network manager applet show you as connected?  If not, can you click on wired connections to enable the connection?

You should be hooked in to your router using a patch cable, not a crossover cable.  I know some ADSL modems use a crossover cable instead of a patch cable - are you sure they are properly set up?

To answer your question, firestarter should not prevent your computer from talking to your router.  But to troubleshoot that, you can always either turn off firestarter or boot from the live cd.

You should be able to talk to your router without it even being plugged in to your modem.

---

### Post by az on 2009-02-06
> **Kevbert said:**
> If that address doesn't work what do you get with [http://192.168.0.1](http://192.168.0.1) ?
What's the model of router ?

It may also be 192.168.2.1

Usually, that ip address is printed on a sticker on the underside of the router along with the default username and password.

---

### Post by kebeat on 2009-02-06
Sorry. The applet shows me unconnected, and the menu items for the connections are dimmed (disabled). 
Neighter ip addresses mentioned are correct, and there is no sticker with an ip address on the router. Stopping Firestarter does not help.
What can we do?
The type of the router is Belkin Wireless G, Model: F5D7230-4 
There is  a LAN/WLAN MAC, a WAN MAC, a serial n., an FCC ID and a PIN code, if needed.

---

### Post by bgates on 2009-02-06
It looks like it is indeed at 192.168.2.1

I found a manual, here:  [http://www.belkin.com/support/download/downloaddetails.asp?lang=1&download=994](http://www.belkin.com/support/download/downloaddetails.asp?lang=1&download=994)

Download the second manual, the first one is useless.  Obviously you will want to skip the many pages about the CD and go straight for the alternate setup.

It says that by default the router will act as the DHCP server for the LAN, which is what you probably want.  So if you got it used or something, make sure that is on.  The computer is not getting an IP address from the router, so if the DHCP service is disabled on the router it would explain that.

---

### Post by az on 2009-02-06
> **bgates said:**
> It looks like it is indeed at 192.168.2.1

I found a manual, here:  [http://www.belkin.com/support/download/downloaddetails.asp?lang=1&download=994](http://www.belkin.com/support/download/downloaddetails.asp?lang=1&download=994)

Download the second manual, the first one is useless.  Obviously you will want to skip the many pages about the CD and go straight for the alternate setup.

It says that by default the router will act as the DHCP server for the LAN, which is what you probably want.  So if you got it used or something, make sure that is on.  The computer is not getting an IP address from the router, so if the DHCP service is disabled on the router it would explain that.

Have you got it working?  Were you able to reset it to factory defaults?

---

### Post by travmon69 on 2009-02-06
yep my belkin 54g  ip was 192.168.2.1  but my dsl modem was also the same ip so i had to change it to 192.168.1.1.  if you have a dsl modem connection you need to change your router setup to a pppoe connection instead of dhcp type for it to sync with dsl.

---

### Post by kebeat on 2009-02-07
The Manual says: 
[I]Step 2   Set your Computer’s Network Settings to Work
         with a DHCP Server
See the section in this manual called “Manually Configuring Network
Settings” for directions.
[/I]
How can I set my Ubuntu to work with DHCP server?
Thanks.

---

### Post by travmon69 on 2009-02-07
> **kebeat said:**
> The Manual says: 
[I]Step 2   Set your Computer’s Network Settings to Work
         with a DHCP Server
See the section in this manual called “Manually Configuring Network
Settings” for directions.
[/I]
How can I set my Ubuntu to work with DHCP server?
Thanks.

are you connected to your isp by a dsl modem?

---

### Post by kebeat on 2009-02-07
Yes.
D-Link ADSL Modem

---

### Post by kebeat on 2009-02-07
How can I set the pppoe connection?

---

### Post by travmon69 on 2009-02-07
> **kebeat said:**
> Yes.
D-Link ADSL Modem

ok you need your dhcp server turned on but you need to change your connection type to pppoe an put your isp login and password in

let me know more about the setting if it works?

---

### Post by travmon69 on 2009-02-07
> **kebeat said:**
> How can I set the pppoe connection?

left side of router setup page has list  under internet wan says connection type

---

### Post by kebeat on 2009-02-07
But I still can not find router setup page 

[I]Using your Internet browser, you can access the Router&#8217;s Web-Based
Advanced User Interface. In your browser, type &#8220;192.168.2.1&#8221; (do
not type in anything else such as &#8220;[http://&#8221;](http://&#8221;) or &#8220;www&#8221;), then press the
&#8220;Enter&#8221; key.[/I] (Manual)

This does not work.

---

### Post by travmon69 on 2009-02-07
> **travmon69 said:**
> left side of router setup page has list  under internet wan says connection type

it sucks to have to do it that way. i can login in to my routers an access point but cannot login to my modem that way unless i directly plug in to the modem

---

### Post by kebeat on 2009-02-07
Any suggestions?

---

### Post by travmon69 on 2009-02-07
> **kebeat said:**
> But I still can not find router setup page 

[I]Using your Internet browser, you can access the Router’s Web-Based
Advanced User Interface. In your browser, type “192.168.2.1” (do
not type in anything else such as “[http://”](http://”) or “www”), then press the
“Enter” key.[/I] (Manual)

This does not work.

if you previously disabled the dhcp server on your router you probably need to reset it to factory settings

---

### Post by travmon69 on 2009-02-07
> **travmon69 said:**
> if you previously disabled the dhcp server on your router you probably need to reset it to factory settings

any luck?

---

### Post by az on 2009-02-07
> **travmon69 said:**
> yep my belkin 54g  ip was 192.168.2.1  but my dsl modem was also the same ip so i had to change it to 192.168.1.1.  if you have a dsl modem connection you need to change your router setup to a pppoe connection instead of dhcp type for it to sync with dsl.
So you were able to log into the router or not?  And if I understand, you logged into your modem and changed its IP address?

> **kebeat said:**
> But I still can not find router setup page 

[I]Using your Internet browser, you can access the Router’s Web-Based
Advanced User Interface. In your browser, type “192.168.2.1” (do
not type in anything else such as “[http://”](http://”) or “www”), then press the
“Enter” key.[/I] (Manual)

This does not work.

If you unplug your modem (and leave it unplugged), and you plug in the router to the computer, does network manager make a connection?  If so, then you are getting an IP address from the router and the DHCP server is working.

---

### Post by travmon69 on 2009-02-07
> **az said:**
> So you were able to log into the router or not?  And if I understand, you logged into your modem and changed its IP address?



If you unplug your modem (and leave it unplugged), and you plug in the router to the computer, does network manager make a connection?  If so, then you are getting an IP address from the router and the DHCP server is working.

AZ      i was just giving KEBEAT an example of how i had to set my router to a different ip cause my dsl modem had the address of 192.168.2.1 the same as my belkin router. the modem ip cannot be changed because it is locked by my isp and cannot be changed so i changed my router ip to prevent a ip conflict on my network.

---

### Post by kebeat on 2009-02-08
Now I can use the Wireless connection, but not the wired one. 
Another PC with Windows can use the wired connection too, with some trouble, after rebooting and running the Setup Assistant from CD. 
It is hard to get real beginner's support on this Forum. Sorry. Thank you anyway.

---

### Post by travmon69 on 2009-02-08
> **kebeat said:**
> Now I can use the Wireless connection, but not the wired one. 
Another PC with Windows can use the wired connection too, with some trouble, after rebooting and running the Setup Assistant from CD. 
It is hard to get real beginner's support on this Forum. Sorry. Thank you anyway.

That is odd?  A few weeks ago on my mom's ubuntu the network settings got messed up and it would say connected to the network but it could not reach the internet. browser would say server not found on every website i tried to access. the dhcp settings got messed up. i reinstalled ubuntu then everything was ok. if you played around with the dhcp settings on ubuntu maybe you messed it up?  did you try running the ubuntu live cd to see if it connects?
  once the router is setup and it works for windows it should work for ubuntu if not then some settings or config got changed on ubuntu and are messed up.
 ubuntu should connect automatically on startup no changes needed.

---

