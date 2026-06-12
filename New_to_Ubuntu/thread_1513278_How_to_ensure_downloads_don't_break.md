---
title: "How to ensure downloads don't break?"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by GeorgeOfTheBush on 2010-06-19
How to ensure that downloads **don't** break - while [COLOR=Blue]downloading large files[/COLOR] - when your laptop's power manager puts the computer to sleep?

Its frustrating to start download of large files and a couple of hours later you find that your laptop has gone to sleep causing the download to break - and you have to start all over again.

---

### Post by howefield on 2010-06-19
Try a download manager.

[https://help.ubuntu.com/community/DownloadManager](https://help.ubuntu.com/community/DownloadManager)

And/or alter your power settings when downloading large files.

---

### Post by nothingspecial on 2010-06-19
Use wget.

If your download breaks, use the -c flag.

You already have it on your system.

---

### Post by tekkidd on 2010-06-19
Well you can start by going into the power settings and telling the laptop never to sleep. You also would want connect the laptop to the router via ethernet. Also it would be best to download via wget (wget <url>) rather than firefox. And to ensure the download is all their after downloading, run an MD5 sum (google it to find out how).

---

