---
title: "iTunes mystery install"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by nnjond on 2009-10-20
Hi,

I seem to have installed iTunes under Wine (c;\ Program files.), But i cant find it anywhere! Has anyone else had this prob?

Thanks

---

### Post by Mike_IronFist on 2009-10-20
> **nnjond said:**
> Hi,

I seem to have installed iTunes under Wine (c;\ Program files.), But i cant find it anywhere! Has anyone else had this prob?

Thanks

Even if you installed iTunes under Wine, it's almost entirely incompatible and won't run under Wine. The Wine App Database (AppDB) shows that it has a rating of "Garbage" for almost all the latest versions.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347")

Even when running under Wine, it's slow, painful, and a nightmare to use.

Might I suggest using Banshee Media Player instead? It works just like iTunes does and has full iPod support! You can install it via Add/Remove applications or Synaptic.

---

### Post by nnjond on 2009-10-20
Thanks for your tip.  Ineed iTunes if i want to dl courses from Stanford Uni.

---

### Post by Mike_IronFist on 2009-10-20
> **nnjond said:**
> Thanks for your tip.  Ineed iTunes if i want to dl courses from Stanford Uni.

Are they podcasts?

---

### Post by martrn on 2009-10-20
> **nnjond said:**
> Thanks for your tip.  Ineed iTunes if i want to dl courses from Stanford Uni.
You dont need to use itunes you just download them using the .rss feed.

[http://itunes.stanford.edu/rss.html]("http://itunes.stanford.edu/rss.html")

and then add them to your Banshee Media Player.  It just looks a bit better in itunes that's all.

---

### Post by nnjond on 2009-10-20
It seems they're podcasts, but Stanford's FAQ includes this:

Do I have to use iTunes and Apple products to have access?

    Currently, you must use the iTunes application to download content. Apple offers a free Windows version of iTunes at [http://www.apple.com/itunes](http://www.apple.com/itunes). For those who use another operating system such as Linux or wish to avoid iTunes altogether, we plan to offer podcast (RSS) access in the near future.

You do not need a Macintosh, iTunes, or an iPod to play the audio files. All you will need is a player capable of playing .mp4 AAC (Advanced Audio Codec) files. (AAC is not exclusively Apple's, although Apple prefers it to alternative file formats.)

---

### Post by Mike_IronFist on 2009-10-20
> **martrn said:**
> You dont need to use itunes you just download them using the .rss feed.

[http://itunes.stanford.edu/rss.html]("http://itunes.stanford.edu/rss.html")

and then add them to your Banshee Media Player.  It just looks a bit better in itunes that's all.

Yeah, just copy that link, open Banshee, go to "Podcasts", click "subscribe to Podcast", paste that link, and subscribe. It's quite easy, and will save you all the headaches of working with iTunes under Wine.

It's an RSS feed, so it will work under ANY podcast-accepting client.

---

### Post by tacantara on 2009-10-20
If you can't accomplish what you need to do with Banshee (which, from my experience, is _really good_ with all but the iPod Touch), then download Sun Microsystem's VirtualBox, set up a virtual Windows machine (if you have a licensed Windows OS disk) and install iTunes on the virtual OS.  I did that, and now I can use the most recent iTunes and receive updates.

If you go the virtual machine route, don't download the version of VB in the repositories, because it is limited in features.  The download from Sun's website gives you a better VM with more features.

---

