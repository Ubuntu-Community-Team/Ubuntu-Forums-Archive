---
title: "Synchronize fonts between computers"
date: 2016-06-14
forum: Networking &amp; Wireless
---

### Post by fejoiwan on 2016-06-14
Hi everyone

The cloud sync app SpiderOak is changing it's price policy - they're cancelling their free plan. So I've got the same problem again I had back when Ubuntu One went offline.

I need something to keep the fonts on my laptop and my desktop computer synchronized. With Ubuntu One and with SpiderOak I could just sync the ~/.fonts folder and everything was fine. But it's quite hard to find an alternative that runs on Linux and let's you sync any particular folder in your home dir. 

Any ideas?

---

### Post by David_Wright on 2016-06-14
> **fejoiwan said:**
> Hi everyone

The cloud sync app SpiderOak is changing it's price policy - they're cancelling their free plan. So I've got the same problem again I had back when Ubuntu One went offline.

I need something to keep the fonts on my laptop and my desktop computer synchronized. With Ubuntu One and with SpiderOak I could just sync the ~/.fonts folder and everything was fine. But it's quite hard to find an alternative that runs on Linux and let's you sync any particular folder in your home dir. 

Any ideas?
You could look into **Syncthing **(or **Unison**, which is slightly more simple/manual) for this purpose - the key factor for both of these being that both computers need to be on at the same time in order to sync because they are not "cloud" based.

I haven't used Syncthing, but have used Unison and it works well for my limited requirements.

---

### Post by fejoiwan on 2016-06-14
Thanks David_Wright, the thought has crossed my mind. I guess I could even use rsync to some extend since I usually install fonts on my desktop first. The trouble is, I rarely have both computers running at the same time - my laptop is quite crappy, so I use the desktop for everything when I'm at home.

So I'm really looking for something cloud based here. Anyone got anything?

---

### Post by fejoiwan on 2016-06-14
Ok, I guess I was a bit impatient when searching. After having another look, I stumbled upon pCloud ([https://www.pcloud.com/](https://www.pcloud.com/)) which seems to do the job quite well at first glance. Hadn't had much time to test it though. It even looks cleaner and more polished than SpiderOak. So everyone having the same problem: I strongly suggest you have a look at that.

---

