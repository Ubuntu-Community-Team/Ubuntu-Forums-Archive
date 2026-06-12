---
title: "How do I downgrade back to 8.10?"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-28
i hate 9.04. i regret upgrading. everything worked fantastically in 8.10. 

is there a way to "downgrade" back to 8.10 without having to nuke my hard drive and start over?

---

### Post by skymera on 2009-04-28
Sorry to hear about your bad experience.

It's generally not easy to downgrade.
How did you install 9.04?

Try a fresh install. Upgrades have always been a pain for me. I fresh installed 9.04 a while back and it's run flawless.
Though Jaunty has been getting mixed reviews.

---

### Post by asuastrophysics on 2009-04-28
you know, a smart idea i probably should've implemented....

putting the /home folder on a separate partition :rolleyes:

how did i install 9.04?
days before the release: ALT+F2 
```
update-manager -d
```
> a new distribution is available. update?
i selected "yes"

9.04 will be great. (probably already is, i should just blame ATI and nVidia both for being so slow to release drivers) 

i'm sure of it. but as of right now, no proprietary drivers for 
ATI Radeon HD 2400 pro   OR 
Intel Mobile GM965/GL960
exist yet. so i have to run metacity and compiz is disabled. bleh. 

hey but at least i know i was very impressed with 8.10! loved it. everything worked flawlessly.

---

### Post by skymera on 2009-04-28
I'm pretty sure the ATI Radeon HD 2400 pro is still supported by FGLRX driver. :)

Reinstall doesn't take long :) I've reinstalled 2/3 times a day before after borking the first two :P

---

### Post by asuastrophysics on 2009-04-28
> **skymera said:**
> I'm pretty sure the ATI Radeon HD 2400 pro is still supported by FGLRX driver. :)

hey, thanks for the fast response :P

no but the FGLRX driver itself is not compatible with jaunty's new version of X-server. not sure why. gotta wait until the new ATI catalyst comes out for that. 

would you suggest making a /home partition? is this a good idea? 
how will ubuntu know that i already have a /home folder on a seperate partition?

---

### Post by skymera on 2009-04-28
I'm running 9.04 with FGLRX on my 4870.
It does work, Compiz'n'all :)
I installed my driver with Envy (from repos)

I would suggest a /home partition if you plan on keeping any precious files or settings.

---

### Post by asuastrophysics on 2009-04-28
> **skymera said:**
> I'm running 9.04 with FGLRX on my 4870.
It does work, Compiz'n'all :)
I installed my driver with Envy (from repos) 

haha oh yeah i had forgotten about envy. i just know that installing catalyst doesnt work...at least for me :lolflag:

---

### Post by tom56 on 2009-04-28
> **skymera said:**
> I would suggest a /home partition if you plan on keeping any precious files or settings.

You should be backing up /home regularly anyway, in which case a separate partition is not necessary.

---

### Post by CoraCoronel on 2009-04-30
:P Hi:

I'm upgrade my SO 8.10 to 9.04, but is so slowly, my video card I think don't really works. So I need know if I can make a downgrade...I really needed. My lap is a Toshiba Satellite A205-SP5830, 2 mb ram, and 160gb hard disk, intel pentium dual core so...somebody can really help me please??

---

### Post by Didius Falco on 2009-04-30
> **CoraCoronel said:**
> :P Hi:

I'm upgrade my SO 8.10 to 9.04, but is so slowly, my video card I think don't really works. So I need know if I can make a downgrade...I really needed. My lap is a Toshiba Satellite A205-SP5830, 2 mb ram, and 160gb hard disk, intel pentium dual core so...somebody can really help me please??

Hi,

When you need some help, you should start a new thread. This is because it is considered impolite to "hijack" the thread.

In your case, the answer you seek is already in the posts above.

Your basic choices, which I'll list in order from easiest to hardest:

1. Reinstall over the top of your 9.04 installation, which will delete all the files on it, including your data.

If you don't have any data that you care about saving, this is the quickest, easiest route.

2. Back up your data first, then reinstall. You can copy your data back after the install is done.

3. It is possible to make a separate partition for your /Home directory and copy your Home folder and all it's contents to it.

Here is a guide to doing that:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

You would then install Ubuntu 8.10 over the top of the current installation, but highlight the new /Home partition, choose the "edit partition" button, tell it to use it, set it to use it as "/Home" but **not** let it partition it.

If you have further questions, come on back to the forum, start a new thread and ask away.

One more tip - make a title for the thread that will let people know what it is you need help with. "Set up a separate Home partition" will get a lot more response that "Help!!!" will, and include as much information as you can in the first post, so people will know how to help you.

I hope this helps you!!

---

