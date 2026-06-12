---
title: "ping tool for panel or notification area?"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by doublemeat on 2007-12-04
Hello, I have a really flaky (EVDO) internet connection.  It's like the stone ages.  I'm looking for a little applet that will ping an internet address periodically (say every 5 seconds), running as a panel applet or notification area applet, with something like a simple red or green light.

There are several such (freeware) apps for Windows that run in the task tray, so I have those boxes covered.  But I've been unable to find one for ubuntu (gnome).  Surely such a thing exists!  Maybe I'm not doing the right google search.

Does any one know of one, or have some good tips for googling very specific Linux stuff?  I've tried many variations and parsings and likenesses of:

```
linux ping "notification area" network
```

Thanks!

---

### Post by redhatoscar on 2007-12-04
The application you are looking for is **Smokeping**

apt-get install smokeping

---

### Post by redhatoscar on 2007-12-04
<a href="http://www.linux-magazine.com/issues/2005/54/smoked_out?category=13390"> Linux Magazine </a>

---

### Post by oberoc on 2007-12-06
If you are using 7.10 Gutsy, you can try gdesklets. Applications->Accessories->gdesklets. I can't find the exact desklet that I used, so you will have to hunt around. 

HTH,
Tino

---

### Post by doublemeat on 2007-12-18
> **redhatoscar said:**
> The application you are looking for is **Smokeping**

apt-get install smokeping

Thanks.  I tried it.  That is really complicated though.  Looks like it requires editing a config file (in a strange one-off syntax), and both a client and a server.

What I'm ideally looking for is something like [Konst Pinger]("http://www.visualsoftru.com/pinger.asp") for Windows.  Although it has some more "power" features, it is mainly just a simple little task tray applet, where all you have to do is 1) enter an address to ping [either local or internet], 2) enter how often, and 3) let it go.  It will show a green box if the last ping was sucessful, red if not.  Easy, shmeezy.  

It is a client-only installation.  On my Windows machines, I have it ping echo.net every five seconds.  This is the easiest way to tell me I need to reboot the router (the Kyocera KR1 - I've gone through three and multiple evdo cards and a full-strength signal; all of them needed rebooting several times daily to get the wan connection back [absolute total crap]).  Otherwise, the process is very painful.

Something like this as a *SIMPLE* Gnome Panel applet would be SOOOOOO useful!!!  (Any developers listening?)  

If anyone knows of something like this, please reply...thanks!

---

### Post by avdongen on 2008-01-16
** BUMP **

Need one to but cant seem to find one, any luck yet on finding one ?

Grts

---

### Post by doublemeat on 2008-02-20
> **avdongen said:**
> ** BUMP **

Need one to but cant seem to find one, any luck yet on finding one ?

Grts


I still haven't found one, and have given up.  I'll search again in another year or so.  ;-)  This is such a simple concept, it should be rediculously easy to write one.  I used to program with Sockets (using pre-built components), and it was stupidly easy.  I ping is totally trivial.  And a UI to show a red or green light for a result, maybe a command line to specify host and interval, should be totally trivial.  Unfortunately I don't know any languages other than bash, that works with a dockable UI.  This would be a perfect opportunity to learn.  (Small app, small scope, quick 'n dirty.)  If I ever do get around to it, I'll post a notice here, but

---

