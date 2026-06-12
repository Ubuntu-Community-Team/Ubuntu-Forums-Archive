---
title: "Network only in roaming mode"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by jcats on 2008-01-06
I just installed Gutsy on my HP dv 9000 laptop. During install (using the Alt. install), the DHCP was successful. But I can only connect to the internet in roaming mode. While I can get the internet , I cannot ping or see my wired Linksys router or my other 2 PC's (both running Gutsy). If I set the network to DHCP, I get no internet at all.
 
My other PC's can see each other, so I figured I need to get the laptop to work in DHCP. I am new to Ubuntu and networking, so any advice needs to be simple.

Thanks;
jcats

---

### Post by stalker145 on 2008-01-07
> **jcats said:**
> I just installed Gutsy on my HP dv 9000 laptop. During install (using the Alt. install), the DHCP was successful. But I can only connect to the internet in roaming mode. While I can get the internet , I cannot ping or see my wired Linksys router or my other 2 PC's (both running Gutsy). If I set the network to DHCP, I get no internet at all.
 
My other PC's can see each other, so I figured I need to get the laptop to work in DHCP. I am new to Ubuntu and networking, so any advice needs to be simple.

Thanks;
jcats

Checking the [Hardware Compatibility Page]("https://wiki.ubuntu.com/LaptopTestingTeam/HewlettPackard"), I didn't see anything for your specific model of HP, but it sounds like it is *possibly* a router configuration error. 

I know on my Linksys (WRT54Gv8 ) there is a spot (not on my network now so I can't be more specific) where you can separate the wired and the wireless from "seeing" each other. Are your other two computers wired? 

EDIT: Now that I look at the manual on the [Linksys Site]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C1&childpagename=US%2FLayout&cid=1166859837314&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3731477881L02"), it seems that that is for accessing the router wirelessly... I still wonder if that's the problem.

---

### Post by cameran on 2008-01-07
i have this exact same issue.  any ideas?

---

### Post by jcats on 2008-01-07
Thanks stalker; I followed the links you sent. Not much for my machine:-? All my machines are wired on the same Linksys router. Thanks for the effort,stalker.

Sorry, carmen, can't help you. But if I figure it out, I'll let you know

jcats

---

### Post by stalker145 on 2008-01-08
> **jcats said:**
> Thanks stalker; I followed the links you sent. Not much for my machine:-? All my machines are wired on the same Linksys router. Thanks for the effort,stalker.

Sorry, carmen, can't help you. But if I figure it out, I'll let you know

jcats

I would suggest that you call Linksys, but I know from experience that the moment you mention that you are using Linux, they will cease *any* effort in helping.

Did you check to see if your router was configured correctly? Maybe reset to default and start from scratch on the router?

---

### Post by jcats on 2008-01-10
Hey stalker;
My  router shows the laptop, and it gets an IP address,as do my PC's. It seems to me that this is a problem with my laptop, as this is the only computer that runs only in roaming.
Keep trying, I'm still open to ideas.
thanks;
jcats

---

