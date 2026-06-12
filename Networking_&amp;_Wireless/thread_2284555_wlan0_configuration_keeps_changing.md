---
title: "wlan0 configuration keeps changing"
date: 2015-06-30
forum: Networking &amp; Wireless
---

### Post by francois.teyssere on 2015-06-30
Hi everyone, 

I'm trying to configure the wifi of my laptop to be able to connect to a wifi access point of a device. 

The device's ip is 192.168.1.209 (and the access point's is 192.168.1.9), so I'm trying to give wlan0 the IP 192.168.0.4. 

I first tried with ifconfig, but at some point (after around 30secs) the configuration seem to expire and go back to previous. As I want something more permanent, I tried to edit /etc/network/interfaces file, which now is the following : 

> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.4
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
gateway 192.168.1.9

iface eth0 inet dhcp

The problem is that the issue remains. When I ifdown the ifup wlan0, it has the desired the settings, but after I connect and send some pings during around 30secs, it disconnects and takes back the previous settings. Did I miss anything in the configuration process?

---

### Post by Bucky Ball on 2015-06-30
Welcome. Click network manager> edit> highlight the wireless connection and click 'edit'> IPv4 tab> change auto-config to manual and set up your static IP address, gateway and DNS servers. 

Whatever you've done in ifconfig may, of course, cause problems. Set that back to its original state, as it was before you tweaked it prior to setting up a static IP address in Network manager (because of course you saved a copy of the original /etc/network/interfaces before tweaking it so just move it back :)).

---

### Post by francois.teyssere on 2015-06-30
Ow okay... I didn't even thought there was a simple way to do that ^^'

Of course I had a backup of all the config files I modified, I won't make my newbie's mistakes again ;)

Thanks for the help!

---

### Post by Bucky Ball on 2015-06-30
Good luck and let us know how you go. I tried for hours setting up a static IP for my local machine, unsuccessfully, on the router when I first got into Ubuntu, then, just  on a whim, thought to try it in the Network Manager on the local machine. Worked straight away.

You're possibly aware of this tip: Set the access point/router DHCP to serve IP addresses in a certain range. You need to do this by opening the config of your router (router IP in the address bar of a browser) and configuring the DHCP settings there, for instance serve IPs between 192.168.0.100-110, larger range or smaller for your circumstances.

Now, when you set the static IP on your local machine make sure it is outside of the range the router is serving in an plain sailing. Good luck. ;)

---

### Post by chili555 on 2015-06-30
> Did I miss anything in the configuration process?Yes, indeed! Maybe this will be helpful:[http://askubuntu.com/questions/638771/configuring-wireless-static-ip-through-terminal/638804#638804](http://askubuntu.com/questions/638771/configuring-wireless-static-ip-through-terminal/638804#638804)

> Also, any wireless interface requires the name of the network and the WPA key in order to associate.

Of course, if you follow the Network Manager route, as Bucky suggests, the ESSID and password are handled for you.

---

### Post by francois.teyssere on 2015-06-30
> **Bucky Ball said:**
> Good luck and let us know how you go.

I just set the IP address, netmask and gateway in the IPV4 settings and it worked straight away, thanks a lot :)

> **Bucky Ball said:**
> You're possibly aware of this tip: Set the access point/router DHCP to serve IP addresses in a certain range. You need to do this by opening the config of your router (router IP in the address bar of a browser) and configuring the DHCP settings there, for instance serve IPs between 192.168.0.100-110, larger range or smaller for your circumstances.

Now, when you set the static IP on your local machine make sure it is outside of the range the router is serving in an plain sailing. Good luck. ;)

Yep, but for now I'm fine with a static IP access point and I don't think I'll need that feature later, but thanks anyway



> **chili555 said:**
> Yes, indeed! Maybe this will be helpful:[http://askubuntu.com/questions/638771/configuring-wireless-static-ip-through-terminal/638804#638804](http://askubuntu.com/questions/638771/configuring-wireless-static-ip-through-terminal/638804#638804)

Thank you, looks very helpful, I'll save it just in case :)

---

### Post by Bucky Ball on 2015-06-30
Great news! Please mark thread solved from thread tools. See second link in my signature if you have probs with that. Enjoy! ;)

PS: No, you shouldn't need to set a range on the router, it is more precautionary and depends on your setup.

If your machine is always on and you always have first dibs on your static IP, all good, but ... if your computer is offline, Joe Anyone comes along and joins your network and the router DHCP serves static IP to Joe, then you try and join the network ... well, it ain't gonna work. Your static IP will be trying to claim that from the router, but it's already in use. Something to keep in mind, but really does all depend on your setup.

With my setup, I have six devices with static IP addresses on the network and other people occasionally come around and join the network. More chance of a clash. I have the router set to serve between 192.168.0.100-110 and all the static IPs are set above 110.

---

