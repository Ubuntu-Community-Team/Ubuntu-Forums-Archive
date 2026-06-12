---
title: "Just installed 9.10 and I can't see streaming video etc..."
date: 2010-03-15
forum: New to Ubuntu
---

### Post by suomalainen on 2010-03-15
Ubunteros,

I just installed 9.10 and I can play streaming video off the internet.

What should I be looking to do?

Thanks

---

### Post by hhh on 2010-03-15
[https://help.ubuntu.com/community/RestrictedFormats/Flash#Ubuntu%209.04%20%28Jaunty%20Jackalope%29%20and%209.10%20%28Karmic%20Koala%29](https://help.ubuntu.com/community/RestrictedFormats/Flash#Ubuntu%209.04%20%28Jaunty%20Jackalope%29%20and%209.10%20%28Karmic%20Koala%29)

Hope that helps

---

### Post by VoodooLoveDog on 2010-03-15
It depends on the streaming type, however start by installing the restricted extras:

```
sudo apt-get install ubuntu-restricted-extras
```

If you are still having a problem, there is an awesome post that deals with lots of video issues:

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by suomalainen on 2010-03-16
Thanks all for Your great support! Now I got fantastic working, hulu, you tube, DVD, and others working!!!!

BUT THERE IS ALWAYS THIS ONE SITE IN FINLAND THAT I NEED TO BE ABLE TO SEE AND HEAR THAT ALWAYS GIVES ME TROUBLE. AND NOW I HAVE PROBLEMS AGAIN!!!

If you go to this link:

[http://www.katsomo.fi/](http://www.katsomo.fi/)

there are some video clips etc... but I can't seem to get them to work.

WOULD ANYONE HAPPEN TO KNOW WHAT I STILL NEED TO INSTALL TO GET THESE WORKING????

Thanks again for helping me.... I wish this Finnish tv channel was same standard as everyone else....

Regards,

---

### Post by mcduck on 2010-03-16
> **suomalainen said:**
> Thanks all for Your great support! Now I got fantastic working, hulu, you tube, DVD, and others working!!!!

BUT THERE IS ALWAYS THIS ONE SITE IN FINLAND THAT I NEED TO BE ABLE TO SEE AND HEAR THAT ALWAYS GIVES ME TROUBLE. AND NOW I HAVE PROBLEMS AGAIN!!!

If you go to this link:

[http://www.katsomo.fi/](http://www.katsomo.fi/)

there are some video clips etc... but I can't seem to get them to work.

WOULD ANYONE HAPPEN TO KNOW WHAT I STILL NEED TO INSTALL TO GET THESE WORKING????

Thanks again for helping me.... I wish this Finnish tv channel was same standard as everyone else....

Regards,

It's pretty awful site for anybody else than Windows users, but enabling the Medibuntu repository and installing w32codecs & gstreamer0.10-pitfdll should make it work.

[http://www.medibuntu.org/]("http://www.medibuntu.org/")

Still, it's going to cause you some pains. They only officially support Windows XP or later Windows version with Internet Exporer 6 or later and Windows Media Player 10. Even having the actual codecs installed still doesn't make the site work correctly, the video player (and partly even the site's layout) has some serious bugs with any other player than WMP.

---

### Post by colobix on 2010-03-16
Coz they are wmv files and mplayer doesn't support these files.
YOu use firefox right? In that case you can install a plugin that alows you to choose media player for each format to play them with.
I use vlc for almost all the formats. 
The plugin is called mediaplayerconnectivity and you can find it here;
[https://addons.mozilla.org/en-US/firefox](https://addons.mozilla.org/en-US/firefox)
These files are also DRM protected and therefor you need to install the moonlight plugin for firefox as well;
[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

Btw, are these videos from Finland or something?
They sounded very Finnish to me.

---

### Post by suomalainen on 2010-03-16
Wow... none of this is seeming to work for me.... When I was running 8.04 I used safari to watch this stream. But now it appears as if Safari isn't available for Ubuntu any longer. Strange????

---

### Post by mcduck on 2010-03-16
> **suomalainen said:**
> Wow... none of this is seeming to work for me.... When I was running 8.04 I used safari to watch this stream. But now it appears as if Safari isn't available for Ubuntu any longer. Strange????

Safari? really? I've never even heard of Linux version of Safari, are you sure you weren't running the Windows version with Wine or something?

---

### Post by suomalainen on 2010-03-16
Man, I'm so tiered.. I made mistake. I just installed Opera and now everytrhing works perfectly!!!!

I got 2 mixed up....

---

### Post by colobix on 2010-03-16
Me neither.
Isn't that an apple browser?
I would use a compatible browser if I were you.
Use either FireFox or Google Chrome.
The last tip I gave you should work perfectly.
Works fine here.

---

### Post by suomalainen on 2010-03-16
I wish your tip were working but it doesn't. No worries I just use opera instead...

---

### Post by wojox on 2010-03-16
Install gecko-media-player from the repo's. It works for me on Firefox-3.6

---

