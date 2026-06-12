---
title: "Wireless Ethernet Bridge"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by scaffee on 2008-12-01
Hi,

I'm a newbie to Ubuntu and Linux in general.

I just downloaded Ubuntu 8.10 to a laptop and am trying to use the laptop as a wireless ethernet bridge. I want to bridge my wireless network to a non-wireless computer running WinXP.

I've been able to get wireless working on my Ubuntu laptop. I've also been able to hard wire my Ubuntu laptop to my AP and that works also.

So here's a diagram of what I'm trying to do:

WinXP box (static 192.168.1.17) <-ethernet cable-> Ubuntu laptop (192.168.1.2) <-wireless-> AP (192.168.1.1)

On my Ubuntu laptop:

eth0 is the Ethernet device
eth1 is the wireless device

I've been reading posts on the forum and have tried the following (after installing bridge application):

On Ubuntu laptop:

# ifconfig eth0 0.0.0.0
# ifconfig eth1 0.0.0.0
# brctl addbr br0
# brctl addif br0 eth0
# brctl addif br0 eth1
# dhclient br0


After performing the above commands, my wireless connection on the Ubuntu laptop works fine. I can get to the Internet through my AP. I can also PING my WinXP box. My WinXP box can PING my laptop.

However, my WinXP box cannot PING the AP. Nor can the WinXP box get to the Internet.

It seems like the Ubuntu laptop is not forwarding packets from the WinXP box on to the AP.

I feel like I'm close to getting this networking problem solved.

What else do I need to do to get this to work right?

Do I need to somehow turn on packet forwarding or establish a route or something?

Have I defined a bad static IP address for my WinXP box?

Any help is greatly appreciated! Thanks a lot!

Sean


P.S. BTW, I used WinXP on the same laptop and bridged the Wireless and LAN connections and this worked great. The non-wireless WinXP box could get to the Internet just fine. So I know the underlying hardware works and can be bridged.

---

### Post by ryry46d9 on 2008-12-02
I'm working on this tonight as well, if you figure it out let me know 

as I will do the same 


my setup is cable modem in the house, wireless router and one XP MCE box 

out in the guest area I got Ubuntu8.04.1 routing to a switch  and then 3 boxes behind that. one XP MCE (another one) a Ubuntu 8.10  a OpenBSD box and a X-box 360 set up as a media extender to stream movies and music off the XP box in this room 

my goal is to have the OpenBSD box after the modem then wireless router (not routing) and bridge Ubuntu so any computer back here is on the same network 

I'm working with 192.168.1.* in the house and 192.168.0.* out here and all wireless traffic goes to 192.168.1.* for some reason the wireless router is not joining the two and I have to do a route add on new systems that join my network

---

### Post by superprash2003 on 2008-12-02
install firestarter in the laptop and enable internet connection sharing . or use this [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) . first try firestarter though

---

### Post by ryry46d9 on 2008-12-03
I couldn't find a good write up , So i took to wireless routers and installed DD-WRT on both of them 


but yes if you just was to give a your windows box internet then firestarter works great  thats what I was using but now I got evert thing on the same network ;)

---

### Post by Snappo on 2008-12-07
I've been looking to do the same, trying out firestarter now. :popcorn:

---

### Post by scaffee on 2008-12-09
Thanks for the help, superprash2003!

I finally got a chance to try out your suggestions.

I downloaded and installed Firestarter first and tried that, both with and without establishing the bridge between my wireless interface (eth1) and my LAN (eth0). For some reason, Firestarter did not want to start when I had the bridge in place. But without the bridge, I could start it.

Nonetheless, neither option helped get Internet to my WinXP machine with Firestarter.

I then tried your second suggestion of the IP masquerade. After playing around with things, I finally got that to work correctly after establishing a bridge.

So the formula that I got to work was:

1. Establish a bridge between wireless interface and wired interface by following this:

# ifconfig eth0 0.0.0.0
# ifconfig eth1 0.0.0.0
# brctl addbr br0
# brctl addif br0 eth0
# brctl addif br0 eth1
# dhclient br0

2. Then perform the IP masquerading step as outlined at:

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) 

3. Set the IP address of your WinXP machine to be something on the same subnet as my Ubuntu laptop (I used 192.168.1.17). Set the Default gateway and Default DNS address on my WinXP machine to be the Ubuntu laptop address (not the AP).

I the only thing that I found that was strange was that I needed to download and install Firestarter before I could download dnsmasq and ipmasq as outlined in the IP masquerading link. I never actually used Firestarter for this procedure, but it seemed required to resolve dependencies for dnsmasq and ipmasq - weird.

Thanks again for the help!

---

