---
title: "I need a torrent client....."
date: 2009-01-29
forum: New to Ubuntu
---

### Post by sluggerjd on 2009-01-29
Hi what is the best and most compatible torrent client for ubuntu with private trackers? Sorry if i shouldnt have said anything about that!

---

### Post by tiresia on 2009-01-29
> **sluggerjd said:**
> Hi what is the best and most compatible torrent client for ubuntu with private trackers? Sorry if i shouldnt have said anything about that!
Why shouldn't say anything about a torrent client?
If you need just a Client, Transmission should work perfectly.
It is already installed.

---

### Post by Acradon on 2009-01-29
A lot of people use Vuze (formerly Azureus). Personally I had some problems with the program, but nothing really major. It seems there are some little bugs in it that can easily be fixed. It really is simple to use. I just have to wait another week before reinstalling it due to the fact that my current ISP shapes traffic badly and restricts all torrent traffic.

I think another one I have heard people talking about is transmission. This client is command line based I think...I haven't tried it. 

Hope this helps

Acradon

---

### Post by x33a on 2009-01-29
the best in my opinion is deluge. vuze (previously azureus) is heavy on the resources and transmission lacks the feathers. deluge is the most comparable to utorrent, if you have been a fan of utorrent.

---

### Post by Mud.Knee.Havoc on 2009-01-29
Check with the private site first.  They'll have an FAQ with a listing of allowed or disallowed clients.  I think almost all sites allow Azureus.  Some private sites are pickier than others.  I've seen Transmission mentioned on some sites as being "officially allowed".  I've seen my favorite (rtorrent) listed as not allowed. :(

I use deluge without a problem.  But, as I said, it all depends on what the site admins allow.

---

### Post by m.musashi on 2009-01-29
Transmission is awesome. I love it. It's installed by default on newer version of Ubuntu so give it a try.

---

### Post by sluggerjd on 2009-01-29
Deluge guy I tried downloading the ubuntu one but it didnt work(32 bit and 64 bit ubuntu both didnt).. So I have just stuck it out with transmission and OMFG I am getting the best speeds I have ever gotten( up to 700 kbps per torrent download) which is insane and on a "freeleech".. So thanks for the suggestions and I would like to learn how to install deluge on my ibook g4(ppc) if anyone can walk me thru it a bit that would be great!

---

### Post by lidex on 2009-01-30
I recently switched to qBittorent from Transmission which I felt had limited features. Couldn't be happier. Love the rss support. Packages for 32 and 64 bit can be found at GetDeb:

[http://www.getdeb.net/app/qBittorrent]("http://www.getdeb.net/app/qBittorrent")

---

### Post by x33a on 2009-01-30
to install deluge , download the deb file for intrepid ibex from the official website (32 or 64 bit depending upon your architecture).

then, double-click the deb and click install, provide it with your password and you are good to go.

alternatively, you can install it with dpkg.

open a terminal

just type sudo dpkg -i filename.deb (filename = deluge file that you downloaded), and it'll install.

i am not sure if these instructions work for power pc though.

---

### Post by binbash on 2009-01-30
deluge is perfect

---

### Post by halovivek on 2009-01-30
I use utorrent using wine. It is working really fine.

---

### Post by rampageoberon on 2009-01-30
A nice and light CLI client is rtorrent

---

### Post by Lod on 2009-01-30
> **halovivek said:**
> I use utorrent using wine. It is working really fine.What is the advantage of using utorrent with wine instead of a native torrentclient?

I use torrentflux on my server. It's php based and available for me everywhere I have Internet access.

---

### Post by mkvnmtr on 2009-01-30
You can install Deluge from the package manager or add and remove. I use it on a G4 Ibook and really like it. Make sure when you set it up you don't port foward. Choose to use random ports. From watching the traffic on firestarter that seems put each connection on a different port and I encounter no blocking. It gives me the fastest speeds my ISP will provide.

---

### Post by rafaelsousa on 2009-01-30
ktorrent is a good one, and the one I'm always use.
It can encrypt data, avoiding traffic shaping. 

```
sudo apt-get install ktorrent
```

---

### Post by winterblues on 2009-01-30
I use Deluge. Always satisfied, never had a problem.

---

### Post by mkvnmtr on 2009-01-30
I just remembered you told me when you were installing that you do a lot of torrents. Try several clients to find the one that works best for you. I liked KTorrent but it quit working on my Ibook. Now I use Deluge and it is low resource. But there are several that work well. It depends on which you like. The nice thing you can download them and try them one at a time until you decide which you like.

---

### Post by Neural oD on 2009-01-30
I second rtorrent. This client rocks - and best of all it's command line - so u can use it with hardly any resources. Also by combining with screen - you can ssh into your machine from anywhere - even a slow connection - and control your downloads

---

### Post by hyper_ch on 2009-01-30
> **rampageoberon said:**
> A nice and light CLI client is rtorrent

> **Neural oD said:**
> I second rtorrent. This client rocks - and best of all it's command line - so u can use it with hardly any resources.

rTorrent FTW! However you should not use the one provided by the packages but use the SVN version. It has improved a lot.

---

### Post by Neural oD on 2009-01-30
> **hyper_ch said:**
> rTorrent FTW! However you should not use the one provided by the packages but use the SVN version. It has improved a lot.

Thanks for that hyper_ch - I should have mentioned that fact! :P

---

### Post by hyper_ch on 2009-01-30
rTorrent is one of the few things I compile myself. Rakshasa keeps adding new stuff all the time ;)

---

### Post by benmoran on 2009-01-30
I was a long time uTorrent user on Windows, so when I switched to Linux I eventually settled on Deluge (after trying EVERYTHING else). It was most similar to uTorrent, so it made me happy at the time. But I found Deluge to be a bit buggy and heavy for my tastes.  After a new install, I just stuck with Transmission. Its not feature rich, but it just grows on you. It does everything I need, and its super light-weight. I've been using their beta repository, and even those are stable for me. Much more so than Deluge.

---

### Post by tombom62 on 2009-01-30
> **Mud.Knee.Havoc said:**
> I've seen my favorite (rtorrent) listed as not allowed. :(

I use deluge without a problem.  But, as I said, it all depends on what the site admins allow.
WHAT?  REALLY??  Man, that's what I use:(

---

### Post by halovivek on 2009-01-30
> **Lod said:**
> What is the advantage of using utorrent with wine instead of a native torrentclient?

I use torrentflux on my server. It's php based and available for me everywhere I have Internet access.

I tried lot of built in torrent which comes from linux. The utorrent is really light weight and lot of options you can find.

---

