---
title: "thin client"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by tjrac on 2008-03-01
Hey Folks,

This is my first post and is probably too abstract but I'm hoping to cut to the chase.  I would like to set up a thin client environment in my home running ubuntu or edubuntu.  I have three old PCs and I would like to purchase a server.  It would be ideal to create an environment where I could integrate at least 1 XP box or run windows programs and integrate 1 MAC box or run MAC programs.  Is this achievable without being a rocket scientist?  Are there resources that anyone could point me to that would assist me in this endeavor?

Thanks!
Tom

---

### Post by Toet on 2008-03-01
LTSP (linux terminal server project) is what you seem to be looking for.

I did it once, and it's quite easy to set up Ubuntu thin clients.

[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

---

### Post by kesomir on 2008-03-01
If you weren't interested in games you could run windows in a virtual machine on the ltsp server and use a remote desktop client to access the windows install when you needed that functionality.

Virtualbox is a good one, it's fast and doesn't require keys (vmware is another that's popular but you need to visit a website to get a free key)

Just make sure to pick a mult-core computer with enough RAM for the server.

Office productivity and vanilla web run superb - lots of clients accessing flash games and linux games will make it crawl.

With three clients you prob won't notice it though and LTSP is superb - you can use edubutnu or install in on ubuntu.

---

