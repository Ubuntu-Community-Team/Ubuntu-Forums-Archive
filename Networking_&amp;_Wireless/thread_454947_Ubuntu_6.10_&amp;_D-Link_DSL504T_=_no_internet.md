---
title: "Ubuntu 6.10 &amp; D-Link DSL504T = no internet"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by dude1234 on 2007-05-26
Have recently loaded ubuntu 6.10 on my computer no. 2.
Modem is D-Link 504T. This modem has a 4 port router built in.
Can't get onto the internet on computer no. 2.
Using the same modem/router my Win2k-Firefox browser on computer no. 1 works fine, which is how I am accessing this forum.

I have read a few posts similar but am seeing conflicting reports.
I am considering upgrading my modem's firmware but the release notes make no mention of ubuntu.

What has to be done to connect ubuntu 6.10 to the internet with this D-link modem?

---

### Post by blueturtl on 2007-05-26
Hi.

I understand the D-Link DSL504T is a combined router and ADSL modem.

Question number 1 (this is probably stupid): does machine #2 connect to the router wirelessly or by wire?

Question number 2: if you connect via cable, to which port on the router is machine #2 connected?

Question number 3: is the router configured to use NAT or network address translation?

Question number 4: is the ethernet/wireless card in machine #2 identified and operational under Ubuntu? If so how is it set up?

---

### Post by dude1234 on 2007-05-27
thanks for responding - see my answers below:-

I understand the D-Link DSL504T is a combined router and ADSL modem.
YOU ARE RIGHT.
Question number 1 (this is probably stupid): does machine #2 connect to the router wirelessly or by wire?
BY WIRE - BOTH ARE BY WIRE.
Question number 2: if you connect via cable, to which port on the router is machine #2 connected?
TRIED A COUPLE OF DIFFERENT SOCKETS FOR PC#2 BUT HAVE ALWAYS HAD PC#1 IN THE TOP #1 SOCKET.
Question number 3: is the router configured to use NAT or network address translation?
JUST CHECKED AND NAT IS "ENABLED".
Question number 4: is the ethernet/wireless card in machine #2 identified and operational under Ubuntu? If so how is it set up?
I'VE HUNTED AROUND AND TRIED TO CHECK THIS AS BEST I COULD BUT PLEASE PROVIDE DIRECTIONS AS AM NEW TO LINUX ETC.

again thanks for helping
Jim

---

### Post by blueturtl on 2007-05-30
Sorry for the long delay.

I think your best course of action is to look at machine #2 a little closer.

You can check the settings of your ethernet on Ubuntu by going into the System menu, then selecting the submenu 'Administration' and from there select the menuitem 'Networking'. This should pop up a dialog for your password. After entering your password the network interfaces of your computer should be displayed.

If no interfaces are displayed in the list Ubuntu has failed to detect your network card. This is bad because Ubuntu is pretty good with wired network cards and I'm yet to run into a single wired card Ubuntu couldn't detect. While not impossible to fix the scenario is one where I would tell you to try another operating system of wait for a new version of Ubuntu to come out.

If however a wired network card is displayed on the list it's probably just misconfigured. I think you can click on the card in the list once and then select a button on the right that says 'Configure' or 'Manage' or something like that. The configuration screen for the network card will have different settings but seeing that you have NAT enabled it's pretty safe to say that the only setting that is of interest to you is wether or not the card is to be manually/automatically configured. Automatic configuration uses DHCP so make sure that is selected.

Let me know how this turns out for you and we'll proceed from there.

---

### Post by dude1234 on 2007-05-30
Many thanks to whoever wrote the above as it is something I can work through this weekend. Although, I'm pretty sure I have done what you said and the network card is there and is identified as an ethernet connection and I set it to DHCP. Will double check this.

I've also done some more on my own. Have downloaded a complete manual for the DSL-504 and am getting an idea of the network settings and options.

