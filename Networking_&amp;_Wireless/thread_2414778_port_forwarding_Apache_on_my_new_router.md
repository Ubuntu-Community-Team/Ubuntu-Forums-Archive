---
title: "port forwarding Apache on my new router?"
date: 2019-03-14
forum: Networking &amp; Wireless
---

### Post by garyed on 2019-03-14
I just switched my service over to Spectrum & can't get my Apache server port forwarding to work. I still have it working on my old Frontier router but the port forwarding settings are a little different & I'm not sure if I'm doing them right or my ISP is blocking me. I called Spectrum & they said they don't block but they can't give me any specifics on how to get it to work. 
My router is  Sagemcom Fast 5260.  I don't know if my internal & external hosts & ports are correct or if there is something else that I'm missing that also needs to be set.
Any help appreciated.

---

### Post by garyed on 2019-03-14
A little update:
I used an online port checker & it shows port 80 is open when I type in my ip address so it looks like Spectrum is not blocking port 80. Just to test, I deleted my above port forward rule on the router & then it showed my port 80 was blocked when I typed in my ip address so the above port forwarding is definitely opening port 80. I just can't connect to my Apache server. I can't figure out what is not set up right because if I plug into my old Frontier router which is still active & type in my correct ip address my Apache server will come up fine. Apache just won't work with my new Spectrum router & new ip address even though port 80 is open. Is there anywhere in Apache config files that might store my external ip address?

---

### Post by garyed on 2019-03-19
Not that anyone was interested but after hours on the phone with 5 different tech support guys & a couple days, I finally found out that I never had a problem to begin with. It seems my home Apache server had been working all the time but the only catch was I couldn't access it using my external ip address while I was connected to my home router. For some reason Spectrum's router will not let any ip address that it gives out to access the same router using the external ip address. I've never seen that before but it's not any problem as long as it can be accessed outside of the home. Just in case anyone runs into this, I figured I'd put it out there.

---

### Post by Doug S on 2019-03-19
> **garyed said:**
> Not that anyone was interested but after hours on the phone with 5 different tech support guys & a couple days, I finally found out that I never had a problem to begin with. It seems my home Apache server had been working all the time but the only catch was I couldn't access it using my external ip address while I was connected to my home router. For some reason Spectrum's router will not let any ip address that it gives out to access the same router using the external ip address. I've never seen that before but it's not any problem as long as it can be accessed outside of the home. Just in case anyone runs into this, I figured I'd put it out there.Oh. That is actually very common. Here is another [current case]("https://ubuntuforums.org/showthread.php?t=2414980").

For my part of it, from your earlier posts, I did not realize this was the issue.

---

### Post by garyed on 2019-03-19
> **Doug S said:**
> Oh. That is actually very common. Here is another [current case]("https://ubuntuforums.org/showthread.php?t=2414980").

For my part of it, from your earlier posts, I did not realize this was the issue.

That's funny because I just noticed that other thread about an hour ago & posted my issue there too. The problem was when i explained my problem in this post I never knew that I could access my network all along from the outside. If I had seen the other thread first I would have checked my network from the outside which is something i never considered doing because I assumed it wasn't working.

---

