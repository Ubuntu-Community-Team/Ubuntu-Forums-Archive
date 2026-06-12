---
title: "Shockwave flash crash"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by phoenix7 on 2011-03-05
The flash plugin in my firefox started to crash these days. Whenever I go to youtube.com to watch a video, as soon as I open the page the shockwave plugin crashes. At the same time, I can see youtube videos in Facebook! This is started to happen in these days possibly after updating the system (I regularly apt-get update & upgrade). Any thoughts/ideas?

---

### Post by lasca85 on 2011-03-06
I have exactly the same issue. Embedded flash works, direct youtube page makes flash plugin crash.

---

### Post by dooper on 2011-03-06
I have the same problem runnning Meerkat and firefox 3.6.13

When i go to youtube to view videos, as soon as i click play,the video is colourcast only in red. sometimes the flash player crashes and says click to reload.

Tried youtube with google chrome and all works ok.

I also have flashaid installed and ran that but it didnt fix the problem..

Presmuably this is a firefox issue?

---

### Post by marl30 on 2011-03-06
Perhaps this post over by Webupd8 maybe of some assistance: [http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html](http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html)

---

### Post by marl30 on 2011-03-06
Try the flash-aid plugin as well. I've had no problems with flash nice I started using it:[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by lasca85 on 2011-03-06
> **marl30 said:**
> Perhaps this post over by Webupd8 maybe of some assistance: [http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html](http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html)

Thanks, I tried one of the solutions - installing Adobe Flash Player 11 Incubator and it solved the problem.

[http://www.multimediaboom.com/install-adobe-flash-player-11-incubator-in-ubuntu-11-04-10-10-10-04/](http://www.multimediaboom.com/install-adobe-flash-player-11-incubator-in-ubuntu-11-04-10-10-10-04/) - this helped me with installing flash 11.

Then I copied libflashplayer.so to /opt/google/chrome/ and renamed it to libgcflashplayer.so (replace the old one). Copying this file to proper Mozilla/Firefox directory should solve the issue for FF.

---

### Post by beew on 2011-03-06
Actually the most elegant solution would be not to use flash altogether for youtube. In FF you can install the flashvideoreplacer plugin  (you need to install gecko-player from the repo or a PPA because the flashvideoreplacer uses mplayer as a backend) This works a lot smoother than flash because it uses a lot less CPU than flash. On one of my older computers I can watch 720p full screen using the flashvideoreplacer whereas using flash I can only go up to 480p without fullscreen.
(One exception, if you have a Nvidia card than flash 10.02 uses vdpau so  it would be smooth and uses very little CPU as well if it doesn't crash  first) 

Another alternative is not to use a browser at all, install minitube. Videos actually load faster than youtube itself and it uses the lowest amount of CPU because it doesn't have to work through a browser. But make sure you get version1.4 from a ppa, the version in the Ubuntu repo is broken.

---

### Post by DMKryl on 2011-03-06
Thx i've installed flash 11 and solved the problem

---

