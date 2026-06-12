---
title: "Setting up another computer with wireless"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by hector24 on 2009-08-17
I know a kind person has explained all this elsewhere but I need to have it in Absolute Beginner language please:

I have Ubuntu on my desktop computer.  This is wired to a router and I have internet connection.

Now I want to add my laptop to the wireless connection so I can use this anywhere in the house.  I have put in all the details on the laptop.  It's connected to the wireless OK but when I try to go online it says 'cannot find server'.  

I added this laptop and had wireless connection when I had MS windows - it told you to put a memory stick in the main computer and transfer the information across (the laptop had to be re-built recently - by the IT manager at my work - so all the connections have been wiped).  There's nothing like that in Ubuntu and I haven't the know how to proceed.

Can anyone help, please?

---

### Post by ZankerH on 2009-08-17
You can probably configure the router from your desktop computer by opening an internet browser (ie Firefox) and typing "192.168.1.1" (without the quotes) into the address bar. The configuration, however, depends on the model of router you have.

---

### Post by 3rdalbum on 2009-08-17
If you can successfully ping this IP address from your laptop:

```
ping 66.102.11.99
```

Then you need to put the DNS addresses into your laptop's configuration. You should be able to obtain your ISP's DNS address from your ISP's website or from the router's configuration panel (the one that you open from your web browser). Find the DNS addresses and put it into Network Manager under the wireless connection (IPv4 settings tab).

---

### Post by mapes12 on 2009-08-17
> **hector24 said:**
> I know a kind person has explained all this elsewhere but I need to have it in Absolute Beginner language please:

I have Ubuntu on my desktop computer.  This is wired to a router and I have internet connection.

Now I want to add my laptop to the wireless connection so I can use this anywhere in the house.  I have put in all the details on the laptop.  It's connected to the wireless OK but when I try to go online it says 'cannot find server'.  

I added this laptop and had wireless connection when I had MS windows - it told you to put a memory stick in the main computer and transfer the information across (the laptop had to be re-built recently - by the IT manager at my work - so all the connections have been wiped).  There's nothing like that in Ubuntu and I haven't the know how to proceed.

Can anyone help, please?

