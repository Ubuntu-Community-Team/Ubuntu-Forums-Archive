---
title: "Wireless no longer working"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by hr_giger on 2011-05-12
Hi, 

My wireless stopped working a few days ago. I have no idea why. 

I can still see all the available networks, but when I try to connect to my normal one it tries for ages then just stops. 

I can still connect with another laptop on ubuntu 10.04 and 11.04, so I'm fairly sure it;'s not the router or anything. 

I had a problem with wireless on this laptop before, because the wireless card was not supported. But I managed to fix that.

(See here if you want: [http://ubuntuforums.org/showthread.php?t=1681845](http://ubuntuforums.org/showthread.php?t=1681845)).

I was using 10.04, so I upgraded to 11.04 to see if it would fix the problem, but it didn't. My wireless card appears to be supported now, though (although I can't find official confirmation of this). 

Here's some stuff:

amanda@amanda-Satellite-Pro-C660D:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:ed:85:14  
          inet addr:192.168.1.92  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8aae:1dff:feed:8514/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43072562 (43.0 MB)  TX bytes:4663372 (4.6 MB)
          Interrupt:43 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23772 (23.7 KB)  TX bytes:23772 (23.7 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:53:43:48  
          inet6 addr: fe80::1e65:9dff:fe53:4348/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18429 (18.4 KB)  TX bytes:19821 (19.8 KB)

amanda@amanda-Satellite-Pro-C660D:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 1c:65:9d:53:43:48
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:d000(size=256) memory:ff600000-ff603fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 88:ae:1d:ed:85:14
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.92 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:c000(size=256) memory:d0104000-d0104fff memory:d0100000-d0103fff

Please let me know what other information you need to help me solve this. 

Thanks.

---

### Post by grahammechanical on 2011-05-12
If you compare what ifconfig says about eth0 with what it says about wlan0 you will see that both are UP but only eth0 is RUNNING. Also the second line of eth0 is

> inet addr:192.168.1.92  Bcast:192.168.1.255  Mask:255.255.255.0

compare that with the second line of wlan0

> inet6 addr: fe80::1e65:9dff:fe53:4348/64 Scope:Link

So, you have an ethernet connection to the router at the address 192.168.1.92. These are the things that you want to see for wlan0. You say

>  when I try to connect to my normal one it tries for ages then just stops.

Make sure that Network Manager has the correct pass phrase or wireless key for the router. It is not your login password.

Click on the  icon, select Edit Connections, select the Wireless tab and your wireless connection and then select Edit and then Wireless security. Tick the box Show password to see what Network Manager is using for a password. Is it the correct one. You can also check to see if the encryption method is the correct one. Wrong settings here will cause the problem that you are experiencing.

Regards.

---

### Post by hr_giger on 2011-05-13
Thanks. I tried that. It's still using the same (correct) password from before it stopped working. It is also the same password on the other ubuntu laptop that is still working. 

Any other ideas?

Mark

---

### Post by QLee on 2011-05-13
[QUOTE=hr_giger]...
Any other ideas?[/QUOTE]

Disconnect from the "wired" connection and then try connecting to wireless again. NetworkManager tries to always keep a connection if it can find one that it recognises and ethernet connection is favoured over wireless. Connections appear to default to "automatic" it seems you want to manually connect from your description.

Another thing to try is to delete the wireless connection (even though it was working in the past) and let NM find a new one.

---

### Post by hr_giger on 2011-05-13
> **QLee said:**
> Disconnect from the "wired" connection and then try connecting to wireless again. NetworkManager tries to always keep a connection if it can find one that it recognises and ethernet connection is favoured over wireless. Connections appear to default to "automatic" it seems you want to manually connect from your description.

Another thing to try is to delete the wireless connection (even though it was working in the past) and let NM find a new one.

Thanks. Tried that. Didn't work.

---

### Post by hr_giger on 2011-05-14
anyone?

---

### Post by ClientAlive on 2011-05-14
If I were having the kind of issue you describe; and there were another unencrypted network in my network list (like a neighbors or something). You aren't supposed to do this unless you get permission from the person; but if you can talk to them and get their permission - click that one and see if it the machine connects successfully to that other network. If it does open a browser and go to a couple places on the internet to be sure, maybe type some arbitrary word into a google search and see if it goes through ok.

This would tell you if its hardware or something else. It would also tell you if it is something within your system or beyond that point. Since you say that other computer's you have do connect successfully that seems to confirm that your internet connection is working. Between those two pieces of information you will have narrowed it down to configuration. If the attempt to connect to a different wireless network fails, its something more centered around the hardware (like the wireless card and the things to do with it).

---

### Post by wildmanne39 on 2011-05-14
> **hr_giger said:**
> anyone?

Hi, you said that your card shows it is supported in natty, but you would still have to go to additional drivers and install the restricted driver, to do that you need to plug your laptop into an ethernet connection so it can download the driver if there is one available in the additional drivers section. Also I had an old laptop and it had a key to turn the wireless card on and off and every time I shut the computer off I had to turn it back on again. I found the way to do that by looking at the manual for my laptop on line. Also many have a switch on them, I am sure you have made sure it is on but it is always worth mentioning.:)

---

### Post by JohnBoy99 on 2011-05-14
Hi
 
Take your computer to a WiFi spot and see if it works there. WiFi uses the same hardware. If it does not (as I suspect) then you have a hardware issue. 
 
The only other thing that comes to my mind is the ultra simple thing that your wireless is turned off. 
 
regards,

---

### Post by ClientAlive on 2011-05-14
> **JohnBoy99 said:**
> Hi
 
Take your computer to a WiFi spot and see if it works there. WiFi uses the same hardware. If it does not (as I suspect) then you have a hardware issue. 
 
The only other thing that comes to my mind is the ultra simple thing that your wireless is turned off. 
 
regards,

Could we see a:

```

rfkill list

```


If you can post the output of these things it will help us see if your wireless is blocked either in hardware or software.

Thanks

---

### Post by hr_giger on 2011-05-15
So, here's the results of rfkill list:

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

I also downloaded the driver again, from here: 

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

and reinstalled it. 

Rebooting after that, ubuntu stopped loading, and did the whole caps-lock-flashing thing. 

I reinstalled ubuntu 11.04, and realised that the driver appears to be a different version, which no longer supports ubuntu. 

I tried rerunning the old version of the driver (supports up to ubuntu 10.10, and I luckily had a copy) on the newly installed ubuntu, and that didn't make any difference.

Unfortunately there isn't a WiFi place within convenient distance, and all the other wireless networks are locked. So, it'll be a little while before I can get to test that suggestion. 

I also checked whether my wireless was switched off - and it's not.

So, I guess there's no driver for my network card, for Ubuntu 11.04. I've considered going back to 10.04, but that was the system it was on when it stopped working, and I had a bit of trouble getting it to work in the first place. I find it strange that that it stopped working, because I don't remember installing anything in particular, or even performing a system update. 

So.....

---

### Post by ClientAlive on 2011-05-15
> **hr_giger said:**
> So, here's the results of rfkill list:

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

I also downloaded the driver again, from here: 

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

and reinstalled it. 

Rebooting after that, ubuntu stopped loading, and did the whole caps-lock-flashing thing. 

I reinstalled ubuntu 11.04, and realised that the driver appears to be a different version, which no longer supports ubuntu. 

I tried rerunning the old version of the driver (supports up to ubuntu 10.10, and I luckily had a copy) on the newly installed ubuntu, and that didn't make any difference.

Unfortunately there isn't a WiFi place within convenient distance, and all the other wireless networks are locked. So, it'll be a little while before I can get to test that suggestion. 

I also checked whether my wireless was switched off - and it's not.

So, I guess there's no driver for my network card, for Ubuntu 11.04. I've considered going back to 10.04, but that was the system it was on when it stopped working, and I had a bit of trouble getting it to work in the first place. I find it strange that that it stopped working, because I don't remember installing anything in particular, or even performing a system update. 

So.....

You know, something just occurred to me. It's possible that, in the course of updating/ upgrading your system something is getting downloaded that makes it quit working. I've never had the misfortune of dealing with that but I've read it around. Not necessarily to do with wireless cards, but just in general, people talk about that happening and about how to stop that one thing from coming in with the other upgrades.

I know that doesn't exactly solve your problem right now, but it's something I thought of. If that were the case and you could nail it down, perhaps you stop that from happening in the future?

---

### Post by ClientAlive on 2011-05-15
I did a google search: "RTL8188CE 802.11b/g/n WiFi Adapter in ubuntu 11.04"

and came up with this:

[http://www.ubuntu.com/certification/catalog/category/NETWORK/index.html?start=100&batch=50](http://www.ubuntu.com/certification/catalog/category/NETWORK/index.html?start=100&batch=50)

The interesting thing is - while "11.04" shows up in the document (showing that the document is recent enough to include that release); and, "RTL8188CE 802.11b/g/n WiFi Adapter" also shows up in the document, they do not appear together.

Just because you mentioned in your first post: "My wireless card appears to be supported now, though (although I can't find official confirmation of this)."

---

