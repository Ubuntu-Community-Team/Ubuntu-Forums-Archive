---
title: "DHCP &amp; remote access, WOL"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by alanwalterthomas on 2009-05-28
My ISP changes my IP address every few hours & I want access to my computer wherever I am. Even if I could get a script that would send the current ip to my email every few hours I don't think I'd be able to wake on lan without knowing the ip address.
I imagine a solution exists somewhere since WOL is pretty useless if it only works for a few hours after checking your ip address.

---

### Post by yaroto98 on 2009-05-28
Try something like dynamicdns

---

### Post by alanwalterthomas on 2009-05-28
Thanks for the tip but I think there's still a problem.
They tell me to get an ip update client that runs on my computer & reports ip changes.
I'm no further ahead because I want to be able to turn the computer off & then use WOL. If the computer's off it can't be running the client.
Any other possibilities, or should I see if my ISP will give me a static ip address?
Thanks

---

### Post by alanwalterthomas on 2009-05-28
Never mind, I think I have a solution which works well enough for me.
My router has DynamicDNS so I should just have to set up the account with the online service then type the data into the DynamicDNS part of my router.
Thanks!

---