As I understand it, DHCP means that my modem gives out dynamic IP numbers to each computer on my network, which is essentially a LAN, these IP nos are 10.1.1.2 and 10.1.1.3, etc.

It also seems like there is some potential for me to change this over from DHCP to fixed IP no for each pc, but I haven't quite understood this yet. I am worried that I will stuff up my connection to the ISP.

One thing I do know is that my ISP gives me a dynamic IP. 203.xxx.xxx.178 etc.

---

### Post by blueturtl on 2007-05-30
If the web connection is working on machine #1 I doubt the router's settings need to be changed.

The NAT simply put is to allow more than a single system web access through a shared connection. See what would normally happen is that your machine would be directly hooked to a modem or what ever device that connects you online. Then that machine would directly receive the public IP address from your ISP. What the router does is act like it's that machine. The router then uses it's own internal workings to redistribute the stuff that is being sent and received to the machines connected to it. For this purpose it uses a DHCP server; a DHCP server will give all the machines connected to the router their own internal IP addresses so the router will know which machine is sending / receiving data. When the machines are connected to the internet they will all appear as just one machine behind that public IP address from the ISP. Clever huh?

Anyway, if the machine connected to the router is using DHCP it should automatically receive an IP address that the router intends as well as the other information required for web access. Do like you said and make sure DHCP is enabled. I also remembered that older versions of Ubuntu allow you to select the default gateway device in the network settings screen. Make sure that the interface that connects to the router is selected as the default gateway device!

This is information overflow, I know. Just hang in there. ;)

edit: If after all this the connection still refuses to work you could post your ifconfig output here.
You can enter the command 'ifconfig' into a terminal window. You can find the Terminal in the Applications menu, I think it's under Accessories in 6.10.

---

### Post by dude1234 on 2007-06-02
hi
1) I have checked in system-admin-networking. There are 4 tabs. (a) Connections->wired connection->address->DHCP. Concluded this is right. (b) General->host name=PC2, domain name=blank (c) DNS->dns servers=10.1.1.1 this is my router's IP, search domains = blank. (d) Hosts->127.0.0.1, alias=localhost, plus there are otheraliases all of which is foreign to me. I haven't ever changed any of the above just left it as is.

2) I have logged into my router from PC#1 and (a) checked status->DHCP clients and got 10.1.1.4=dude which is PC#1 and 10.1.1.2="unknown" which is PC#2 now that "unknown" is dubious because PC#2 I log in as "nedkelly" so why did it not identify that?

3) Also while logged in at the router from PC#1 I have done a Ping 10.1.1.2 which is PC2 and got an ok response. Then I ping 10.1.1.4 which is PC1 and get an ok response. This looks good.

4) Went back to Ubuntu on PC2 and checked in Tools->Network Tools and Ping 10.1.1.1 which is the router and got an ok result. Then also Devices=ethernet interface (eth0) protocol IPV4, IP=10.1.1.2,netmask=255.0.0.0,broadcast=10.255.255.255.

5) I can readily log-in to the router from PC2 or PC1.

Can't think what to do next, but PC2 does seem to have a good pathway to the router, although I am puzzled about the router result being "unknown" as noted above.

---

### Post by blueturtl on 2007-06-02
Well this has me baffled. The problem is not the connection or interfaces on either of the machines (both get their IP addresses). Also both machines respond to ping, yet only PC #1 can access the internet. Very curious indeed. Have you tried pinging the machines from each other also, or just through the router? What about pinging a web address through machine #2?

Is there another machine you could test with that you could hook to the router? I've never heard of routers having compatibility issues with machines running spesific operating systems.

What applications do you use to test internet access on PC #2?
I suppose you haven't tried to setup firewalls or iptables rules on PC #2 either?

I'm reaching here but does your ISP use a bridge mode connection? I've witnessed some problems with bridged connections and routers running NAT. I think you can find this information in the ADSL portion of your device's settings.

I have a feeling this will turn out to be something utterly silly, we've spent so much time and energy on it already. ;)

---

