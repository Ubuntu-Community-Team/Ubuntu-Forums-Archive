---
title: "desktop session recorder"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by emeraldgirl08 on 2011-06-02
I am wondering if anyone has any experience with the ones in the Ubuntu Software Center? 

I would like one of these programs and am asking the community which desktop session recorder works very well.

TIA.

---

### Post by iansane on 2011-06-02
I've used recordmydesktop with gtk-recordmydesktop which shows up in software center as "Desktop Recorder".

Just installed it on 64bit 11.04 and got an error that was easily remedied by installing libxdamage-dev from system>administration>synaptic package manager, and then restarting. The error was that the xdamage extension was missing or something like that (oops forgot the exact message). But it works good now and it's a simplistic interface. It saves the videos as ogv which can then be converted to avi or other formats with different programs.

[http://ubuntuforums.org/showthread.php?t=806125](http://ubuntuforums.org/showthread.php?t=806125) for using mencoder in a script or command line.

There is also something called recorditnow in synaptic. If you have gnome, it will probably need to install a ton of kde libs because it's made for kde.

---

### Post by pqwoerituytrueiwoq on 2011-06-02
i have had issues with recordmydesktop (if i have compiz on)
i have been using xvipcap some people like kazam though

---

### Post by iansane on 2011-06-02
> **pqwoerituytrueiwoq said:**
> i have had issues with recordmydesktop (if i have compiz on)
i have been using xvipcap some people like kazam though

Pros/Cons matter of opinion I guess.

xvidcap seems to work fine on my system. (installed it too to compare it with recordmydesktop).

With recordmydesktop I get to put the capture area where ever I want it but with xvidcap it starts in the top left corner and can only be made bigger. I couldn't drag it to a specific area.

With recordmydesktop I got to choose where to save the file and what to name it. In xvidcap it puts the file in my home directory named a default "test-0000.mpeg" so I have to go and rename it.

Big pro in my opinion for xvid is that it saves it as a mpeg which means any xvid capable dvd player can play the video if I burn it straight to a cd or dvd without the need for any conversion.

---

