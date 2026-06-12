---
title: "K torrent or Transmission ?"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by rufio666 on 2010-07-29
Hi there everyone !
I'm new Linux user and i have to solve one torrent topic. K Torrent 
or Transmission ? Before i moved to Linux UTorrent was my default torrent client which i thing is one of the best.Which torrent client is the best on Linux ?

---

### Post by NFblaze on 2010-07-29
Some say rtorrent, some say Deluge, some say Ktorrent, some say Transmission, etc.

There are many options, you might as well just try them all and figure out which one you like best. 

Though, by default Ubuntu comes with Transmission.

---

### Post by _h_ on 2010-07-29
I prefer the standard prebundled Transmission, which is simple and easy to use.

Also has privacy block lists, encryptions and support for magnet links.

---

### Post by pixel_pusher on 2010-07-29
Transmission is my weapon of choice for torrents. Cant say why, but it always seems to get the best transfer rates.

---

### Post by lovinglinux on 2010-07-29
I don't like Transmission interface, because I like to see torrent info on the same window. Ktorrent is way much better IMO, but recently I switched to qBitTorrent, which is the fastest client I ever used.

---

### Post by jtarin on 2010-07-29
I've used Ktorrent,Deluge,qBit but I've settled on Transmission. I'm a uTorrent user also and had it running in Wine awhile but went native instead.

---

### Post by Goolie on 2010-07-29
As a sworn utorrent user, deluge was the only one I felt comfortable with.

=D

---

### Post by lovinglinux on 2010-07-29
BTW, there is an uTorrent version for Linux being developed that should be available later this year.

---

### Post by 2uk_ on 2010-07-29
I like transmission. I find download speeds are generally higher than when I had UTorrent/Windows.
Also it's got a really simple layout. Nothing complicated to look at

---

### Post by ajgreeny on 2010-07-29
I have used both ktorrent and transmission and find that both are good, and in my case both give me download speeds close to or at my maximum line speed.  I personally prefer transmission which is a set and forget application.  I am not too worried about some of the details of a download, as long as it's fast, so I don't need all the bells and whistles of ktorrent, and transmission tells me how fast things are coming down and going up; that's all I need.

---

### Post by x C0MMAND0 x on 2010-07-29
Transmission for the win, imo.  But whatever works best for you.

---

### Post by Legendary_Bibo on 2010-07-29
I like Vuze, but when I used Transmission I ended up maintaining over 1MB of download speeds despite the amount of seeders, I never had that with Vuze, but I like Vuze for it's features, and I use Transmission when it's mission critical to download something fast.

---

### Post by rufio666 on 2010-07-29
Thank you for fast respond everyone !
And i come to the point when "try it on" will be my next move :D
This qBitTorrent is sounding good and i hope is not baned ;)

---

### Post by giddyup306 on 2010-07-29
I liked Transmission since I began using it.  I was then told to try Deluge to increase trackers and speed.  It did neither.  I was like "wow this is cool, has a lot more features".  After messing with it for about an hour I went back to Transmission because the added features were things I'd never use,  That and Transmission is easier to use IMHO.


If you want to try something super light weight you might want to try rTorrent.

I'd aviod bitTorrent and uTorrent at all costs.

[http://www.ricehatersclub.com/vbulletin/showpost.php?p=456435&postcount=1]("http://www.ricehatersclub.com/vbulletin/showthread.php?t=30484&highlight=bittorrent")

---

### Post by grantoos on 2010-07-29
I tried them all and I stuck with Qbittorrent but now I'm using Transmission because I find with the other programs they either slowed down my whole internet speed, or the other problem was if I put an upload limit on a torrent it would bring the download speed as well.  With Transmission I can put an up limit and my download is still going full force.

---

### Post by rufio666 on 2010-07-29
Transmission is just running with outstanding speed:D without any problems at all.Compare  to the KTorrent is more flexible and is going on top gear faster than KT(kt needs half an our to get top speed-i don't now why) Thanks to all torrent client topic sorted ! ;)

---

### Post by davegtt on 2010-08-25
Ive just started using ubuntu for the first time tonight. I started downloading a couple of torrents and speeds were coming down great, 2 mins later all my torrents were on 20% and said download limit exceeded and cut the internet connection. it comes back up if I close transmission but thats no good. anyone have any ideas? Theres nothing in preferences saying I have limits set etc

---

### Post by davegtt on 2010-08-25
Actually just tried it again and it says Tracker gave an error - Connection limit exceeded. It cuts off firefox too whilst running yet soon as I close it Im running again???

---

### Post by jtarin on 2010-08-25
> **davegtt said:**
> Actually just tried it again and it says Tracker gave an error - Connection limit exceeded. It cuts off firefox too whilst running yet soon as I close it Im running again???


Most common problem: 
If for some reason (e.g. pc crash, or frozen client) your client exits improperly and you restart it, it will have a new peer_id, so it will show as a new torrent. The old one will never receive a "event=completed" or "event=stopped" 
and 
Some clients, notably TorrentStorm and Nova Torrent, do not report properly to the tracker when canceling or finishing a torrent. In that case the tracker will keep waiting for some message - and thus listing the torrent as seeding or leeching, making the tracker think you're still downloading. 

How to Solve it ? 

# close your bittorrent client. 
# select the tracker passkey reset (if there is one) 
# download the new .torrent 
# re-start your bittorrent client with the new .torrents 

another reason could be that your .torrent is beeing used by other people. 
because you uploaded them to another tracker/forum or what ever or shared it with someone, same solution as above.

---

### Post by formaldehyde_spoon on 2010-08-25
Love the super simple Tranmission interface, but I also like Deluge.

---

### Post by UncleNinja on 2010-08-25
I like Transmission because it's simple and fast. It just downloads and I'm done. Nothing complicated. :KS

---

### Post by M93 on 2010-08-25
Transmission is really good
it comes by default
its got block list, encryptions, exceptions, limit download and upload speed
its got a really simple interface
and its kinda faster than utorrent/windows

---

### Post by warfacegod on 2010-08-26
I prefer ktorrent.

You may find this link useful: [http://ubuntuforums.org/showthread.php?t=1259923](http://ubuntuforums.org/showthread.php?t=1259923)

---

### Post by davegtt on 2010-08-26
Does Transmission let you download more than one torrent at a time? I was downloading 3 and thats what gave me my problems, I paused 2 and the 3rd just finished nicely, I cant use the internet whilst downloading either. Anymore than one torrent downloading at a time and I get that connection error.

---

### Post by warfacegod on 2010-08-26
> **davegtt said:**
> Does Transmission let you download more than one torrent at a time? I was downloading 3 and thats what gave me my problems, I paused 2 and the 3rd just finished nicely, I cant use the internet whilst downloading either. Anymore than one torrent downloading at a time and I get that connection error.

Sounds like your overloading your router. You can set Torrent clients to a fixed amount of bandwidth. Check the link I posted.

---

### Post by Shpongle on 2010-08-26
+1 for transmission , Its a great tool for the job.. does everything I need

---

### Post by dynamo2 on 2010-08-26
+1 for transmission, simple and does the job without the extra features many wont ever use or need.

---

