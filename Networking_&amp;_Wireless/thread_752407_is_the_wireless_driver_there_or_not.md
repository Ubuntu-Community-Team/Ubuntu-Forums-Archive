---
title: "is the wireless driver there or not?"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by enuckon on 2008-04-11
Could not start wireless connection through integrated 
wireless adapter (ASUS P5K-E/WIFI-AP LGA 775 Intel P35) 
with Ubuntu 7.10.    I suspect that there is no default driver 
installed.   

Could anyone suggest if the driver is there at all or not?   

Here is some more info:

A.  I could see wireless signal bars from my and my neighbors 
routers.  

B.  The output of  **'sudo lshw'** mentions **no driver** for wireless
interface:

[B]"
...
description: Wireless interface
...
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
"[/B]

C.  Router **cannot be "pinged"**.

Thanks in advance.
E.

---

### Post by dstew on 2008-04-11
If you can see access points, there is at least some driver operating the card. Whether it is the best driver remains to be seen. Probably, you have a configuration problem, and not a driver problem.

Post the output of```
lspci
iwconfig
sudo lshw -C network
```

---

### Post by enuckon on 2008-04-12
Thanks a lot for reply.    I am attaching the outputs of the commands that you 
have mentioned (the names are self-explanatory).   Why would wireless driver 
name not show in 'lshw' output?   Best wishes, E.

---

### Post by dstew on 2008-04-12
From the outputs, it seems that everything is working OK, that is, there is a driver working the card, and the wlan0 network is connected to the access point. I am not sure why the driver is not listed with the lshw output, but maybe it is just the regular native driver, so it does not bother to list itself.

As to why you cannot get to the internet, or ping the router, that is all a matter of how the network is set up. How is your router set up? Is it a DHCP server? What are its network, netmask, and DNS settings? How is your computer network set up? To see that, post the output of```
cat /etc/network/interfaces
```

---

### Post by enuckon on 2008-04-13
Appreciate your help.   Here is the output of 'cat /etc/network/interfaces' 
attached.   Thanks, e.

---

### Post by dstew on 2008-04-13
How is your router set up? Your interfaces file is set up for a wireless card that gets its IP address by DHCP.

---

### Post by chili555 on 2008-04-13
Perhaps NetworkManager will not connect as long as your ethernet is connected. From lshw:>  ip=192.168.1.102This is a quote from [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for them;Don't you just love being 'managed'?

---

### Post by enuckon on 2008-04-15
Thanks, guys!    The wired connection is default indeed, as I just found out.  
What I also noticed with Network Tools is that two Wireless interfaces are 
created when I disable wired connection and activate wireless connection 
with Network Settings.   See attached images.   
**'wlan0'** in *netTool_wlan0.png* gets configured to connect to the 
router,  But the other one as in *netTools_wlan0_other.png* gets all the 
addresses and gives away more info.   The other one is named **wlan0:atahi**.   
Is **atahi** some driver name?   Why are two interfaces created?    
Thanks again, e.

---

### Post by enuckon on 2008-04-15
As for the router, it is set for DCHP, and a laptop under XP connects 
okay through wireless, but the Ubuntu one doesn't at this point.

---

### Post by chili555 on 2008-04-16
The avahi interface, to make a long story short, is created when the interface can't get an IP address from an outside source, such as a router, DSL modem, etc. avahi swings into action and assigns a placeholder address, 169.xxx. This just means you have not yet given all the correct details needed to connect. Did you press that *Configure* button? You will need to put in your ESSID and any encryption details, WEP, WPA, Kilngon, etc. Linux is very picky about what network it will connect to, for security reasons, so you must specify, exactly, the ESSID you want. And linksys is not the same as Linksys.

If you are not sure of the ESSID, open a terminal and do:```
sudo iwlist wlan0 scan
```Post back and tell us some good news.

---

### Post by enuckon on 2008-04-16
No luck at this point.  Here is what 'iwlist wlan0 scan' says
(without the neighbor's routers):
"
wlan0     Scan completed :
          Cell 01 - Address: 00:18:F8:F9:63:1A
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Quality=17/64  Signal level=64/65  
                    Encryption key:  on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000009b623a80db
"

DNS Servers as shown in Network Manager for Wireless Properties 
are the same as for the XP laptop with wireless connection through the 
same router.  I am attaching a screen shot of Netstat - Network 
Tools window:[B] it seems that gateway address and netmask are 
different from the XP laptop[/B].   How could I specify the working 
Gateway and Netmask addresses for Ubuntu wireless?    thanks, e.

---

### Post by dstew on 2008-04-17
> How could I specify the working Gateway and Netmask addresses for Ubuntu wireless?In the System --> Administration --> Network window, chose the interface, then Properties.

---

### Post by chili555 on 2008-04-17
> Cell 01 - Address: 00:18:F8:F9:63:1A
ESSID:"linksys"
Mode:Master
Channel:6
Frequency:2.437 GHz
Quality=17/64 Signal level=64/65
**Encryption key: on**I suggest you open a terminal and do:```
sudo iwconfig wlan0 essid linksys
sudo iwconfig wlan0 key <your_encryption_key>
sudo dhclient wlan0
```Let us know.

---

### Post by enuckon on 2008-04-17
No luck. 
> In the System --> Administration --> Network window, chose the interface, then Properties.

Well, the Properties cannot be changed for DHCP, they can only be 
adjusted if I select "static IP" instead of DHCP in the Network Window.  

I do not understand why the problem has to be the DHCP thing, 
because the wired connection deals with it okay.  
Here is response from "sudo dhclient wlan0" - see attached 
"dhclient.txt".   Do you see any problem there?   Thanks again, e.

---

### Post by dstew on 2008-04-18
You are right, DHCP should get the IP address, along with the gateway. At present, the only thing I can think of is that there is something wrong with the encryption, so the DHCP offer is not being seen, or the reply packets are not being seen. What is your current iwconfig output? And post your current /etc/network/interfaces file contents. Double check your encryption key and router setup, to make sure you have these correct. Router DHCP is enabled, correct? If it was once, and the wired got an IP, then it was disabled, the wired might still work using the old IP, but maybe the wireless cannot get an IP now. Just a thought...

Also, can you connect using a static IP setup? If not, then encryption may be the problem, not DHCP.

---

### Post by chili555 on 2008-04-18
Where or how have you specified your encryption key? Is it WEP or WPA? If you have not given your computer the secret handshake (the encryption key) and your router has it in place, you will never connect.

My own preference, and I may be wrong, is to stick with DHCP for now. With DHCP, if you have an IP address you know you connected. With static, you don't know unless you ping or try to surf the web.

---

