---
title: "Small footprint media player?"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by triplenine on 2009-02-13
I know that this has been discussed in a number of ways and have read a few posts about it, but I am looking for a media player that handles playlists well. I have a few other requirements as well.

I am using a Dell mini 9 with the 4GB SSD running the Ubuntu package that it was delivered with. That size restriction both in storage and screen size sets my limits pretty clearly. I have my network connections set up so that when I am at home I can reach my music server just fine. My concern is that I have a part time deal where I MC a pub quiz that requires me to use multiple playlists for music and some of the quiz rounds.

 Last night I was using Amarok and things went badly. Due to the restricted storage I was using a thumb drive as a storage space for my background music. The functions of Amarok were moving painfully slow and it locked up on more than one occasion. This could be rectified by more RAM which I have ordered but may or may not be here by next week. Another funny moment was when I could not confirm my choices in the configuration tool because the default configuration window was larger than my screen size and would not resize even when using the resize tool. PITB for sure.

So here is the meat of this post what I am looking for is a media player that will handle playlists easily without taking up too much real estate on the drive and the screen and does not require a heavy resource load. Who knows? Amarok might be right for me but it sure did not give me a favorable impression last night.

What do you think?

---

### Post by wolfen69 on 2009-02-13
i would go with VLC. after opening a video with it, it is only using 10mb ram, and is very small on the screen.

---

### Post by BDNiner on 2009-02-13
xmms would be the one i would chose. It was made to resemble winamp so you can create a playlist. I don't know how it handles multiple playlists. There are several forks of xmms since it is no longer in development like Audacious and beep media player or xmms2

---

### Post by avtolle on 2009-02-13
Depending on the release the OP is using, xmms will not be in the repos (from 8.04 on) and will need to be, as I recall, compiled from source. What about banshee? I've no experience with it, but it seems it might be an alternative. Also, under Gnome, Exaile (which is touted to be like Amarok, only for Gnome) is available. It seems to have multiple play list capabilities.

---

### Post by cariboo on 2009-02-13
Xmms is available [here]("http://www.pvv.ntnu.no/~knuta/xmms/"), I've only tried it running Jaunty, but it seems to work OK.

Jim

---

### Post by egalvan on 2009-02-13
> **avtolle said:**
> Depending on the release the OP is using, xmms will not be in the repos (from 8.04 on) and will need to be, as I recall, compiled from source. What about banshee? I've no experience with it, but it seems it might be an alternative.

Audacious & Banshee are in the 8.04x repos.

---

### Post by triplenine on 2009-02-13
From what I have read, audacious has little to no playlist support. I will take a look at Banshee butI think I might just have to give vlc a try. It is a standby for me with video and I will have to monkey with its playlist support to see if it is workable - though anything would be better than my Amarok experiment. There is nothing like having a bar full of trivia players staring at you while you try to troubleshoot on the fly.

---

### Post by LowSky on 2009-02-13
VLC is the best optino for a small player, Personally I like exaile, and use it at home it doesnt have the same requirements as amorok, which always broke for me too.

For you I think VLC would work best.
Also pick up a 16 GB flash drive, they are now about $20 and for the use of Mcing a quiz thing at the local pub it could be a great backup if needed

---

### Post by mcduck on 2009-02-13
MPD with Sonata as client.. ;)

Actually I would personally use ncmpc as client if I had one of those mini laptops. You can't really get much lower resource usage and better use of available desktop space than what ncmpc has.

---

### Post by prshah on 2009-02-13
> **triplenine said:**
> 
So here is the meat of this post what I am looking for is a media player that will handle playlists easily without taking up too much real estate on the drive and the screen and does not require a heavy resource load.

I vote for quodlibet; the repositories only contain 1.0, which works great, but you can also download and compile 2.0 from sourceforge if you feel up to it.

---

### Post by kanikilu on 2009-02-13
I also think VLC would fit your needs. Also it probably hasn't been mentioned since it doesn't support playlists (that I know of?), but "moc" (in the repos) is a fun little text-based music player. I use it on my Eee PC since it only seems to use ~5MB of RAM (and that's with about 10 albums in the queue).

---

### Post by triplenine on 2009-02-17
So - I finally got a chance to sit down and make a few changes. I think vlc will work. It is so quick and to-the-point. I think I will keep Amarok around for my day to day ipod/music needs.

---

### Post by stchman on 2009-02-17
> **triplenine said:**
> I know that this has been discussed in a number of ways and have read a few posts about it, but I am looking for a media player that handles playlists well. I have a few other requirements as well.

I am using a Dell mini 9 with the 4GB SSD running the Ubuntu package that it was delivered with. That size restriction both in storage and screen size sets my limits pretty clearly. I have my network connections set up so that when I am at home I can reach my music server just fine. My concern is that I have a part time deal where I MC a pub quiz that requires me to use multiple playlists for music and some of the quiz rounds.

 Last night I was using Amarok and things went badly. Due to the restricted storage I was using a thumb drive as a storage space for my background music. The functions of Amarok were moving painfully slow and it locked up on more than one occasion. This could be rectified by more RAM which I have ordered but may or may not be here by next week. Another funny moment was when I could not confirm my choices in the configuration tool because the default configuration window was larger than my screen size and would not resize even when using the resize tool. PITB for sure.

So here is the meat of this post what I am looking for is a media player that will handle playlists easily without taking up too much real estate on the drive and the screen and does not require a heavy resource load. Who knows? Amarok might be right for me but it sure did not give me a favorable impression last night.

What do you think?

I have an Acer Aspire One and use Rhythmbox.  It is fast and easy to use.  Amarok is a KDE app and I find KDE apps more bloated than Gnome apps.  I know some other forum members will protest, but it is my opinion.

I don't hate KDE apps, I love K3b and K9Copy(only KDE apps I use regularly).

Rhythmbox also does iPod management.

---

### Post by triplenine on 2009-02-17
Going back to Rhythmbox for iPod support is a good idea. It will let me drop the KDE components to free up space. Since I am only running the one KDE app it makes since to use a Gnome based app for the sake of libraries that can multitask for other apps.

---

