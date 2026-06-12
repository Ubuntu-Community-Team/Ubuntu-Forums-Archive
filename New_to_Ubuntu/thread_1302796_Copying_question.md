---
title: "Copying question"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by KyleRickards on 2009-10-27
Hi all

I feel so silly for asking this but...

I have a folder on my PC (ubuntu) with quite a few files and folders in it. I have previously copied this as a back up to my external HDD.

I have since made some changes and added things to the original folder and thought that I could copy it across to the external drive again, selecting "Skip All" to avoid copy the data I had already backed up. However, when I select Skip All, it seems to start copying everything across again anyways (rather than the just the stuff I have added since).

Am I being completely stupid here and missing the point?

K.

---

### Post by martrn on 2009-10-27
Use UnisonFileSynchronizer The file synchronisation tool in order to ensure that your files are synchronised better, more efficientally and you don't miss any files when your are synchronising them !

[URL="http://en.wikipedia.org/wiki/Unison_(file_synchronizer)"]
http://en.wikipedia.org/wiki/Unison_(file_synchronizer)[/URL]

---

### Post by HarrisonNapper on 2009-10-27
You can also use rsync (and grsync if you prefer a GUI) which is in synaptic.

Cheers.

---

### Post by KyleRickards on 2009-10-27
Thanks for that, I don't want to copy all the drive though, just this one folder and its subs - will it do that?

Edit - is it command line only?

Kyle

---

### Post by KyleRickards on 2009-10-27
Thanks all

Using Grsync now, seems perfect for what I want!

Kyle

---

### Post by tea for one on 2009-10-27
> **KyleRickards said:**
> Thanks for that, I don't want to copy all the drive though, just this one folder and its subs - will it do that?

Edit - is it command line only?

Kyle

I also would recommend Grsync and it does have a reasonably intuitive GUI. Once you have made an original back up, it will sync the changes only but you have many options in the interface to control the back up operation.

---

