---
title: "[SOLVED] SSH &amp;amp; rTorrent"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by ghindo on 2008-06-03
I'm using SSH to tunnel into a remote machine.  I'm trying to run rTorrent on that remote machine, but every time I close an SSH connection, I close rTorrent as well.  How can I keep rTorrent open and running on that remote machine?

---

### Post by balance07 on 2008-06-04
use 'screen' it's a virtual terminal
basically, start rtorrent with 'screen rtorrent'
then "detach" from the screen by pressing 'ctrl-a' then 'd'
you can then logout, whatever (just keep maching running)
when u come back, type 'screen -r' to "reattach"

google "gnu screen" for more details

---

### Post by ghindo on 2008-06-06
> **balance07 said:**
> use 'screen' it's a virtual terminal
basically, start rtorrent with 'screen rtorrent'
then "detach" from the screen by pressing 'ctrl-a' then 'd'
you can then logout, whatever (just keep maching running)
when u come back, type 'screen -r' to "reattach"

google "gnu screen" for more detailsThat did the trick, thanks!  Pretty easy, too :)

---

### Post by codetiger on 2009-10-10
That works great. My torrent box now needs no monitor. :) Otherwise I have to attach my monitor to it everytime I start. 

Thanks a lot for the tip

---

