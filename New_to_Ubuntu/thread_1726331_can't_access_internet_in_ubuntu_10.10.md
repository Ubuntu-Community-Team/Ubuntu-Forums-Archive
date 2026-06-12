---
title: "can't access internet in ubuntu 10.10"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by anirban_chakravorty on 2011-04-11
Hi,
I am using ubuntu 10.10 and am a beginner to linux. My ISP provides internet connection through ethernet cables. I have configured the settings like IP address,subnet,gateway,DNS,alternate DNS properly and am able to ping my gateway also. But i am unable to access internet and the mozilla returns me with a 404 exception. My ISP provided me with a client software in windows where i am required to enter my username and password provided by them to connect to internet. They don't provide such client software for linux or ubuntu. Without internet connection in ubuntu i am even unable to install WINE to run such client software.
For more information: i am from Kolkata,India and am using Alliance Broadband as ISP. 
Please help!
Regards,
Anirban

---

### Post by K_45 on 2011-04-11
Are you connecting through a router or a separate modem? You should set those settings in the router (if required) and run an Ethernet cable to your PC. You don't need any external software.

---

### Post by anirban_chakravorty on 2011-04-11
@k_45: Thanks for the reply. 
But the router and the gateway resides with my internet service provider. They have local hotspots around the city where they have kept those devices. They have drawn ethernet cables from one of those points to my home. Hence, the ISP have the devices at their end and i have got only the ethernet cables at my end.
I am able to connect to the internet in windows through a client software provided by them, but they don't have any such software for the linux platform....
So, how do i connect to internet in ubuntu 10.10?

---

### Post by jtarin on 2011-04-11
Enter the command "ifconfig" (without quotes) in a terminal and post the results.
After that try the command  "ifup eth0" (without quotes) and then open a browser and tell us the results.
[You could also try this solution.]("https://help.ubuntu.com/community/ADSLPPPoE")

---

### Post by Johan.VB on 2011-04-25
> **jtarin said:**
> Enter the command "ifconfig" (without quotes) in a terminal and post the results.
After that try the command  "ifup eth0" (without quotes) and then open a browser and tell us the results.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:3f:13:26:5e  
          inet6 addr: fe80::202:3fff:fe13:265e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22103 (22.1 KB)  TX bytes:5327 (5.3 KB)
          Interrupt:10 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13168 (13.1 KB)  TX bytes:13168 (13.1 KB)


ifup eth0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied


Upon starting Firefox
Server not found
Firefox can't find the server at [www.google.com]("http://www.google.com").

this as done on a Acer TravelMate 291LMi
using a Realtek 8931 ethernet controller
connected to a motorola cable modem

---

### Post by jtarin on 2011-04-25
Try the command with sudo. ```
sudo ifup eth0
```When you get a response such as this...."Permission denied"....you must elevate your priviliges with sudo or change permission on the file. Also try the link in my previous post about using PPPOE if you get unsatisfactory results.

---

### Post by dineshs on 2011-04-25
anirban_chakravorty,
Pl try [this]("http://ubuntuforums.org/showpost.php?p=9611335&postcount=9")

---

### Post by Johan.VB on 2011-04-26
> **jtarin said:**
> Try the command with sudo. ```
sudo ifup eth0
```When you get a response such as this...."Permission denied"....you must elevate your priviliges with sudo or change permission on the file. Also try the link in my previous post about using PPPOE if you get unsatisfactory results.

"sudo ifup eth0" yielded:
Ignoing unknown interface eth0=eth0

PS
I have entered device MAC as the HWAddr I found with ifconfig, see above.
I see there are 3 different alphanumerical MAC numbers on the cable modem, 
but none in the wh:at:ev:er format
and none is the same as the HwAddr

---

### Post by jtarin on 2011-04-26
> S
I have entered device MAC as the HWAddr I found with ifconfig, see above.
I see there are 3 different alphanumerical MAC numbers on the cable modem,
but none in the wh:at:ev:er format
and none is the same as the HwAddrWe can not see your cable modem from the "ifconfig" you posted......should I use my psychic powers or will you share this source with us?:P

---

### Post by Johan.VB on 2011-04-26
> **jtarin said:**
> We can not see your cable modem from the "ifconfig" you posted......should I use my psychic powers or will you share this source with us?:P

these 3 alphanumericals are printed on the cable modem itself.
labelled as : HFC MAC ID, USB CPE MAC ID and MTA MAC ID respectively

btw 
the PPPoE option is for when there is need for a password and username to reach www, right?
my ISP havent given me any such, nor a DNS, and I surf quite happily anyhow :)

---

### Post by jtarin on 2011-04-26
If your hooked up with ethernet cable try the HFC MAC ID:

[Excellent link for cable modem users]("http://homepage.ntlworld.com/robin.d.h.walker/cmtips/index.html")

---

### Post by Johan.VB on 2011-04-27
> **jtarin said:**
> If your hooked up with ethernet cable try the HFC MAC ID:

[Excellent link for cable modem users]("http://homepage.ntlworld.com/robin.d.h.walker/cmtips/index.html")

HFC MAC ID dit not work.
the link only have hints for windows
only thing that might be something was non-running DHCP client process, but how figure out that in Ubuntu 10.10?

also, it seems "ipconfig" in windows is split into at least two commands in ubuntu : "ifconfig" and "route -n" but
> **route -n**
Kernel IP routing table Destination     Gateway         Genmask         Flags Metric Ref    Use Ifacegave no numbers whatsoever

---

### Post by jtarin on 2011-04-27
Just because it has hints for windows doesn't mean that the TCIP,PPPOE protocols have changed magically from one system to the nexr.....an IP address is still an IP address.

Post the results from the command ```
netstat --route
```

---

### Post by Johan.VB on 2011-04-28
> **jtarin said:**
> Post the results from the command ```
netstat --route
```

same response as for "route -n" above ie no numbers whatsoever, just the headings.

---

