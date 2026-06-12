---
title: "No CD/DVD Drivers Installed With Ubuntu 10.04.2"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by perpetualtimewaster on 2011-06-03
[SIZE=3]I'm unable to play or burn any dvds due to the lack of drivers being installed by the Ubuntu 10.04.2 cd.  I can't download any Torrent files & get error messages saying my file system is almost full.  I tried searching for installing drivers on this forum & I keep getting an error messages saying my search term words were too small.  Any ideas?[/SIZE]

---

### Post by Allavona on 2011-06-03
The only thing you need for torrents is a torrent client. Ktorrent, Vuse, and the default Transmission all work fine, sometimes it takes awhile for the trackers to refresh.

Ubuntu doesn't install non-free codecs by default. You'll need to do that yourself.

---

### Post by jramshu on 2011-06-03
```
sudo apt-get install ubuntu-restricted-extras
```

---

