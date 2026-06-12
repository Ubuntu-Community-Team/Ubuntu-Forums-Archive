---
title: "How do I get stated DSL speeds"
date: 2017-07-22
forum: Networking &amp; Wireless
---

### Post by SuperFreak on 2017-07-22
I have just upgraded my dsl from 6Mb/s to 15 Mb/s. I ran both OOkla speedtest and Google speed test and both show I am only getting 12 Mb/s. I took an image of my TP W8970 Modem/Router status which seems to show I am getting over 14Mb/s. What is causing the discrepancy?

---

### Post by wildmanne39 on 2017-07-22
There are always differences because of server traffic, distance to the server from your computer etc, in my opinion that difference is small and quite normal, nothing to be concerned about.

---

### Post by lisati on 2017-07-23
^^^This.

I just checked, and I should be able to get 13Mb/s, and the speedtest.net results seem to confirm this. On the rare occasions I download something, it seldom utilizes the full capacity of the connection.

---

### Post by SuperFreak on 2017-07-23
So from the image I attached is my download rate at the modem 14268 kb/s and it declines from there to the computer a foot away to 12Mb/s as tested online at Ookla Speed Test? I don't understand why this is

---

### Post by wildmanne39 on 2017-07-23
If this is a wifi connection do the following so we can see what is going on if you have to be that close there is an issue.

Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by SuperFreak on 2017-07-23
No it is hard wired by ethernet. I am just surprised that I would lose nearly 2.3 Mb/s speed  and wondered if it is a faulty connection between the PC and the modem (bad ethernet connection) or something. Also I booted to both Ubuntu and Mint and Mint is getting 12 Mb/s and Ubuntu 10.3 Mb/s. I am not sure if this is just coincidence but I did the tests on Ookla about 5 minutes apart.

---

### Post by wildmanne39 on 2017-07-23
It sounds like your ethernet cable may be bad. That is really all I can tell you  about your issue.

---

### Post by SuperFreak on 2017-07-23
Thanks, I tried a new ethernet cable I had and it made no difference. I guess I have to accept it the way it is.

---

### Post by johndough2 on 2017-07-24
Hi

You seem to have ADSL, not DSL according to your thumbnail.

Your max is shown as 14592, so do you divide by a thousand or a thousand and twenty four?

14592 is either 14.59 or 14.25 neither of which is actually 15.

So I think you are of the mindset to accept the amount you are getting and realise the ISP has probably rounded up and uses base 1000 for their calcs/promises.

Off topic slightly, but the speed is constant, fibre optic uses the speed of light and copper achieves 90+% of that. 
What changes is the frequency, the higher the frequency the "higher the speed".  
Another factor is the distance to the speedtest server, try a ping to your nearest and one the other side of the globe.

Ping 8.8.8.8 at various times and note the values, depending on your contention ratio and 'busy' times expect some wide variations.  Mine varies from 13 milli-seconds to 19 milli-seconds.

Therefore less packets get delivered at 19 m/s intervals than 13 m/s intervals per second (53 to 77) , quite a big % variation in actual usage, rather than the quoted/paid-for from my ISP.

---

### Post by vocx on 2017-07-24
> **SuperFreak said:**
> No it is hard wired by ethernet. I am just surprised that I would lose nearly 2.3 Mb/s speed  and wondered if it is a faulty connection between the PC and the modem (bad ethernet connection) or something. Also I booted to both Ubuntu and Mint and Mint is getting 12 Mb/s and Ubuntu 10.3 Mb/s. I am not sure if this is just coincidence but I did the tests on Ookla about 5 minutes apart.
You seem to think the speed tests by Ookla or Google are scientifically accurate ways to measure the speed of your Internet. They are not.

> **wildmanne39 said:**
> There are always differences because of server traffic, distance to the server from your computer etc, in my opinion that difference is small and quite normal, nothing to be concerned about.

As mentioned by others, the speed of the connection depends on a lot of things, including server used for the tests, current network traffic, quality of the physical connection, interference, size of packets, etc. There are just too many variables. The speed advertised by your provider is just an average, and if you check your contract they may even indicate that the rate should be around 70% of the advertised rate during peak hours. So if you "pay" for 15 Mbps, and get 12 Mbps that may be totally "normal".

Also, you cannot trust the data reported by your modem. Your modem connects directly to the Internet service provider's servers, so they may actually give preference to these tests so they report good values. It's like asking a restaurant's owner whether the food in his establishment is good, "of course it is!", he will say.

So, don't worry too much about those 3 Mbps difference. Unfortunately you cannot do much about it. You can only talk with your wallet, so if you are not satisfied with the rate you are getting you should change service provider.

---

