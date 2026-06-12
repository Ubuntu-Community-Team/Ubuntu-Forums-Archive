---
title: "uTorrent"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by dondiego2 on 2010-02-12
I received an invite to join a private bittorrent site called Revolution.  The problem is that it appears you can only use certain bittorrent clients for downloading - specifically uTorrent.  I used to use this with Windows all the time and it is a great little bittorrent client.  My problem is trying to run it on Ubuntu as it is a Windows program.

I followed the directions on this site 

[http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml](http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml)

I installed Wine and set everything up as directed.  When I try to start uTorrent it just hangs up and doesn't do anything.  I am at work right now and won't have access to my home computer until this evening.

I was just wondering if anyone has been successful in using uTorrent in Ubuntu.

---

### Post by Techsnap on 2010-02-12
Try installing the latest version of WINE:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Cabs21 on 2010-02-12
First off private torrent sites monitor your DL vs UL ratio.  If it is bad (usually usually 0.9 or lower) then they typically halt or throttle your downloading.  You probably can not upload because....

1) You have a firewall on your router that does not let signals come IN through certain ports unless you are sending a signal out through that port.  You need to open the port in your router to allow signals associated with uTorrent to your IP address, then set up uTorrent to only use that port and turn off random port on start up.

2) You might be uploading with the wrong tracker and or format.  I know the private site I use has a specific format that all torrents need to be in and I have to use there tracker.  I also have to upload in a certain way or I the torrent will not be linked to the files I am uploading.

3) you could be uploading/downloading files that have no seeders or no one wants.

if you could give some more info about the torrent seeds, if your uploading or downloading, and what type of router/ISP you are using, then I can help you with better instructions.

Cabs

---

### Post by beegary on 2010-02-12
At the risk of being Captian Deluge plugger but.......
 
Deluge is a great replacement for muuTorrent and runs natively in Linux.
It is available in the Repos. Compared to Transmission my speeds are better and it seems to deal with the ports etc very well on its own (i think via uPnP).
 
There was a little discussion about utorrent and Deluge here:
[http://ubuntuforums.org/showthread.php?p=8792664#post8792664](http://ubuntuforums.org/showthread.php?p=8792664#post8792664)

---

### Post by Cabs21 on 2010-02-12
> **beegary said:**
> At the risk of being Captian Deluge plugger but.......
 
Deluge is a great replacement for muuTorrent and runs natively in Linux.
It is available in the Repos. Compared to Transmission my speeds are better and it seems to deal with the ports etc very well on its own (i think via uPnP).
 
There was a little discussion about utorrent and Deluge here:
[http://ubuntuforums.org/showthread.php?p=8792664#post8792664](http://ubuntuforums.org/showthread.php?p=8792664#post8792664)


Deluge is great and I love it when i can use it however private sites tend to only work on certain torrent client.  I would recommend you check to make sure that you HAVE to use uTorrent and cant use Bittorrent or similar client that is native to linux.

---

### Post by beegary on 2010-02-12
> **Cabs21 said:**
> Deluge is great and I love it when i can use it however private sites tend to only work on certain torrent client. I would recommend you check to make sure that you HAVE to use uTorrent and cant use Bittorrent or similar client that is native to linux.
 
Sorry good point, I was too busy trying to big up Deluge. 
If the OP wants to give me a link to the torrent Ill give it a go from deluge/karmic

---

### Post by Techsnap on 2010-02-12
> **Cabs21 said:**
> First off private torrent sites monitor your DL vs UL ratio.  If it is bad (usually usually 0.9 or lower) then they typically halt or throttle your downloading.  You probably can not upload because....

1) You have a firewall on your router that does not let signals come IN through certain ports unless you are sending a signal out through that port.  You need to open the port in your router to allow signals associated with uTorrent to your IP address, then set up uTorrent to only use that port and turn off random port on start up.

2) You might be uploading with the wrong tracker and or format.  I know the private site I use has a specific format that all torrents need to be in and I have to use there tracker.  I also have to upload in a certain way or I the torrent will not be linked to the files I am uploading.

3) you could be uploading/downloading files that have no seeders or no one wants.

if you could give some more info about the torrent seeds, if your uploading or downloading, and what type of router/ISP you are using, then I can help you with better instructions.

Cabs

