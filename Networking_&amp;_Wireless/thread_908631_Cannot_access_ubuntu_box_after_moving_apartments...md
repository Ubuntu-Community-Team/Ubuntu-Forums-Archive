---
title: "Cannot access ubuntu box after moving apartments...huh?"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by krelkor on 2008-09-02
Just moved apartments, and tried to hook up my headless server to my router and access some movies off my laptop wirelessly since i am without internet for the next few days. I cannot get access to the box from my windows laptop. I can ping the box using tracert, but i cannot SSH in with putty, or access directly by either hostname or ip address. 

Nothing has changed from moving apartments, it is the same cable, same port on router, same laptop, same IP address. The only difference is that my deskop PC is not on the network right now as it is still in storage. 

So I have a hypotheses:

My desktop with windows XP has the same user name as my ubuntu box. Have i messed up permissions somehow in ubuntu to only allow  access to the box once the desktop has signed into it(that doesnt really make much sense... but im out of ideas). 

Thoughts?

---

### Post by NadmanET on 2008-09-02
Sounds like for whatever reason some of your services didn't get loaded when it booted back up.  If you can ping it and not access through SSH I would plug in the console and start troubleshooting it.  Good luck!

---

