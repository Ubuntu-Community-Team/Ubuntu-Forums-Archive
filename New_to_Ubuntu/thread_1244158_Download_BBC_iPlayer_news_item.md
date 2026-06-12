---
title: "Download BBC iPlayer news item"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-08-19
A friend was on the news on TV last night, and he's asked me to download the news item to save it for posterity.

I'm not managing to figure out how to do this. I can find the news item on [bbc.co.uk]("http://www.bbc.co.uk/"), but not how to download it.

I have access to Ubuntu 8.04, Ubuntu 9.04 and Windows Vista, so whichever is easiest.

Can anyone help (I believe that the item expires in just a couple of hours)?

Thank you.

---

### Post by zeroseven0183 on 2009-08-19
This might sound a bit technical but if you can locate in the page source the filename of the video then you can download it using your browser.

Do you know the file extension of the video?

---

### Post by Paddy Landau on 2009-08-19
I've had a look at the [web page's]("http://www.bbc.co.uk/mediaselector/check/england/realmedia/southtoday/oxford/oxford?size=16x9&bgc=C0C0C0&nbram=1&bbram=1&nbwm=1&bbwm=1") source code. I'm really not sure, but could it be .asx?

If so, then I have this [video link]("http://www.bbc.co.uk/england/realmedia/southtoday/oxford/bb/oxford_16x9_bb.asx") (I think) -- which doesn't work on my 8.04 machine.

---

### Post by philinux on 2009-08-19
Right click on it then select open with movie player. After it's streamed dont close totem. Open places file system and go to /tmp the file will be in there.

---

### Post by howefield on 2009-08-19
Just tested this in a virtual machine (windows xp) and worked a treat.

[http://www.hidownload.com/download-streaming-solutions/download-bbc-news-video.htm](http://www.hidownload.com/download-streaming-solutions/download-bbc-news-video.htm)

---

### Post by Paddy Landau on 2009-08-19
Wow, what a hassle!

> **philinux said:**
> Right click on it then select open with movie player. After it's streamed dont close totem. Open places file system and go to /tmp the file will be in there.
Unfortunately, the only file left in /tmp was a socket for Totem, which didn't help me.

> **howefield said:**
> ... tested this in a virtual machine (windows xp) and worked a treat.
It says that it doesn't work for asx files. And guess what! However, the same site did say how to do it:
[http://www.hidownload.com/support/download-asx-wmx.htm](http://www.hidownload.com/support/download-asx-wmx.htm)

Thank you for the help. I'll mark this thread as solved.

---

