---
title: "I can see wireless network but cannot connect"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by dkuhlman on 2008-04-23
I've followed a number of threads here, and have finally gotten to the point where I can see my wireless network.  But ...

Although, in both wicd and wifi-radar, I can see my wireless network, I cannot connect to it.

When I try to connect, in wicd I see this:

```

None: Obtaining IP address...
dlink004: Obtaining IP address...
```
When I use wifi-radar, I see:

```

Connected to None(IP address:None)
```

and wifi-radar prints out the following in the window where I started it:

```

Listening on LPF/eth0/00:1b:38:11:07:70
Sending on   LPF/eth0/00:1b:38:11:07:70
Listening on LPF/wlan0/00:1b:9e:1f:99:4c
Sending on   LPF/wlan0/00:1b:9e:1f:99:4c
Sending on   Socket/fallback
Stale pid file.  Removing
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1b:9e:1f:99:4c
Sending on   LPF/wlan0/00:1b:9e:1f:99:4c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15

```

I'm using WPA Personal security on my wireless router.  But, this problem occurs even when I configure my router as an unsecured wireless network.

I have wpasupplicant installed.

Is there something that I need to configure?  If so what and how?

- Dave

---

### Post by superprash2003 on 2008-04-24
mostly either DHCP is not enabled in your wifi router or you havent set your wlan adapter in ubuntu to accept ips automatically

---

### Post by dkuhlman on 2008-04-24
> **superprash2003 said:**
> mostly either DHCP is not enabled in your wifi router or you havent set your wlan adapter in ubuntu to accept ips automatically

Thanks for help.  That sounds like a good clue. My router is configured for DHCP, I'm pretty sure.  When I use wifi-radar to connect, I see "Acquiring IP address" and then it times out.

So, **how** do I set my wlan adapter in ubuntu to accept the ip address automatically?  I searched the Web and found a page about how to do this in MS Windows, but nothing for Ubuntu Linux.  I read the man page on ifconfig and iwconfig, but could not find anything that seemed relevant.  Perhaps there something about this in your Web page:

    [http://prash-babu.blogspot.com/](http://prash-babu.blogspot.com/)

But, I could not find it.

So, how do I learn how to set my wlan adapter to do this?

- Dave

---

### Post by superprash2003 on 2008-04-24
hey..go to system->administration->Network and select your WLAN card and click on properties.. and there set it to Automatically assign ip(DHCP)

---

### Post by dkuhlman on 2008-04-25
> **superprash2003 said:**
> hey..go to system->administration->Network and select your WLAN card and click on properties.. and there set it to Automatically assign ip(DHCP)

Thanks for the suggestion.  But ...

In System->Administration->Network, my wireless connection is already configured with "Automatic configuration(DHCP)".  And yet it still does not connect.

In the console window where I started wifi-radar, it shows:

```
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
```

Is that a clue?  I'll search for info on DHCPDISCOVER.

I found this at Wikipedia:

[http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol#DHCP_discovery]("http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol#DHCP_discovery")

Needless to say, this is way deeper than I want to go.  And, I don't see any more clues about what to do.

I actually was able to connect, **once**.  But, I had my ether net cable pluged in when I made the connection, then pulled out the cable, and the wireless connection still worked.

I found this message about how to solve a similar problem on Fedora:

[http://http://suseforums.net/lofiversion/index.php/t26987.html]("http://http://suseforums.net/lofiversion/index.php/t26987.html")

but, there is no file /etc/sysconfig/wpa_supplicant on my system.  There is a /etc/wpa_supplicant directory, but it contains two shell scripts.  So, I don't know how to configure wpa_supplicant, other than the suggestion you've given me.

I'll keep searching.  And, I'm going to boot MS Windows again to make sure that my router is functioning.

Thanks again for help.  I apologize for rambling on.  I'm trying to use this thread to document what I've tried.

- Dave

---

### Post by JHumphrey on 2008-04-25
you may have problems similar to mine here: [http://ubuntuforums.org/showthread.php?t=765647](http://ubuntuforums.org/showthread.php?t=765647)

---

### Post by superprash2003 on 2008-04-25
instead of setting it to Automatically assign ip(DHCP) , just enter ip address manually and insert gateway ip as router ip.. now try pinging the router..

---

### Post by kevdog on 2008-04-25
Try taking a look at this thread:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

