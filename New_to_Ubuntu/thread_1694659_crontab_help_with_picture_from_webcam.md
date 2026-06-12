---
title: "crontab help with picture from webcam"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by djyoung4 on 2011-02-24
So I have a htpc sitting next to the tv in my living room and there is a webcam connected to it.  I would like to set up a crontab entry that would take a picture with the webcam at a certain time of the day.  From what I have read about cron it shouldn't be too difficult to set up but I don't know the command to take the picture with the webcam.  any help is greatly appreciated

---

### Post by seawolf167 on 2011-02-24
A way to do this would be to first install streamer

```
sudo apt-get install streamer
```

then test the command to take a picture from your webcam

```
streamer -c /dev/video0 -o some.file.jpeg
```

once you have what you want, add a crontab entry

```
sudo gedit /etc/crontab
```and add a line like this to run each day at 6am some.command as root

```
00 6 * * * root some.command
```see the link to crontab in my  sig for more information on how to format crontab entries.

---

### Post by djyoung4 on 2011-02-25
> **seawolf167 said:**
> A way to do this would be to first install streamer

```
sudo apt-get install streamer
```

then test the command to take a picture from your webcam

```
streamer -c /dev/video0 -o some.file.jpeg
```

once you have what you want, add a crontab entry

```
sudo gedit /etc/crontab
```and add a line like this to run each day at 6am some.command as root

```
00 6 * * * root some.command
```see the link to crontab in my  sig for more information on how to format crontab entries.

works good.  the only problem is I don't want it to overwrite the image that gets taken the time before.  I want it to just take pictures every time and sequentially name them or some other way where it doesn't write over the picture from the previous time.  Nor can I get it to save into a different folder besides my home folder

---

### Post by aeiah on 2011-02-25
you shouldnt need it to run as root, and you should be able to save it to any folder you choose (if you have the right permissions)
```

streamer -c /dev/video0 -o /path/to/filename.jpg

```

should work fine. for using a different name each time, it'd probably make the most sense to name it with the date (or time and date if you're likely to run it more than once a day). you can use the 'date' command for this, within your command like so:

```

streamer -c /dev/video0 -o /path/to/filename_$(date '+%Y%m%d').jpg

```
this will save the photo in /path/to/ with the name 'filename_20110225.jpg' - setting the date out like this will ensure that alphabetical ordering is the same as chronological ordering. loads of formatting options exist for 'date', just look at the manual for them.

your crontab entry would look like this (for 6am):
```

0 6 * * * streamer -c /dev/video0 -o /path/to/filename_$(date'+%Y%m%d').jpg

```

---

### Post by djyoung4 on 2011-02-26
> **aeiah said:**
> you shouldnt need it to run as root, and you should be able to save it to any folder you choose (if you have the right permissions)
```

streamer -c /dev/video0 -o /path/to/filename.jpg

```

should work fine. for using a different name each time, it'd probably make the most sense to name it with the date (or time and date if you're likely to run it more than once a day). you can use the 'date' command for this, within your command like so:

```

streamer -c /dev/video0 -o /path/to/filename_$(date '+%Y%m%d').jpg

```
this will save the photo in /path/to/ with the name 'filename_20110225.jpg' - setting the date out like this will ensure that alphabetical ordering is the same as chronological ordering. loads of formatting options exist for 'date', just look at the manual for them.

your crontab entry would look like this (for 6am):
```

0 6 * * * streamer -c /dev/video0 -o /path/to/filename_$(date'+%Y%m%d').jpg

```
That doesn't work.  I tried it and nothing.  also the picture the webcam takes looks awful.  is there a way to change the picture quality settings in the script[ This is the webcam that I am using in case your interested]("http://www.amazon.com/Xbox-360-Live-Vision-Camera/dp/B000GCGB3M").  Now the crontab entry won't even work.  Heres the entry:
```
00 0    * * *   root    streamer -c /dev/video0 -o filename_$(date '+%Y%m%d').jpg
```
Is there a way to check for errors

---

### Post by aeiah on 2011-02-26
well, does the command work outside of cron? and yes, you can probably change the resolution. look at the manual for streamer. in a terminal you'd do ```
man streamer
```

i dont own a webcam, nor have streamer installed.

---

### Post by djyoung4 on 2011-02-27
yes the command works and the manual for streamer is very short.  doesn't contain too much info other then a couple basic examples and some attributes.

---

### Post by djyoung4 on 2011-02-28
any ideas

---

### Post by seawolf167 on 2011-02-28
I suggest looking at the streamer help section

```
streamer --help
```

there are a lot of options you can use for audio/video.

Once you get the settings you like (along with the above posted how-to for appending the date onto the filename), setup a cron entry (but have it run at ~1 minute intervals) so you can easily check to see if it is working without waiting until midnight (i.e. 00 0))

A double check to ensure cron is running:

```
ps -ef | grep -i cron
```

---

