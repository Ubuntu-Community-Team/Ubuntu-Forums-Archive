---
title: "Rejecting IP address given from DHCP server"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by mchaggis on 2008-03-14
Hi,

This may seem a strange question, but I am trying to find out a way (and if indeed it is possible) to reject the IP address a dhcp allocates you and force it to allocate a different one.

Background:

As part of my job I work from many client offices, however, at one of these offices I have noticed that if I end up being allocated the IP address 10.128.6.23 then I have network traffic for any where from 2minutes to 20mins. I am fairly certain that their DHCP is misconfigured, or that there is a machine on their network that has been given this IP address as a static. However, any attempts to point this out or get them to investigate this issue falls on deaf ears. I can set a static IP address but I know that this could cause conflicts with their DHCP as I do not know the IP range that the DHCP server controls.


So, the ideal would be to configure my dhcp client to detect when the problematic IP is allocated and force a renew to get a different IP address.

Is this possible and if so any ideas of how I configure the dhclient or go about writing a script/hook to get round this?

Cheers

---

### Post by wblancqu on 2008-03-14
If you know the subnetmask and a given DHCP IP, you can calculate which range of IP addresses is given by the router. Knowing that, you could indeed switching to a static ip, by first pinging to your chosen IP to  make sure it isn't in use by another client.

Just brainstorming out loud...

---

### Post by handydan918 on 2008-03-14
> **wblancqu said:**
> If you know the subnetmask and a given DHCP IP, you can calculate which range of IP addresses is given by the router. Knowing that, you could indeed switching to a static ip, by first pinging to your chosen IP to  make sure it isn't in use by another client.

Just brainstorming out loud...

2 nice tools for this kind of work...
nmap and ipcalc. 
Both are in the repos, I believe.

---

### Post by mozetti on 2008-03-14
I participated in a discussion about requesting a specific IP from a DHCP server. It involves replacing Ubuntu's standard DHCP client and installing a new one, but this should allow you to specify an IP addy, but still work with the DHCP server.

Here's the thread: [http://ubuntuforums.org/showthread.php?t=686954](http://ubuntuforums.org/showthread.php?t=686954)

---

### Post by mchaggis on 2008-03-14
Yeah, 10.128.6.23 turns out it is their printer. The ip range is not really the issue. DHCP issue IP's from a given pool. The trick when assigning static IP's is to pick an address out side of this range. This is something that the Sys Admins at this place have forgotten when assigning the printer the IP address.

However, assigning an IP address within the allowed network IP range is not a sure fire hit, as if the DHCP server is configured to allocate IP's from that entire range then the fact that I have set a static still runs the risk of the DHCP server eventually giving that IP address to someone else.

Cheers for your efforts. 

Like I said, if they would configure their network properly, then it would not be an issue:mad:

---

### Post by mchaggis on 2008-03-14
> **mozetti said:**
> I participated in a discussion about requesting a specific IP from a DHCP server. It involves replacing Ubuntu's standard DHCP client and installing a new one, but this should allow you to specify an IP addy, but still work with the DHCP server.

Here's the thread: [http://ubuntuforums.org/showthread.php?t=686954](http://ubuntuforums.org/showthread.php?t=686954)


The aim is not to specify an IP address, as what if I request a specific IP address that has already been allocated? 

Like I said, when the DCHP server offers me an IP address, I'd like a way that I can reject the IP address and ask the DHCP server to give me a different one from it's pool?

---

### Post by Iowan on 2008-03-14
Check the settings/options in **/etc/dhcp3/dhclient.conf** and the associated **man** pages.  There *seem* to be options for the client to request (reject?) ip addresses.

---

### Post by mozetti on 2008-03-15
> **mchaggis said:**
> The aim is not to specify an IP address, as what if I request a specific IP address that has already been allocated? 

Like I said, when the DCHP server offers me an IP address, I'd like a way that I can reject the IP address and ask the DHCP server to give me a different one from it's pool?

Sure, I understood that. I was thinking that if you knew an IP in the range to request then you could do that and DHCP on the server would keep tabs and not give that one out to someone else. I didn't provide the solution to your question, but I thought it might be an alternative solution that would work.

---

### Post by koenn on 2008-03-15
mozetti: that's not a bad idea

there doesn' seem to be a way to actually refuse a certain address during the dhcp session. 
You can request a new address by running
```

dhclient -r
ifconfig eth0 down
dhclient

```
but chances are you get the same address assigned again (and again, ...)

if you can demonstrate that you get the ip address of a printer (and possibly mess up printer jobs all over the network), maybe you can ask for a dhcp reservation from the network admins.They should fix their dhcp server, really, but a reservation would help untill they get round to do that.

---

