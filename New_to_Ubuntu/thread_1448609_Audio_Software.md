---
title: "Audio Software"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by Frogs Hair on 2010-04-06
Hi,

I'm looking for some audio software , a six or eight  ban graphic EQ . If there is a good ,up to date selection in the repository, please point me in the right direction. Thanks

---

### Post by RedSingularity on 2010-04-06
How about audacity?

---

### Post by tekkidd on 2010-04-06
Audacity is simple

If you want to go PRO go for Ardour 

Both are in repos

---

### Post by Frogs Hair on 2010-04-06
Thanks ! I will give it a try. Many times I don't know whats up to date  and still supported in the repository.

---

### Post by Frogs Hair on 2010-04-07
Hi,
 
Installed Audacity and lost all sound when I opened the program incuding Rythmbox,
Last.fm and system sounds. After removing the program audio worked again. I checked all volume and mute settings in Audacity and Ubuntu before removing the program.

---

### Post by derande on 2010-04-07
As much as I hate to do it, I run either Audition or Cool Edit Pro 2 under Virtualbox > Windows.

I do audio editing work in my day job (and on personal time) and Audacity just isn't robust enough for me.

---

### Post by lidex on 2010-04-07
> **Frogs Hair said:**
> Hi,
 
Installed Audacity and lost all sound when I opened the program incuding Rythmbox,
Last.fm and system sounds. After removing the program audio worked again. I checked all volume and mute settings in Audacity and Ubuntu before removing the program.

Did you check PCM level in alsamixer?
```
alsamixer
```

---

### Post by Frogs Hair on 2010-04-07
Thanks For the reply! 

PCM  is 100<>100

---

### Post by Frogs Hair on 2010-04-17
Solved !  I found that the Pulse Audio EQ from the ppa suits my needs .

---

