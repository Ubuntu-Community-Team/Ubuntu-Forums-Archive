---
title: "play .mov on trailers.apple.com"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by dumble on 2011-01-14
Hello,

I installed ubuntu 10.10 desktop edition on my asus eeePC 1005PE. I did not like the netbook edition, so I switched.
 
Now I want to play trailers (.mov files) via trailers.apple.com. So it works fine when I choose 'watch' automatic or 480p. But when I choose 'download' 720p then I only hear the sound and do not see the video.

I tried it in chrome and firefox. Both do not work.

How can I watch the trailers on apple.com in 720p quality?

---

### Post by [Snc] on 2011-01-14
> **dumble said:**
> Hello,

I installed ubuntu 10.10 desktop edition on my asus eeePC 1005PE. I did not like the netbook edition, so I switched.
 
Now I want to play trailers (.mov files) via trailers.apple.com. So it works fine when I choose 'watch' automatic or 480p. But when I choose 'download' 720p then I only hear the sound and do not see the video.

I tried it in chrome and firefox. Both do not work.

How can I watch the trailers on apple.com in 720p quality?

you have to have the quicktime codecs installed to play apple quicktime mov files, i dont know about the quality tho, HD 720p should work out of the box if the hardware supports it.

---

### Post by dumble on 2011-01-14
yeah I think so. During installation of 10.10 I enabled ubuntu-restricted-addons. And afterwards I installed the ubuntu-restricted-extras via Ubuntu software center..

+ as I said, if i choose 'watch', it does work.. If i click download in trailers.apple.com website, I only hear the sound? Have you tried on your system?

---

### Post by dumble on 2011-01-14
yeah I think so. During installation of 10.10 I enabled ubuntu-restricted-addons. And afterwards I installed the ubuntu-restricted-extras via Ubuntu software center..

+ as I said, if i choose 'watch', it does work.. If i click download in trailers.apple.com website, I only hear the sound? Have you tried on your system?

---

### Post by d3ngar on 2011-01-14
What movie player are you using?

I have been using VLC since long as my default player. It has it's own codecs - and lots of them...

---

### Post by d3ngar on 2011-01-14
What movie player are you using?

I have been using VLC since long as my default player. It has it's own codecs - and lots of them...

simply install via:
```
sudo apt-get install vlc
```

it should sort out the dependincies...

---

### Post by d3ngar on 2011-01-14
What movie player are you using?

I have been using VLC since long as my default player. It has it's own codecs - and lots of them...

simply install via:
```
sudo apt-get install vlc
```

it should sort out the dependincies...

---

### Post by dumble on 2011-01-14
yeah but installed vlc, but it plays inside the browser. So I dont think it plays with vlc

---

### Post by d3ngar on 2011-01-14
You mentioned something about downloading it? If I download a mov file it play with VLC...

Also you can install the VLC browser plugin :)

GL

---

### Post by dumble on 2011-01-14
have you tried it? Go to trailers.apple.com. For example click 'The Fighter' trailer. So click the fighter, this link:
[http://trailers.apple.com/trailers/paramount/thefighter/](http://trailers.apple.com/trailers/paramount/thefighter/)

Click the arrow down of the blue botton (that says watch now), chose the 720p. What happens then? I know in windows it will start buffering the 720p version in quicktime. But in linux ubuntu, I only hear the sound.. but I see no video..

---

### Post by [Snc] on 2011-01-16
> **dumble said:**
> have you tried it? Go to trailers.apple.com. For example click 'The Fighter' trailer. So click the fighter, this link:
[http://trailers.apple.com/trailers/paramount/thefighter/](http://trailers.apple.com/trailers/paramount/thefighter/)

Click the arrow down of the blue botton (that says watch now), chose the 720p. What happens then? I know in windows it will start buffering the 720p version in quicktime. But in linux ubuntu, I only hear the sound.. but I see no video..

I tried, it works fine, under all HD resolutions. When I right click the movie and select "About" in the menu, I get a dialog saying "Totem Browser Plugin 2.32.0" etc etc etc,. In Firefox you can go to "about:plugins" and see which ones are installed, mine says "VLC Multimedia Plugin (compatible Totem 2.32.0)"

So, install and update VLC and it should work...

Enjoy!

---

### Post by dumble on 2011-01-18
Its not working with me. I allready installed vlc.

Then went also to syntapic package manager and installed mozilla-vlc-plugin (or something similar)

and, still not working. And again, It works when I want to watch (default and 480p). But it doesnt work when I click download 480p / 720p / 1080p

---

### Post by [Snc] on 2011-01-18
> **dumble said:**
> Its not working with me. I allready installed vlc.

Then went also to syntapic package manager and installed mozilla-vlc-plugin (or something similar)

and, still not working. And again, It works when I want to watch (default and 480p). But it doesnt work when I click download 480p / 720p / 1080p

what does about:plugins say?
does it return any error or any other message?

---

### Post by [Snc] on 2011-01-18
> **'[Snc] said:**
> what does about:plugins say?
does it return any error or any other message?
the smiley is in the way.... what i wanted to say was: have you tried to update the plugins in firefox?
```
about:plugin
```
as the url?

---

### Post by dumble on 2011-01-19
see html attachment for about: plugins:

---

### Post by mc4man on 2011-01-19
You're using the totem-mozilla plugin which should work fine for that type of apple trailers
For the dl ones try right clicking on the 720p > open in a new tab or new window, it should work then

---

### Post by durand on 2011-01-19
Maybe your netbook isn't powerful enough to play 720p?

---

### Post by dumble on 2011-01-21
mc4man and durand, you are both right. It works when I open in a new tab, but when I open the 720p the image is shocking (probably because my netbook can not handle it). When I open the 480p in a new tab it works fine.. 

Thanks for ur help

---

