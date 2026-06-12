---
title: "Transmission pauses torrent automatically."
date: 2014-05-09
forum: Networking &amp; Wireless
---

### Post by drakonisoh on 2014-05-09
I am downloading a large torrent file(> 100 GB). Since my download speed is low(64 kB/s), I am downloading the files individually. For the past three nights, I left transmission running and went to sleep. To my surprise, each time I woke up, not even an hour of progress had been made. Both my computer and my internet connection were continously running the whole night. The reason for the lack of downlaod progress was the the torrent had automatically been paused by transmission, showing a 'Verify local data' error. The error message did not persist and the files were downloaded without corruption after simply resuming. This problem has been annoying me greatly, since this does not happen at day but at night(I live in south-asia, so it may be due to differences in time-zone betweeen me and the peers). How can this be solved? I am using transmission 2.51 and ubutnu 12.04. I tried asking on the transmission gtk help forums but have not gotten replies for long.

At the very least, how can the torrent's be automatically resumed periodically?

---

### Post by vanadium on 2014-05-09
The error message indicates that some of the local data are not correct, in which case further download is suspended. With right-click on the torrent, then selecting "Verify local data", the local data will be checked, and wrong parts are removed. After that, download of the torrent will resume.

Normally this would only happen if you have stopped and restarted the torrent. I would not expect this would happen during a download: then, each piece is checked as it is downloaded, and the piece is redownloaded if the check does not pass. I wonder whether the issue you have may be due to a mal functioning hard drive.

---

### Post by drakonisoh on 2014-05-09
> **vanadium said:**
> The error message indicates that some of the local data are not correct, in which case further download is suspended. With right-click on the torrent, then selecting "Verify local data", the local data will be checked, and wrong parts are removed. After that, download of the torrent will resume.

Normally this would only happen if you have stopped and restarted the torrent. I would not expect this would happen during a download: then, each piece is checked as it is downloaded, and the piece is redownloaded if the check does not pass. I wonder whether the issue you have may be due to a mal functioning hard drive.

I did not need to click on "Verify local data", only had to click resume. 

There's probably nothing wrong with my hard drive, since the downloads even immediately before the discussed one went smoothly. Neither did I rename any files.
I had paused the torrent each time, though, but the download continued flawlessly for 15-20 mins before I slept.

However, if this problem can be fixed simply by resuming, does transmission not have an option to resume the download if such a problem occurs, or at least periodically check if a particular torrent is paused and then automatically resume it? Auto-resume would be helpful if one needs to leave torrents unattende for a long time. I've searched for many hours for such a script, but have not found one.

Thanks for replying.

---

