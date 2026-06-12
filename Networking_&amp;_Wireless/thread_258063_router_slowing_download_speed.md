---
title: "router slowing download speed"
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by Myomax65 on 2006-09-15
My Linksys WRT54G is slowing my download speed from 4800K -> 300K (tested using testmy.net). Uploads remain the same around 300K. I've determined the MTU, no help. I've even tried using my windoze machine. What gives?

---

### Post by ciscosurfer on 2006-09-15
When did this start happening; after any new installs, etc.  Need more info to troubleshoot this networking problem.  I would first make sure that the settings in your router haven't changed, that you don't have a loose plug (yes, this can happen and yes, it can affect download speeds).  If you're getting the same problem on your Windows machine (connecting through the same router), then it's a problem with your router setup/config...of course, your ISP could also be throtle'ing you down, but that's unlikely...there are any number of possible scenerios here...check the first suggestions then post back here.  Hope that helps you out.

---

### Post by Myomax65 on 2006-09-15
After trouble shooting some issues at work, I decided to run some tests at home to compare. I did not expect to see such low dl speeds (300k), so I bypassed the router and boom (4800k). So basically I discovered it by coincidence. As far as I know, it has been this way as long as I have had the service and the router, bought it new. This was my first broadband service so I was still pleased with the higher speeds vs dial-up. All the cables are secure. I've reset to default, but no change.

---

### Post by Fully216 on 2006-09-15
I have heard of people getting speedup by loading openwrt on their Linksys WRT54G routers.  Just a thought, you might want to consider switching/upgrading the filmware.  From what I understand, there is a lot of unnecessary overhead and it is poorly programmed 'out of the box'.  I know that everything except version 7.0 is supported.

See [http://openwrt.org/](http://openwrt.org/) for more details on the topic.

---

### Post by Myomax65 on 2006-09-15
Thank you all for your help. I ran a firmware upgrade which solved the problem. I'm back up to 4800k!

---

### Post by ciscosurfer on 2006-09-16
I should've thought of that (upgrading the firmware #-o) I'm glad you're back "up to speed!"

---