Given that your wired connection can access the internet I don't think your router has any DNS issues. Sometimes a wifi device lights up and gives the impression that it's connected when really it isn't. If it's an internal device in Terminal ```
lspci
``` If it's a USB device ```
lsusb
```Also, let's do the first connection test in Terminal ```
ping 127.0.0.1 -c4
``` and post the ouptut back here. You can also check the external IP address of your router by going here: [http://whatismyipaddress.com/](http://whatismyipaddress.com/) Try pinging that too.

---

### Post by 3rdalbum on 2009-08-17
> **mapes12 said:**
> Given that your wired connection can access the internet I don't think your router has any DNS issues.

I've had the situation before where the router's DHCP is not understood by all the computers on the network, and the DNS is either not sent or not recieved by the client. But you have given some excellent suggestions.

---

### Post by molan on 2009-08-17
As another newbie, first, go into your router with your known working computer and copy down the settings that will be needed: SSID, whether or not the SSID is broadcast, the type of encryption that you may have on the wireless router, etc.
 
Now, first thing on your laptop, does it have an external button to turn the wireless on/off and is it in the "on" position? Not trying to offend, just trying to run through some of the simplest things so that everything can be covered. :)

---

### Post by hector24 on 2009-08-19
Not at all offended.  In fact I need more help at this level.

Yes, I've tried clicking the 'aerial' button.

I've tried the other advice but I must be doing something wrong.  I cannot access anything by putting 192.168.1.1 into my desktop browser.  I tried with and without [http://.](http://.)  'Oops, link appears to be broken' came up.

I cannot ping anything on my laptop (I think I've done this right - in start..> run??).  The screen just goes blank.

I'd be grateful for any help, but in very basic terms please.

Thanks.

---

### Post by SuaSwe on 2009-08-19
Some routers' IP addresses are 192.168.2.1 (e.g. Belkin), or 192.168.0.1 (e.g. NETGEAR). Try these and if it doesn't work, continue on...

First, make sure that the desktop is connected and getting webpages. 

XP
Start -> Run -> cmd -> type in 'ipconfig /all' (no quotes) and find the 'Default Gateway' number; that's your router's IP address that you need to access in your browser.

Vista
Start -> All Programs -> Accessories -> *right-click* on Command Prompt and select 'Run as administrator'. Type in 'ipconfig /all' (no quotes) and find 'Default Gateway'. Again this is the number you need to access your router.

Ubuntu
Go to Terminal, type in 'route' or possibly 'sudo route' (no quotes, of course) and you should find it in there.

What type of router are you using, by the way?

---

### Post by hector24 on 2009-08-19
Many thanks.  That's clear to me and it worked.  My IP address on the desktop is 192.168.10 but on my laptop it's 192.168.0.1.  Should they be different?

My router came with the Tiscali package.  It's a SpeedTouch FCCA7B.

---

### Post by hector24 on 2009-08-19
Hi - I was ambiguous.  When I said 'it worked' I meant the command.  I still can't connect to the internet.  Keeps saying 'cannot find server'.

---

### Post by LewRockwell on 2009-08-19
> **hector24 said:**
> Many thanks.  That's clear to me and it worked.  My IP address on the desktop is 192.168.10 but on my laptop it's 192.168.0.1.  Should they be different?

My router came with the Tiscali package.  It's a SpeedTouch FCCA7B.

The IP address of the default gateway should be properly entered/listed in every device/operating system on the secure side of the LAN

Above, you state that in your correctly configured desktop the gateway is entered as "192.168.10" and your laptop is incorrectly configured to "192.168.0.1"

One other note, regardless of when or how you correct this particular trouble-call, you should learn how to correctly configure your LAN devices such as any configurable modems, routers, switches, etc.

To that end, the internet is overflowing with information on specific units and various tutorials geared towards all skill levels

.

---

### Post by amsum on 2009-08-19
> **hector24 said:**
> I know a kind person has explained all this elsewhere but I need to have it in Absolute Beginner language please:

I have Ubuntu on my desktop computer.  This is wired to a router and I have internet connection.

Now I want to add my laptop to the wireless connection so I can use this anywhere in the house.  I have put in all the details on the laptop.  It's connected to the wireless OK but when I try to go online it says 'cannot find server'.  

I added this laptop and had wireless connection when I had MS windows - it told you to put a memory stick in the main computer and transfer the information across (the laptop had to be re-built recently - by the IT manager at my work - so all the connections have been wiped).  There's nothing like that in Ubuntu and I haven't the know how to proceed.

Can anyone help, please?

Well, which version of Ubuntu you are using?
Also, if I am not wrong you have ubuntu on both Desktop and laptop now; and your desktop with wired connection is getting internet?

---

### Post by grappler on 2009-08-19
How did you try to connect to your router - it is not clear to me from the previous interactions. 

Did you use the gnome network manager? I don't understand your IP addresses. 192.168.0.1 seems to me to be a router IP address rather than one of your computers. 192.168.10 is not a correctly formed IP address - do you mean 192.168.0.10? 

What kind of security is your router running - I'm guessing WPA - the information for connections on the memory stick would presumably a long password of some kind. 

The gnome network manager is pretty easy to configure. If you have it running in the panel and click on it it should show the list of available wireless networks - including your router. If you click on that it will try to connect and at some stage ask for a password - usually with a guess of what kind of security your router uses. It doesn't always get that  right but it discriminates well between WEP and WPA. 

If the wireless connection is  really there - try pinging 192.168.0.1 to check - then it sounds like a DNS issue. Try right clicking on the network-manage icon in the panel, and select "Edit Connections" Click on the "Wireless" tab and it should have your router listed as "Auto <name of your network>". Click on that and it will open a dialog box. Click on ipv4 settings Click on the pull-down menu alongside "Method" and select "Automatic (DHCP) Addresses Only" and enter in the DNS Servers box the IP address of your router - which I'm guessing is 192.168.0.1. Click on "Apply" and try to reconnect.
Then try to recon

---

### Post by LewRockwell on 2009-08-19
hopefully the OP is finding success as we key...

.

---

### Post by hector24 on 2009-08-20
When I try to connect to the internet the message says 'unknown protocol'.  Is that something I can fix myself?  I'd be grateful for help with this.

---

### Post by hector24 on 2009-08-20
Massive loss of confidence here.  I really am finding this very hard to follow.  I'm very grateful for everyone's help, though.

I had Ubuntu installed on my desktop (not my laptop, that's XP) only because my sons managed to keep downloading viruses on XP.  it sounded like a good idea at the time.  I have internet access on my desktop but the computer is plugged into the router.  Ubuntu seemed to connect me to the internet without my having to do anything.  

The LAN settings on my laptop are all correct - there is no choice here as the proxy server box has to be de-selected and then the other boxes are greyed out automatically.  I do know this is correct as I've just had it demonstrated by the IT manager this morning at work and it was how it was set before the laptop crashed and had to be re-built.  It's only since this that I've not been able to connect to the wireless at home.  He connected to the wireless network at work with no difficulty.    

I don't know what gnome is or how to access it.  Sorry.  When I pinged 192.168.0.1 into the desktop it told me there were 58 bytes of data.

My IT manager at work did not know why I shouldn't be able to connect to the internet via wireless at home.  

I need to be able to use XP (via my laptop) to work from home.

Am I better off putting XP back on my desktop?  I think you need a lot more basic computing knowledge to use Ubuntu than I have.

---

### Post by SuaSwe on 2009-08-20
OK, so to confirm: your laptop is XP and it is getting webpages OK?

If so, please do this (ensure that it's getting webpages first by opening IE or any other browser, then click on a link once loaded so we know it's not working offline):

Start -> Run -> type in cmd, press OK

Type in 'ipconfig /all' (no quotes), find the IP address, subnet mask and default gateway listed there and paste them in here (mind the dots, they need to be in the right place otherwise it won't make sense!).

SpeedTouch routers generally have an IP address (the router's IP address is what your computer thinks of as the "default gateway") of 192.168.1.254, but checking what default gateway your working computer is picking up will tell us for sure.

Don't give up on Ubuntu just yet, it can be daunting to set up but it's worth it in the end!

---

### Post by chris1950 on 2009-08-20
Have same(error) problem. VISTA(Desktop) can see (manipulate shared files) on Laptop (Ubuntu) but laptop can not see Desktop. Laptop is wireless desktop is wired to wireless router. Both have Internet access.

---

### Post by SuaSwe on 2009-08-20
Just reread the message above my last one and to be honest I'm a little confused.

hector24, could you answer these questions:

1. Which PC (e.g. which OS) works, and which one doesn't? If one or both is having problems with wireless but not ethernet or vice versa, please indicate.

2. Or, can both computers connect via ethernet?

3. If it's merely a wireless issue you have, you need to check a) your router settings, and b) your PC's WLAN settings. So, we need your default gateway (that's the router's IP - it may be on the underside of your router, and very probably it's 192.168.1.254), and we need to know which OS is having problems with the wireless. 

From what I gather this is an XP issue and not a Ubuntu one (Ubuntu is working fine, I gather?) but I'm happy to try and help as I'm pretty clued up about XP and its various wireless misbehaviours. Feel free to PM me if you like. :)


Edit: Read opening post and now I'm even less sure what OS you're using. :D Happy to assist as best I can as soon as I find out what you're running on the PC that is working, vs on the PC that isn't, and exactly what isn't working on both/either.

---

### Post by mapes12 on 2009-08-21
> **hector24 said:**
> Massive loss of confidence here.  I really am finding this very hard to follow.  I'm very grateful for everyone's help, though.

I had Ubuntu installed on my desktop (not my laptop, that's XP) only because my sons managed to keep downloading viruses on XP.  it sounded like a good idea at the time.  I have internet access on my desktop but the computer is plugged into the router.  Ubuntu seemed to connect me to the internet without my having to do anything.  

The LAN settings on my laptop are all correct - there is no choice here as the proxy server box has to be de-selected and then the other boxes are greyed out automatically.  I do know this is correct as I've just had it demonstrated by the IT manager this morning at work and it was how it was set before the laptop crashed and had to be re-built.  It's only since this that I've not been able to connect to the wireless at home.  He connected to the wireless network at work with no difficulty.    

I don't know what gnome is or how to access it.  Sorry.  When I pinged 192.168.0.1 into the desktop it told me there were 58 bytes of data.

My IT manager at work did not know why I shouldn't be able to connect to the internet via wireless at home.  

I need to be able to use XP (via my laptop) to work from home.

Am I better off putting XP back on my desktop?  I think you need a lot more basic computing knowledge to use Ubuntu than I have.Your other posts gave me the impression you had Ubu on your laptop and you had difficulty connecting with wifi at home. Now your posting XP on your laptop and the IT Manager can connect. Of course he can cos he's using XP which will have wifi driver support for wifi adapter. If you also have Ubu on the laptop and you need help connecting wifi then please post the outputs to the Terminal commands from post #4.

---

### Post by hector24 on 2009-08-21
I'll try to be really clear.

My desktop: I have a desktop (Dell Pentium 4 HT) on which Ubuntu (issue 9.04) has been installed.  It is wired to the router and I have internet connection with no problems.

My laptop: I have a work laptop (Dell Inspiron, 6400, with Windows XP).  I cannot get online via wireless on my laptop.  I can at work.  At home the laptop connects to our wireless router (on 'wireless network connection' it reads: 'SpeedTouchFCCA7B Security-enabled wireles network, Connected').  However, when I click Internet Explorer the message that comes up says: 'The page cannot be displayed', and at the bottom of the screen it says 'Cannot find server'.  When I click File and Properties it says: 'Cannot find server, Unknown Protocol'.  My LAN setting I know to be correct; I have no choice here.  The way the system is set up, to use internet at home I have to deselect 'Use a proxy server...'  at which all other options are greyed out.  

Previously: I had wireless connection with this laptop which I set up when I had XP on my desktop.  Recently my laptop became corrupted and had to be re-built (if that's the right expression).  Now I cannot get it to connect to the server at home.

I need my laptop to work from home: my work system is not accessible via Ubuntu (it is too 'buggie'? evidently).

I'm grateful for your help and encouragement (much needed).  If anyone does have any advice can you please tell me where I access/enter the information you suggest?  Many, many thanks.

---

### Post by SuaSwe on 2009-08-21
NB: Heretoforth I shall ignore your Ubuntu PC, so whenever I say "your computer" I'm referring to your work laptop.


Right-o! *rubbing hands together* I need you to check a few things:

First and foremost: can you connect and get webpages with your computer when connected with an ethernet cable? If you haven't tried, please do so first of all and let me know how it went (you may need to power off the router and the computer then power first the router then the computer back on, however with ADSL this is generally not necessary).

Now, you say that your wireless definitely connects to your wireless network, and says "connected"? Good! Provided that this is the case, please do the following:

- After connecting to the wireless connection, go to Start -> Run -> type in 'cmd' (no quotes), press OK. In the little black window, type:

```

