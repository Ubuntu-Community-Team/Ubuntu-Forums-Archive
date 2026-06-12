---
title: "How to check md5sum on a downloaded file"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by yeehi on 2009-03-22
I have the file on my hard disk.
How do I check its md5sum?

I tried right clicking and looking in properties, but nothing was listed.

Do I need to install another program? Which one?

---

### Post by taurus on 2009-03-22
What file is it?  Are you currently running windows or Linux?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by yeehi on 2009-03-22
On linux, OperaTor:

[http://archetwist.com/opera/operator](http://archetwist.com/opera/operator)

Thank you for your help.

---

### Post by taurus on 2009-03-22
How about running it from a terminal.  Open a terminal, Applications -> Accessories -> Terminal, and change to whichever directory that you've saved the first.  Then run md5sum from there.

```
cd ~/Desktop (Assuming you've saved it to your desktop.)
md5sum *filename*
```

---

### Post by yeehi on 2009-03-22
Thank you.
I did the MD5sum.

A GUI for the MD5sum would be very nice. It would help with checking the comparison, too.

Is there an application you recommend for this?

---

### Post by Sef on 2009-03-22
> A GUI for the MD5sum would be very nice. It would help with checking the comparison, too.

Is there an application you recommend for this?

If you download via a torrent, then the md5sum is done automatically.

---

### Post by yeehi on 2009-03-22
I would like to check md5sums on files not downloaded from a torrent, too.

Typing md5sum into package manager results in lots of hits. I don´t know which to choose.

---

### Post by roger_1960 on 2009-03-22
Hi

I suggest you try gisomount  It has a GUI and can be run by typing gisomount in terminal.  You can of course create an icon on the desktop to run it if you wish.

---

