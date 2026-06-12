---
title: "understanding DNS"
date: 2014-02-01
forum: Networking &amp; Wireless
---

### Post by Ubi_one_2014 on 2014-02-01
Hi

Could some one explaine the follwing issue

My ISP was down last sunday, so therefore i had no internet the whole day.

I own an NAS and a WDTVLive.
Both devices where not connected on the internet and/or home network after last sunday
the issue was DNS related.

For reasons unknown i changed the default DNS into the DNS servers from opendns in the NAS, and voila, it came back to the net :P

I did the same trick into the WDTVLive, and this reported back on the net imedeatly.

After a device reboot it conncted to the NAS and works like it always did

So, my question is, why default DNS failed to work, and opendns just works??

---

### Post by coldraven on 2014-02-01
The same thing happened to me last Saturday. My router showed that it was connected but no web-sites would load.
My ISP is a small company and they shut their office at the weekend so no help was available.
I changed the DNS settings from "Automatic discovery" to "User discovered" and put in Google's public DNS numbers. (8.8.8.8 and 8.8.4.4)
That fixed it and I was back online. On Monday I spoke to my ISP's technical support and was told that their DNS server had gone wrong. I have read that DNS servers are sometimes hacked to direct people to malware sites. I have no idea how this is achieved.
In my router I now I have my ISP's DNS address as the first option and Google's as the second. So if the first fails it should use the second address.
In a Discworld sort of way I guess that a DNS sever is a black box with a deamon and a load of phone directories inside. Maybe the deamon can be distracted sometimes :) I'm sure that someone will put us right.

---

### Post by Ubi_one_2014 on 2014-02-01
hi coldraven,

yes, it's very remarkble.
however, i am on a verry much big ISP over cable, and i can reach them 7 day's a week

---