The program doesn't even work for the OP. That's not what was asked, since the program hangs. It should work with the latest version of WINE. The version in the Ubuntu repos is quite old.

---

### Post by Grenage on 2010-02-12
I've never used a private tracker that enforced a certain client; if it's true, then it's completely retarded.  I imagine the OP is confused or has been mislead.

---

### Post by Solethara on 2010-02-12
Actually many private trackers enforce clients because some clients aren't givin out stats correctly. In other words, trackers want to prevent fake uploading and such.So, It isn't retarded.

---

### Post by dondiego2 on 2010-02-12
> **Grenage said:**
> I've never used a private tracker that enforced a certain client; if it's true, then it's completely retarded.  I imagine the OP is confused or has been mislead.


This is a private torrent site that is accessible by invite only.  An earlier poster is correct in that you have to upload in order to download and keep your ratio up or you will be kicked off.

My problem. stated again, is that the person who sent me the invite says that the site only works with uTorrent.  I will try it with some other programs when I get home but he tells me that he has tried with some Linux torrent clients and he could not get the site to work until he used uTorrent.  He is running it on Windows 7.

I don't want to go back to Windows.  I will try to install an updated version of Wine when I get home.  Again the problem is that I cannot even run uTorrent in Linux, the program hangs up and will not open.  It has nothing to do with downloading or uploading a bittorrent.

---

### Post by Grenage on 2010-02-12
> **dondiego2 said:**
> This is a private torrent site that is accessible by invite only.  An earlier poster is correct in that you have to upload in order to download and keep your ratio up or you will be kicked off.

My problem. stated again, is that the person who sent me the invite says that the site only works with uTorrent.  I will try it with some other programs when I get home but he tells me that he has tried with some Linux torrent clients and he could not get the site to work until he used uTorrent.  He is running it on Windows 7.

I don't want to go back to Windows.  I will try to install an updated version of Wine when I get home.  Again the problem is that I cannot even run uTorrent in Linux, the program hangs up and will not open.  It has nothing to do with downloading or uploading a bittorrent.

Of this I am aware, I only really use private trackers.  Other clients are fine, your friend is mistaken.

---

### Post by burnetbj on 2010-02-12
Hello

Not sure if this would help any but if you could get away from wine it might be worth a try 

I use ktorrent which seems to be identical to utorrent which also run native in linux and works very well. 

As i am not informed at all about torrents beside click here and click there this may just be another bogus post 

Anyhow good luck

---

### Post by dondiego2 on 2010-02-12
> **Grenage said:**
> Of this I am aware, I only really use private trackers.  Other clients are fine, your friend is mistaken.


Thanks, my friend who told me this happens to be my son....so I don't think he would lead me astray!  But I just received the invitation late last night and all I did was manage to get logged in to the site.  

I haven't had a chance to look around the site yet for any special requirements myself.  I did notice that it starts you off with a good ratio so you can get started.  This evening I will check out out more thoroughly.

---

### Post by Grenage on 2010-02-12
I meant no offence. :)

You should however be fine with any client; sill, the proof of the pudding is in the eating.  Let us know how you get on.

---

### Post by Cabs21 on 2010-02-12
Let me know if you need help setting up uTorrent to work in Ubuntu.  I know it works and have been using it for a while now.

And if the private site you are using says uTorrent only then my guess is you wont be able to use any other client but uTorrent.  You might be able to work in kTorrent if it mirrors uTorrent enough to fool the private tracker/server but also check your sites rules to make sure that you are ok using that client.  They might have a rule stating that you will be removed/banned for NOT using uTorrent.  just a thought.

---

### Post by MD9 on 2010-02-12
Iam using utorrent on ubuntu 9.10, using wine 1.1.37, works perfectly no problems with uploading and downloading.

try the new wine, and if still doesn't work try wine->configure wine->applications and change the windows version. works in windows 2000 for me.

---

### Post by dondiego2 on 2010-02-13
> **Grenage said:**
> Of this I am aware, I only really use private trackers.  Other clients are fine, your friend is mistaken.



I finally got it going.  The site will let you download torrents with any manager you want.  The issue is that it will only let you seed with specific bittorrent managers.  If you don't seed to keep your ratio above a certain level the site will kick you out.

So I managed to get uTorrent working with Wine and everything is good.

---

