---
title: "Network traffic monitoring software? Use with Conky?"
date: 2013-11-10
forum: Networking &amp; Wireless
---

### Post by s-p-constantine on 2013-11-10
Hi,

I've seen plenty of applications, such as Etherape, that allow monitoring of network traffic. These all seem to be of data off the machine I'm using.

I'd like to monitor data traffic volumes from all the devices on my home network (*e.g.* a couple of XBoxes). My BT HomeHub router doesn't give me that capability.

Ideally, I like some desktop widgets, or better still, integration with Conky, so that I can see readily see what devices are using my bandwidth.

(No packet snooping, just traffic volume monitoring!)

Is there anything out there that I can use?

Thanks - Steven.

---

### Post by TheFu on 2013-11-10
To monitor network traffic the monitoring needs to see the traffic. That usually means it has to sit on the device where the bandwidth is used - or do it on the network equipment.  Otherwise, only a partial view can be provided.

Desktop widgets are not the best way to monitor bandwidth use. System monitoring is something that most end-users do not perform very well, IMHO. One of the easiest ways that I know to bridge the end-user and server monitoring is with SysUsage. [http://blog.jdpfu.com/2009/12/16/sysusage-3-0-installation-steps](http://blog.jdpfu.com/2009/12/16/sysusage-3-0-installation-steps) is a little dated, but give the general idea for installation.  To see the stuff it will graph, [http://sysusage.darold.net/screenshot-sysusage/](http://sysusage.darold.net/screenshot-sysusage/) .

On Ubuntu, the package dependencies should be 
   - sysstat 
   - rrdtool 
   - librrds-perl
   - librrd4
   - libdbi1
   - sysusage
if my ansible script is correct still. Could be wrong.

This will only provide the view of monitored systems ... windows/linux/unix ... don't think smart TVs, specialty media players, or Android/Apple are supported.  For those, it really needs to happen on the router.  Any router running dd-wrt, tomato or pfSense can do it. The graphs on tomato are really easy to use.

Another alternative is to force all other devices to use a transparent proxy and monitor that device. [http://www.tldp.org/HOWTO/TransparentProxy.html](http://www.tldp.org/HOWTO/TransparentProxy.html) Probably more than you'd like to bite.

---

### Post by houstonbofh on 2013-11-10
As stated, you need to "see" the traffic to monitor the traffic.  This can be a monitor port on a managed switch.  Or you can build an Ubuntu system with a second network card and bridge them, then pass all of the traffic through that bridge.

And if you like etherape, also check out ntopng, an update of the well regarded ntop. [http://www.ntop.org/ntop/its-time-for-a-completely-new-ntop-say-hello-to-ntopng/](http://www.ntop.org/ntop/its-time-for-a-completely-new-ntop-say-hello-to-ntopng/)

---

### Post by ajgreeny on 2013-11-10
Just to see what is going through my own computer I use vnstat and take the output from that into conky.  I accept that if there are other machines using the network it will not be a accurate overall figure, but for my one main machine it is fine for me.

The .conkyrc content I use for the network display is
```
NETWORK IP: $alignr eth0 -  ${addr eth0}
DOWN: ${downspeed eth0}/s$alignr UP: ${upspeed eth0}/s
${color #FFA500}${downspeedgraph eth0 40,158}$alignr${upspeedgraph eth0 40,158}${color #FFFFFF}
TOTAL ${totaldown eth0}$alignr TOTAL ${totalup eth0}

#NETWORK IP: $alignr eth0 -  ${addr eth0}
#DOWN: ${downspeed eth0}/s $alignr TOTAL ${totaldown eth0}
#${downspeedgraph eth0 20,320}
#UP: ${upspeed eth0}/s $alignr TOTAL ${totalup eth0}
#${upspeedgraph eth0 20,320}
#
# To make hddtemp run as user use command "sudo chmod u+s /usr/sbin/hddtemp"
[COLOR=#ff0000]# To make vnstat run as user use command "sudo chmod u+s /usr/bin/vnstat"[/COLOR]
# "${execi 60 vnstat" updates figures every 60 seconds.
DOWN:                        UP:
Today: ${execi 60 vnstat | grep "today" | awk '{print $2 $3}'}${alignr}Today: ${execi 60 vnstat | grep "today" | awk '{print $5 $6}'}
Week:  ${execi 60 vnstat -w | grep "current week" | awk '{print $3 $4}'}${alignr}Week:  ${execi 60 vnstat -w | grep "current week" | awk '{print $6 $7}'}
Month: ${execi 60 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${alignr}Month: ${execi 60 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
```
Note the command in red needed to run vnstat as user instead of root.

---

### Post by s-p-constantine on 2013-11-10
@TheFu, @houstonbofh, @ajgreeny, 

Thanks for your thoughts.

I'm really interested to see data flows from some of the devices on my network, *e.g.* an XBox.

A BT HomeHub 3 is my ADSL modem and network DHCP server - it seems to have hardly any administration capability. I also have two wireless routers on my network, one a WRT54G running DD-WRT. If I switch the DHCP on my network to the WRT54G, even though it's not the gateway, could I then tap into its admin capability?

Cheers - Steven.

---

### Post by tgalati4 on 2013-11-10
Try moving things around so that the WRT54G becomes the gateway.  You can set up a static route through the WRT to the ADSL modem then have the WRT serve up the DHCP addresses.  Then you can poll dd-wrt for network statistics.  Once you have collected some data, you can set up Quality of Service (QoS) in dd-wrt to suit your needs.

---

### Post by SeijiSensei on 2013-11-10
Make a Linux box be the internal network's default gateway and configure it to forward outbound traffic upstream to your router.  Then you can run something like [ntop]("http://www.ntop.org/") on the Linux box and see all the network traffic.  You can install ntop from the repositories.

Even then I'm not sure you'll see traffic that remains entirely within the local network.  Remember that TCP/IP and Ethernet rely on broadcasts to communicate within the local subnet.  Only when traffic must leave the local subnet are routers involved.  In essence all the machines communicate locally by shouting out the destination IP address of the packets they generate and waiting for the target to grab its packets as they flow by over the wire.  While the method sounds incredibly inefficient, it's a tribute to Bob Metcalfe's insight that it works so well.  IBM's token-ring protocol may had made more logical sense, but it was more expensive to implement and ultimately did not provide substantial performance improvements over Ethernet.

---

### Post by dentaku65 on 2013-11-11
You can use this raw command from terminal:
```
xterm -hold -e sudo iftop [COLOR="#FF0000"]-i wlan0[/COLOR] &
```
where in [COLOR="#FF0000"]red[/COLOR] you must indicate your network dev

---

### Post by s-p-constantine on 2013-11-11
Thanks again for the replies.

@[**[COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895") how would I go abpout polling DD-WRT from my linux machine. Just some pointers on the web would be great, and I can learn/tinker the specifics for myself...

---

### Post by TheFu on 2013-11-11
[http://www.dd-wrt.com/wiki/index.php/Network_traffic_analysis_with_netflow_and_ntop](http://www.dd-wrt.com/wiki/index.php/Network_traffic_analysis_with_netflow_and_ntop)
There is also the bwlog [http://www.dd-wrt.com/wiki/index.php/BWlog](http://www.dd-wrt.com/wiki/index.php/BWlog)
and using SNMP traps.

If you aren't tied to dd-wrt for some reason (GigE router), then Tomato is a similar firmware with those graphs built-in. That could be easier.

---

### Post by s-p-constantine on 2013-11-17
Great, all sorted.

WRT54G with DD-WRT v24 sp2 has now replaced my BT HomeHub3 and is polling network traffic to my laptop.

Just need to get smarter with ntop now and learn to filter-out the data I'm not interested in.

Thanks for all help provided.

---

### Post by s-p-constantine on 2013-11-22
Aaaaargh.

DD-WRT router slow-down. Need to fin an alternative router than can cope with my multiple XBox Live/Netflix/Lovefilm connections....

---

### Post by houstonbofh on 2013-11-22
I have been very happy with tomato firmware.  Especially the "Toastman" variants...

---

