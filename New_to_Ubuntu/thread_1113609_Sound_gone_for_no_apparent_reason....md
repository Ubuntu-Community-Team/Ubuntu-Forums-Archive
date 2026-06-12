---
title: "Sound gone for no apparent reason..."
date: 2009-04-01
forum: New to Ubuntu
---

### Post by Kajika on 2009-04-01
Once in a while (once a week or so) my sound will stop working. I've double checked by turning up my speakers, master volume, by trying rhythmbox & firefox, etc. It will come right back if I restart my computer though. Any way to fix this without having to restart? It's not a major problem but gets annoying if I have a very long movie loaded on hulu or something . Thanks!

---

### Post by _Purple_ on 2009-04-02
I had the same problem when I tried to run YouTube with VLC player or any other media player at the same time.

System> Preferences> Sound

I have set everything to Alsa under devices and now the problem is solved.

---

### Post by Elfy on 2009-04-02
Next time it happens it could be worth checking the logs - System Admin >System Logs (in Jaunty it's Log File Viewer)

see what it says at the end of messages

You could also see if dmesg gives any clue

```
dmesg |tail
```
will give last ten lines

---

### Post by Kajika on 2009-04-02
**Purple:** Didn't help, speakers just started making a buzzing sound until I switched everything back & restarted.
**Forestpixie** I honestly don't know how to read logs, it all looks like gibberish to me. Sorry, I'm sure it would have helped but I'm nowhere near linux-savvy yet.

---

### Post by Sarai the Geek on 2009-04-02
> **Kajika said:**
> **Purple:** Didn't help, speakers just started making a buzzing sound until I switched everything back & restarted.
**Forestpixie** I honestly don't know how to read logs, it all looks like gibberish to me. Sorry, I'm sure it would have helped but I'm nowhere near linux-savvy yet.

You could try posting your logs so folks who can read them can help. :)

---

### Post by Kajika on 2009-04-02
**sarai**Will do! I love this community!

---

### Post by _Purple_ on 2009-04-03
Looks like it didn't solve my problem either. It happened again after a long time. Got the follwing lines from log:

```
pulseaudio[5604]: protocol-native.c: Failed to push data into queue
last message repeated 620 times
```

---

### Post by _Purple_ on 2009-04-04
Managed to solve the problem using the steps given [here](http://ubuntuforums.org/showthread.php?t=843012). Thanks forestpixie for the link. :)

---

### Post by Elfy on 2009-04-04
> **Kajika said:**
> **Forestpixie** I honestly don't know how to read logs, it all looks like gibberish to me. Sorry, I'm sure it would have helped but I'm nowhere near linux-savvy yet.

I see that Sarai the Geek answered that - I had my tired head on at the time - I sort of expected you to do so if you couldn't read them :D

What you could do though, this takes little knowledge, would be to try searching for any error messages you did find, copy the error message and search for it - if you get no results - start taking bits of it away - you will find similar errors.

I use uboontu.com or googlbuntu.com for general searching of the buntu forums

Further the link _Purple_ refers to is one I gave him on irc, so there isn't a post missing from here, the link was

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

