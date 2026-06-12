---
title: "Mainly Linux Network Moving Slowly"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by 67comet on 2008-05-05
I can't think of a better place to put forth this question so here goes.

I've got a small network running in my home. I have Fiber running into the house with a Linksys WRT54GL (Tomato installed) handing out the signals and cat5 to the machines in the house.

I have a web server (Ubuntu Server 7.10), media server (Ubuntu Server 8.04), web backup (Debian 4.0 headless), workstation (Ubuntu 8.04), a Vonage Linksys router and empty cat5 cable for working on other boxes some times. These boxes are all hooked to the WRT54GL via copper and a mindless hub (workstation and web backup are running through the hub). Wirelessly I've got an Ubuntu 7.10 powered workstation/media box, Ultimate Edition workstation/media box, two Mac OS X/Linux powered MacBook Pro computers that connect on occasion,two iPod Touch devices that use the wireless when needed.

I know this is a lot to ask of a normal home network, but this is what I've got on my network.

My issue is that when we first got fiber (in November 07) it was super ultra smokin' fast. But now? It is dismal at best. A simple aptitude update takes several minutes and heaven forbid it needs more than 10mb or so because that would take hours.

How can I go about trouble shooting this and finding out where the slow down is coming from? I've tried shutting down all but vital machines, only using stock Linksys settings and have watched my wireless to see of there are any unwanted leachers. Nothing seems to make a difference although once in a blue moon my speeds seem to pick up to an almost acceptable speed.

Anyone know a decent method to go about narrowing down the issue? Please help, I'm all out of ideas.

Thank you.

---

### Post by HunterThomson on 2008-05-05
Have you tried to just plug in the router to the fibre line then plug in a laptop to the router (or what ever) and then go to testmy.net to make sure the fibre line is not the problem? Have you called your ISP and asked them about the problem? The ISP has a recorded of everything that has or is going over that line.

---

### Post by HunterThomson on 2008-05-05
by the way... How much do you pay for the line? What is the down and up bandwidth suppose to be? I would like to know so I could dream about it tonight:)

---

### Post by 67comet on 2008-12-08
I pay 7500 to 8,000 yen for my fiber (bout $80'ish a month) and it's nice and fast. Not sure exactly; but a 4gig file takes about 30 minutes +/- depending on whom I'm getting it from. I've done some speed tests online with it, but can't remember the speeds.

My issue isn't external though; only internal. I can move files around my network fine, just going to my web-server is slow. All machines share with each other via NFS and they are all set up the same (fstab mounted like: IP:/file/location /mount/point nfs defaults 0 0 and the /etc/exports are all similar to: ip.add.ress(rw,sync,no_subtree_check) ip.add.ress(rw,sync,no_subtree_check) etc etc ... My servers are all Ubuntu Server 8.04 except for my movie and junk file server; they run Debian because Ubuntu Server edition would not install (very old hardware on those two -PII 450mhz, 94mb ram, 4gig and 500gig hdd on the junk file server and Cyrix 233mhz, 131mb ram, 10gig/500gig on the movie server-). My web server info can be reviewed @ [http://www.openlug.com/wp-content/sysinfo/](http://www.openlug.com/wp-content/sysinfo/) .

My ISP has been totally cool with my serving out of my house. They even found an English speaking person that helped me get PPPoE working to my router so I could assign the port to my web server etc etc .. The only real issue I have that is ongoing is the e-mail issue common with most ISPs in the US.

---

