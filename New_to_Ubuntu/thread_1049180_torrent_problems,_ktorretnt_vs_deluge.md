---
title: "torrent problems, ktorretnt vs deluge"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by beanco on 2009-01-24
hi all,

i have both ktorrent and deluge.

ktorrent currently seems to be *stuck* if you will. all the downloads are stalled,  even those that theoretically have many many seeders....

so i thought i would try deluge but when i click on a down load this torrent button, ktorrent opens.

yes, i am a n00b at this stuff, so forgive my questions if they seem silly...

ok, so, is there a reason ktorrent is *stuck* and is there a way to use deluge? i use epiphany, btw....

thanks

robi

---

### Post by diablo75 on 2009-01-24
Do you have a router?

---

### Post by SOULRiDER on 2009-01-24
Download the .torrent manually. Then open Deluge and open them suing Deluge from Deluge's menu. I use rTorrent, its a CLI client but i prefer it over those two, you might wanna check it out.

---

### Post by SOULRiDER on 2009-01-24
> **diablo75 said:**
> Do you have a router?

That too, make sure your ports are open and nothing is blocking the traffic.

---

### Post by mkvnmtr on 2009-01-24
I used Ktorrent and really liked it but it quit working on me in 8.04. I searched around and found Deluge and like that just as well. On either one make sure youo are set to use random ports and you should not have to port forward. I just download the torrent to save to desktop and then click add in Deluge to put in the torrent.I like that because it gives me a chance to look at the files in the torrent to see if there are some I don't wish to download.

---

### Post by diablo75 on 2009-01-24
> **mkvnmtr said:**
> On either one make sure youo are set to use random ports and you should not have to port forward.

I disagree (unless you have no router and are directly connected to the Internet/Modem).

If you have a router, you should do two things:

1.  Set your PCs IP address to be static (Non-changing).
2.  Port forward some random port number to your PCs IP address and set your torrent client program to listen on that number.

If you don't, inbound connection requests will hit your router, but your router won't know where to pass the requests on to because no port forwarding "rule" exists to tell it where to pass the packet on to and it will just drop the packet.  You can still get by without without setting up port forwarding but your download speeds will be much slower.

---

### Post by diablo75 on 2009-01-24
> **beanco said:**
> ktorrent currently seems to be *stuck* if you will. all the downloads are stalled,  even those that theoretically have many many seeders....

One other thought:

Sometimes torrents come from member-only trackers, meaning you have to be a member of a website with your own login account before the torrent will download.

---

### Post by beanco on 2009-01-24
i have a router, but until last night it was not an  issue.... \


guess my OP was not clear. I used ktorrent and liked it, for months. then yesterday or the day before, things started slowing down, stalling.... i thought maybe it was a ktorrent issue that is why i tried deluge....


i really do not understand all this stuffa bout down loading manually.... how do i do that?

and thanks for the help.

robi

---

### Post by diablo75 on 2009-01-24
Perhaps your ISP is [throttling]("http://en.wikipedia.org/wiki/Bandwidth_throttling") your connection??

---

### Post by beanco on 2009-01-24
> **diablo75 said:**
> Perhaps your ISP is [throttling]("http://en.wikipedia.org/wiki/Bandwidth_throttling") your connection??

i suppose there could be more traffic now causing the isp to throttle, but i have no way o checking this, do i?

robi

---

### Post by diablo75 on 2009-01-24
> **beanco said:**
> i suppose there could be more traffic now causing the isp to throttle, but i have no way o checking this, do i?

robi

An easier question would be:  Who's your ISP?  Certain ISPs have reputations for blocking torrent traffic.

---

### Post by beanco on 2009-01-24
my isp is datanet located in budapest hungary...


robi

---

### Post by GrandpaLeaman on 2009-01-24
I don't know why ktorrent stalls so I can't really help you with that, but I am using Firefox. Unlike Epiphany, Firefox pops up a dialog to allow you to select the default or an alternate torrent client to use.

---

### Post by diablo75 on 2009-01-24
> **beanco said:**
> my isp is datanet located in budapest hungary...


robi

You might hit the networking forums up to see if anyone in there thinks that your ISP might be hampering your bandwidth, or blocking torrent traffic.  In the mean time, you could try changing the port number your client listens on.  Sometimes the blocking can be as simple as blocking a specific port number after they've seen so much traffic heading your way on that port.  They may see it and go, "He's probably trying to pirate something." and just block that one port.  But you have about 64000 other port numbers you can try.

If they're more sophisticated, they might be blocking traffic by packet type.  The only thing I can think of doing about that is making sure your client has encryption enabled.

You might also check this out:

[http://torrentfreak.com/optimize-your-BitTorrent-download-speed/](http://torrentfreak.com/optimize-your-BitTorrent-download-speed/)

---

### Post by jerrrys on 2009-01-24
[http://http://azureuswiki.com/index.php/Bad_ISPs#Hungary]("http://azureuswiki.com/index.php/Bad_ISPs#Hungary")

---

### Post by jerrrys on 2009-01-24
[http://azureuswiki.com/index.php/Bad_ISPs#Hungary]("http://azureuswiki.com/index.php/Bad_ISPs#Hungary")

---

