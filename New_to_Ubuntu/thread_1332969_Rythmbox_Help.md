---
title: "Rythmbox Help"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2009-11-20
I found a website that allows me to download a package that will display an awesome lyrics screenlit in the bottom corner of my screen when Im playing a song from Rythmbox. I downloaded the package, but I have no idea how to get it to work or install it to work in Rythmbox. Any help please. 

Heres the link to the site where I downloaded the package

[http://www.gnome-look.org/content/show.php?content=98762&forumpage=0](http://www.gnome-look.org/content/show.php?content=98762&forumpage=0)

---

### Post by mikewhatever on 2009-11-20
Just googled it for you. ;)

[http://www.unixmen.com/linux-tutorials/351-display-lyrics-of-your-playing-track-with-lyrics-screenlet](http://www.unixmen.com/linux-tutorials/351-display-lyrics-of-your-playing-track-with-lyrics-screenlet)

---

### Post by Captainflowers91 on 2009-11-21
I tried what the page said, but the problem is I can't install Screenlets. Im running 9.10 Karmic Koala if that means anything. Anyway, heres the message that displays when I try to install via the Ubuntu Software Center

E:I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch):

---

### Post by mikewhatever on 2009-11-21
That's odd, screenlets depend on python and not java. Can you post the exact output of that command.

sudo apt-get install screenlets

---

### Post by Captainflowers91 on 2009-11-21
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  screenlets: Depends: python-wnck but it is not going to be installed or
                       python-gnome2-desktop but it is not going to be installed
              Recommends: python-feedparser but it is not going to be installed
              Recommends: python-gtkmozembed but it is not going to be installed or
                          python-gnome2-extras (< 2.19) but it is not going to be installed
              Recommends: iceweasel but it is not installable or
                          firefox
              Recommends: python-evolution but it is not going to be installed or
                          python-gnome2-desktop but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-15-1) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by mikewhatever on 2009-11-21
Try updating the list of packages with **sudo apt-get update** .

---

### Post by Captainflowers91 on 2009-11-21
No such luck :/

---

### Post by mikewhatever on 2009-11-21
> **Captainflowers91 said:**
> No such luck :/

What's that supposed to mean? Can you also post the output of the last command.

---

### Post by Captainflowers91 on 2009-11-21
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0DA7581859566E92
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768D
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43BB102C405A15CB
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 638ABCA0FA3A1271
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0CC1223EE2314809
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D79F61BE8D31A30
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A8E3034D018A4CE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC6D7D9D009ED615
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F104610CF0876AC9
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 978228591BD3A65C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4FEC45DD06899068
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6298AD34413576CB
W: GPG error: [http://le-web.org](http://le-web.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A423FD95416E75D



I posted the whole thing, beginning with when it began listing errors

---

### Post by mikewhatever on 2009-11-21
You seem to be using a bunch of unsigned launchpad repositories instead of a standard set. May I ask why?

To change that, go to System->Admin->Software Sources and select a server, preferably near your geo location.

---

### Post by Captainflowers91 on 2009-11-21
Well, I rebooted and it said I had some broken packages, and when I fixed those and ran the terminal prompt you gave me, it worked like a charm. Thanks for all the help

---

