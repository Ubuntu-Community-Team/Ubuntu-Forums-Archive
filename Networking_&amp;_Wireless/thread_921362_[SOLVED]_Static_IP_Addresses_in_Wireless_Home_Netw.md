---
title: "[SOLVED] Static IP Addresses in Wireless Home Network"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by Jacobian on 2008-09-16
Hey there,

I have a wireless gateway router and a Ubuntu laptop. I'd like to have a static IP address for the Ubuntu laptop.

My Ubuntu laptop can access the Internet using DHCP. However, when I edit the "/etc/network/interfaces" file to set up a static IP address, I'm no longer able to connect.

Here is my /etc/network/interfaces file:
```
auto lo
iface lo inet loopback

auto wlan1
iface wlan1 inet static
        netmask 255.255.255.0
        gateway 192.168.0.1
        address 192.168.0.44
#       network 192.168.0.0
#       broadcast 192.168.0.255

```

The "wlan1" interface is my wireless network card, which I've been successfully using to access the Internet using the automatic DHCP.

The router has the local IP address 192.168.0.1, and the network mask has been set to 255.255.255.0, using the router's web interface.

This is for our home wireless network, and we only have three computers connected. The highest IP address that I've seen automatically assigned through DHCP was 192.168.0.9. Using the router's web interface, I double-checked that 192.168.0.44 was available while I tried to set up the static IP address.

I can set temporary static IP addresses using ifconfig, but so far I haven't been able to make this permanent in my /etc/network/interfaces file.

I've tried many variations of the interfaces file. I've also tried variations while turning off DHCP on the laptop using /etc/init.d/dhcdbd stop. Nothing has worked so far...

Is there anything else I should read about? Is there anything that you would double-check?

---

### Post by desktopj on 2008-09-16
You also need the following addresses that are usually provided via dhcp in order to access outside your local network.

Default Gateway - Your firewall/router ip
DNS - Your ISP's dns servers ips

Jeff

---

### Post by caljohnsmith on 2008-09-16
Try adding a line for your Wireless network name:
```
iface wlan0 inet static
address 192.168.1.23
netmask 255.255.255.0
gateway 192.168.1.1
[COLOR="Blue"]wireless-essid My Home WLAN[/COLOR]
```
Let me know if that helps.

---

### Post by Jacobian on 2008-09-16
Thank you very, very much for your suggestions.

Here's what I've done:

I checked the DNS name servers listed in "/etc/resolv.conf": The two name servers listed there are the same as the two name servers configured in the router. This matches what we were given by our Internet Service Provider. The "resolv.conf" file is being automatically created for me whenever I use DHCP, thanks to NetworkManager.

I expanded the "/etc/network/interfaces" file to include the name of the wireless network:
```
auto lo
iface lo inet loopback

auto wlan1
iface wlan1 inet static
        netmask 255.255.255.0
        network 192.168.0.0
        gateway 192.168.0.1
        address 192.168.0.44
        broadcast 192.168.0.255
        wireless_essid ACTIONTEC
        wireless_channel 1
```

But I'm still not able to connect...

I should say that I've turned off all wireless security on the router to make it easier to debug this.

Is there any chance that my router could be working with DHCP, but not be set up correctly for static IP addresses? There is a section in the web interface for static routing, which I've left blank. Here's the full story on how my router is set up. My router says:

> * The wireless network ESSID is ACTIONTEC, on channel 1, with no security encryption.

* DHCP is enabled.

* The netmask is 255.255.255.0. The router address is 192.168.0.1. The beginning IP address 192.168.0.2 and the ending IP address is 192.168.0.254. (This is the default configuration: I'm interpreting this as the range of valid IP addresses that can be given out.)

* The firewall security level is set to "Basic." No services are blocked on an individual IP address basis. There are no blocked websites. The router is accepting all client MAC addresses.

* No ports are being forwarded.

* DNS is set to "Dynamic" (as opposed to "Static"). There are two working DNS servers listed, which match the nameservers in my "/etc/resolv.conf" file.

* There is an option for static routes. Here is the static routing table:
Destination: 192.168.0.0, Gateway: 0.0.0.0, Netmask: 255.255.255.0
Destination: 0.0.0.0, Gateway: 67.41.xxx.xxx, Netmask: 0.0.0.0

Both routes are both marked as valid routes. I've left this section unchanged. I'm not sure how to configure this. I'm assuming it's not necessary to change this if I'm using DHCP?

* Dynamic Routing (RIP) is set to "Off" (as opposed to "Version 1" and "Version 2"). NAT is "On"

* The router is getting its IP address through PPPoA using RFC1483 bridged encapsulation. There is an option for an "unnumbered mode" which isn't set.

Have I done anything silly? :)

