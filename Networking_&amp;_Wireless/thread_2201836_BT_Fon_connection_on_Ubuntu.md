---
title: "BT Fon connection on Ubuntu"
date: 2014-01-26
forum: Networking &amp; Wireless
---

### Post by josephconvert on 2014-01-26
I am trying to connect with BT Fon on Ubuntu 12.4. I can connect to other wireless connections listed in Network connections, and my own using my key. But the BT Fon appears to connect but my browser says serve not found.
                    
  I have looked at endless Google pages on this question and nobody know the answer, or those who say they do have not actually tried it for themselves.
   
  The best I can find out is that BT Fon connection can only be established in Windows, as Windows has a piece of vital software not available to Ubuntu. I can connect to BT Fon on my Windows laptop, so this seems to be correct. 
   
  Help would be most appreciated – even if it is to confirm that BT Fon is not possible on Ubuntu.

---

### Post by chili555 on 2014-01-26
> The best I can find out is that BT Fon connection can only be established in Windows, as Windows has a piece of vital software not available to Ubuntu. I can connect to BT Fon on my Windows laptop, so this seems to be correct. I highly doubt it. I'm not saying impossible but I am saying improbable.

Did you Google this? [http://ubuntuforums.org/showthread.php?t=1891220](http://ubuntuforums.org/showthread.php?t=1891220)> Been using BT internet for nearly 2 years now. Works the same whether i'm on my windows box, ubuntu box, or slackware box. I am interested in the statement that:> the BT Fon appears to connect but my browser says serve not found.From the terminal, what does this tell us?```
nm-tool
sudo lshw -C network
```Thanks.

I get the same kind of hokum from my ISP, too; "We don't support Linux. Bye." I ask them to provide a working IP address at my doorstep and I'll figure out the rest. I have, so far, had little or no difficulty doing so.

---

### Post by josephconvert on 2014-01-26
Here is what I get when putting 
nm-tool
sudo lshw -C network

into terminal:

```

joseph@joseph-System-Product-Name:~$ nm-tool  
 

 NetworkManager Tool  
 

 State: connected (global)  
 

 - Device: wlan1  [BT Fon] ------------------------------------------------------  
   Type:              802.11 WiFi  
   Driver:            rtl8192cu  
   State:             connected  
   Default:           no  
   HW Address:        64:66:B3:0A:49:6D  
 

   Capabilities:  
 

   Wireless Properties  
     WEP Encryption:  yes  
     WPA Encryption:  yes  
     WPA2 Encryption: yes  
 

   Wireless Access Points (* = current AP)  
     *BT Fon:         Ad-Hoc, DE:FF:53:F7:C3:9F, Freq 2412 MHz, Rate 0 Mb/s, Strength 100  
 

   IPv4 Settings:  
     Address:         10.42.0.1  
     Prefix:          24 (255.255.255.0) 
     Gateway:         0.0.0.0  
 

 

 

 - Device: eth0 -----------------------------------------------------------------  
   Type:              Wired  
   Driver:            forcedeth  
   State:             unavailable  
   Default:           no  
   HW Address:        48:5B:39:BA:7C:22  
 

   Capabilities:  
     Carrier Detect:  yes  
 

   Wired Properties  
     Carrier:         off  
```
 

 
```

 joseph@joseph-System-Product-Name:~$ sudo lshw -C network  
 [sudo] password for joseph:  
   *-network                
        description: Wireless interface  
        physical id: 1  
        bus info: usb@1:5  
        logical name: wlan1  
        serial: 64:66:b3:0a:49:6d  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-58-generic-pae firmware=N/A ip=10.42.0.1 link=yes multicast=yes wireless=IEEE 802.11bgn  
 joseph@joseph-System-Product-Name:~$
```

---

### Post by josephconvert on 2014-01-26
I should mention that although it says it BT Fon is connected, and it seems, Firefox says there is no internet connection.

I should also mention that if I connect wirelessly through my normal WEP connection from my router there is no problem connecting. Nor if I connect wired. It is only BT Fon that gives this problem.

Also, the link you sent me to is not to do with BT Fon connection, but simply with wireless connection in Ubuntu. This is distinct. BT Fon is a hotspot connection which should work without your router and from anywhere.

---

### Post by chili555 on 2014-01-26
This IP address and the lack of a gateway address:> Address: [COLOR="#FF0000"]10.42.0.1[/COLOR]
Prefix: 24 (255.255.255.0)
Gateway: 0.0.0.0
...suggest you edited Network Manager to 'Create New Wireless Network.' [http://www.techotopia.com/images/c/c9/Ubuntu_11_unity_network_menu.jpg](http://www.techotopia.com/images/c/c9/Ubuntu_11_unity_network_menu.jpg) That is for computer-to-computer or ad hoc arrangements. I doubt that is what you want. I think you want computer-to-router or an infrastructure arrangement. Please right-click the Network Manager icon, select 'Edit Connections' and Wireless. Be sure the mode is set to Infrastructure and not Ad Hoc. If you have added any extra settings in there, remove them. Reboot and try to connect again.> BT Fon is a hotspot connection which should work without your router and from anywhere. However, the hotspot is still a wireless router.

---

### Post by josephconvert on 2014-01-26
Thank you for your reply. I would like to mention that BT Fon does not connect to wireless in the normal way. I have not tried your connection suggestion because I can connect normally to my wireless router and putting in the WEP code.

BT Fon does not work that way. It connects directly to the web and calls up a BT log in page in the browser. You then log in in the browser as a BT customer or as someone who has purchased time on BT Fon. This does not involve a WEP key.

When I connect wirelessly to my router and follow your instructions in your previous post in Terminal I get this reading:

```
joseph@joseph-System-Product-Name:~$ nm-tool 

NetworkManager Tool 

State: connected (global) 

- Device: wlan1  [BT Fon] ------------------------------------------------------ 
  Type:              802.11 WiFi 
  Driver:            rtl8192cu 
  State:             connected 
  Default:           no 
  HW Address:        64:66:B3:0A:49:6D 

  Capabilities: 

  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 

  Wireless Access Points (* = current AP) 
    *BT Fon:         Ad-Hoc, DE:FF:53:F7:C3:9F, Freq 2412 MHz, Rate 0 Mb/s, Strength 100 

  IPv4 Settings: 
    Address:         10.42.0.1 
    Prefix:          24 (255.255.255.0) 
    Gateway:         0.0.0.0 



- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            forcedeth 
  State:             unavailable 
  Default:           no 
  HW Address:        48:5B:39:BA:7C:22 

  Capabilities: 
    Carrier Detect:  yes 

  Wired Properties 
    Carrier:         off 
```


```
joseph@joseph-System-Product-Name:~$ sudo lshw -C network 
[sudo] password for joseph: 
  *-network               
       description: Wireless interface 
       physical id: 1 
       bus info: usb@1:5 
       logical name: wlan1 
       serial: 64:66:b3:0a:49:6d 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-58-generic-pae firmware=N/A ip=10.42.0.1 link=yes multicast=yes wireless=IEEE 802.11bgn 
joseph@joseph-System-Product-Name:~$ 
```

This is a successful connection. But if I try to connect with the BT Fon I get the result sent before.

My point is that connection to BT Fon is not like an ordinary connection and seems only to work in Windows, as it does in my Windows PC.

---

### Post by chili555 on 2014-01-26
> Wireless Access Points (* = current AP)
*BT Fon:[COLOR="#FF0000"] Ad-Hoc[/COLOR], DE:FF:53:F7:C3:9F, Freq 2412 MHz, Rate 0 Mb/s, Strength 100

IPv4 Settings:
[COLOR="#FF0000"]Address: 10.42.0.1
Prefix: 24 (255.255.255.0)
Gateway: 0.0.0.0
[/COLOR]
What exactly did you change?

Are you saying that everything seems to work as expected except that the browser log-in never appears?

---

### Post by josephconvert on 2014-01-26
Thank you. Yes, everything seems to work, but the browser log-in does not appear. Even if I put [www.btfon.com](www.btfon.com) in the browser no connection can be made. Firefox does not recognize any connection to the internet. But the Ubuntu connection icon says a connection is made. I can disconnect it and reconnect it, but with the same results.

I have not changed any settings at all, The only difference between the readings I sent is one is taken with the BT Fon connection, the other with wiress connection through my router with my WEP key.

BT Fon does not require a WEP key because it acts as an unsecured connection. The connection is made by log-in on the BT website.

---

### Post by chili555 on 2014-01-26
Actually, I'm stuck here. I have tried to get the login page to show up using Firefox, Chromium and even lynx, a Text-mode WWW Browser. I can't do it. However, I suspect that when you open the browser, DNS is set by BT Fon and redirects to their login page. If you supply the correct user name, a proper DNS nameserver is given. Since Ubuntu uses DNS caching and /etc/resolv.conf looks like:```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1 
```The DNS never gets rewritten. At least that's my best guess until I disable DNS caching on a test rig and investigate further.

I wish I had a better answer. Maybe a colleague will jump in and help us.

---

### Post by josephconvert on 2014-01-27
Thank you for looking into this so carefully. You are right. Firefox should spring open into the BT Fon log-in page at btfon.com. This is what happens in Windows. If it does not spring open on its own, it goes directly there when you open your browser manually. 

On a Google search for this problem some say Windows has a Cisco software which is not available for Linux and this enables the proper connection in Windows. 

If you ask for BT support they just say they do not support Linux, and that is all they will say.

---

### Post by grahammechanical on 2014-01-27
Just some information

[http://www.btfon.com/](http://www.btfon.com/)

> [COLOR=#333333][FONT=Arial]As a BT broadband customer, you get _automatic membership to the Fon network_. It&#8217;s the easiest way to get free access to Fon hotspots throughout the UK and across the world.[/FONT][/COLOR]

> [COLOR=#333333][FONT=Arial]One signal is encrypted and private - it&#8217;s just for you. The other signal is public, and accessible _to registered members of the Fon community_. [/FONT][/COLOR]

If an ISP is failing to provide the service that we are paying for we can tell them that they are going to lose our custom. And then change supplier.

> [COLOR=#333333][FONT=Arial]If you are a BT Broadband user and you would like to check whether you are opted in you can[/FONT][/COLOR]

> [COLOR=#333333][FONT=Arial]The BT Home Hub router has the Fon community software pre-installed. [/FONT][/COLOR]

> [COLOR=#333333][FONT=Arial]Anyone with a broadband connection can join Fon. Just [/FONT][/COLOR][buy a Fonera router]("http://corp.fon.com/en/products")[COLOR=#333333][FONT=Arial] and connect it to ADSL/broadband. Once your Fon Spot has been created and registered, you&#8217;re ready to enjoy free WiFi at millions of Fon Spots worldwide.[/FONT][/COLOR]

Regards.

---

### Post by josephconvert on 2014-01-27
Yes, this information is correct. Anyone can join BT Fon. But also anyone who uses BT Broadband is automatically opted in to BT Fon. That is the case with me, and that is why I can use it with no problems with Windows. Also, no equipment is required. The connection is made wirelessly and from any place near a Hotspot where BT Fon shows up as a connection. 

Also, as you observe, anyone who is not a BT customer may join BT Fon by purchasing units of time on it.

A Fonera router is a special router that makes part of your own Broadband connection contribute to a Fon hotspot by sharing your bandwidh. With one of these you will show up to others as a BT Fon wireless connection they can connect with. This is distinct from simply connection to BT Fon wherever you happen to be. Obvioulsy you do not carry your router around with you when traveling! 

I daresay, as you suggest, that I could complain to BT that a service I am paying for is unavailable on a Linux system, and perhaps that they are part of a monopoly with Microsoft. There remains the question of whether Mac users can connect with BT Fon.

---

### Post by josephconvert on 2014-01-28
I made a mistake previously and sent the same connection information twice, when I meant to send one for the BT Fon connection and one for wireless connection to my router. Here is the connection to me router: ~~~~~~~~~~~~~~~~~~~~~~~~ joseph@joseph-System-Product-Name:~$ nm-tool    NetworkManager Tool    State: connected (global)    - Device: wlan1  [ap00300A5C121D] ----------------------------------------------    Type:              802.11 WiFi    Driver:            rtl8192cu    State:             connected    Default:           yes    HW Address:        64:66:B3:0A:49:6D      Capabilities:      Speed:           1 Mb/s      Wireless Properties      WEP Encryption:  yes      WPA Encryption:  yes      WPA2 Encryption: yes      Wireless Access Points (* = current AP)      SKY8B39D:        Infra, 7C:4C:A5:9D:C8:61, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA2      *ap00300A5C121D: Infra, 00:22:3F:5C:38:28, Freq 2462 MHz, Rate 54 Mb/s, Strength 76 WEP      IPv4 Settings:      Address:         192.168.0.4      Prefix:          24 (255.255.255.0)      Gateway:         192.168.0.1        DNS:             192.168.0.1      - Device: eth0 -----------------------------------------------------------------    Type:              Wired    Driver:            forcedeth    State:             unavailable    Default:           no    HW Address:        48:5B:39:BA:7C:22      Capabilities:      Carrier Detect:  yes      Wired Properties      Carrier:         off      joseph@joseph-System-Product-Name:~$ sudo lshw -C network  [sudo] password for joseph:     *-network                        description: Wireless interface         physical id: 1         bus info: usb@1:5         logical name: wlan1         serial: 64:66:b3:0a:49:6d         capabilities: ethernet physical wireless         configuration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-58-generic-pae firmware=N/A ip=192.168.0.4 link=yes multicast=yes wireless=IEEE 802.11bgn  joseph@joseph-System-Product-Name:~$

---

### Post by grahammechanical on 2014-01-28
Is this solved now? I was wondering about the special software in the routers that are used for FON connectivity. Is this software trying to load Internet Explorer and not just the system's default browser? Just a wild guess.

---

### Post by josephconvert on 2014-01-28
> **grahammechanical said:**
> Is this solved now? I was wondering about the special software in the routers that are used for FON connectivity. Is this software trying to load Internet Explorer and not just the system's default browser? Just a wild guess.

There are a number of things to update here. It occurred to me to try running the Ubuntu Live CD in my Compaq NX6325 laptop. Ubuntu cannot use the built-in wireless on this laptop, which I already knew. So I plugged in my USB TP-Link WN822N. Ubuntu immediately recognizes this and lists the available wireless connections. I tried the BT Fon connection. As on my Desktop computer, it appears to connect but Firefox says no server is available when I open it. Even if I direct it to [www.btfon.com](www.btfon.com) nothing happens. 

If I try to connect to my wireless router there is no problem. I get instant request to put in my WEP and a connection is established. The result of this was the same as with my desktop.

Wondering if it was Ubuntu that was the problem, I tried the latest Fedora Live CD in my Laptop. This picked up the internal wireless hardware on boot-up and allowed me to connect to BT-Fon and sign in on Firefox - which opened in the BT log-in page when I opened Firefox. So in Fedora, with the internal wireless of my Compaq there is no problem.

So I plugged in the USB TP-Link. This showed a list of connections instantly, including BT Fon. But when I tried connecting to BT Fon it appeared to connect but no connection was possible in Firefox. I tried my own router wireless connection and this was fine.

This all indicates that Linux does not correctly configure TP-Link. It 'half' works in Linux. Yet this USB wireless device is listed as recommended for Ubuntu on the website that tests wireless cards and USB devices for Ubuntu. That is why I purchased it. If works perfectly in Windows, including BT Fon.

So the problem lies with how Linux configures TP-Link, or else TP-Link is not compatible with Linux as it is said to be.

It looks as if the only way out of this is to find a different wireless USB for my desktop.

Thank you for sticking with the problem! If you have any suggestions that spring to mind from this information I would be very pleased to hear them.

---

### Post by grahammechanical on 2014-01-28
May be you need to change a setting inside the TP-Link? Perhaps you could access the settings of the BT router and then compare with the settings in the TP-Link and see if there is anything that you could change. I am out of ideas.

Regards.

---

### Post by josephconvert on 2014-01-29
> **grahammechanical said:**
> May be you need to change a setting inside the TP-Link? Perhaps you could access the settings of the BT router and then compare with the settings in the TP-Link and see if there is anything that you could change. I am out of ideas.

Regards.

Well, there are no settings to change in the TP-Link adapter. It is simply an adapter you plug in to a USB port which Ubuntu recognizes and configures. Nor would changing any settings in the router have any effect. The adapter runs independently of the router, and when connection to any connection aprt from my own the router may be turned off. The adapter is for picking up other routers or hotspots. BT Fon is a hotspot and may be connected with through the adapter without the router be turned on. In other words, the TP-Link is an adapter for traveling away from home, although it may also be used for extending wireless range at home between rooms.

Later I will send the connection readings of the faulty connection to BT Fon. Something there may give us a clue what is happening.

---

### Post by josephconvert on 2014-01-30
I said I would send the connections readings for the failed connection in Federa. However, Federa Live CD does not recognize the commads;
nm-tool
sudo lshw -C network

I suppose these commands are unique to Ubuntu and different commands are required for Fedora.

Just to summarize. Federa connects successfully on my Compaq NX6325 using its internal Wifi connection, including BT Fon.

But using TP-Link USB adapter it connects to connections requiring WEP key, but appears to connect to BT Fon but in fact does not. It would seem that Linux distros don't configure TP-Link fully, even though this is listed as an adapter recommended for Linux and for Ubuntu. So a different adapter is needed. But I have no way of knowing which to try since this one is listed as working fully with Ubuntu when in fact it only half works.

---

