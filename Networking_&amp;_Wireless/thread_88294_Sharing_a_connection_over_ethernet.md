---
title: "Sharing a connection over ethernet"
date: 2005-11-09
forum: Networking &amp; Wireless
---

### Post by nicholaspaul on 2005-11-09
The folks at IRC are great. I love em. But they are ready to ban me for ever if I ever use the words 'crossover' and 'cable' in the same sentence anytime soon. So I'm hoping someone else can help, cos I"m losing my mind!

x86 is a desktop Breezy machine that gets the internet via wifi. PPC is a laptop running Breezy that has no connection (how sad). So I want to ply a crossover cable into x86's ethernet card to give the internet to PPCs ethernet port. 

INTERNET > wifi router > x86 > ppc. 

I've installed Firestarter and got nowhere. I've tried using static ip's, different subnets... my head is spinning. Could someone please tell me (reasonably plainly , cos DHCP and DNS still confuse me) how to do this? Is firestarter the way to go? Do I need a DNS server too? 

Thanks!!

[ps I'm often on IRC so please catch me there if you can! - #ubuntu ]

---

### Post by UbuntUser4389 on 2005-11-10
I am going to ask maybe a dumb question but here it goes! Does your desktop have a wireless network adapter installed?? If so, can you get the same thing or a different wireless card adapter for your laptop that would work with Ubuntu?

If not, could you possibly get a regular ethernet/broadband router and connect the wireless one to it? then you would have:
                            
INTERNET>router>wifi router>x86
[COLOR="White"]INTERNET>router[/COLOR]>ppc

Would that work for you? If you are trying not to spend any more money I am not sure what to tell you. I haven't done much with Linux, I am a newbie! If I didn't answer your question, I hope you find someone who can! Good Luck!!

---

### Post by az on 2005-11-10
[QUOTE=nicholaspaul]
INTERNET > wifi router > x86 > ppc. 
[/QUOTE]


Your wifi router has two addresses, an external and an internal one.  Your x86 pc will have to do the same.  It will be sharing a connection between networks, so the address it has on it's external connection (wireless) will have to be on a different network than the internal one (crossover cable).  It (the x86 bo) will router from one network to the other.

You can use Firestarter for NAT (Network Address Translation - routing, masquerading, internet connection sharing - they all mean the same thing)  If you are not using static connections, you also need to route dns.  So dns masq is great since it is both for DNS masquerade as well as being a dhcp server.

So the address thing can look like this:

INTERNET
69.68.67.66
wifi router
192.168.0.1
|
192.168.0.100
x86 
192.168.1.1
|
192.168.1.2
ppc

so wifi router has an address on the internet that is 69.68.67.66 and an internal address (on your lan in your house) of 192.168.0.1

Your x86 box has an address of 192.168.0.100 on you lan and will have 192.168.1.1 as the address of another network (the one between your x86 and ppc boxes)

Your ppc will use the 192.168.1.2 address for it's connection with the crossover cable.

Does this help?

aboutdebian.com - There is a nice tutorial on networking and how network addresses are used.

NOTE:  Because the first three numbers determine the network and the last number determines the individual on the network, 192.168.0.1 and 192.168.1.1 are two different machine on two different networks. (192.168.0.x)

192.168.0.100 and 192.168.0.101 are two different machines on the same network.

---

### Post by nicholaspaul on 2005-11-10
[QUOTE=UbuntUser4389]I am going to ask maybe a dumb question but here it goes! Does your desktop have a wireless network adapter installed?? If so, can you get the same thing or a different wireless card adapter for your laptop that would work with Ubuntu?[/QUOTE]
OH yes., I've looked into wireless adapters. They're a bit problematic with PPC so I'm going with plan B.

> 
If not, could you possibly get a regular ethernet/broadband router and connect the wireless one to it? 
That's not a bad idea. If all else fails, perhaps I will. 

Thanks for the suggestions.

---

### Post by matthew on 2005-11-11
First off, for anyone looking at this and wanting to do something similar I wrote a long howto that covers much of this info in detail. Here's the link:
[http://ubuntuforums.org/showthread.php?t=76346]("http://ubuntuforums.org/showthread.php?t=76346")

*** <tone=gentle and friendly>*** I'm going to attempt to post here the same information from that howto, modified to make it work in this context. I will try (but can't promise) not to miss anything. I know the howto works well, so please read it thoroughly and make sure you understand it--ask me if you have any specific question as to what I am talking about there...try to avoid the "I can't get it to work, what do I do?" sort of comments...be as specific as you can and help will be quicker to find. Okay, end of teacher mode.

Please confirm that I understand the problem correctly.

In this thread you are trying to go  INTERNET > wifi router > x86 > ppc.
Both the x86 and ppc computers are running Ubuntu 5.10 (Breezy). 
The x86 already has a working internet connection.
You are using a crossover cable to go from the ppc to the ethernet port on the desktop which is connected to the internet via a wireless (wi-fi) connection.

Everything right so far?? If so, here is what you need to do:

**Get the following info from your wireless router**
For me this is through a browser interface at 192.168.1.1 when connected directly to the router via an ethernet cable or wireless connection.
  
Find the following information from your router's configuration. I will list mine (where security permits) for comparison and so you can see it below as we continue. On the linksys wrt54g with firmware version 4.20.7 this is found under Status->Router in the configuration pages.
  
Here is mine as a sample:
     IP address: 192.168.15.100
     Default gateway: 192.168.15.1
   Subnet mask: 255.255.255.0
  Domain name: your.netprovider.net
     DNS: xxx.xxx.xxx.xxx (there will likely be 2 or 3 assigned to you by your internet provider and DHCP)
  
  *the router assigns addresses to computers using it from 192.168.1.100 to 192.168.1.149

**Plug the crossover cable in from the ppc to the ethernet port of the x86**

[B]Install and configure Firestarter on both the x86 and the ppc
[/B]a. If you have an existing firewall installed on either computer, disable and uninstall it. We will use Firestarter as it is easy to configure. However, if you already know how to configure your firewall and want to continue using it, feel free to do so. (and I will assume you won't need to ask me anything about it)
  
  b. Install Firestarter on both computers, either using synaptic or apt-get install firestarter.
  
  c. Configure Firestarter on the x86:
  
Preferences->Network Settings
  -select the wireless card as your "Internet Connected Network Device"
  -select the ethernet card as your "Local Network Connected Device"
  -select "Enable internet connection sharing"

d. Configure Firestarter on the ppc:
   
 Preferences->Network Settings
   -select the ethernet card as your "Internet Connected Network Device"

**Configure your network rules on the x86**
  
  From the panel menu: System->Administration->Networking
  
Your wireless connection should already be configured properly and working so I won't discuss that here. Your settings for that card/connection will not change at all.
  
  Highlight your Ethernet Connection and select "Properties"
  
  Check "This device is configured"
  
  Configuration: Static IP address
  IP Address: 192.168.2.102 *see note just below
  Subnet mask: 255.255.255.0
  Gateway address: 192.168.15.100 +see note just below
  
  Choose your wireless connection as the "Default gateway device"
  
  Click "ok" because you are done here.
  
*the important thing here is to choose a different subnet from what your router assigns to computers connected to it. Mine assigns addresses in the 192.168.1.xxx subnet so I chose to use here 192.168.2.xxx
  
  +This is from the Default Gateway listed in the router's setup page as shown above.
  
  **Configure your network rules on the ppc**
  
  From the panel menu: System->Administration->Networking
   
  Highlight your Ethernet Connection and select "Properties"
   
   Check "This device is configured"
   
   Configuration: Static IP address
   IP Address: 192.168.2.103 *see note just below
   Subnet mask: 255.255.255.0
   Gateway address: 192.168.2.102 +see note just below
   
   Choose your wireless connection as the "Default gateway device"
   
   Click "ok" because you are done here.
   
*the important thing here is to choose the same subnet as your laptop is using. Earlier we used 192.168.2.102 subnet so I chose to use here 192.168.2.103. Same subnet, different computer.
   
   +This ***has*** to be the same as the IP address for your laptop's ethernet connection (eth0).
  
  **Configure the Domain Name and servers properly**
This step insures that your ppc will have access to the internet the same way the x86 does and be able to use names for web sites and not just IP addresses...in other words, we are going to tell your desktop the some of the same information manually that your router is telling your laptop through DHCP.
  
  On your x86, open the file /etc/resolv.conf (*use Nautilus to browse there and click on it*)

  In it you will find something like this:
       Code:
       [LEFT]search your.netprovider.net
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx[/LEFT]
        
   Keep this information handy.
  
  Go to the ppc and put the exact information in the file /etc/resolv.conf on the ppc using your favorite editor.

[LEFT]```
sudo gedit /etc/resolv.conf
```[/LEFT]
        
It is probable that this file is currently blank. Iif it is not, completely erase the contents if there are any and type in exactly what is shown in the same file on your x86 and then save it.
  
**Test**
Open firefox and type something simple in the address bar like "www.google.com"
  
  If we did everything right it will work, but we are not quite done.
  
The resolv.conf file will be regenerated on the desktop every time you reboot. Unless you enjoy recreating the file each time, there is one more step remaining.
  
  While the current internet connection is working, with all the [extra repositories enabled]("https://wiki.ubuntu.com/AddingRepositoriesHowto"), fire up synaptic or apt-get install **resolvconf**
  
  Once that is installed

       [LEFT]```
cp /etc/network/interfaces /etc/network/interfaces_backup

gedit /etc/network/interfaces
```[/LEFT]
        
   and add the following to that file under the heading shown using the information from your current, working /etc/resolv.conf:
```
iface eth0 inet static
[LEFT]dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
dns-search your.netprovider.net[/LEFT]
   
```     
   This will automatically create your (correct) /etc/resolv.conf file every time you reboot.

Okay, try all that step by step. Go slowly and make notes as needed. If you have further problems please ask! (Try to be really specific, though. That makes helping a lot easier.)

---

### Post by nicholaspaul on 2005-11-12
Thanks for the really lengthy reply! I'll go through this reeaally carefully and let you know how it goes.

---

