---
title: "workaround to connect to local wifi network w/ Linux PC hardwired to range extender"
date: 2022-02-07
forum: Networking &amp; Wireless
---

### Post by ozark_hillbilly on 2022-02-07
Ubuntu 20.04 LTS

I have a situation where I installed a home weather station that has wifi capability. 
To interface w/ the weather station directly (192.168.1.1) you set your device to search for local wifi networks
and then select the network the weather station projects in AP mode. You sign on and then have access to calibration parameters and 
the ability to do firmware upgrades, etc. 

In normal mode the weather station syncs up with my local router and provides data access available through
sites like the Weather Underground. But to do firmware upgrades the platform has to be a desktop pc where you
first download the firmware upgrade file off the web, unzip, and pass to the weather station processor. 

My problem is I have no way to scan for additional networks through the Linux Desktop. It is ethernet hardwired 
to a range extender that links to my home router upstairs. Is there any way the home router can "see" the weather
station network and allow my Desktop to route over to it?

Its a stretch I know. The weather station has no physical ports and my Linux PC is hardwired dependent. Is the only
option to put some sort of "USB wifi" on the Desktop and then hope it will connect to the weather station? 

What software is needed off Synaptic to allow the Desktop to search for local networks?

thanks for any suggestions...

---

### Post by him610 on 2022-02-10
> I installed a home weather station
I have been thinking about buying one of these. What make, model did you install?
> What software is needed off Synaptic to allow the Desktop to search for local networks? I think this will provide what you are looking for.
Go to the stickies in the Network forum, follow the instructions here, [https://ubuntuforums.org/showthread.php?t=370108]("https://ubuntuforums.org/showthread.php?t=370108")
It is a networks diagnostic that will search, find, and list all wifi networks within range.

After rereading post, you may find it necessary to install a wireless network adapter in your PC. I don't know of a way to access your wireless weather station from your PC through the router; although, there may be a way of which I am unaware.
Can you 'ssh' into the weather station?

---

### Post by him610 on 2022-02-10
Say ozark_hillbilly,

I thought about this a little more. I would think your weather station is one of those IoT devices that communicate with some server in the sky. I have a IoT thermostat that communicates with its server in the sky. My IoT thermostat gets its updates from its server in the sky; I never have to worry about it.

> But to do firmware upgrades the platform has to be a desktop pc where you first download the firmware upgrade file off the web, unzip, and pass to the weather station processor.
Is that what it says in the manual for your wireless weather station? 
It has an IP address assigned by your wireless router, or it has a static IP address set by the manufacturer. 
> ...you first download the firmware upgrade file off the web, unzip, and pass to the weather station processor.
I would think you could 'scp' the file over, but you probably need a user, and password for the weather station.

>  Is there any way the home router can "see" the weather station network and allow my Desktop to route over to it?
You should be able to log into the router and view all of the connected devices, both wired and wireless. If you know the IP address, you can probably ping it to see if there is a path. Since your PC and the Weather Station are served by the same network router, pinging is probably no issue, but you do need to know the IP address.

Maybe, one of the resident subject matter experts will offer more enlightened suggestions on your issue.

---

