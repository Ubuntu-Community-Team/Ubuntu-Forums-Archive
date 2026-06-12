---
title: "driver install question"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by clay woodruff on 2010-01-19
I purchased a webcam and i can't install the drivers from the cd is there a way to install driver from the manufacturers cd. or do i have to use drivers from repository. it is compatable with linux only cant find one that allows it to stream over internet. i run 9.10

---

### Post by warfacegod on 2010-01-19
Go to the webcam's manufacturer website and search for a driver there.

---

### Post by clay woodruff on 2010-01-19
so the cd that came with it is useless. there isnt any terminal command that can be used to get from cd

---

### Post by warfacegod on 2010-01-19
It depends on whether or not the CD has a Linux driver on it. In my experience driver CD's are Windows based.

---

### Post by clay woodruff on 2010-01-19
ok yeah thats what i thought but just wasn't sure, thanks for your time

---

### Post by warfacegod on 2010-01-19
Post back if you need help installing the driver. If not just mark the thread as closed.

---

### Post by halitech on 2010-01-19
> **clay woodruff said:**
> I purchased a webcam and i can't install the drivers from the cd is there a way to install driver from the manufacturers cd. or do i have to use drivers from repository. it is compatable with linux only cant find one that allows it to stream over internet. i run 9.10

do you mean you can get it to work in programs like cheese but you need someway of doing live streaming? If it works in programs like cheese, check here: [http://www.linux.com/news/hardware/peripherals/8211-five-fun-ways-to-use-a-linux-webcam](http://www.linux.com/news/hardware/peripherals/8211-five-fun-ways-to-use-a-linux-webcam)

---

### Post by rossmoore on 2010-01-19
Most of the time you don't need a driver for a webcam in linux - it just works. You can easily check by installing cheese:
sudo apt-get install cheese
Run it from the menu, make sure you've selected the right camera if you have several and it _should_ just work.

It looks like you want to do something else a bit specific - stream the webcam over the web to be viewed somewhere else like a security camera, rather than like skype. I guess this is software that may have come with you webcam, and that's what you're trying to get? I'm sure it can be done in linux, probably pretty easily, but you'll need someone else's help for that - and you'll need to pretty specific about what you want to achieve so we can be sure we find you the right answer.

---

### Post by rossmoore on 2010-01-19
Nice link, halitech - I've bookmarked that one now, thanks!

---

