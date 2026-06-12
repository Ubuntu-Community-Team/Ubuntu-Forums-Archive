---
title: "auto-update of firefox 4.0b2"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by fremantle on 2010-07-29
i installed firefox latest beta by following these awesome instructions [http://surferzworld.com/?p=193](http://surferzworld.com/?p=193)

now i wana know which repository i should add to my sources so that i will get the latest update for the beta firefox.
thnx


10.10a2

---

### Post by Res2216firestar on 2010-07-29
Unfortunately, there's no repository that has beta versions of firefox. You'll have to do it manually.

---

### Post by itisbasi on 2010-07-30
You can add the mozilla daily builds ppa.

sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa && sudo apt-get update
sudo apt-get install firefox-4.0

There are instructions in the link that you've quoted in your post.

---

