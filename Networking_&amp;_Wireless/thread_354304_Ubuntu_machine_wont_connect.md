---
title: "Ubuntu machine wont connect"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by lxlScubaStevelxl on 2007-02-05
So I had a slighty old computer, and I didnt have the ram for it to be upgraded to XP, so I put Ubuntu on it instead. 

Anyway, It didnt have a network card, so I got one. Long story short, my brother popped it in, it connected fine to the internet. Then after I moved it to a different room, the network card disconnected due to not being screwed in. I popped it back in place and screwed it in, and now the machine wont connect at all. I checked the back of the tower, and all teh network card lights are on, letting me know it has a connection, But it wont connect to the internet at all.

Any ideas on how I can fix this problem?

ps. If it helps any, its a D-link network card, and all computers in my home are connected through a Linksys router.

---

### Post by lhtown on 2007-02-05
Did you try rebooting your brother?

You can try pinging a website to see if that works.

I am assuming you are connecting with a wired network. If you entered the IP address manually, you are probably connecting to a different port with the other cable. You could either figure out what the correct IP is or just use DHCP which is automatic.

---

### Post by lxlScubaStevelxl on 2007-02-05
The tower has been diconnected for quite some time before now, Its only plugged in now because we actually need it. Its been like this for awhile, but I have just decided to do something about it now. Im not familier with Ubuntu in the least, it was my buddies idea to put it on. The rest of my family wouldnt know the difference, so I had no objections.

---

### Post by lhtown on 2007-02-06
Welcome to Ubuntu! For Windows and Mac users, it is a bit of an adjustment at first, but after a couple of weeks or so, it really is great for most users. 

After using Linux for over two years, if I even had to run a TEST Windows system, I would be kicking and screaming. Also, the new Fiesty coming up in a few months looks like it will be more newbie-friendly than ever.

When I first switched from Windows to Debian (about 6 months or so before Ubuntu came out with its first release), I was so fed up with the Windows upgrade/lock-in cycle that I was totally determined to make it work. Also, I was just tired of paying for all of the little things that you have to buy with Windows as well as the virus and security problems. 

Also, I saw the direction that Linux was going with its fast development model and the way Windows was going with its glacial, it's good-enough-to-make-a-profit model, and, for me, switching was a bit of a struggle, but I was totally determined to make it work, and it has worked ever since for me.

When Ubuntu came out, it took care of a lot of the things that I once struggled with in Debian and each release gets easier and more fun for those of us that actually USE our computers.

---

### Post by Iowan on 2007-02-07
I'm kinda short on time, so I can't go into adequate details (now). I'm a bit embarrassed to admit that I can't remember the name of the menu selection to check the status of your network card.  From a terminal, you can see if the machine is getting an IP address with **ifconfig**.  You could try pinging the router.  You could also check (post?) the contents of the **/etc/network/interfaces file**.  

I'll try to check back when I get home tonight.

---

### Post by Iowan on 2007-02-08
Sorry for delay...
System>Administration>Networking should show the network card status.  If not active, Properties should allow you to enable it.  Depending on whether you've set static addresses or are using DHCP, **dhclient** (from terminal) *should* get an address assigned.

---

