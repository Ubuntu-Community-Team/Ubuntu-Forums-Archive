---
title: "Can I give Firefox or Konqueror or ... priority in using bandwidth?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by 1002285 on 2009-02-17
I'd like to use a bittorrent client and get a good download speed with it, but at the same time I would like Firefox to have priority in using bandwidth over the bittorrent client.
I use Vuze and I have not found a way to have Vuze working without affecting very much my work with FF. Is there a way to do that?

(I'm also not really able to make Vuze take full advantage of my connection speed - when downloading, i.e, packages with Synaptic, the DL speed is much greater than at the best times with Vuze. But nevertheless - when Vuze is working, FF is very-very slow. But I guess this is because I cannot use Vuze settings).

---

### Post by mkvnmtr on 2009-02-17
I can't help with that app but some general things that might help. Vuse uses a lot of resources for a torrent client. Transmission uses quite a bit less but I like Deluge. It gives me most of the information of vuse without the high cpu usage. You need to find your max bandwidth. The speed you get from the repositories is usually a good indication. Then set your max torrent bandwidth to about 90% of that figure. That should leave enough for your browser to work ok. You can of course adjust this as you wish later on. Usind adblocker and noscript will help on the speed of your browser also because you won't have to use your bandwidth to download adds.

---

### Post by MrWES on 2009-02-17
> **1002285 said:**
> I'd like to use a bittorrent client and get a good download speed with it, but at the same time I would like Firefox to have priority in using bandwidth over the bittorrent client.
I use Vuze and I have not found a way to have Vuze working without affecting very much my work with FF. Is there a way to do that?

(I'm also not really able to make Vuze take full advantage of my connection speed - when downloading, i.e, packages with Synaptic, the DL speed is much greater than at the best times with Vuze. But nevertheless - when Vuze is working, FF is very-very slow. But I guess this is because I cannot use Vuze settings).


I don't know what your setup is; whether or not you are behind a router or what. I have a linksys router and I installed tomato; a third party firmware for the router. One of the best features it has is customizable QOS settings; Quality of Service. It allows you to set priority bandwidth to certain ports, etc. Might be worth looking into.

Bill

---

### Post by hatten on 2009-02-17
> **mkvnmtr said:**
> I can't help with that app but some general things that might help. Vuse uses a lot of resources for a torrent client. Transmission uses quite a bit less but I like Deluge. It gives me most of the information of vuse without the high cpu usage. You need to find your max bandwidth. The speed you get from the repositories is usually a good indication. Then set your max torrent bandwidth to about 90% of that figure. That should leave enough for your browser to work ok. You can of course adjust this as you wish later on. Usind adblocker and noscript will help on the speed of your browser also because you won't have to use your bandwidth to download adds.
If you do like this, the torrent will run at 90% all the time, even when firefox isn't used...Meaning the download will take 10% longer time!

---

### Post by Blueball32 on 2009-02-17
> **hatten said:**
> If you do like this, the torrent will run at 90% all the time, even when firefox isn't used...Meaning the download will take 10% longer time!

Yeah but most torrents won't use 100% of bandwidth...that screws your calc ;)

---

### Post by mkvnmtr on 2009-02-17
Well hatten your right but if I was in a hurry I would just buy the stuff. Seriously it only takes 30 seconds to change the settings if you are not using something else. I use the browser and Thunderbird for business and like it to work with moderate speed. My bigger problem is having 200 or more connections at once and the router is the bottle neck. For some content it would probably be better to use IRC with only one connection.

---

### Post by davidsrsb on 2009-02-17
Some ISPs throttle your bandwidth if they detect P2P. This means that P2P will make you browsing crawl even if you restrict its bandwidth

ISP can also treat different ports unequally, my ISP puts http through a proxy with very poor performance.

---

### Post by hatten on 2009-02-18
> **Blueball32 said:**
> Yeah but most torrents won't use 100% of bandwidth...that screws your calc ;)
yeah i know, but when i downloaded ubuntu, kubuntu and xubuntu it was impossible to surf the web without changing options, and if i stay at a site reading in 5 minutes i lose some time at my torrents. I don't like changing settings every time i leave the computer

---

