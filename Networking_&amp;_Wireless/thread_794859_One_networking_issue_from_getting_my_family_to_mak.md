---
title: "One networking issue from getting my family to make the switch"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by agim on 2008-05-15
The last hurdle, is the fact that at my family's home, the wireless connection sucks. I assume this is because of some quirk of the router, but I don't know.

If anyone could shed some light on this situation, it would be a big deal.

Honestly, I don't know where to start, other than to say that my wireless is very fast everywhere else.

Also, I use bcmwl5.inf with ndiswrapper.

Please help! So close to saving my family from the windows tax and all of the other crap that goes along with it!

---

### Post by dmizer on 2008-05-15
lots of questions here:

what router (make and model) are you using?
have you simply tried rebooting your router?
is your router located by the TV (if not, where?)?
do you get the same speed results when connected via ethernet?
what signal strength are you getting from the router?
same problem in windows?
does [disabling ipv6](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?) fix your problem?

---

### Post by agim on 2008-05-15
motorola sbg900 wireless surfboard gateway

I have tried rebooting my router, with no affect.

It is located by the TV, I am really interested in hearing why you ask.

Same speed through ethernet

Signal strength between 50-80 percent, depending on where I am in the house.

Windows is much faster, 2 or 3 x as fast.

I have turned off ipv6 in firefox and through ubuntu by adding a file called bad_list to /etc/modprobe.d with the line: alias net-pf-10 off. Which I read turned off ipv6. I see it is different than the method you linked to. I will try that as well.
Edit: No significant difference with the linked method of turning off ipv6.

Thanks

---

### Post by dmizer on 2008-05-15
tv's emit lots of RF, so if you were having problems with wireless but not wired, i would suspect that you were getting interference from the tv (which can sometimes happen).  if you're getting the same speeds through wired, and wireless, this is probably not the case.

peform a speed test in both ubuntu and windows: [http://www.bandwidthplace.com/](http://www.bandwidthplace.com/) and see if there is any difference reported in the speed test.

try using opendns: [https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

---

### Post by agim on 2008-05-15
Thanks for the help, I am going to look into OpenDNS. I will let you know if it works.

Edit: The difference when using openDNS is incredible! Thanks so much. This is unbelievable!

---

### Post by dmizer on 2008-05-15
> **agim said:**
> Thanks for the help, I am going to look into OpenDNS. I will let you know if it works.

Edit: The difference when using openDNS is incredible! Thanks so much. This is unbelievable!

fantastic.  glad we got you going.

---