ipconfig /all

```

then press Enter, then do

```

ping 192.168.1.254

```

then Enter, then

```

ping 213.177.33.151

```

then Enter, then

```

ping www.lego.com

```

then Enter. Finally, click in the top left-hand corner of the Command Prompt box. A menu should come up where you want to select Edit -> Select all. When everything is white, press the corner and do Edit -> Copy. Paste all that text in here for our perusing. :)

Note: all these commands need to be typed in *exactly* as above so mind the dots and spaces!

---

### Post by hector24 on 2009-08-21
Thank you for the instructions.  Here are the results:

  	 	 	 	 	 	  Microsoft Windows XP [Version 5.1.2600]
 (C) Copyright 1985-2001 Microsoft Corp.
 

 N:\>ipconfig /all
 

 Windows IP Configuration
 

         Host Name . . . . . . . . . . . . : cg-laptop-cc3
         Primary Dns Suffix  . . . . . . . : SALESIAN.internal
         Node Type . . . . . . . . . . . . : Unknown
         IP Routing Enabled. . . . . . . . : Yes
         WINS Proxy Enabled. . . . . . . . : No
         DNS Suffix Search List. . . . . . : SALESIAN.internal
                                             lan
 

 Ethernet adapter Local Area Connection:
 

         Connection-specific DNS Suffix  . : lan
         Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Cont
 roller
         Physical Address. . . . . . . . . : 00-15-C5-B9-8E-3C
         Dhcp Enabled. . . . . . . . . . . : Yes
         Autoconfiguration Enabled . . . . : Yes
         IP Address. . . . . . . . . . . . : 192.168.1.65
         Subnet Mask . . . . . . . . . . . : 255.255.255.0
         Default Gateway . . . . . . . . . : 192.168.1.254
         DHCP Server . . . . . . . . . . . : 192.168.1.254
         DNS Servers . . . . . . . . . . . : 192.168.1.254
         Lease Obtained. . . . . . . . . . : 21 August 2009 21:36:13
         Lease Expires . . . . . . . . . . : 22 August 2009 21:36:13
 

 Ethernet adapter Wireless Network Connection:
 

         Connection-specific DNS Suffix  . :
         Description . . . . . . . . . . . : Intel(R) PRO/Wireless 3945ABG Networ
 k Connection
         Physical Address. . . . . . . . . : 00-18-DE-80-FF-49
         Dhcp Enabled. . . . . . . . . . . : No
         IP Address. . . . . . . . . . . . : 192.168.0.1
         Subnet Mask . . . . . . . . . . . : 255.255.255.0
         Default Gateway . . . . . . . . . :
 

 N:\>ping 192.168.1.254
 

 Pinging 192.168.1.254 with 32 bytes of data:
 

 Reply from 192.168.1.254: bytes=32 time=1ms TTL=64
 Reply from 192.168.1.254: bytes=32 time<1ms TTL=64
 Reply from 192.168.1.254: bytes=32 time<1ms TTL=64
 Reply from 192.168.1.254: bytes=32 time<1ms TTL=64
 

 Ping statistics for 192.168.1.254:
     Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
 Approximate round trip times in milli-seconds:
     Minimum = 0ms, Maximum = 1ms, Average = 0ms
 

 N:\>ping 213.177.33.151
 

 Pinging 213.177.33.151 with 32 bytes of data:
 

 Reply from 213.177.33.151: bytes=32 time=46ms TTL=245
 Reply from 213.177.33.151: bytes=32 time=37ms TTL=245
 Reply from 213.177.33.151: bytes=32 time=38ms TTL=245
 Reply from 213.177.33.151: bytes=32 time=37ms TTL=245
 

 Ping statistics for 213.177.33.151:
     Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
 Approximate round trip times in milli-seconds:
     Minimum = 37ms, Maximum = 46ms, Average = 39ms
 

 N:\>ping [www.lego.com](www.lego.com)
 

 Pinging [www.gslb.lego.com](www.gslb.lego.com) [213.177.33.151] with 32 bytes of data:
 

 Reply from 213.177.33.151: bytes=32 time=38ms TTL=245
 Reply from 213.177.33.151: bytes=32 time=38ms TTL=245
 Reply from 213.177.33.151: bytes=32 time=39ms TTL=245
 Reply from 213.177.33.151: bytes=32 time=37ms TTL=245
 

 Ping statistics for 213.177.33.151:
     Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
 Approximate round trip times in milli-seconds:
     Minimum = 37ms, Maximum = 39ms, Average = 38ms
 

 N:\>

---

### Post by flux_user on 2009-08-21
Before we start there are several steps that have to be done.  I personally suggest that you make several posts about each topic and work your way up until you get a working internet connection.  Doing it this way on large post; will get confusing for all the participants.  

Below is a summary of what has to be done.

There are a couple of things that need to be checked:

**Wirless in Ubuntu**
[LIST=1]
[*]Does your wireless card work in Ubuntu?
[/LIST]

**Router  Configuration**
[LIST=1]
[*]Is your wireless enabled on your router?
[*]Does wireless router have MAC address filtering turned on?  If so you need the MAC address from your wireless card in Ubuntu
[*] What about a passphrase  setting in your router and Ubuntu.
[/LIST]

[B]Getting your Laptop and Router to talk to each other.
[/B]
[LIST=1]
[*]MAC Filtering
[*]Encryption & Authenticaion (router and ubuntu)
[*]Passphrase (router  and Ubuntu)
[/LIST]

Before anything we have to know that Ubuntu knows about your wireless card.

/sbin/ifconfig 

Look for a section called wlan0.  If that exists then we can move onto the next step.  If your wireless card doesn't exist post a new subject say wireless help card not recognised.

Like I said there is a lot to be done and this should be handled in small steps so that things don't get too long and confusing.  If  a post runs on too long; some helpers may not have the tenacity to work all the way through it.  Also if a post is too long; new people may not read the 100 pages prior to your current situation.  In essence:  Do small steps; and work your way up.  Start with your wireless card.  Does Ubuntu / Linux recognise your card.

/sbin/ifconfig 

or 

/sbin/ifconfig | grep wlan0

I personally suggest:

/sbin/ifconfig | grep wlan0

if you see something on screen; then your wireless card is seen.

Move to section 2.

---

### Post by SuaSwe on 2009-08-21
This is an XP issue. Ubuntu is on ethernet and working fine, from what I gather!


Now, looking at what you posted there, your default gateway (your router's IP) is indeed 192.168.1.254. You can ping the router, IP addresses (Lego's in this case) and URL's with the setup you had whilst running the tests - looks like you had the ethernet cable connected at the time. 

Your wireless network connection on the other hand has not picked up the default gateway. Please go into Network Connections, right-click on the Local Area Connection and disable it (if you need it back in future, simply right-click and enable again). Then right-click on the Wireless Network Connection, click Properties, find 'Internet Protocol (TCP/IP)' in the list in the middle and double-click it. Ensure that both 'Obtain IP addresses automatically' and 'Obtain DNS server addresses automatically' are selected. Once confirmed, ensure that your wireless connection is connected to the SpeedTouch, then rerun the tests listed in my previous post.

In case it's also a browser issue, please answer the following:
- Have you tried any other internet browser?
- Have you removed any proxies and automatic configuration scripts (in IE, go to Tools -> Internet Options -> Connections -> LAN Settings -> untick everything and press OK, Apply, OK again)?
- Are you using any firewalls, like Norton or ZoneAlarm?
- Can you browse webpages at work? Do you know what type of internet connection you use there, e.g. LAN, wireless router, VPN?

On standby, awaiting further info!

---

### Post by hector24 on 2009-08-22
[quote=SuaSwe;7825722]This is an XP issue. Ubuntu is on ethernet and working fine, from what I gather!


"Now, looking at what you posted there, your default gateway (your router's IP) is indeed 192.168.1.254. You can ping the router, IP addresses (Lego's in this case) and URL's with the setup you had whilst running the tests - looks like you had the ethernet cable connected at the time. 

Your wireless network connection on the other hand has not picked up the default gateway. Please go into Network Connections, right-click on the Local Area Connection and disable it (if you need it back in future, simply right-click and enable again). Then right-click on the Wireless Network Connection, click Properties, find 'Internet Protocol (TCP/IP)' in the list in the middle and double-click it. Ensure that both 'Obtain IP addresses automatically' and 'Obtain DNS server addresses automatically' are selected. Once confirmed, ensure that your wireless connection is connected to the SpeedTouch, 
then rerun the tests listed in my previous post."

Many thanks.  I can't right click anything from Network Connections, but if I go to Internet Options, Connections, LAN settings, the proxy server is deselected already.  I must have a different set up from you; I can't right click anything on Network Connections and there is no button for Properties for Wireless Network Connection.  

"In case it's also a browser issue, please answer the following:
- Have you tried any other internet browser?
- Have you removed any proxies and automatic configuration scripts (in IE, go to Tools -> Internet Options -> Connections -> LAN Settings -> untick everything and press OK, Apply, OK again)?
- Are you using any firewalls, like Norton or ZoneAlarm?
- Can you browse webpages at work? Do you know what type of internet connection you use there, e.g. LAN, wireless router, VPN?"

I've tried connecting to work files which I don't think use Internet Explorer, but no luck there.  I've removed IE.  There's Norton on the system.  I can browse web pages at work.  I'm not sure what the sytem we use is but there's wireless connection and I think I have to re-check LAN, use proxy server.

---

### Post by hector24 on 2009-08-22
> **flux_user said:**
> 

/sbin/ifconfig 

or 

/sbin/ifconfig | grep wlan0

I personally suggest:

/sbin/ifconfig | grep wlan0

if you see something on screen; then your wireless card is seen.

Move to section 2.

Thanks for your help.  I got something up when I put /sbin/ifconfig.  I know the router is OK because my husband can get connected wirelessly with his laptop.

---

### Post by SuaSwe on 2009-08-22
Network Connections should list all network connections set up on your machine; if they're not showing in there then there will be something seriously wrong. 

Try Start -> Run -> type in 'ncpa.cpl' (no quotes), or
Start -> Control Panel -> **ensure that Classic View is selected top-left**, find and click Network Connections

In there you must have both your Local Area Connection and your Wireless Network Connection. If they are not in there then you can't change the properties of the connection (in fact, you shouldn't even be able to connect) and we'll never be able to get the wireless set up and working. 

See if you can find Network Connections, then re-run those ipconfig and ping tests from a previous post of mine with only the wireless connected (e.g. no ethernet cables running from the computer to any router).

---

### Post by hector24 on 2009-08-22
Will do.  I was looking in the wrong place!  Thank you for your help.

When I try to connect to wireless it's now saying 'limited or no connectivity'.  When I click repair there's a long delay before it says it can't renew my IP address.  Here's what came up when I entered your commands:

  	 	 	 	 	 	  Microsoft Windows XP [Version 5.1.2600]
 (C) Copyright 1985-2001 Microsoft Corp.
 

 N:\>ipconfig/ all
 

 Error: unrecongnized or incomplete command line.
 

 USAGE:
     ipconfig [/? | /all | /renew [adapter] | /release [adapter] |
               /flushdns | /displaydns | /registerdns |
               /showclassid adapter |
               /setclassid adapter [classid] ]
 

 where
     adapter         Connection name
                    (wildcard characters * and ? allowed, see examples)
 

     Options:
        /?           Display this help message
        /all         Display full configuration information.
        /release     Release the IP address for the specified adapter.
        /renew       Renew the IP address for the specified adapter.
        /flushdns    Purges the DNS Resolver cache.
        /registerdns Refreshes all DHCP leases and re-registers DNS names
        /displaydns  Display the contents of the DNS Resolver Cache.
        /showclassid Displays all the dhcp class IDs allowed for adapter.
        /setclassid  Modifies the dhcp class id.
 

 The default is to display only the IP address, subnet mask and
 default gateway for each adapter bound to TCP/IP.
 

 For Release and Renew, if no adapter name is specified, then the IP address
 leases for all adapters bound to TCP/IP will be released or renewed.
 

 For Setclassid, if no ClassId is specified, then the ClassId is removed.
 

 Examples:
     > ipconfig                   ... Show information.
     > ipconfig /all              ... Show detailed information
     > ipconfig /renew            ... renew all adapters
     > ipconfig /renew EL*        ... renew any connection that has its
                                      name starting with EL
     > ipconfig /release *Con*    ... release all matching connections,
                                      eg. "Local Area Connection 1" or
                                          "Local Area Connection 2"
 

 N:\>ping 192.168.1.254
 

 Pinging 192.168.1.254 with 32 bytes of data:
 

 Destination host unreachable.
 Destination host unreachable.
 Destination host unreachable.
 Destination host unreachable.
 

 Ping statistics for 192.168.1.254:
     Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),
 

 N:\>ping 213.177.33.151
 

 Pinging 213.177.33.151 with 32 bytes of data:
 

 Destination host unreachable.
 Destination host unreachable.
 Destination host unreachable.
 Destination host unreachable.
 

 Ping statistics for 213.177.33.151:
     Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),
 

 N:\>ping [www.lego.com](www.lego.com)
 Ping request could not find host [www.lego.com](www.lego.com). Please check the name and try aga
 in.
 

 N:\>

---

### Post by SuaSwe on 2009-08-22
Mm, if it says "Limited or no connectivity", it won't be able to ping. The "ping" command is used to check connectivity between your computer and other hosts (like your router, or a website) and if there is no internet connection, this will not work!

What I need you to do now is go back into Network Connections (follow my instructions above so you get to the right place!), right-click on the Wireless Network Connection, find 'Internet Protocol (TCP/IP)' in the list in the middle and double-click it. Make sure that both the 'Obtain IP address automatically' and 'Obtain DNS server address automatically' is selected, as opposed to 'Use the following'.

Once this is done, press OK. You will then be back in the Wireless Network Connection Properties window. Close out of that too, then right-click on the wireless and click 'Disable', then right-click again and click 'Enable'.

Try connecting to the wireless again. If it says 'Connected', try to get webpages. If it doesn't work, run 'ipconfig /all' (not the space! You typed it in wrong last time, which is why the command didn't run) and the 'ping' commands again.

If it still says 'Limited or no connectivity', there are other things we'll have to look at, including possibly logging into the router configuration.

Note that your Norton firewall may be causing this whole issue; it's worth disabling it. Do you know how to do that?

---

### Post by hector24 on 2009-08-22
Thank you again.  I really appreciate your efforts.  

I have double checked the IP and DSN boxes are ticked individually.  I disabled and then enabled again.  I've turned off the firewall.  Still limited or no connectivity and no internet connection.  I will go through the 'run' commands as before.

Here is what came up:
   	 	 	 	 	 	  Microsoft Windows XP [Version 5.1.2600]
 (C) Copyright 1985-2001 Microsoft Corp.
 

 N:\>ipconfig/all
 

 Windows IP Configuration
 

         Host Name . . . . . . . . . . . . : cg-laptop-cc3
         Primary Dns Suffix  . . . . . . . : SALESIAN.internal
         Node Type . . . . . . . . . . . . : Unknown
         IP Routing Enabled. . . . . . . . : Yes
         WINS Proxy Enabled. . . . . . . . : No
 

 Ethernet adapter Local Area Connection:
 

         Media State . . . . . . . . . . . : Media disconnected
         Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Cont
 roller
         Physical Address. . . . . . . . . : 00-15-C5-B9-8E-3C
 

 Ethernet adapter Wireless Network Connection:
 

         Connection-specific DNS Suffix  . :
         Description . . . . . . . . . . . : Intel(R) PRO/Wireless 3945ABG Networ
 k Connection
         Physical Address. . . . . . . . . : 00-18-DE-80-FF-49
         Dhcp Enabled. . . . . . . . . . . : Yes
         Autoconfiguration Enabled . . . . : Yes
         Autoconfiguration IP Address. . . : 169.254.76.93
         Subnet Mask . . . . . . . . . . . : 255.255.0.0
         Default Gateway . . . . . . . . . :
 

 N:\>ping 192.168.1.254
 

 Pinging 192.168.1.254 with 32 bytes of data:
 

 Destination host unreachable.
 Destination host unreachable.
 Destination host unreachable.
 Destination host unreachable.
 

 Ping statistics for 192.168.1.254:
     Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),
 

 N:\>ping 213.177.33.151
 

 Pinging 213.177.33.151 with 32 bytes of data:
 

 Destination host unreachable.
 Destination host unreachable.
 Destination host unreachable.
 Destination host unreachable.
 

 Ping statistics for 213.177.33.151:
     Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),
 

 N:\>ping [www.lego.com](www.lego.com)
 Ping request could not find host [www.lego.com](www.lego.com). Please check the name and try aga
 in.
 

 N:\>

---

### Post by SuaSwe on 2009-08-22
At this point I think the best option will be to reset your network settings. Note that all firewalls on the computer MUST be switched off for this as you may otherwise risk your PC's health. It's rare that these commands cause system problems but it's always possible, so if you're unwilling to attempt them, please let me know and I'll try and think of an alternative.

Go to Start -> Run -> type in 'cmd' (no quotes)

In the Command Prompt window, type these in and press Enter after each one:

```

