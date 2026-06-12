---
title: "cannot access google.com , youtube , any site with google apis ......"
date: 2014-02-08
forum: Networking &amp; Wireless
---

### Post by aban on 2014-02-08
I have **Ubuntu 12.04.4 LTS** installed,and use a wi-fi network router to connect to internet .But it seems I **cannot navigate my web browser to google.com nor to youtube or any site with google apis**. :confused: This doesn't appear to be a router setting -- I have two other Windows laptops on the same network, and they resolve google.com just fine.  It also doesn't seem to be a browser issue -- neither chrome nor firefox can navigate to google.com from my Ubuntu machine.All other websites I type in appear to load just fine. 

I have tried to ping 8.8.8.8 and it gets response but in the browser it does not display any page !!!
Any thoughts?  I'm just not even sure how to troubleshoot such an issue. 
p.s. - I am a beginner in using ubuntu . 
Thank You :)

---

### Post by praseodym on 2014-02-09
Check the browser settings if any proxy is in use. Also try using the Google nameservers:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by aban on 2014-02-09
Tried this but the page is still not opening . Can you pls tell me a different way ??

---

### Post by praseodym on 2014-02-09
Any router settings (check the manual)?

---

