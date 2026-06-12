---
title: "Web-based speed tests so different from speedtest-cli"
date: 2017-07-23
forum: Networking &amp; Wireless
---

### Post by akwusmc on 2017-07-23
I've looked around and I can't find information on this particular subject, though I admit my search-fu is limited.

Why are the results from web-based internet speed test results so much different than the results from speedtest-cli? The internet plan I have allows up to 100Mbps up and down. My computer uses a Gigabit card, though my router is only a 100Mbps switch (cheap emergency purchase). I've used Ookla's test (speedtest.net and speedtest.tvn.net) as well as testmy.net and the results are consistently 25-30Mbps down and 75+ Mbps up. But when I check with speedtest-cli I get download results that are significantly higher than the web-based results (around 80-85Mbps). Why is there so much disparity between results?

I'll admit that my hardware is hardly cutting edge and that my plan is the lowest tier (not to mention that the ISP has an automatic hedge with advertised speeds 'up to') but how can I argue my service is deficient when I can't even tell myself? Do browsers clog things up that much?

TIA

---

### Post by chili555 on 2017-07-23
Do you want to be confused even more? Test with Firefox and then Chromium!

Here are the test results I just ran on Chromium with wireless:

Ookla 259/301

Fast.com 240/-

speedtest-cli  235/153

dslreports  346/333

testmy.net  114/97

I think the answer is that each testing site uses slightly, and in some cases, vastly different methods to get the answer. If I toss out my highest and lowest, the remaining are pretty consistent and are what I believe.

---

### Post by akwusmc on 2017-07-23
> **chili555 said:**
> Do you want to be confused even more? Test with Firefox and then Chromium!

I don't even want to get into the differences between browsers!

My difficulty is that, using the test my ISP prefers (speedtest.tvn.net) I've never gotten a result over 50Mbps, and it's usually 30Mbps or less ... but upload speeds are consistently near my service level (100Mbps up and down). But I can't test via browser automatically over time (well, *I* can't) to develop a trend I can beat my ISP up over not getting the speeds I'm paying for.

But I CAN test with speedtest-cli over time with a cron job; the problem is that the command line test consistently shows my speeds to be near where I think they should be ... hardly what I want to show the ISP. So why the disparity? I understand graphics and advertising bloat but even that is data as far as the internet is concerned. Even when I've shutdown every other device in the house, cleared caches on my computer, completely shutdown and restarted before I run web-based tests I can't consistently get above 30Mbps. 

I'm not so much looking for a solution as for an explanation as to why this disparity exists, and does it make any difference.

---

