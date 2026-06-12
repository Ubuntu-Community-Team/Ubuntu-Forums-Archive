---
title: "Bit torrent problems [qt, azerus and bt all do it]"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by skiingdomo on 2007-05-09
Hi

So I have some problems with my bit torrent. Here is my setup:

-Core2duo, Gigabyte motherboard w/onboard lan, 1gig DDR, Nvidia 7600GT, 320gig drive.
-I am in Japan with 25mbit DSL. 
-I use a japanese isp's DSL router, which has port forwarding (which I have set up).
-I always download 3 or 4 TV episodes a week (latest, just released episodes which I cant view in Japan) which are all well seeded (1000+ seeds).
-When I ran windows XP and Utorrent before I switched to Ubuntu, and got 500 - 800kbytes/s  solid on torrents.

The problems after switching to 7.04 Ubuntu:

Azereus (Tried version from repositories and the latest from source forge, and tried both java engines):
- Slow. never get a solid speed as I did with Windows / Utorrent. Sometimes it spikes to 300kbytes/s
- Torrents in the downloading section show up as finished, but dont switch to the seeding window, and still show 96 - 99% complete. Stopping and starting the torrent pops it over so not a biggy.
- I have had a 800meg torrent download 1.5gigs worth of data before being complete. The weird part is it only got 3.6megs worth of bad packets which it threw out (no idea what was going on). Torrent played fine in the end.
- If I switch it on to the port which I am forwarding on my router, it comes up with all kinds of errors that the port is in use / NAT is not working. If I change it to a port which is not set up to forward, it doesnt complain / works.
- If Ieave my PC on downloading then after 3 - 4 hours all torrents go down to 0 speed. restarting the system is the only way to fix this.

QTtorrent:
- Never can get a download rate of above ~50k/sec for an individual torrent.

Bittorrent (default client):
- Doesnt really work at all. Havnt looked at it long enough at its not a real long term solution for me.

I have been putting up with these problems since Fiesty Fawn came out and I switched over. I am even resulting to booting to windows just to download and watch some english TV. Everything else works fine.

This is the ONLY thing I am really hating with Ubuntu. I am loving everything else. does anyone have ANY suggestions at all as to how I can get this working! Thanks!!

---

### Post by skiingdomo on 2007-05-09
Forgot to add:

Uploading works fine:180k/sec (about the max ive ever had it). All torrents are at about a 5 - 10 ratio when they complete. Right now Qt is doing 30down and 110 up. :S

Any ideas anyone?

---

### Post by Baroo on 2007-06-04
I have the same problem!  Let me know if you find a solution as restarting in windows just to download stuff is a real pain.

---

