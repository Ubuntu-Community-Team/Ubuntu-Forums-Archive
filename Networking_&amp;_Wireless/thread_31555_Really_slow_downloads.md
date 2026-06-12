---
title: "Really slow downloads"
date: 2005-05-03
forum: Networking &amp; Wireless
---

### Post by veritas366 on 2005-05-03
This may have nothing to do with Ubuntu but I thought some of you might have some things I could check to see where the problem lies.  

My download speeds are horrible.  I have a cable modem, thru a linksys router into a hub.  If I go to some "measure your download speed" freebie site, it has me at 1.5mbps as expected.  Reality is anywhwer from 100 - 300 kpbs.  Often it will start at around 300 and go down steadily till about 100.  Very often too, it will cut off before the download is even complete.

I also notice the collision detection light on in my hub.  While I think this is normal for big downloads, it seems that it is on quite a bit more than I remember.  

What can I check to rule out issues on my end before I call my ISP?

Edit:  just tried on my windows side to make sure it wasn't Ubuntu.  As I suspected, it is not.  

Second Edit:  Just called my ISP...they say I am getting 4% packet loss from their end pinging me.  When I ping out, I get no packet loss. How can I check for packet loss during downloads?

Thanks.

---

### Post by veritas366 on 2005-05-04
Well, no one seems to have any suggestions but I wanted to add some more info just in case someone wants to answer this post.  When I went to a speed test site, it has my download speed at 1.6mbps.  I NEVER get anywhere close to that.  Immediately after running that test, I found a random big file to download and it did the same thing...started at about 300kbps and then started to drop in speed immediately.  

My ISP said I had 4% packet loss...would that explain this behavior?  It seems odd that the speed tests always give me much higher than actual downloads.  (I've tried downloading files from several different sites, so I don't think it's on the server end.)  

I'd love som input.

---

### Post by veritas366 on 2005-05-05
Did I post this in the wrong forum?

---

### Post by lappy512 on 2005-05-05
ubuntu forums might not be the right place, but i think i can help. I have a connection from comcast rated at 4mbps. on the test site, 4.2mbps.

When I download, i get 2000KB/s thru firefox, then go down to about 520KB/s.

The reason is that most web browsers record using KB/s, even though sometimes they put them all lowercase. if you divide your connection (1600) by 8 (bits - bytes conversion), you get about 200KB/s, which is what you are getting. I get 4000/8 which is about 500KB/s. 

Conclusion: you are fine.

---

### Post by veritas366 on 2005-05-05
Now I'm getting it.  I also should be getting 4 mbps or about 470 kBps.  I'm not.  By the way, [www.testmy.net](www.testmy.net) is a great site.  Measures not only your speed but how it compares with the average of your ISP.

---

### Post by lappy512 on 2005-05-05
well, I can only tell you that it seems normal, because some of my friends who have Comcast get only 75 KB/s or about 600kbps.

according to your website, i get 9.5 Mbps or 1161 kB/s, but that's because that was my fast period.
I get a more accurate reading from [http://www.broadbandreports.com/stest](http://www.broadbandreports.com/stest)

---

### Post by veritas366 on 2005-05-06
>  	well, I can only tell you that it seems normal, because some of my friends who have Comcast get only 75 KB/s or about 600kbps.

according to your website, i get 9.5 Mbps or 1161 kB/s, but that's because that was my fast period.
I get a more accurate reading from [http://www.broadbandreports.com/stest](http://www.broadbandreports.com/stest) 

Well, your friends should complain.  I haven't quite figured it out, yet as far as the official advertised speed, but it is at least 3 but I think it is now 4mbps.  

At what is now about 140 kB/s I see a noticeable slowing...DSL would be faster.  At the speeds your friend is getting...he should get a dialup connection!

Just for the heck of it, I'm posting both tests from Broadbandreports test and testmy.net.

Here's testmy:

> :::.. Download Stats ..:::
Connection is:: 1106 Kbps about 1.1 Mbps (tested with 2992 kB)
Download Speed is:: 135 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (main)
Test Time:: Fri May 06 2005 07:15:40 GMT-0500 (CDT) 
Bottom Line:: 20X faster than 56K 1MB download in 7.59 sec 
Diagnosis: May need help : running at only 30.95 % of your hosts average (comcast.net) 

And Broadbandreports:

2005-05-06 08:21:33 EST: 1652 / 356
Your download speed : 1692214 bps, or 1652 kbps.
A 206.5 KB/sec transfer rate.
Your upload speed : 365396 bps, or 356 kbps.

Interestingly, they find this speed to be above the benchmark, so I don't know how they get the benchmark.  I would assume that benchmark would be based, at least in part, on the speeds that ISP's SAY they will provide...and I think 3 and even 4 Mb/s are the norm these days.  I suppose they are just taking the averages from what they measure, but that means there is a pretty big discrepancy among cable ISP's between advertised and provided rates.  

Not sure why Broadbandreports test is faster, though still I'm much slower than I'm supposed to be.

Here now, though in small print and hard to find, is the advertised speed rate:

> Speed comparisons are for downloads only and are compared to 768Kbps DSL and 56Kbps dial-up.  Maximum download speed of 4Mbps (or 6 Mbps) and upload speeds of 384Kbps (or 768Kbps) depending on the product that is selected.  Increased speeds not yet available in all areas.  Actual speeds may vary and are not guaranteed.  Many factors affect download speed. 

Of course, they have the old "your mileage may vary" clause, but if you call tech support they always say "we want to make sure you are getting the advertised speeds."

Anyway, all this is a bit of a digression.  I originally posted here, believing, correctly, that this was not a problem with Ubuntu but wondering if Ubuntu had tools to help diagnose.  Since I'm pretty sure this is an ISP problem and not my hardware (though I am going to hook everything up directly, without a router, just to check) I'll just wait for the tech to come this afternoon.

---

