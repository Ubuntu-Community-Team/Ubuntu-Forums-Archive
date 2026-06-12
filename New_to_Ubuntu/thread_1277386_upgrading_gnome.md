---
title: "upgrading gnome"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by libihero on 2009-09-28
is there any way for me to upgrade my gnome from 2.24 to 2.28 without upgrading my ubuntu?

---

### Post by Darkwing-Duck on 2009-09-28
I was doing some reading on this and all I can find to do this is to compile an updated Gnome for yourself. The guys over at Gnome have built a way to get it done however. Note, this is not a easy task.
 
[http://projects.gnome.org/garnome/docs.html](http://projects.gnome.org/garnome/docs.html)
 
Sorry we couldn't be more help for you.[SIZE=2]
[/SIZE]

---

### Post by nhasian on 2009-09-28
are you still on Ubuntu 8.10?  I know 9.04 had some issues with Intel video cards, but 9.10 is just a month away and it is going to be a really nice release with lots of improvements.  You can test out the karmic beta build this thursday by booting off a liveCD.

---

### Post by LewRockwell on 2009-09-28
> **libihero said:**
> is there any way for me to upgrade my gnome from 2.24 to 2.28 without upgrading my ubuntu?

It might be possible to do this although we wouldn't bother with Karmic Koala right around the corner

.

---

### Post by libihero on 2009-09-28
ya im still on 8.10 cuz of the graphics card
so karmic is supposed to have that problem fixed?

---

### Post by nhasian on 2009-09-28
Looks like I hit that right on the nail.  :KS
Yeah Karmic has much better support for both Intel and ATI video adaptors.  I'm feeling left out cause they didnt add KMS for Nvidia cards yet.  Maybe by Lucid Lynx 10.04 for me...

anyway,

download the Karmic Beta LiveCD ISO when its released on Thursday and give it a whirl.  I think you will be pleased.  

btw, you will want to backup your existing data and do a fresh install to take advantage of grub2 and EXT4 if you choose to install Karmic.

> **libihero said:**
> ya im still on 8.10 cuz of the graphics card


---

### Post by Mark Phelps on 2009-09-29
> **libihero said:**
> ya im still on 8.10 cuz of the graphics card
so karmic is supposed to have that problem fixed?

Didn't notice what card you have, but if it's an ATI and it's NOT one of the newer HD 3x or HD4x cards, the answer is NO -- it's not fixed in Karmic -- at least, not in any of the alphas I've tried so far.

---

### Post by libihero on 2009-09-29
haha ya i have one of the older ones
so im guessin imma be stuck with 8.10 then for a while :(

---

### Post by Mark Phelps on 2009-10-01
> **libihero said:**
> haha ya i have one of the older ones
so im guessin imma be stuck with 8.10 then for a while :(

Actually, unless ATI/AMD change their collective minds and decide to restore support for the older (what they now call "legacy" cards) or the open source driver developers decide to add 3D acceleration to the current drivers -- it's not "for a while", it's "permanently".

BTW -- I'm in the same situation and quite disgusted at ATI/AMDs dropping of support for these cards -- some of which are still being sold today!

---

### Post by LewRockwell on 2009-10-01
> **Mark Phelps said:**
> Actually, unless ATI/AMD change their collective minds and decide to restore support for the older (what they now call "legacy" cards) or the open source driver developers decide to add 3D acceleration to the current drivers -- it's not "for a while", it's "permanently".

BTW -- I'm in the same situation and quite disgusted at ATI/AMDs dropping of support for these cards -- some of which are still being sold today!

totally disgusting and unacceptable!

what are they thinking!?!

it's like offering an automobile for sale to everyone...

except that the pedals are ten feet from the seat...

"built for everyone"...as long as you're tall...

{{sigh}}

argh!

.

---

### Post by Mark Phelps on 2009-10-01
> **LewRockwell said:**
> ... 

it's like offering an automobile for sale to everyone...

except that the pedals are ten feet from the seat...

"built for everyone"...as long as you're tall...

{{sigh}}

argh!

.

Actually, I would say it's like selling last year's model car on the lot today, and then when you come back in two months to upgrade the radio, they tell you it's not possible because it's now a "legacy" product! (even though it WAS possible when they built it)

And yeah, I know that tens of thousands for a new car is not like a couple of hundred for a video card -- but the principle is the same (IMHO).

---

### Post by libihero on 2009-10-01
the only problem i had was that the open source video card would sometimes cause my screen to flicker for a second
if that gets fixed or if there's a way to fix that, then i would upgrade

---

