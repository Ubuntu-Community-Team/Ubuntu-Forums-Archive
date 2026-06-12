---
title: "Magnet links from the pirate bay"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by Falc7 on 2009-11-18
Firefox gives me the message 
Firefox doesn't know how to open this address, because the protocol (magnet) isn't associated with any program.

WHen i try to use magnet links, i googled and found this solution:
* Type about:config into the address bar and press Enter.
* Right-click -> New -> Boolean -> Name: network.protocol-handler.external.magnet -> Value -> true
* Right-click -> New -> String -> Name: network.protocol-handler.app.magnet -> Value -> /opt/azureus/azureus
* Ensure network.protocol-handler.expose-all is set to true. (mine was already)


But it dosen't work for me, can anyone help?

---

### Post by MonoDeem on 2009-11-18
```
/opt/azureus/azureus <magnet>

```Does it work when executed from the Terminal ?

---

### Post by lovinglinux on 2009-11-18
[http://ubuntuforums.org/showthread.php?t=1273985](http://ubuntuforums.org/showthread.php?t=1273985)

---

### Post by Falc7 on 2009-11-18
> **MonoDeem said:**
> ```
/opt/azureus/azureus <magnet>

```Does it work when executed from the Terminal ?

Actually i am using deluge, usr/bin/deluge dosen't work to start deluge, however thats where the file is, if i type deluge into terminal it starts

---

### Post by decoherence on 2009-11-18
are you typing "usr/bin/deluge" or "/usr/bin/deluge"? Just asking 'cause there is a difference. "usr/bin/deluge" tries to run a file located under your current working directory, so unless you're currently in the "/" directory you'll probably get an error.

Back to your problem, rather than

Right-click -> New -> String -> Name: network.protocol-handler.app.magnet -> Value -> /opt/azureus/azureus

try

Right-click -> New -> String -> Name: network.protocol-handler.app.magnet -> Value -> /usr/bin/deluge

I haven't actually done this so no idea if it'll work. Looks like it should, though.

---

### Post by Falc7 on 2009-11-18
Oh yes i did make a type in my previous post, it should be /usr/bin/deluge, no luck however, i guess deluge dosen't support magnet files possibly? It seems people in that other thread haven't got it working yet either

edit: i've noticed that TPB says magnet links use a DHT network, which the wikipedia page for deluge says it supported, so it should work

---

### Post by decoherence on 2009-11-18
Have you tried downloading the magnet file and opening it from Deluge? Does it error? Or just not recognize it?

deluge-torrent.org is gone... frustrating

---

### Post by arbogast on 2009-11-18
they're at deluge-torrent.info \\:D/

---

### Post by Vivified on 2009-11-18
> **decoherence said:**
> Have you tried downloading the magnet file and opening it from Deluge? Does it error? Or just not recognize it?

It can't be downloaded like a normal .torrent file.

---

### Post by kiridude on 2009-11-19
I'm having the same problem using magnet links with deluge. I tried [this]("http://www.rohitab.com/discuss/index.php?showtopic=35291") add on for firefox, but still no cigar.

Its pretty hard finding directions for using magnet links...

---

### Post by decoherence on 2009-11-19
> **Vivified said:**
> It can't be downloaded like a normal .torrent file.

Wild. Do you have a link to an example file you can post? (make sure it's public domain or we'll get closed! ;) )

---

### Post by Vivified on 2009-11-19
Something like this?

[http://thepiratebay.org/recent](http://thepiratebay.org/recent)

All the links have a magnet link next to them.

---

### Post by doas777 on 2009-11-19
interesting. I have largely ignored magnet links (as they've always been azureus-only), and it looks like everyone else has as well, until just this week. is the the tpb change that has everyone looking at them, or is there a new bug that is killing previously available functionality?

---

### Post by Vivified on 2009-11-19
The previous functionality is intact. However, TPB claims that "This is the future. And the present", a decentralisation in the torrent world. Time will tell...

---

### Post by kiridude on 2009-11-20
TPB has shut down their tracker for good and are now recommending DHT and PEX. Thats why the sudden interest in magnet links.

[http://torrentfreak.com/the-pirate-bay-tracker-shuts-down-for-good-091117/](http://torrentfreak.com/the-pirate-bay-tracker-shuts-down-for-good-091117/)

---

