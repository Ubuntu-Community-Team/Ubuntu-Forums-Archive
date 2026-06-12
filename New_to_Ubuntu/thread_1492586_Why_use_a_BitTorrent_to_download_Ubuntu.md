---
title: "Why use a BitTorrent to download Ubuntu?"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by adamk918 on 2010-05-24
Just curious...

Why is downloading Ubuntu over a BitTorrent preferred over a regular download with Firefox?

---

### Post by Jarthur121 on 2010-05-24
Cause torrents work by downloading small files from multiple web sources. The more sources (or seeders) you have, the quicker you download the file. Since there are so many seeders for the Ubuntu Torrent you can download it at a faster speed than a normal Firefox download.

---

### Post by SRST Technologies on 2010-05-24
The answer to this requires a little explanation of how bittorrent, http, and big fat internet pipes work.

Let's start with the HTTP method.  If you download Ubuntu from the Ubuntu server, you must remember that everyone and their brother is hitting Ubuntu's site right now for everything under the sun... to look at the site, to download it too, and whatever.  Ubuntu's server only has so big a connection to the internet and you're sharing that with everyone.

Bittorrent... bittorrent is not using the Ubuntu server at all (except maybe for some scrapes, I don't know where the tracker is).  Bittorrent directly connects you to my computer, Bob's computer, Sally's computer, and everyone else who has a copy of it that is willing to share with you.  Instead of connecting to one server (Ubuntu) you're connecting to 10,000 people who individually have less bandwidth than Ubuntu, but collectively are extremely fast and to boot, less people are hitting these individual users at once than Ubuntu's server.

If you have the chance to download free software via Bittorrent, always do it.  By doing this you're also costing Canonical and Ubuntu less too, as they have to pay for the bandwidth you are using to download their file.  Bittorrent users have already paid their monthly bill and you're not costing them anything more.

---

### Post by jimmy the saint on 2010-05-24
Kindness.  Rather than hitting the main server, like so many others do at the exact same time, you are distributing the load.  Also, it will likely be faster in the initial days post-release, since the main servers get bogged down with so many dl requests.

---

### Post by adamk918 on 2010-05-24
> **SRST Technologies said:**
> The answer to this requires a little explanation of how bittorrent, http, and big fat internet pipes work.

Let's start with the HTTP method.  If you download Ubuntu from the Ubuntu server, you must remember that everyone and their brother is hitting Ubuntu's site right now for everything under the sun... to look at the site, to download it too, and whatever.  Ubuntu's server only has so big a connection to the internet and you're sharing that with everyone.

Bittorrent... bittorrent is not using the Ubuntu server at all (except maybe for some scrapes, I don't know where the tracker is).  Bittorrent directly connects you to my computer, Bob's computer, Sally's computer, and everyone else who has a copy of it that is willing to share with you.  Instead of connecting to one server (Ubuntu) you're connecting to 10,000 people who individually have less bandwidth than Ubuntu, but collectively are extremely fast and to boot, less people are hitting these individual users at once than Ubuntu's server.

If you have the chance to download free software via Bittorrent, always do it.  By doing this you're also costing Canonical and Ubuntu less too, as they have to pay for the bandwidth you are using to download their file.  Bittorrent users have already paid their monthly bill and you're not costing them anything more.
Great explanation! I'll remember it next time I need to download Ubuntu (my fingers are crossed that Maverick Meerkat will be better) since I've already downloaded it via the HTTP method.

---

### Post by shazbut on 2010-05-24
If you're lucky your ISP will have a local mirror of the Ubuntu directories, it's always worth checking if yours does.  All my isos and updates one hop away on the ISP server via http download.  I've seen downloads at 25-30000 K_Byte_/s from that server at times here at work.

---

### Post by cascade9 on 2010-05-24
> **SRST Technologies said:**
> Bittorrent... bittorrent is not using the Ubuntu server at all (except maybe for some scrapes, I don't know where the tracker is).  Bittorrent directly connects you to my computer, Bob's computer, Sally's computer, and everyone else who has a copy of it that is willing to share with you.  Instead of connecting to one server (Ubuntu) you're connecting to 10,000 people who individually have less bandwidth than Ubuntu, but collectively are extremely fast and to boot, less people are hitting these individual users at once than Ubuntu's server.

I agree 100% with everything you said.....except for the speed detail. I have no idea how much bandwidth the server which you d/l ubuntu has, but I've seen some pretty amazing speeds from even single-peer connections. I've seen my admittedly not that great bandwidth get taken up 100% with a single peer (2.5MB a sec, on a connection that speedtest returns about 19-20Mbit a sec d/l speed). 

I think that was a connection from japan, where you can get gigabit internet. Residential. Yes, gigabit. Also avaible in Hong Kong ;) I doubt you would saturate that with 1 peer. LMAO

There is also 1 other great reason for getting a .torrent. With any decent torrent client, you can check the finished file to amke sure its all d/led corectly. I always do this, never bother with checksumming my d/led .isos, and I've never got a bad disc yet. (and I know that some people are going to roll eyes at that, and probably someone is going to point out its not the same thing).

---

### Post by SRST Technologies on 2010-05-24
That's another reason to hate Hong Kong and the Japanese.  Or, I could move there.

Either way, yeah, you could sometimes get better results from a http download and worse with bittorrent, but those are anomalies and not the norm.

---

### Post by Sef on 2010-05-24
> I think that was a connection from japan, where you can get gigabit internet. Residential. Yes, gigabit. Also avaible in Hong Kong  I doubt you would saturate that with 1 peer. LMAO

A friend who lives in Japan had a 60 gb internet connection.   

> There is also 1 other great reason for getting a .torrent. With any decent torrent client, you can check the finished file to amke sure its all d/led corectly. I always do this, never bother with checksumming my d/led .isos, and I've never got a bad disc yet. (and I know that some people are going to roll eyes at that, and probably someone is going to point out its not the same thing).

Torrents are automatically checked, so no need to md5sum the download.

---

### Post by cascade9 on 2010-05-25
> **SRST Technologies said:**
> That's another reason to hate Hong Kong and the Japanese.  Or, I could move there.

Either way, yeah, you could sometimes get better results from a http download and worse with bittorrent, but those are anomalies and not the norm.

I cant speak for Japan, but HK is fantastic. Great city :) 

Unless somebody is using a ISP that 'shapes' torrents. Then direct d/ls would be faster. Not having ports forwarded could also drop the torrent speed to less than a direct d/l as well.

> **Sef said:**
> A friend who lives in Japan had a 60 gb internet connection.   

Torrents are automatically checked, so no need to md5sum the download.

60GB o.O Hmm, that means, at full speed...I could blow my usage quota in about 2 minutes or less. :| 

Thanks for that, I knew that torrents were checked but I was unsure about how reliable the checking was ;)

---

### Post by 3rdalbum on 2010-05-25
Torrents are not only checked, but they are checked constantly while downloading.

With an HTTP download, you would attempt to download the whole file, and then manually md5sum it afterward. If only one byte was wrong, the sum would fail, and you'd have to attempt to download the whole 699 MiB again.

With a Bittorrent download, it checks each section as it comes down. If one byte is wrong, then it will automatically download that 2 MiB section again.

Yeah, Bittorrent can sometimes be faster, especially on release day when everyone is hitting the server. But the benefits for file checking make it seriously worthwhile for everyday use, when you can.

---

