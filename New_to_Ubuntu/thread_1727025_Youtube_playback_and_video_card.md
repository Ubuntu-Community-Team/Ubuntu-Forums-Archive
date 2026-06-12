---
title: "Youtube playback and video card"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by jonobugs on 2011-04-12
I'm not really sure what my problem is so I'm posting to this forum because I'm pretty newbish even though I've been using Ubuntu for about a year now.

So, I can't view Youtube anymore. I get the general error, "An error occurred, please try again later." on top of a black screen. 

I've tried different browsers with the same problem. Interestingly I'm still able to watch embedded Youtube videos if they're posted on Facebook or some other sites.

I can also watch Youtube videos if I boot up in Windows.

I first started having problems a couple of months ago after an update, but then, I just got a white or greyish screen with no message. I thought that perhaps after another update it would correct itself, but it didn't. However, now I do get an error message.

The other thing that has changed is that I installed drivers for my video card from the manufacturer's website. The drivers are for AMD Radeon HD 6800 Series. I used the 64bit drivers.

Anyway, my video now works better, but I still can't view Youtube videos. I'm not sure if it's because of the video card drivers or something else.

I was hoping someone might have experience with this problem!

Cheers for any help.

Jono

---

### Post by K_45 on 2011-04-12
I'd remove the downloaded drivers and try the built in ones.

---

### Post by lovinglinux on 2011-04-12
Try deleting YouTube cookies.

Also check the discussion at [http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html](http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html)

---

### Post by earthpigg on 2011-04-12
youtube also started being wonky for me, a few months ago. 

it has something to do with youtube having several flash items (instead of *just* the video) on any given video's page.

workaround for me was to use flashblock firefox addon, so i can control which flash items load.

incedentally, facebook and many other sites are now also much faster to load and better behaved in general.

---

### Post by wlraider70 on 2011-04-12
what happens if you go to an html5 video on youtube?

---

### Post by jonobugs on 2011-04-20
Thanks for all the suggestions!

Sorry for the long delay, I didn't realize I had responses yet. I was waiting for an email to tell me there was a reply....

Anyway the default Linux drivers don't work at all. I end up going into the lowest graphics mode which makes everything look fat, especially in videos.

Also, many games and other programs won't work in low graphics mode.

After I installed the drivers, everything is much clearer and better, so I'm really reluctant to go back to low graphics mode.

I tried using the flashblock addon, but maybe I'm not using it correctly. It stops the video from loading as well, and when I click to start it up, it gives the same error message.

I tried viewing the HTML5 videos on youtube but that didn't work either. I COULD watch an html5 video on the original HTML5 development site though.

Oh, I can also seem to watch many youtube videos if I'm viewing them in Facebook. Not all of them though.

I'd like to mention that I have the same problem viewing youtube videos regardless of which browser I use. 

I went into Windows (using a dual boot system) and I was able to watch youtube videos in any browser.

I haven't tried deleting youtube cookies yet. I'm still trying to figure out how to do that.

Thanks again for the help...still not working yet though!

Jono

---

### Post by jonobugs on 2011-04-20
Ahhh, I think deleting the cookies solved the problem! Kind of.

Going to this webpage explains in details:
[https://bugs.launchpad.net/ubuntu/+source/gnash/+bug/555345](https://bugs.launchpad.net/ubuntu/+source/gnash/+bug/555345)

Basically, delete the firefox cookies for youtube and then block youtube cookies. The only problem with that solution is that you won't be able to log into your youtube account. However, I can now watch youtube videos!!

Thanks all.

---

