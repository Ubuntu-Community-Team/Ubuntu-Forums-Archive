---
title: "Any idea how rtorrent can send an email once a file is finally there?"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-02-04
Thank you for the trick if it is possible

Regards

 :-({|=

---

### Post by mobilediesel on 2010-02-04
> **frenchn00b said:**
> Thank you for the trick if it is possible

Regards

 :-({|=

Yes, it looks like it's possible though I've not done it myself.
[http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Sendemailforcompleteddownloads](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Sendemailforcompleteddownloads)
For version 0.8.4 or newer:
add this to the .rtorrentrc
```
# First and only argument to rtorrent_mail.sh is completed file's name (d.get_name)
system.method.set_key = event.download.finished,notify_me,"execute=~/rtorrent_mail.sh,$d.get_name="

```
here's the rtorrent_mail.sh
```
#!/bin/sh
echo "$(date) : $1 - Download completed." | mail -s "[rtorrent] - Download completed : $1" alerts@example.com

```
and of course make that script executable with ```
chmod +x rtorrent_mail.sh
```

---

