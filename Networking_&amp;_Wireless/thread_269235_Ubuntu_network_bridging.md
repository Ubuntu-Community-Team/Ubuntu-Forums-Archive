---
title: "Ubuntu network bridging"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by Ryan450 on 2006-10-01
Hey guys,

In windows I used a network bridge to get my xbox onto the internet. My computer's internet access comes through my wireless card, but I bridged the wireless card to my ethernet nic to allow the xbox to grab DHCP info from my router. How can I get this set up in Ubuntu?

Wireless router -> Computer -> Xbox

With the location of my cable modem, moving the xbox to connect it directly into the router isnt an option, it really would be nice to get this running under ubuntu.

---

### Post by mips on 2006-10-01
You don't need bridging. Install firestarter, configure ICS and configure DHCP server if required (can't remember as i havent used firestarter in a long time).

---

### Post by Ryan450 on 2006-10-01
Alright, I've downloaded and installed Firestarter, enabled ICS sharing. First it was giving me some problems with eth0 not being up and running, I assigned that a static IP address which is 192.168.1.150

Then I booted up my xbox and connected it into eth0 via cross-over cable, assigned a static ip address to the xbox using the following info. 

IP: 192.168.1.3
SUBNET MASK: 255.255.255.0
Gateway: 192.168.1.1 (my router's IP).

This aint working, and I'm not too advanced in my networking configurations yet. Any idea why this isnt working? If I can I'll gladly skip over installing the DHCP server on my machine, since static IP's should be sufficient.

---

### Post by mips on 2006-10-01
You can NOT have your wireless and wired connections in the same network.

From interpretation I assume your fireless uses network 192.168.1.0, as your routers address falls within that network.

Configure Eth0 with the following parameters:
Ip Address 192.168.2.1
Netmask 255.255.255.0
Broadcast 192.168.2.255
Gateway 192.168.**1**.1

Configure your Xbox with the following parameters:
Ip Address 192.168.2.10
Netmask 255.255.255.0
Broadcast 192.168.2.255
Gateway 192.168.**2**.1

If you need to configure DNS addresses anywhere point it to your routers address for now.


> **Ryan450 said:**
> Alright, I've downloaded and installed Firestarter, enabled ICS sharing. First it was giving me some problems with eth0 not being up and running, I assigned that a static IP address which is 192.168.1.150

Then I booted up my xbox and connected it into eth0 via cross-over cable, assigned a static ip address to the xbox using the following info. 

IP: 192.168.1.3
SUBNET MASK: 255.255.255.0
Gateway: 192.168.1.1 (my router's IP).

This aint working, and I'm not too advanced in my networking configurations yet. Any idea why this isnt working? If I can I'll gladly skip over installing the DHCP server on my machine, since static IP's should be sufficient.

---

### Post by Ryan450 on 2006-10-01
that did it :). Thank you very much.

---

### Post by dhl84 on 2007-06-21
Sorry to bring up this old post but I thought it'd be better than to start a new one.
I'm trying to get my 360 to route traffic through my Ubuntu Feisty Fawn. Similar situation as the OP... I managed to get the PC and 360 to see each other, but when I do a Live connection test it gets to the MTU testing stage then fails. 
It seems that the default MTU for the ethernet adaptor is 1500 which is supposed to be within the limit, and I know it can't be due to the adaptor's limitations because it works fine through the same hardware in XP.
Does anyone have any ideas?
TIA

---

### Post by mips on 2007-06-22
Xbox Live requires a minimum MTU setting of 1365 or higher.

Check your router configs and also ensure you configure both interfaces on your linux box to 1500.
To do it in linux see,  [http://ubuntuforums.org/showpost.php?p=582018&postcount=5](http://ubuntuforums.org/showpost.php?p=582018&postcount=5)

If your router is set to AUTO then statically configure it for 1500.

Google** XBOX 360 MTU settings**  and you will find many people with this issue.

---

### Post by dhl84 on 2007-06-22
Hi there,
Thanks for the quick response. I did have a look at googling the MTU problem, but didn't come up with much apart from changing the adaptor (eth0) MTU. Now that I think about it, I didn't try changing the MTU on the wlan0 adaptor, nor the router. Regarding the router, I figured that, as it bridges the connection fine in Windows, it would be fine, but I will check that.
Thanks again.

---

### Post by Frazer on 2008-01-10
Thanks, this thread helped me fix my issues :)

Im now using firestarter to get it working on a static ip

---

