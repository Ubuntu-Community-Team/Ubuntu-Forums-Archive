---
title: "Torrents and web pages, priority"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by Zalbor on 2006-10-10
If I'm downloading a torrent with many seeders/leechers (that's what triggers it as far as I can tell) web pages have difficulty loading. I was using Azureus at first and I had to stop any torrent in order to view a web page.
Then I noticed that if I used Windows, then it all works fine, so it wasn't a problem with my router, but with Ubuntu.
Now I'm using kTorrent, and although the problem has been lessened, it's still there... Is there a way to solve it?

---

### Post by judgejudy on 2006-10-10
> **Zalbor said:**
> If I'm downloading a torrent with many seeders/leechers (that's what triggers it as far as I can tell) web pages have difficulty loading. I was using Azureus at first and I had to stop any torrent in order to view a web page.
Then I noticed that if I used Windows, then it all works fine, so it wasn't a problem with my router, but with Ubuntu.
Now I'm using kTorrent, and although the problem has been lessened, it's still there... Is there a way to solve it?
 Yes dont upload a lot when suffing set uploads to about 5kb then open it back up to full when you just want to down load :D

---

### Post by Jorge on 2006-10-10
I recommend you to keep Azureus. It is highly configurable. Check this page, for tips and tricks:
[http://www.azureuswiki.com/index.php/Tips_and_tricks]("http://www.azureuswiki.com/index.php/Tips_and_tricks")

For me, the best recommendation is to have a "auto" in upload speed. It detects your network demand and adjust the limit.

---

### Post by Zalbor on 2006-10-11
Thanks for the replies... But if it was an issue with configuring the client, shouldn't I have the exact same problem in Windows? I configured Azureus in the exact same way in both OSes.

---

### Post by Zalbor on 2006-10-12
It doesn't seem to be an uploading problem... When I'm just seeding without downloading it works great.

---

### Post by Zalbor on 2006-10-12
...and it was just confirmed. I limilted the upload rate to 5 KB/s, still the same problem. It definitely has to do with downloading.

---

### Post by Stolie on 2006-10-12
This problem has to do with both d/l and u/l speeds and bandwidth usage. The faster you pull info down or up, the more 'net traffic it causes, and the less bandwidth you have for email, surfing, and other such stuff.

---

### Post by Zalbor on 2006-10-12
Ok, I understand that. But could you at least explain why that's only a problem in Ubuntu? The torrents I've downloaded from windows are pretty lively too, and yet messengers and web pages have had no trouble at all there.
I've also set Quality of Service in my router, to give priority to web pages rather than torrents.

---

### Post by lonce on 2006-10-13
This is easy.  Even if you are downloading slowly in torrents, your upload that you allow through the program is pretty much maxed.  Now if you went with default install of the program it just took your max.  

For you to surf a website, you have to send the request to the site.  It is then put in line behind all the packets of torrent going out.  Thats why it slows down your web surfing.

Take your upload bandwidth, what ever it is.  Then set your torrent upload speed to 70 percent of that.  This allows you bandwidth set aside for internet or email or what have you.

---

### Post by lonce on 2006-10-13
You also have to think, when your uploading torrents, your sending packets to all your seeds and peers, its not completely a bandwidth issue, its also the great amount of packets your sending out.  To surf the internet, they get put in the line and have to wait their turn to be sent.

---

### Post by lonce on 2006-10-13
The only software I have used that didnt see this affect is Utorrent.  Never really had this problem, but azeurus is a huge resource hog.

---

### Post by Zalbor on 2006-10-13
> **lonce said:**
> This is easy.  Even if you are downloading slowly in torrents, your upload that you allow through the program is pretty much maxed.  Now if you went with default install of the program it just took your max.

For you to surf a website, you have to send the request to the site.  It is then put in line behind all the packets of torrent going out.  Thats why it slows down your web surfing.

Take your upload bandwidth, what ever it is.  Then set your torrent upload speed to 70 percent of that.  This allows you bandwidth set aside for internet or email or what have you.
Ok, but as I said above, if I'm just seeding, which means 0 download and (supposedly) MAX upload, it works! It's *only when downloading* that I have a problem.
And still, how does that explain it working in one OS and not in the other?

---

