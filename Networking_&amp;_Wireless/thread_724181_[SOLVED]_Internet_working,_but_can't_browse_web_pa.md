---
title: "[SOLVED] Internet working, but can't browse web pages"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by kmano8 on 2008-03-14
I can connect to synaptic and pidgin, but get an "unable to connect" in firefox and opera.  I'd copy my ifconfig, but can't since I'm posting from another machine..  any ideas?

Also, when I went to check my properties for eth0 (wired connection), it was set to "enable roaming mode".  This seems wrong, so I unchecked that and set config to DHCP (which I'm pretty sure is where it always was).  I'm connecting through the standard linksys 54g wireless router.

---

### Post by Zafrusteria on 2008-03-14
Have you tried setting the DNS setting from your ISP in the wired connection parameters on Ubuntu?

---

### Post by kmano8 on 2008-03-14
there are two entries in dns servers... 68.87.64.146 and 68.87.75.194  I'm on comcast.

---

### Post by kmano8 on 2008-03-14
If other services requiring the internet work, why is it just web browsing?

---

### Post by ittiam on 2008-03-14
Is it too slow or you are just not able to get anything?

---

### Post by kmano8 on 2008-03-14
Solved... my mobloquer was updated last night and it reset the exceptions list.

---

