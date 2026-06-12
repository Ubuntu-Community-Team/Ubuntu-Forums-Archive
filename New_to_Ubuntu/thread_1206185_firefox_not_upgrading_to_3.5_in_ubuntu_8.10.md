---
title: "firefox not upgrading to 3.5 in ubuntu 8.10"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by libihero on 2009-07-06
i tried manually upgrading firefox, and then i also got an alert with updates to upgrade firefox, but my firefox still doesnt show it to be upgraded.

---

### Post by nhasian on 2009-07-06
did you add the PPA for Ubuntu Mozilla Security Team to your sources list?

[https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa)

---

### Post by lovinglinux on 2009-07-07
Firefox 3.5 is installed side-by-side with 3.0.11

---

### Post by danggrianto on 2009-07-07
this is the code to istall firefox 3.5
```
wget -O - http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2 | tar xj -C ~
```

source: [lifehacker]("http://lifehacker.com/5306169/install-firefox-35-on-ubuntu-with-one-command")

---

### Post by lovinglinux on 2009-07-07
The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT). I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

