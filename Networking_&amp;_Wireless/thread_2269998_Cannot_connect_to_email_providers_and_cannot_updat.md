---
title: "Cannot connect to email providers and cannot update"
date: 2015-03-19
forum: Networking &amp; Wireless
---

### Post by scorbetta on 2015-03-19
Dear all, 

I have an x86_64 laptop on which I installed Ubuntu 14.04.2 LTS with kernel 3.13.0-46-generic. I never had problems with my wireless connection, but I suddenly started having issues a couple of weeks ago. In particular the following happens (I use Firefox as default browser, tried also with Opera):

- I can access with no problems *some* websites
- I cannot access gmail: "Secure Connection Failed"
- For some websites (e.g., hotmail) I got: "Application Blocked... in accordance with company policy". However, I asked my company and they didn't make changes to the network and indeed I never had problems so far
- I cannot do apt-get update since I got a lots of "^Ign" and "^Err" rows and "  503 Service Unavailable"
 
Any ideas?
Thanks

Cheers
S

---

### Post by scorbetta on 2015-05-18
So, anyone with a solution so far??

---

### Post by corti-nico on 2015-05-18
> **scorbetta said:**
> So, anyone with a solution so far??

Maybe you're having problem with system date and SSL (this cause your site browsing problem).
Can you check your system date with command:
```
date
```
In a terminal and let us know

---

