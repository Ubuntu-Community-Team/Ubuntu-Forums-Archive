---
title: "remote mirroring of main screen under wayland, ala x11vnc"
date: 2018-01-13
forum: Networking &amp; Wireless
---

### Post by ivo-welch on 2018-01-13
plain vanilla ubuntu 17.10:  I am trying to find out whether there are any programs that allow me to see from a remote location what is on the display head of my ubuntu desktop.  (I do not want to start a new session, but look at what is on display :0.)  I believe x11vnc was one recommended solution, but it is not working with wayland.  I am getting a badimage error.  Pointers (and examples or tutorials) appreciated.

---

### Post by TheFu on 2018-01-13
I don't think anything does that, but you can use ffmpeg to capture the screen video (probably at 15fps) and have it stream that file. [https://trac.ffmpeg.org/wiki/Capture/Desktop](https://trac.ffmpeg.org/wiki/Capture/Desktop)  How you stream it is up to you.  A media center program can usually make files available, even if the files are being appended.

Of course, there are lots of different ways to solve most problems. Above is just what I think would actually work and be the best solution. There are others, like if you have nextcloud, then there is nextcloud-talk which supports screen sharing.  Google-hangouts, stuff like that.  talky.io is another.

If you just want to share a terminal, perhaps tmux or screen can be used. [http://wiki.networksecuritytoolkit.org/index.php/HowTo_Share_A_Terminal_Session_Using_Screen](http://wiki.networksecuritytoolkit.org/index.php/HowTo_Share_A_Terminal_Session_Using_Screen)

Wayland is pretty new.  I have no idea whether any of these solutions work with it or not.  You can logout, choose X11 and login to get the older, well supported, X11 methods back.

---

