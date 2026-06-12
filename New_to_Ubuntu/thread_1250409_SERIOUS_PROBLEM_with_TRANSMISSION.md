---
title: "SERIOUS PROBLEM with TRANSMISSION"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by shreyanshjain8 on 2009-08-26
hi techies...

i have been trying to download a torrent from transmission.. but it do not start downloading... the torrent is healthy with maximum seeds.. i tried different download clients also.. (bit torrent and deluge) but still failed... (i m using intrepid)

:(:(:(:(
the same torrent i tried in windows with Utorrent and torrent file was downloaded successflly...

even i asked one of my friend also to try the same torrent in his ubuntu machine... but he also failed...  :-(

can any1 help me in resolving this issue... i don like windows and for such a silly problem i don wanna to switch over windows... plzz plzz help me out ...

thanx in advance..:(

---

### Post by wormser on 2009-08-26
Are you on the same network as the Windows box?  If your friend has the issue when using Ubuntu then there might be something wrong with the torrent.  Try using another torrent and see if it has the same issue.

---

### Post by Penguin Guy on 2009-08-26
> **wormser said:**
> Try using Deluge.

Maybe you hadn't seen this part of his post:
> **shreyanshjain8 said:**
> i tried different download clients also.. (bit torrent and deluge) but still failed...


Does this problem occur for all torrents or just this one?

---

### Post by lovinglinux on 2009-08-26
Have you considered the possibility that tracker could be down? There a few torrent related threads posted today and since Pirate Bay was shut down by court order a couple of days ago and the tracker is still down, I believe is not a coincidence.

As far as I remember, uTorrent uses DHT by default, so if the tracker is down, you still be able to connect to several peers. Check if you have DHT enabled on your torrent client.

You can also check if the tracker is responding. I don't know about transmission, but Deluge tells you if it can't get responses from the tracker in the torrent info.

Anyway, have you opened the port on the router and configured the torrent client to use the same port?

Do you have active firewall rules?

---

### Post by nuketro0p3r on 2009-08-26
I am having the same problem. The ports are all forwarded and the firewall is offline as it is, by default. Although I am now getting normal speed with uTorrent after disabling 'Local Peet Discover', 'Peer Exchange' and 'DHT' I couldn't get it to work with Deluge, Transmission, rTorrent and KTorrent and one more thing all the trackers seem to be offline no matter what client I use.

---

### Post by lovinglinux on 2009-08-26
> **nuketro0p3r said:**
> I am having the same problem. The ports are all forwarded and the firewall is offline as it is, by default. Although I am now getting normal speed with uTorrent after disabling 'Local Peet Discover', 'Peer Exchange' and 'DHT' I couldn't get it to work with Deluge, Transmission, rTorrent and KTorrent and one more thing all the trackers seem to be offline no matter what client I use.

Try to download from Ubuntu tracker [http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

---

### Post by Charles Kerr on 2009-08-26
The most likely culprit is that TPB is down and that your torrent uses TPB as the tracker.  This situation has been causing a lot of complaints for the various clients the past few days.

If that's not the issue, please check [http://trac.transmissionbt.com/wiki/SlowSpeeds](http://trac.transmissionbt.com/wiki/SlowSpeeds) and walk through the "Slow Speeds" checklist there that helps diagnose some of the more common reasons for slow/no speeds.

---

