---
title: "Wired Internet Connection"
date: 2014-07-12
forum: Networking &amp; Wireless
---

### Post by colin22 on 2014-07-12
I have been using Ubuntu for ages - suddenly it won't connect to the Internet although is says it is connected to the network.
Firefox just says it can't communicate with website.
What do I need to do to sort it please.
Colin

---

### Post by TheFu on 2014-07-12
We can't tell where the issue lies based on the description.
Please follow these troubleshooting steps and report back: [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

With that output, we'll know where the issue lies.

---

### Post by varunendra on 2014-07-13
Welcome to the forums colin22!

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

**@TheFu**, That blog isn't opening for me, *"Server Error..... took too long to respond"*, could be a temporary error though.

---

### Post by TheFu on 2014-07-13
> **varunendra said:**
> 
**@TheFu**, That blog isn't opening for me, *"Server Error..... took too long to respond"*, could be a temporary error though.

[http://www.downforeveryoneorjustme.com/blog.jdpfu.com](http://www.downforeveryoneorjustme.com/blog.jdpfu.com) says it is up. If you PM me, we can troubleshoot.

---

### Post by Bucky Ball on 2014-07-13
Please troubleshoot on the thread so others may share, learn and contribute. Thanks. ;)

---

### Post by coldraven on 2014-07-13
Log into your router using a browser, my router is at [http://192.168.2.1/](http://192.168.2.1/)
Check that you are connected, you will see something like 
[TABLE="class: tabdata, width: 760, align: center"]
[TR]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD="width: 80, align: center"] [COLOR=#000000]Downstream[/COLOR][/TD]
[TD="width: 80, align: center"] [COLOR=#000000]Upstream[/COLOR][/TD]
[TD="width: 280"] [/TD]
[/TR]
[TR]
 [TD="class: light-orange"][/TD]
[TD="class: light-orange"][/TD]
[TD][RIGHT] [COLOR=#000000]SNR Margin[/COLOR][/RIGHT]
[/TD]
[TD][CENTER]:[/CENTER]
[/TD]
[TD="width: 80, align: center"] 20.0 [/TD]
[TD="width: 80, align: center"] 24.0[/TD]
[TD]db[/TD]
[/TR]
[TR]
 [TD="class: light-orange"][/TD]
[TD="class: light-orange"][/TD]
[TD][RIGHT] [COLOR=#000000]Line Attenuation[/COLOR][/RIGHT]
[/TD]
[TD][CENTER]:[/CENTER]
[/TD]
[TD="width: 80, align: center"] 23.0 [/TD]
[TD="width: 80, align: center"]  11.0 [/TD]
[TD="width: 280"]db[/TD]
[/TR]
[TR]
 [TD="class: light-orange"][/TD]
[TD="class: light-orange"][/TD]
[TD][RIGHT] [COLOR=#000000]Data Rate[/COLOR][/RIGHT]
[/TD]
[TD][CENTER]:[/CENTER]
[/TD]
[TD="width: 80, align: center"]  8128 [/TD]
[TD="width: 80, align: center"]   448 [/TD]
[TD="width: 280"]kbps
[/TD]
[/TR]
[/TABLE]

The data rate shows that I am connected to my ISP.
Then check that your router has got an IP address, probably something like 217.123.123.123
It gets this address from your ISPs DNS server and sometimes they go wrong, in which case you will only see 0.0.0.0.
My ISP has had this problem several times, usually at the weekend when there is no tech support :(
But you can fix it!
Find the DNS section in your router and change it from "Automatic" to something similar to"User Discovered".
Then put 8.8.8.8 in the "Primary DNS server" field.
Then put 8.8.4.4 in the "Secondary DNS server" field, remember to click "Save".
These are Googles public DNS servers and you should now be back online.

When I eventually got tech support from my ISP I asked them to give me the IP of their DNS server so I now have this as "Primary" and Google's 8.8.8.8. as "Secondary".
That way when my ISP fails it automatically will use Googles. I believe that DNS servers are sometimes hacked or DDOSed which explains why they fail.

---

### Post by TheFu on 2014-07-13
> **Bucky Ball said:**
> Please troubleshoot on the thread so others may share, learn and contribute. Thanks. ;)

The issue reaching my blog is likely due to firewall filtering against abuse and NOT something anyone other than the firewall manager can solve.

Switching back to the steps from the blog article ... it contains systematic commands, in a specific order, to check for 
a) local connectivity via IP
b) internet connectivity via IP
c) internet connectivity via DNS
d) odd routing issues due to multiple interfaces being enabled (wifi AND wired ethernet)

In the end, the "my network doesn't work" root cause can be determined quickly.  
To many end-users, **my network is down** is really that DNS isn't working and their "network" (in the pure sense) is just fine.
Does that make sense?

---

### Post by TheFu on 2014-07-13
It is possible that we are confusing the modem and router terms.
Also, there are privacy concerns in using Google's DNS, but for a short time, I wouldn't worry too much in using it.  There are tools available to find the fastest DNS for your specific location. Over time, these change.  

Sadly, these tools cannot determine how trustworthy and DNS provider is.  Just realize that DNS is the backbone of HTTPS/SSL security, so if the DNS server is not returning 100% true and correct results, then your financial data from any online transaction is at risk.

So - we need for Colin to report back after running a few commands.

---

