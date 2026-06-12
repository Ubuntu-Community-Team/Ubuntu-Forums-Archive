---
title: "[SOLVED] Slow/No Internet Access via Firefox when running torrent client"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by taecha on 2008-07-24
I am experiencing extremely slow or even no internet access via Firefox when running torrent clients although my total bandwidth is hardly used. If have tried both Transmission and Deluge. As soon as I stop the downloads on the torrent client, everything's back to normal in Firefox.

I am running Ubuntu 8.04, Transmission 1.06 or Deluge 0.9.03 and Firefox 3.0.

Any suggestions and solutions?

Thanks.

---

### Post by Monkeon on 2008-07-24
I've experienced something similar on my windows box.  I'd start off by trying to figure out whether this is a software or hardware issue.  Does the slow down occur immediately after you start up the torrent client?  If it seems to get gradually worse, I'd say that indicates it could be some kind of jam in the router....torrents can use LOTS of connections and some routers don't get on so well with that....!  If you have a decent router, you might be able to configure it to cope better.

If the slow down is pretty instantaneous, it's probably a software thing....I'd probably try using a different browser to see if that makes a difference...

---

### Post by timcredible on 2008-07-24
how do you know your bandwidth isn't being completely used?

---

### Post by taecha on 2008-07-24
@Monkeon: I think it actually gets worse over time. Do you know what has to be tweaked to have the router cope better with the traffic? I connect through a Linksys WRT54GL router.

@timcredible: I run the netspeed applet which shows that I only use a fraction (around 25%) of my usual bandwhidth (as provided by my ISP and measured through speedtest.net)

---

### Post by earthmeLon on 2008-07-24
To help my router 'better cope' I installed DD-WRT on it.  It's seems more efficient and you can make some modifications that will help your network out with BT traffic.

Also, try disabling DHT (I think that's what it's called) and peer exchange.  That seems to help a bit, as well.

---

### Post by Monkeon on 2008-07-25
Like earthmeLon said, you'll probably need to put the Tomato or DD-WRT firmware on to your router.  That will give you options to let you limit the number of active connections and reduce the timeout of inactive connections etc.  There are tutorials knocking about online that give more details...

---

### Post by taecha on 2008-07-25
I have played with my router but that didn't change anything. Also, I found that downloads through Firefox are still fast. Hence, it's only the websites that load slowly or not at all. It might thus not be a router problem at all. Could it be a problem with FF?

---

### Post by AmericanYellow on 2008-07-25
I had the same problem. I discovered that my ISP was 'throttling' my connection. You might be in the same situation.

Because torrenting has become very popular and common, ISPs aren't able to handle the massive traffic. Their solution is to limit both your download and upload speeds. What pisses me off is that the ISP will never tell you.
I found out my ISP was throttling my connection because once they started, my XBOX live Halo gameplay would lag and continually disconnect. I called my ISP and the Rep told me that the traffic from my house is excessive.
Now that people are learning about this and complaining, my ISP announced that are going to stop throttling and start charging excessive traffickers an extra fee every month. They say the extra cash will allow them to expand so that they can handle more traffic.:mad: They already have capacity to expand:mad:.

Anyway, I moved out from home for a year and lived on my schools campus. Now that I'm home a year later, my connection is faster than ever. I've started torrenting again though. They will soon slow me down. I don't really care because I'm headed back to school in a month. :)

---

### Post by taecha on 2008-07-25
> **Monkeon said:**
> There are tutorials knocking about online that give more details...

do you have the links handy?

@AmericanYellow:

this sounds like a plausible cause. Although, it still would not explain why websites load slowly or not at all in FF, would it?

I had Tor and Privoxy installed earlier but removed them to see whether it would change anything. It didn't. Could they have altered any system settings that are causing this problem?

---

### Post by AmericanYellow on 2008-07-25
> **taecha said:**
> do you have the links handy?

@AmericanYellow:

this sounds like a plausible cause. Although, it still would not explain why websites load slowly or not at all in FF, would it?

I had Tor and Privoxy installed earlier but removed them to see whether it would change anything. It didn't. Could they have altered any system settings that are causing this problem?

It does explain why websites would load slowly or not at all.

Because the ISP is reducing your available bandwidth, in additional to the whatever torrent client are you using consuming the remaining bandwidth, any other application like Firefox will not be able to function properly due to lack of bandwidth. Thus, pages will load very very slowly or in most cases, a webpage will load so slowly that Firefox will timeout and nothing will load.