---

### Post by caljohnsmith on 2008-09-16
> **Jacobian said:**
> 
```
auto lo
iface lo inet loopback

auto wlan1
iface wlan1 inet static
        netmask 255.255.255.0
        network 192.168.0.0
        gateway 192.168.0.1
        address 192.168.0.44
        broadcast 192.168.0.255
        [COLOR="Blue"]wireless_essid[/COLOR] ACTIONTEC
        wireless_channel 1
```

I believe it should be "wireless-essid" with a dash, not an underscore. Also, you shouldn't need the line for the wireless channel; when you connect to your WLAN, that will automatically be configured. I don't think you need the "network" line either, but I could be wrong. And just out of curiosity, have you tried simply setting up a static IP in System > Admin > Network? That will configure your /etc/network/interfaces file for you and you won't have to worry about the exact syntax to use. Let me know how it goes. :)

---

### Post by Jacobian on 2008-09-16
Mmm, you're right about the dash! It looks like you've already solved part of the problem.

I've been experimenting with the Network Settings dialog. It looks like you can bring it up through the nm-applet on your toolbar as well.

I found my device (wlan1) in the dialog and tried it out:

When I enable "roaming mode," it reverts my "/etc/network/interfaces" file back to the default DHCP settings:
```
auto lo
iface lo inet loopback
```

It's nice to know that I can always revert back and at least have Internet access.

When I manually configure my device for a static IP address, using the drop-down menus in the Network Settings dialog, I get an "/etc/network/interfaces" file like this:
```
auto lo
iface lo inet loopback

iface wlan1 inet static
        address 192.168.0.55
        netmask 255.255.255.0
        gateway 192.168.0.1
        wireless-essid ACTIONTEC

auto wlan1
```

However, it still doesn't connect to the Internet!

I wonder if this means the router needs to be changed in some way? In any case, I'm going to use this generated "interfaces" file from now for testing purposes.

---

### Post by caljohnsmith on 2008-09-16
I just noticed your wireless interface is wlan1, not wlan0; do you have two wireless interfaces? 

Also, using that interface file that Network Manager generated, please post the output of the following:
```
route -n
ifconfig
iwconfig
ping -c3 192.168.0.1
ping -c3 74.125.19.99
```

---

### Post by alanmilne on 2008-09-16
I think you may find that the answer to this problem lies in the fact that your router has the DHCP pool set for 192.168.0.2 - 192.168.0.254 (*all* of network 192.168.0.0). Any device that uses an address within this range (e.g. 192.168.0.44) may not be recognised by the router as it feels that these addresses are for it to hand out and control.

Try reconfiguring your router so that the DHCP address pool contains only a few addresses, leaving others for static IP configuration and then choose a static IP address outside of the DHCP pool range.

---

### Post by caljohnsmith on 2008-09-16
> **alanmilne said:**
> I think you may find that the answer to this problem lies in the fact that your router has the DHCP pool set for 192.168.0.2 - 192.168.0.254. Any device that uses an address within this range (e.g. 192.168.0.44) may not be recognised by the router as it feels that these addresses are for it to hand out and control.

