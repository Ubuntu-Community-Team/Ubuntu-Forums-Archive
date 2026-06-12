---
title: "Network Activity"
date: 2013-11-27
forum: Networking &amp; Wireless
---

### Post by mayagrafix on 2013-11-27
Why is this PC always uploading and/or downloading a steady stream of data? even if it is minimum data transfer at less than 300-kbs, it never stops. I already have turned off Ubuntu One cloud and Dropbox, so is ET trying to phone home? :confused:
[[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/NetworkHistoryactive_zps287a9e19.png[/IMG]](http://s16.photobucket.com/user/mayagrafix/media/binaryes/NetworkHistoryactive_zps287a9e19.png.html)

---

### Post by Doug S on 2013-11-27
Use a packet sniffer, such as tcpdump or wireshark, to observe what is going on at the packet level. There is a bit of low level traffic, arp and such, just to enable the network to work. Example (for interface eth0)```
sudo tcpdump -n -tttt -i eth0
```

---

### Post by jonobr on 2013-11-27
HEllo


You could look at "top" to see what processes are running at any given time

---

