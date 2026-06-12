---
title: "Transmission Bittorrent Daemon on Headless with Autoadd"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by RichardCL on 2009-11-13
Dear Forum,

I'm using transmission on a desktop and want to move the whole application to a headless Karmic server. The difficult part is that I want to take the partially completed torrents too.

I installed transmission-daemon and it works fine. I also copied the partially completed torrents to /home/bittorrent/downloads (bittorrent is the user that will spawn the daemon).

Now I have the directory full of torrents that I want to add but don't want to do each one manually.

Can't I just have a function "automatically add torrents from..." like in the GUI version of transmission?

I have the web interface up and running but no option there.


Thanks in advance


Rich

---

### Post by lovinglinux on 2009-11-13
Copy the folders **torrents** and **resume** from **~/.config/transmission** to the new machine.

---

