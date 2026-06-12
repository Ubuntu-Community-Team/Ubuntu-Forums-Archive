---
title: "Installing firefox 4"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by FORCEGC on 2011-03-22
I am trying to install firefox 4 on ubuntu 10.04 lucid and i cant seem to understand the tarball file type whatsoever. Can you guys please walk me through it i have searched on google and they dont help me so i have came to the gurus.

---

### Post by jmszr on 2011-03-22
FORCEGC,

Here is a link to the Firefox 4 Mega Thread: [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

Instructions are in the first post.

Edit: Or, as below.

---

### Post by jcolyn on 2011-03-22
You don't need the tar do the below and firefox will be upgraded to the new stable firefox 4

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
``` ```
sudo apt-get update
``` ```
sudo apt-get install firefox ubufox
```

---

### Post by FORCEGC on 2011-03-22
Thank you so much it worked. :)

---

### Post by Alancj05 on 2011-03-22
Thanks. It updated my 3.6 nicely. I was getting crashes with firefox on both Vista and Ubuntu. For a while Java wasn't working right either. It was slow as hell. I hope 4 is more stable! I about started using IE 9.

---

### Post by zaivala on 2011-03-23
Jcolyn, I did what you said, and still have 3.6.

---

### Post by zaivala on 2011-03-23
This worked:


Code:

sudo add-apt-repository ppa:mozillateam/firefox-next
sudo apt-get update
sudo apt-get install firefox-4.0

OK. No it didn't. That is, I installed 4.0, but it doesn't show up. Do I need to purge 3.6? What next?

---

### Post by oklokl on 2011-03-23
[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)
Delete is the same in

---

### Post by expatCM on 2011-03-23
zaivala ...  you may be missing step #6 in the following thread.

[http://ubuntuforums.org/showthread.php?t=1712181](http://ubuntuforums.org/showthread.php?t=1712181)

---

