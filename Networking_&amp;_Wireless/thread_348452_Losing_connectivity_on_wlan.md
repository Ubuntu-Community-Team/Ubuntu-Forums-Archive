---
title: "Losing connectivity on wlan"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by malfist on 2007-01-28
Ever sense I  set up my wireless internet I've been having fits with it. It kicks me off every now an then for no reason. By shear number of times this has happened I've been able to (I think) figure out the (or atleast one of) the causes for this to happen. It seems when I'm running BitTornado (or any BitTorrent software) if I get too may peers (16-20) it kicks my internet connection. When I go to terminal and scan wlan0 I get 'this device does not support this feature' most of the time, sometimes I get what I should get.
Any ideas on how to fix this? Or atleast a good Torrent Client that I can set the max number of peers. BitTornado offers that feature with a few hard-coded options, the lowest being 20, which will get me kicked. I'm running no firewall, but the router has a firewall built in but it should be disabled (I think I did that last night).

Any ideas? Or atleast something to get me started?

---

### Post by RandomJoe on 2007-01-29
Does this only happen on WLAN?  Have you tried it with a hardwired connection?

I have heard that some home routers go stupid if the number of connections they have to track gets too high.  ('High' being relative - not all that many.)  What router do you have?

You say you disabled the router's firewall - is your computer getting a private or public IP?  If it's getting a private one (192.168.x.x typically) then the router is still doing NAT (network address translation) which means it has to keep track of every active connection your system makes in order to properly make the translations.  This is evidently too much for some of the weaker systems.

---

### Post by malfist on 2007-01-29
It only happens on wlan, ehto worked fine but someone in my household hates the cord (mother and tripping housekeeper). Its not a good router from what I have heard, it's linksys and I'm running wireless with the worst dongel, NetGear WG111v2 (really v1, labeled as v2). I have a private ip, assinged though DHCP from the router. I never get similies when downloading. I'm not totaly sure that it is the torrents causing it because it happens without it but it almost always happens within about a half a minute after starting a popular torrent. It never seems to happen when I'm not using bandwidth (aka, playing MUD's (dsl-mud.org)), but then I'm using GNOME-Mud and not a browzer but I don't think that would have anything to do with it.
I'm also shareing the internet connection with one other computer which does not have this problem (It's wired and windows).

---

### Post by Hanzerik on 2007-01-29
What kernel are you running? Version, i386, 486, 686? and do you use ndiswrapper?

I have run into problems running ndiswrapper on an SMP kernel, so I just run it on a stock i386, or 486, non SMP kernel.

---

### Post by malfist on 2007-02-02
I am using ndiswrapper, I believe the kernel is i386, I know it is ix86, how would you check for it? It's an older computer.

---

### Post by Hanzerik on 2007-02-05
uname -r

---

### Post by malfist on 2007-02-07
uname -r returns: 2.6.15-27-386
I'm giving up, I've heard Fendora works with it a lot better and I've always wanted to try Fendora so I downloaded 6 (yes, I know 7 if coming out soon) so I'm going to try it. Ubuntu was my first ;).

---

### Post by malfist on 2007-02-07
lovely, fendora wont install

---

