---
title: "Bandwidth Monitor questions"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by ragrim on 2007-08-21
Hi, 

im running Server 7.04 as a gateway with shorewall firewall and im using the bandwidth monitor through webmin to monitor my network useage, but it seems to be very inacurate...

example.... the monitor does not capture all network information, yesterday i downloaded 100mb+ but the gateway only registered me as using a total of 1.5mb of data.

ive tried a few bandwidth monitoring programs but they all seem to be the same.

another thing, i got ethstatus to monitor the load on my network card but its chosen the wrong card, i want it to monitor my external card not just my internal, is there a way to configure it to monitor 2 cards? or to select a card?

Thanks in advance

---

### Post by Ek0nomik on 2007-08-21
I don't have much experience with bandwidth meters on Linux, but have you tried Conky?  The default Conky setup has a bandwidth (download and upload) meter.

---

### Post by ragrim on 2007-08-21
i just looked up that conky but from what i can tell its GUI monitor, does it run in terminal? i dont have desktop installed on my server i use command line for everything.

---

### Post by Ek0nomik on 2007-08-21
Oh, I'm sorry I didn't know you didn't have a GUI.

I managed to find this:  [http://onlyubuntu.blogspot.com/2007/03/bandwidth-monitoring-tools-for-linux.html](http://onlyubuntu.blogspot.com/2007/03/bandwidth-monitoring-tools-for-linux.html)

Seems to have quite the large list of bandwidth monitors.  Hopefully a few are for the command line interface.

---

### Post by wirelessmonkey on 2007-08-21
I think you're making a syntax mistake ragrim.  You downloaded a 100 MegaByte file, but you only used ~1.5 Mega Bits (per second) of bandwidth.  "Megabit" is a bandwidth metric "MegaByte" is a file size metric.

---

### Post by Ek0nomik on 2007-08-21
> **wirelessmonkey said:**
> I think you're making a syntax mistake ragrim.  You downloaded a 100 MegaByte file, but you only used ~1.5 Mega Bits (per second) of bandwidth.  "Megabit" is a bandwidth metric "MegaByte" is a file size metric.

I think he was saying that he knows for a fact he downloaded over 100 megabytes of data, but the log only said he downloaded 1.5 megabytes of data.  Although I could be misunderstanding him as well...

---

### Post by robert_pectol on 2007-08-21
Here's a script that you may be interested in trying out:

[http://rob.pectol.com/myscripts/bandwidth.sh.txt](http://rob.pectol.com/myscripts/bandwidth.sh.txt)

It will generate a nice little gui dialog with your total RX and TX data, as well as your system uptime!  Save it as "bandwidth.sh" and make it executable (chmod 755 bandwidth.sh).  Then you can either run it directly from the command line, or create a little custom launcher for your taskbar that calls it.  Enjoy!  :-)

---

### Post by Ek0nomik on 2007-08-21
> **robert_pectol said:**
> Here's a script that you may be interested in trying out:

[http://rob.pectol.com/myscripts/bandwidth.sh.txt](http://rob.pectol.com/myscripts/bandwidth.sh.txt)

It will generate a nice little gui dialog with your total RX and TX data, as well as your system uptime!  Save it as "bandwidth.sh" and make it executable (chmod 755 bandwidth_useage.sh).  Then you can either run it directly from the command line, or create a little custom launcher for your taskbar that calls it.  Enjoy!  :-)

Based upon the authors name it looks like you wrote it.  :)

---

### Post by robert_pectol on 2007-08-21
Perhaps...  :-)

---

### Post by ragrim on 2007-08-22
Sorry if i wasnt clear.. what i mean is i have downloaded over 100 megabytes of data but the log only showed 1.5 megabytes of downloaded data.

i should be a little more specific aswell, ive tried atleast 10-15 differant programs so far. like bandwidthd, ethstatus, the webmin bandwidth monitor and so on but none of them seem to be accurate.

what i need is 2 things..

1. to be able to see the amount of internet usage IP xxx.xxx.xxx.xxx on my network has used! (we have 40 odd computers on the network and are trying to track who is downloading all the porn :P)

2. to monitor the current load of each ethernet card in the gateway server. so far ethstatus is great it show me exactly what i want to know, problem is it only shows me 1 network card, i need to be able to see the current kb/s tranfer on both.

So if anyone has any ideas on how to make my current webmin bandwidth monitor work properly, or has a link to a program that works properly, all i need is something that runs in a terminal, web interface is optional, id be very happy.

Thanks :D

---

### Post by ragrim on 2007-08-22
bump,

So anyone got any ideas for me?

---

### Post by wirelessmonkey on 2007-08-22
I use Cacti to monitor bandwidth, [www.cacti.net](www.cacti.net)...

---

### Post by vdawg on 2007-08-26
what exactly is bandwidthd not doing?

The way I have it setup on our subnet it shows me IP traffic for all the computers - we have static ips assigned so it's pretty accurate :)

---

### Post by ragrim on 2007-08-27
bandwidthd seems to be inaccurate and doesnt break down the bandwidth usage in a format i need it. Bandwidth monitor in webmin shows me hourly reports by IP which is very usefull except its not accurate.

im yet to find a bandwidth monitor that records my downloads with even a remote accuracy. bandwidthd recorded 1.4gb downloaded via HTTP on 1 of our computers that is a terminal within the factory that does not have any internet explorer or firefox and its port 80 is blocked so it cant view HTTP.

---

### Post by wirelessmonkey on 2007-08-27
You want traffic counters, not bandwith monitors.

---

### Post by ragrim on 2007-08-27
yeah your right there.

ive tried another handfull of programs today, none of which seem to suit my needs :( i realy wish there was a net limiter for Ubuntu

---

### Post by Aessa on 2007-09-02
The best I've tried yet is ntop. Terribly complex but with only a litlle customisation you can get really nice graphs, totals, open ports and a store of other things. It has one extremely annoying drawback...it does not keep statistics on restart. So let's assume you have a reliable electricity source, you still lose it all about every week (I think) when the log file gets rotated. Either way, if ntop managed its own persistent stats it would be a great monitoring tool. As for network traffic control, I suppose you could set up a proxy (Squid) with user accounts, site blocks etc...

---

### Post by ragrim on 2007-09-19
i think i have finally discovered why the bandwidth monitor in webmin isnt reporting all usage, it seems that i have to update the statistics manually every hour or it loses the data.

does anyone know is there any option to increase how much it can store? or is there a way i can get the bandwidth monitor to automatically update the statistics?

Thanks.

---

### Post by mjt_colo on 2007-12-05
> **robert_pectol said:**
> Here's a script that you may be interested in trying out:

[http://rob.pectol.com/myscripts/bandwidth.sh.txt](http://rob.pectol.com/myscripts/bandwidth.sh.txt)

It will generate a nice little gui dialog with your total RX and TX data, as well as your system uptime!  Save it as "bandwidth.sh" and make it executable (chmod 755 bandwidth.sh).  Then you can either run it directly from the command line, or create a little custom launcher for your taskbar that calls it.  Enjoy!  :-)
[FONT="Comic Sans MS"][SIZE="4"]
very nice, and thanks.... from a linux newbie.

Michael[/SIZE][/FONT]

---

