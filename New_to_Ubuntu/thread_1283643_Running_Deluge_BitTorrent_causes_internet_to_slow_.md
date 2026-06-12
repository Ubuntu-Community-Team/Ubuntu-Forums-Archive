---
title: "Running Deluge BitTorrent causes internet to slow to snail's pace"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-10-05
I'm downloading some torrents via the Deluge BitTorrent Client and what has become obvious is that my internet available for other stuff such as browsing becomes so slow that many pages can't load at all.

I've got Deluge set up to receive up to 12 streams simultaneously and to upload up to 12 streams as well. Is that too many? If so, what are good settings for that type of stuff that won't cause me problems surfing the net?

---

### Post by greyfox1 on 2009-10-05
What sort of connection do you have?

---

### Post by wojox on 2009-10-05
[http://ubuntuforums.org/showthread.php?t=1259923](http://ubuntuforums.org/showthread.php?t=1259923)

---

### Post by kaivalagi on 2009-10-05
> **wojox said:**
> [http://ubuntuforums.org/showthread.php?t=1259923](http://ubuntuforums.org/showthread.php?t=1259923)

Very good guide!

---

### Post by lovinglinux on 2009-10-05
> **kaivalagi said:**
> Very good guide!

Thank you ;)

---

### Post by Roger Allott on 2009-10-06
Yes, the guide is excellent. At least I now know what a seeder and a peer is!

I've trimmed my upload speeds etc. but now I'm getting something really weird. When I have Deluge and Firefox running, my internet connection goes completely (after a short while) and I need to reboot my machine.

I'm using virgin media home broadband, with a stated d/l limit of 10 Mbps.

I've run a speedtest and, without Deluge running, I seem to be hitting pretty close to that, but upload seems to be a pretty rubbish 0.47 Mbps.

During the short time I had Deluge and Firefox running, the speeds attained on speedtest were much lower - about 2.4 Mbps d/l and 0.11 Mbps u/l.

Does anyone here happen to know whether virgin is one of those ISPs that blocks ports used for BitTorrents?

---

### Post by ankspo71 on 2009-10-06
> **Roger Allott said:**
> Yes, the guide is excellent. At least I now know what a seeder and a peer is!

I've trimmed my upload speeds etc. but now I'm getting something really weird. When I have Deluge and Firefox running, my internet connection goes completely (after a short while) and I need to reboot my machine.

I'm using virgin media home broadband, with a stated d/l limit of 10 Mbps.

I've run a speedtest and, without Deluge running, I seem to be hitting pretty close to that, but upload seems to be a pretty rubbish 0.47 Mbps.

During the short time I had Deluge and Firefox running, the speeds attained on speedtest were much lower - about 2.4 Mbps d/l and 0.11 Mbps u/l.

Does anyone here happen to know whether virgin is one of those ISPs that blocks ports used for BitTorrents?

Hi,
Virgin Media, GB?  Check here:
[http://www.azureuswiki.com/index.php/Bad_ISPs](http://www.azureuswiki.com/index.php/Bad_ISPs)

Also, when you start reaching enough connections to give you trouble, check deluge's cpu usage in 'top', 'htop', or gnome system monitor. For some reason, a bit-torrent client's cpu usage dramatically increases according to transfer rate and number of transferring connections. Firefox 3.5+ seems to be working much better for me than 3.0+ was with a bit-torrent client running.

Right now I am running Transmission. I told it to use only 10 connections for downloads and 10 connections for uploads. I am also running transmission with a 'nice value' of 5, which makes transmission run with less priority. Even with a limited number of connections I can still download quickly and upload reasonably. Plus now it doesn't cause trouble for Firefox 3.5 or flash videos. I am still tweaking away to find the right balance of cpu usage, but I am in the right area.

I didn't have much interest in torrents until recently, when I saw people having trouble downloading and updating since the beta karmic was released...so I'm still learning as I go and my main interest is seeding. Hopefully something in what I said in the post will help you and others.
(sorry about rambling on)
James.

PS. I agree, the tutorial from the other poster above is great!

---

### Post by Nick Rhodes on 2009-10-07
I'm on Virgin's 10 meg setting and found that doing pure downloading of torrents at max speed (Ubuntu's iso torrents for example), is creating around 40KB of traffic out... now subtract that from the 80k max we can get up and only leaves you with 40KB usable for uploading.
So tune your upload settings around this 40KB up (try 3 upload slots to start) and set your download max speed between 60 and 80% of max if you want decent web surfing speed. Amount of download slots does not make a difference to resource hogging, but you want low as possible that keeps good speed, i vary between 4 and 8 torrents. What I found makes a difference is total download slots, too many causes router and network devices to hang, try a conservative setting of 100 connections and bump it up if you download speed suffers, but ive seen routers choke on as low as 200 max connections, mine struggles with more than 350 connections global, but i find on popular torrents 200 connections is enough for good speed.

Of course this may not help and you are suffering from a bug, but I've experienced hung router from too optimistic settings and the telltale is if doing nothing else the load in 1 min peaks above 1 (I have 1 core and this indicates processes are queueing up)

Cheers, Nick.

---

### Post by Roger Allott on 2009-10-08
> **Nick Rhodes said:**
> I'm on Virgin's 10 meg setting and found that doing pure downloading of torrents at max speed (Ubuntu's iso torrents for example), is creating around 40KB of traffic out... now subtract that from the 80k max we can get up and only leaves you with 40KB usable for uploading.
So tune your upload settings around this 40KB up (try 3 upload slots to start) and set your download max speed between 60 and 80% of max if you want decent web surfing speed. Amount of download slots does not make a difference to resource hogging, but you want low as possible that keeps good speed, i vary between 4 and 8 torrents. What I found makes a difference is total download slots, too many causes router and network devices to hang, try a conservative setting of 100 connections and bump it up if you download speed suffers, but ive seen routers choke on as low as 200 max connections, mine struggles with more than 350 connections global, but i find on popular torrents 200 connections is enough for good speed.

Of course this may not help and you are suffering from a bug, but I've experienced hung router from too optimistic settings and the telltale is if doing nothing else the load in 1 min peaks above 1 (I have 1 core and this indicates processes are queueing up)

Cheers, Nick.

Thanks for that. My settings are now:
200 max connections global, 
d/l speed limit of 175 KiB/s, 
upload speed limit of 30 KiB/s,
max upload slots 5,
total active 14,
total active downloading 8,
total active uploading 4.

Two things on these settings confuse me. 
First, what is the difference between 'max upload slots' and 'total active uploading'?
Second, what is the purpose of the 'total active' parameter? Surely it should just be the sum of 'total active downloading' and 'total active uploading', shouldn't it?

---

### Post by lovinglinux on 2009-10-08
> **Roger Allott said:**
> Two things on these settings confuse me. 
First, what is the difference between 'max upload slots' and 'total active uploading'?

"Total active uploading" is the number of different torrents would be allowed to upload at the same time. "Max upload slots" is the maximum number of peers you will be uploading to at the same time.

> **Roger Allott said:**
> Second, what is the purpose of the 'total active' parameter? Surely it should just be the sum of 'total active downloading' and 'total active uploading', shouldn't it?

I guess so :)

---

### Post by Roger Allott on 2009-10-08
> **ankspo71 said:**
> Hi,
Virgin Media, GB?  Check here:
[http://www.azureuswiki.com/index.php/Bad_ISPs](http://www.azureuswiki.com/index.php/Bad_ISPs)

Thanks. Virgin doesn't seem to have any more of an issue with torrents than other UK ISPs, but they do throttle bandwidth quite considerably for the top 5% of users.

In my opinion, that's not a bad policy. Although I signed up for unlimited bandwidth and 10 Mbps speed, I can accept some limitation during peak hours to help ensure complete coverage to all subscribers.

---

### Post by Roger Allott on 2009-10-08
Something I've noticed is that I'm much less likely to experience connectivity problems when Deluge is just running in the system tray. When Deluge is running its display screen and I try to open a page in Firefox or simply follow a link to a new page, that's when my connectivity is likely to vanish.

Has anyone else noticed this behaviour? Has anyone any ideas as to what's causing it? Or indeed, has anyone any solutions?

---

### Post by alphaniner on 2009-10-08
Are you running an up-to-date version?  The version in the repos was quite out of date last I checked.  I had all kinds of problems with it, including connectivity issues if I recall correctly.

---

### Post by Roger Allott on 2009-10-08
> **alphaniner said:**
> Are you running an up-to-date version?  The version in the repos was quite out of date last I checked.  I had all kinds of problems with it, including connectivity issues if I recall correctly.

Ooh, that's interesting!

The version I'm using comes from the Synaptic Package Manager and is version 1.1.6+dfsg-2ubuntu1

Why would the repository not have the latest version?

Which repository has the latest version?

---

### Post by alphaniner on 2009-10-08
Your version isn't as old as the one I had been running (I think it was 0.6, when the up-to-date version was 1.1.3 :shock: ) but it is still out of date.  I can't get to the official site because of my company's proxy, but [getdeb.net]("http://www.getdeb.net/search.php?keywords=deluge") has v1.1.9.  Your best bet though, would be to get it from [Deluge's PPA]("https://launchpad.net/~deluge-team/+archive/ppa").  Also, you might find help on their forums [http://www.deluge-torrent.org/]("http://www.deluge-torrent.org/").

---

### Post by Roger Allott on 2009-10-08
Scrap my last question. It's pretty obvious what needs to be done. Full instructions are at [https://launchpad.net/~deluge-team/+archive/ppa]("https://launchpad.net/~deluge-team/+archive/ppa").

I still don't understand why the core repositories contain apparently inferior versions of apps.

---

### Post by alphaniner on 2009-10-08
> **Roger Allott said:**
> I still don't understand why the core repositories contain apparently inferior versions of apps.

It's because Canonical doesn't actually maintain all the packages in the repos, some are handled by third parties.  I wish there were a disclaimer that packages may be out of date, but what can you do?  Meh, just be glad there's getdeb and the PPA system. :)

---

