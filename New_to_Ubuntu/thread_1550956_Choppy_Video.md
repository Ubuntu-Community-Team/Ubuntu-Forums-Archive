---
title: "Choppy Video"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by Failboat88 on 2010-08-11
When I watch videos, mainly flash, it's real choppy. My system monitor shows my memory 70% programs 30% cashe. CPU load is 80-90+. I have an intel PD 2.8, ATI 850x, and one gig ddr2 667. 

I don't think the videos were so bad when I first installed and they aren't hd. Is the problem lack of hardware or something software related. 

Choppy pr0n sucks. Please help.

---

### Post by dv3500ea on 2010-08-11
Flash performance sucks, particularly on Linux :(
And it's hard for the community to do anything about it because it is closed source. 

I often download videos instead of streaming them. For some sites, such as youtube, you can use a program called [abby]("apt:abby") to download videos. (also [clive]("apt:clive"), [cclive]("apt:cclive") or [youtube-dl]("apt:youtube-dl") on the command line).

Using HTML5 versions of sites is a good idea too. (A example is ["]http://www.youtube.com/html5]]("http://www.youtube.com/html5)).

Sometimes, a buffered video will appear in your /tmp folder - you could play that in vlc or totem instead of playing by browser.

Also, pasting this in the URL bar will give you a link to the video file that you can right click and download on ***some*** sites. ```
javascript:document.body.innerHTML = '<a href="' + document.getElementsByTagName("embed")[0].outerHTML.match(/file=(.*?)\.flv/)[0].match(/file=(.*)/)[1] + '" style="font-size:xx-large">VIDEO IS HERE</a>'+document.body.innerHTML
```

---

### Post by Failboat88 on 2010-08-13
So, you wouldn't think my system specs have anything to do with it?

---