### Post by dude1234 on 2007-06-02
Previously you asked me to check the “ipconfig”.
On PC1 the result is -> DNS suffix = blank, IP address=10.1.1.4, Subnet mask = 255.0.0.0, Default gateway=10.1.1.1.
On PC2 the result is ->
nedkelly@PC2:~$ ipconfig
bash: ipconfig: command not found
nedkelly@PC2:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:D0:B7:86:6D:0B  
          inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::2d0:b7ff:fe86:6d0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2177 (2.1 KiB)  TX bytes:1818 (1.7 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


Ping result from PC1 to PC2 = OK
Ping result from PC2 to PC1 = blocked by Zonealarm.
Ping result from PC1 to router = OK
Ping result from PC2 to router = OK

What about pinging a web address through machine #2?
Ping result from PC2 to 66.230.200.100 = OK. 
This last one is a significant outcome as it means PC2 has sent data through the internet to Wikipedia server and received a response. Hmmm!

Is there another machine you could test with that you could hook to the router?
I recently set up a W2k PC for my parents and had it connected on the same router.

What applications do you use to test internet access on PC #2?
Firefox – it’s all I have as yet just what came with ubuntu.

I suppose you haven't tried to setup firewalls or iptables rules on PC #2 either?
No.
I'm reaching here but does your ISP use a bridge mode connection?
Don’t believe so. There is a bit of info about this in the manual for the router but to my knowledge I am using DHCP.

Thanks again for all your help. Please keep the suggestions coming.
Jim

---

### Post by dude1234 on 2007-06-03
FOUND THE SOLUTION TO MY PROBLEM IN THE TEXT QUOTED BELOW.
I actually read this previously and thought I had tried it but perhaps I omitted the close-down and restart of Firefox. Many thanks to all helpers on this forum.
Re: Bt Voyager router works Dlink DSL-504 wont
If I read you correctly, the Kubuntu CD will connect to the internet through the D-Link router, but the Ubuntu one won't. Don't understand that but, whatever, I think it might be worth checking to see this isn't the IPv6 issue causing the problem. Windows XP isn't yet enabled for IPv6 (afaik), but most Linux distros are. Inadequate or old router firmware is confused by IPv6 modified IP addressing, and you get what you are experiencing.

In fact, this is what I experienced with my D-Link-G604T wireless router last year. Windows connected fine, but most parts of Linux didn't. Disabling IPv6 in whatever Linux distro I was using was a workaround until I updated the router firmware and then, bingo, everything was hunky-dory.

A quick experiment. Fire up Ubuntu with your D-Link connected and start Firefox. Type 'about:config' in the address bar (without the quotes), and then 'ipv6' (again no quotes) in the filter. You should be seeing a line beginning 'network.dns.disableIPv6'. Double-click on 'false' (or right-click) and it will change to true. You have now disabled IPv6 in firefox. Close it down and start it up again, and if you can now browse the internet, IPv6 was your problem. If not, sorry - don't know what's going on.

If it is IPv6, search these forums for ways of disabling IPv6 globally in your installed Ubuntu or, much better, upgrade your firmware if it is available.

---

### Post by blueturtl on 2007-06-04
> Is there another machine you could test with that you could hook to the router? I've never heard of routers having compatibility issues with machines running spesific operating systems.

> Windows XP isn't yet enabled for IPv6 (afaik), but most Linux distros are. Inadequate or old router firmware is confused by IPv6 modified IP addressing, and you get what you are experiencing.

Well now that I would have never suspected. Good that you found the solution though. I'll have to remember this for future troubleshooting...

---

### Post by dude1234 on 2007-06-09
After fixing the problem with firefox, I continued to have issues with other programs on ubuntu. Finally this morning I installed an upgraded firmware package for my DSL-504T modem. After that all the issues have disappeared. Ubuntu can connect to the internet now and my Evolution email can now connect to my mail server.

keywords:- internet DSL modem 504T D-Link email Evolution ubuntu update upgrade software

---

