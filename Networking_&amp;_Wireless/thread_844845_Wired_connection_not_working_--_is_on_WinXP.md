---
title: "Wired connection not working -- is on WinXP"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by altonbr on 2008-06-30
I'm a guest at this house on my laptop and I can't connect to the network.

I cleared my DNS and search servers, turned on roaming and I still can't connect with physical CAT5.

The connection is a direct connection to a modem. I've never actually had a direct connection work in Ubuntu, only through a router.

Am I missing a step? Doesn't seem very intuative to use 'vim /etc/network/interfaces' or '/etc/init.d/networking restart'.

Oh, I've also tried killing nm-applet and restarting it, but it still won't work.

Lastly, the connection works on a Windows XP machine.

---

### Post by untermensch on 2008-06-30
The modem could possibly not like Linux? not sure why but I know the company I use for internet, it's software wont run on Linux. Can you connect threw wireless ?

---

### Post by lisati on 2008-06-30
If you have setup disks from your ISP or from your hardware supplier, you might want to run them through Windows first, get your connection up and running, and then try connecting with Linux.

---

### Post by altonbr on 2008-06-30
My Windows machine works fine and the connection is broadband so it should 'just work'.

I would post
> ifconfig
> cat /etc/network/interfaces
> sudo /etc/init.d/networking restart
but I can't connect to the Internet with it. No wireless networks around for me to piggy back either.

---

### Post by katiad on 2008-06-30
Can you copy the output of those into a textfile, which can be read from Windows?

Put it on a flash drive or a cd, maybe?

---

### Post by altonbr on 2008-06-30
Uh, sadly, I don't even have that. I'll have to figure something out.

In the mean time I can tell you that another Ubuntu computer doesn't work. What's the procedure of retreiving an IP address from your ISP? I've only ever worked with routers.

---

### Post by him610 on 2008-07-01
I experienced a problem similar to that this morning. What I did was to boot my machine into WinXP, then from the command line interface (CLI), enter "ipconfig /all". Make note of the IP address of your machine, subnet mask, the gateway, the router, and the DNS addresses in the response. 

Quit Windows. Restart and boot into _buntu. I assume you have properly installed the drivers for your wired NIC.

When your system has booted into a stable environment, open the Network Settings utility, unlock it with you password, highlight the Wired Connection, click on Properties, uncheck Enable Roaming. On the  Configuration box select Static IP Address, enter your IP address previously noted, the subnet Mask, and the Gateway address. Close the Properties box. Open the DNS tab, click on +Add next to the DNS Server area, add each DNS address previously noted. Close the Network Settings window.

This should configure your system so you can establish a connection to the upstream gateway (modem.)

Good luck, don't give up, and keep trying until you get it right.

---

