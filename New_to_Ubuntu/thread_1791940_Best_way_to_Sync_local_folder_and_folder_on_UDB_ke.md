---
title: "Best way to Sync local folder and folder on UDB key?"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by MaxVK on 2011-06-27
Hi. I have Lucid running on my main home machine, but I have a small app that I wrote that is used on both. The app folder contains several other sub-folders, and they in turn contain various data files.

Since I often take the app out on a USB key and edit some of the data files in the process, Id like something that can sync the two versions of the app, in either direction, so whichever version has changed those changes will be seen on both versions.

Preferably Id like something that is a simple GUI or can easily be scripted so an icon can be clicked once the USB key is inserted. It would be nice if the program used could detect the USB key as well, but that is not a requirement, just a fancy.

The data that would be sync'ed is plain text, often just HTML, but it is ***critical*** data for me, so I need something that is not likely to get flaky for any reason.

Does anyone have an ideas for me please?

regards

Max

---

### Post by ptn107 on 2011-06-27
```
sudo aptitude install unison
```

---

### Post by ClientAlive on 2011-06-28
When ever I hear "sync" I think of rsync. It's supposed to be pretty robust too.

```

man rsync

```

I'm sure a guy could write a script for it too but I think (I think) it has options to make it be persistent (don't quote me on that). It's standard with Linux tho (comes with the standard install).
--------------------------

I'm not sure which file a guy would look for but maybe there's a file that is run whenever you insert your usb stick (like the way .bashrc is run on startup). If there is such a file seems like a guy could put a scrip in it that calls to rsync and even a filter for that particular usb device??

I don't know. Just thinking.
---------------------------

Edit 2:

With Ubuntu 10.04 the mount point for usb is

```

/media

```

---

### Post by MaxVK on 2011-06-28
ptn107: 
Thanks, I did see others mention Unison but I also saw that someone thought it was 'Flaky' at times, which is why I didn't just jump at it. Have there been any reports of 'Flakiness' that you know of with Unison?

ClientAlive:
Yes, I also read about rsync but what I was reading seemed to far to complex and rigid for what I need to do - I need only those files that have been changed to be copied and I read of some issue with file dates or something that meant things would not always be copied.

I like the idea of being able to script rsync, but if Unison is as simple as Iv seen then that would be easier and quicker, my only concern being any possible 'Flakiness'.

Thanks for your ideas, Id certainly like to hear about it if there are any negative reports you may have heard about Unison, otherwise I think this might be the way to go.

Cheers

Max

---

