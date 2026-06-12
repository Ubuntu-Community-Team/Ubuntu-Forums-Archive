---
title: "Atheros AR5006EG 802.11 b/g Wireless Problems on gutsy64 bit"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by mguthriejr on 2008-02-25
Well i Have installed Ubuntu on my laptop and I cant get it to work under 64 bit ubuntu 
im running an amd turion 64 X2 with a AR5006EG 802.11 b/g Wireless PCI Express Adapter Ive seen lots of posts about how to do it in 32 bit ubuntu but does anybody know if those methods will work in 64 bit or not?

Thx

---

### Post by littletinman on 2008-02-25
Same here. I'm still getting help and looking around. What laptop do you have?

---

### Post by amay1283 on 2008-02-25
HI folks! I am new to linux (Ubuntu 7.10). Facing same problem with Atheros card. I am using Acer laptop...amd Turion64...Any help or suggestions would be welcome.......Thnx:)

---

### Post by mguthriejr on 2008-02-25
im using a compaq presario with an amd turion 64 x2

---

### Post by nutz on 2008-03-01
I have been working really hard on this but mine still isn't working either. I would be extremely thankful for any help I can get with this. Same wireless NIC...

Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01) on Ubuntu 7.10 AMD64.

---

### Post by swampdweller on 2008-03-04
Same here.
Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
in an Acer Aspire 5520-5771 laptop (AMD TK-55).  The only consolation I can offer is the
fact that if you settle for 32-bit Ubuntu, ndiswrapper and the 32-bit driver work great.
I gave up on the 64-bit when I got this laptop in October.  I switched to the 32-bit and my
wifi has been humming along smooth as silk.
Of course I will be immensely grateful to anyone who succeeds with AR5006EG in
64-bit Ubuntu, but, for what it's worth, let me warn those intrepid pioneers that
ndiswrapper with the 64-bit driver will very nearly *appear* to work.
You will see access points, you may even be able to intermittently connect, weakly,
to a select subset of them.  You might then be tempted to post "It Works!", only to realize
in the ensuing hours that it doesn't really.
Still, like all of us here, I dare say, I would rather be running 64.
Meanwhile however, I **am** running, and in practice, I think I would be hard pressed to
discern any performance difference (between 32-bit and 64-bit Ubuntu).  Of course one
wishes for 64 bits, but it is, at this stage, a matter far more of principle than practice.

---

### Post by johnhunsley on 2008-03-10
Hi,

I'm runnning Kubuntu 7.10 on HP9000 2xAMD64 Turion with Atheros AR5006EG wifi card. and I have successfully got my wifi running. It took a while and lot of fidlding about but here's what I did:

I followed the instructions from this guys blog - 

[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)

I could see the card was working but just could not get an ip address from my DHCP enabled wifi router so I decided to try again. Follow the commands:

1. see what interface we have

** lspci **

this shows the type of wifi card my machine has. You need the driver for the Atheros AR5006EG, I tried to find an AMD64 bit compatable driver from this site but when you click the download link for the 64bit net5416 driver it just gives you the older net5211. I tried all of these but the one which finally worked was the 32bit net5211 driver.

2. Now blacklist the useless driver that came with the machine

 **blacklist ath_pci**

3. make sure no drivers are installed

 **sudo ndiswrapper -l **

4. un install any thing that comes up

 **sudo ndiswrapper -r [B]*driver_name***[/B]

5. now install the 32bit net5211.inf file we downloaded

 **sudo ndiswrapper -i [B]*/path/to/driver/net5211.inf***[/B]

6. write the configuration to modprobe

**sudo ndiswrapper -m**

7. run modprobe

**sudo modprobe ndiswrapper**

8. restart networking

**sudo /etc/init.d/networking restart**

9. check the interface is up and running 

**iwconfig**

You should see wlan0 with all the connection details for your router. You might not immeditaley get an ip address if so do this:

10. reboot the machiine

11. System Settings - networking 
Check you can see eth1 and wlan0 in the interface list and both are enabled. Try configuring the wlan0 interface, hit Administrator Mode, right click the interface and configure. Make sure your security settings and channel match your router. 

12. remove the ndiswrapper from modprobe

**sudo rmmod ndiswrapper**

13. write to modprobe again

**sudo modprobe ndiswrapper**

14. restart networking

**sudo /etc/init.d/networking restart**

15. check the interface is up and running 

**iwconfig**

If you still dont see the wlan0 settings all present and correct then reboot again, go to System Settings - networking,  and see if your wlan0 interface has a valid ip from your DHCP router, if so your in business, if not repeat the  10 -15 again, I have read some people say that it takes two or three goes after boot to write to modprobe sucessfully.

One other thing, make sure your wifi card is turned on!!! Sounds crazy but make sure the Wireless switch on the front left of the machine is switched over to the right. I have two lights on my Wireless button, a blue 'mast' type icon light and a round red icon light. I'm guessing that HP got it the wrong way round because when the switch is to the right, next to the round red icon, it is on!  :)

I am also using KWifiManager to scan for networks, Even when I couldn't connect it would still be able to scan and show up any available networks which is good because you can ensure your wifi router is working ok if your having problems.

Hope that helps.

John.

---

### Post by swampdweller on 2008-03-10
Mr. Hunsley, I'm confused, are you running Gutsy64 or Gutsy32?

---

### Post by nutz on 2008-03-10
> **swampdweller said:**
> Mr. Hunsley, I'm confused, are you running Gutsy64 or Gutsy32?

+1 and is it the 5006 or 5007?

---

### Post by johnhunsley on 2008-03-11
I'm running Kubuntu 7.10 (Gutsy) 64. I have 2xAMD64 Turion and I have installed the 32bit net5211 Atheros driver with ndiswrapper.

Everytime I boot up I have to issue the following commands:

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart

Following the networking restart the interface kicks into life and gets a valid ip address from DHCP and all is well.

Whats 5006 or 5007?

John

---

### Post by Flag on 2008-03-11
John is right,

I had the same problems, Acer Aspire 7520, Atheros card. Download the 64 bit driver, though it still shows as Ath 5211, same as 32 bit.
Wifi starts without problem at some locations, at others I have to the same as John does.

Fred

---

### Post by swampdweller on 2008-03-11
A grain of salt for those who care to take it...

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,faq/#can_i_use_32-bit_windows_driver_in_64-bit_mode]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,faq/#can_i_use_32-bit_windows_driver_in_64-bit_mode")

---

### Post by joshnuss on 2008-03-29
Thank You John! you rock buddy

---

