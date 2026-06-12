---
title: "Torrents Download"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by Anybloodyid on 2009-06-24
Hi

Is there anything better than Kget for downloading torrents?

Thanks

---

### Post by nandemonai on 2009-06-24
There are heaps of Linux torrent clients.. :)

Deluge, Transmission, rtorrent, Vuse and many many more.

Better is relative. All depends what you prefer.

Myself I use rtorrent on my server and transmission on my desktop.

Try a few out and see what you like.

---

### Post by Anybloodyid on 2009-06-24
Thanks Nand

I figured there had to be something better than Kget

---

### Post by prshah on 2009-06-24
> **Anybloodyid said:**
> 
Is there anything better than Kget for downloading torrents?

Another vote for rtorrent; however, be warned; rtorrent has a nil-to-rudimentary GUI interface.

I personally prefer it for it's capabilities and the fact that I can use my Palm Treo phone to ssh in my computer and control it.

rtorrent is powerful and flexible and wonderful and uses minimal resources but... lacks a "GUI"; this is a plus in my opinion, but clearly that makes it not everybody's' cup of tea.

---

### Post by Anybloodyid on 2009-06-24
Hi

I installed rtorrent now where do I find it?

---

### Post by nothingspecial on 2009-06-24
Type ```
rtorrent
```

Then press enter. Press Tab to list the available torrents then type the one you want to start.

Press the down arrow so that 3 little *s appear next to it then press Ctrl S to start it.

---

### Post by nothingspecial on 2009-06-24
In fact, [[COLOR="Red"]here[/COLOR]]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/") is a nice little beginners guide.

---

### Post by Hated On Mostly on 2009-06-24
Deluge is easy to setup and use and comes with an easy to use blocklist.

[http://deluge-torrent.org/](http://deluge-torrent.org/)

Download the latest version from either here:

[https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

or here:

[http://www.getdeb.net/app/Deluge](http://www.getdeb.net/app/Deluge)

Or you can install it from Add/Remove or Synaptic since a good version of Deluge comes with Jaunty.


If you are a beginner you don't want to use rtorrent. Hell, if you are experienced you don't want to use rtorrent.

---

### Post by Anybloodyid on 2009-06-24
Nothing 

Thanks for that and thanks for the link I'll look at it shortly.

---

### Post by Cheesemill on 2009-06-24
+1 for Deluge

---

### Post by Anybloodyid on 2009-06-24
OK I'm trying Deluge first, but it says No incoming Connections!
How do I tell ubuntu to allow deluge to have incoming connections?

---

### Post by Cheesemill on 2009-06-24
Check out this thread from yesterday for info on setting up Deluge.
[http://ubuntuforums.org/showthread.php?t=1194732](http://ubuntuforums.org/showthread.php?t=1194732)

---

### Post by Bölvaður on 2009-06-24
I vote for the standard transmission. You can get the latest version from their repos, you can find information on how to install it on their website. It is a torrent client for people that dont want to fittle with too many settings and configs.

---

### Post by Anybloodyid on 2009-06-24
Thanks for help offered

---

### Post by ~sHyLoCk~ on 2009-06-24
> **Anybloodyid said:**
> Hi

Is there anything better than Kget for downloading torrents?

Thanks

Deluge is the best!

---

### Post by blackxored on 2009-06-24
+1 Vuze

---

### Post by prshah on 2009-06-24
> **~sHyLoCk~ said:**
> Deluge is the best!

I _was_ a Deluger through and through; but it kept losing my torrents (87% complete.. reboot.. starting again from 0%). This may have been fixed in recent versions, but now that I have (semi-) mastered rtorrent, I can't see myself using anything else...

---

### Post by ~sHyLoCk~ on 2009-06-24
> **prshah said:**
> I _was_ a Deluger through and through; but it kept losing my torrents (87% complete.. reboot.. starting again from 0%). This may have been fixed in recent versions, but now that I have (semi-) mastered rtorrent, I can't see myself using anything else...

Hmm that;s weird i have been using deluge [since I loved utorrent] for a while now without any issues. I have never tried rtorrent though so can't compare.

---

### Post by philcamlin on 2009-06-24
dont use transmission if you have a firewall you will notice alot of people port scanning for transmission so i dont use it anymore

i dont know whats going on but doesnt look good to me

transmisson : port 51413

all the port scanner people are looking for that 

i dont even torrent...

---

### Post by nandemonai on 2009-06-24
> **philcamlin said:**
> dont use transmission if you have a firewall you will notice alot of people port scanning for transmission so i dont use it anymore

i dont know whats going on but doesnt look good to me

transmisson : port 51413

all the port scanner people are looking for that 

i dont even torrent...

My guess is that you used it in the past and have uPnP enabled on your router hence it opened up/forwarded a port to your machine. This would explain why you're seeing connections on that port and no others.

Might want to look into that.

Edit:

Transmission isn't the only application that will use uPnP if it can, most torrent clients do.

---

### Post by Anybloodyid on 2009-06-25
Hi

Well after trying all the flavours I've decided to go with Deluge it downloads at a reasonable speed compared to the others and seems more user friendly.
The only problem I have is that at the bottom it reads No Incoming Connections
I've used gufw to allow Deluge but that sign at the bottom is still there.

What do I need to do to allow incoming connections?

---

### Post by prshah on 2009-06-25
> **Anybloodyid said:**
> 
What do I need to do to allow incoming connections?

You have to "open" / "forward" the port used by Deluge on your Internet router. The instructions for this vary from model to model, see [http://www.portforward.com](http://www.portforward.com) for more details.

---

### Post by ~sHyLoCk~ on 2009-06-25
> **Anybloodyid said:**
> Hi

Well after trying all the flavours I've decided to go with Deluge it downloads at a reasonable speed compared to the others and seems more user friendly.
The only problem I have is that at the bottom it reads No Incoming Connections
I've used gufw to allow Deluge but that sign at the bottom is still there.

What do I need to do to allow incoming connections?

Port forwrding.

---

### Post by Anybloodyid on 2009-06-25
Hooray at last!!

Had to do port forwarding and use gufw to allow incoming connections.

Thanks to all those who pointed me in the right direction

---

