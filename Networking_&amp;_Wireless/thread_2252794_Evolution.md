---
title: "Evolution"
date: 2014-11-14
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2014-11-14
On my desktop at work, I am running Ubuntu 10.04 LTS with evolution 2.28.3. Everything worked fine up until yesterday. 

Through evolution, I access half a dozen or so POP email accounts - four bellsouth.net accounts and three 1and1.com accounts. The bellsouth accounts are downloading and sending just fine. However, when I try to send or receive mail using the 1and1 accounts, I am getting a "Error while Fetching Mail. Failed to read a valid greeting from POP server pop.1and1.com" error message.

I went round and round with 1and1 yesterday quadruple checking server and port settings, rebooting everything except the refrigerator and nothing helped.

The reason I am asking for help here, though, is because I tried accessing the same accounts with the same server and port settings from my laptop using the same network connection and... it works fine. The only difference is that the laptop is running Ubuntu 12.04LTS instead. That tends to indicate an issue with Ubuntu/evolution. 

ANY help would be great, because I REALLY need to access those accounts on my shop computer. And I know that 10.04 is outdated, but outdated should mean that it just stops working - or that updates break it.

---

### Post by kc1di on 2014-11-15
just a possibility - Double check to make sure your security settings in evolution on those 1&1 accounts is correct for the server.
I had a similar problem and found out that the default security setting on those accounts was wrong for their server. 
Good Luck

---

### Post by rebeltaz on 2014-11-15
SSL/TLS and such? Yeah... I triple checked those, too. This seems to be something related to an update that was pushed to the system. I swear I want to think that all of this started after I let it do an update :( 

Thanks, though...

---

### Post by rebeltaz on 2014-11-25
OK... so please explain this... 

I was able to get the mail to work by changing the security settings to TLS ... BUT... my laptop still works fine using SSL - which is what 1and1 TOLD me to use. So why can my desktop not log in with SSL like it is supposed to / used to?

---

