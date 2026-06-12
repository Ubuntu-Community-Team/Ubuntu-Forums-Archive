---
title: "bittorrent won't download"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by jfluet on 2009-09-06
i am having problems downloading or connecting to tracker. this started happening after i installed Deluge and KTorrent to try a different client, i prefer BitTorren so i uninstalled Deluge and KTorrent and when i went back to bittorrent it woudent connect to any torrent i try to download. i checked to see if the right ports are opened and 6881 to 6889 are opened.
please help!

---

### Post by darkwalt on 2009-09-06
Are you using wifi on a campus?

---

### Post by lovinglinux on 2009-09-06
> **jfluet said:**
> i am having problems downloading or connecting to tracker. this started happening after i installed Deluge and KTorrent to try a different client, i prefer BitTorren so i uninstalled Deluge and KTorrent and when i went back to bittorrent it woudent connect to any torrent i try to download. i checked to see if the right ports are opened and 6881 to 6889 are opened.
please help!

Installing Ktorrent or Deluge wouldn't affect other clients. I bet you are trying to download a torrent which includes a tracker like thepiratebay.org or something similar. It's probably a tracker issue, since TPB connection was taken offline due to a court order last week. Since then, several torrent threads have been posted on the forums. Not a coincidence, is it?

Make a test with a reliable torrent like [Ubuntu official torrents]("http://www.ubuntu.com/getubuntu/downloadmirrors#bt"). If it doesn't work, then check if you have the correct port forwarded in your router, then check if the torrent client is using the same port, then check if you have any firewall rules blocking the connection. If everything is correct and you still can't get a connection, then try changing the port to a single port between 49152 and 65535. It's usually not recommended to use 6881 to 6889, because some ISP block traffic on those ports, since they are standard for torrent. Being standard doesn't mean you have to use them.

---

### Post by jfluet on 2009-09-06
darkwalt 

no wifi strait up wired connection.

lovinglinux
i was using thepiratbay.org, where else is a good torrent site?

---

### Post by darkwalt on 2009-09-06
mininova.org is the one that I use.

---

### Post by lovinglinux on 2009-09-06
> **jfluet said:**
> lovinglinux
i was using thepiratbay.org, where else is a good torrent site?

The problem is not the site, but the torrent file, which has thepiratebay.org tracker. Unfortunately, several and legal torrents on the web also uses the pirate bay tracker, no matter if you downloaded from them or not. So when the TPB tracker goes down, for whatever reasons, then your torrent stops downloading. You can simply replace the tracker with another one. Open Deluge, go select the torrent and look into the Details tab in the bottom panel. Copy the torrent hash number and add it to this address:

```
http://www.torrentz.com/
```

like this:

```
http://www.torrentz.com/**[COLOR="Red"]60d5d82328b4547511fdeac9bf4d0112daa0ce00[/COLOR]**
```

This will open the torrent page based on hash value. Scroll down to the "Torrent Trackers" section, then copy one or more address of available trackers. 

You should see something like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=127733&stc=1&d=1252293106[/IMG]

Then open Deluge, right-click on the torrent file and select "Edit Tracker". Replace the pirate bay address with the new one and restart the torrent. This should fix it.

You can also try to add these trackers, which are very popular and seems to be reliable:

```
http://tracker.publicbt.com:80/announce
http://tracker.openbittorrent.com:80/announce
```

Some torrent sites offer their own tracker, so you don't depend on the tpb. For instance, [Mininova's Featured Torrents](http://www.mininova.org/featured/cat/) are legal, since they are uploaded by creators and they are tracked by Mininova's tracker.

.

---

### Post by jfluet on 2009-09-09
still can seem to download,
there is no hash number that i could see anywhere to copy.
when opening ports it asks what server IP to use dose this matter 192.168.1.115 1s what its at and i can only change the last number. 
everything else regarding internet works.
all i want is more Dexter and some season 5 of 24 at the moment.
ubuntu dont fail me now!
thanks for your help so far.

---

### Post by halitech on 2009-09-09
to me it looks like it is looking for your local computer to be serving the files as 192.168 IPs are reserved for local networks. that could be why you can't download anything...

---

### Post by lovinglinux on 2009-09-09
> **jfluet said:**
> still can seem to download,
there is no hash number that i could see anywhere to copy.
when opening ports it asks what server IP to use dose this matter 192.168.1.115 1s what its at and i can only change the last number. 
everything else regarding internet works.
all i want is more Dexter and some season 5 of 24 at the moment.
ubuntu dont fail me now!
thanks for your help so far.

In this case I won't help you, since I don't support downloading unauthorized content. I don't know if it's legal to download such files in your country, but that's is definitely not allowed here in the forums.

---

