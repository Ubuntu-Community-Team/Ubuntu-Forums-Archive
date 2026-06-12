---
title: "Ubuntu noob"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by spamzilla on 2006-08-04
I am trying to setup the internet on my laptop, using my wireless SMC 2635w NIC. 

I quickly realised that the CD wouldn't install the driver for me, so where can I find the correct driver?

Then how do I install the driver and gain access to the internet via my router?

Any help would be much appreciated, and please, keep any instructions simple ;)

Cheers

---

### Post by moma on 2006-08-04
Maybe ndiswrapper is the answer?
[http://ndiswrapper.sourceforge.net/]("http://ndiswrapper.sourceforge.net/")
Ndiswarpper means that you use the orginal Windows driver in Linux via ndiswrapper module. It's pretty easy to set up.

Your card is listed under supported cards.
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

But hopefully someone can inform if there is a native driver for Linux.

---

### Post by spamzilla on 2006-08-04
Ok thanks. I'll try using ndiswrapper to install the driver asap.

Is there anything else know I need to know before I dive in and do this?

**EDIT **

at the page in the first link about ndiswrapper, I'm not sure where to go to read how to explain how to do this :S

Can someone explain how to do this or find a different link please. I have been looking for days and am moments away from giving up with Ubunut :(

thanks

---

### Post by stormblue on 2006-08-04
I believe there are two versions of the card.  Is the front of your card red, blue, and white or is it blue and gray?

If it is red, blue, and white you already have the drivers installed as it uses the prism chipset.  I'm unfamiliar with the blue and gray card.

Give us the output of 
```

sudo iwconfig
```

---

### Post by spamzilla on 2006-08-04
I have the blue and gray version.

When I type that command in, I get the following:

> 
lo      no wireless extension

eth0    no wireless extension

ra0 RT2400PCI ESSID: off/any
    Mode= managed  channel= 1   Bite Rate=1 1 mb/s
    RTS tro: off     Fragment thr: off
    Encryption key: off
    Link Quality= 0 Signal level= 0 Noise level= 0
    Rx invalid nwid: 0 invalid crypt: 0 invalid misc= 0

sit0  no wireless extension


I don't even get the green light to come on when i plug the card in :/

---

### Post by stormblue on 2006-08-04
In the terminal type

```
sudo ifconfig ra0 up
```

That should get it to light up.

---

### Post by spamzilla on 2006-08-04
Yup that got the light to show up, thanks :)

In the Network tools program, I added a valid IP address, and my routers default gateway and subnet mask. The ra0 thing activated, and then I tried to connect to the Internet and failed. I also entered my LAN IP info and still couldn't connect to the internet :(

Is there something else I need to do?

---

### Post by stormblue on 2006-08-04
This is how I get the internet working.  I never could get the GUI tools to work in gnome.

sudo ifconfig ra0 up
sudo iwconfig ra0 essid network_name
sudo dhclient ra0

Run the commands in that order and you should get 'er up and running just fine.  If you need WEP let me know, it's just one more command.

---

### Post by spamzilla on 2006-08-04
Yeah I protected my connection with WEP. Can I have that command please.

Thanks a lot, you're a :KS!!

---

### Post by stormblue on 2006-08-04
between the essid key and the dhclient command type
```

sudo iwconfig ra0 key network_key

```

---

### Post by spamzilla on 2006-08-04
Excellent! I'll post back here after I have run those commands :D

Thanks again!!!

---

### Post by spamzilla on 2006-08-04
That didn't work *confused*


After  
I typed in sudo dhclient ra0, I got the following 


===================================================

Listening on LPF/ra0/04:e2:d3:a1:fd
Sending on LPF/ra0/04:e2:d3:a1:fd
Sending on socket/fallback
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9 DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 19 5DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16 5DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
NO DHCPOFFERS received
Trying release 192.168.1.3
Ping 192.168.1.1 56 bytes of data

Ping stats
1 packet sent, 0 received, 1+ errors 100% packet loss time 0sec

No working lease in persistent database - sleeping

===========================================================

Can anyone tell me how to fix this please?

Thanks :)

---

### Post by stormblue on 2006-08-04
Check your router to make sure DHCP is turned on and it isn't mac addresses filtered or something.

---

### Post by spamzilla on 2006-08-04
The only DHCP setting I could find was "Enable DHCP Server" which was already enabled. Is there another setting I need to enable, or is that the correct one?

---

### Post by stormblue on 2006-08-04
No, that's right.  I've had that happen to with my wireless router.  I don't know what the cause is.  It wouldn't happen to be a netgear wgr614v6 would it ?

