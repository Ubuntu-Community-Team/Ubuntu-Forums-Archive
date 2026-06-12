---
title: "setting up ICS from ubuntu into SP2"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by .chaos on 2008-06-18
here's the full situation.  ubuntu laptop > switch > XPSP2 on wifi.

trying to share my xp wifi over the switch to ubuntu.  right now i've determined that my ethernet card is eth0 and eth0 is showing a 169.* address.  i've not setup anything on my XP machine.

tried searching but it seems putting in ICS brings up alot of people trying to use their DSL connection instead of my situation.  can someone walk me through this a bit?  :confused:

---

### Post by superprash2003 on 2008-06-18
you have to setup ICS in xp.. once you do that.. set eth0 to DHCP and it should work!!

---

### Post by .chaos on 2008-06-18
> **superprash2003 said:**
> you have to setup ICS in xp.. once you do that.. set eth0 to DHCP and it should work!!having a problem with the windows machine.  the advanced tab doesn't show anything for internet connection sharing.  just the firewall settings above then blank underneath.  doesn't even have the words and boxes blanked out. :(

---

### Post by .chaos on 2008-06-18
ok, so i think my router is impeding my progress here.  DHCP is setup on it and whenever i try to enable ICS (i got the box working by enabling the internal network card)it tells me automatic IP addressing failed because there's a device taking one of the IP's.  i've since turned off the laptop and my phone which the router addressed an IP for, which i thought was pretty cool, but this whole thing would work better if i knew what IP's windows requires so i can tell the router to not assign them.

---

### Post by .chaos on 2008-06-19
i'm being told by someone else to shut off DHCP at the router and force addies to all NIC's.  is there an easier way to do this?

---

### Post by .chaos on 2008-06-19
lol got it working another way.  modified /etc/network/interfaces.  set gateway to the IP of the xp machine i wanted to be the host.  made sure i was set to dhcp instead of static.  on the windows machine i just bridged the wifi with the internal network NIC.

so the situation is that i have connectivity through my XP machine without ICS.  cat5 > switch > cat5.

i don´t understand why it works but it does.  :confused:

---

### Post by .chaos on 2008-06-19
well i  have it working but it doesn't always work on boot up.  i have to ```
/etc/init.d/network restart
```  at least i did last time.  i've only booted it once since the changes.

---

### Post by .chaos on 2008-06-23
and it's not working again.  /etc/init.d/networking restart provides RTNETLINK answers: no such process.

after it says DHCPRELEASE to (Router IP) it says "There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072.

after that it tries DHCPDISCOVER on 255.255.255.255 (subnet is actually 255.0) port 67 and failes then sleeps.  "No working leases in persistent database - sleeping. and drops me at the prompt.

i tried using the graphic network manager to no avail.  seems to edit the same /etc/network/interfaces file that i was editing manually anyway.

/etc/network/interfaces has the same exact info as my windows machine except the gateway address is the windows machine's address.  i'm sharing the windows connection through a bridge.

i'm trying to set it up following this.  

[http://www.nukesilo.com/2007/03/19/configuring-dhcp-addressing-for-ubuntu-linux/](http://www.nukesilo.com/2007/03/19/configuring-dhcp-addressing-for-ubuntu-linux/)

address = machine desired IP
netmask = subnet (255.255.255.0)
network = router IP (192.168.0.100)
broadcast = 192.168.0.255
gateway = XP machine 192.168.0.50
dns-nameservers = XP machine which is set to pull from the router which has DNS relay on.  

it worked for like two days then saturday it went down and has stayed that way.  seems to intermittently come and go until this where it finally died.  never had an issue with it in windows even though it ran the same install for 5 years.

---

