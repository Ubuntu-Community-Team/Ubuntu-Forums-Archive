---
title: "How do I install FL Studio using Wine?"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by HellaSpencer on 2010-10-07
So I just installed Ubuntu about 3 hours ago and I'm having trouble installing my old programs. Does installing programs on Ubuntu always SUCK? I want to put on FL Studio 9 (running Ubuntu Netbook 10.04) and I even read the tutorial and it's giving me a ton of trouble. I don't really know how to type the terminal commands. Is there an easy way to install Windows programs on here? Any help appreciated.

---

### Post by juil on 2010-10-07
Well, you did come to the right place...
It only 'sucks' because you don't know how to do it.
With anything new there is a learning curve and installing apps in Linux is different than in Windows.

That program is Windows only compatible. 
Using Wine might help you run it in Ubuntu but there is no guarantee. 
Look in Synpatics and it should have Wine.
Wine allows Windows applications to run on Linux.

---

### Post by HellaSpencer on 2010-10-07
Yea I knew it was only Windows compatible but even messing around with Wine I can't get it to work. Synaptics?

---

### Post by aysiu on 2010-10-07
> **HellaSpencer said:**
> Is there an easy way to install Windows programs on here? No, just as there isn't an easy way to install Mac programs on Windows or Linux programs on Mac (Fink is not easy).

As you may guess, installing Linux programs on Linux is quite easy, just as installing Windows programs on Windows is easy.

If you want to install Linux programs on Linux, this should help you out:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Mileage may vary on trying to use Wine to install FL Studio:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=178](http://appdb.winehq.org/objectManager.php?sClass=application&iId=178)

---

### Post by juil on 2010-10-07
If you can't get it to work with Wine, please post error messages you are getting or whatever the problem is so we can help you.

---

### Post by aysiu on 2010-10-07
> **HellaSpencer said:**
> Yea I knew it was only Windows compatible but even messing around with Wine I can't get it to work. Synaptics?
Wine isn't a cure-all for running Windows programs on Linux.

It's a hack to *try* to run Windows programs on Linux. Some Windows programs will run. Others won't. Even the ones that do run may be difficult to set up in Wine... or not have full functionality.

I'm retitling your thread so you can get some proper help.

---

### Post by HellaSpencer on 2010-10-07
Ok so when I try to run it it says

> The file '/home/spencer/.cache/.fr-M8XKqb/Fruity Loops FL Studio XXL Producer 9.0/flstudio_9.0.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by Locke_99GS on 2010-10-07
Run it with wine. From within the directory:
```

wine ./flstudio_9.0.exe

```

---

### Post by juil on 2010-10-07
You could try following the steps in this link:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by HellaSpencer on 2010-10-07
This is all way over my head. Lol maybe I'll just try and install this stuff tomorrow. I've been irritated by Ubuntu enough for the night.

---