Sometimes it happens when the antenna is pointed away from the card.

---

### Post by spamzilla on 2006-08-05
I have a safecom SWAMR-54108 wireless router and the antenna isn't pointed away from my card.

It would seem that I spelled "SWAMR" wrong when entering my essid in the terminal, and when I corrected this, I got assigned an IP address, broadcast address and gateway. However, when I try to connect to the internet, my connection times out, but I can ping my ip address and gateway successfully :/

Did I need to install the cards driver? I think I have the correct driver sat on my laptop, but I have no idea if I need to install it, or even, HOW to install it!

Does anyone have any solutions to my problems?

Cheers

---

### Post by stormblue on 2006-08-05
If you can ping your router, I would think you would have the right drivers installed.

Try to ping 72.14.207.104 and if you can ping it try to load [http://72.14.207.104](http://72.14.207.104) in firefox.  Let me know how this goes.

---

### Post by spamzilla on 2006-08-05
Pinging to that IP address failed both times :(

If this means I need to install a driver, how do I actually install it?

Thanks :)

---

### Post by spamzilla on 2006-08-06
Can anyone help me out please :D 

Thanks

---

### Post by gannic on 2006-08-06
There is Mac Address control on that router - you need to make sure it is disabled for the time being. You can turn it back on later.

YOu say you can ping your router - Can you log into your router?

If so your problem probably lies with the router connecting to the internet - not your wireless card. Have you got this router connecting to the internet with any other computer or network card. I have one of these so I may be able to help.

---

### Post by stormblue on 2006-08-06
What Gannic said is right.

Now we just need to figure out why you can't get on the internet.  It's not a DNS issue, as the IP I gave you was to google.  

You could try removing the router and setting it up with just the information the ISP gave you and just connect your computer to the modem.  On the other hand you could also try taking that information and setting up your router with it.  Do you need a log in or password?

---

### Post by spamzilla on 2006-08-06
I CAN login into and ping my router! What is odd is that I successfully visited zoints.com, but the page loaded up really slowly. No other page would load up, and I would get a connection time out error :/

I use this NIC when I use Windows XP and I have no problems connecting to the internet. The router also works like a charm connecting my Dad's PC (directly) to the internet, and my bro's laptop to the internet (wireless connection). 

There is no point me taking out the router and connecting to the internet via a modem, as I will always be connecting via wireless, when using my laptop. So it's best I sort out the wireless problem :P

i am clueless how to sort this out :( I'd also like to say that the help you guys are giving me is excellent, and I really appreciate it :mrgreen: I just hope that both of your vast knowledge can solve my problem!!!

Cheers

---

### Post by stormblue on 2006-08-06
So it has to be a wireless issue on your laptop.  Try giving us the output of iwconfig ra0 , ifconfig ra0 , and iwlist ra0 scan.

Turn wep off if you have it on just so we can test this and then run these commands:
```

sudo ifconfig ra0 up
sudo iwconfig ra0 essid network_name
sudo dhclient ra0 

```
and see what you can get out of it.

---

### Post by spamzilla on 2006-08-06
Hey

Right, this is what I got after entering the commands into Terminal

Listening on LPF/ra0/04:e2:d3:a1:fd
Sending on LPF/ra0/04:e2:d3:a1:fd
Sending on socket/fallback
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCP from [router ip] 
Bound [my ip address]-- renewal 241661 seconds

A few question:

I made my IP a static one. Should it be a static address or DHCP?

Is there any software I am overlooking built into Ubuntu to connect to my wireless connection?

Why am I trying to connect to port 67? Isn't WWW access port 80, or does this only apply to Windows?

Cheers :)

---

### Post by stormblue on 2006-08-06
You should be connected then.

1. It doesn't matter if it is static or DHCP under most circumstances.  Just make sure that if it's static, it's configured in the networkwing config or your interfaces files and if not you're going to have to run DHCP.  On the other hand if you have both static and dynamic IP's on a network you may run into problems with a static IP requesting an IP that is already given out via DHCP.   A way to avoid this is to set your DHCP settings above something like 192.168.1.100 and then set all your static settings <99

2.  there is nm-applet.  There is also system -> admistration -> networking to configure it.  You can use wifi-radar as well, which has worked for me in the past.

3. All http traffic goes over port 80 by defualt.  This can be changed.  Port 67 is used for DHCP requests.  Is that where you saw it?

---

### Post by spamzilla on 2006-08-06
So why can't I browse any websites then *confused* I'll play around with some settings to see if I can get things to work.

Hmm ok I'll change my IP address to over .100

I was using Networking to configure everything to begin with and the program is pretty good!

Yeah that's where I saw it. I have never come across connecting to the internet via port 67! I guess you learn somethinmg new every day ;)

---

### Post by stormblue on 2006-08-06
I would stick with DHCP that way we know it works.  It easiest to build upon something we know that works.  I have no idea what could be wrong at this point.  You were once able to access the internet, you can connect to your router.  Have you tried using an ethernet cord to the router and/or using just the modem to connect to the internet?

---

### Post by spamzilla on 2006-08-07
I couldn't connect to the internet via an ethernet cable plugged in to my router either. I tried various settings and nothing seems to work :(

I could login to my router though :confused:

---

### Post by gannic on 2006-08-07
Just to clarify, I am not an expert...at anything as far as I know. However I do have the same safecom router and 2 windows and 2 wireless Ubuntus? connecting to it. It is from this questionable platform I am talking. Much of this came about more through luck than judgement.

There are a number of settings on the router that might cause the affect you are experiencing, but it seems unlikely you enabled them without knowing it. To save stormblue's sanity and just check (I am 3 days old in Ubuntu - so cant help much with that) - I would do the following - sorry if you already have...

This router is great but has a few interesting "features" - if you can - the first thing I would do is make sure you have the latest firmware. It reduces the unintentional "features" and adds a few deliberate ones. Your issue here is that everyone else is happy with how the router is working so you have to tread carefully. In fact I would note down every setting you change.

Log into the router...
Toolbox > Backup Setting 
This will save a configfile of your current settings. I have never has to restore one so cant guarantee it works.

Check your wireless key. The most reliable way to do this is to copy it straight off the router..in Basic Setting > Wireless > Security and into a notepad document on a USB stick or something.  Then copy it straight in to the appropriate key textbox in network manager.

**OPTIONAL**
You may end up battering everone elses connections if you do this, but providing you reset everything exactly as before you should be OK.

Turn off wireless encryption (unplug the internet/phoneline if you are worried about someone using your interenet connection while WEP is turned off)....

Basic Settings > Wireless > Security - None
**OPTIONAL END**

As stormblue said - if you have been using static IPs...

In Basic Settings > DHCP Server 
Make sure enable is checked

In Basic Settings > DHCP Server 
IP Pool Starting Address <set to a value above all your static addresses>

In Basic Settings > DHCP Server 
IP Pool Ending Address <set to a value (at least 10) above the starting value>

Save and Reboot - buttons at foot of page.

Then...in Basic Setting > Wireless...
You will see a button "MAC address control" at the foot of the page.

Click on this and then in the page...
uncheck enable.
uncheck connection control.
uncheck association control.

Save and reboot the rooter (buttons at foot of page)

Now - preferably without any other computers connected - login to the router via wireless. 

If this is successful again...plug the phoneline/www back into the router and try google. Try a few other pages...if it works you may wish to unplug the phoneline again while you reenable WEP.

To do this...

Basic Setting > Wireless <and under "security" choose the option you had checked before.>

Some of your findings so far do not tally with this being a router problem, but some of them do. So its worth a go.

---

### Post by spamzilla on 2006-08-07
Ok thanks. I'll try this as soon as the PC is free!

Cheers

---

### Post by spamzilla on 2006-08-08
I changed all of those settings, and I now get a "connection has timed out" error page, when trying to connect to google.com and other sites. I can connect easily when I use windows.

---

### Post by stormblue on 2006-08-08
try removing the router from the network and plugging straight into the modem.  Then run the following:

```
sudo ifconfig eth0 up
sudo dhclient eth0
```

Let me know if that gets you online.

---

### Post by gannic on 2006-08-08
Are you still able to log in to your router using wireless?

Also, can I confirm - are you saying that even when WEP is on you can connect to the router and alter settings?

---

### Post by spamzilla on 2006-08-08
My router is a router/modem *confused* but I'll try the other modem any way.

I'll check on the WEP asap :)

---

### Post by stormblue on 2006-08-08
Oh, it's a router/modem combo?

Nevermind then.  I don't mean dial-up modem.

---

### Post by spamzilla on 2006-08-08
I couldn't login to my router with WEP on. Sorry i didn't say this earlier :(

---

### Post by stormblue on 2006-08-08
Okay keep wep off and DHCP on and see if you can connect to your router and change settings.

This is correct right?

---

### Post by WalmartSniperLX on 2006-08-09
Hey i have kernel version 2.6.15-26-386 will ndiswrapper work for me?

---

