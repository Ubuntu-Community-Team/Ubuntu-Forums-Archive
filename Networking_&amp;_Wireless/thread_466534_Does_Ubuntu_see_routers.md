---
title: "Does Ubuntu see routers?"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by NJC on 2007-06-06
Ubuntu 6.06.

Ubuntu properly configured my Ethernet card and I hooked up a Linksys router today (I don't have a high speed connection yet). 

Under Device Manager I only see Network Interface under the Ethernet card. How can I tell if Ubuntu can properly see this router?

---

### Post by odiseo77 on 2007-06-06
Well, as far as I know (and this is the way I access to my router under linux and windows), you can access your router by entering it's IP address in a browser and hitting the enter key (you'll probably be prompted for username and password unless you haven't set up your router yet).

Regards.

---

### Post by NJC on 2007-06-06
Thanks odiseo77 ... I went to the Linksys website and it claims the IP is 192.168.1.1 but no joy. The model is BEFSR41 - maybe the previous router owner changed the IP??

EDIT: Duh, I don't think I'm following the Linksys instructions properly.

---

### Post by meng on 2007-06-06
Ubuntu doesn't really "see" the router as a device, although if you're connected properly it should be able to connect to it as a part of the network - you might consider opening your firewall to allow connections from 192.168.1.1, although that may not be causing your problem.

---

### Post by odiseo77 on 2007-06-06
Have you read the manual that came with your router? It should specify which IP address to enter... anyway, you can try with 192.168.1.254 to see what happens.

Regards.

---

### Post by esavato on 2007-06-06
when you run the command 
```
ifconfig
```

do you have an ip address assigned to eth0?  You may want to 'bounce' the interface by turning it off and then back on...

```

ifconfig eth0 down
ifconfig eth0 up
ifconfig

```

if the interface does not have an ip address at this point, you can manually assign one in the subnet of the router to gain access...

```

ifconfig eth0 address 192.168.1.101
```

Here is the man page for ifconfig
[http://www.die.net/doc/linux/man/man8/ifconfig.8.html](http://www.die.net/doc/linux/man/man8/ifconfig.8.html)

---

### Post by bukwirm on 2007-06-06
Sometimes the IP address to access the router is printed on the bottom of the router.
If you think someone changed the settings, you can often reset the router by pressing a button somewhere on the router - see the documentation for details,

---

### Post by NJC on 2007-06-06
First, apologies if I am leaving out important info - tonight is the first time I've ever configured routers. Note that at this time I don't have a DSL connection to ISP nor do I have a DSL modem - just an ethernet card and router. 

- I did reset the router.
- Linksys claims 192.168.1.1 is the default, after a reset (but still did not connect)
- All of the lights on Port 1 of router are lit up 
- Ethernet card connection is Activated via Networking window

I did not see an address after running ifconfig. Here's the output:
```
eth0      Link encap:Ethernet  HWaddr 00:D0:B7:92:49:32
          inet6 addr: fe80::2d0:b7ff:fe92:4932/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:16500 (16.1 KiB)

```

ifconfig up/down = Permission denied

```
ifconfig eth0 address 192.168.1.101

```
renders Uknown host

At this point I just wanted to see if Ubuntu recognized the router but maybe I need a modem to properly test. :confused:

---

### Post by bukwirm on 2007-06-07
You have to be root (sudo) to use ifconfig.

You really need access to the router's configuration to troubleshoot it - make sure you enter the IP address (192.168.1.1) exactly in your browser's address bar.

You should not need a modem to connect to the router (you are connecting directly to the router via an ethernet cable, right?).

---

### Post by NJC on 2007-06-07
bukwirm;

I entered in exactly 192.168.1.1 and nada - I do have the router connected directly from ethernet card to 2nd port (all 3 lights are lit on 2nd port of router).

---

### Post by kerry_s on 2007-06-07
reboot or restart the network connection, if you connected after you system was powered on then you didn't get a dhcp lease so your not connected.

sudo /etc/init.d/networking restart

command doesn't always work a reboot is better. linksys are a pain to setup properly and i find them slow.

common web access->
192.168.1.1
192.168.2.1
192.168.201

usually passwd is 
admin
admin
or
 admin
(nopasswd)

---

### Post by kevdog on 2007-06-07
Sounds like you are using a wired connection directly into the linksys router.  If you bought this router "used" you may want to flash the router back to its original settings.  There is a tiny reset button on the back of the router that you need to hold in for about 10 seconds or until all the lights on the front of the router turn on at once.  I believe all linksys routers have a LAN address of 192.168.1.1 with username admin and no password (or is it the other way around???).  Anyway try this first.  It seems clear that your ethernet card isnt seeing your router.  Do you have another computer on the LAN that connects through the router to the outside world??

---

### Post by woland on 2007-06-07
If you are totally stuck and can't figure out to what IP address the router is set to, or you don't know the password, you can hardware reset the  router to default settings.

After that you need to see the manufacturer's manual, to set it up.

I had to do it couple of times on mine.

---

### Post by NJC on 2007-06-07
FWIW these are the instructions I've followed - I'll have to battle later as I have to go to work.

[http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=3676&p_created=1151114781&p_sid=vVqovxDi&p_accessibility=0&p_lva=3676&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MzEmcF9wcm9kcz0wJnBfY2F0cz0wJnBfcHY9JnBfY3Y9JnBfc2NmX2xhbmc9MSZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PUJFRlNSNDE*&p_li=&p_topview=1](http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=3676&p_created=1151114781&p_sid=vVqovxDi&p_accessibility=0&p_lva=3676&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MzEmcF9wcm9kcz0wJnBfY2F0cz0wJnBfcHY9JnBfY3Y9JnBfc2NmX2xhbmc9MSZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PUJFRlNSNDE*&p_li=&p_topview=1)

---

### Post by Rui Pais on 2007-06-07
> **NJC said:**
> FWIW these are the instructions I've followed - I'll have to battle later as I have to go to work.

[http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=3676&p_created=1151114781&p_sid=vVqovxDi&p_accessibility=0&p_lva=3676&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MzEmcF9wcm9kcz0wJnBfY2F0cz0wJnBfcHY9JnBfY3Y9JnBfc2NmX2xhbmc9MSZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PUJFRlNSNDE*&p_li=&p_topview=1](http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=3676&p_created=1151114781&p_sid=vVqovxDi&p_accessibility=0&p_lva=3676&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MzEmcF9wcm9kcz0wJnBfY2F0cz0wJnBfcHY9JnBfY3Y9JnBfc2NmX2xhbmc9MSZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PUJFRlNSNDE*&p_li=&p_topview=1)

your ifconfig on post [#8]("http://http://ubuntuforums.org/showpost.php?p=2796517&postcount=8") shows an ipv6 address but not an ipv4. Maybe that prevents net card to communicates to router (some routers seems to have problems with ipv6). 
Maybe trying to blacklist ipv6 module, reboot and try to connect router then...

---

### Post by NJC on 2007-06-08
> **NJC said:**
> First, apologies if I am leaving out important info - tonight is the first time I've ever configured routers.** Note that at this time I don't have a DSL connection to ISP nor do I have a DSL modem - just an ethernet card and router**.

Being Joe Greenhorn at router config, am I trying to do the impossible. IE is it even possible to test a router that's not connected to a modem? 

I am still using a dialup modem but I don't see how a router (only connected to Ethernet card and nothing else) would be seen by entering 192.168.1.1 via dialup modem. I tried Deactivating dialup Connection and turning off dialup modem and retested the router IP but no success. 

Question: Am I wasting my time testing this router without a DSL modem connected?

---

### Post by Mr. C. on 2007-06-08
NJC,

Try to ignore your belief that you need a broadband modem.  It is incorrect.

Your router is an Ethernet device.  It connects to other Ethernet devices, like the network interface card (NIC)  in your system.  These two are sufficient to be able to talk to each other. Additional Ethernet hardware, such as a broadband modem is irrelevant.

Your router is "seen" because you have wired your NIC to the router.  They see each other as a lamp sees electricity when you plug the lamp in.  That's how they work.

Don't  have your dialup modem *active* while you are trying to connect to the router.

As other's have stated, your router's default configuration will be specified in the user's manual.  You need to know a) its IP address, or b) if it has DHCP enabled by default.  In either case, if you do not know its current configuration, perform a factory reset to get the router back into a know state.

If it provides DHCP-assigned IP addresses by default, then you can simply connect your Ethernet card and router, and configure your Ubuntu system to use dynamic addresses.  Disabling and enabling your NIC is sufficient.

If DHCP is not enabled by default, you will need to configure a static IP that is different from, but on the same network as, the router.  Typically this is 192.168.1.1 or similar.  It is important that you have broadcast, subnet mask, and IP address correct.

If you can't get past this, you'll really need to contact Linksys's tech support to walk you through it.  It really is not difficult.

MrC

---

### Post by Dexter Bip on 2007-06-08
Hmm, I'm a newb myself and more than prepared to be shouted down or corrected, but here's my tuppenworth anyway:

Firstly, as long as your computer is connected to the router via ethernet and the router is on, there's no reason you should have to have the router connected to a modem to be able to browse to the config page and such.

Secondly, this might be worth a go to find out the router IP address: Make sure it's connected and that nothing except your computer is connected to it, then find out your computer's IP and subnet mask and, from terminal, run the ping command with the numbers from your computer's IP address and 255 anywhere there's a 0 in the subnet mask. So, assuming your computer has the address 192.168.1.1 and subnet mask 255.255.255.0, run:

```
ping 192.168.1.255
```

(note: the way most router's are configured, the above command should work as it is)

then you should *hopefully* get ping responses from two IP addresses. One will the the IP of your computer, and the other one should be the router. Try going to that one in your internet browser.

To be honest though, if it's a second hand router and the settings have been changed, there could be any amount of obstacles; the dhcp server could be turned off, it might have some manner of filtering, it may very well be password protected. With this in mind it really is better to fully hard reset it to factory defaults and start from scratch. Have a poke about the linksys pages and google if necessary to find how to hard reset your router to factory settings. If you can't find anything, then pushing in the tiny reset button with a paperclip or such while the router is turned on for 15-20 seconds, then unplugging the router with the button still held down, plugging it back in and continuing to hold the button down for another 15-20 seconds should cover most bases.

---

### Post by kerry_s on 2007-06-08
It's a linksys, expect problems. You might have to press the reset button and try to access it as soon as the lights stop flashing, some have a time limit from reset to access after say a min it blocks all access.

---

### Post by NJC on 2007-06-09
Update:

The red Diagnosis light is constantly on - and I understand this is not a good sign. It could be the main problem ... although strange because the chap I received the router from would not have given me a borked unit.

I'll need to see if it can be fixed first.

---

### Post by NJC on 2007-06-15
Gentlemen;

After a more hours of fiddling/configuring/gnashing of teeth to turn off the router red diagnosis light, I decided to remove router cover as a last effort. The seal was broken so it had been off before. 

I reseated a connection, held down the reset button and somehow the magic Router Fairy came by and POOF, the red light went off! 8-) 8-) Good thing too because this router was inches away from being landfilled. 

Once light was off I was able to run the Flash upgrade program under Win. Rebooted to Ubuntu and FINALLY Router web interface is accessible via 192.168.1.1. Oddly, it only works if I configure the Admin/Networking to 192.168.1.50 instead of 192.168.1.1. Next step will be to find a DSL provider. 

Thanks to all for your help!

---

