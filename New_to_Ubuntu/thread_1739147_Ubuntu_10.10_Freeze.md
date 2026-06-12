---
title: "Ubuntu 10.10 Freeze"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by daniell59 on 2011-04-25
I gave my friend a CD with Ubuntu 10.10 32 bits. He tried running it off the CD. After about 5 or ten minutes it freezes. This has happened about 2 or 3 times. I MD5 sum tested it. The download was perfect. He says that there are no such freezes in Windows XP. He has one GIG of memory.
Any ideas?

Thanks

---

### Post by mynameisnotbob on 2011-04-25
Did you run memtest? (can you do that from LiveCD?) It could be his cache.

---

### Post by daniell59 on 2011-04-25
> **mynameisnotbob said:**
> Did you run memtest? (can you do that from LiveCD?) It could be his cache.

Thanks,

I haven't checked Ubuntu 10.10 Does it provide for a memory test?

---

### Post by Rex Bouwense on 2011-04-25
> **daniell59 said:**
> I gave my friend a CD with Ubuntu 10.10 32 bits. He tried running it off the CD. After about 5 or ten minutes it freezes. This has happened about 2 or 3 times. I MD5 sum tested it. The download was perfect. He says that there are no such freezes in Windows XP. He has one GIG of memory.
Any ideas?

Thanks
Another possibility is a bad burn.  Occasionally, I have run an md5sum on a downloaded distro and then burned it to a CD.  It wouldn't boot.  After reading about similar problems in the forums I figured I got a bad burn so I burned it at a slower speed and bingo bango success.  Did you use the CD for your installation?  That would be an indication that the burn was good.

---

### Post by Dutch70 on 2011-04-25
It can be many things when it comes to freezes. Does it do it in failsafe mode? How about if you disable Compiz? To do that, right click your desktop, select "change background" and then click the visual effects tab & select "none" 

Also, what video card do you have? To be sure, run the following command in a terminal and copy/paste the output into your next post.
```
lspci | grep VGA
```

---

### Post by daniell59 on 2011-04-25
> **Rex Bouwense said:**
> Another possibility is a bad burn.  Occasionally, I have run an md5sum on a downloaded distro and then burned it to a CD.  It wouldn't boot.  After reading about similar problems in the forums I figured I got a bad burn so I burned it at a slower speed and bingo bango success.  Did you use the CD for your installation?  That would be an indication that the burn was good.

The installation also froze.

---

### Post by jtarin on 2011-04-25
Do as suggested then.....recheck the MD5 and burn at a slower speed.What media are you burning to?

---

### Post by mynameisnotbob on 2011-04-26
> **daniell59 said:**
> Thanks,

I haven't checked Ubuntu 10.10 Does it provide for a memory test?

yes, it has two memtest options in the GRUB, at least on my box.

---

