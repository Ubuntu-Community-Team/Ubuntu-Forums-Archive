---
title: "Ho do I add this station to Rhythmbox Radio streams?"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by anthony62490 on 2009-05-15
I am a big Demoscene fan, so naturally I would like to add the DemoVibes Radio stream to my Rhythmbox radio list. The URL listed on the DemoVibes player doesn't seem to be working, so I am probably doing something wrong.

The website for Demovibes radio is: [http://www.scenemusic.eu]("http://www.scenemusic.eu") (stream player is located on the right-hand side of the page, duh.)

And the player provides me with the url: [http://mirror.bitshit.org/necta.html]("http://mirror.bitshit.org/necta.html")

But when I plug this into Rhythmbox, nothing happens. Do you know what I am doing wrong?

Also, I tried the same thing with the FOX News stream and the BCN (Broadband Comedy Network) stream, but no dice. Got any ideas?

---

### Post by jtuchscherer on 2009-05-15
Hi there,

If you go to [http://www.scenemusic.eu](http://www.scenemusic.eu) website, you'll find links to the playlist files (.m3u). Download one of those and open it in a text editor. You will find a URL. Use this URL in Rhythmbox to add a new Internet Radio Station.

Quote from the website:

The stream urls are:

    * [http://calcipher.verbrennung.org:8000/nectarine.ogg.m3u](http://calcipher.verbrennung.org:8000/nectarine.ogg.m3u) (192kbit/ogg, props Enno)
    * [http://demovibes.de:8000/necta192.mp3.m3u](http://demovibes.de:8000/necta192.mp3.m3u) (192kbit/mp3, props Locutus)
    * [http://natrox.ath.cx:8000/](http://natrox.ath.cx:8000/) (props pipe)
    * [http://scenemusic.klapa.eu/necta.m3u](http://scenemusic.klapa.eu/necta.m3u) (192kbps, port 80, for firewalled people, props Wacko)
    * [http://scenemusic.unfy.org/necta.m3u](http://scenemusic.unfy.org/necta.m3u) (192kbps, port 80, for firewalled people, props Unfy)

That worked for me.

---

### Post by AndyCooll on 2009-05-15
Just copy one of those stream url's indicated by jtuchscherer (they're listed half-way down the demovibes webpage), open up Rhythmbox, go to radio stations, select "New Internet Radio Station", paste the m3u link, and it should play and add it to your list of radio stations. No need to open up a text editor.

If you choose the ogg ones they'll play out-of-the-box. The mp3 ones require additional codecs (if you haven't already installed them). 

:cool:

---

### Post by anthony62490 on 2009-05-16
Thanks both of you. That makes perfect sense. I managed to get hold of all three streams without a problem. It just took a couple of downloads and one peek at a page's source code. Thanks a lot!

---

