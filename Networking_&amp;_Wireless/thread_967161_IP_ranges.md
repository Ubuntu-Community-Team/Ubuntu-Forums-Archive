---
title: "IP ranges"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by lionheartxxi on 2008-11-01
Hi Ppl.  I have installed moblock and now im trying to add ip addresses, only thing is they are in ranges.  Its to allow moblock to connect to steam servers.  for example the first one is 63.98.16.176 to 63.98.16.183.  Would 63.98.16.0 allow those as its the network ID.  I hope i dont look like a total noob.  I hope their is someone who can advise me further.  Thanks in advance!!!

---

### Post by lionheartxxi on 2008-11-01
i suppose i could just remove valve corporation from the blocklists couldnt i?

---

### Post by lionheartxxi on 2008-11-01
bleh but suppose everytime it updates it will just add it again.

---

### Post by lionheartxxi on 2008-11-01
sorry for wasting your time, something as simple as putting valve corporation in the whitelist allowed connectivity.  Sorry for the trouble.

---

### Post by lionheartxxi on 2008-11-01
dam it actually stopped moblock from running at all ffs. very frustrating.

---

### Post by jre on 2008-11-03
In your other thread [http://ubuntuforums.org/showthread.php?t=967139](http://ubuntuforums.org/showthread.php?t=967139) you already got the answer. Using the allowlists from iblocklist.com is the recommended way.

Still:
To permanently remove certain lines by keyword use the  IP_REMOVE in /etc/moblock/moblock.conf (or better /etc/default/moblock). These lines will be removed then after every update/reload.
If you tell us what you did we might tell you why moblock isn't working anymore.
"moblock-control status" , "moblock-control show_config" and the logfiles might provide further usefull information.

---

### Post by jre on 2008-11-03
Edit: deleted double post

---

