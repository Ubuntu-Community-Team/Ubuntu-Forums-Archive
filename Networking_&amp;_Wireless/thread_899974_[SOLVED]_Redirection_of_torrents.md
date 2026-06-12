---
title: "[SOLVED] Redirection of torrents"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by Capilano on 2008-08-24
Greetings

I would like to thank all of those who post solution to this forum. It has been a great help for me. On this subject, I may be obtuse, but I cannot find the right solution.
The need: I have a laptop for everyday use. However, I do not want to leave it on at all time. When I download torrents file, it may take a long time for them to complete/ I would like to be able to initiate a torrent download on my laptop and have the actual download send to another box on my home network. This network is controlled by the laptop through SSH. I can see the file on the other machine and do what I want with them.
Can someone offer a solution or an indication as to where I could find the relevant info.
Thank you all in advance.

:confused:

---

### Post by cariboo on 2008-08-25
I would suggest torrentflux, it is a web based client, If you have apache installed on your server you can download the torrent to your server with out having to tie up your laptop.

Jim

---

### Post by hosk on 2008-08-25
Also, if you are SSHing, try using screen & btdownloadcurses

```
screen
```

```
btdownloadcurses
```

the man file for btdownloadcurses has all the stuff you might want, like max upload speed, and once you have BTdownloadcurses running hit CTRL A and then D and you'll detach the screen and your torrent downloading will continue.

---

### Post by Capilano on 2008-08-26
Thank you very much for your help. It works flawlessly.:guitar:

---

