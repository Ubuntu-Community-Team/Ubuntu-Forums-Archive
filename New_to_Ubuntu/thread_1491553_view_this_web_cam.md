---
title: "view this web cam"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by bob brazie on 2010-05-23
Ubuntu 10.04 and FireFox 3.6.3

Can someone tell me how to view this web cam?

[http://www.tappedintoelephants.com/asp/index.php](http://www.tappedintoelephants.com/asp/index.php)

I am trying to set my wife up with Ubuntu and if she can't view her favorite web cams it will be a deal breaker. <g>

Thanks in advance.

---

### Post by themusicalduck on 2010-05-23
I managed to get it to display by right clicking on "click here" under the webcam box and Save link as.

Then I opened the downloaded file in vlc and it worked. It might be possible to get vlc to be the default media player in Firefox. It's probably trying to play it with Totem and it wouldn't work when I opened the file with it. At least you can view it opening it in vlc if necessary.

I was disappointed that it was night time and I couldn't see any elephants :P

---

### Post by bob brazie on 2010-05-24
Check back later and you will see plenty.

There must be a way to have it play in FireFox by default. That will be a deal breaker for my wife to do all of those steps to view the cam.

Any one have other suggestions?

Thanks, Bob.

---

### Post by themusicalduck on 2010-05-24
I think I've found a fix. Install gecko-mediaplayer. ```
sudo apt-get install gecko-mediaplayer
```

It now works in Firefox for me, but just not for Chrome.

It seems to take quite a long time to load though, but it might work better for you.

---

### Post by bob brazie on 2010-05-24
It does take a long time to load but thanks for the work around.

I sure wish it would play in the embedded site player. It seems it is looking for a MMS protocol source. Microsoft Media Server protocol source. Some sort of plug in for FireFox maybe.

Maybe someone knows what this is and how to install it?

---

### Post by themusicalduck on 2010-05-24
Does it not play in the embedded player on the site for you after installing that package? It plays ok for me on Firefox.

---

### Post by bob brazie on 2010-05-24
Oh, yes it does after a re-start. But it is sooooooo slow to load.

---

