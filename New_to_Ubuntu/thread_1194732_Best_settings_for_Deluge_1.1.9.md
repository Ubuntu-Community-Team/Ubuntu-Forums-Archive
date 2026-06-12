---
title: "Best settings for Deluge 1.1.9?"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by taminrob on 2009-06-23
I am wondering if anyone can help me get to those blazing fast dl speeds that I hear others talking about and as of yet, I can only dream about?

I am fairly new to the whole torrent thing, but really like what I have been able to do so far, but I am sure that there are a few tweaks that I can make to get more speed on my downloads.  

I am running Deluge 1.1.9.  I use a DSL Internet service with 6 Mb down, and roughly 4 kb up, and a Linksys WRT54gs router (using wired connection for the most part, though I do use wireless from time to time).

About the only thing I have done so far is to limit my upload speed to 150 kb while I am downloading.  What other tweaks and setting changes can I make to take advantage the resources that I have?  I realise that alot comes from the seed/leach ratio, I am just interested in the the areas that I have control over.

I am not opposed to using another torrent client, if there is a better one available, I just chose this one because it is user friendly and it seemed faster than Transmission.

Thanks for you help and advice.

Also, if it makes any difference, I have my PS3 and a DirecTV receiver connected to that router by Ethernet cable and a Wii  and a second laptop connected wirelessly, but only this computer is actively using bandwidth while downloading.

---

### Post by lovinglinux on 2009-06-23
Stick with  Deluge. It's the best client in my opinion.

