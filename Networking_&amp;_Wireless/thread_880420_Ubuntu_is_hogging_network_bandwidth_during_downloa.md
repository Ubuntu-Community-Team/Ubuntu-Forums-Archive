---
title: "Ubuntu is hogging network bandwidth during downloads"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by tsdemented on 2008-08-05
Hi there.

I am on a network with my brother's (Windows XP) PC and my Laptop (Windows XP). We have a cable modem attached to a router, which is attached to my phone router for Vonage (Which goes to my PC and my laptop).

When I am using Ubuntu and perform a download, either through HTTP or torrents, it will hog up the bandwidth over the whole network and the Windows XP machines will run extremely slow online. It might take 20-30 seconds to load up [www.google.com](www.google.com), for example.

I've tried re-booting up Windows XP and performing the same downloads. It does not negatively effect the bandwidth of my laptop or my brother's PC when I'm using Windows XP, so I assume that there is something wrong with my setup in Ubuntu.

Is there a way for me to limit the bandwidth, or is there another way to solve this?

Thank you

---

### Post by spin2cool on 2008-08-05
Most bittorent clients will allow you to throttle your download and upload speeds.  Both are important, as the other computer in your home has to send responses to web servers before receiving data in return.

For other types of traffic, you might look into a router that allows you to do bandwidth throttling.  (alternately, see if you can install DD-WRT on your router, which should allow you to do the same)

---

### Post by hyper_ch on 2008-08-05
as mostly the download bandwidth exceeds the upload one by far (in my case 10 : 1) I'd suggest to throttle the max. upload from your torrent client to 90-95% of the available upload OR you could use QoS to give a low priority on p2p traffic.

Depending on your router I'd even suggest Tomato WRT over DD-WRT. I think the QoS is a lot better in Tomato...

---

### Post by stinger30au on 2008-08-05
another way is to asign the ubuntu box a static ip and if you have a decent router you cant throttle it via the router config as well

---

### Post by flytripper on 2008-08-05
always leave some bandwidth using the throttle function on the client.... plus  it tends to hog network resources anyway.

---

### Post by tsdemented on 2008-08-05
I'm using Deluge for torrents and I already have it set to limit download speed to 40kbps and upload speed to 3kbps, and it seems like as long as it's running, everything else on the network runs like crap. We have a cable connection and I can download at say, 300kbps at a given time, so why at that time would 40kbps be slowing down the entire network? I would think that it would have no noticeable effect on other computers in the network, but it certainly does.

---

### Post by Living2007 on 2008-08-05
> **tsdemented said:**
> Hi there.

I am on a network with my brother's (Windows XP) PC and my Laptop (Windows XP). We have a cable modem attached to a router, which is attached to my phone router for Vonage (Which goes to my PC and my laptop).

When I am using Ubuntu and perform a download, either through HTTP or torrents, it will hog up the bandwidth over the whole network and the Windows XP machines will run extremely slow online. It might take 20-30 seconds to load up [www.google.com]("http://www.google.com"), for example.

I've tried re-booting up Windows XP and performing the same downloads. It does not negatively effect the bandwidth of my laptop or my brother's PC when I'm using Windows XP, so I assume that there is something wrong with my setup in Ubuntu.

Is there a way for me to limit the bandwidth, or is there another way to solve this?

Thank you
Try another BitTorrnet client on you Ubuntu PC, also, try to decrease the amount of Tracffic coming through to your computer.

Another thing to keep in mind is that once data arrives to your router, the bandwidth changes and your router might not have a big bandwidth like what the internet has. So if a computer is hoging most of the traffic, other PC (depeding on where slowness is) will be affected.

---

