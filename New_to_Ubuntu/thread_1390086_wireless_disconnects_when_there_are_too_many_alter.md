---
title: "wireless disconnects when there are too many alternatives"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by rkparker on 2010-01-25
Hello, 

I have an interesting wireless problem that I can't find between the solved threads.
I've been using ubuntu for half a year (now 9.10), more or less. In my home I have **ONE wireless network**, and I can connect to this network without problems. 
Now I live in an appartment with around **10 wireless networks** (all with a weak signal). In this situation, the network manager **switches from one network to the other** all the time, making impossible to work online. The longest connection **lasts one minute**. 

When I choose one of this wireless connections with Windows XP it stays connected  as long as I use it, without any problems. 

Please, can anyone help me with this issue? I don't want to go back to XP!

Thanks, 

rkparker

---

### Post by inobe on 2010-01-25
welcome to the forums


sounds as if you have an extended list of networks ?

if you right click the connection icone and hit edit connections' you will get a dialog, click the wireless tab, you should see a fair amount of connections, remove the connections you do not use or all, restart your system, connect to one network and avoid connecting to others if the connection drops, this would only build another list.

if i lose a connection and i'm prompted to connect again' i simply right click the connection icon and uncheck wireless, i wait a few seconds and enable it.

this is assuming you connect to a secure connection.

---

### Post by atlaslion on 2010-10-16
I had a similar problem. My wireless network was conflicting with other signals in the building where I live. I fixed the issue by changing the wireless channel on my router.
I hope this help

---

### Post by diablo75 on 2010-10-17
> **atlaslion said:**
> I had a similar problem. My wireless network was conflicting with other signals in the building where I live. I fixed the issue by changing the wireless channel on my router.
I hope this help

Pro-tip:  When you change channels on your wireless router, only use channels 1, 6 or 11 (or higher if available).  The reason for this is that there is  spillover in the radio wavelenths used.  So channels 1 actually overlaps with channels 2 and 3, channel 6 overlaps channels 4-8, and 11 over 9-13.  Here's an image that illustrates this  from an Android app displaying a survey of nearby wireless networks.

[IMG]http://www.davestechsupport.com/blog/images/wifiandroid.jpg[/IMG]

---

### Post by beew on 2010-10-17
> **inobe said:**
> welcome to the forums


sounds as if you have an extended list of networks ?

if you right click the connection icone and hit edit connections' you will get a dialog, click the wireless tab, you should see a fair amount of connections, remove the connections you do not use or all, restart your system, connect to one network and avoid connecting to others if the connection drops, this would only build another list.

if i lose a connection and i'm prompted to connect again' i simply right click the connection icon and uncheck wireless, i wait a few seconds and enable it.

this is assuming you connect to a secure connection.

You don't need to uncheck the wireless, just choose edit connection> wireless and uncheck automatic connect for those network that you don't use.

But I am wondering if there is a way to configure Ubuntu so that, say if one network drops off it will pick up the strongest one available automatically.

---

