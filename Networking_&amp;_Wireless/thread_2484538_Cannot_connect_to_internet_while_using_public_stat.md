---
title: "Cannot connect to internet while using public static IP address"
date: 2023-03-02
forum: Networking &amp; Wireless
---

### Post by chris-dutrow on 2023-03-02
[COLOR=#232629][FONT=-apple-system][FONT=var(--theme-post-body-font-family)][FONT=inherit]Having a weird problem with configuring a public static IP address in Ubuntu 20.04. The computer will not connect to the internet. Web browser will not load any web pages and I cannot ping 8.8.8.8
[/FONT]
[FONT=inherit]I checked over the settings I'm using many times.
  * The IP address is correct, the gateway is correct and the netmask is correct. DNS settings are correct.
  * Verified that the problem is not with the networking hardware or cable by connecting the box to the internet through a "normal" home router using DHCP.
  * Verified that the ISP settings are fine and the public IP address is working fine by connecting a windows machine using identical settings (The windows machine is off now and is no longer using the IP address)

[/FONT]From what I understand, I should be able to put in the Static IP address, Netmask, Gateway, and DNS servers and that should be it...
[FONT=inherit]
This is a brand new Ubuntu installation on a Mini PC box.[/FONT]
[FONT=inherit]
The hardware architecture is:[/FONT]

[LIST]
[*]COX modem
[LIST]
[*]Router
[LIST]
[*]General office stuff
[*](I tested Ubuntu box here with DHCP to make sure there wasn't an issue with the hardware or cable)
[/LIST]

[*]Swtich
[LIST]
[*]Servers
[*](I tested a windows machine here to make sure there was not a problem with the IP address configuration)
[*]**The Ubuntu box** (that won't connect to the internet)
[/LIST]
[/LIST]
[/LIST]
[FONT=inherit]I also tested these things:[/FONT]

[LIST]
[*]Made sure the ethernet cable and network hardware worked by hooking Ubuntu box up to my router and using DHCP internet - internet worked fine on this Ubuntu box when using DHCP and my router.
[*]Made sure the static IP worked by configuring the same settings on a windows box that I have. That box was able to successfully get internet with that IP address hooked up using the same cable and same switch
[*]Tried disabling IPv6 (I think this is how windows does it if I don't explicitly supply a manual IPv6)
[/LIST]
[FONT=inherit]I'm not really sure what else to do. I don't even know how to trouble shoot this in terms of looking to find out where the connection is failing. My guess is there is some obscure setting I need to correct, or there is some default part of the Ubuntu installation that is blocking the connection. 

Here are some screen shots of the configuration:

[IMG]https://tmpej.s3.amazonaws.com/Screenshot+from+2023-03-02+09-23-30.png[/IMG]

[IMG]https://tmpej.s3.amazonaws.com/Screenshot+from+2023-03-02+09-23-07.png[/IMG]


[IMG]https://tmpej.s3.amazonaws.com/Screenshot+from+2023-03-02+09-24-17.png[/IMG]

Scrolled down here to show the routes:
[IMG]https://tmpej.s3.amazonaws.com/Screenshot+from+2023-03-02+09-24-24.png[/IMG]


[/FONT]
[/FONT]
[/FONT][/COLOR]

---

### Post by TheFu on 2023-03-02
Please use text, not images for stuff like this.  Please, change the huge images to attachments. Be kind to people who paid for internet by the byte.

The output from **ip a** and **ip route | column -t** and the contents of the /etc/resolv.conf are usually enough after basic ping tests show what the core issue is.  The first test is really to ping from close devices to farther and farther away devices - peers, your router, your gateway, the ISP gateway, then remote servers.  Ping by IP first, but try the names too.  If you can't ping 1.1.1.1 or 8.8.8.8, the issue with closer.

[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) 

BTW, sometimes ISPs have outages.

Lastly, if you are behind a router in your building, then the public IP is usually taken by it and you have to choose a static IP on the LAN (non-routable range) for your systems.  If the DHCP range provided from your home router is 192.168.1.x, then you can't just grab some public IP and use it.  Your system must be on the 192.168.1.x subnet ... or some other subnet configured in the router to be managed.

---

### Post by coffeecat on 2023-03-02
Cross-posted from: [https://askubuntu.com/questions/1457304/machine-with-static-ip-address-will-not-connect-to-the-internet-20-04](https://askubuntu.com/questions/1457304/machine-with-static-ip-address-will-not-connect-to-the-internet-20-04)

---

