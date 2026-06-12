---
title: "WPA2 at work, WPA1 at home with Intel 2915 wireless"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by wfroelich on 2008-01-08
Over the holidays I installed Gusty (7.1) on a Dell D810 an am struggling to get the wireless roaming working as expected.

I originally installed it at home and had some trouble connecting to my home wireless which was using WEP.   In troubleshooting that I switched it over to WPA1 and was finally able to connect from Ubuntu. 

Then when I got back into the office I tried to connect to the office wireless which uses WPA2.  It found the access point and I was able to enter the key and get connected.

Now comes the problem.  When I go home and startup the laptop it can see my home wireless (and many of the neighbors) but it won't connect.  One or two times I have gotten it connected at home but I cannot reproduce it.

After a bunch of playing around trying to get it working I'm at the  point where when I select it from the list it prompts for my key but then fails to connect and iwconfig for the interface shows Rx invalid crypt with a very high number.

I'm thinking it's confused between the WPA2 from the office and the WPA1 key I input when trying to connect.

Can anyone lend a hand getting this working?

Thanks,

--Bill

---

### Post by wieman01 on 2008-01-08
I just want to recommend an option called WICD:

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

It might do a better job.

---

### Post by wfroelich on 2008-01-09
UPDATE:

I tried a number of things including KevDog's troubleshooting tips and ended up uninstalling network-manager and network-manager-gnome and along removing security from my wireless router.

I was able to make a manual connection without encryption so I re-installed network-manager and network-manager-gnome and was able to connect.

Then I put a new WPA1 key on the wireless router and was prompted for it and it connected!

So while I can't say what fixed it, at least it is currently working.  I'll keep my fingers crossed that when I get into the office in the morning I can still connect there (WPA2) and again when I get back home in the evening without making other changes.

The only problem is that it wants to default to my neighbors router instead of mine but at least I can switch it over.

I'll post another update tomorrow.

---

