---
title: "No sound in Kubuntu"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by bonez4ever on 2009-10-19
Hi guys everything I play doesn't have sound and all it says is "Unexpected end of data, some information may be lost." I need some help I am still a big noob at Kubuntu.

-Thanks
Bonez4ever

---

### Post by martrn on 2009-10-19
Ubuntu is not recognising your sound card or sending data to it.

You need to open a terminal to diagnoise sound card problems because they are something that is at the very basic level (eg in a linux kernel module.)

What do you get when you type :-
```
lspci -v | less
aplay -l
```
To list motherboard cards, and list playable sound cards.  ????

Have you seen / tried 
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
it can be something simple but can also be something at the end but generally these sound troubleshooting steps  work!

---

### Post by SkyNet2029 on 2009-10-19
I thought Kubuntu used alsaconf? can't you just do a 
 
```
$sudo alsaconf
```
 
and reset the hardware that way to see if that fixes it?

---

### Post by sandyd on 2009-10-19
> **SkyNet2029 said:**
> I thought Kubuntu used alsaconf? can't you just do a 
 
```
$sudo alsaconf
```and reset the hardware that way to see if that fixes it?
alsaconf is depreciated and has been removed from the ubuntu repos (removed from alsa-utils) for some time already.

---

### Post by bonez4ever on 2009-10-19
Thanks for the post I am trying everything now

---

