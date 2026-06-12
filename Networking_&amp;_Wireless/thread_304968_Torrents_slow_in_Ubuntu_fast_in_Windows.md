---
title: "Torrents slow in Ubuntu fast in Windows"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by Tilex on 2006-11-22
Hi there,  I've been looking around in the forum for a while now, but no post seems to solve my problem...

In Windows, I use(d) BitLord for downloading torrent files and it works very well with download speeds reaching my ISP limit (320Kb/s) and upload speeds set to 80% of my theoretical max (80 kb/s) so I don't flood my connection.

In Ubuntu, I get max up/down speeds of roughly 3Kb/s, which makes it quite long to download a 4-gig iso.  
Now the only difference between Windows and Ubuntu seems to be the built-in firewall in Ubuntu (firestarter? iptables?) and the different program used (I use KTorrent or Azureus, both with limited success), which can use different ports than BitLord in Windows.  My Linksys router is set the same as in Windows, and I checked what ports BitLord was using (65535) and changed for those ports in KTorrent, and I also disabled uPnP AND Firestarter firewall and no success.
Anyone has the magic touch that I don't seem to have?

By the way, thanks to everyone who has helped other posts because I have read so many of them so far and they solved most of my problems!! :-D

---

### Post by stoeptegel on 2006-11-24
Does the normal web surfing suffers too (very sluggish) when you use BitTorrent? If not, it's probably a configuration of the client which doesn't make sense.

---

### Post by Tilex on 2006-11-24
No Web surfing is fine...

I think it's related to the number of peers I am able to connect to because I manage to top my upload limit off, compared to my download limit that ocsillates between 0 and 15kb/s all the time.  That is even though I am downloading a very popular torrent which I would download at high speeds (200 kb/s) with BitLord in Win.
Maybe the uPnP or something but my router (linksys WRT54GS) admin menu doesn't let me see any option related to uPnP...

---

### Post by alican timur on 2006-11-26
the same thing happens to me. i'm using deluge and i was using bitcomet in windows.

---

### Post by zgornel on 2006-11-26
Try using Azureus and reading some configuration tutorials. Azureus is very complex so you'll get a better chance of solving the speed issues.

---

### Post by meng on 2006-11-26
I get pretty quick downloads with Azureus, but I had to set up the portforwarding on my router to get NAT working properly. Yes, Azureus is more resource-hungry but the GUI and color-coding can be helpful if you're tweaking to optimize your settings.

---

### Post by alanpotpot on 2006-11-26
I have some problems with azureus as well. I have port forwarding enabled on the router but for some reason it would not work. What I usually do is open the test the ports in windows using azureus and utorrent and then go back to ubuntu. After that my torrents health is now green. 

Has anyone have a theory on why this happen?

---

### Post by mgmiller on 2006-11-26
I have found no difference between windows and Ubuntu speeds for bittorrent downloading.  I use Azureus in both OS's in both cases the computers are not using DHCP to get IP addresses from the router.  I set my computer as a fixed IP 192.168.1.4 for example.  Then in the linksys router under the "gaming" tab, I use port forwarding to set the range of ports Azureus needs to go directly to my IP.  Works great.

---

### Post by meng on 2006-11-26
> **alanpotpot said:**
> I have some problems with azureus as well. I have port forwarding enabled on the router but for some reason it would not work. What I usually do is open the test the ports in windows using azureus and utorrent and then go back to ubuntu. After that my torrents health is now green. 

Has anyone have a theory on why this happen?

I don't have a theory that explains that ... that's Twilight Zone stuff!

---

### Post by kaylus on 2006-11-28
> Hi there, I've been looking around in the forum for a while now, but no post seems to solve my problem...

Hi there :) Try using the gnome bt-downloader-gui and see if that affects your rate. If so there may be an explanation for you! I had  horrid problems with KTorrent I was downloading at .5kbps and uploading at 100kbps, when I used bt-downloader instead I was downloading and uploading at 100kbps. If that is the case you may be able to tweak those clients to get the best connection!

---

### Post by Tilex on 2006-12-01
Being the thread's author, I felt compelled to share with you guys that my problem seems to be resolved.  Since Azureus started to disapear after 5-10 minutes downloading torrents, I switched completely to Ktorrent.  

The download speed was still pretty low, even though I had forwarded the required ports.  I simply rebooted my router, and after that, download speeds topped 220 kb/s.  I guess that's ok now!

---

### Post by trubblemaker on 2006-12-01
this seems to be a common issue thanks for the tip

---

### Post by phatzmb on 2006-12-02
Sounds like a problem i had which i just fixed - c&ped from another topic:

i just fixed a very irritating bittorrent problem i've been having for the last few days with azureus and ktorrent. my downloads and uploads were stalling - every 5 seconds. they went up to around 5-15kb/s, then back down to zero for a few seconds and so on. my ports were forwarded fine.

just now i tried turning of uPnP, which solved the problem immediately. i'm not sure exactly how uPnP works, but it would seem that while trying to open my ports it was ruining the port forwarding i already had.

---

### Post by pt123 on 2007-03-16
Thanks turning of the uPnP worked on uTorrent

---

