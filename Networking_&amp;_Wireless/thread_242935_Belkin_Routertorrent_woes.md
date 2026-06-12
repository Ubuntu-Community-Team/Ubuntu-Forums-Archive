---
title: "Belkin Router/torrent woes"
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by larryni on 2006-08-24
I installed Ubuntu back in May and it has been happily running along without any problems. I connect to the Net using a 'Belkin ADSL Modem with Wireless G-Router' and never had a problem with that either. The machine runs 24/7 with torrents down/uploading (Azureus) in the background with normal speeds I was used to in Windows. 

About 3 weeks ago I noticed that the torrent speeds weren't the best anymore (especially up speeds) and I kept losing my Internet connection after about 3-4 hours, the status light on the router just switched off. My local network was alright though. A quick router reset and I had my connection back for another 3 or so hours. Then at the start of this week the time in between dropping the connection went down to about 1 hour, often less. But now it wasn't only the Internet connection that went, but the status lights for the phone line and my wireless went as well. I couldn't even log in to the router's setup pages anymore.

I thought my router was on its way out and went ahead and ordered a second-hand one off ebay (money's tight at the moment :rolleyes:) on Monday afternoon. Then on Monday night I had to boot into Windows in order to use the TV out (damn ATI cards). As I was gonna be in Windows for a good few hours I loaded up uTorrent to keep seeding. And guess what - the router stayed online. So I left it running overnight and the lights were still on in the morning. I thought it might be a problem with Azureus in Ubuntu. I then installed uTorrent using Wine, but with the same result - all the lights went off after an hour or so.

I haven't loaded up any torrent programs today and have been able to use the connection all day long without any problems. Anyone got any idea what's going on here?

---

### Post by royale on 2006-08-24
I had a similar problem with Azureus on Ubuntu while it was working without problem in Windows.  What version of java are you using?  ("java -version")

---

### Post by larryni on 2006-08-24
It's version 1.5.0_07. But I don't think it's that. It was working fine up until 3 weeks ago. And the same thing happens when I use uTorrent.

---

### Post by x64Jimbo on 2006-08-24
You're most likely being kicked by your ISP for excessive bandwidth usage. You might try turning on encryption in your client to mask your traffic type.

---

### Post by larryni on 2006-08-24
I'm sure that's not it either. I actually have quite a high b/w allowance with my ISP, about 200GB a month. And they would always send me an email when I get too close to warn me that they'll start traffic shaping if I keep using too much. As I mentioned before, in Windows things are grand. As soon as I switch back to Ubuntu my router collapses after an hour. And not just my Internet connection, but my whole local network.

---

### Post by x64Jimbo on 2006-08-24
I don't understand. You just said that the same thing happens with uTorrent, which is a windows program

---

### Post by larryni on 2006-08-25
Yes, it is. But it runs on Ubuntu using Wine. That's why I don't believe it's got anything to do with Java.

---

