---
title: "Deluge questions"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2009-03-05
Hy all!
I'm new to this torrent stuff, so I have a bunch of questions.I use Deluge for downloading.
1.Is it good, or you suggest to use another client?
2.In "Deluge" in the upload section, I have 2 numbers.For example 798.0 MB (16.4 MB).What does the number in parentheses signifies?
3.If I add all the numbers from the upload section I get around 8 GB, but on the site ([http://www.torrentbits.ro](http://www.torrentbits.ro)) I'm only credited with 2.84 GB.Any idea why?
4.Do I have to configure the firewall so deluge can work properly? My upload is really poor, in this manner I will never have a good ratio...The "random port" option is ticked and when I press "Test active port" I get "TCP port 59558 closed on 92.80.55.251" What does that mean?
Thanks!

---

### Post by cb951303 on 2009-03-05
> **Troll_the_Great said:**
> Hy all!
I'm new to this torrent stuff, so I have a bunch of questions.I use Deluge for downloading.
1.Is it good, or you suggest to use another client?
2.In "Deluge" in the upload section, I have 2 numbers.For example 798.0 MB (16.4 MB).What does the number in parentheses signifies?
3.If I add all the numbers from the upload section I get around 8 GB, but on the site ([http://www.torrentbits.ro](http://www.torrentbits.ro)) I'm only credited with 2.84 GB.Any idea why?
4.Do I have to configure the firewall so deluge can work properly? My upload is really poor, in this manner I will never have a good ratio...The "random port" option is ticked and when I press "Test active port" I get "TCP port 59558 closed on 92.80.55.251" What does that mean?
Thanks!

1. It's arguably the best (feature-wise)
2. 798 is probably the  size of the file you downloaded and the one in parenthesis is how much you uploaded for the time being.
3. Trackers may lag, wait a few hours.
4. You don't have to configure your firewall but you can forward a port if it says "closed".
Basically, you should setup your network interface with a static IP.
Then go to router settings and forward the port you will use to that static local ip. Here is a good start: [http://portforward.com/](http://portforward.com/) When it says open for that port, you're good to go :popcorn:

---

### Post by sleepyjon on 2009-03-05
> **cb951303 said:**
> 1. It's arguably the best (feature-wise)
2. 798 is probably the  size of the file you downloaded and the one in parenthesis is how much you uploaded for the time being.
3. Trackers may lag, wait a few hours.
4. You don't have to configure your firewall but you can forward a port if it says "closed".
Basically, you should setup your network interface with a static IP.
Then go to router settings and forward the port you will use to that static local ip. Here is a good start: [http://portforward.com/](http://portforward.com/) When it says open for that port, you're good to go :popcorn:

I use deluge, and 2 is:

Total uploaded(Total uploaded for this session)

---

### Post by Troll_the_Great on 2009-03-05
> **cb951303 said:**
> 1. It's arguably the best (feature-wise)
2. 798 is probably the  size of the file you downloaded and the one in parenthesis is how much you uploaded for the time being.
3. Trackers may lag, wait a few hours.
4. You don't have to configure your firewall but you can forward a port if it says "closed".
Basically, you should setup your network interface with a static IP.
Then go to router settings and forward the port you will use to that static local ip. Here is a good start: [http://portforward.com/](http://portforward.com/) When it says open for that port, you're good to go :popcorn:

3.I have the account for a week now, isn't that enough for the tracker to update itself?
4.If I do the port forwarding thing, will I get better results?

PS:The link you gave me is for windows users....

---

### Post by cb951303 on 2009-03-05
> **Troll_the_Great said:**
> 
4.If I do the port forwarding thing, will I get better results?

PS:The link you gave me is for windows users....

yes you will. 
that site is for routers not for a specific OS.

---

### Post by mkvnmtr on 2009-03-05
That port foward link will be the same for any distro. Look for your router and it will tell you how to set up a static address. It will also tell you how to open a port. I set it up on my mac system so still have a static address but I have never done it on linux and all three of my machines max out my allowed speed from my ISP.

---

### Post by cb951303 on 2009-03-05
It's really not that difficult
Here is a screenshot of my settings.

192.168.1.1 is my router's IP. Netmask should be same as in screenshot.
Local static IP can be (by default) anything between (router IP) x.x.x.1 and x.x.x.255, so I chose 192.168.1.101 :popcorn:

PS: Network manager had a nasty bug (I don't know if it's fixed) that prevents these settings to be saved. But there is a workaround that I don't remember now, you can search the forums.

---

### Post by Troll_the_Great on 2009-03-05
My router is a Huawey EchoLife HG 510.I don't find in the list Deluge...Can somebody guide me step by step with this port forwarding stuff?

---

### Post by cb951303 on 2009-03-05
[http://www.portforward.com/english/routers/port_forwarding/Huawei/HG510/Utorrent.htm](http://www.portforward.com/english/routers/port_forwarding/Huawei/HG510/Utorrent.htm)

no settings for deulge but utorrent is close enough. any other bittorrent client is close enough. just look for the same settings under deluge preferences

---

### Post by Troll_the_Great on 2009-03-05
The problem is I have to set up a static IP adress and the guide is only for Mac, Windows and XBox, no linux setup...:(
[http://www.portforward.com/networking/staticip.htm](http://www.portforward.com/networking/staticip.htm)

---

### Post by cb951303 on 2009-03-05
> **Troll_the_Great said:**
> The problem is I have to set up a static IP adress and the guide is only for Mac, Windows and XBox, no linux setup...:(
[http://www.portforward.com/networking/staticip.htm](http://www.portforward.com/networking/staticip.htm)

I just sent a screenshot. You missed it I think :D Look at post #7 in this thread

---

### Post by MrWES on 2009-03-05
[http://old.basis-net.ru/device/huawei/smartax/pdf/hg510.pdf]("http://old.basis-net.ru/device/huawei/smartax/pdf/hg510.pdf")

That appears to be the manual for your router; several sections on port forwarding and routing.

I didn't see anything for setting a static IP from the router. Although, I can do that from my linksys -- I'm not familiar with this brand/model.

Bill

---

### Post by MrWES on 2009-03-05
> **cb951303 said:**
> 
PS: Network manager had a nasty bug (I don't know if it's fixed) that prevents these settings to be saved. But there is a workaround that I don't remember now, you can search the forums.

[http://ubuntuforums.org/showthread.php?t=974382]("http://ubuntuforums.org/showthread.php?t=974382")

That's the thread for that static IP work around.

Bill

---

### Post by cb951303 on 2009-03-05
> **MrWES said:**
> [http://ubuntuforums.org/showthread.php?t=974382]("http://ubuntuforums.org/showthread.php?t=974382")

That's the thread for that static IP work around.

Bill
Actually I remembered that there is simpler one. Abuse the "System Setting" and "Connect Auto" check buttons in "Auto" until they are really unchecked. Create new connection for static IP. Check both of them and it should work :popcorn:

---

### Post by Troll_the_Great on 2009-03-08
I manage to open my ports, though I don't know if I did it the right way.I followed the tutorial from [http://portforward.com/](http://portforward.com/) , but it wasn't enough, so I installed firestarter and I closed the firewall.That was the only way I could receive the message:
```
TCP port 50000 open on 92.85.54.106

Yay! :-)
``` 
I don't know if this was a bright idea or not, I was hoping you will tell me :D
Anyway,I have another request.Can you please me tell me exactly what settings should I set? I followed a tutorial, but it was for uTorrent, and I was hoping for something more personalized :)
Thanks!

---

### Post by cb951303 on 2009-03-08
> **Troll_the_Great said:**
> I manage to open my ports, though I don't know if I did it the right way.I followed the tutorial from [http://portforward.com/](http://portforward.com/) , but it wasn't enough, so I installed firestarter and I closed the firewall.That was the only way I could receive the message:
```
TCP port 50000 open on 92.85.54.106

Yay! :-)
``` 
I don't know if this was a bright idea or not, I was hoping you will tell me :D
Anyway,I have another request.Can you please me tell me exactly what settings should I set? I followed a tutorial, but it was for uTorrent, and I was hoping for something more personalized :)
Thanks!

the port number or the static IP number you set doesn't matter at ALL. As long as it says open you're ok. But I don't know about the firewall. I can open ports without messing with firewall...

---

### Post by Troll_the_Great on 2009-03-08
> **cb951303 said:**
> the port number or the static IP number you set doesn't matter at ALL. As long as it says open you're ok. But I don't know about the firewall. I can open ports without messing with firewall...

I was referring to the firewall when I said that I don't know if it was such a bright idea :)

---

### Post by cb951303 on 2009-03-08
> **Troll_the_Great said:**
> I was referring to the firewall when I said that I don't know if it was such a bright idea :)

I know I replied for this part :D > 
I followed a tutorial, but it was for uTorrent, and I was hoping for something more personalized 

edit: ah sorry, I get it, you mean a more personalized setting for firewall instead of turning it off?

---

### Post by Troll_the_Great on 2009-03-08
> **cb951303 said:**
> edit: ah sorry, I get it, you mean a more personalized setting for firewall instead of turning it off?

Yes,and for deluge, because there are lots of settings, like "Enable Main Line DHT", "NAT-PMP", "Peer exchange", "Local Peer Discovery" and so on.I would like that someone who is using deluge to tell me exactly what to set.
Cheers!

---

### Post by gandaran on 2009-03-08
Troll_the_Great
deluge may be the best torrent client feature-wise but to get top download speeds it needs a lot of incoming ports opened, installing the firewall will complicate things, in my opinion the default ubuntu torrent application (transmission) is excellent if not better than deluge, only needs one open port and very fast, in fact I always get better results with transmission.

---

### Post by cb951303 on 2009-03-08
> **Troll_the_Great said:**
> Yes,and for deluge, because there are lots of settings, like "Enable Main Line DHT", "NAT-PMP", "Peer exchange", "Local Peer Discovery" and so on.I would like that someone who is using deluge to tell me exactly what to set.
Cheers!

enabling DHT is a good idea, it lets you download files directly from DHT supported clients.

as long as your port is opened manually NAT, UPNP etc. won't have an effect. it doesn'T matter if they are enabled or not.

---

### Post by Troll_the_Great on 2009-03-08
> **cb951303 said:**
> enabling DHT is a good idea, it lets you download files directly from DHT supported clients.
Hmmm....I saw in a forum that enabling DHT can damage your ratio because your upload is not taken into account (at least with DHT supported clients).Another problem is that is a big difference(almost 20 GB) between the upload I see in Deluge and in the snatch list.Why?

---

### Post by Troll_the_Great on 2009-03-10
So?

---

### Post by cb951303 on 2009-03-10
> **Troll_the_Great said:**
> So?

I have no idea why tracker and actual stats differ but I'm pretty sure in theory DHT doesn't affect ratio because, firstly the upload/download done with DHT is not registered by tracker and secondly, even if it was, since it's able to do both download and upload, ratio would stay the same.

PS: Ah that also clarifies the difference between your client stats and tracker. Could you tell if there is any difference between downloads too?

---

### Post by Troll_the_Great on 2009-03-10
> **cb951303 said:**
> PS: Ah that also clarifies the difference between your client stats and tracker. Could you tell if there is any difference between downloads too?

There are only minor differences between Deluge and tracker in the download section (about 2-3 MB).
And DHT is turned off, so that's nothing to clarify the difference between client and tracker in the upload section.

---

### Post by Troll_the_Great on 2009-03-13
Bump!

---

### Post by Troll_the_Great on 2009-03-13
> **bgrand said:**
> Open a specific port from your router. Do not use random port option.

I already did that, I don't use the random port option.

---

### Post by Troll_the_Great on 2009-03-14
....

---

