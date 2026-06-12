---
title: "login issues with gmail,youtube on ubuntu 10.10"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by converge2ashish on 2011-02-05
Hi,  I am novice to Ubuntu 10.10. I am unable to login to orkut,youtube account in firefox 3.6.13 under Ubuntu 10.10. I am giving the correct authentication. Same is working under windows xp.  I guess the problem might be with Java. I have already installed the java plug in. When I type about: Plugins in url, I can see Java(TM) Plug0in 1.6.0_22.I have also installed JDK and other avilable stuff from canonical partners.   Even when I tried to submit this thread from ubuntu 10.10, I was unable to do so. So I am posting this from windows XP.  Please take a look. If you could suggest some pointers that would be great.  Thanks for your time, Ashish

---

### Post by zkriesse on 2011-02-05
You mentioned YouTube, can you not visit the site? Or rather, can you not see the site content?

---

### Post by converge2ashish on 2011-02-06
Hi zkriesse, I am able to visit youtube and see the content of the site.
I am facing issues when I am trying to login to the site using my credentials.

Thanks,
Ashish

---

### Post by peculiar penguin on 2011-02-06
The problem isn't Java (none of sites mentioned use it AFAICT), it's  your browser not accepting or storing cookies. Either cookie support is  turned off (in Firefox check Extras > Options... > Privacy, you can either turn it on globally OR define an exception for the sites you want) or the browser profile is broken (open a terminal, run "firefox -P" to open the profile manager, create and use a new profile there).

---

### Post by converge2ashish on 2011-02-09
Hi peculiar penguin, Cookie option is already enabled. Still is not working.
Thanks.

---

### Post by converge2ashish on 2011-02-12
Hi Guys, Finally I am able to pin point the problem. In firestarter firewall settings I checked enabled ICMP filtering which was not allowing some sites to work. I un-checked that option and sites are working again.

Thanks for time.

---

