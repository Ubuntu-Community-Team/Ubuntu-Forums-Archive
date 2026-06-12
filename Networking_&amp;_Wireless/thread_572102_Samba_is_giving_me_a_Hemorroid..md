---
title: "Samba is giving me a Hemorroid."
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by tankertuff on 2007-10-10
I've done like 4 different samba howtos, and tried everything I can think of. I had It working last night, then it just quit. I'm trying to set up a samba network with my windows box. This is my first attempt at any of this, so I don't really know what I'm doing wrong. And please, before I just get a bunch of links, i'm sure I've beat you to them. I first tried to just set up a share with the System>Administration>Shared Folders command. well, I could see the windows stuff in the Places>Network, and even write to them. I could also see the Ubuntu share there, but not through windows, it would show up as nothing when I would try to go to the domain. I did have it show me once, but asked me for a pass, which I later saw I didn't have set. well, now, windows can't see linux, linux can't see windows, this is after I did a samba howto from on this site. I love linux, and have been using it for a while now, and I'm trying to stay, but I NEED windows for my music production as ubuntu studio is a joke, as well as all audio creation on linux. The only thing keeping me from wiping ubuntu is I have too much time in this install and I don't want to lose any more productivity due to a reinstall. Any Ideas?? (like I said, please don't just post a bunch of howto links) Thanks guys.

---

### Post by HermanAB on 2007-10-10
What you need is a debug strategy:
[http://www.aeronetworks.ca/samba-debug-howto.html](http://www.aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by tankertuff on 2007-10-10
thanks, I'll give that a try.

---

### Post by tankertuff on 2007-10-10
oh, and I forgot to mention, when I go to Places>Network in Ubuntu, and click on Windows Network, it shows absolutely nothing, while there's folders in view in VMWare XP

---

### Post by Blindraven on 2007-10-10
Same problem I'm having right now, I'll bet you have more boxes on the network and Samba is fighting for privs.

When I get my techy to fix it I'll let you know whats going on.

---

### Post by dmizer on 2007-10-10
is the windows box you're trying to share files with ... a virtual machine?  if so, what kind of networking do you have in place?  bridged or are you using NAT?  what vmware software are you using?

vmware complicates filesharing across a network.  do you have a separate windows machine that you can test with outside of a virtual machine?

---

### Post by tankertuff on 2007-10-13
> **dmizer said:**
> is the windows box you're trying to share files with ... a virtual machine?  if so, what kind of networking do you have in place?  bridged or are you using NAT?  what vmware software are you using?

vmware complicates filesharing across a network.  do you have a separate windows machine that you can test with outside of a virtual machine?


I was using the vmware from the repos, and I tried both NAT, Bridged, and actually had it working with host only, but then it just destructed, lol. I just reinstalled windows on another partition though, I actually tried to run Reason in xp through VMware and it was horrible, also read you could install it through wine, but despite all the info I saw saying it was feasible, it wouldn't work, so, as much as I hate it, it's dual boot for me. That's a bummer too, because I was looking forward to getting out of windows for good, but my software choices just won't let me, and I'm not about to spend a total of 8-10,000 bucks for new rig/software. :( thanks for the help though. (My samba experience will probably be better once I have a separate machine instead of trying the whole virtualization bs, which is totally worthless for music production,)

---

### Post by dmizer on 2007-10-13
i think you can install both vmware player (which has terrible file sharing issues) and vmware server (filesharing works if networking is set up carefully) from the repos.

anyway, sorry to hear that ubuntu's not going to fit the bill for your music production, but that's fairly typical when you are forced to rely on a specific piece of software or hardware.  not really anyone's fault per se ... just a bummer.

you might consider turning an old unused computer into a file server.  just throw a big disk into it and install dapper server (cli only) and samba.

---

### Post by tankertuff on 2007-10-14
yeah, I'm planning on doing that. A friend of mine just got a job as an admin at a local computer center, and a loaded customer came in and upgraded his computer (it already had a quad core intel EE , and 2 gb ddr800, lol), well, the guy didn't want the parts, and I needed some, so I'm getting an early christmas present. gonna set this rig up w/ ubuntu, and the other w/ xp pro, so hopefully samba won't be so difficult with 2 physical machines. I'm sure it'll go a heck of a lot smoother. I was kinda ticked reason didn't work in Ubuntu, everything I read said it would, I will say this though, running steam through cedega gave me waaaaay better framerates, lol. I guess it's because there's not the winrot and bloated OS overhead in the background.

---

