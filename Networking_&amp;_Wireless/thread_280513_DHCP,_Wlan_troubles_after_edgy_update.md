---
title: "DHCP, Wlan troubles after edgy update"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by hannesw on 2006-10-19
When I upgraded to Edgy Beta from Dapper a week or so ago, two things happened: DHCP stopped working over Wlan (I haven't had any opportunity to test over ethernet), and the available Wlan networks are no longer listed in the Gnome network admin applet. 

I was able to solve the DHCP issue by myself. The syslog contained the following message each time I configured the interface with DHCP:

 dhclient: Can't allocate interface ethlease { 

So I figured out the problem might be old dhcp lease files, and indeed, there were old lease files lying around in /var/lib/dhcp3. After I removed these, DHCP started working again. I guess this is a bug in the dhcp code and/or upgrade script.

The other issue, wireless networks not being displayed, I haven't been able to figure out yet. The computer in question is a Samsung X20 laptop, the module used is ipw2200. Any hints or ideas where to look?

---

### Post by larytet on 2006-11-07
problem with DHCP in my case
fresh install of Edgy
everything works just fine with static IP
DHCP fails. I see IP address and DNS server, but there is no Internet. Ping to the gateway works
Removed lease files - still no luck
I did not invest time - just set static IP

---

### Post by trubblemaker on 2006-11-15
my bet is that your having issues with ipv6, the quick way to check is to
see if you can ping google.

if you can then you can add
"blacklist ipv6" to /etc/modprobe.d/blacklist
and reboot if you can now surf 

if that works you can :
       do nothing and continue to surf

look up howto turn off ipv6 in firefox and re-enable ipv6 by removing it from the blacklist... (it's firefox that not working properly with misconfigured ipv6)

---

