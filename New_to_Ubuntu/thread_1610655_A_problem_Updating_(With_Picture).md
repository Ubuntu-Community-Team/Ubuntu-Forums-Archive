---
title: "A problem Updating (With Picture)"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by SammiSabbat on 2010-11-01
[IMG]http://i107.photobucket.com/albums/m297/SK84EVR_01/Screenshot-2.png[/IMG]

There is a triangle with an exclamation point inside and when i hover over it, It tells me what to do but i cant figure out how.

---

### Post by P4man on 2010-11-01
what happens when you run the updater: system > admin > update manager?
Possibly you will have to select another mirror in software sources.

---

### Post by SammiSabbat on 2010-11-01
[IMG]http://i107.photobucket.com/albums/m297/SK84EVR_01/Screenshot-3.png[/IMG]

My internet is connected.
Help?

---

### Post by sandyd on 2010-11-01
> **SammiSabbat said:**
> [IMG]http://i107.photobucket.com/albums/m297/SK84EVR_01/Screenshot-3.png[/IMG]

My internet is connected.
Help?

post output of
```

sudo apt-get update
```

---

### Post by MooPi on 2010-11-01
Can you try an update via the terminal
Open a terminal and ```
sudo apt-get update
```
Give us any errors that come out if it doesn't work.

---

### Post by SammiSabbat on 2010-11-01
it updated somethings but then at the end it did this.

"

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.


"

---

### Post by P4man on 2010-11-02
Same problem as here I think:
[http://ubuntuforums.org/showthread.php?t=1475399&page=2](http://ubuntuforums.org/showthread.php?t=1475399&page=2)

Check post 17, change your DNS settings.

---

### Post by SammiSabbat on 2010-11-02
THANK YOU THANK YOU THANK YOU! lol, it is working just fine now.

---

