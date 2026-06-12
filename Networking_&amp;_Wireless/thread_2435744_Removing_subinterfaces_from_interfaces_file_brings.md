---
title: "Removing subinterfaces from interfaces file brings them back upon reboot"
date: 2020-01-25
forum: Networking &amp; Wireless
---

### Post by sdewan on 2020-01-25
I am not very experienced with ubuntu and trying to remove some subinterfaces within ubuntu. However, every time I remove the subinterfaces by running "sudo nano /etc/network/interfaces" command, these interfaces come right back.
Ubuntu version: 12.04.5 LTS
Then, I found this command "IP link show" which showed that these interfaces are in UP state. So, I ran "sugo ifconfig eth.300 down" to bring these links down.
However, everytime I restart my ubuntu server, all the subinterfaces I've deleted come back.
How can we permanently delete these sub interfaces?

---

### Post by wildmanne39 on 2020-01-25
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by guiverc on 2020-01-25
Ubuntu 12.04 LTS is EOL ([http://fridge.ubuntu.com/2017/05/01/ubuntu-12-04-precise-pangolin-end-of-life-reached-on-april-28-2017/](http://fridge.ubuntu.com/2017/05/01/ubuntu-12-04-precise-pangolin-end-of-life-reached-on-april-28-2017/)); being released in 2012-April (thus 12.04) with 5 years of supported life.

If you're using Ubuntu 12.04 ESM, I'd suggest using your Ubuntu Advantage support options, otherwise I'd suggest you move to a supported release of Ubuntu.  

The normal *release-upgrade* path for 12.04 upgrades is to 14.04 LTS; however it's also now EOL; so a re-install may be necessary.

Ubuntu LTS releases come with 5 years of support; so 12.04 was supported until 17.04 (or 2017-April) unless extended using ESM.

---