*Note that most, if not all torrent clients are bandwidth hogs and that is how they are designed to achieve great upload/download speeds*

The reason why his speed test showed that he is only using a fraction of his bandwidth is because ISPs usually hide the fact that they are purposely slowly you down. As taecha said, 

"I run the netspeed applet which shows that I only use a fraction (around 25%) of my **USUAL** bandwhidth (**as provided by my ISP** and measured **through speedtest.net**)"****

That USUAL(100%) bandwidth that you think you have is reduced by ISP and there is no way for any speedtest to detect that your bandwidth is initially being reduced. The speedtest will then base its results on the USUAL(100%) bandwidth and it will appear that you are only using a small percentage. And in actuality, that small percentage which in taecha case is 25% is all the ISP is allowing him/her to utilize.

---

### Post by taecha on 2008-07-26
Thanks for your help everyone. Also, thanks to AmericanYellow for your thorough explanation. I have switched back to Transmission and noticed that at least torrent download speeds are better than with Deluge. Also, FF page loading seems to be somewhat faster. So, I will further investigate and see whether I can narrow down the cause.

To those guys who are experienced DD-WRT/Tomato users: is it possible to flash the router with the original firmware if need be?

---

### Post by earthmeLon on 2008-07-28
With DD-WRT you can revert back to the original firmware. I am not sure about with Tomato, but I'd bet you can. Be careful, It's like updating your BIOS;  One wrong move could send you back to buy a new router :D  That being said, I seriously believe the benefits outweigh the risks.

GL :D

---

### Post by taecha on 2008-07-29
I've followed earthmeLon's and Monkeon's advice and installed a new firmware on my router. After reading various forums I went for Tomato since it seems to be more user-friendly than DD-WRT.

Guess what? I can surf the net again while downloading and torrenting - and that even **without** activating QoS! And my torrent speeds have also improved.

Thanks for the tip, guys. Works well for me!

---

### Post by earthmeLon on 2008-07-29
Glad to hear it worked out.  One thing you might want to tweek is your UDP/TCP Timeouts.  I think mine are at 300.

---

### Post by taecha on 2008-07-29
I only problem left is that I seem not to be able to get CIFS working. Any experience with that?

---

### Post by asnd16 on 2008-11-04
ok I never had the issue till I installed ubuntu 8.10 and when deluge is running I get the same issue.  I am running dd-wrt and am tempted to prioritize the firefox so it can have the internet priotity then deluge.  I also lowered the number of IP connections availible.     I unchecked DHT and that helped with the page loading but I dont think it helps with the speed of the torrent.  Im pretty sure my internet is not thorottling or at least if they are it is something new. 

NOW what was your overall solution . . . Like I stated I have never had the issue before I installed 8.10

---

### Post by dmizer on 2008-11-04
> **taecha said:**
> I only problem left is that I seem not to be able to get CIFS working. Any experience with that?

Please see the second link in my sig. :)

---

### Post by taecha on 2008-11-04
@asnd16:

I am running Ubuntu 8.04, so I can't really comment on why you experience a slowdown after the upgrade. However, all I did was installing Tomato on my router after which everything worked well even without activating QoS!

Two things come to my mind:

1. What **version** of deluge are you running? Because I experienced problems after installing the latest version (back then 0.9.x) of deluge from their website. Subsequently, I had downgraded to the version provided in the Ubuntu repos, i.e., 0.5.8.9 after which things worked smoothly. I have installed deluge 1.0.4 only a few days ago. While I do **not** experience network slowdowns or a slower FF I have noticed **considerable strain** on my CPU which I did not when running deluge 0.5.8.9. Hence, *I expect deluged to cause some if not all of the problems*.

2. Try using transmission or any other torrent-client to see whether the problem persists. In my case, performance was better with transmission. This again should show whether the problem is caused by deluged as I believe.

Hope this helps.

---

### Post by taecha on 2008-11-05
I have downgraded to deluge 0.5.8.9 yet again. CPU load has dropped from a continuous 100% alternating between cores to a normal load. And download speed has more than doubled! Hence, I believe something's wrong with deluged and/or its integration in Ubuntu.

My advice: stick with the current deluge-version from the Ubuntu repos.

---

