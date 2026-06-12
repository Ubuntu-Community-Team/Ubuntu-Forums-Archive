---
title: "Firefox and Evolution drop outs with 6.10"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by newaustralian on 2007-03-27
Both Firefox and Evolution will drop out if no activity for about 2 minutes.  I connect via an ADSL modem.  However, after Firefox etc drops out I can still ping a server via the terminal which shows the connection is still good.  I spoke to my ISP about the problem and their monitoring of my line still shows a connection even when Firefox shows a disconnection. This is consistent with my pinging at least.

Can anybody throw some light on this please.

It is inconvenient to go back to the network settings  to reconnect.

---

### Post by Floppyjoe on 2007-03-28
> **newaustralian said:**
> Both Firefox and Evolution will drop out if no activity for about 2 minutes.  I connect via an ADSL modem.  However, after Firefox etc drops out I can still ping a server via the terminal which shows the connection is still good.  I spoke to my ISP about the problem and their monitoring of my line still shows a connection even when Firefox shows a disconnection. This is consistent with my pinging at least.

Can anybody throw some light on this please.

It is inconvenient to go back to the network settings  to reconnect.
Do you also use a router?
Sometimes if I have my router set to Connect on demand with a maximum Idle time set then my router will renew its DHCP leases as well as reconnect with the modem after a period of inactivity above the maximum idle time. If your DNS is not configured properly then these DHCP renewals will overwrite your resolv.conf file and you won't be able to resolve Domain names properly. This would cause the type of behaviour you are describing with your programs.

---

### Post by newaustralian on 2007-03-28
Do not use a router and the Ubuntu configuration is standard.

---

### Post by Mr. C. on 2007-03-28
What do you mean "drop out" ? 

Web connections are stateless - they come and go.  So by definition, you are either seeing elements load, or you're not.

Not knowing how you have Evolution setup, its hard to understand the context here as well.

Drop out doesn't make sense in this context, so if you can be more specific, that might help.

MrC

---

### Post by newaustralian on 2007-03-28
By drop out I mean following:  In Evolution it comes up with  "error fetching mail"
in Firefox " Unable to connect ....... Try again"

Time limit seems random although averages about 2 minutes. For example it happened while I was typing this post and I am not that slow a typist.  Once I go back to network settings and apply my saved configuration everything continues as if nothing had happened

---

### Post by Mr. C. on 2007-03-28
Ok, this makes more sense.  Try to provide exact error messages; they are more useful than interpretation.

Two possible solutions for you to try, in order until the problem is resolved:

1) If your /etc/resolv.conf file contains the IP address of your router in the **nameserver **line, replace it with your ISPs nameservers.  You can have from 1 to 3 nameserver lines, as in
```
nameserver *ip1*
nameserver *ip2*
nameserver *ip3*
```

2) Disable IPv6: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

MrC

---

### Post by newaustralian on 2007-03-28
Thanks Mr C 

I already had my ISP servers listed so method 1 was not applicable.

Went to second method and followed instructions to disable ipv6 for Firefox and it solved  the problem for Firefox but I still had the error "error fetching mail" with Evolution so felt that I was on the right track.

Next I followed the instructions to disable ipv6 for ubuntu however when I checked the disablement by typing  ip a | grep inet6 I got the following reponse:

    inet6 ::1/128 scope host 
    inet6 fe80::2e0:4cff:fee9:dbe4/64 scope link 

which suggests ipv6 is not disabled. Firefox is still OK but Evolution still has the problem.  

NowI need advice on the meaning of the above response and possible next steps

---

### Post by Mr. C. on 2007-03-28
It means you did not disable IPv6.  Re-read and perform the steps given on the page.

MrC

---

### Post by newaustralian on 2007-03-29
Further to Mr C post

I repeated the first set of instructions for disabling ipv6 with the same result.

Next I blacklisted ipv6 and this time it worked ie no response to "... grep inet6"

Firefox is working fine but I still have the same problem with Evolution ie error message
"error while fetching mail : no route to server"