Please post a screenshot of the result of [Speedtest.net](http://www.speedtest.net/), so I can have a better idea of your connection.

---

### Post by aeiah on 2009-06-23
are you aware that 6mbit internet does not mean you'll get 6 megabytes per second download?

download a few large files (like a linux iso) and allow them to settle in for a minute or two. download using firefox or wget or do a synaptic upgrade and see what download speed you're getting, and compare it to a well seeded torrent (either again, a large file like an ubuntu iso, or something on a private tracker with loads of seeders and hardly any leeches). is there much difference? i can squeeze 1225kb/s download out of my connection and can occasionally manage 1200 (1.2mb/s) in deluge, but usually 1.1mb/s. its about the same for other file downloads with firefox and wget if the server at the other end is fast and quiet. i havent really changed any settings in deluge. i cap my upload at 110kb/s (my max is about 125kb/s) although this is mostly because browsing grinds to a halt if my upload is maxed out through deluge.

---

### Post by Cheesemill on 2009-06-23
Even at your theoretical maximum speed of 6Mb/s the fastest speed you can ever hope to achieve is around 6000/8 = 750kB/s
 
What sort of speeds are you getting?
I suggest trying to download the Ubuntu 9.04 i386 Desktop torrent as a test as this should max out your connection easily.
_[COLOR=#0000ff][http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)[/COLOR]_[]("http://torrent.ubuntu.com:6969/file?info_hash=%60%D5%D8%23%28%B4Tu%11%FD%EA%C9%BFM%01%12%DA%A0%CE%00")

---

### Post by sadaruwan12 on 2009-06-23
Hi,

I also was faced by this question 'cos in my country we don't have the luxury  of MB bandwidth if some wants more bandwidth then hire the price we've to pay currently I'm on a 512kBps line and thats enough for me to download terabyte of data through deluge. We'll to help you I'm giving you some web links that might help you in boosting your performance and a calculator to calculate proper settings for your bandwidth.

[LIST]
[*][Link 1]("http://www.makeuseof.com/tag/10-ways-to-speed-up-torrent-downloads/")
[*][Link 2]("http://torrentfreak.com/speed-up-your-torrents/")
[/LIST]

For the [calculator]("http://infinite-source.de/az/az-calc.html")

And don't worry these posts might not mention your torrent client but the things they say to do is very much identical. Also the calculator might say that it's for azures another torrent client (Not Very Good) but the setting suggestion work with other clients as well, so don't worry about that.

Also it's very important that you get an idea about your true bandwidth speed to do that visit this link [http://www.speedtest.net/]("http://www.speedtest.net/") and get your true download speed remember to run this test couple of times to get a good reading. Also select the nearest sever for that this site automatically gives you a server that will give you the optimal speeds. So use this to get your true speed and use the calculator to calculate your settings for deluge and insert those setting to get the best speeds.

Buddy, stick with delude 'cos it's the best one in the GPL world and it's rival is uTorrent but it only runs on windows.

*Hope this helps you*

---

### Post by taminrob on 2009-06-23
Thanks for the input so far.  Yes, I know some about the limitations created by seeds/leaches, but unless these people are not telling the truth about having fully downloading a given file (movie) within 3 hours of its posting, then I would think there should be something that I can change that will at least help improve my dl times.  

My current average per torrent is about 20 kb/s, but I have had a few that have reached 150 - 200 kb/s, but only two that I can think of.

When I Download updates for Ubuntu, I can regularly get 2.5 - 4.0 Mb/s.

Here is the requested result from Speedtest,

[http://www.speedtest.net/result/502397920.png](http://www.speedtest.net/result/502397920.png)

I know (or at least think) that I wont be able to compare to the people running a T1 or T3 or some such mass speed connection, but I would like to get the most of what I have available.

---

### Post by Cheesemill on 2009-06-23
Have you opened the correct ports on your router and forwarded them to Deluge?

Also you have contention ratio to consider, most residential broadband (at least in the UK) has a ratio of 50:1 meaning that you are potentially sharing your 6Mb download speed with up to 49 other people.

---

### Post by billgoldberg on 2009-06-23
> **taminrob said:**
> I am wondering if anyone can help me get to those blazing fast dl speeds that I hear others talking about and as of yet, I can only dream about?

I am fairly new to the whole torrent thing, but really like what I have been able to do so far, but I am sure that there are a few tweaks that I can make to get more speed on my downloads.  

I am running Deluge 1.1.9.  I use a DSL Internet service with 6 Mb down, and roughly 4 kb up, and a Linksys WRT54gs router (using wired connection for the most part, though I do use wireless from time to time).

About the only thing I have done so far is to limit my upload speed to 150 kb while I am downloading.  What other tweaks and setting changes can I make to take advantage the resources that I have?  I realise that alot comes from the seed/leach ratio, I am just interested in the the areas that I have control over.

I am not opposed to using another torrent client, if there is a better one available, I just chose this one because it is user friendly and it seemed faster than Transmission.

Thanks for you help and advice.

Also, if it makes any difference, I have my PS3 and a DirecTV receiver connected to that router by Ethernet cable and a Wii  and a second laptop connected wirelessly, but only this computer is actively using bandwidth while downloading.

If you are using ADSL you should lower your upload speed as much as possible. I set mine at around 5kb/sec when downloading and then at unlimited after I'm done downloading (for seeding).

Unlike cable, download speeds on ADSL are highly reduced if you are uploading.

Also limit the numbers of peers that can connect to your box to something around 30-40.

Also, some torrents are just slow. I usually only download from private torrent trackers, where my line gets maxed out immediatly, but on public trackers those speeds are much slower most of the time.

---

### Post by Cheesemill on 2009-06-23
> **billgoldberg said:**
> If you are using ADSL you should lower your upload speed as much as possible. I set mine at around 5kb/sec when downloading and then at unlimited after I'm done downloading (for seeding).

I don't think you have to go that low. I've found that limiting it to around 80% of maximum wont impact on your download speed, you just need to leave enough upload capacity for the bittorrent protocol overhead.

---

### Post by taminrob on 2009-06-23
Ok, two quick replies.

First - Which setting do I change to limit how many people are accessing me?

Second - I have random ports enabled in deluge but have made no changes to my router...do I need to?

Also, I use Demonoid, ( they seem to have good quality torrents without alot of the crap virus/trojan filled files that some have) as far as I know, they are a private tracker.

---

### Post by Cheesemill on 2009-06-23
> **taminrob said:**
> Ok, two quick replies.

First - Which setting do I change to limit how many people are accessing me?

Second - I have random ports enabled in deluge but have made no changes to my router...do I need to?

Also, I use Demonoid, ( they seem to have good quality torrents without alot of the crap virus/trojan filled files that some have) as far as I know, they are a private tracker.

If you open up preferences in Deluge and go to the Bandwidth page you'll see the setting for connections (you can also right-click on the icon in the far bottom-left of the main window).

If you now head to the Network section you can choose your incoming port, de-select 'Use random ports' and choose one yourself (between 10,000 and 60,000 to be safe).
You now need to forward this port number from your router to your PC. The method for this varies from router to router so I'm going to point you to [www.portforward.com](www.portforward.com) for detailed instructions.

---

### Post by lovinglinux on 2009-06-23
> **taminrob said:**
> Thanks for the input so far.  Yes, I know some about the limitations created by seeds/leaches, but unless these people are not telling the truth about having fully downloading a given file (movie) within 3 hours of its posting, then I would think there should be something that I can change that will at least help improve my dl times.

The speed you download depends on several factors:

[list][*] the limit of your download speed
[*] the limit of your upload speed
[*] the limit of upload speed of those you are downloading from
[*] the the number of peers also downloading from those you are downloading from
[*] the number of torrents being uploaded by those you are downloading from
[*] the number of peers you can connect to[/list]

So unless the swarm has hundreds or thousands of peers and good seeder/leecher ratio, the download speed will probably not be near your download speed limit. Unless you connect to very generous peers with huge upload bandwidth. I love when I connect o Japaneses. They have unbelievable fast connections  :) 

> **taminrob said:**
> My current average per torrent is about 20 kb/s, but I have had a few that have reached 150 - 200 kb/s, but only two that I can think of.

You have a 6.4 Mbps download and 0.43 Mbps upload connection. If we convert this to KiB/s, they would be 780 KiB/s down and 52.5 KiB/s up. This basically means that your ISP is clever when selling their plans, because you have a very nice download speed, but a very limited upload speed. What does this means in terms of torrents? The torrent protocol works in a way that the more you give, the more you get. This means that even considering that you have 780 KiB/s download speed, your upload speed would be limiting your torrent download considerably.

To maximize your connection you should set you upload limit to 80% of your real upload limit. If you set the upload to unlimited, it would have an adverse effect. I don't know how to explain this, but it has something to do with clogging your network. So, set Deluge bandwidth options like this:

Maximum Connections: 150
Maximum upload slots: 6
Maximum Download Speed (KiB/s): -1.0 (unlimited)
Maximum Upload Speed (KiB/s): 42
Maximum Half-Open Connections: 50
Maximum Connection Attempts per Second: 20

Leave the default values for "Per Torrent Bandwidth Usage".

Your average download speed is definitely not good. My connection is 480 KiB/s down and 74 KiB/s up. My average speed is about 60-80 KiB/s, but I usually get speeds of 200 KiB/s with regular torrents and 400 KiB/s if I'm downloading an Ubuntu release.

Since you can get 200 KiB/s eventually, I think problem might be the torrents you are downloading or maybe you are not forwarding the port to your router properly. If you do not forward your port, you will still be able to download and eventually get high speed downloads, but most of the time you won't connect to many peers and your download speed will be reduced. The more peers you connect, more likely that you will get better speeds.

Try to find other torrents with at least a few hundred of peers and a seed/leecher ratio of at least 1:1. Very fast torrents usually have thousands of peers and a seed/leecher ratio of 2:1 or above.

Also try to share only a single torrent at any given time and limit the number of seeding torrents when you are downloading. For example you can set the "queue" options like this:

Total active: 2
Total active downloading: 1
Total active seeding: 1

But pause any seeding torrents when you are downloading.

---

### Post by lovinglinux on 2009-06-23
> **taminrob said:**
> First - Which setting do I change to limit how many people are accessing me?

Already explained in my previous post

> Maximum Connections: 150


> **taminrob said:**
> Second - I have random ports enabled in deluge but have made no changes to my router...do I need to?

Yes, you need. That's probably the cause of your ,low download speeds. As I said in the previous post, you will still be able to download without forwarding the port, but number of peers you connect will be less than optimal. The more user you connect, bigger the chance of getting high download speeds.

As already suggested, look at [http://portforward.com/](http://portforward.com/) for instructions on how to forward the port from your router. It would be easier if you set Deluge to use a single port for download and forward the same port on your router. Leave the upload port as random, since they are not affected by port forwarding settings. If you want to use random ports for download too, then you should enable UPnP on Deluge and on your router. The UPnP will open the necessary ports automatically. Unfortunately, this wasn't working on Deluge recently. Additionally, some people will argue that using UPnP is a security risk. I use it and never had a problem with it. It's up to you, but you should know that there are risks (google it). 

If you use firewall rules, then you also need to open the port used for downloading on Deluge and forwarded by the router, otherwise it will be blocked.

---

### Post by Cheesemill on 2009-06-23
What a fantastic post lovinglinux
You couldn't get better support than that if you paid for it !!!!
:KS:KS:KS

---

### Post by lovinglinux on 2009-06-23
> **Cheesemill said:**
> What a fantastic post lovinglinux
You couldn't get better support than that if you paid for it !!!!
:KS:KS:KS

Thank you. This is a subject that I like to talk about and I have researched a lot when I started to use torrents. There are a few settings that I still don't understand very well, but then I use values recommended by the developers of the client ;) I'm very happy with my download speeds tho :)

---

### Post by Cheesemill on 2009-06-23
> **lovinglinux said:**
> I'm very happy with my download speeds tho :)

Me too. I max out at 1.3 MiB's on the Ubuntu torrents with Deluge, my routers synced at 11.1 Mb so I think I'm the only person on my line :)

---

### Post by bubbhasdance on 2009-06-23
Sorry to kinda-threadjack here, but I'm having the same problems as the original poster. My download speed (tested) is about 5 MiB/s and my upload speed is about 1 MiB/s (horrible I know -_-) I usually get about 20-70 KiB/s on Deluge, sometimes getting above that. Recently, my speeds on Deluge have been very slow, creeping around 0.5-10 KiB/s. 

If lovinglinux doesn't mind, could I possibly get some guides to changing my torrent settings as well? Thanks in advance!

---

### Post by lovinglinux on 2009-06-23
> **bubbhasdance said:**
> Sorry to kinda-threadjack here, but I'm having the same problems as the original poster. My download speed (tested) is about 5 MiB/s and my upload speed is about 1 MiB/s (horrible I know -_-) I usually get about 20-70 KiB/s on Deluge, sometimes getting above that. Recently, my speeds on Deluge have been very slow, creeping around 0.5-10 KiB/s. 

Since the problem started recently, it is possible that your ISP started throttling torrent connections. I would recommend using a download port different from the usual 6881-6889 range. Use any port between 49152 and 65535. Additionally, set the Network encrypton settings like this:

Inbound: Forced
Outbound: Forced
Level: Full Stream
Encrypt Entire Stream: selected

> **bubbhasdance said:**
> If lovinglinux doesn't mind, could I possibly get some guides to changing my torrent settings as well? Thanks in advance!

I don't mind, but I'm not sure if there is something different from the previous settings that I could recommend. Just set the upload limit to 98 instead of 42.

What speeds do you get when downloading an Ubuntu release torrent?

EDIT: you could also use this:

Maximum Connections: 250
Maximum upload slots: 8
Maximum Download Speed (KiB/s): -1.0 (unlimited)
Maximum Upload Speed (KiB/s): 98
Maximum Half-Open Connections: 50
Maximum Connection Attempts per Second: 20

---

### Post by bubbhasdance on 2009-06-23
Thanks so much, this worked perfectly. I am a new Ubuntu user and I must say, the sheer size of the community here is amazing.

---

### Post by lovinglinux on 2009-06-23
> **bubbhasdance said:**
> Thanks so much, this worked perfectly. I am a new Ubuntu user and I must say, the sheer size of the community here is amazing.

Great. What's your speed now?

---

### Post by taminrob on 2009-06-23
Thank you!  I really appreciate the help.  I will make these changes and let you know how it went.

---

### Post by Hatfield on 2009-07-06
Great thread!  I'm learning a ton!

So I've been tweaking my Deluge settings all day and have a couple questions.  This shouldn't be considered a thread hijack (I hope) since it also relates to Deluge settings.

I have a DSL connection (2000ft from nearest "central office"; D/L 1.58 Mbps; U/L 0.22Mbps).  And my speeds are sporadic at best(between 40KiBs and 180KiBs).  I've followed the directions in this thread given my bandwidth connection and said calculators.
But I've tweaked Deluge settings so much, I've forgotten the default settings for "Per Torrent Bandwidth Usage"...

> **lovinglinux said:**
> ...

Leave the default values for "Per Torrent Bandwidth Usage".
...

Can someone let me know the default settings?

---

### Post by lovinglinux on 2009-07-07
> **Hatfield said:**
> Great thread!  I'm learning a ton!

So I've been tweaking my Deluge settings all day and have a couple questions.  This shouldn't be considered a thread hijack (I hope) since it also relates to Deluge settings.

I have a DSL connection (2000ft from nearest "central office"; D/L 1.58 Mbps; U/L 0.22Mbps).  And my speeds are sporadic at best(between 40KiBs and 180KiBs).  I've followed the directions in this thread given my bandwidth connection and said calculators.
But I've tweaked Deluge settings so much, I've forgotten the default settings for "Per Torrent Bandwidth Usage"...



Can someone let me know the default settings?

-1 for all settings

---

