---
title: "BitTorrent is very slow"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by jfluet on 2009-01-19
i use BitToreent client and it wont go faster than 30kbs if it goes that fast. i seed and my upload rate it set at 50kbs could it be my modem or router? i have a wired connection.

i'm not sure exactly what settings or ports to use.
please help
thanks a bunch!

---

### Post by spiderbatdad on 2009-01-19
[http://www.dessent.net/btfaq/](http://www.dessent.net/btfaq/)

---

### Post by lukjad on 2009-01-20
It could be that wherever you live, the provider is throttling all torrents, legal or otherwise. It may be something to look into.

---

### Post by jfluet on 2009-01-21
it went about 250-300kbs a few months ago. and it now the average speed is 10kbs max 30kbs.

---

### Post by lukjad on 2009-01-21
Well, maybe the throttling is new?

---

### Post by jfluet on 2009-01-24
this seemed to work.

 Originally Posted by dk21  View Post
Try to run in console:

sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

and

sudo iptables -A INPUT -p udp --dport 6881 -j ACCEPT

(change the port number...)


and then, incrase the maximum peers in preferences...

I was downloading slowly because I couldn't handle more peers... I incrased it to 200 and I got a great speed incrase: 40 to 450Kbps

in the torrent you can see "downloading from X of Y connected peers". In my case, 50 was the maximum...

PS: Got almost 600kbps...

---

### Post by treepolitik on 2009-01-28
My big trouble is that I can't seed anything without having downloaded it first.  In other words, I have to **re-download what I already have** in order to seed it.  

The one time I tried seeding without first downloading.  I made a torrent file, loaded it, typed in the announce for the Pirate Bay site, and nothing happened.  If I did it right, shouldn't it show up in the client?

---

### Post by white3911 on 2009-02-14
resolved

---

### Post by treepolitik on 2009-03-02
> **treepolitik said:**
> My big trouble is that I can't seed anything without having downloaded it first.  In other words, I have to **re-download what I already have** in order to seed it.

The one time I tried seeding wihout first downloading.  I made a torrent file, loaded it, typed in the announce for the Pirate Bay site, and nothing happened.  If I did it right, shoudn't it show up in the client?

For more information, consult the [Transmission BitTorrent]("http://www.transmissionbt.com/") site, if that's what you have.  That's where I recieved much help.  To answer my own question, and speed up my downloads, *I decided to have a little fun*.  I was working with ** uTorrent on a Windows computer and Transmission on my Linux**.

Whenever the Windows computer had a lot more of a thing, I put it onto my **portable drive**, and brought it to the Linux computer.  I **paused the file** in Transmission, and **drag-and-dropped** the file from my portable drive to the download folder(which is my desktop).  After the **replacement** dialogue(Merge/Replace), I hit **Verify Local Data**, watched as the percentage magically went up, and hit **Start** as soon as it was done verifying.

**If I had the whole file** on the Linux computer *and took it out a long time ago*, I started a **re-download** (from the exact same file/folder name on the exact same torrent site), *and waited just long enough for a folder to appear on my desktop*.  Then I stopped it, did a drag-and-drop replacement, Verified Local Data, watched the magic, and hit Start.  It appeared in the **Downloaded** tab, and started seeding.

Whenever the Linux computer had a lot more of a thing, I put it onto my portable drive and brought it to the Windows computer.  I**drag-and-dropped** the files to the Desktop.  I **Created a New Torrent**, typed in the tracker, and saved the torrent file to the Desktop as well.  I occasionally had to delete the old one from the list in uTorrent.  **If I had the full file**, it appeared in Completed and started seeding.

The tracker for The Pirate Bay is
[http://tracker.thepiratebay.org/announce](http://tracker.thepiratebay.org/announce)
It was very convenient to do things with two computers, because I needed the exact same file name, or the same folder, to download or help seed the same torrent.  However, when I received one particular file, it was all **.rar files** and I needed to use [the RAR extractor]("http://www.rarlab.com/download.htm") to extract it.  (In Linux, I used Wine Windows Emulator on the Windows version, but alternatively you can download the Linux version as a tar.gz tarball, which has its own extraction rules).  So when I went to seed it, I had to *remove the extracted file/folder so just the .rar files were there*, the same way I first found it.  

Notes
The reason why I also told the Windows side of the story, is for appreciation that you are doing the same process with different programs, and in case you might have a family desktop computer with Windows and your own laptop with Ubuntu on it.  Want to give it a try?  Also, since then I've discovered that many of the clients are *available on both Windows and Linux.*

**If you want to create torrents with your own file names, or ones that never existed,** it appears you will have to become a member of The Pirate Bay or another torrent site.  You can "create"(it's technically re-create, because of the preceding statement) torrent files in Transmission and type in the tracker using New, but I prefer drag-and-drop.

**Transmission wins!**  After uTorrent/Windows stopped finding seeders, Transmission/Linux continued to find seeders.  It appears that Transmission is compatible with more clients than uTorrent, or has better capabilities overall.

Essentially you are **running two programs** when you use Transmission.  Type "top" into Terminal, and you'll see that gnome-video-thu is using a lot of virtual memory.  If I am correct, Transmission tells gnome-video-thu to play the bits and make sure everything is there, from one hash mark to the next.  
**Ratio,** put in simple terms, *tells you if "you gave as much as you got"* of that particular file.  With BitTorrent, we want to encourage generosity.  Remember that .75 is 3/4, in which you gave 3 units, and got the complete 4 units of the thing.  *You want to get 1.00*  Usually if you are more generous, people will help you achieve your target ratio more quickly.  *Ratios only show after you have the complete thing.*  Make sure you **go by the individual ratios,** not your overall ratio next to the blue circular arrow.  More info is below.

Other Ways of Analyzing Speed
There may be only one seeder.  Unfortunately, you don't have much control over this, except to try to *give that particular one your full bandwidth* and hope the person is generous enough.  In all the clients, there is a place where you can see who is **"Choked" or "Unchoked," and "Interested or not Interested."**
Whether you're uploading or downloading you can **double-click on a torrent,** go to the **Peers tab,** and hold your mouse over the info for each peer, and *it will tell you what the letters mean.*  They may change over time.  
  
If someone is Choked, it means there is not enough room in your bandwidth.  **If they're a nicer seeder,** you try to Unchoke them to give them more bandwidth.  *However, they can say they're not Interested* in giving you the bits that you want.  I believe you can do these functions manually in Azureus(now called Vuze), which is why I've decided to give it a try sometime.  There are plenty of other BitTorrent software in Applications-->Add/Remove.  *Be sure to select Internet in Add/Remove to narrow your search* to keep the memory usage down, before you type in BitTorrent in the search.  This will also allow you to keep track of which BitTorrent clients you've downloaded to try.

When you're seeding in Transmission, the most you can do is **try to seed to a few people as quickly as possible,** rather than seed to a whole bunch of people at once.  You can control this by **double-clicking on the torrent** in the Seeding tab(it's easier for me to just work with the Seeds and Downloads separately), then going to the Options tab.  I usually keep it at 4 peers max, and raise the speed of whatever I'm doing, Upload or Download, *if the message in the movie I'm seeding is important to me.*  I slow down the other ones using these options.  You can also use this to slow down your overall bandwidth, especially if you are using a college dormitory connection.

If your connection speed is a problem and you're on wireless, you might consider trying a signal booster, called a repeater.  It's much smaller than a router and looks kind of cute.  If I get one and figure out how to use it in Ubuntu, I'll post.  

Special Cases
Sometimes, if a downloader hits the max download speed consistently, and if the particular movie has an important message, or if I'm the only one seeding, and the person is the only one downloading, I'll give the person my full bandwidth by pausing the others.  *I sometimes also prioritize the ones with lower ratio.*  The great thing is that the others never know who I am unless they know what I upload.

All Night Long
Sometimes the download is so slow that you may have to leave your computer running all night.  Remember that *there is always a more difficult solution that is easier to think of.*  **Make sure there's good ventilation.**  I prop the laptop at a 45 degree angle or 2 inches in the air on each edge, being careful not to cover the vents.  Alternatively, use a cooling pad, an open window, or the garage(if it's cool).   My sister even sometimes puts the laptop in the freezer for a few minutes every now and then.

---

