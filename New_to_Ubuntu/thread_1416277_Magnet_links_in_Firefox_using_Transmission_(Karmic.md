---
title: "Magnet links in Firefox using Transmission (Karmic)"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by prince.buster on 2010-02-25
Transmission supports Magnet links from version 1.80 onwards, which will probably not be added to the Ubuntu repositories until the Lucid Lynx release in april.

You can upgrade it anyway using the PPA:
[https://edge.launchpad.net/~transmissionbt/+archive/ppa]("https://edge.launchpad.net/~transmissionbt/+archive/ppa")

A tutorial on adding PPA's can be found [here]("http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu").

Then you must configure Firefox to recognise the Magnet links.

* Type about:config into the address bar and press Enter.
* Right-click -> New -> Boolean -> Name: network.protocol-handler.external.magnet -> Value -> true
* Right-click -> New -> String -> Name: network.protocol-handler.app.magnet -> Value -> /usr/bin/transmission
* Ensure network.protocol-handler.expose-all is set to true
(thanks to kwacka for this info)

P2P is the way forward, folks

p.s note that this only works for magnet links that refer to torrent files. Other P2P URN's such as those found on Gutenberg.org will not work with the above settings. We are still waiting for comprehensive URN handling in Firefox.

---

### Post by mörgæs on 2010-02-25
Confirmed: In the alpha version of 10.04, Transmission is version 1.90 supporting magnet links.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by snapy on 2010-04-30
> **mörgæs said:**
> Confirmed: In the alpha version of 10.04, Transmission is version 1.90 supporting magnet links.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

does firefox also work correctly?

---

### Post by phpdonk3y on 2012-04-07
Before trying the about:config route try disabling your firewall for the first torrent then you may find that it configures itself ie your firewall is blocking the process. You only need to disable it for a minute then put it backup.

Try ```
sudo ufw status
```if it says its enabled then try

```
sudo ufw disable
```click on the torrent link then it should configure itself to handle them its just the initial step that seemed to screw it up

then ```
sudo ufw enable
``` to stay safe[r]

worked for meeeeee.
BYe

---

### Post by oklokl on 2012-04-07
[https://launchpad.net/~tualatrix/+archive/ppa]("https://launchpad.net/%7Etualatrix/+archive/ppa")

sudo add-apt-repository ppa:tualatrix/ppa

sudo apt-get update

sudo apt-get install qbittorrent ubuntu-tweak

ubuntu-tweak

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=215612&stc=1&d=1333775083[/IMG]
[http://ubuntuforums.org/attachment.php?attachmentid=215612&stc=1&d=1333775083](http://ubuntuforums.org/attachment.php?attachmentid=215612&stc=1&d=1333775083)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=215613&stc=1&d=1333775083[/IMG]
[http://ubuntuforums.org/attachment.php?attachmentid=215613&stc=1&d=1333775083](http://ubuntuforums.org/attachment.php?attachmentid=215613&stc=1&d=1333775083)

Firefox open
start qbittorrent

sudo ufw allow out 6881:6999/tcp
sudo ufw allow out 6881:6999/udp
sudo ufw allow out 30000:60000/tcp
sudo ufw allow out 30000:60000/udp

---

### Post by mikewhatever on 2012-07-03
> **prince.buster said:**
> Transmission supports Magnet links from version 1.80 onwards, which will probably not be added to the Ubuntu repositories until the Lucid Lynx release in april.

You can upgrade it anyway using the PPA:
[https://edge.launchpad.net/~transmissionbt/+archive/ppa]("https://edge.launchpad.net/~transmissionbt/+archive/ppa")

A tutorial on adding PPA's can be found [here]("http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu").

Then you must configure Firefox to recognise the Magnet links.

* Type about:config into the address bar and press Enter.
* Right-click -> New -> Boolean -> Name: network.protocol-handler.external.magnet -> Value -> true
* Right-click -> New -> String -> Name: network.protocol-handler.app.magnet -> Value -> /usr/bin/transmission
* Ensure network.protocol-handler.expose-all is set to true
(thanks to kwacka for this info)

P2P is the way forward, folks

p.s note that this only works for magnet links that refer to torrent files. Other P2P URN's such as those found on Gutenberg.org will not work with the above settings. We are still waiting for comprehensive URN handling in Firefox.

This doesn't work, even if the correct path for transmission (/usr/bin/transmission-gtk) is used. Another disadvantage of this method is - there is no apparent way to undo the changes.

This is the way that works: [http://maketecheasier.com/open-magnet-link-in-browser/2010/02/19](http://maketecheasier.com/open-magnet-link-in-browser/2010/02/19)

...and to undo the changes, run "gedit .mozilla/firefox/*.default/prefs.js", search for "magnet" and remove the two lines.

---

### Post by ubudog on 2012-07-03
Old thread closed.

---