ipconfig /flushdns

```

```

netsh int ip reset reset.log

```

```

netsh winsock reset catalog

```

Make sure that you type them in precisely as you see them in there.

If you prefer, you can also try a system restore from a time when the wireless was connected (even if it wasn't working at the time). You do this by going to Start -> All Programs -> Accessories -> System Tools -> System Restore, and follow the instructions.

---

### Post by hector24 on 2009-08-22
Still saying limited or no connectivity, I'm afraid.  I've tried disabling and enabling again to no avail.

---

### Post by SuaSwe on 2009-08-23
Did the commands run through? The flushdns and winsock ones should actually state that they completed successfully and prompt you to reboot.

Did you try system restore as well?

---

### Post by hector24 on 2009-08-23
I think I was prompted to do a reboot.  I tried system restore but it's blocked; I have to take the laptop in to work to have the administrator do this.

I won't be going into work for another week.  Thank you for all your help.

---

### Post by SuaSwe on 2009-08-24
You can also try disconnecting from the wireless and just reconnecting, or lowering the encryption level (e.g. if you're using WPA go to WEP, or if you're already on WEP disable it completely) and see if it'll connect.

---

### Post by hector24 on 2009-08-25
> **SuaSwe said:**
> You can also try disconnecting from the wireless and just reconnecting, or lowering the encryption level (e.g. if you're using WPA go to WEP, or if you're already on WEP disable it completely) and see if it'll connect.

I've done both the above and still cannot connect to server.

Thank you for all your help.  I'm aware I've taken up a lot of your time.  I think I'll take my laptop in to work next week and try to get the IT people to take me seriously when I say I can't connect to my wireless router - put the ball in their court.  I'll let you know what happens.

Many thanks.

---

### Post by hector24 on 2009-09-06
Thank you again to everyone for their help.  I'm finally sorted.  Probably an easy solution but not to me.  All the following applies to my laptop: I re-set my router and then reconnected to wireless network.  I then found my IP address and entered this on a Google search.  I then reconfigured my router using the Thompson Speedtouch wizard and then - voila!  The reason I had so much trouble is that I wasn't able to do the search on my desktop (which has Ububtu).  Don't know why but as long as I can go online with both laptop and desktop I'm not worried.
 
Thanks again.

---

