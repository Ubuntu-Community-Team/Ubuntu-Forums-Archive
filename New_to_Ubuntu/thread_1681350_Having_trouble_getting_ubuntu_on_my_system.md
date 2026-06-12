---
title: "Having trouble getting ubuntu on my system"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by Jon Anderson on 2011-02-04
I sent for a CD ,they turned me down, I had received one years ago. I'm unable to download it to my computer, I tried downloading it three times and it is always corrupted. I really would like to try Ubuntu. I want to get off the windows wagon. Any suggestions? all Ideas will be appreciated.

Thanks
Jon Anderson

---

### Post by Elfy on 2011-02-04
As you don't say how you have been getting the iso I'd try downloading it with a torrent first - [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt)

I assume that it is the download that is corrupted - you checked with the md5sum? 

If you still have issues you can buy the cd from many places.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by Synthetic Sam on 2011-02-04
Alternatively try metalink downloading:

Go to [http://releases.ubuntu.com](http://releases.ubuntu.com) and select the release you want from the folder list at the bottom.  Then select the file that ends with the metalink extension.

Then pick a metalink utility from the list here: [http://en.wikipedia.org/wiki/Metalink](http://en.wikipedia.org/wiki/Metalink) that's suitable for your operating system.  I like aria2c, but that's personal preference.

This should be more reliable than trying to download directly, and supports resuming download etc etc.

[edit] By default the metalink will choose to download by bittorrent first, if this is a problem, edit the metalink file with a text editor and remove the torrent reference (it's an XML file and relatively straightforward).

---

### Post by EthioJOB on 2011-02-04
Have you tried torrents? I normally prefer them when downloading large files. Check out [w.ubuntu.com/desktop/get-ubuntu/alternative-download#bt]("http://w.ubuntu.com/desktop/get-ubuntu/alternative-download#bt")

Of course you'll need a BitTorrent software, which you'll find easily (try uTorrent, my favourite).

---

### Post by The Cog on 2011-02-04
Another reason for downloading torrents is that they don't arrive corrupted - the torrent client chacksums them during the download.

---

