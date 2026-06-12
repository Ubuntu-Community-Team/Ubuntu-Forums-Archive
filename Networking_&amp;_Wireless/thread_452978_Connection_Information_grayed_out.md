---
title: "Connection Information grayed out"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by Novakane on 2007-05-23
Running Feisty here. I changed my network configuration from DHCP to fixed IP temporarily. I subsequently changed back to DHCP, but now the Connection Information menu item on the Network Configuration (on the top panel) is grayed out. How do you re-enable it? Or is there a terminal command that lets me see my DNS info? I don't see DNS info using ifconfig.

Thanks.

---

### Post by cantormath on 2007-05-23
> **Novakane said:**
> Running Feisty here. I changed my network configuration from DHCP to fixed IP temporarily. I subsequently changed back to DHCP, but now the Connection Information menu item on the Network Configuration (on the top panel) is grayed out. How do you re-enable it? Or is there a terminal command that lets me see my DNS info? I don't see DNS info using ifconfig.

Thanks.

to see the NIC connections........
```
:~$ sudo ifconfig
```or ```
 :~$ sudo ifconfig eth0
```or any card you want to get info on. if it is wireless, you can also see the wireless info ```
 :~$ sudo iwconfig 
``` You can also see what your hardware is, including your NIC, with ```
 :~$ lspci  
``` You can see boot messages about your card (assuming the card is eth0) with ```
 :~$dmesg eth0 
```.  You can list hardware information about your network with ```
:$ sudo lshw -C network
``` You can reauthenicate (DHCP) the card with the router ```
 :~$ sudo dhclient
```or  ```
 :~$ sudo dhclient eth0
```If you would like to reset the network connection ```
 :~$ sudo /etc/init.d/networking restart
```.  You can also replace restart with stop and start. A question: are you using wireless and if so are you using wep ? to set wireless with wep ```
sudo iwconfig ath0 essid SSID key THEKEY
```or if it is an ascii key (open) ```
sudo iwconfig ath0 essid virusdownloader.dll key -s:thekey
```the you got to sudo dhclient the card again.  Hope that helps alittle.

---

### Post by Novakane on 2007-05-23
Thanks for the quick response, cantormath. None of those commands shows me the DNS numbers I'm looking for, though. Before, I could click the Manual Network Configuration ( icon with two little black monitors on the top panel), select Connection Information from the drop-down menu, and see IP and DNS info. Now that menu item is grayed out since I changed from DHCP to static and back again. If I knew what app that menu item started, I could just run it, maybe put a link on my desktop.

The reason I like to look: for some reason today, it listed my DNS as 192.168.1.1, which ain't the DNS numbers I need. And I couldn't ping any domain names. I rebooted, and got the right DNS numbers, and then things worked okay.

I know I can ping a domain name to see if I picked up the right DNS numbers, but I'd like to just look from the menu like before. BTW, I had the same thing happen on another Feisty machine I have here. Menu item is grayed out after a temporary switch to a static IP.

No, I'm not using wireless. I'm only a foot from the router, so I just plug in with CAT5.

---

### Post by cantormath on 2007-05-24
> **Novakane said:**
> Thanks for the quick response, cantormath. None of those commands shows me the DNS numbers I'm looking for, though. Before, I could click the Manual Network Configuration ( icon with two little black monitors on the top panel), select Connection Information from the drop-down menu, and see IP and DNS info. Now that menu item is grayed out since I changed from DHCP to static and back again. If I knew what app that menu item started, I could just run it, maybe put a link on my desktop.

The reason I like to look: for some reason today, it listed my DNS as 192.168.1.1, which ain't the DNS numbers I need. And I couldn't ping any domain names. I rebooted, and got the right DNS numbers, and then things worked okay.

I know I can ping a domain name to see if I picked up the right DNS numbers, but I'd like to just look from the menu like before. BTW, I had the same thing happen on another Feisty machine I have here. Menu item is grayed out after a temporary switch to a static IP.

No, I'm not using wireless. I'm only a foot from the router, so I just plug in with CAT5.

I have no idea why you are getting the grey area etc......I use dapper...

as far as setting up the static ip goes.......assuming I am getting what you are asking.....to setup a static ip, did you configure configure that /etc/network/interface?
here is an example of what I mean for a static IP:

>  # An example static IP setup: (broadcast and gateway are optional)
     #
     auto eth0
     iface eth0 inet static
          address 192.168.0.42
          network 192.168.0.0
          netmask 255.255.255.0
          broadcast 192.168.0.255
          gateway 192.168.0.1
Debian checks that file on reboots or shutdown. Therefore on the next boot, it'll know to either launch dhcp or to NOT launch it.

As far as the DNS thing you are talking about, do you mean this?
> $ nslookup fuckmicrosoft.biz
Server:         192.168.1.1
Address:        192.168.1.1#53
Non-authoritative answer:
Name:   fuckmicrosoft.biz
Address: 68.105.146.57


Again, let me know if I am totally missing what you are saying about that.

---

### Post by Novakane on 2007-05-24
Thanks again. I succeeded in setting the static IP, but I decided to change back to DHCP. That part is working fine. The Connection Information thing on the menu showed my IP, broadcast, gateway, mask, AND my DNS (Domain Name Server) numbers. If the browser doesn't have valid DNS numbers from my ISP (and it didn't last night), it doesn't know where to look to resolve addresses like google.com, and it won't pull up any pages...unless you enter the full IP number in the address bar.

So all I was looking for was a quick way to see if I got valid DNS numbers after booting up. Last night it was showing 192.168.1.1 for a Domain Name Server, and that's just the router's gateway address. My particular DNS numbers should be 65.174.114.2 and 3.

Anyway, thanks for your help. Maybe someone else here has had the same problem with 7.04 and will chime in.

---

