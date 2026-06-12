---
title: "Connecting to a wireless network with mac filtering problems"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by Tammo777 on 2008-10-26
I recently installed Ununtu 8.4 and updated it. I have my wireless driver working and can connect to some networks. I have problems connecting to any networks that have mac filtering enabled. I have checked my mac address and it is the same as the mac address placed in the lists on those networks. Has anyone seen this problem before? 

just to let you know, I'm running unbuntu on a dell 1525.

Thanks in advance,
stephen

---

### Post by issih on 2008-10-26
Can only think that maybe you have used the mac address of the ethernet port rather than the wireless card. If its not that then I'm at a loss for what's going on.

---

### Post by Pixtu on 2008-10-26
I too had a similar problem, although my problem was (I believe) also linked to the Belkin F5D6050 adapter I am using.

I was using Feisty (7.04) and everything was working. Then I found I could no longer connect with the router, even though I could see it. I am not sure but this might have been around the same time that we changed the router to mac filtering.

I then re-installed using Hardy (8.04) and still couldn't connect.

After much playing around I have been able to connect manually via the command line.

Have you tried to connect manually?

I can't say for sure which element caused the most problems for me and it might also depend on what adapter you are using, but if it works manually (command line) then there might be a problem with the network manager and mac filtering.

---

