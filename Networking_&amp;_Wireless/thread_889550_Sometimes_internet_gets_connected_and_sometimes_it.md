---
title: "Sometimes internet gets connected and sometimes it not..."
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by shredder12 on 2008-08-14
Hey, I have Ubuntu 8.04 installed on my system..actually i downloaded a 700 Mb installation file from Ubuntu site.. so i need to install all the required packages from internet but I am facing a lot of problems while connecting to internet..
When the first time I configured my ethernet connection it seems to work well but the next time i restarted my system and changed the settings it didn't work..I don't know why..
I tried the command
```
ifconfig 
```
to know whether I am getting an IP address or not..
then I came to know that the values weren't correct..
I changed the valued of ip, subnet mask and gateway to the correct values..and after a few efforts it got connected but when i tried do the same thing the third time..
it is still not connecting..
I tried to open the network tools from system->administration->networking tools..
and when i selected the ehternet interface I could see..
that the packets were being transmitted and received..
It looks something like this..
Transmitted bytes:10.9kb
Transmitted packets:87
Received bytes:252.4kb
Received packets:2632

and all this is increasing at a slow rate..
the icon which shows the link speed..
says not available..

one more problem is that when i tried to click the configure options it first of all asked for the password and then it said that

```
**The interface does not exist**
Check that it is correctly typed and that it is correctly supported by your system..
```
Common..
if it was not connected properly then how could it have worked properly a couple of times..and have downloaded as well as installed 14 packages from internet..

Help me with this problem !!!
I m really frustrated with this one..

---

### Post by Vishal Agarwal on 2008-08-14
This can be a connectivity problem from your ISP. In one window do ping to some web IP MSN or YAHOO etc. continuous, to check the connectivity every time during the download.

I also face the same problem of Connected/Disconnected. and I am checking in the same manner.

---