Evolution works fine once I reapply the network settings.

Seems there maybe two issues here?

---

### Post by Mr. C. on 2007-03-29
> **newaustralian said:**
> Further to Mr C post

I repeated the first set of instructions for disabling ipv6 with the same result.

Next I blacklisted ipv6 and this time it worked ie no response to "... grep inet6"
[

Perfect.
> **newaustralian said:**
> 
Firefox is working fine but I still have the same problem with Evolution ie error message
"error while fetching mail : no route to server"

Evolution works fine once I reapply the network settings.

Seems there maybe two issues here?

Yes, it seems.  This is the first mention of the "no route to server" error.

What is the POP server setting you have setup in Evolution?  After you've found it, show output of 

```
netstat -nl
nslookup *popserver*
```

replacing *popserver* with the name configured in Evolution.

MrC

---

### Post by Chappy7777 on 2007-03-29
I get the same error message when trying to send an email, "error while fetching mail : no route to server".  I believe that my problem is caused by the fact that my email address is different than the ISP I am using to connect to the net. I have been using a Web based email service that my other ISP provides for a couple years so I don't want to change ISPs/email addresses. Oh. My connection to net is via an external serial dialup modem, since hispeed is not available in deep woods Ontario. Cell Phones don't work either. Twilight zone. :( 

I am not sure if this is your situation or not. If so, you'll likely find the way around it before I do, since I don't need Evolution. I just thought it would be nice to set it up and try it. Which I did, but no joy. 

Good luck, maybe this will help,
Chappy

---

### Post by newaustralian on 2007-03-29
Thanks again for your help Mr C.

Name of POP server is "mail.aapt.net.au" for receiving mail.

Copy of terminal output follows:

mehirst@mehirst-desktop:~$ netstat -n
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ]         DGRAM                    4127     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    4296     @/org/kernel/udev/udevd
unix  3      [ ]         DGRAM                    12430    /dev/log
unix  2      [ ]         DGRAM                    9086     @/org/freedesktop/hal/udev_event
unix  3      [ ]         STREAM     CONNECTED     13098    
unix  3      [ ]         STREAM     CONNECTED     13097    
unix  3      [ ]         STREAM     CONNECTED     13095    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     13094    
unix  3      [ ]         STREAM     CONNECTED     13092    /tmp/orbit-mehirst/linc-1617-0-75af45cd18e5
unix  3      [ ]         STREAM     CONNECTED     13091    
unix  3      [ ]         STREAM     CONNECTED     13090    /tmp/orbit-mehirst/linc-1244-0-1cfde12d50f92
unix  3      [ ]         STREAM     CONNECTED     13089    
unix  3      [ ]         STREAM     CONNECTED     13088    /tmp/orbit-mehirst/linc-1617-0-75af45cd18e5
unix  3      [ ]         STREAM     CONNECTED     13087    
unix  3      [ ]         STREAM     CONNECTED     13084    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     13083    
unix  3      [ ]         STREAM     CONNECTED     13081    /tmp/.ICE-unix/4599
unix  3      [ ]         STREAM     CONNECTED     13080    
unix  3      [ ]         STREAM     CONNECTED     13076    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13075    
unix  2      [ ]         DGRAM                    12983    
unix  3      [ ]         STREAM     CONNECTED     12471    /tmp/orbit-mehirst/linc-1431-0-50aae896c4f6b
unix  3      [ ]         STREAM     CONNECTED     12470    
unix  3      [ ]         STREAM     CONNECTED     12467    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     12466    
unix  3      [ ]         STREAM     CONNECTED     12454    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12453    
unix  3      [ ]         STREAM     CONNECTED     12223    /var/run/cups/cups.sock
unix  3      [ ]         STREAM     CONNECTED     12222    
unix  3      [ ]         STREAM     CONNECTED     11970    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11969    
unix  3      [ ]         STREAM     CONNECTED     11968    @/tmp/dbus-zO3s4neq15
unix  3      [ ]         STREAM     CONNECTED     11967    
unix  3      [ ]         STREAM     CONNECTED     11966    /tmp/orbit-mehirst/linc-12b4-0-3fe93e6faee9b
unix  3      [ ]         STREAM     CONNECTED     11965    
unix  3      [ ]         STREAM     CONNECTED     11962    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     11961    
unix  3      [ ]         STREAM     CONNECTED     11957    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11956    
unix  3      [ ]         STREAM     CONNECTED     11946    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11945    
unix  3      [ ]         STREAM     CONNECTED     11943    /tmp/orbit-mehirst/linc-123e-0-3cd567c9746a
unix  3      [ ]         STREAM     CONNECTED     11942    
unix  3      [ ]         STREAM     CONNECTED     11941    /tmp/orbit-mehirst/linc-12aa-0-78c02bdc8d9bc
unix  3      [ ]         STREAM     CONNECTED     11940    
unix  3      [ ]         STREAM     CONNECTED     11933    /tmp/orbit-mehirst/linc-12aa-0-78c02bdc8d9bc
unix  3      [ ]         STREAM     CONNECTED     11932    
unix  3      [ ]         STREAM     CONNECTED     11931    /tmp/orbit-mehirst/linc-1244-0-1cfde12d50f92
unix  3      [ ]         STREAM     CONNECTED     11930    
unix  3      [ ]         STREAM     CONNECTED     11929    /tmp/orbit-mehirst/linc-12aa-0-78c02bdc8d9bc
unix  3      [ ]         STREAM     CONNECTED     11928    
unix  3      [ ]         STREAM     CONNECTED     11925    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     11924    
unix  3      [ ]         STREAM     CONNECTED     11920    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11919    
unix  3      [ ]         STREAM     CONNECTED     11913    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11912    
unix  3      [ ]         STREAM     CONNECTED     11872    /tmp/orbit-mehirst/linc-1255-0-2d481f0cb8bde
unix  3      [ ]         STREAM     CONNECTED     11871    
unix  3      [ ]         STREAM     CONNECTED     11870    /tmp/orbit-mehirst/linc-1280-0-410fdc4dc1a1
unix  3      [ ]         STREAM     CONNECTED     11869    
unix  3      [ ]         STREAM     CONNECTED     11837    /tmp/orbit-mehirst/linc-1280-0-410fdc4dc1a1
unix  3      [ ]         STREAM     CONNECTED     11836    
unix  3      [ ]         STREAM     CONNECTED     11835    /tmp/orbit-mehirst/linc-1244-0-1cfde12d50f92
unix  3      [ ]         STREAM     CONNECTED     11834    
unix  3      [ ]         STREAM     CONNECTED     11828    /tmp/mapping-mehirst
unix  3      [ ]         STREAM     CONNECTED     11823    /tmp/orbit-mehirst/linc-1280-0-410fdc4dc1a1
unix  3      [ ]         STREAM     CONNECTED     11822    
unix  3      [ ]         STREAM     CONNECTED     11819    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     11818    
unix  3      [ ]         STREAM     CONNECTED     11807    
unix  3      [ ]         STREAM     CONNECTED     11802    /tmp/orbit-mehirst/linc-1255-0-2d481f0cb8bde
unix  3      [ ]         STREAM     CONNECTED     11801    
unix  3      [ ]         STREAM     CONNECTED     11800    /tmp/orbit-mehirst/linc-1244-0-1cfde12d50f92
unix  3      [ ]         STREAM     CONNECTED     11799    
unix  3      [ ]         STREAM     CONNECTED     11798    @/tmp/dbus-zO3s4neq15
unix  3      [ ]         STREAM     CONNECTED     11797    
unix  3      [ ]         STREAM     CONNECTED     11794    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11793    
unix  3      [ ]         STREAM     CONNECTED     11792    /tmp/orbit-mehirst/linc-123e-0-3cd567c9746a
unix  3      [ ]         STREAM     CONNECTED     11791    
unix  3      [ ]         STREAM     CONNECTED     11790    /tmp/orbit-mehirst/linc-126f-0-5f3dbf373c887
unix  3      [ ]         STREAM     CONNECTED     11789    
unix  3      [ ]         STREAM     CONNECTED     11782    @/tmp/dbus-zO3s4neq15
unix  3      [ ]         STREAM     CONNECTED     11781    
unix  3      [ ]         STREAM     CONNECTED     11780    /tmp/orbit-mehirst/linc-126f-0-5f3dbf373c887
unix  3      [ ]         STREAM     CONNECTED     11779    
unix  3      [ ]         STREAM     CONNECTED     11778    /tmp/orbit-mehirst/linc-1244-0-1cfde12d50f92
unix  3      [ ]         STREAM     CONNECTED     11777    
unix  3      [ ]         STREAM     CONNECTED     11776    /tmp/orbit-mehirst/linc-126f-0-5f3dbf373c887
unix  3      [ ]         STREAM     CONNECTED     11775    
unix  3      [ ]         STREAM     CONNECTED     11772    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     11771    
unix  3      [ ]         STREAM     CONNECTED     11767    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11766    
unix  3      [ ]         STREAM     CONNECTED     11754    /tmp/orbit-mehirst/linc-1255-0-2d481f0cb8bde
unix  3      [ ]         STREAM     CONNECTED     11753    
unix  3      [ ]         STREAM     CONNECTED     11746    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     11745    
unix  3      [ ]         STREAM     CONNECTED     11743    /tmp/.ICE-unix/4599
unix  3      [ ]         STREAM     CONNECTED     11742    
unix  3      [ ]         STREAM     CONNECTED     11741    @/tmp/dbus-zO3s4neq15
unix  3      [ ]         STREAM     CONNECTED     11740    
unix  3      [ ]         STREAM     CONNECTED     11736    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11735    
unix  3      [ ]         STREAM     CONNECTED     11728    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11727    
unix  3      [ ]         STREAM     CONNECTED     11725    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11724    
unix  3      [ ]         STREAM     CONNECTED     11716    /tmp/orbit-mehirst/linc-1240-0-3cd567caadb0
unix  3      [ ]         STREAM     CONNECTED     11715    
unix  3      [ ]         STREAM     CONNECTED     11714    /tmp/orbit-mehirst/linc-123e-0-3cd567c9746a
unix  3      [ ]         STREAM     CONNECTED     11713    
unix  3      [ ]         STREAM     CONNECTED     11712    /tmp/orbit-mehirst/linc-125a-0-497a706894556
unix  3      [ ]         STREAM     CONNECTED     11711    
unix  3      [ ]         STREAM     CONNECTED     11710    /tmp/orbit-mehirst/linc-1244-0-1cfde12d50f92
unix  3      [ ]         STREAM     CONNECTED     11707    
unix  3      [ ]         STREAM     CONNECTED     11709    /tmp/orbit-mehirst/linc-1244-0-1cfde12d50f92
unix  3      [ ]         STREAM     CONNECTED     11706    
unix  3      [ ]         STREAM     CONNECTED     11708    /tmp/orbit-mehirst/linc-1244-0-1cfde12d50f92
unix  3      [ ]         STREAM     CONNECTED     11705    
unix  3      [ ]         STREAM     CONNECTED     11700    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11699    
unix  3      [ ]         STREAM     CONNECTED     11698    /tmp/orbit-mehirst/linc-125a-0-497a706894556
unix  3      [ ]         STREAM     CONNECTED     11697    
unix  3      [ ]         STREAM     CONNECTED     11694    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     11693    
unix  3      [ ]         STREAM     CONNECTED     11691    /tmp/.ICE-unix/4599
unix  3      [ ]         STREAM     CONNECTED     11690    
unix  3      [ ]         STREAM     CONNECTED     11686    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11685    
unix  3      [ ]         STREAM     CONNECTED     11680    @/tmp/dbus-zO3s4neq15
unix  3      [ ]         STREAM     CONNECTED     11679    
unix  3      [ ]         STREAM     CONNECTED     11677    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11676    
unix  2      [ ]         DGRAM                    11675    
unix  3      [ ]         STREAM     CONNECTED     11674    /tmp/orbit-mehirst/linc-1257-0-497a706861a2a
unix  3      [ ]         STREAM     CONNECTED     11673    
unix  3      [ ]         STREAM     CONNECTED     11670    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     11669    
unix  3      [ ]         STREAM     CONNECTED     11667    /tmp/.ICE-unix/4599
unix  3      [ ]         STREAM     CONNECTED     11666    
unix  3      [ ]         STREAM     CONNECTED     11662    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11661    
unix  3      [ ]         STREAM     CONNECTED     11656    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11655    
unix  3      [ ]         STREAM     CONNECTED     11650    @/tmp/dbus-zO3s4neq15
unix  3      [ ]         STREAM     CONNECTED     11649    
unix  3      [ ]         STREAM     CONNECTED     11648    /tmp/orbit-mehirst/linc-124f-0-75970cbb2e441
unix  3      [ ]         STREAM     CONNECTED     11647    
unix  3      [ ]         STREAM     CONNECTED     11644    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     11643    
unix  3      [ ]         STREAM     CONNECTED     11641    /tmp/.ICE-unix/4599
unix  3      [ ]         STREAM     CONNECTED     11638    
unix  3      [ ]         STREAM     CONNECTED     11634    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11633    
unix  3      [ ]         STREAM     CONNECTED     11625    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11624    
unix  3      [ ]         STREAM     CONNECTED     11623    /tmp/orbit-mehirst/linc-1248-0-4193f4dc66902
unix  3      [ ]         STREAM     CONNECTED     11622    
unix  3      [ ]         STREAM     CONNECTED     11619    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     11618    
unix  3      [ ]         STREAM     CONNECTED     11615    @/tmp/dbus-zO3s4neq15
unix  3      [ ]         STREAM     CONNECTED     11614    
unix  3      [ ]         STREAM     CONNECTED     11604    @/tmp/dbus-zO3s4neq15
unix  3      [ ]         STREAM     CONNECTED     11603    
unix  3      [ ]         STREAM     CONNECTED     11601    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11600    
unix  3      [ ]         STREAM     CONNECTED     11597    /tmp/orbit-mehirst/linc-1242-0-75970cbca600
unix  3      [ ]         STREAM     CONNECTED     11596    
unix  3      [ ]         STREAM     CONNECTED     11593    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     11592    
unix  3      [ ]         STREAM     CONNECTED     11590    /tmp/.ICE-unix/4599
unix  3      [ ]         STREAM     CONNECTED     11589    
unix  3      [ ]         STREAM     CONNECTED     11585    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11584    
unix  3      [ ]         STREAM     CONNECTED     11575    @/tmp/dbus-zO3s4neq15
unix  3      [ ]         STREAM     CONNECTED     11574    
unix  3      [ ]         STREAM     CONNECTED     11566    /tmp/orbit-mehirst/linc-1240-0-3cd567caadb0
unix  3      [ ]         STREAM     CONNECTED     11565    
unix  3      [ ]         STREAM     CONNECTED     11562    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     11561    
unix  3      [ ]         STREAM     CONNECTED     11554    /tmp/orbit-mehirst/linc-123e-0-3cd567c9746a
unix  3      [ ]         STREAM     CONNECTED     11553    
unix  3      [ ]         STREAM     CONNECTED     11550    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     11549    
unix  3      [ ]         STREAM     CONNECTED     11547    /tmp/.ICE-unix/4599
unix  3      [ ]         STREAM     CONNECTED     11545    
unix  3      [ ]         STREAM     CONNECTED     11541    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11540    
unix  3      [ ]         STREAM     CONNECTED     11546    /tmp/.ICE-unix/4599
unix  3      [ ]         STREAM     CONNECTED     11531    
unix  3      [ ]         STREAM     CONNECTED     11527    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11526    
unix  3      [ ]         STREAM     CONNECTED     11516    /tmp/.ICE-unix/4599
unix  3      [ ]         STREAM     CONNECTED     11515    
unix  3      [ ]         STREAM     CONNECTED     11514    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11513    
unix  3      [ ]         STREAM     CONNECTED     11512    /tmp/orbit-mehirst/linc-1239-0-694401093571
unix  3      [ ]         STREAM     CONNECTED     11511    
unix  3      [ ]         STREAM     CONNECTED     11508    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     11507    
unix  3      [ ]         STREAM     CONNECTED     11496    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11495    
unix  3      [ ]         STREAM     CONNECTED     11488    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11487    
unix  2      [ ]         STREAM                   11478    
unix  3      [ ]         STREAM     CONNECTED     11465    @/tmp/dbus-zO3s4neq15
unix  3      [ ]         STREAM     CONNECTED     11464    
unix  3      [ ]         STREAM     CONNECTED     11457    /tmp/orbit-mehirst/linc-1226-0-890d16d65446
unix  3      [ ]         STREAM     CONNECTED     11456    
unix  3      [ ]         STREAM     CONNECTED     11453    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     11452    
unix  3      [ ]         STREAM     CONNECTED     11448    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11447    
unix  3      [ ]         STREAM     CONNECTED     11434    @/tmp/dbus-zO3s4neq15
unix  3      [ ]         STREAM     CONNECTED     11433    
unix  3      [ ]         STREAM     CONNECTED     11406    /tmp/orbit-mehirst/linc-11f7-0-45d66546ec654
unix  3      [ ]         STREAM     CONNECTED     11405    
unix  3      [ ]         STREAM     CONNECTED     11404    /tmp/orbit-mehirst/linc-1220-0-754b6d8cd41f9
unix  3      [ ]         STREAM     CONNECTED     11253    
unix  2      [ ]         DGRAM                    11239    
unix  3      [ ]         STREAM     CONNECTED     11233    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11232    
unix  3      [ ]         STREAM     CONNECTED     11229    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11228    
unix  3      [ ]         STREAM     CONNECTED     11227    
unix  3      [ ]         STREAM     CONNECTED     11226    
unix  2      [ ]         DGRAM                    10992    
unix  3      [ ]         STREAM     CONNECTED     10991    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10990    
unix  2      [ ]         DGRAM                    10973    
unix  3      [ ]         STREAM     CONNECTED     10899    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10898    
unix  3      [ ]         STREAM     CONNECTED     10891    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10890    
unix  3      [ ]         STREAM     CONNECTED     10869    @/tmp/hald-local/dbus-8isjf6s20X
unix  3      [ ]         STREAM     CONNECTED     10865    
unix  3      [ ]         STREAM     CONNECTED     10830    @/tmp/hald-local/dbus-8isjf6s20X
unix  3      [ ]         STREAM     CONNECTED     10827    
unix  3      [ ]         STREAM     CONNECTED     10808    @/tmp/hald-local/dbus-8isjf6s20X
unix  3      [ ]         STREAM     CONNECTED     10804    
unix  3      [ ]         STREAM     CONNECTED     10797    @/tmp/hald-local/dbus-8isjf6s20X
unix  3      [ ]         STREAM     CONNECTED     10793    
unix  3      [ ]         STREAM     CONNECTED     10786    @/tmp/hald-local/dbus-8isjf6s20X
unix  3      [ ]         STREAM     CONNECTED     10775    
unix  3      [ ]         STREAM     CONNECTED     10736    @/tmp/hald-local/dbus-8isjf6s20X
unix  3      [ ]         STREAM     CONNECTED     10728    
unix  3      [ ]         STREAM     CONNECTED     10666    @/tmp/hald-local/dbus-8isjf6s20X
unix  3      [ ]         STREAM     CONNECTED     10658    
unix  3      [ ]         STREAM     CONNECTED     10651    @/tmp/hald-local/dbus-8isjf6s20X
unix  3      [ ]         STREAM     CONNECTED     10635    
unix  3      [ ]         STREAM     CONNECTED     9081     @/tmp/hald-runner/dbus-plEwuRNBju
unix  3      [ ]         STREAM     CONNECTED     9080     
unix  3      [ ]         STREAM     CONNECTED     9049     
unix  3      [ ]         STREAM     CONNECTED     9048     
unix  2      [ ]         DGRAM                    9010     
unix  2      [ ]         DGRAM                    8937     
unix  5      [ ]         STREAM     CONNECTED     8974     /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8868     
unix  2      [ ]         DGRAM                    8706 

    
mehirst@mehirst-desktop:~$ nslookup mail.aapt.net.au
Server:         10.1.1.1
Address:        10.1.1.1#53

Non-authoritative answer:
Name:   mail.aapt.net.au
Address: 210.10.73.252

Hope this is what you are looking for.

---

### Post by Mr. C. on 2007-03-29
Darn, I missed a option to the netstat command I gave you.

Please run

```
netstat -ln
```

and replace your output above with the new data (by editing your post).

My apologies.
MrC

---

### Post by Mr. C. on 2007-03-29
Your pop server is listening and active.  Duplicate the telnet command below from a Terminal window, and enter your username and password as shown to see if you can successfully log in.  The blue colors below are output from the POP server.  You input the rest.

```
$ telnet 210.10.73.252 110   
[COLOR="RoyalBlue"]Trying 210.10.73.252...
Connected to 210.10.73.252.
Escape character is '^]'.
+OK POP3 Ready pfep02 00013297[/COLOR]
USER your_user_name
[COLOR="RoyalBlue"]...[/COLOR]
PASS your_password
LIST
QUIT
[COLOR="RoyalBlue"]+OK QUIT[/COLOR]
[COLOR="RoyalBlue"]Connection closed by foreign host.[/COLOR]
```

If you can connect, and list your files, everything is working fine.  Next step is to properly configure Evolution.

MrC

---

### Post by newaustralian on 2007-03-29
Again my thanks Mr C

Yes I could login successfully using telnet and list my files.

I configured Evolution with help from my ISP tech support who are clearly more conversant with Windows than Ubuntu.

Over to you

---

### Post by Mr. C. on 2007-03-29
Ok, so I might be confused, but it sounds like you have what you need to connect to your POP server to receive email.  I recall you had an error fetching mail - is this still a problem ?

If you can't receive your email now in Evolution, you'll have to show how your Evolution is configured for Receving Email.

Server Type: ?
Server: ?
Username : same as your telnet test

Use Secure Connection: ?
Authentication Type: ?

MrC

---

### Post by newaustralian on 2007-03-30
Thanks Mr C.

Problem is still there.

OK so the receiving details are:

Full error message is  "Error while fetching mail, could not connect to mail.aapt.net.au No route to server"

Server type: POP
Server: mail.aapt.net.au
Username: [email]mehirst@aapt.net.au[/email]
Security: No encryption
Authentication: Password and Remember password box is ticked

I have also checked sending mail and I get a similar problem but let us deal with the receiving aspect first. It could be that the answer to one solves the other.

---

### Post by Mr. C. on 2007-03-30
Earlier I asked you if you were using your ISP's name servers, or your router as a name server.  You said this was not a factor.  Yet the domain name lookup I had you perform earlier shows that you are using a DNS server at address:

Server: 10.1.1.1

I do not know if this is your ISP's private DNS server, or if this is a caching DNS server on your modem, or what.  It is a private IP, so I cannot discover what it is.

Your symptoms are signs of DNS trouble.  I suggested you remove your nameserver lines in your /etc/resolv.conf file.

Try either or both of these:

```
nameserver 192.189.54.33
nameserver 192.189.54.17

```
Now these servers may not work for you, as I don't not know if they will resolve queries for you recursively.  If they do not work, use these instead:

```

nameserver  208.67.222.222
nameserver  208.67.220.220

```

The /etc/resolv.conf file will be overwritten if your network goes down, or you reboot.  We are merely trying to resolve the current problem.

Let me know if this resolves the problems.
MrC

---

### Post by newaustralian on 2007-03-30
Mr C

When I opened  /etc/resolv.config the 10. 1 etc nameserver was in the file.

I replaced that line with:

nameserver 192.189.54.33
nameserver 192.189.54.17

as you suggested and Evolution will now both receive and send correctly so it looks like we are getting somewhere.

I assume from your comment that this is the first step. Please advise further.

Thanks for all your help so far.

---

### Post by newaustralian on 2007-03-30
More information Mr C

You mentioned that the /etc/resolv.config file would be overwritten if the network disconnected or I rebooted the computer.

After about 30 minutes I returned to Evolution and the old problem was back.  I opened /etc/resolv.config file and saw that the nameservers I had manually entered as you instructed (see previous post) had been overwritten by my local 10.1.1 address.

During that 30 minutes I had been using Firefox to browse the web but nothing else.

I guess the question is what is overwriting the nameservers?

---

### Post by Mr. C. on 2007-03-30
What is happening is that your connection is dropping, and when restored, you are getting reassigned DHCP parameters; this overwrites the name servers in the /etc/resolv.conf file, with a name server most likely from your router. I'd suggesting changing this name server in post #6, but I don't think I fully made myself clear.

In post #3, you indicated you did not have a router.  I'd suggest you pick up an inexpensive router/firewall/NAT appliance.  This will help mitigate future issues like you have been experiencing.  You can configure the router always provide the proper assignments - you have more control.

In the file /etc/dhcp3/dhclient.conf, there is a section that looks like:

```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;

```
Remove the "domain-name-servers, " part so that it looks like this:

```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, host-name,
        netbios-name-servers, netbios-scope;
```

You can now go change your resolv.conf back to the configuration that worked.  Next time the network connection restarts, DHCP will not provide the DNS servers, so your resolv.conf file should be left alone.

MrC

---

### Post by newaustralian on 2007-03-31
Mr C

Made the changes as advised in post 21 and all worked well until I rebooted the computer when the /etc/resolv.conf nameservers I had entered got overwritten by the local.  I checked the dhclient.conf file and the amendment I made as post 21 was still valid.

I have gone back through all the posts to see if  I have missed anything.

On rechecking my limited manuals for the ADSL modem it is sometimes called a modem and sometimes a router.  The device is a Dlink DSL 502T supplied about 9 months ago by my ISP.  I have it connected to an Ehternet 10/100 adapter.

Ipv6 is still disabled and Firefox has consistently worked on startup and all reboots.
Gaim and Ekiga work and I can manually ping servers. The problem seems to be confined to the resolution of the Evolution servers and whatever is overwritting those nameserver specifications.

Further advice appreciated and many thanks for your patience.

---

### Post by Mr. C. on 2007-03-31
Go ahead and add this to /etc/dhcp3/dhclient.conf:

```
prepend domain-name-servers 192.189.54.33;
prepend domain-name-servers 192.189.54.17;
```

save the file, and run :

```
sudo /etc/init.d/networking restart
```

That should prepend the name servers to your resolv.conf file, so that they are used first.

MrC

---

### Post by Floppyjoe on 2007-03-31
The info in this link may help you solve your problem:
[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=15](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=15)
You can use your ISP provided DNS nameservers instead of the OpenDNS servers in the prepend line

Never mind oops. Mr. C. beat me to the enter key.

---

### Post by newaustralian on 2007-03-31
Many thanks Mr C

prepending the servers works.  Evolution does not appear to disconnect over time and when I reboot the correct nameservers are in resolv.config.

In the process I have learnt something about linux and I thank you for that.

I wonder is it worth creating a HOWTO so that others have a helpful reference. Part of the solution is in the HOWTO about disabling Ipv6 but that was only part of it?

Over and hopefully out

---

