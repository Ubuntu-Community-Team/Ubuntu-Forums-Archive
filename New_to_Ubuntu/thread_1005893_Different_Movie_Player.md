---
title: "Different Movie Player?"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by mag1strate on 2008-12-08
Hey guys, I was just wondering if there is a problem with the video I downloaded, or the movie player that comes with Intrepid is bad. The video seems to flicker and when another window is moved over the movie window, the video plays over that window to the size of the video.. sorry if the explanation is bad, but just wondering if you guys know anything?

---

### Post by MarblePanther on 2008-12-08
It is probably compiz, turn it off and see how it plays

also try enabling deinterlace and install the ubuntu-restricted-extras package to get codecs

---

### Post by MarblePanther on 2008-12-08
Oh, another Reznor fan!

---

### Post by JoshuaRL on 2008-12-08
You also might try VLC.  Its in the repos and Add/Remove.  Many here prefer it to any other video player.

---

### Post by MarblePanther on 2008-12-08
We solved it.  Compiz problem/buggy video driver.

For others:

install fusion-icon from the repos and set it to startup automatically so you can toggle compiz

Also install mplayer or vlc instead of totem

---

### Post by binbash on 2008-12-08
go to your video player's configuration and set the output to x11

---

