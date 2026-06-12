---
title: "Internet connection"
date: 2005-04-28
forum: Networking &amp; Wireless
---

### Post by larry on 2005-04-28
Hi Everybody,
I am a newbie setting up his first internet connection.
First I was unsure about whether my ethernet card was recognized, but I can at least  ping it, which should be a good sign.
Now I have an aethra stargate router (not aethra II or something else), which should be linux compatible .
The seller told me it has already an IP address configured, the DHCP server is enabled, then he gave me the router's username and no password is configured. 
On the other hand, my internet provider (adsl connection) gave me long before another username and password and in my home connection configuration instructions I read that the IP and the DNS addresses are both given by the server (though I can use some DNS addresses).
Furthermore, it tells me that If I want to connect to the internet via the ethernet card I should use:
Protocol: PPPoE
Encapsulation: LLC
VPI: 8 VCI: 35

I think i have all of the relevant data, but I do not know how to handle them. Should I use ifconfig to give my eth0 the same address as the router? My problem is that I do not know how to reach the router.
Thanks a lot
Larry

---

### Post by nad on 2005-04-28
Your router has a built in web interface accessable with a web browser. A quick search did not turn up the default ip address of your unit. The most common default addresses are 192.168.0.0 and 192.168.1.0.

In a web browser, type in: [http://192.168.0.0](http://192.168.0.0) (or the correct address listed in your manual) for the web configuration interface login and configure the router per your manual and isp's instructions.

---

### Post by hobnob on 2005-04-28
Hi Larry,

I don't have any experience with the Aethra router, but these things usually all work the same way. You need to set your ethernet card to get its address automatically from the router using DHCP. You can easily set this in Gnome by going to 

System -> Administration -> Networking

then 

Select your ethernet connection -> Properties -> Configuration -> DHCP.

This should reset your address immediately, but if no luck, a restart will always solve it : ) Now you have to set up the router to tell it your ISP's details.

Open Firefox and go to '10.0.0.1'. You should get the router's login page asking for a username/password. Enter the one the seller gave you, or if the [manual](http://edirectory.aethra.net/edirectory/downweb.asp?ID=1017) is anything to go by, you can enter anything for the username, and leave the password field blank.

From here, you can follow the router's "Quick Start" procedure to enter the details for your ISP, i.e. PPPoE, LLC, VPI/VLC... 

Once this is all done, you should be connected! So come back here and tell me how easy it all was : )

---

### Post by larry on 2005-04-28
Thanks a lot, but something seems to go wrong.
1)I selected DHCP in the properties of the eth0 connection
2)I then when I open firefox and I type the address 10.0.0.1 (confirmed by my vendor), but I find out that my connection is refused.

BTW, if I also try activating the DHCP ethernet connection, after configuring its properties in step 1). It then happens that the box I tick gets unticked almost at once.
Seen that I can ping my eth0 card, do you think the problem is with the router?
Cheers
Larry

---

### Post by hobnob on 2005-04-28
What do you mean by "ping my card"? To ping a card, it has to have an address associated to it, and so what address are you using?

Can you also post the output of 'ifconfig', so I can see what's going on with the card. Also, try "ping 10.0.0.1" so see if you can see the router. It sounds like your card is not talking to the DHCP server, so we have to find out why not.

---

### Post by nad on 2005-04-28
"BTW, if I also try activating the DHCP ethernet connection, after configuring its properties in step 1). It then happens that the box I tick gets unticked almost at once."

Have you power cycled both the router and your computer?

Please post your file: /etc/network/interfaces

---

### Post by larry on 2005-04-29
This is what I get if I run ifconfig eth0 after configuring the IP and the netmask.


eth0     Link encap:Ethernet     HWaddr 00:0E:2E:28:D4:01
         inet addr:10.0.0.2      Bcast:10.255.255.255   Mask:255.255.255.0
         inet6 addr: fe80::20e:2eff:fe28:d401/64 Scope:Link
         UP BROADCAST MULTICAST MTU:1500   Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:33 errors:0 dropped:0 overrruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 b)  TX bytes:6570 (6.4 KiB)
         Interrupt:ll Base address:0xe000


I can ping the eth0 IP 10.0.0.2 or any other I choose, but I cannot reach 10.0.0.1 which is the router's IP.

This is what I read in /etc/network/interfaces :

auto lo
iface lo inet loopback

iface eth0 inet dhcp
name Ethernet LAN card
auto eth0

Thanks a lot

Larry

---

### Post by hobnob on 2005-04-29
When you say "configured the IP and netmask", you just told the interface to use DHCP, didn't you? Your interfaces file looks like it is correct, and if you didn't specify an IP directly, your card has been assigned the correct IP, so I am wondering why it can't see the router.

Can you post the output of "route" please?

Edit: "I can ping...any other I choose". Hold on... which other IPs are you choosing? Can you ping public IPs? Or are manually setting your card to 10.0.0.x and pinging that?

---

### Post by larry on 2005-04-29
Hi,
This is the output of the route command:
Destination     Gateway     Genmask                    Flags   Metric     Ref   Use   Iface
10.0.0.0                  #       255.255.255.0                  U       0           0        0     eth0

 I first configured the ethernet card using ifconfig  to set its IP to 10.0.0.2 and its netmask to 255.255.255.0.
Then I tried gnome utility and I selected dhcp in the properties of the ethernet connection (this time the box remained ticked).
Then I used the route command.
Before I meant I can always ping my eth0 card no matter what ID I give to it (10.0.0.*).
Does the output of route mean the default ip address is 10.0.0.0?
I can ping that BTW.
Cheers
Lorenzo

---

### Post by larry on 2005-04-29
Thanks everybody!
I solved the problem (I was using the wrong cable and the wrong internet protocol).
Best Regards
Lorenzo

---

