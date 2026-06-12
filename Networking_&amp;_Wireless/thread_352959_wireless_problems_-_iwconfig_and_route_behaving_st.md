---
title: "wireless problems - iwconfig and route behaving strangely"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by cornflake_pirate on 2007-02-04
Hi guys, I've been trying for a few hours to get my wireless on another computer working and not making much progress. I'm running edgy, with a Netgear WG311v3. The driver is working fine through ndiswrapper. 

I've disabled the router's security (no WEP) just to get things working. Running 

```
iwlist wlan0 scan
```

gives me the router's ssid "Motorola" and the MAC address, and Mode: Managed.

I've put this information into iwconfig, but no matter what I do, iwconfig is not registering the router's MAC address when I tell it

```
iwconfig wlan0 ap aa:bb:cc:dd:ee:ff
```

iwconfig just says "Access Point:Not-Associated" instead of the MAC address that I just gave it.

Running dhclient always fails, so ifconfig says that wlan0 has no IP address.

I've also tried giving the computer a static IP (192.168.0.42) and registering that with the router. Then when I try 

```
ping 192.168.0.42
``` 

there are no problems (so the driver etc is definitely OK). Then when I try pinging anything else, it gives the error

```
192.168.0.42: Destination host is unreachable
```.

So static IP isn't working either.

In case it's relevant, "route" gives an empty routing table. Trying to tell route to use 192.168.0.1 gives a "network is unreachable" error. :(

 I really have the feeling that the problem is iwconfig not registering the router's MAC address. Any suggestions guys??

---

### Post by cornflake_pirate on 2007-02-04
sorry not sure how to delete posts...

---

### Post by gradedcheese on 2007-02-04
I believe that when you ping yourself, the packets don't actually go out on the wire(less)  ;)

Try using the router's SSID if that's being broadcast:

sudo iwconfig wlan0 essid Motorola

That said, you may want to check that 'wlan0' is really your network card and not a virtual interface for management.  Run:

ifconfig -a

Do other interfaces show up?  For example, if you have one Ethernet card and one Wireless card but you see intead:

eth0
eth1
wlan0

Then I would bet that 'eth1' is the real wireless card while wlan0 is its management interface.  eth1 would then be the one you want to iwconfig...

---

### Post by cornflake_pirate on 2007-02-04
Thanks for your help - I'll try that out asap. :)

---

### Post by cornflake_pirate on 2007-02-10
> **gradedcheese said:**
> I believe that when you ping yourself, the packets don't actually go out on the wire(less)  ;)

Try using the router's SSID if that's being broadcast:

sudo iwconfig wlan0 essid Motorola

That said, you may want to check that 'wlan0' is really your network card and not a virtual interface for management.  Run:

ifconfig -a

Do other interfaces show up?  For example, if you have one Ethernet card and one Wireless card but you see intead:

eth0
eth1
wlan0

Then I would bet that 'eth1' is the real wireless card while wlan0 is its management interface.  eth1 would then be the one you want to iwconfig...

ifconfig -a is showing

eth0     Link encap: Ethernet
lo         Link encap: Local Loopback
sit0      Link encap: IPv6-in-IPv4    NOARP
wlan0   Link encap: Ethernet


Other than the wireless, the computer has an ethernet adapter and an RJ11 port which I'm guessing is an internal modem. That seems to make all devices accounted for :/ 

"sudo iwconfig wlan0 essid Motorola" takes about 2 seconds for the computer to do, and there's no error messages. But then running iwconfig again, the ESSID is still "off/any". Same thing still for "sudo iwconfig wlan ap [router MAC addr]", the Access Point is still Not-Associated. 

I feel like I'm so close to it working but iwconfig isn't doing what it's told :/

Any other suggestions?

---

