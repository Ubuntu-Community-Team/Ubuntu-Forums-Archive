---
title: "USB driver for Huawei SmartAX MT882?"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by applegrew on 2007-09-24
I have the Huawei SmartAX MT882 adsl router. It is already connected to my laptop (running Kubuntu) using the ethernet. The only spare port left is a USB port, which I want to use to connect to my desktop. For Windows and Mac it comes with driver to make it work over the USB. How do I make it run over the USB on Kubuntu?

I did find some links on this forum which looks helpful but are in some language I don't know. These links are [http://ubuntuforums.org/showthread.php?t=426944](http://ubuntuforums.org/showthread.php?t=426944) and [http://www.ubuntu-es.org/index.php?q=node/19203](http://www.ubuntu-es.org/index.php?q=node/19203) . Pls help. :KS:)

---

### Post by applegrew on 2007-09-24
people pls  help. Atleast can anyone translate the instructions at the above mentioned links? I need to get my router working via USB so that I can convert my Desktop also into Linux from Windows. :(

---

### Post by applegrew on 2007-09-25
An update. I tried to just connect my router and my (kubuntu) computer via the USB cable and then my Knetworkmanager notified that the link is up and a new eth1 network was visible, but the network wasn't still accessible. I checked the CD supplied with my router and I found a patch for Linux kernel 2.4 to make it work with my router. (**I have attached that file in this post**). It said something about CDCEther module (please the attached file). I checked my lsmod output and found three modules named like cdcether, usbnet, etc.

Pls help me to make my router work with ubuntu. Thanks for all the help, in advance.

---

### Post by applegrew on 2007-09-25
somebody pls reply.

---

### Post by goodlife76 on 2007-11-27
Hi Appelgrew ,

I too am facing the same problem and actually the zipped files that you have attached will not work for ubuntu 7.10 as here the kernel is ver 2.6.x and the CDCEther files are according to kernel ver 2.4.x and henece even if you try to make them (i.e compile the driver in terminal window) it will fail with a host of errors.

Now at the site :
[http://www.linuxdriverproject.org/twiki/bin/view/Main/DriversNeeded](http://www.linuxdriverproject.org/twiki/bin/view/Main/DriversNeeded) 
I see a mention that there are currently no drivers for our need for kernel ver 2.6 and hence I am still searching away across sites to find out if anybody in the world is already constructing them. So sorry even after so many words above I too don't have the solution but atleast I have idenitifed the block points and spreading the word around so that people searching also try to search for the compatible drivers of SmartAX MT882 with kernel ver 2.6.x.

Regards
goodlife76

---

### Post by applegrew on 2007-12-02
Hi Goodlife76,

After trying to get it work so many times, I have now decided to buy a switch or router. I will keep my opens if I come across any such drivers. I will report it here when I find one.

---

### Post by itisbasi on 2007-12-21
i've got the exact same problem...haven't found the drivers yet....how about you guys applegrew and goodlife76???have you got it working...i used google translate to translate the 2 links that you've mentioned in the post...but i couldn't make much sense of it...probably cos i am a noob to linux....

---

### Post by applegrew on 2007-12-22
@itisbasi

Today I have bought an ADSL Wifi Router from Netgear. So, I no longer need the drivers. As far as support is concerned Huawei sucks. Let's hope Netgear is not like, but maybe I won't also not need one now.

BTW I have bought [Netgear DG834G]("http://www.netgear.com/Products/RoutersandGateways/GWirelessRouters/DG834G.aspx"). Furthermore, its firmware is opensource. Its code can be downloaded from [here]("http://kbserver.netgear.com/kb_web_files/open_src.asp").

---

### Post by itisbasi on 2008-01-09
yeah you're right applegrew....huawei support sucks....they only responded to my initial mail asking for my modem specifications and haven't respondede after that despite multiple reminders....i've given up on it finally...

---

### Post by prashantryp on 2008-03-22
I am new to ubuntu/linux but see @ device manager if u r using ubuntu 7.10 gusty it displays mt882 modem so i think modem is installed.

but I like to make a WAN miniport pppoe connection LIKE IN WINDOWS so i can put user id and password to connect to my internet. I dont want autodial by modme's pppoe.

Is it due to IPV6 because in windows it's woking with IPV4

even i am unable to ping my modem by entering fixed ip setting in netwrok configuration.

or some thinig else.

---

### Post by prithvitech on 2008-05-17
I have to connect my MT882 modem to USB only, since I need at least 2 additional NICs to connect to local network and an additional modem, and my laptop does not have the luxury of 3 NICS.

Status - 
* I'm using hardy heron 8.0.4 server.

* /var/log/messages tells me that eth1 has been registered as cdc ethernet. I configured eth1 in /etc/network/interfaces as 192.168.1.8. Can ping 192.168.1.8, but cannot ping modem at 192.168.1.1

* Same configuration with same modem allows me to ping the modem (through USB) on XP. Therefore, the modem is working fine. 

* Same configuration on a different laptop running FC6 gives the exact same problem - eth1 registered, network interface configured, but cannot ping modem; implying that it's something to do with the linux driver inbuilt into the kernel. 

Any assistance on what to do next would be greatly appreciated.

Prashant

---

### Post by JoyceBabu on 2008-05-18
Me too facing the same problem. If anyone has any solution, plz post it here.

It was working fine with my MacBook when I was using OSX Tiger, but when I upgraded to Leopard, it stopped working there too. :(

---

### Post by bgturk on 2008-07-19
My LAN card is not working, and I am desperately trying to connect to the internet through my USB port. 
Ubuntu recognizes the SmartAX MT882 router just fine (and this is how I am connected to the internet now), but Leopard fails. I need to use Leopard.
Does anybody know if this router has drivers for Leopard, and where I can download them?

Thanks!

---

