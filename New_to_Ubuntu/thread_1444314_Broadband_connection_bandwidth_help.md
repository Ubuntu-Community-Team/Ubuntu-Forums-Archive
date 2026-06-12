---
title: "Broadband connection bandwidth help?"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by karthick87 on 2010-04-01
My friend who has broadband connection can use his connection free upto [COLOR=Red]1GB[/COLOR]  per month,after that he is charged..Is there any program or script to block internet usage after a particular bandwidth?

---

### Post by Nisal on 2010-04-01
some download managers have that option

---

### Post by Rushyang on 2010-04-01
Hi..! though I may not suggest anything for you because I've ubuntu's experience just for 2 days now.. and I already googled whatever I needed.

I've the same problem as your friend has, I can use just 2.5 GB/month. 

I googled it and I found that "gkrellm" is good for tracking the network usage.

It is might be installed as.. 
> sudo apt-get install gkrellmin the terminal.

Although, I found that widget pretty annoying because It is little confusing to set it up for pppoe usage details.

Also, i found some bandwidth monitor tools here..
> [http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

I hope that helps. Thanks.

---

### Post by cascade9 on 2010-04-01
1GB a month?!!?!?!?!!! 

Thats just way to small IMO. I was doing 3GB+ a month on dialup.....

Edit- how much are the charges per GB after the 1GB?

---

### Post by aeiah on 2010-04-01
vnstat tracks bandwidth usage over periods of time. 'vnstat -m' will give you a monthly breakdown including current usage for the month, and estimated usage for that month.

within the vnstat config file you can set the max bandwidth, or you may want to find a shell script that'll give you notifications when you get to 900mb or something rather than turning the interface off.

---

### Post by karthick87 on 2010-04-01
After 1GB he has to pay 1Rupee Per MB.

---

### Post by cascade9 on 2010-04-01
> **getyourkarthick said:**
> After 1GB he has to pay 1Rupee Per MB.

Thats not bad. Not great to have to pay for going over, but its better than australian ISPs- 1Rupee = $0.025 au, the ISPs here excess charges range from $0.50 a GB up to $180 a GB. 

I know of several people here who have internet conenctions that charge for excess use and have recived some huge bills- one case was over $1000 .au in one month. (a lot of ISPs throttle you down to a lower speed if you go past your maximum usage, that is what my ISP does).

---