Try reconfiguring your router so that the DCHP address pool only contains a few addresses, leaving others for static IP configuration and then choose a static IP address outside of this range.
Interesting thought, but have you by chance tested that with your own router or someone elses? I'm just wondering because at least for the router I'm currently using (and the few ones I've used before), I can connect with a static address that is inside the configured range of DHCP addresses as long as nobody is currently using that IP.

---

### Post by alanmilne on 2008-09-16
I have to admit that it is some time since I was professionally employed in the Internetworking field, however I can say that my own home router exhibits this behaviour (I know, technically it should not but we live in a world of cheaper devices with non-standard functionality). It's just a suggestion :-).

---

### Post by caljohnsmith on 2008-09-16
> **alanmilne said:**
> I have to admit that it is some time since I was professionally employed in the Internetworking field, however I can say that my own home router exhibits this behaviour (I know, technically it should not but we live in a world of cheaper devices with non-standard functionality). It's just a suggestion :-).
Thanks for sharing that, that's definitely useful info then since I've not yet encountered that behavior with just the few routers I've used; but as you pointed out, with the huge variety of routers on the market, I'm not surprised it can happen. :)

---

### Post by Jacobian on 2008-09-16
Well, you guys did it: You fixed me. I'm posting this message from a static IP address!

Thank you very much :)

But there's a story to tell, so I'll tell you how it happened:

In response to your posts, I tried everything that was suggested: I reduced my DHCP IP pool, so that the DHCP is only permitted to give out IP addresses from 192.168.0.8 to 192.168.0.254.

Then I ran the network diagnostic commands: for static IP addresses both inside and outside the DHCP pool, then again with and without the DHCP pool restricted. And nothing worked. Not even the gateway ping test.

Then, suddenly, I got a phone call.

And when I came back in again, the static IP address was connected. The network applet was still showing no available networks, but somehow Firefox had loaded its webpage, the buddy list was up... it was like stepping out for a moment and returning to the Twilight Zone.

I ran ifconfig, and sure enough, my static IP address was listed. I could connect to the router now: there was my static IP address in the list of active users!

That's not the way this usually works, is it? You just step away for a moment and everything works?

Well, I wasn't expecting that. *Of course* I ran upstairs to tell the rest of the family what had just happened, and everybody was very happy...

And then I came downstairs again, and nothing worked anymore. Heh.

But it turns out that by restarting the networking services, you could recreate the Twilight Zone scenario...

It's very subtle: I missed it before, because the network applet wasn't listing any available networks. However, after restarting the network services, after a delay, there WAS a connection.

When I got called away to the phone, the router was apparently just about to complete the static connection. While I was away, the router accepted and the Internet services completed, and I returned to a working system.

However, our router is a bit unreliable. I had noticed that during my testing, the router would occasionally drop connections and I would sometimes have to restart the router.

I tried to compensate for this by repeating the tests until I was sure of the results.

Well, by the time I got back downstairs, it must have dropped the connection. Running '/etc/init.d/networking restart' must have repeated the request for a static IP address, which the router fulfilled. Thus recreating the Twilight Zone scenario.

The network applet really doesn't list any wireless networks, but perhaps that's by design? I'm not in roaming mode, after all: I'm using a specific configuration. I did notice that even though no wireless networks are offered, there is no red X over the connection icon, which would ordinarily mean that all devices are disconnected. So perhaps even this is not as mysterious as it seemed.

It looks like I can reliably reconnect to the wireless network simply by running the '/etc/init.d/networking restart' command.

So I believe I am fixed.

I was using alanmilne's suggestion when everything started working, so I'm not sure whether it's actually required or not. But I'm not very inclined to change it now that everything is working. Besides, it's nice to know that we have a safe block of static IP addresses that are guaranteed to be free for static connections.

However, it was only by running caljohnsmith's diagnostics that I noticed the static network was working. The applet itself was not enough for me to realize that anything was different.

So thank you everyone! I'll give you all a formal thanks via the forum mechanism if it will let me.

---

### Post by caljohnsmith on 2008-09-17
Well as long as things are working, Jacobian, that's what counts, even though what you describe does seem a bit strange. By the way, is by chance your router a Linksys WRT54G? I'm only asking because I have one and had problems with the connection being flaky, but I found out that it is actually a bug in their firmware that can be circumvented with a few simple steps. Anyway, if you have a WRT54G, let me know, and I might be able to help you with your sporadic internet connection. 

To mark the thread as solved, simply go to the top of the thread, click "thread tools", and then click "marked as solved". :)

---

### Post by Jacobian on 2008-09-17
We have an ActionTec gateway router. It has been very flaky for everyone. I'll check to see if there are any updates for the firmware.

Thanks again for all your ideas and for following this thread. I'll mark this as solved.

---

