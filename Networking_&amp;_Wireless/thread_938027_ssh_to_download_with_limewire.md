---
title: "ssh to download with limewire"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by bigdee973 on 2008-10-04
i have an ssh client... is there any possible way i could ssh into my ssh server computer and give it the command to download stuff by using the terminal?? any ideas at all? 

ALSO HOW CAN I BASICALLY generally use my programs in terminal for ssh is it possible? could i recomplie something or install something for it? any helps works thanks

---

### Post by kdcoetzee on 2008-10-04
Well you can always use wget to download content from the web.
But limewire. I don't think so. I know you can setup [FDM]("http://www.freedownloadmanager.org/") to be a web based client. And I heard that [utorrent]("http://www.utorrent.com/") can do it aswell. but both are for Windows. maybe with wine.

You can ssh with port forwarding to view the web interface

```
 ssh username@server -L 8080:localhost:80 
```

Hope this helps.

---

### Post by jpkotta on 2008-10-04
Use the -Y or -X option to ssh to enable X forwarding.  Or find a client that doesn't use X.

```
ssh -X user@server xlogo
```

---

### Post by kdcoetzee on 2008-10-04
But i think to use X forwarding you need to export DISPLAY and a value.

Try this howto.

[http://gentoo-wiki.com/HOWTO_X-forwarding]("http://gentoo-wiki.com/HOWTO_X-forwarding")

---

### Post by bigdee973 on 2008-10-04
hmmm i see isee no i cant forward x because my ssh client doesnt support frame buffering its from a phone...but do u think i could grab the source code of limewire and try to compile and create my own command line program for limewire using its protocols to fetch music etc?

---

### Post by kdcoetzee on 2008-10-05
Well uhm... on your phone ,now thats another story. 
I quickly scanned the web. it seems like the idea is there. 
[http://blog.limewire.org/?p=215]("http://blog.limewire.org/?p=215")

---

### Post by bigdee973 on 2008-10-06
> **Juggernaut_KDC said:**
> Well uhm... on your phone ,now thats another story. 
I quickly scanned the web. it seems like the idea is there. 
[http://blog.limewire.org/?p=215]("http://blog.limewire.org/?p=215")

my phone can run ssh just fine.  i download torrents from my phone to my home PC i just want to be able to create a command line interface or something for limewire so that i could just download stuff from my phone onto my home pc another thing that i cant figure out is how can i have the pc im connect to, to run a program i want on it??  for example...from phone..give command to open limewire and stay open even after i sign off from phone...come home and see limewire running on pc...i cant figure how to make programs open up and run in the pc im connected to anyone have any ideas?

---

### Post by kdcoetzee on 2008-10-07
I know about ssh on the phone. I have putty on mine.

If you just want to download torrents.
Transmission client of ubuntu. You can set it to automatically start downloading when a new torrent file enters a specific folder.

Have not tested it yet, but give it a try.

i quickly Googled for a command line torrent client.

[http://www.cyberciti.biz/tips/linux-command-line-bittorrent-client.html]("http://www.cyberciti.biz/tips/linux-command-line-bittorrent-client.html")
[https://help.ubuntu.com/community/BitTorrent]("https://help.ubuntu.com/community/BitTorrent")
[http://www.ubuntu-unleashed.com/2008/04/top-linux-bittorrent-clients-for-ubuntu.html]("http://www.ubuntu-unleashed.com/2008/04/top-linux-bittorrent-clients-for-ubuntu.html")

Just run a search on the pages for 'command' or something similar, if you don't want to read though it.

---

